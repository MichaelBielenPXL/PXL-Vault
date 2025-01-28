# Docker Command Reference

## General Docker Commands

- `docker version` - Show Docker version information.
- `docker info` - Display system-wide information about Docker.
- `docker help` - Get help with Docker commands.

## Working with Images

- `docker images` - List all images on the local system.
- `docker pull <image>` - Download an image from a registry.
- `docker build -t <image_name> .` - Build an image from a Dockerfile.
- `docker rmi <image>` - Remove an image.
- `docker rmi $(docker images -q)` - Removes all images.

## Working with Containers

- `docker ps` - List running containers.
- `docker ps -a` - List all containers (including stopped ones).
- `docker run <image>` - Run a new container from an image.
- `docker run -it <image>` - Run a container interactively (with a terminal).
- `docker run -d <image>` - Run a container in detached mode.
- `docker stop <container>` - Stop a running container.
- `docker start <container>` - Start a stopped container.
- `docker restart <container>` - Restart a container.
- `docker kill <container>` - Forcefully stop a container.
- `docker rm <container>` - Remove a container.
- `docker logs <container>` - Fetch logs of a container.
- `docker exec -it <container> <command>` - Execute a command in a running container.
- `docker attach <container>` - Attach to a running container.
- `docker rm -f $(docker ps -aq)` - Delete all containers stopped and running.

## Networking

- `docker network ls` - List all networks.
- `docker network create <network_name>` - Create a new network.
- `docker network inspect <network>` - Inspect a network.
- `docker network prune -f` - Delete all networks `-f` to skip the confirmation prompt.
- `docker network connect <network> <container>` - Connect a container to a network.
- `docker network disconnect <network> <container>` - Disconnect a container from a network.
- `docker inspect --format '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' <container_name>` - Check the IP address of a container.
- `ifconfig` - Command to check the IP address of a container or Linux system.
- `docker network create --subnet=172.18.0.0/16 network1` - Create a network with a specific subnet.

## Volumes

- `docker volume ls` - List all volumes.
- `docker volume create <volume_name>` - Create a new volume.
- `docker volume inspect <volume>` - Inspect a volume.
- `docker volume rm <volume>` - Remove a volume.
- `docker run -v <volume_name>:/path/in/container <image>` - Mount a volume to a container.
- `docker volume prune -f` - Deletes all unused volumes.

## Docker Compose

- `docker-compose up` - Create and start containers defined in `docker-compose.yml`.
- `docker-compose down` - Stop and remove containers, networks, and volumes defined in `docker-compose.yml`.
- `docker-compose logs` - View logs for all services in a Compose project.

## Container Cleanup

- `docker system prune` - Remove all unused data (containers, networks, images, etc.).
- `docker container prune` - Remove all stopped containers.
- `docker volume prune` - Remove all unused volumes.
- `docker image prune` - Remove dangling images.
- `docker network prune` - Remove all unused networks.

## Advanced Commands

- `docker stats` - Display a live stream of container resource usage.
- `docker inspect <container|image>` - Show detailed information about a container or image.
- `docker history <image>` - Show the history of an image.
- `docker export <container>` - Export a container’s filesystem as a tar archive.
- `docker import <tar_file>` - Import a tarball as an image.
- `docker save <image>` - Save an image to a tar archive.
- `docker load <tar_file>` - Load an image from a tar archive.

## MySQL and PHPMyAdmin

- Start MySQL container:
    
    ```bash
    docker run -d --name my_mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=rootpassword mysql:latest
    ```
    
- Start PHPMyAdmin container:
    
    ```bash
    docker run -d --name phpmyadmin -p 8081:80 --link my_mysql:db -e PMA_HOST=db -e PMA_PORT=3306 phpmyadmin/phpmyadmin
    ```
    

## SSH Configuration

- Copy public SSH key to server:
    
    ```bash
    type $HOME\.ssh\id_ed25519.pub | ssh student@172.24.64.1 -p 2222 "mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys && chmod 600 ~/.ssh/authorized_keys && chmod 700 ~/.ssh"
    ```
    

## Dockerfile Instructions

- **FROM**: Sets the base image.
- **RUN**: Executes commands in a new layer.
- **CMD**: Default command for a container.
- **ENTRYPOINT**: Command executed when the container starts.
- **LABEL**: Adds metadata.
- **EXPOSE**: Specifies network ports.
- **ENV**: Sets environment variables.
- **ADD**: Copies files/URLs to the image.
- **COPY**: Copies files/directories to the container.

---