# Launch Configurations and Auto Scaling Groups 

Automate and manage many Instances at once

## Launch Configuration

A blueprint for an EC2 Instance. 

## Auto Scaling Group

Uses Launch Configurations to create and manage the scaling of instances 

1. Set up a Launch Config with ECS Container Agent 
2. Point the Container Agent to the desired Cluster

Note About Container Instances 
- Point Directly to Internet Gateway
- Point to a NAT Gateway or NAT Instances 

## Terminology 

### Total Service CPU Reservations 

  Number of Tasks X CPU Reserved by each Task

### Service CPU Utilization 

  CPU utilized by Total Tasks / CPU Reserved by Total Tasks

### Service Memory Reservation 

  Number of Tasks X Memory Reserved by each Task


### Service Memory Utilization 
 
  Memory utilized by total Tasks / Memory reserved by total Tasks


## AutoScaling Process
 
1. Set CloudWatch Alarm to watch Service CPU Utilization
2. Set alarm to trigger if Service CPU Utilization goes up 70%
3. If Alarm Triggers, tell our ECS service 
4. When our service is notified of the alarm, tell it to add more Tasks to our
Service

## Automating Anything in AWS

1. Pick a Metric to Watch
2. Set a threshold
3. If alarm triggers, preform an action


## Auto Scaling ECS Services

Minimum # of Tasks is the Service must have

Desired # of Tasks is the 'ideal' number of Tasks to have running at once

Maximum # of Tasks is the max number of Tasks to be run when scaling or updating



