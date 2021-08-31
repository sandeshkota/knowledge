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

