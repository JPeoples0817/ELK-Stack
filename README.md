## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Diagrams/Project 1 Diagram.drawio.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the /etc/ansible/install-elk.yml file may be used to install only certain pieces of it, such as Filebeat.

  - /etc/ansible/install.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly redundant, in addition to restricting traffic to the network.
- What aspect of security do load balancers protect? What is the advantage of a jump box? Load balancers ensure that redundancy is in place. The main advantage of jump box is have control over the other devices that's on the host machine.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
- What does Filebeat watch for? Filebeat monitors logs and log files that you choose to monitor.
- What does Metricbeat record? Metricbeat takes all the metrics and data that is collected and sends them to the output that is chosen.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function   | IP Address              | Operating System |
|----------|------------|-------------------------|------------------|
| Jump Box | Gateway    | 10.0.0.4 40.78.105.138  | Linux            |
| Web-1    | DVWA       | 10.0.0.5                | Linux            |
| Web-2    | DVWA       | 10.0.0.7                | Linux            |
| Elk-VM   | Elk Server | 10.1.0.4 20.119.234.127 | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- My home network
Machines within the network can only be accessed by Jump Box.
- Which machine did you allow to access your ELK VM? What was its IP address? 
	Jump Box 10.1.0.4 / 20.119.234.127

A summary of the access policies in place can be found in the table below.

| Name      | Publicy Accessible | Allowed IP Addresses |
|-----------|--------------------|----------------------|
| Jump Box  | Yes                | 40.78.105.138        |
| Web-1     | No                 |                      |
| Web-2     | No                 |                      |
| Elk-VM    | Yes                | 20.119.234.127       |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Automation allows less errors and allows for it to be revised and improved through different individuals

The playbook implements the following tasks:
- Install docker.io
- Install python3-pip
- Install docker module
- Configure to use more memory
- Download and launch docker elk container and allow for start on boot up

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Ansible/docker ps.PNG

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 10.0.0.5
- Web-2 10.0.0.7

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
- Filebeat reads and sends log files from the ones that is being monitored.
- Metricbeat collects the data that and sends it to an output of your chosing.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to /etc/ansible.
- Update the /etc/ansible/hosts file to include ELK server and webservers
- Run the playbook, and navigate to http://20.119.234.127/app/kibana to check that the installation worked as expected.

- _Which file is the playbook? Where do you copy it?_ /etc/ansible/install-elk.yml to /etc/ansible/roles/filebeat-playbook.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ /etc/ansible/files/filebeat-config.yml
- _Which URL do you navigate to in order to check that the ELK server is running?_ http://20.119.234.127/app/kibana

