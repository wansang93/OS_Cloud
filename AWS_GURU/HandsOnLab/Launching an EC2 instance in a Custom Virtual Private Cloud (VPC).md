# Launching an EC2 instance in a Custom Virtual Private Cloud (VPC)

- Link -> [사이트에서 직접 들어가야 함]

![lab_diagram_Launching_an_EC2_instance_in_a_Custom_Virtual_Private_Cloud_(VPC)](./images/lab_diagram_Launching_an_EC2_instance_in_a_Custom_Virtual_Private_Cloud_(VPC).png)

## 시나리오

AWS의 EC2 인스턴스로 Static Web 서버를 만들려고 합니다.

## Introduction

In this hands-on lab, we will launch EC2 instances in a custom VPC, complete with all the required networking configuration. This lesson walks through the architecture and gets us set up and ready to go.

## Solution

### Create Custom VPC

1. Create a VPC
   - Navigate to the VPC console.
   - Note: Do not use the VPC Wizard to create your VPC; instead, configure your VPC from scratch.
   1. Select Your VPCs.
   2. Click Create VPC, and set the following values:
      - HoLVPC, 10.0.0.0/16, No IPv6 CIDR block, Default Tenancy
   3. Click Create.

### Create Public and Private Subnets

Build two subnets for your VPC. One will be public to allow access from the Internet and one will be private. Ensure you are assignibg the valid CIDR blocks when creating your subnets.

1. Create Public Subnet
   1. Select Subnets.
   2. Click Create subnet.
   3. Enter the following values in order for Name, VPC, Availability Zone, and IPv4 CIDR Block.
      - sn-public-a, HoLVPC, us-east-1a, 10.0.1.0/24
   Note: Although the name of our subnet is hol-public-a, it is not actually public just yet. By definition a public subnet must have an Internet Gateway. In the next tasks, we will add an Internet Gateway so that instances in this newly created public subnet can access the Internet.

2. Create Private Subnet
   1. Click Create subnet.
   2. Enter the following values in order for Name, VPC, Availability Zone, and IPv4 CIDR Block.
      - sn-private-b, HoLVPC, us-east-1b, 10.0.2.0/24
   Note: By default, all subnets are private. If there is no route to the Internet via an Internet Gateway, instances running in the subnet can only be reached by other instances in the VPC.

### Create Routes and Internet Gateway

- Auto-assign public IPv4 address
  - Automatically request a public IPv4 address for instances launched into the public subnet.
  1. Select Subnets.
  2. Select sn-public-a, Actions, and Modify auto-assign IP settings.
  3. Enable Enable auto-assign public IPv4 address.

- Configure Internet Gateway
  - An internet gateway enables communication over the Internet.
  1. Select Internet Gateways, and click Create internet gateway.
  2. Set the name tag as hol-VPCIGW, and click Create internet gateway.
  3. Select the newly created IGW, click Actions and then Attach to VPC.
  4. Select HoLVPC and click Attach internet gateway.

- Configure Routing
  - Create a new route table for HoLVPC to tell traffic in the public subnet, sn-public-a, how to get to the Internet.
  Note: You may notice there is already a default route table created for you associated with your main network. This route allows traffic from the 10.0.0.0/16 network to pass to other nodes within the network, but it does not allow traffic to go outside of the network, such as, to the public Internet. Each VPC you create by default is associated with this main route table; therefore, the main route table shouldn't allow traffic out to the public Internet so we'll create a new one specifically for public Internet traffic.
  1. Click Route Tables.
  2. Click Create route table.
  3. Set the name tag as publicRT and the VPC as HoLVPC.
  4. Click Create.
  5. Click Close.
  6. Select your newly created route table.
  7. Click Routes tab.
  8. Click Edit routes, and Add route.
  9. Set the destination as 0.0.0.0/0, target as Internet Gateway, and select hol-VPCIGW.
  10. Click Save routes.
  11. Click Close.

- Associate with Subnets
  1. Select publicRT, and click the Subnet Associations tab.
  2. Click Edit subnet associations.
  3. Select sn-public-a.
  4. Click Save.

Great, now our public subnet will allow traffic within it to access the public Internet.
