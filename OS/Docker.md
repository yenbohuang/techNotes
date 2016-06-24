# Verify docker installation

See if this command works.

    docker run hello-world

See details on <https://docs.docker.com/linux/step_one/>

# Run a docker image

    docker run [OPTIONS] IMAGE [COMMAND] [ARG...]

# List all docker images

    docker images

See details on <https://docs.docker.com/linux/step_three/>

# See which docker containers are ran

    docker ps 

See details on <https://docs.docker.com/engine/tutorials/dockerizing/>

# Display logs in a container

    docker logs -f <container name>

See details on <https://docs.docker.com/engine/tutorials/dockerizing/>

# List running process in a contailer

    docker top <container name>

See details on <https://docs.docker.com/engine/tutorials/usingdocker/>

# Inspect container

    docker inspect <container name>

See details on <https://docs.docker.com/engine/tutorials/usingdocker/>

# Open a shell in runnint container

    docker exec -it <container name> /bin/sh

See deatils on <https://docs.docker.com/engine/tutorials/networkingcontainers/>

