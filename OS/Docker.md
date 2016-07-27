# Docker + Consul + Swarm + Registrator + Nginx

These blog posts (from part 1 to 4) introduce about how to use "Docker + Consul + Swarm + Registrator + Nginx" for blue-green deployment:

* <https://technologyconversations.com/2015/07/02/scaling-to-infinity-with-docker-swarm-docker-compose-and-consul-part-14-a-taste-of-what-is-to-come/>
* <https://technologyconversations.com/2015/07/02/scaling-to-infinity-with-docker-swarm-docker-compose-and-consul-part-24-manually-deploying-services/>
* <https://technologyconversations.com/2015/07/02/scaling-to-infinity-with-docker-swarm-docker-compose-and-consul-part-34-blue-green-deployment-automation-and-self-healing-procedure/>
* <https://technologyconversations.com/2015/07/02/scaling-to-infinity-with-docker-swarm-docker-compose-and-consul-part-44-scaling-individual-services/>

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

# List running process in a container

    docker top <container name>

See details on <https://docs.docker.com/engine/tutorials/usingdocker/>

# Inspect container

    docker inspect <container name>

See details on <https://docs.docker.com/engine/tutorials/usingdocker/>

# Open a shell in running container

    docker exec -it <container name> /bin/sh

See details on <https://docs.docker.com/engine/tutorials/networkingcontainers/>

# Stop a running container

    docker stop <container name>

See details on <https://docs.docker.com/engine/tutorials/usingdocker/>

# Clean up local environments

## Kill all running containers

    docker kill $(docker ps -aq)

## Delete all containers

    docker rm $(docker ps -aq)

## Delete all images

    docker rmi -f $(docker images -aq)
