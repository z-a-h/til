CASL 
=======

CASL is an authorization library based on the `cancan` ruby library.
It is focused around defining user abilities in a system rather than specific
roles.

Methods
-------

There are three methods used to check a users priveledges. 

### Can

Can defines an ability that a user is able to perform
`ability.can('update', 'Story')`
This returns boolean true if a user is permitted to complete the action

### Cannot

Cannot defines an ability that a user is not permitted to perform
`ability.cannot('update', 'Story')`
This returns boolean true if a user is not permitted to complete the action

### Throw Unless Can

This method throws a 'ForbiddenError' exception if an action is not permitted
by the user.
`ability.throwUnlessCan('delete', 'Story')`



