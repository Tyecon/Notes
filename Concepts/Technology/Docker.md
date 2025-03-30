Topics: [[Technology]], [[IT]], [[Programming]]
# dock her? I hardly know her.
Docker is a sandboxing environment so 'idk it works on my computer' happens less and if the program explodes, the explosion is safely contained in a docker shipping container.
# How to use
0. Install a package manager (chocolatey on Windows, brew on Mac)
1. Download Docker 
	- Windows:`choco install docker`
	- Mac: `brew install --cask docker
	- Arch: `pacman -yu docker`
	- Debian: `apt-get install docker`
	- Desktop GUI Applications are available: https://www.docker.com/get-started/
2. `docker --version`
3. Docker extension or LSP in your IDE
4. `docker init`
## Dockerfile
```dockerfile
# Example Dockerfile
FROM ubuntu:latest
RUN apt update && apt install -y curl
CMD ["bash"]
```
RUN keywords are while building the image, while CMD is what will run when it's launched.
## Images
A Docker **image** is a blueprint for containers. It includes the OS, software, and dependencies.  
There are plenty of baseimages that you can import into your dockerfile to make it easier.
## Containers
A **container** is a running instance of an image. It's lightweight, isolated, and reproducible.
## Docker Volumes (Persistent Storage)
Docker containers lose data when restarted unless you use volumes.
## Layer Caching
Dependencies put in the dockerfile will be cached so subsequent builds are faster.
## .dockerignore
It will ignore files you don't want to bring in.
## Docker Compose
Docker Compose helps manage multi-container applications (eg backend, database, frontend) with a compose.yaml file.
```yaml
version: '3'
services:
  backend:
    build: .
    ports:
      - '9000:9000'
  web:
    image: nginx
    ports:
      - "8080:80"
  db:
    image: postgres:latest
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
    volumes:
      - postgres_data:/var/lib/postgresql/data
volumes:
  postgres_data: 
```
## Docker Scout
Generates detailed reports of packages used in the image, and will check for known vulnerabilities.  
In docker desktop you can just go to the vulnerabilities tab and Start Analysis.
# Commands
- `docker start <container_id>`
- `docker ps`: List running containers.
	- -a to see stopped containers
- `docker volume create my_volume`: Create a persistent storage volume
- `docker run -it ubuntu`: Run container from image
	- `-v my_volume:/data` Add a volume
	- `-p host:container`: Port forwarding
- `docker logs <container_id>`: View logs from running container
- `docker exec -it <container_id> bash`: Access shell from within container
- `docker stop <container_id>`
- `docker rm <container_id>`: Remove container
- `docker rmi <image_id>`: Remove image
- `docker system prune -a`: Remove all stopped containers, unused images, and cache
- `docker-compose up -d`: Start compose in detached mode
- `docker-compose down`: Stop compose
- `docker network ls`: List Networks
- `docker network create my_network`: Create a network
- `docker network connect my_network my_container`: Connect container to network
