### Default types of networks in docker
- bridge
- none
- host

### Commands

To see the list of networks
``` docker network ls ```

To create a new network
``` docker network create <network_name> ```

To use this network when running an application
``` docker run -d -p 8000:80 --net <network_name> sample-web-app ```



