# ECS Task Definitions 

A specification of what is required to set up Containers on Container Instances.
It defines each of the containers, their cpu, memory, ports, etc. 

Task Definitions can be used to either run a specific task, or to create a
service.

The Task Definitions tell the Cluster how to setup the containers on EC2 and how
many containers to setup. 

## Running ECS Tasks

Gives a Cluster a Task Definition and puts the tasks on container instances.
Running tasks are good for cron jobs or other one off actions.

## Task Placement Strategies 

1. AZ Balanced Spread
 - Spreads tasks evenly across AZ and evenly among instances in each AZ. Good
   for fault tolerance.

2. AZ Balanced Binpack
 - Spreads tasks evenly across AZ, but within AZs it tries to use the least
   amount of instances. It does this to optimize cost. 

3. Binpack
 - Same as 3, but doesn't care about AZ

4. One per Host

5. Custom 
