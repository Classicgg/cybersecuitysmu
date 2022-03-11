# cybersecuitysmu
Elk Stack Project
![ELlk Stack Deployment](https://user-images.githubusercontent.com/101211313/157756291-9757ecdd-7035-4312-8737-8443957d14a0.jpg)
These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook (.yml) file may be used to install only certain pieces of it, such as Filebeat.

The following ansible-playbooks are needed to create and install DVWA and the ELK-server

my-playbook.yml - used to install DVWA servers
elk-playbook.yml - used to install ELK Server
filebeat-playbook.yml - Used to install and configure Filebeat on Elk Server and DVWA servers
metricbeat-playbook.yml - Used to install and configure Metricbeat on Elk Server and DVWA servers
This document contains the following details:

Description of the Topology
Access Policies
ELK Configuration
Beats in Use
Machines Being Monitored
How to Use the Ansible Build
Description of the Topology
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network. Load Balancing ensures availability to the web-servers which is the availability aspect of security in regards to the CIA Triad.

What is the advantage of a jump box? The main advantage of using a JumpBox is having one origination point for administrative tasks. This ultimately sets the JumpBox as a Secure Admin Workstation (SAW). In order to conduct administrative tasks administrators are required to access the JumpBox before accessing the other servers.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.

Filebeat watches for log files/locations and collect log events. (Filebeat: Lightweight Log Analysis & Elasticsearch)
Metricbeat records metrics and statistical data from the operating system and from services running on the server (Metricbeat: Lightweight Shipper for Metrics)
The configuration details of each machine may be found below.

Name	Function	IP Address	Operating System
Jump Box	Gateway	10.1.0.7	Linux (Ubuntu 18.04 LTS)
Web-1	Web Server - Docker - DVWA	10.1.0.5	Linux (Ubuntu 18.04 LTS)
Web-2	Web Server - Docker - DVWA	10.1.0.6	Linux (Ubuntu 18.04 LTS)
ELK-Server	ELK Stack	10.0.0.4	Linux (Ubuntu 18.04 LTS)
Access Policies
The machines on the internal network are not exposed to the public Internet.

Only the Jump Box Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

Personal IP Address
Machines within the network can only be accessed by SSH.

The ELK-Server is only accessible by SSH from the JumpBox and via web access from Personal IP Address.
A summary of the access policies in place can be found in the table below.

Name	Publicly Accessible	Allowed IP Address
Jump-Box	No	Personal IP Address
Web-1	Yes Thru Load Ballancer	13.66.204.159 LB Public IP 10.0.0.4 - JumpBox
Web-2	Yes Thru Load Ballancer	13.66.204.159 LB Public IP 10.0.0.4 JumpBox
ELK-Server	No	SSH 10.0.0.4 - JumpBox HTTP Port 5601 Personal IP
Elk Configuration
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

The main advantage of automating the installation process is that we could deploy multiple servers easily and quickly without having to physically touch each server.
The playbook implements the following tasks:

Install Docker.io and pip3
Increases VM memory
Download and Configure elk docker container
Sets Published Ports

![Elkinstance](https://user-images.githubusercontent.com/101211313/157783626-ac4b69a4-7980-404c-b8c8-eb515e3786e5.jpg)


