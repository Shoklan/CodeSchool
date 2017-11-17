# Try Docker
##

## Level 1
- Linux Containers are isolated environments that can run code while sharing a single OS.
- Docker is a tool to make it easy to work with Linux containers.
- An *Image* is a blueprint for createing a container.
- To start a container use `docker container run <container_name>:<version_#>`.
- You can create a socket via the flag `-p <n>:<n>`.
- That flag stands for publish ports.
- You can run commands against a container using `exec`.
- But, to do that you need to find it's id; use `ls`.
- You can maintain a shell connection to a container using the flags `-it`.

## Level 2
- Dockerfiles are about automating the stuff necessary at container boot.
- All Dockerfiles start with the keyword `FROM`.
- You can open a port using the line `EXPOSE <port>`.
- You can run a command in the container using `RUN`.
- You can add contact details using `LABEL maintainer="your@email.com"`.
- To build an image you use `docker image build`.
- You can pass other information using the `--tag` command.
- You can list all images built using `docker image ls`.

## Level 3
- To get application into the image container, you can:
	1. Copy the files into the container.
	2. Use the Dockerfile.
- Containers don't normally maintain permenancy.
- To solve this, one could use a *Data volume*; which exposes local files to the container.
- Copy files into the container using `docker container cp`.
- The command mut source the host first and then `container_name:<path>`.
- To use the Dockerfile instead, you can use the keyword `COPY`.
- Do have the container run in the background, use `--detach` flag.
- To link and create a volume use `-v <local_path>:<docker_path>`.

## Research
- portainer

## Resources
- [Docker Website](docker.com)
