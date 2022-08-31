# NACL Vs Security Groups


## NACL

NACLs are stateless firewalls which work at Subnet Level, meaning NACLs act like a Firewall to an entire subnet or subnets. A default NACL allows everything both Inbound and Outbound Traffic. Unlike Security Groups, in NACLs we have to explicitly tell what to deny in Inbound and Outbound Rules. There’s no Implicit Deny in NACL.


- NACL can be understood as the firewall or protection for the subnet.
- These are stateless, meaning any change applied to an incoming rule isn’t automatically applied to an outgoing rule.
- Multiple subnets can be bound with a single NACL, but one subnet can be bound with a single NACL only, at a time

### Example

If a request comes through port 80, it should be explicitly indicated that its outgoing response would be the same port 80.


## Security Groups

- Security group can be understood as a firewall to protect EC2 instances.
- These are stateful, which means any changes which are applied to an incoming rule is automatically applied to a rule which is outgoing.
- Security groups are associated with an instance of a service. It can be associated with one or more security groups which has been created by the user.
  
### Example

If the incoming port of a request is 80, the outgoing response of that request is also 80 (it is opened automatically) by default.


## Use Case Example

Let’s say you have allowed SSH Access of an Instance to a User in Dev Team and he’s connected to it and actively accessing it and for some reason(realizing that the user is involved in some malicious activity) you wanted to remove his SSH access.

In this case you have two choices — 1) Remove SSH inbound allow rule of that user in the Security Group Inbound Rule. 2) Add an NACL Rule explicitly denying traffic from his IP address. If you go with the first one, he would not lose his SSH connection, this is due to the connection tracking behavior of Security Groups. If you go with the latter choice, NACL would immediately block his Connection. So in this case, it’s better to use a NACL Deny Rule rather than deleting a Security Group allow Rule.