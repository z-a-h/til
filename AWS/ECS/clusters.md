# ECS Clusters

## Basic Terminology 

*Cluster*: Logical group of EC2 instances that can hold containers.

*Container Agent*: Manages the state of containers on a single EC2 instance. Acts
as a proxy for the Docker Daemon on the EC2 instance

*Container Instance*: An EC2 instance that has a Container Agent and is a part 
of a cluster 

## Overview 

A cluster is a group of EC2 instances that each have an ECS Container Agent to
point to a cluster. Basically a cluster is a group of Container Instances

Clusters are valuable because they are able to manage instances across multiple
availability zones. 


## Creating a Cluster

1. Create an empty cluster in the AWS Console
2. Create IAM Roles for EC2 Instances
3. Set up EC2 Instances w/ ECS Container Agent
  - Either Manually Install
  - Or Use ECS Optimized AMI
4. Point Agent to Cluster
  - Add `ECS_CLUSTER=NAMEOFCLUSTER` in `ecs.config` at `etc/ecs/ecs.config`
5. Launch Instance

