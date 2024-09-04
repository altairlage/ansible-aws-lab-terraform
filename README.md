# Ansible and Semaphore lab deployed by Terraform in AWS

[![Ansible Badge](https://img.shields.io/badge/Ansible-E00?logo=ansible&logoColor=fff&style=for-the-badge "Ansible")](https://www.ansible.com/)
[![Semaphore CI Badge](https://img.shields.io/badge/Semaphore%20CI-19A974?logo=semaphoreci&logoColor=fff&style=for-the-badge)](https://semaphoreui.com/)
[![Terraform Badge](https://img.shields.io/badge/Terraform-844FBA?logo=terraform&logoColor=fff&style=for-the-badge)](https://www.terraform.io/)
![AWS](https://img.shields.io/badge/AWS-%23FF9900.svg?style=for-the-badge&logo=amazon-aws&logoColor=white)
![Amazon EC2 Badge](https://img.shields.io/badge/Amazon%20EC2-F90?logo=amazonec2&logoColor=fff&style=for-the-badge)


Lab developed to test and perform knowledge share for my team about Ansible, Semaphore, and Terraform. It shows several Terraform deployments in AWS. The intent is to exercise the most common deployments using Terraform.

This project contains several modules. Each module represents a lab, which deploys resources specific infrastructure or services setup. 
\
&nbsp;
\
&nbsp;


## basic_networking
This module deploys a basic AWS infrastructure, a VPC with some subnets, the CICD subnet to run some CICD services, a 3 tier subnet schema (public, middleware, and DB subnets), and the basic requirements to allow connectivity. 

### Architecture
Basic networking deployment architecture:
![Basic networking deployment architecture](/doc_resources/basic_networking_arch.png "Basic networking deployment architecture")
https://lucid.app/lucidchart/740b7a07-ecc3-4aa5-9e78-50ac4efa7627/view
\
&nbsp;
\
&nbsp;


## ansible_lab
Deploys a complete Ansible lab, including:
- 5 EC2 instances:
    - The Ansible control node in CICD subnet.
        - Setups Ansible and runs Semaphore service (with MySQL) via docker-compose.
    - 4 managed nodes in middleware subnet.
        - 2 in each AZ.
- A load balancer to expose the Semaphore service for remote configuration;
\
&nbsp;
\
&nbsp;


# Deploy commands
The deployment was developed in Terraform.
To run the deployment, you need to:

- Install terraform
    - In the host you're running the deployment
- Have a session created with AWS and have its credentials stored in your ~/.aws/credentials file. 

### Init
terraform init -backend-config=./env/us-west-2.tfbackend

### Plan
terraform plan -var-file=./env/us-west-2.tfvars

### Apply
terraform apply -var-file=./env/us-west-2.tfvars --auto-approve

### Destroy
terraform destroy -var-file=./env/us-west-2.tfvars --auto-approve
\
&nbsp;
\
&nbsp;

