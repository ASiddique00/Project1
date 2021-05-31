## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](https://github.com/ASiddique00/Project1/blob/main/Diagrams/Network%20Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - Install-elk.yml (https://github.com/ASiddique00/Project1/blob/main/Ansible/Install-elk.yml.txt)

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly avaiable, in addition to restricting in-bound access to the network.
- Load balancing ensures Availabitlity, Web traffic and Websecurity.
- The jumpbox ensures to minimize the any cyber attacks by ensuring remote connections to the cloud network through a single virtual machine via access control and security.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the jumpbox and system network.
- Monitors the file changes to VM machine
- Collects the metric records from the machine and services running on the server machine

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

|Name         | Function    | IP Address    | Operating System |
|-------------|-------------|---------------|------------------|
| Jump Box    | Gateway     |52.189.217.190 | Linux            |
|             |             |10.0.0.4       |                  |
|Web-1        | Webserver   |10.0.0.5       | Linux            |
|Web-2        | Webserver   |10.0.0.6       | Linux            |
|Web-2        | Webserver   |10.0.0.10      | Linux            |
|ELK Server   |ELK Server   |20.36.45.243   | Linux            |
|             |             |10.2.0.4       |                  |
|Load Balancer|Load Balancer|191.239.180.217| Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jumpbox provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 14.201.41.50

Machines within the network can only be accessed by jumpbox provisioner.
- Jumpbox. Public IP 52.189.217.190, Private IP 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes via SSH  (22)   | 14.201.21.50         |
|  Web-1   | No                  | 10.0.0.4             |
|  Web-2   | No                  | 10.0.0.4             |
|  Web-3   | No                  | 10.0.0.4             |
|ELK Server| Yes via HTTP (5601) | 14.201.21.50         |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- It helps in quick and easy deployment of multiple apps. No manual restarting of the services with the help of automation script. Tasks are written in script which are deployed via playbook which is more efficient and helps in faciliating OS and applications updates.

The playbook implements the following tasks:
- Install docker.io
- Install pip3
- Install Docker python module
- Increase virtual memory
- Download and launch a DVWA docker container
- Enables the Docker service

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](https://github.com/ASiddique00/Project1/blob/main/Diagrams/sebp-elk761.PNG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 (10.0.0.5)
- Web-2 (10.0.0.6)
- Web-3 (10.0.0.10)

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat allow us to collect log events and Metricbeat allow us to collect metrics and system statistics information.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to Anisble container node.
- Update the /etc/ansible/hosts file to include...
- $ansible-playbook install_elk.yml elk
- $ansible-playbook install_filebeat.yml webservers
- $ansible-playbook install_metricbeat.yml webservers 
- Run the playbook, and navigate to Kibana (http://20.36.45.243:5601/app/kibana) to check that the installation worked as expected.

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
