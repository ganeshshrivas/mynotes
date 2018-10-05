---
layout: post
title: Setting up vagrant
---

Vagrant is a tool through which you can create and develop virtual environments. It is very easy to setup virtual machines and managing them using CLI with vagrant. 

### Install Virtual Box
[Download Virtual Box](https://www.virtualbox.org/wiki/Downloads) and install it.

### Install Vagrant
[Download Vagrant](https://www.vagrantup.com/downloads.html) and install it.

### Create an Instance

Create a directory for the instance setup.

```
mkdir ubuntu_machine
cd ubuntu_machine
```

Now we need to select a box to install, vagrant boxes are package format for vagrant environments. We are going to install <span style="color:red">ubuntu/xenial64</span> but you can search and select various boxes from the [public catalogue of vagrant boxes](https://app.vagrantup.com/boxes/search).

```
vagrant init ubuntu/xenial64
vagrant up
```

```vagrant up``` runs the instance in virtual box. SSH into the instance using the command:
```
vagrant ssh
```

### Enable port forwarding from guest to host

```vagrant init``` creates a configuration file called the Vagrantfile. We can edit this file and change default configurations. To enable port forwarding, uncomment and modify the below line as:

```
config.vm.network "forwarded_port", guest: 3000, host: 3000
```

Now restart the instance to reflect the changes.
```
vagrant reload
```

### Setting up sync folder
We can set up a sync folder between guest and host machine. This is helpful when you are not using vim as the default editor. Uncomment and modify the below line in Vagrantfile as:
```
config.vm.synced_folder ".", "/vagrant"
```

First argument is the directory path on the host machine and second is the directory path on the guest machine. By default vagrant using <span style="color:red">rsync</span> to sync files between the directories. But you can use <span style="color:red">nfs</span> for fast synching. NFS required host only network with a specific IP.
```
config.vm.network "private_network", ip: "192.168.33.10"
config.vm.synced_folder ".", "/vagrant", type: "nfs"
```
