# Configuring Docker and using shortcut commands

Today i was trying to configure my new system with docker so i could continue some docker fun. I was trying to pull down
an image and had issues connecting to docker hub. Always make sure that dockerd is running if not run `systemctl enable
docker` and `systemctl start docker`. Also if you haven't done so add docker to the user group `sudo usermod -aG docker
$USER`

When this is done the system should enable you to pull images down. Once down you can use a simple program to start an
image.

To begin we need to pull the image down.
```
docker pull <image>
```

Once pulled we can run the container for the first time giving it a name to be used later.
```
docker run -it --name my_container -v src:dest <image>
```

Once this is created we are able to exit and reattach to the container whenever we wish, i wrote a simple program that
starts and attaches to the container or sends an error saying the container name is not there. The script is below.

```
#!/bin/bash

container_name="$@"

[ ! `docker inspect --format='{{.Name}}' $(sudo docker ps -aq --no-trunc) | grep "$container_name"` ]  && echo "Container doesn't exist exiting" && exit
echo "Container $container_name found attaching"

if [ ` docker container inspect -f '{{.State.Running}}' "$container_name" ` == "true" ]; then
  docker attach "$container_name" 
else

  docker start "$container_name" 
  docker attach "$container_name"
fi
```

Simply create the script in your path with a name such as `da` then when you need to run the container just
`da my_container` and you are straight into the container.

If we did not configure the container correctly to begin with we can run `docker rm my_container` to remove the
container however all information will be lost. If information needs to be moved out of the container we can use a
script to retroactively mount a volume into a container. The script is found at my github.
(bootstrapdockervol)[github.com/qwertimer/.dotfiles/scripts/bootstrapdockervol)


