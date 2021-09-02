# YAML-Bash-Script
Ansible YAML for Cloud Security and Bash Scripts for Linux System Administration. Plus Network Diagrams
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.


https://drive.google.com/file/d/1kxLTfT2JhzOVJHoRToULtntAbfrZYqhZ/view?usp=sharing

install_elk.yml

https://drive.google.com/file/d/1PLIXOBaLz3JwCcZ2CSV-rtztETWlXqUC/view?usp=sharing


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

  Enter the playbook file._

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting inbound access to the network.
Load balancers process incoming traffic to be shared by both vulnerable web servers. Jump box access control will ensure that only authorized users - namely, ourselves - will be able to connect in the first place. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the file systems of the 
What does Filebeat watch for? VMs on the network
What does Metricbeat record? CPU usage; attempted SSH logins; sudo escalation failures; etc.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway            | 10.0.0.9   | Linux (Ubuntu)      |
| DVWA 1    | Web Server       |  10.0.0.10 | Linux  (Ubuntu)          |
| DVWA 2    | Web Server       |  10.0.0.8   | Linux      (Ubuntu)      |  
| ELK VM    | Monitoring         | 10.1.04     | Linux    (Ubuntu)        |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from home network IP.


Machines within the network can only be accessed by _____.
They can only be accessed from the home network and by each other. The DVWA 1 and DVWA 2 VMs send traffic to the ELK server. 

A summary of the access policies in place can be found in the table below.

| Name             | Publicly Accessible | Allowed IP Addresses |
|-----------------|-----------------------|----------------------|
| Jump Box      | Yes                          | [Public IP]   |
|  DVWA 1        |  No                          |  10.0.0.1 - 254     |
|  DVWA 2        |  No                          |   10.0.0.1 - 254    |
|  ELK  VM       |  No                          | 10.1.0.1 - 254      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it minimizes the number of potential errors and also help save time. 
What is the main advantage of automating configuration with Ansible?
Using automating configuration with Ansible help IT administrators to avoid the daily harwork, help them save time, and use the free time that they have on important task that will help and add values to the company. Ansible offers help for coordinating turn of events and tasks in contemporary test-driven application plan. It gives a steady climate to the turn of events and tasks group, consequently prompting smooth organization. Ansible robotization helps impressively with the portrayal of Infrastructure as Code (IAC).  

The playbook implements the following tasks:
* Install Docker
* Configure Webserver
* Install Elk Sever
* Install Filebeat
* Install Metricbeat 

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
https://drive.google.com/file/d/1nf3S9Psdg9LOL59B2-S-jsBWYTqFNSv2/view?usp=sharing

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- DVWA 1 10.0.0.10 
- DVWA 2 10.0.0.8

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat


These Beats allow us to collect the following information from each machine:
* Filebeat permits the ELK Server to screen and save records of logs while providing a graphical user interface to monitor the data.
* Metricbeat permits the ELK Server to screen important utilization measurements like CPU use, memory use, and screens what is coming all through the worker at indicated minutes on schedule. After the screenings all the information are sent to Elasticsearch and Logstash.


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: The Jump Box

SSH into the control node and follow the steps below:
- Copy the playbook file to Ansible Control Node.
- Update the  file to include...
- Run the playbook, and navigate to the VM where it has been installed to check that the installation worked as expected.

Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?
YAML (.yml) files are playbook files that can be run with Ansible. Typically, it's copied into a container where ansible is installed to be deployed.

- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
You have to update the host file in order to run the playbook on a specific machine. You can do that by typing this command: ansible-playbook install_elk.yml elk and ansible-playbook install_filebeat.yml webserver

* $ cd /etc/ansible 
* $ nano hosts (to update the hosts file and add the webservers IP and the Elk IP)
* [webservers]
  10.0.0.7
  10.0.0.8
* [elk]
  10.1.0.4

* Update ElkServer-IP inside of each configuration file
   * Replce Kibana localhost with ELK Server local IP (10.1.0.4)
   * Replace Elasticsearch localhost with ELK Server local IP (10.1.0.4)
   

- Which URL do you navigate to in order to check that the ELK server is running?
You have to run: curl http://[Elk-Public-IP]:5601. (That is the address or domain for KIbana)

As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

sudo docker start (the container name)

sudo docker ps

sudo docker exec -ti (the container name) bash

sudo ansible-playbook ( the .yml file you would like to run)
