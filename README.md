# Project-1
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/EM-Jones75/Project-1/blob/b662a8ee65960a52d8e8f42b2a47d3d455b52e8f/Full%20Diagram.PNG

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Elk.yml file may be used to install only certain pieces of it, such as Filebeat.

  https://github.com/EM-Jones75/Project-1/blob/5be752f2ccccf33d2ff17ef854a523992fdbfa2f/Elk.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly efficent, in addition to restricting overflow to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files or locations and system services.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.1.0.4   | Linux            |
| Web1     | Server   | 10.1.0.5   | Linux            |
| Web2     | Server   | 10.1.0.7   | Linux            |
| Web3     | server   | 10.1.0.10  | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the localhost machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-localhost

Machines within the network can only be accessed by the Jump box provsioner.
-20.115.58.230

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses           |
|----------|---------------------|----------------------          |
| Jump Box | Yes                 | 10.1.0.5, 10.1.0.7, 10.1.0.10  |
| Localhost| no                  | 10.1.0.4                       |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
Ansible will configure the Vms in bulk rather than one at a time which save tremendous amounts of time.

The playbook implements the following tasks:
- Installing the docker files and modules
- Installing python
- Increase virtual memory for the VMs
- Download and launch a docker Elk container
- Enable Docker on start up

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://github.com/EM-Jones75/Project-1/blob/93678f42015bf24507a7b2471ef425b6a6e3bcf4/Elk%20docker.PNG

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web1:10.1.0.5
- Web2:10.1.0.7
- Web3:10.1.0.10

We have installed the following Beats on these machines:
- filebeat https://github.com/EM-Jones75/Project-1/blob/167fe5d34a2eebf34946acacd34b47810fcbc29a/filebeat.yml
- metricbeat https://github.com/EM-Jones75/Project-1/blob/6ed83161317b7b90743f74846b6d535c80a7999b/metricbeat.yml

These Beats allow us to collect the following information from each machine:
Filebeat moniters the log files or locations that are specified, collects log events (such as audit logs, deprecation logs, gc logs, server logs, and slow logs), and forwards them either to Elasticsearch or Logstash for indexing.  While Metricbeat takes metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash, allowing admins to view data such as Apache. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook.yml file to /etc/ansible.
- Update the hosts file to include the VMs internal ip addresses
- Run the playbook, and navigate to http://20.120.240.33:5601/app/kibana to check that the installation worked as expected.



