---
layout: guide
title: StorageOS Docs - Cluster install
anchor: install
module: install/clusterinstall
# Last reviewed by simon.croome@storageos.com on 2017-04-11
---

# Cluster install

To test high availability, set up a three node StorageOS cluster using a laptop or single machine.

## Prerequisites

Install [VirtualBox](https://www.virtualbox.org/wiki/Downloads) and [Vagrant
1.9.3](http://vagrantup.com/downloads.html). You will also need the Vagrant plugin for Alpine, a lightweight Linux distribution used for testing:

```bash
$ vagrant plugin install vagrant-alpine
```

## Installation

1. Clone this repository, which contains scripts to automate setup.
```bash
$ git clone https://github.com/storageos/storageos-alpine.git
$ cd storageos-alpine
```

2. Bring up a three-node StorageOS cluster. This takes around five minutes.
```bash
$ make all
Bringing machine 's-1' up with 'virtualbox' provider...
Bringing machine 's-2' up with 'virtualbox' provider...
Bringing machine 's-3' up with 'virtualbox' provider...
[...]
```
This sets up three virtual machines named `s-1`, `s-2`, `s-3` running
* Alpine Linux
* Docker
* The recommended KV store, Consul.
* The StorageOS volume plugin.

3. Connect to one of the VMs:
```bash
$ vagrant ssh s-1
```

Now you are ready to [install an application](../applications/postgres.html) or [manage the cluster](../manage/cli.html).

To log into other nodes:
```bash
$ exit
$ vagrant ssh s-2
```

To clean up:
```bash
$ exit
$ make destroy
```
