# UCB_Project_1
Code and images from Project 1

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/ahshra/UCB_Project_1/blob/main/Diagrams/Network_Architecture.png  

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the [yml file] file may be used to install only certain pieces of it, such as Filebeat.

  -install-elk.yml

This document contains the following details:
- Description of the Topolog
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the Damn Vulnerable Web Application.

Load balancing ensures that the application will be highly resilient, in addition to restricting access to the network.
- Load balancers ensure that the network stays running if one box is overwhelmed with load. A jump box allows the virtual machines to be protected from access from the wider net.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system.
-I created a playbook for filebeat, which monitors for log files.
-I also created a plybook for metricbear, which colledcts metrics from the operating systems and services running on the server.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    | VM       | 10.0.07    | Linux            |
| Web-2    | VM       | 10.0.0.6   | Linux            |
| web-3    | VM       | 10.0.0.8   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Load Balancer machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-[IP Address Redacted]

Machines within the network can only be accessed by ssh.
-Elk-Server-VM, accessible at **.**.**.***.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box |     No              | 10.0.0.1             |
| Web-1    |     No              | 10.0.0.7             |
| Web-2    |     No              | 10.0.0.6             |
| Web-3    |     No              | 10.0.0.8             |
| Elk      |     No              | 10.1.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because you can quickly deploy new machines.

The playbook implements the following tasks:
- installs docker.io
- installs python3-pip
- installs docker module
- increases virtual memory
- downloads and installls a docker elk container
- makes sure to enable service docker on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
-Web-1 (see IP above)
-Web-2 (see IP above)
-Web-3 (see IP above)

We have installed the following Beats on these machines:
- filebeat
- metricbeat

These Beats allow us to collect the following information from each machine:
-We can collect file logs, operating system and network logs.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy filebeat-config.yml and metricbeat-config.yml.
- Update
- Run the playbooks.

The playbook files are filebeat-playbook.yml and metricbeat-playbook.yml. You can find them here:
https://github.com/ahshra/UCB_Project_1/blob/main/Ansible/filebeat-playbook.yml
https://github.com/ahshra/UCB_Project_1/blob/main/Ansible/metricbeat-playbook.yml

Update the config fies for filebeat and metricbeat to run Ansible on a specific machine. 
In order to verify that you can access your server, navigate to http://[your.ELK-VM.External.IP]:5601/app/kibana. Use the public IP address of your new VM. 
