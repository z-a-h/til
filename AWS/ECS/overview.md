# EC2 Container Service 

The EC2 Container Service or ECS is an AWS service for managing docker containers

## Creating a Repository for an Docker Image

First create a new ECS repository in the AWS console. After creation you should
see a list of bash commands for build, tagging and pushing a docker image.

Run `aws ecr get-login --no-include-email --region us-west-1` to get login
credentials for connecting dockerhub to AWS. Then run the `docker login` command
that is returned from the `aws ecr get-login`. 

Tip: Run `$(aws ecr get-login --no-include-email --region us-west-1)` to pipe
the output directly into the terminal.

Then build the docker image locally by running `docker build -t <image/name>`

Next, tag the image for local use and for pushing the image to remote repository
by running `docker tag <image/name>:latest <url-for-ecs-repo>:latest`

Finally, push the image to the ECS repo. 
`docker push <url-for-ecs-repo>:latest`


