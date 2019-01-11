
## POC: Automating the Infrastucture creation process on AWS

## Purpose
The purpose of this task is to automate the creation of the AWS infrastructure 
## Version History

```
Version     Date            Remarks(s)
0.1         31-10-2018      Initial version.

```

## Prerequisites

To be able to execute the playbook/role the following requirements need to be in place:

- AWS account 
- Ansible server deployed
- source code (Bitbucket)
- Requires Ansible 2.4 or newer

## Procedure

The entire flow is been setup in three parts:

1] Setting up the AWS infrastructure and deploying two EC2 instances for the same.

The role `aws-infra` is called to setup the aws infrastructure.The role performs the following task
  a) Creation of VPC
  b) Creation of Subnet 
  c) Creation of InternetGateway
  d) Creation of Route table
  e) Creation of Security group
  f) Creation of keypairs
  g) Creation of EC2 

 The way to execute the role is by calling the playbook `infra_setup.yml`
```
 ansible-playbook infra-setup.yml 
```

As the infra creation is success it creates the following:-
 1.VPC 
 2.Subnets in VPC which is created 
 3.Internet Gateway and it is attached to the VPC created.
 4.Route teable of VPC.
 5.Security group.
 6.Keypair to access the Ec2 instance and keypair is also saved on ansible machine to access the machine later.
 7.Ec2 instance is created usong all the resources created above.

## Security Implemented:

AWS infrastructure is setup, so the setup is installed in our VPC and the firewall is applied using the security groups by limiting the ports and accessability.

Using the private keys for the authentications with the servers.(no username and passwords)

All the variables and credentials are encrypted using the Ansible Vault Encryption feature.(AES 256 Encryption)

