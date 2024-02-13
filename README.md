# AWS-NETWORKING-IPLEMENTATION
 ## VPC , Subnets , IG , NAT , Routing 

# VPC(Virtual Private Cloud)

 ## Creating a new VPC

Go to VPC page

VPC resource choose (VPC only)

Give it name (first-vpc)

In IPv4 CIDR manual block info choose IPv4 manual input

Input the IPv4 provided

In IPv6 CIDR  block info select no IPv6 CIDR block

 Now create the VPC by clicking on Create vpc button

  Results.

![image](https://github.com/NANA-2016/AWS-NETWORKING-IPLEMENTATION/assets/141503408/0b55303d-68b7-42fb-ac18-18c533934786)

Once a VPC is created,it is assigned a VPC id and a Route table is also creates as shown on the screeensot below .

![image](https://github.com/NANA-2016/AWS-NETWORKING-IPLEMENTATION/assets/141503408/e41ff76c-ebfb-4f99-89bf-f6b3fdc9c7cd)

# Subnets

## Creating and configuring Subnets.

On VPC page,go to subnets ->create subnet ->click on vpc already created -> click on create subnet. (if you have several subnets to create, instead of clicking on the create subnet button first, click on add new sunet till you are done adding all your subnets then you can click on create subnet.

Also ensure youspecify the cidr block and Available zone for the subnet because if you dont choose a zone ,it will be randomly allocated by AWS

Expected output on subnets page.

![image](https://github.com/NANA-2016/AWS-NETWORKING-IPLEMENTATION/assets/141503408/5722658c-7f22-438d-92f3-33714fd2e136)

## NB:

Creating a Public subnet Procedure.(for resources that need connection to the internet)

Subnet> create subnet>Attach an intenet gateway>update the route table associated with this subnet(to allow flow of traffic to and from the internet)

Creating a Private subnet Procedure.(for resources you dont want to expose to the internet)

Subnet> create subnet(route table to these subnet dousnt allow direct traffic to and from the internet)

# Internet gateway and Routing table

  ## Internet Gateway.

   Connects VPC to the internet.

    These are route that allows the subnets to start operating as public subnets. Also you need to route table towards IGW using the public IP assisgned to AWS resourse eg an instance.

    Internet Gateway creation.

    vpc>Internet gateway>create internet Gateway> give it a name> click on create gateway at the end of the page.

     You Later nned to attach the IGW to yor VPC by going on the  gateways page>select the gateway crated> click on the dropdown on the action button and click attach to VPC button> select the VPC you want to 
     
     make an attachment to and click on attack internet gateway at the endof the page.

      The IGW state will be attached as shown on the screenshot below.

     ![image](https://github.com/NANA-2016/AWS-NETWORKING-IPLEMENTATION/assets/141503408/9d45c89f-1a5a-4125-93d6-273c99e29e95)

## Routing table.

It directs movement of data  on the VPC

#### Steps of creating and configuring route table

vpc>route table>create route table>NAME>VPC to use>create route table

Confuguring the route table 

vpc>Route tables>(rtb)>Edit routes>destination (0.0.0.0.0/0)> Target Internet (Gateway)SELECT IGW you wnat to edit>save changes

![image](https://github.com/NANA-2016/AWS-NETWORKING-IPLEMENTATION/assets/141503408/b0eae279-8396-4216-84e1-b439e93f7d68)


vpc>Route tables>(rtb)>subnet associations>Edit  subnet association(public subnets)>Save associations.

![image](https://github.com/NANA-2016/AWS-NETWORKING-IPLEMENTATION/assets/141503408/f5d2bffc-b62e-485d-aa75-ce6f30dede97)


After these configuration, The VPC is ready and you can run an EC2 instance in public subnets if they nned internet or private subnets if they dont.

![image](https://github.com/NANA-2016/AWS-NETWORKING-IPLEMENTATION/assets/141503408/a5b2dd5f-ce94-4e7b-9648-074c4dfeee09)

## NAT Gateway and Private Subnets

 Helps the private subnets that should not be exposed to the internet  to be able to have access to the internet eg for updates and downloads and prevents anything from the internet from getting into the private subnet.

 #### Creating a Network Address Translation(NAT) gateway.

 VPC>NAT GATEWAYS>Create NAT Gateway>Natgateway settings> give a name to the NAT gateway>select the subnet you want to link it upto> Allocate an elastic IP(As it is a requirement here)>create NAT gateway.

![image](https://github.com/NANA-2016/AWS-NETWORKING-IPLEMENTATION/assets/141503408/852471a2-e662-4c3d-9cb0-e6479749434e)

vpc>Route tables>(rtb)>Edit routes>destination (0.0.0.0.0/0)> Target (nat)SELECT nat you wnat to edit>save changes

![image](https://github.com/NANA-2016/AWS-NETWORKING-IPLEMENTATION/assets/141503408/64f9d702-fcbb-4a8a-bff6-bb368b9e75d7)

vpc>Route tables>(rtb)>subnet associations>Edit  subnet association(private subnet)>Save associations.

![image](https://github.com/NANA-2016/AWS-NETWORKING-IPLEMENTATION/assets/141503408/83452847-3887-4b60-878d-9bdad988b4f3)

 





    



 
