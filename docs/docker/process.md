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

### Push to private repo
- Create a private repository in AWS or other places

- Login to the private repo
```yaml
# Logging in to AWS repo ( AWS CLI to be installed & credentials configured)
$(aws ecr get-login --no-include-email --region eu-central-1)
```

- Naming an image: registryDomain/imageName:tag
```yaml
docker pull mango:4.2
# is same as
docker pull docker.io/library/mongo:4.2
```

- For private repo, full name should be provided
```yaml
# to push to docker.io
docker push <image_name>

# to private repo - we need to tag it with repo path
docker tag my-app:1.0 213232.dkr.ecr.eu-central-1.amazonaws.com/my-app:1.0

# Push the tagged image to private repo
docker push 213232.dkr.ecr.eu-central-1.amazonaws.com/my-app:1.0
```

### Pull the image and run container
- Pull image from repo

```yaml
# DockerCompose file

version: 3
services:
    my-app:
        image: 213232.dkr.ecr.eu-central-1.amazonaws.com/my-app:1.0
        ports: 
            - 3000:3000
            
        volumes:
            - db-data:/var/lib/mysql/data
            
volumes:
    db-data
```

