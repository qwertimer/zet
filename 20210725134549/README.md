# Docker runs chroot, namespaces and cgroups along with other things.

Docker essentially runs these tools to isolate the container from the
main OS. It also sets up networking and other things. But essentially
you can play around with this idea by exporting a docker container and
untaring the filesystem. Once done you can chroot into the space and
play around with it. 
[https://btholt.github.io/complete-intro-to-containers/docker-images-without-docker]


