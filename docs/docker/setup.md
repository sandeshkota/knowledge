### Docker file
``` Dockerfile ``` is used toc create docker images

### Staring a service within a container
The CMD (Command) tells which service to start when a docker image is ran
```
FROM UBUNTU
...
CMD [ "nginx" ]
```

Run through command line
``` docker run ubuntu sleep 5 ```

Through docker file
```
FROM UBUNTU

CMD sleep 5
```
Command can also be supplied as an array ``` CMD ["sleep", "5" ] ```
While using the array, the first should always be executable and the rest of the parameters should be listed each as an item in the array

Suppose we want the sleep time to be 100 ``` docker run ubuntu-sleeper 100 ```
```
FROM UBUNTU

ENTRYPOINT ["sleep"]
```

To add a default value if it is not supplied
```
FROM UBUNTU

ENTRYPOINT ["sleep"]

CMD ["5"]
```

If we have a new version of the executable which is in ENTRYPOINT, we can run it using ``` docker run --entrypoint sleep2.0 ubuntu-sleeper 100 ```



### Docker Compose
Suppose we have several docker images to run and also ensure that the containers have access to the required containers, to ensure that all these are handled effectively, we can use Docker Compose file

- Suppose we have an application as below
```
  voting-app (app to vote)              result-app (app to see the results)
  
  im=nmemory-db (redis)                db (postgreSQL)
   
                  worker (.net core)

```

- Without Docker Compose (Use links to link each other contaienrs)
```
docker run -d --name=redis redis

docker run -d --name=db postgre:9.4  --link db:db  

docker run -d --name=vote -p 5000:80  --link redis:redis  voting-app

docker run -d --name=result -p 5001:80 result-app

docker run -d --name=worker  --link db:db    --link redis:redis   worker
```

-- with docker compone. Doesn't need links as the docker compose will create it's own network so that the applications can communicate to each other by default with just the names
```
redis:
  image: redis
db:
  image: postgres:9.4
vote:
  image: voting-app
  ports:
    - 5000:80
  links:
    - redis
result:
  image: result-app
  ports:
    - 5001:80
  links:
    - db
worker:
  image: worker
  links:
    - redis
    - db
```
To bring this up, run ``` docker-compose up ```

Using ```--link``` is old way

- Docker Compose Build (since the last three applications are our own image creations)
```
redis:
  image: redis
db:
  image: postgres:9.4
vote:
  build: ./vote
  ports:
    - 5000:80
  links:
    - redis
result:
  build: ./result
  ports:
    - 5001:80
  links:
    - db
worker:
  build: ./worker
  links:
    - redis
    - db
```


### Docker Compose Versions
The above examples are for version #1. It has changed a lot with amny added features and deprecating old features.

- The containers are linked by default.
```
version: 2
services:
  redis:
    image: redis
  db:
    image: postgres:9.4
  vote:
    image: voting-app
    ports:
      - 5000:80
    depends_on:
      - redis
      
      ...
```

- With different networks
```
version: 2
services:
  redis:
    image: redis
    networks:
      - back-end
      
  db:
    image: postgres:9.4
    networks:
      - back-end
      
  vote:
    ...
    networks:
      - front-end
      - back-end
    
  result:
    ...
    networks:
      - front-end
      - back-end

networks:
  - front-end
  - back-end
```
