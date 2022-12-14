## APPLICATION DEPLOYMENT-AWS-ANSIBLE

<!-- PROJECT TABLE OF CONTENTS -->
<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">project Prerequisites</a></li>
        <li><a href="#installation">Project Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">project Usage</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## Knowing More About The Project

This project demonstrates the power building and hosting a PHP app within the AWs infrastructure/Ecosystem.


### This Project Was Built With

The project is built using,
* AWS services and resources
* Terraform infrastrure provisioning tool
* Ansible Configmanagment tool
* Apache webserver



<!-- GETTING STARTED -->
## Getting Started

### Pre-requisite
•	Login to your free AWs account
•	Create an IAM user and generate Access_key and secret_key

•	Setup the aws cli  with Required credentialsat the default region.

•	First download and install the terraform using this link

As a first step, install terraform (see: https://www.terraform.io/downloads)) and select your machine version if its windows 

and if its mac you can select accordingly and install the requirements:

•	Then download and install AWs CLI Installation requirements We support the AWS CLI on Microsoft-supported versions of 64-bit Windows.

Admin rights to install software

•	Install or update the AWS CLI To update your current installation of AWS CLI on Windows, download a new installer each time
you update to overwrite previous versions. AWS CLI is updated regularly. To see when the latest version was released, see the AWS CLI changelog on GitHub.
Download and run the AWS CLI MSI installer for Windows (64-bit):

https://awscli.amazonaws.com/AWSCLIV2.msi

•	Install Ansible using this link (https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)

### Installation

1. First Clone the project repo now

  $ git clone https://github.com/clement2019/app_deployment-aws_ansible
   ```
2. Install Terraform tool

3. Install Ansible tool


<!-- USAGE EXAMPLES -->
## Usage

As fas as hosting the PHP application is concerned it separated into 3 parts.

### Part 1: Provisioning the Infrastructure Resopurces to use

This infrastructure and its resources are provsioned within AWS ecosystem using Terraform tool.

1. Change directory into the infrastructure folder in the project cloned repository.
2. The following commands shpould be be run respectively
    - terraform init
    - terraform plan
    - terraform apply

The above will authomatically provision the required infrastructure resources and while  shotting out the EC2 instance public IP
as the output.

### Part 2: The second is very critail as well it involves installation of the PHP application

### Part 3: This part is equally critical because i build an PHP application for it to wok it requires a dependency called Apache webserver and that has to be installed as requitred software on the Aws Ec2 instance just provsioned while the application database will be MySql all these will be done using Ansible.

1. Originally inside inventory hosts file in the ansible directory /etc/ansible/hosts  we can store all the ip addresses but for this project we wont go that route,thwr is actually an inventory.yml file i created inside the ansible directory and replace 0.0.0.0 with the public IP copied from the Ec2 instance provisioned in part 1.
2. Replace the contents of the ./ansible/secrets/ssh.private with your private key. 
This is the private key corresponding to the public key used in Part 1 while provisioning the infrastructure using terraform.
3. Then run the ansible playbook using the below command
    - ansible-playbook -i inventory.yml application.yml

### Part 3: No to run into uncessary cost it is advisable we destroy all the resources so far created
for the application

By running the below command to tear down the application.

    - terrafrom destroy
