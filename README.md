# ansible
4.Server Setup using Ansible
### Commands to install Ansible to your EC2 instance

#### SSH into your EC2 instance:
    -Open a terminal or command prompt on your local machine.
    -Use the SSH key associated with your EC2 instance to connect:

         ssh -i path/to/your/key.pem ec2-user@your-ec2-instance-public-ip

#### Update the system:
    -Update the package lists and upgrade existing packages:
         sudo yum update -y

#### Installing Ansible
    -nstall the EPEL (Extra Packages for Enterprise Linux) repository:
         sudo yum install epel-release -y

    -Install Ansible using yum package manager:
         sudo yum install ansible -y

#### Verifying Installation
     -Check the Ansible version to ensure it's installed correctly:
          ansible --version


###Running Ansible playbook on EC2 instance

#### Create an Ansible playbook:
    -Create a new YAML file with a .yml extension (e.g., playbook.yml).
    -Open the file in a text editor.
    -Define the tasks and configurations you want to apply to the EC2 instance using Ansible modules and YAML syntax.
    -Save the playbook file.

#### Configure the inventory file:
    -An inventory file lists the hosts (EC2 instances) on which Ansible will run the playbook.
    -Create a new inventory file (e.g., inventory.ini).
    -Open the file in a text editor.
    -Add the EC2 instance(s) information in the following format:
	
        [group_name]
        host1 ansible_host=<public_ip_address> ansible_user=<username> ansible_ssh_private_key_file=<path_to_ssh_key>
    -Replace 'group_name', 'host1', <public_ip_address>, <username>, and <path_to_ssh_key> with the appropriate values. You can create multiple groups and add 
     more hosts if needed.

#### Test the connection:
    -Run the following command to test the connection with the EC2 instance(s):
        
         ansible -i inventory.ini group_name -m ping
    -Replace 'inventory.ini' with the path to your inventory file, and 'playbook.yml' with the path to your playbook file.
    -Ansible will connect to the EC2 instance(s) specified in the inventory file and execute the tasks defined in the playbook.

#### Monitor the playbook execution:

    -Ansible will display the output of each task as it runs.
    -Once the playbook execution completes, you'll see a summary of the executed tasks and their status.

#### Ansible script information
This ansible script will do below deployment

    -In Install Docker role
         -Update package
         -Install necessary pakages for docker installation
         -Install DockerHow to run the ansible script
    -Change hosts as per requirement in host file hosts
         -Run the script
               ansible-playbook server_setup.yml -i hosts
