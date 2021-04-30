CLOUD SECURITY PROJECT
This is my first project which dealt with the ELK stack and ansible.
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

ELK-PROJECT/Diagram/ELK PROJECT (2).png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the yml file may be used to install only certain pieces of it, such as Filebeat.



This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
In relation to security, Load Balancers provide redundancy. They distribute traffic to multiple servers which can stop DDOS attacks. If one server is backed up, then there is another server that is running the application and is ready to go.The jumpbox is great for an added security measure as it allows you to keep only the jumbox connection ports open to the public. When you connect to the Jumpbox, you can then connect to your Virtual Machine which only allows the jumpbox's IP to connect to it, which makes it more secure.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system network.
Filebeat watches out for all sorts of logs, it monitors them and also records them and with it, one can monitor any suspicious activity on their virtual network.While Filebeat monitors logs, Metricbeat records metrics and statistic and sends them to either elasticsearch or Logstash.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.6   | Linux            |
| Web 1    | VM       | 10.0.0.9   | Linux            |
| Web 2    | VM       | 10.0.0.10  | Linux            |
| Elk VM   | VM       | 10.1.0.5   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
Jumpbox IP: 10.0.0.6

Machines within the network can only be accessed by SSH connection to the jumpbox, like the ELK machine which was accessible thorugh web 1 machine (IP: 10.0.0.9) which had the key pair which allowed SSH connection to the ELK machine.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | Any public IP        |
| Web 1    | No                  | 10.0.0.6             |
| Web 2    | No                  | 10.0.0.6             |
| Elk VM   | No                  | 10.0.0.9
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it automatically updates, cuts the configuration time and it configures all of tasks automatically.

The playbook implements the following tasks:
- Install Docker
- Install Python pip3
-Download and launch a docker elk container
-Increase virtual memory

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

ELK-PROJECT/Linux/Linux Screenshots.pdf

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
Web 1: 10.0.0.9
Web 2: 10.0.0.10
We have installed the following Beats on these machines:

Filebeat

These Beats allow us to collect the following information from each machine:

Filebeat allows us to collect log events and gather information of system logs
.
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the file to your /etc folder.
- Update the file to include your host.
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

- _Which file is the playbook? ELK-PROJECT/Ansible/Install-elk.yml.pdf Where do you copy it? You copy this file to your /etc folder.
-  How do I specify which machine to install the ELK server on versus which to install Filebeat on? You would have to specify the host in order to specify which machine to install the ELK server on.
- _Which URL do you navigate to in order to check that the ELK server is running? Kibana Url (Elk machine IP:5601)

