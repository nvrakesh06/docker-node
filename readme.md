docker build .

# To see all the docker images
docker image ls

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

# To see all containers
docker ps

# kill the contianer
docker rm <container-name> -f

docker exec -it <container-name> bash
exit