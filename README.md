# DockerNotes


### Frequently Used Docker Commands
|Purpose	|	Command/Description|
|-----------|----------------------|
|List all containers |	docker ps -a|
|List all images|	docker images|
|View logs of a container|	docker logs <container_name>|
|Stop a running container|	docker stop <container_name>|
|Remove a container	|docker rm <container_name>|
|Remove an image|	docker rmi <image_name>|
|Copy files from container|	docker cp <container_name>:<path_within_container> <dest_path_in_host>|
|Copy files to container|	docker cp <src_path_in_host> <dest_container_name>:<path_within_container> |
|Cleaning up old images/networks|	Stop all containers. Then \n docker system prune -f| 
|Log in to a running container|	docker exec -ti <container_name> sh|
|Check the contents of an image|	You have to create a container from the image to do so. Use the run command to start a container.\n  docker run -ti --rm <image_name> sh| 



## Permission Issues
Since there are volume mappings for server log directories to the host machine, the very first attempt to start the server might fail with the server unable to write logs. This can be easily fixed by changing the owner and(or) allowing appropriate permissions.
By default, the log directories are mapped under the host directory /opt/docker/was-9.0.0-mq-9.0-npp-6.2
```
sudo chown -R iid:iid /opt/docker/was-9.0.0-mq-9.0-npp-6.2 && chmod -R 777 /opt/docker/was-9.0.0-mq-9.0-npp-6.2
```
