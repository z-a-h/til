# IAM Overview

IAM stands for Identity Access Management.

## Terminology

*Principal*: The subject/policy holder

*Action*: The abilities the policy grands the subject

*Conditions*: The conditions where the policy is or is not valid

*Resources*: The AWS elements that are able to be accessed 

## Main Concepts 

### Policies 

Set of rules that defines the conditions under which a AIM principal can
take actions on specific resources.

### Users

A person or resource which policies can be attached to.
Users without a policy might be able to access the CLI or console, but won't be
able to do anything.

### Groups

Policies defined for sets of Users. Rather than attaching individual policies to
a User, a group can have it's policies defined and Users can be added to the
Group.

### Roles

Roles allow other services, like EC2, to act on other AWS resources. 


