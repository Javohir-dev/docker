#### List of running containers:
```bash
docker ps
```
#### List of all containers:
```bash
docker ps -a
```
#### List of all containers (only id):
```bash
docker ps -aq
```
#### Download image from official site:
```bash
docker pull <image_name>
```
#### List or images:
```bash
docker images
```
#### Remove images
```bash
docker image rm <image_name>
```
#### Run container:
```bash
docker run <image_name>:<tag>
```
#### Run container on background (detached) mode:
```bash
docker run -d <image_name>:<tag>
```
#### Map port localhost 8080 to port 80 in the container:
```bash
docker run -d -p 8080:80 <image_name>:<tag>
```
#### List of containers:
```bash
docker container ls
```
#### Stop running container:
```bash
docker stop <container id or name> 
```
#### Start stopped container:
```bash
docker start <container id or name>
``` 
#### Remove container:
```bash
docker rm <container id or name>
```
#### Force Remove container:
```bash
docker rm -f <container id or name>
```
#### Remove all containers:
```bash
docker rm $(docker ps -aq)
```
#### Naming containers:
```bash
docker run --name <container_name>
```
#### List of containers pretty formatted:
##### Format:
```bash
export FORMAT="ID\t{{.ID}}\nNAME\t{{.Names}}\nImage\t{{.Image}}\nPORTS\t{{.Ports}}\nCOMMAND\t{{.Command}}\nCREATED\t{{.CreatedAt}}\nSTATUS\t{{.Status}}\n"
```
```bash
docker run --format=$FORMAT
```
#### Mount current folder to container volume read-only:
```bash
docker run --name website -v $(pwd):/usr/share/nginx/html:ro -d -p 8080:80 nginx
```
#### Enter into container:
```bash
docker exec -it <container_name> bash
```
#### Share volumes between containers:
```bash
docker run --name <container_name> --volumes-from <from_container_name> -d nginx
```
#### Build image with tag from Dockerfile in currenct directory:
```bash
docker build --tag <name:tag> .
```
#### Tagging images:
```bash
docker tag <from image:tag> <to image:new-tag>
```
#### Information about container:
```bash
docker inspect <container_id or name>
```
#### See logs:
```bash
docker logs <container_id>
```
#### See logs with following:
```bash
docker logs -f <container_id>
```
#
## Dockerfile configurations
#### Simple configuration for build node express image:
```Dockerfile
FROM node:latest
WORKDIR /app
ADD package*.json ./
RUN npm install
ADD . .
CMD node index.js
```
