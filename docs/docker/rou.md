### Docker exits after running unless a process inside the container is running. 
- Running ``` docker run nginx ``` will download the image and run the contianer
- Then if you run ``` docker ps -a ``` will show the container in exited state
- Ideally containers are meant to run a specific process and not to run the OS

### Run and Sleep for sometime
``` docker run ubuntu sleep 5 ``` runs the container, waits for 5 ms and then exits

### By default Docker doesn't listens to the standard input or output
We need to attach the standard input / output for the container
