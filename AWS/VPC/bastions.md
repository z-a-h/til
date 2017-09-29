# Bastion Server

A bastion server is server in the public subnet that is used to access our
private subnet. 

For example, to check out the logs on a D  in the private subnet, we'll have to
SSH into the bastion server.

## Creating a Bastion Server

1. Create the Bastion Security Group

Create a new Security Group for accessing the bastion server. Connect the
security group to the VPC.  Edit the Inbound rules of the Security group to only
allow SSH access from your personal IP address and append with `/32`, meaning
that exact IP address, rather than a range.

2. Create an EC2 Key Pair and set it up on our local machine 

On the EC2 dashboard, create a new pair of SSH keys, and name the after the VPC.
After creation, the keys are automatically downloaded.  Move the keys to a safe
location and run `chmod 400 <ssh-keys-name>.pem` to change their access to read
only. 

Use `ssh-add -K ./<ssh-keys-name>.pem` to store the keys so you don't have to
manually use them. 

3. Create a Bastion Server and Launch into our VPC's Public Subnet

Create a new EC2 instance with the default Amazon Linux AMI. Then use the
standard `t2.micro` instance.  Configure the instance to connect to our VPC
network, and to the public subnet in availability zone A. 

Add tags to the instance with key `name` and a value identifying the instance as
a bastion instance for the VPC. Then attach the instance to the security group
created for the bastion server. 

Finally, select the recently created SSH key pairs as the keys for the newly
created instance. 

4. SSH into the Bastion and do a couple administrative tasks

When the instance state is running, select the Instance and copy the IPv4 public
IP address. In the terminal, run `ssh -A ec2-user@<IPv4-address>`.  The `-A` tag
tells SSH to take our key pair with us into the bastion server, so it can be
used to access other servers from inside the ec2 instance. 

Run `sudo yum update` to update the packages. 

