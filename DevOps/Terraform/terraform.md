# Terraform AWS Seed

Terraform Common AWS Infrastructure Seed

## Install Terraform in linux instance
    1. download Terraform 
    wget https://releases.hashicorp.com/terraform/1.0.2/terraform_1.0.2_linux_amd64.zip
    
    2. Unzip File
    unzip terraform_1.0.2_linux_amd64.zip
    
    3. Move terraform folder to bin folder
    mv terraform /usr/local/bin/

    4. check version
    terraform -v

## Create IAM user for Terraform script
    1. Create user with Access Type `Programmatic access`
    2. Managed policy : AdministratorAccess
    3. Download csv for `Access key ID` and `Secret access key`

## configure IAM user in linux machine
    1. Run commond : aws configure
    2. provide user details

    AWS Access Key ID [None]: ****
    AWS Secret Access Key [None]: ****
    Default region name [None]: us-east-2 (Same as ec2 region)
    Default output format [None]: text

## create demo_instance
mkdir demo_instance

## go to inside folder
cd demo_instance

## create file provider.tf
[ec2-user@ip-10-10-01-01 demo_instance]$ cat  provider.tf
provider "aws" {
region = "us-east-2"
}

## create file webservice.tf
[ec2-user@ip-10-10-01-01 demo_instance]$ cat webservice.tf

resource "aws_security_group" "webservice_sg" {
ingress {
from_port = 80
to_port = 80
protocol = "tcp"
cidr_blocks  = ["0.0.0.0/0"]
}
ingress {
from_port = 22
to_port = 22
protocol = "tcp"
cidr_blocks  = ["0.0.0.0/0"]
}
egress {
from_port = 0
to_port = 0
protocol = "-1"
cidr_blocks  = ["0.0.0.0/0"]
}
}

## create file ec2.tf
[ec2-user@ip-10-10-01-01 demo_instance]$ cat ec2.tf

resource "aws_instance" "web_server" {
ami = "ami-0233c2d874b811deb"
instance_type = "t2.micro"
vpc_security_group_ids = ["${aws_security_group.webservice_sg.id}"]
tags {
Name = "created_server_by_terraform"
}
}

## run commond for creating new instance

1.  terraform init
2.  terraform validate [for validate script, it will show error if script is not valid]
3.  terraform plan
4.  terraform apply [Command is creating infrastructure based on provided script]
5.  terraform destroy [Command reverted all infrastructure which is created by script]

