### Creation in CD
- Developer commits the code to Github
- CI (Jenkins) builds the application and packages it into a Docker Image
- Pushes it to Docker Repository
- Deployment: Pulls thre image from Docker repository
- Runs the container using the image

### Creating the Docker images
- Dockerfile - a blue print to create a docker image
- Starts always from a base image

```yaml
# Dockerfile

# A base image  of node
FROM node

# Set environment variables, if needed
ENV MONGO_DB_USERNAME=admin\
    MONGO_DB_PWD=password
    
# executes linux command on host - creates the folder
RUN mkdir -p /home/app

# Copy content - runs in host
COPY . /home/app

CMD [ "node", "/home/app/server.js" ]
```

In Jenkins: Build docker image based on Dockerfile

```yaml
# the . at the end points to docker file path
docker build -t my-app:1.0 .
```

Then it can be pushed to a Dokcer registry
```yaml
docker push <path_image>
```
