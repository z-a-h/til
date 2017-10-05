# ECS Services 

## What Services Do

1. Set up Tasks from Task Definitions on the best suited Container Instance
  - Same as Running a Task

2. Monitors our Tasks and reports back metrics
  - Can be paired with CloudWatch Alarms and Actions 

3. Keeps the number of Tasks we specify always up and running
  - Specify the number of tasks running
  - Replace any failing tasks
  - Can set Min % of Tasks to be Healthy 
  - Can set Max % of Tasks that can be live
 
4. Updates our Tasks by handing them revised Task Definitions
  - Can update without having a service outage by add/removing incrementally 

5. Scales In/Out tasks based on customer demand
  - Use Cluster and Service CloudWatch metrics to trigger scaling 

6. Distribute the demand evenly to all Tasks via a Load Balancers
  - Must use Elastic Application Load Balancer
