# ProjectELK
design and deployment of an ELK server
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://drive.google.com/file/d/1-ioDvc3n9zf82Ks7ve9iGXa9tLmYkapP/view?usp=sharing

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the .yml file may be used to install only certain pieces of it, such as Filebeat.

  - ansible-playbook elk.yml
  - filebeat.config.yml
  - filebeat-playbook.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- A load balancer adds additional layers of security without changes to the application, it does this through authenticating user access and the firewall in the balancer further protects. 
- The advantage of using a jump box is that it is a secure machine which can be first connected to before doing any administrative tasks or as an origination point prior to connecting to untrusted environments or servers, it can also be used as a tool to manage other systems on other security networks. Another advantage is that all tools on the jump box are maintained on the one system, so only a single system is required for any new tools or updates.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system services.
- Filebeat watches for log events and monitors the log files and locations that you specify.
- Metricbeat records statistics and metrics from the operating system and shipds them to the specified output.

The configuration details of each machine may be found below.

| Name       | Function   | IP Address | Operating System   |
|------------|------------|------------|--------------------|
| Jump Box   | Gateway    | 10.0.0.4   | Linux Ubuntu 18.04 |
| Web-1      | Webserver  | 10.0.0.7   | Linux Ubuntu 18.04 |
| Web-2      | Webserver  | 10.0.0.6   | Linux Ubuntu 18.04 |
| Web-3      | Webserver  | 10.0.0.8   | Linux Ubuntu 18.04 |
| ELK-SERVER | ELK-server | 10.1.0.4   | Linux Ubuntu 18.04 |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-115.64.122.31

Machines within the network can only be accessed by the jumpbox or load balancer
- jump box 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name          | Public Access | Allowed IP    |
|---------------|---------------|---------------|
| Jump Box      | yes           | 115.64.122.31 |
| Webservers    | no            | 10.0.0.4      |
| Load Balancer | yes           | 115.64.122.31 |
| ELK-SERVER    | yes           | 115.64.122.31 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- can be set up on multiple machine through just one system.

The playbook implements the following tasks:
- install docker
- download containers
- increase memory
- launch containers

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://drive.google.com/file/d/12yCbDLG2bqfUG5YNlBatjHx6lZVnk6Zz/view?usp=sharing

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web - 1
- Web - 2
- Web - 3

We have installed the following Beats on these machines:
- Metricbeats
- Filebeats

These Beats allow us to collect the following information from each machine:
- Metricbeats collect all metrics and statistics from the os and services running on the server to track memory and CPU usage
- Filebeats collect centralized log data and ships it to the ELK
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to the ansible container.
- Update the ansible/hosts file to include the ip addresses of your ELK and webservers
- Run the playbook, and navigate to (ELKserverIP):5601/app/kibana to check that the installation worked as expected.


