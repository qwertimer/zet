# fork-bomb notes

I found this post on a youtube video -
https://www.youtube.com/watch?v=rwH6h0Avu0U. Thought it worthwhile to
store for later.
Episode 16 - Running a fork-bomb on Linux :(){ :|: & };: 

The "notes.txt" associated with this episode just reads "don't fork bomb lol" but there's still stuff to learn here.

The error message that Dave saw when he ran his fork bomb read:
	fork: Resource temporarily unavailable

This introduces an important but common theme in Unix/Linux systems programming, the standard error numbers and how system calls use them.

In Linux, the man page errno(3) describes a mapping of each error code used by the kernel in communicating with userspace, and a general human-readable description of each error number. On a relatively recent Linux, this includes:
       EAGAIN Resource temporarily unavailable (may be the same value as
              EWOULDBLOCK) (POSIX.1-2001).

EAGAIN refers to the symbolic name of an error number, made available in the Linux standard C library, by doing '#include <errno.h>' in your source code. This contains a line, handled the C pre-processor:
	#define	EAGAIN		11	/* Try again */
... which replaces the symbol EAGAIN with the integer literal 11, any time it occurs in C source code. That same error number is what's returned to C programs by the kernel in certain error conditions. In fact, the kernel itself is generally compiled against the same exact errno.h that the standard library is compiled with.

Not that helpful yet, but every system call and major C library function has a man page including an ERRORS section, where the meaning of that error code in the specific context of this function is explained. From the same Linux as the above quote, for the fork(2) man page:
       EAGAIN A system-imposed limit on the number of threads was
              encountered.  There are a number of limits that may
              trigger this error:

              •  the RLIMIT_NPROC soft resource limit (set via
                 setrlimit(2)), which limits the number of processes and
                 threads for a real user ID, was reached;

              •  the kernel's system-wide limit on the number of
                 processes and threads, /proc/sys/kernel/threads-max,
                 was reached (see proc(5));

              •  the maximum number of PIDs, /proc/sys/kernel/pid_max,
                 was reached (see proc(5)); or

              •  the PID limit (pids.max) imposed by the cgroup "process
                 number" (PIDs) controller was reached.

We've discussed in my comments for previous episodes what a fork() system call does. As a very brief refresher here, it's the way a Unix/Linux process tells the kernel that it needs to spawn a child process. When the kernel, having been asked to do so, returns EAGAIN instead of spawning that process, this man page is telling us that one of four things has happened:
1. The uid isn't permitted to spawn any more processes, via the 'nproc' resource limit which can be accessed via sysctl or manipulated using the /proc/sys/ interfaces, and which interoperates with the process-level ulimit settings.
2. The host itself can't spawn any more processes or threads without a kernel tunable being increased.
3. The host itself can't grant process IDs to any new processes, via a separate kernel tunable. 
4. The cgroup (control group) in which the fork was executed has exhausted its configured limit on available processes. CGroups are the Linux construct upon which containers such as those used by Docker, etcd, and Kubernetes are built, and are comparable to the "zones" concept in Illumos/Solaris, and to other virtualization mechanisms provided by other operating systems that are capable of acting as a hypervisor.

Note that all of these four conditions are Linux-specific! A different Unix will have similar conditions but will instrument potentially very different interfaces to all of the relevant tuning parameters.

Anyway, from the error message we saw, these man pages tell us that Dave's fork bomb didn't exhaust his system of memory, or of CPU time, or of related resources like disk into which audit context needs to be written before a login can occur or a process can spawn. Rather, he exhausted one of the critical limits permitting his fork-bombed environment to keep forking.

Which of the four do I think he hit? Dave mentioned that he was surprised that the system allowed him to SSH back in. SSH runs as root, which is a separate user subjected to a separate resource limit from unprivileged users on the system. He likely only fork-bombed his unprivileged 'dave' user, and not the whole system.

As denial-of-service attacks go, this one is fairly disappointing. If he had looked at resource utilization in the hypervisor, he likely would have seen that the system itself was very busy on CPU, maybe even exhausting more than 100% of one CPU, but not so busy that the hypervisor's scheduler was failing to meet the demand. Other activities for other users on the system, such as privileged daemons, were likely slowed but not halted. His login attempts via ssh were likely still successfully logged. There are far more brutal ways to seize up a system. 

In fact, Dave said that we couldn't recover from the error without rebooting, but this likely wasn't true. Yes, fork() was failing, and yes, most attempts to repair the system would have been based on fork(). But there was one that he still had available to him, which he never tried: exec(). Remember, fork() tells the kernel to spawn a new process, and the kernel here was happily saying "Nope, no, uh-uh, I'm not doing that any more. EAGAIN." But we have another way to get a process, which is to cause an existing one, such as the shell where Dave launched the fork bomb, to execute something: exec(). An exec call tells the kernel: throw out the program running in my existing process, saving all the open file handles and environment variables, and then load this other new program into the hollowed-out process. An exec() would not have given EAGAIN. The man page for execve(2) says that the system call can indeed give EAGAIN, but under different--and narrower--conditions than fork() gives it. He had a shell, as user 'dave'. In fact, he had two shells, the first one where he launched the fork bomb, and the second one that he was surprised to get when he ssh'ed back in. He could have restored the system to normal service with a one-line command from either of those shells: 'exec pkill -u dave bash'. Likely, he could also have gotten an interactive shell which was not blocked from forking processes if he had instead given 'exec sudo su -' and further inspected the health and state of the instance.

So, how can you suck at programming less by thinking about what happened during this episode:
1. Learn more about what options exec gives you on a system which is too resource-starved to fork, and therefore understand more clearly what happens when you say 'exec' before running a command.
2. Learn more about how Unix/Linux error messages are documented, via errno.h, errno(3), and the ERRORS section in various system call man pages.
3. Think about how, in real-world programming, you need to implement meaningful exception handling, not just for exceptions arising from your own logic, but for when you start making low-level calls for things like I/O or memory allocation, and those things raise errors instead of working as normal. If you ask for more memory and don't get it, do you want your program to crash, or do you want it to try to jettison non-essential data and rescue itself? If you try to write to disk and the disk is full, or out of inodes, what do you want to do?

Remember, this fork bomb isn't just a cool example of a compact way to blow up a system. It's also a working model for how a programming error can starve your system of some essential resource. If you were writing a program that was aggressively using fork() and exec() in the way that a bash loop does, and your program recursed in ways you did not expect it to recurse, it could do what this fork bomb does, without intentionality on your part. Having read my notes here, and having watched Dave's video, perhaps now you know more about what kind of error and exception handling you might want to build into such a program. Parallelism is a hugely critical part of modern programming, and perhaps as a software developer you have already learned about things like atomicity and sychronization and threadsafe vs not, but it's not actually turtles all the way down. At the bottom, each time you try to add parallel work, something is using a system call which is doing something like fork(), or like the equivalent calls which are used for threading, to ask the kernel to allocate more resources, and that system call might fail for reasons you do not anticipate during normal operations. With the better understanding of Unix/Linux/POSIX error messages that this video can help teach you, you are better armed to write robust exception handlers for those unexpected problems, so that your program fails more gracefully than Dave's did.

Happy defensive programming!
