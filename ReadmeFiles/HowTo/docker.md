# Docker utils

This file will u help with building and running dockers

## Installation 

Follow the steps on [1] for the correctly instalation for dockers.

## Building dockers

In the repository root run the next command for build the images with microRos (This would be run in all systems)

```
docker build -f Utils/Docker/Files/Dockerfile -t mircro-ros:humble .
```

For run the docker u will need the next command
```
docker run -it --rm --privileged --name micro-ros micro-ros:humble 
```



## Reference

[1] [Install Docker Engine](https://docs.docker.com/engine/install/)