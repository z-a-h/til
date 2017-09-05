# Deploying Docker Containers to Elastic Beanstalk

## Create EC2 Instance

## SSH Into EC2

## Install Docker
>`sudo yum install -y docker`

Start Docker Daemon
>`sudo service docker start`

Ensure Daeon will restart upon reboot
>`sudo chkconfig docker on`

## Download a Docker Container
>`sudo docker pull IMAGE_NAME`

## Test Container 
>`sudo docker run -it --rm IMAGE_NAME
  `i` - makes the container run interactively
  `t` - allocates a pseduo-TTY to the container
  `rm`- tells Docker to delete the container when the last application stops

If container works, then terminate by selecting `CTRL-C`

## Build a Custom Docker Container
Create a subdirectory to store the Dockerfile and a directory to store the
application
>`mkdir ~/application && cd ~/application`
>`mkdir deploy && chmod 777 deploy`

## Build the Docker Image

## Start the Container
>`sudo docker run -d -p 8080 -v /home/ec2-user/application/deploy:/app/src
>IMAGE_NAME`

## Ensure Container is Running
>`sudo docker ps`
Take note of the port mapping
>`PORTS'
>`0.0.0.0:32769->8080/tcp, 0.0.0.0:32768->9990/tcp`
This port mapping tells you that whatever TCP traffic is sent to port `32769` on
EC2 will be forwarded to port `8080` inside the container

## Change the AWS EC2 security group of your Docker Instance
  STEPS:
  - AWS Mgmt Console -> Services -> EC2 -> Security Groups
  - Select Security Group for EC2 instance 
  - Click Inbound Tab -> Edit -> Add Rule
  - `Type: Custom TCP Rule` `Protocol: TCP` 
  - `Port Range: xxxxx-50000` set the range's lower limit to include the port
    number from docker
  - `Source: Anywhere 0.0.0.0/0`
  - Click Save

## Build and Run a Docker Contaier with your Application
- Modify the Dockerfile to include your application 
- `mkdir ~/application` 
- `cd ~/application`
- Create a new Dockerfile, including your application in the image
  - Download files from github or s3
  - Change file ownership 
  - Create a log directory
  - Explicity expose port 8080
- Build Image from Dockerfile
- Run a container from the new image
  >`sudo docker run -d -p 8080 image-name`
  `-p` tells the command to assign a local port on the EC2 and forward all
network traffic from this local port to port 8080 inside the container`

## Deploy a Docker container to AWS Elastic Beanstalk
- Create a Dockerrun.aws.json file
- Make sure to match the port number used by expose in the Dockerfile
- Include a log directory

## Initialize EB
>`eb init`
- Choose Single Container Docker

## Create Application Environment
>`eb create env-name`
After 7-8 minutes the application should be launched and deployed
