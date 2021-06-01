## Basic Docker Usage
### Pull docker images
Docker images are kernel for docker containers. You can build multiple container for different tasks based on one image. Go to [docker_hub](https://hub.docker.com/) to get new images.
* Search for image
* Filter tags for detail

### Build Container
There are many turtorials explain how to set parameters for constructing Docker containers. [Officail one](https://docs.docker.com/engine/reference/commandline/run/) and [Chinese](https://www.runoob.com/docker/docker-run-command.html).

Also Simple one.
```
docker run -it --net=host -p 8888:8888 --gpus all --name YourName -v /home/Username/project:/workspace docker_image:tag_name bash
```
A simple explaination of parameters above:
* `-it` interactive
* `--net` network setting
* `-p` portal setting
* `--gpus` allow this container use GPU
* `--name` naming this container
* `--v` mount docker space with actual space in your PC, need to specify this if you want keep files that modified in docker
* `docker_image:tag_name` the docker image
* `bash` allow you use command line(CLI) to operate in container
