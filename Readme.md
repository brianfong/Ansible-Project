# HW-13 

## Description/Topology
Load balancing ensures that the application will be highly available, in addition to restricting access to the network.

The load balancers protect the VMs from intrusion, and the jump box is used to protect the network, having priviledged access

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the fiels and system resources.

Filebeat watches for changes in the file system
Metric Beat monitors the operating system, running services, 

|NAME                |FUNCTION                   |IP ADDRESS                   | OPERATING SYSTEM
|----------------|-------------------------------|-----------------------------|-------|
|Jumpbox|Gateway|Internal|Linux|
|Load Balancer|Obfuscation|Public|Linux|
|DWVM|WebApp|Internal|Linux
|ELK|Monitoring|Internal|Linux

## AccessPolicies
Only the Load Balancer can accept traffic from the internet
DVWA Machines should be only allowed to talk to the jump box as well as being added to the Load Balancer
The Jumpbox as well as the ELK VM should be whitelisted to the users IP

## ELK Configuration

The main benefit of using ansible to deploy ELK is the automatic configuration of the backend, log forwarders and front end deployed together, which then can be replicated across containers/virtual machines
The ansible playbook will: 
- install docker
- install pip and python module
- run the docker container

## Ansible how  to

- move all files to /etc/ansible
- change host IPs to their respective groups in the hosts file (webservers, elkservers, etc)
- check vms to see if docker container is running

Playbook files are yml files, typically saved in the etc/ansible directory
The hosts file will determine where each docker image is installed
To visit ELK, enter the public IP of the VM ELK is installed, followed by :5601 