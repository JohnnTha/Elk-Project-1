# Elk-Project-1
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Diagrams/Azure diagram.PNG

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

- _TODO: Enter the playbook file._
      -filebeat-playbook.yml
      -install.elk.yml
      -metricbeat-playbook.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly _____, in addition to restricting _____ to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_
    -Load balancers protects the system from DDoS attacks by shifting attack traffic. The advantage of a jump box is to give access to the user from a single node that can be secured and monitored.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- _TODO: What does Filebeat watch for?
      -Filebeat watches logs files and other log data changes.
- _TODO: What does Metricbeat record?
     -Metricbeat records metric data from target servers such as CPU, memory, and data from running on servers.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.1.0.4   | Linux            |
| Web1     | server   | 10.1.0.7   | Linux            |
| Web2     | server   | 10.1.0.6   | Linux            |
| Elk      | server   | 10.0.0.6   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the _____ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_
    -local public IP address

Machines within the network can only be accessed by _____.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_
    -Jump-box-10.1.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | Local IP             |
| Web1     | No                  | 10.1.0.4             |
| Web2     | No                  | 10.1.0.4             |
| Elk      | No                  | 10.1.0.4             |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_
    -The main advantage is to be able to make a playbook that can be deployed to multiple servers. 

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
    -ssh into jump-box
    -sudo docker start and attach ansible
    -cd /etc/ansible/ and create the Elk installation playbook
    -add the private IP address into host file
    -run ansible-playbook install.elk.yml
    -ssh into elk to see if it installed

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Screenshots/Elk-Docker-ps.PNG

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_
    -Web1-10.1.0.7
    -Web2-10.1.0.6
    
We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_
    -Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
    -Filebeat collects log data changes (Screenshots/file-beat data.PNG) Metric beat collects metric data such as cpu, memory, disk, and network (Screenshots/Metricbeat data.PNG).

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
    -/etc/ansible/roles/files
- Update the _____ file to include...
    -filebeat-config.yml
- Run the playbook, and navigate to ____ to check that the installation worked as expected.
    - -http://40.74.224.127:5601/app/kibana#/home

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
    -filebeat-playbook.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
    -hosts file
    -By having two different groups in the hosts file, one for webservers and the other elk.
- _Which URL do you navigate to in order to check that the ELK server is running?
 -http://40.74.224.127:5601/app/kibana#/home

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
