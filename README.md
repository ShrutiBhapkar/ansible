# Server Setup using Ansible

This Ansible script automates the setup of a server, including the installation of Docker.

## Prerequisites

- SSH access to your EC2 instance(s)
- Ansible installed on your local machine

## Installation

1. SSH into your EC2 instance:

```bash
ssh -i path/to/your/key.pem ec2-user@your-ec2-instance-public-ip
Update the system:
bash
Copy code
sudo yum update -y
Install Ansible:
bash
Copy code
sudo yum install epel-release -y
sudo yum install ansible -y
Verify the installation:
bash
Copy code
ansible --version
Running the Ansible Playbook
Create an Ansible playbook:

Create a new YAML file with a .yml extension (e.g., playbook.yml).
Define the tasks and configurations you want to apply to the EC2 instance using Ansible modules and YAML syntax.
Save the playbook file.
Configure the inventory file:

Create a new inventory file (e.g., inventory.ini).
Add the EC2 instance(s) information in the following format:
php
Copy code
[group_name]
host1 ansible_host=<public_ip_address> ansible_user=<username> ansible_ssh_private_key_file=<path_to_ssh_key>
Replace 'group_name', 'host1', <public_ip_address>, <username>, and <path_to_ssh_key> with the appropriate values. You can create multiple groups and add more hosts if needed.
Test the connection:

Run the following command to test the connection with the EC2 instance(s):
bash
Copy code
ansible -i inventory.ini group_name -m ping
Replace 'inventory.ini' with the path to your inventory file and 'group_name' with the appropriate group name.
Run the Ansible playbook:

Execute the following command to run the playbook on the EC2 instance(s):
bash
Copy code
ansible-playbook -i inventory.ini playbook.yml
Replace 'inventory.ini' with the path to your inventory file and 'playbook.yml' with the path to your playbook file.
Monitor the playbook execution:

Ansible will display the output of each task as it runs.
Once the playbook execution completes, you'll see a summary of the executed tasks and their status.
Ansible Script Information
This Ansible script performs the following deployment steps:

Install Docker role:
Update packages.
Install necessary packages for Docker installation.
Install Docker.
