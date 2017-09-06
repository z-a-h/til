# ATTRIBUTE-BASED ACCESS CONTROLL

ABAC defines access control granted to users via policies combining attributes
together. Sometimes referred to as Policy-Based Access Control (PBAC) or
Claims-Based Access Control (CBAC) on Microsoft.

## BENEFITS 

* Fine grained compared to Role-Based Access Control (RBAC)
* Can be evaluted using Boolean logic
* Attributes can be set-valued or atomic-valued
* Allows for Dynamic Control

## COMPONENTS 

### ARCHITECTURE 

The recommended architecture is broken into three points:
1. __Policy Enforcement Point__(PEP) 
  * Responsible for protecting the app & data covered by ABAC
  * Inspects requests and generates an authorization requests to send to PDP.
2. __Policy Deciscion Point__(PDP)
  * Brain of architecture
  * Evalutes incoming requests against policies it has been configured with
  * May use PIPs to retrieve metadata
  * Returns a Permit or Deny deciscion 
3. __Policy Information Point__(PIP)
  * Bridges the PDP to external sources of attributes, such as database or LDAP

### ATTRIBUTES 

Attributes can be about anything or anyone, but generally fall into four
categories or grammatica functions
1. __Subject Attributes__
  * Describes the user attempting to access something
  * Examples: role, department, job title
2. __Action Attributes__
  * Describes te action being attempted by the subject
  * Examples: read, delete, view, write, update
3. __Resource Attributes__
  * Describes the object the subject is acting upon
  * Examples: Object Type(Medical Record, Bank Account), Team, Location
4. __Contextual Attributes__
  * Describes environemntal attributes related to a dynamic aspect of the scenario
  * Examples: Time of Access, Payment Status, Computed but not stored attributes

### POLICIES

Polices are statements that group attributes together to express what is or is
not authorized. Policies can be granting or denying. They can also be scoped
locally or globally or override other policies.

Examples:
1. A user can view a story if they are a part of the team writing the story.
2. A user can add a member to a team if they are the team owner or team admin.
3. No access for any user after 4:20pm

ABAC is powerful because it allows for as many policies as needed to cater to
different circumstances.

[SOURCE](https://en.wikipedia.org/wiki/Attribute-based_access_control)

