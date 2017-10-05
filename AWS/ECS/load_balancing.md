# Application Load Balancers

Classic LBs spread traffic between instances 
Application LBs spread traffic between Tasks

## Components 

- The Load Balancer 
  * Central point for attaching options and configs

- Target Groups
  * Common group of apps or tasks

- Listeners 
  * What ports and protocols 

- Listener Rules 
  * What do to when traffic hits a particular listener

Can have more than one target group or service 

The Listener rule priority numbers are inversely related to their 


1. Create a Target Group

2. Create an Application Load Balancer, make a Listener & Listener Rule that
points to the Target Group

3. Register the Application Load Balancer and Target Group with the ECS Service 


