# CyberSec1-Brian
This repository is a collection of the scripts and network diagrams created in Cyber Sec Bootcamp class
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

See Screenshots

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Filebeat Config file may be used to install only certain pieces of it, such as Filebeat.

See Filebeat Playbook

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly redundant, in addition to restricting public access to the network.
- Load balancers protect the network from denial of service attacks by controlling the inbound traffic and it’s distribution to the network. Using a jump box is an example of a secure architecture technique called fanning in, it allows us to focus more on one or two nodes instead of having to monitor an entire network. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system logs.
- Filebeat is used to collect logs from specific systems like Apache or mySQL
- Metricbeat records the statistics and metrics from the specific systems on the network 

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1     |   Server    |   10.0.0.5      |   Linux          |
| Web-2     |   Server    |  10.0.0.6      |  Linux            |


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
	
73.164.105.86

Machines within the network can only be accessed by Jump Box
- Jump Box - IP 40.122.51.219

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes  | 73.164.105.86    |
|    Web-1      |    No       |    40.122.51.219      |
|     Web-2     |     No      |        40.122.51.219       |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- It allows for a more rapid configuration and one that is repeatable for other iterations or versions.

The playbook implements the following tasks:
- Install docker.io
- Install python-3
- Install docker python module

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

See Docker ps screenshot

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5 & 10.0.0.6

We have installed the following Beats on these machines:
- Filebeats & Metricbeats

These Beats allow us to collect the following information from each machine:
- Filebeat is able to collect the system logs from the virtual machines setup in the virtual network, these are logs specific to the systems that are installed on the VMs. Metricbeat retrieves information from the same place as Filebeat but instead of logs they are system metrics and statistics. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the ELK Playbook file to /etc/ansible.
- Update the ansible.cfg file to include the ip addresses for the host and allow port connections to 5601. 
- Run the playbook, and navigate to http://13.66.230.108:5601/app/kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?
