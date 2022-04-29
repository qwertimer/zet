# Use --start-at-task and --step to move through playbooks in dev

Often i have needed to rerun only a certain part of a playbook during
development. Whilst Ansible is Idempotent and wont change anything that
doesnt need changing some of my plays or tasks take a while. I found if
i need to start at a specific task i can use the `--start-at-task="task
name"` to start at a specific point.

Further to this i can use the `--step` flag to step through the
playbook. This is interactive and so i can skip plays and tasks that i
don't need to do.



