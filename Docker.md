<p><a target="_blank" href="https://app.eraser.io/workspace/hm0bslbrEGNmIYeGMCml" id="edit-in-eraser-github-link"><img alt="Edit in Eraser" src="https://firebasestorage.googleapis.com/v0/b/second-petal-295822.appspot.com/o/images%2Fgithub%2FOpen%20in%20Eraser.svg?alt=media&amp;token=968381c8-a7e7-472a-8ed6-4a6626da5501"></a></p>

## ❓ What problem existed before Docker?
Before Docker, we faced:

### 1. “It works on my machine” problem
-  Code works on developer laptop 
-  Fails on QA / Production
 👉 Due to: 
-  Different OS 
-  Different library versions 
-  Missing dependencies 
### 2. Environment inconsistency
Example:

-  Dev → Java 17 
-  Prod → Java 11
 💥 App breaks
### 3. Heavy Virtual Machines (VMs)
-  Each VM has full OS 
-  High memory usage 
-  Slow startup
## ❓ How Docker solves it?
Docker uses **containers**:

✔ Lightweight (no full OS)
 ✔ Same environment everywhere
 ✔ Fast startup
 ✔ Portable



👉 Package:

-  Code 
-  Dependencies 
-  Runtime 
-  Config
```
Docker is a platform to build, ship, and run applications using containers.
```
- [ ] container
A container is:

-  Lightweight 
-  Isolated environment 
-  Runs application + dependencies
- [ ] Docker Image
-  Blueprint of container 
-  Read-only 
-  Contains app + dependencies
- [ ] Docker Container
- Running instance of image 
👉 Image = Class
 👉 Container = Object

- [ ] Dockerfile
A script to build an image.

- [ ] Docker Hub
- Public registry to store images 
-  Like GitHub for Docker images
- [ ] Docker network
Allows containers to communicate.

Types:

-  bridge (default) 
-  host 
-  overlay
- [ ] port mapping
- Expose container port to host.
```
docker run -p 8080:80 nginx
```
👉 Host: 8080 → Container: 80

- [ ] Docker Compose
Used to run multi-container apps.

Example:

-  Spring Boot 
-  MySQL 
-  Redis 
👉 Defined in `docker-compose.yml` 



![image.png](/.eraser/hm0bslbrEGNmIYeGMCml___reH6N9pVJiNfGdAXN9KgdrK06xP2___image_xzTeFILMb3PzgjHM_dg7N.png "image.png")





![image.png](/.eraser/hm0bslbrEGNmIYeGMCml___reH6N9pVJiNfGdAXN9KgdrK06xP2___image_KakkF33wjQrxapbg1EZGa.png "image.png")



## What is difference between Docker and Kubernetes?
| Docker | Kubernetes |
| ----- | ----- |
| Container runtime | Orchestration |
| Runs containers | Manages containers |
| Single host | Cluster |
- [ ] container orchestration
Managing:

-  Scaling 
-  Load balancing 
-  Auto-healing 
👉 Done by Kubernetes





```
docker build -t myapp .          # Build image from Dockerfile
docker run -d -p 8080:80 myapp   # Run container in background
docker ps                        # List running containers
docker ps -a                     # List all containers
docker stop <id>                 # Stop a container
docker rm <id>                   # Remove a container
docker images                    # List images
docker rmi <image>               # Remove an image
docker logs <id>                 # View container logs
docker exec -it <id> bash        # Enter running container
docker pull nginx                # Pull image from Docker Hub
docker push myrepo/myapp         # Push image to registry
```




<!--- Eraser file: https://app.eraser.io/workspace/hm0bslbrEGNmIYeGMCml --->