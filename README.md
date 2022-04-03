# Project1
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![NetworkDiagram](https://user-images.githubusercontent.com/102398249/161442666-d37dd9ab-05a6-45da-b2c0-8dd4286b6789.JPG)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the file may be used to install only certain pieces of it, such as Filebeat.

- _[installelkyml.txt](https://github.com/acharris989/Project1/files/8405424/installelkyml.txt)

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
- _TODO: What aspect of security do load balancers protect?  What is the advantage of a jump box?_ 
- Load balancers help to protect and ensure availability. The main advantage of a jump box is that it provides a secure, single access point for sys admins to simultaneously deploy configurations efficiently amongst several virtual machines on a network. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system metrics.
- _TODO: What does Filebeat watch for?_ 
- Filebeat monitors for any suspicious changes to system log files
- _TODO: What does Metricbeat record?_ 
- Metricbeat records system metrics

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function   | IP Address | Operating System |
|----------|------------|------------|------------------|
| Jump Box | Gateway    | 10.0.0.4   | Linux            |
| Web-1    | Web Server | 10.0.0.5   | Linux            |
| Web-2    | Web Server | 10.0.0.6   | Linux            |
| Web-3    | Web Server | 10.0.0.7   | Linux            |
| ELKVM    | ELK Server | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_ 
- 130.45.76.220

Machines within the network can only be accessed by SSH.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_  
- Jump Box (from ansible container) - 40.122.34.186

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | IP Addresses Allowed |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 130.45.76.220        |
| Web-1    | No                  | 10.0.0.4             |
| Web-2    | No                  | 10.0.0.4             |
| Web-3    | No                  | 10.0.0.4             |
| ELKVM    | No                  | 40.122.34.186        |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_ 
- Automating allows repetitive tasks to be done much more quickly, efficiently and with fewer mistakes.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ... Install docker.io
- ... Install python3-pip 
- ... Increase virtual memory to 262144
- ... Download and launch docker elk container
- ... Enable service docker on boot 

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
![dockerps](https://user-images.githubusercontent.com/102398249/161446413-07df84e6-97ce-415a-a62d-b189793b974f.JPG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_
- 10.0.0.5
- 10.0.0.6
- 10.0.0.7

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
- Filebeat monitors for any suspicious changes to system log files which could indicate an attack. This might be done with the Threat Intel Indicator Match rule.
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the YAML file to roles.
- Update the hosts file to include the ELK VM host
- Run the playbook, and navigate to results to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_ 
- The playbook file is the YAML file, copied into the roles directory.
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ The hosts file should be updated to specify the IP addresses of the machines. The ELK server is grouped separately from the webservers in order to specify which plays are run on each group.
- _Which URL do you navigate to in order to check that the ELK server is running?
- http://51.13.117.124:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._!
