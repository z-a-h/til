# Docker images

### Build an image
Either create an image via a Dockerfile, or pull a remote image from DockerHub

>`docker build -t image-name ./location/of/Dockerfile`

### Download an Image
If no tag or version is given, it will download the latest
>`docker pull image-name:version`

Community images are namespaced
>`docker pull some-dudes/image-name`

### View Downloaded Images on Machine
>`docker images`

### Remove an Image
By name
>`docker rmi image-name`

By id (only need first few letters)
>`docker rmi id`

### Run an image in a container
>`docker run -p HostPort:ContainerPort image-name`
