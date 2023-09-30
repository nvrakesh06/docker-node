docker build .

# To see all the docker images
docker image ls
# To see all the docker volume
docker volume ls

# delete 
docker image rm <image-id>

# To name the image
docker build -t <image-name> .

# run container
docker run --name <container-name> <iamge-name>

# detach mode
docker run -d --name <container-name> <iamge-name>

# adding ports
docker run -p 3000:3000 -d --name <container-name> <iamge-name>
// from_port:to_port

# persistent data
docker run -v pathtofolderlocation:pathtofoldercontainer -p 3000:3000 -d --name <container-name> <iamge-name>
docker run -v %cd%:pathtofoldercontainer -p 3000:3000 -d --name <container-name> <iamge-name>
docker run -v ${pwd}:pathtofoldercontainer -p 3000:3000 -d --name <container-name> <iamge-name>
docker run -v ${pwd}:/app -v /app/node_modules -p 3000:3000 -d --name <container-name> <iamge-name> // for node_modules
docker run -v ${pwd}:/app:ro -v /app/node_modules -p 3000:3000 -d --name <container-name> <iamge-name> // for read-only bind mount
docker run -v ${pwd}:/app:ro -v /app/node_modules --env PORT=4000 -p 3000:4000 -d --name <container-name> <iamge-name> // env PORT
docker run -v ${pwd}:/app:ro -v /app/node_modules --env-file ./.env -p 3000:4000 -d --name <container-name> <iamge-name> // env file

# To see all containers
docker ps
docker ps -a

# kill the contianer
docker rm <container-name> -f
# kill the contianer and associated volume
docker rm <container-name> -f -fv

docker volume prune

docker exec -it <container-name> bash
exit

# logs
docker logs <container-name>

printenv // in bash

<!-- build using docker-compose -->
docker-compose up -d
<!-- build image before building containers -->
docker-compose up -d --build
docker-compose down -v

<!-- build using multiple file -->
docker-compose -f docker-compose.yml -f docker-compose.dev.yml up -d