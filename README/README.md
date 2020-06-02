## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

ELK_Stack_Project/README/Images/NetworkDiagram.JPG

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ELK-project.yml file may be used to install only certain pieces of it, such as Filebeat.

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly availabe, in addition to restricting access to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system metrics.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.1.0.4   | Linux            |
| DVWA-VM1 | Website  | 10.1.0.6   | Linux            |
|ELK-server| ELK      | 10.1.0.5   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 70.181.146.68

Machines within the network can only be accessed by Jump Box.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 70.181.146.68        |
| ELK      | No                  | 10.1.0.4             |
| DVWA     | No                  | 10.1.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because this allows for a set of instructions that can be used to set up and configure multiple machines with minimal changes or alterations.

The playbook implements the following tasks:
- Installs docker.io
- Installs python-pip
- Uses pip to install docker
- Sets maximum virtual memory
- Downloads and launches an ELK container via docker

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

ELK_Stack_Project/README/Images/DockerPS.JPG

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.1.0.6

We have installed the following Beats on these machines:
- Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat collects log files from the monitored machines and sends them to Elasticsearch or Logstash. Metricbeat collects metrics from the operating system and from services running on the server.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the ELK-project.yml file to /etc/ansible/.
- Update the hosts file to include a webserver group with the machines IP address
- Run the playbook, and navigate to (machinesIPAddress):5601 to check that the installation worked as expected.
