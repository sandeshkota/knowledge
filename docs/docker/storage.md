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
```yaml
FROM UBUNTU

RUN apt-get update && apt-get -y install python

RUN pip install flask flask-mysql

COPY ./opt/source-code

ENTRYPOINT FLASK_APP=/opt/source-code/app.py flask run
```
To build
```yaml
docker build Dockerfile -t sk/sample-app
```


Dockerfile #2
```yaml
FROM UBUNTU

RUN apt-get update && apt-get -y install python

RUN pip install flask flask-mysql

COPY app2.py/opt/source-code

ENTRYPOINT FLASK_APP=/opt/source-code/app2.py flask run
```
To build
```yaml
docker build Dockerfile -t sk/sample2-app
```

In the above case the images that are built in the First Dockerfile (except the code) is re-used 
and only the Source code iiamge is built on top of the flask image that was already buil;t using Dockerfile #1 


### Readonly Layer and Read-Write Layer
When a container is ran using an image - a new container layer is created which is a read-write layer. Where the container generated data is stored.

when the container is closed/deleted, all the data is deleted.

### To Persist
- Volume Mounting
Create a volume
```yaml
docker volume create data_volume 
```
And map this to the container so that the container can use it
```yaml
docker run -v data_volume:/var/lib/mysql mysql 
```

To automatically create a volume, creates the new volume and then mounts it
```yaml
docker run data_new_volume:/var/lib/mysql mysql 
```

- Bind Mounting
In case the volume already exists, a directory,
```yaml
docker run  -v data/mysql:/var/lib/mysql mysql 
```


### New way
Using -v is old way. Use -mount
```yaml
docker run \
--mount type:bind,source=/data/mysql,target=/var/lib/mysql mysql
```
