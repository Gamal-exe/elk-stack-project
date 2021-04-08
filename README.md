## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

<img src="C:\Users\jaque\Pictures\Screenshots\network diagram.png" alt="network diagram" style="zoom:50%;" />

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - elk.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly secure, in addition to restricting traffic to the network.
- Load balancers are integral in their nature to security, they are able to divert traffic from a companies main server to a public, rendering a DDOS Attack ineffective. The advantage of a jumpbox is in their isolation.
- Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the system logs and system metric

- filebeat watches for log files and sends them to elasticsearch
- metricbeat collects metrics from the operating system or server.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name        | Function  | IP Address | Operating System |
| ----------- | --------- | ---------- | ---------------- |
| Jump Box    | Gateway   | 10.0.0.1   | Linux            |
| web 1       | VM        | 10.0.0.5   | Linux            |
| web 2       | VM        | 10.0.0.6   | linux            |
| Elk machine | elk-stack | 10.1.0.4   | linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- this.is.my.ip

Machines within the network can only be accessed by
- Jump-Box

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
| -------- | ------------------- | -------------------- |
| Jump Box | Yes                 | this.is.my.ip        |
| Web-1    | No                  |                      |
| Web-2    | No                  |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- it automates the download and installation process of programs, saving time and energy.

The playbook implements the following tasks:

- download docker
- update cache
- check for docker presence 

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![docker_ps_output](C:\Users\jaque\Pictures\Screenshots\docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5	
- 10.0.0.6

We have installed the following Beats on these machines:
- filebeat and metricbeat

These Beats allow us to collect the following information from each machine:
- filebeat collects and send logs while meatricbeat collects and sends metrics from your machine.

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the elk.yml file to ansible directory 
- Update the hosts file to include webserver IPs and db IPs
- Run the playbook, and navigate to http://20.46.242.103:5601/?app?kibana to check that the installation worked as expected.

