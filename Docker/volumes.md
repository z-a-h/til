# Docker Volumes

Containers are not persistant by design
Instead, docker uses volumes to persist data between container instances

The same volume can be mounted to multiple containers

### Create Volume
>`docker volume create --name webdata`

### Mount a Volume to a Container
When running a container, use the `-v` flag to specify a volume to attach followed by `:` and the file path to mount the volume at
>`docker run -v webdata:/usr/share/file/path -p 8000:80 image-name`

### View the names & locations of the volumes mounted to a specific container
>`docker inspect -f '{{ .Mounts }}' container-name`
>`## OUTPUT : [{volume-name /var/lib/docker/volumes/volume-name/_data /usr/share/file/path local z true rprivate}]`

### Find information about a specific volume
>`docker volume inspect volume-name`

### List All Volumes
`docker volume ls`

Must stop all containers before removing a volume

### Remove Volume
>`docker volume rm volume-name`
