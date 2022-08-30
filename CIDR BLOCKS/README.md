# CIDR Blocks

![VPC_Image2](https://user-images.githubusercontent.com/110179866/187457280-b58fa33d-e259-4653-b438-3476ad0a4edb.png)


- Classless Inter-Domain Routing (CIDR) block basically is a method for allocating IP addresses and IP routing. When you create a network or route table, you need to specify what range are you working in. "0.0.0.0" means that it will match to any IP address. Some IP addresses are specific, like 10.0.0.0, which will match to any IP address beginning with 10. With any IP address range, you can be more specific by using a suffix(something like /32 from your example). These allow the notation to specify number of bits to be used from Prefix(actual IP-range like 10.0.0.0). It represents the bit length of the subnet mask, as indicated above. The subnet mask is like masking when painting. You place a mask over what you DO NOT want to paint on.


### How to create a CIDR Block


Create a VPC with a 10.0.0.0/16 CIDR block using the following create-vpc command.

```aws ec2 create-vpc --cidr-block 10.0.0.0/16 --query Vpc.VpcId --output text```

The command returns the ID of the new VPC. The following is an example.

```vpc-2f09a348```

Using the VPC ID from the previous step, create a subnet with a 10.0.1.0/24 CIDR block using the following create-subnet command.

```aws ec2 create-subnet --vpc-id vpc-2f09a348 --cidr-block 10.0.1.0/24```

Create a second subnet in your VPC with a 10.0.0.0/24 CIDR block.

```aws ec2 create-subnet --vpc-id vpc-2f09a348 --cidr-block 10.0.0.0/24```

