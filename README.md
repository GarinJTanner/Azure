## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Diagram](https://raw.githubusercontent.com/GarinJTanner/Azure/main/Diagram/ELK-Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the [my-playbook.yml](https://github.com/GarinJTanner/Azure/blob/main/Ansible/my-playbook.yml) file may be used to install only certain pieces of it, such as Filebeat.


This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly efficient and reliable, in addition to restricting traffic to the network.
-  Load balancers help divvy out traffic to multiple servers instead of having the traffic impact just one machine, which not only improves performance but helps prevent denial-of-service attacks. The purpose of the jump box is to centralize all administrative tasks, allowing security monitoring to be performed on a single machine.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
-  Filebeat watches for changes to log files
-  Metricbeat monitors system metrics and services

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    | Webserver| 10.0.0.5   | Linux            |
| Web-2    | Webserver| 10.0.0.6   | Linux            |
| ELK-VM   | Webserver| 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 71.193.51.206

Machines within the network can only be accessed by SSH on port 22.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 71.193.51.206        |
| Web-1    | No                  |  10.0.0.4 10.0.0.6   |
| Web-2    | No                  |  10.0.0.5 10.0.0.6   |
| ELK-VM   | No                  | 71.194.51.206        |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which allows for rapid deployment.

The playbook implements the following tasks:
-  Install Docker
-  Install Python and the Python Docker Module
-  Download and launch the Docker web container
-  Enable the Docker service


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![docker ps](https://raw.githubusercontent.com/GarinJTanner/Azure/main/images/docker-ps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
-  Jump-Box 10.0.0.4
-  Web-1 10.0.0.5
-  Web-2 10.0.0.6

We have installed the following Beats on these machines:
-  Filebeat
-  Metricbeat

These Beats allow us to collect the following information from each machine:
Filebeat collects data on file logs,

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
-  Filebeat watches for changes to log files, which we can use to pull info on events like login attempts, deprecation logs
-  Metricbeat monitors system metrics and services

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
