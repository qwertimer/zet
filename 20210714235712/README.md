# docker can set just internet access for the container

If you want to set a docker container to give internet access you can set `--network = bridge` if you want complete access you can set `--network = host`. This is helpful if you want to provide open connectivity to the docker container and your computer acts as a router. Further research might be needed in this. 
