## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - [filebeat-playbook.yml](filebeat-playbook.yml)
  - [filebeat-config.yml](filebeat-config.yml) 

This document contains the following details:

- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly "efficient", in addition to restricting "high-traffic" to the network.

- _What aspect of security do load balancers protect?_

  Helps to prevent servers from being overloaded with traffic and helps increase uptime. As well as protecting against DDoS attacks

- _What is the advantage of a jump box?_

  Jump box is a secured system that is only used for admin tasks. This helps to prevent chance of hackers or malware attacks

  

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the "network" and system "logs".

- _What does Filebeat watch for?_

  Monitors log files/locations specified and sends them to Elasticsearch/Logstash

- _What does Metricbeat record?_

  Records metrics/statistics data and ships them to the output that you specify, such as Elasticsearch or Logstash 

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name                 | Function | IP Address                                  | Operating System |
| -------------------- | -------- | ------------------------------------------- | ---------------- |
| Jump-Box-Provisioner | Gateway  | 40.117.173.135 (Public)//10.0.0.4 (Private) | Linux            |
| ELK-Server           | Server   | 40.75.20.234 (Public)//10.1.0.4             | Linux            |
| Web-1                | Server   | 10.0.0.5 (Private)                          | Linux            |
| Web-2                | Server   | 10.0.0.6 (Private)                          | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box-Provisioner machine can accept connections from the Internet. 

Access to this machine is only allowed from the following IP addresses:

- _172.124.211.179 (LocalHost IP)_

Machines within the network can only be accessed by Jump-Box-Provisioner.

- _TODO: Which machine did you allow to access your ELK VM?_

  Jump-Box-Provisioner

- _What was its IP address?_

  40.117.173.135 (Public)//10.0.0.4 (Private)

A summary of the access policies in place can be found in the table below.

| Name       | Publicly Accessible | Allowed IP Addresses        |
| ---------- | ------------------- | --------------------------- |
| Jump Box   | Yes                 | 172.124.211.179             |
| ELK-Server | No                  | 172.124.211.179 // 10.0.0.4 |
| Web-1      | No                  | 10.0.0.4                    |
| Web-2      | No                  | 10.0.0.4                    |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

- _Allows you to deploy to multiple servers using a single playbook_

The playbook implements the following tasks:

- _Install docker.io_
- _Install python3-pip_
- _Install docker container_
- _Increase and use more memory_
- _Launch docker container: elk_

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats

This ELK server is configured to monitor the following machines:

- _Web-1 (10.0.0.5)_
- _Web-2 (10.0.0.6)_

We have installed the following Beats on these machines:

- _Filebeat_
- _Metricbeat_

These Beats allow us to collect the following information from each machine:

- _Filebeat collects information about file systems while Metricbeat collects machine metrics_

### Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:

- Copy the "playbook.yml" file to "/etc/ansible/roles".

- Update the "/etc/ansible/hosts" file to include

  [webservers]

  10.0.0.5 ansible_python_interpreter=/usr/bin/python3
  10.0.0.6 ansible_python_interpreter=/usr/bin/python3

  [elk]
  10.1.0.4 ansible_python_interpreter=/usr/bin/python3

- Run the playbook, and navigate to "http://Elk-Server.External.IP:5601/app/kibana" to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_

- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc.
