# Elk-Stack-Project-1
Cybersecurity bootcamp Elk Stack Project 1. 
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Diagrams/Network Diagram.png 

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the yml and config file may be used to install only certain pieces of it, such as Filebeat.

  Ansible/install-elk.yml.txt

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly efficient, in addition to restricting traffic to the network.
-What aspect of security do load balancers protect? 
•	Load balancers protects the system from DDoS attacks by shifting traffic.
What is the advantage of a jump box?
•	The advantage of a jump box is to give access to the user from a single node that can be secured and monitored.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
-What does Filebeat watch for?
•	It watches for any information in the file system which has been changed and when it was changed. It also watches for log files/locations and collects log events.
- _TODO: What does Metricbeat record?
•	Collects metrics and statistics and ships them to the output you specify. It also records metric and statistical data from the operating system and from services running on the server.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name       | Function   | IP Address | Operating System |
|------------|------------|------------|------------------|
| Jump Box   | Gateway    | 10.1.0.4   | Linux            |
| Web-1      | Server     | 10.1.0.6   | Linux            |
| Web-2      | Server     | 10.1.0.7   | Linux            |
| Elk-Server | Elk Server | 10.0.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- Add whitelisted IP addresses_ Public IP address that changes everytime VM is turned on/off eg: 20.222.123.175

Machines within the network can only be accessed by SSH.
-Which machine did you allow to access your ELK VM? What was its IP address? JumpBox VM, its private IP address (Vnet IP)-10.1.0.4

A summary of the access policies in place can be found in the table below.

| Name       | Publicly Accessible | Allowed IP Address |
|------------|---------------------|--------------------|
| Jump Box   | No                  | 10.1.0.4           |
| Web-1      | No                  | 10.1.0.6           |
| Web-2      | No                  | 10.1.0.7           |
| Elk-Server | No                  | 10.0.0.4           |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible?
•	Allows you to deploy to multiple servers using a single playbook 


The playbook implements the following tasks:
•	Install docker.io
•	Install Python-pip
•	Install docker container
•	Launch docker container: elk
•	Command: sysctl -w vm.max_map_count=262144

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Diagrams/Project 1 Elk.JPG

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
-List the IP addresses of the machines you are monitoring— Web-1(10.1.0.6) Web-2(10.1.0.7) 

We have installed the following Beats on these machines:
-Specify which Beats you successfully installed- Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- - Filebeat monitors log files or locations you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
- Metricbeat collects metrics from the operating system and from services running on the server.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to /etc/ansible.
- Update the configuration file to include webservers and ElkVM private IP address
- Run the playbook,and navigate to ElkVM to check that the installation worked as expected.

_Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it? /etc/ansible/file/filebeat-configuration.yml 
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? dit the /etc/ansible/hosts file to add webserver/elkserver ip addresses
- _Which URL do you navigate to in order to check that the ELK server is running? http://[your.ELK-VM.External.IP]:5601/app/kibana


