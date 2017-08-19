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
- You can add contact details using `LABEL maintainer="your@email.com".
- To build an image you use `docker image build`.
- You can pass other information using the `--tag` command.
- You can list all images built using `docker image ls`.

## Level 3