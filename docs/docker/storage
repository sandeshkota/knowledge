### Docker storage
When you install docker the follwoing file system is created
```
/var/lib/docker
  aufs
  containers
  image
  volumnes
```

### Multiple applications with alomost same images
- The layered images that are created using docker are stored in ``` iamges ```

Dockerfile #1
```
FROM UBUNTU

RUN apt-get update && apt-get -y install python

RUN pip install flask flask-mysql

COPY ./opt/source-code

ENTRYPOINT FLASK_APP=/opt/source-code/app.py flask run
```
To build
```
docker build Dockerfile -t sk/sample-app
```


Dockerfile #2
```
FROM UBUNTU

RUN apt-get update && apt-get -y install python

RUN pip install flask flask-mysql

COPY app2.py/opt/source-code

ENTRYPOINT FLASK_APP=/opt/source-code/app2.py flask run
```
To build
```
docker build Dockerfile -t sk/sample2-app
```

In the above case the images that are built in the First Dockerfile (except the code) is re-used 
and only the Source code iiamge is built on top of the flask image that was already buil;t using Dockerfile #1 


### Readonly Layer and Read-Write Layer
When a container is ran using an image - a new container layer is created which is a read-write layer. Where the container generated data is stored.
