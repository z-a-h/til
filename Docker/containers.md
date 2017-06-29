# Docket Containers

### Run container from image-name
Will download image from docker hub if it's not saved locally
>`docker run image-name`

### Run as background daemon
>`docker run -d image-name`

### View containers currently running
>`docker ps`

### Stop a Container
>`docker stop container-id`

### View Containers Regardless of Status
>`docker ps -a`

### Start a Container
>`docker start container-id`

### Remove a Container
Container must be stopped before it can be removed
>`docker rm container-id`

### Run a Short-lived Container
Runs the command in docker, then immediately shuts down the container after the command exits
>`docker run --rm container one-off-command`
