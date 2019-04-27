# Ansible Playbook for installing Cloudera's CM 6.2

This is a playbook for deploying Cloudera's Cloudera Manager 6.2 on to your instances with a single button!

### Prerequisites

In this setup there is a master which will hold CM 6 and serve as the NTP master for this time-island 

the rest of the nodes are meant to be added to the cluster 

There are 2 things that you have to do before using this playbook before you can deploy your new CDH cluster

1. Make sure that the ansible master have passwordless access to all the nodes to be hooked up

a) Generating ssh key on the ansible master

```
ssh-keygen -b 4096 -t rsa
```

b) Copying the ansible master's ssh key into all nodes
```
ssh-copy-id root@<node-ip>
```

2. Updating the hosts file

The first column is the host's name that will be set and cross propagated in each node's /etc/hosts file

The second column contain the host's ip address

There should only be 1 node under [cm] which will server as the cloudera manager

It is also suggested that this node is the same as the one on [ntpmaster] for convenience sake.

In my sample code the NTP master and CM is not actually within the cloudera cluster as i want to isolate the master from the cluster for easy maintenance


## Getting Started

After setting up the ssh keys and updating the hosts file using the playbook is as simple as

```
ansible-playbook -i hosts site.yml
```
 

## Disclaimer

This playbook is compiled against ansible 2.4.2.0 on CentOS Linux release 7.6.1810 

This is a hobbyist project, there is absolutely no warranty or responsibility for damages that might be unintentionally caused by this playbook

Ansible belongs to Red Hat, Inc

CDH, CM, cloudera belongs to Cloudera, Inc
