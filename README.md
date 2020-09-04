# Ansible Collections - goldeagle.metrics | [中文](README_zh.md)

Ansible collections for metric monitoring & IoT data streaming.

[<img src="https://img.shields.io/github/license/goldeagle/ansible-collection-metrics?style=flat-square">](./LICENSE)
<img src="https://img.shields.io/github/repo-size/goldeagle/ansible-collection-metrics?style=flat-square">
<img src="https://img.shields.io/github/last-commit/goldeagle/ansible-collection-metrics?style=flat-square">

## Table of Contents
1. [Description](#chapter-1)
2. [Technical Overview](#chapter-2)<br>
  2.1. [Softwares Intro](#chapter-2-1)<br>
  2.2. [Supported OSs](#chapter-2-3)
1. [Quick Start](#chapter-3)
2. [Software Lists](#chapter-4)<br>
  4.1. [Dashboard](#chapter-4-1)<br>
  4.2. [Time Series Database](#chapter-4-2)<br>
  4.3. [Stream Process](#chapter-4-3)<br>

## 1. Description <a id="chapter-1"></a>

Ansible collections for metric monitoring & IoT data stream. 
Includes some popular softwares such like prometheus or grafana.

## 2. Technical Overview <a id="chapter-2"></a>

### 2.1. Softwares Intro <a id="chapter-2-1"></a>

* chronograf - a dashboard in TICK stack
* grafana - the most popular metric monitoring dashboard
* influxdb - time series database in TICK stack
* loki - a prometheus like time series database for logging
* prometheus - the most popular metric time series database
* tdengine - a fast distributed time series database system for IoT scenes
* telegraf - a metrics gathering agent in TICK stack

### 2.2. Tested OSs  <a id="chapter-2-3"></a>

* [x] Debian 10
* [x] Ubuntu 20.04.1
* [x] Kali 2020.3
* [x] CentOS 8.2
* [x] Fedora 32-1.6
* [ ] Gentoo
* [ ] MacOS

## 3. Quick Start  <a id="chapter-3"></a>

### 3.1. Install ansible

First of all, download "ansible"
- Debian & Ubuntu:
```bash
$ sudo apt install ansible
```

- Centos 8 & Fedora 32:
```bash
$ sudo dnf install ansible
```

- MacOS:
```bash
$ brew install ansible
```

- From github repository:
```bash
$ git clone https://github.com/ansible/ansible
```

### 3.2. Add a user for ansible

Add an ansible user:
```bash
$ sudo useradd {{ your_ansible_user }}-m -G users,sudo -s /bin/bash
$ sudo passwd {{ your_ansible_user }}
```

Become this ansible user:
```bash
$ sudo su - {{ your_ansible_user }}
$ mkdir -p ~/.ssh
```

Generate ssh key pair:
```bash
$ ssh-keygen -t rsa -b 4096 -C "{{ your_ansible_user }}"
```

Deploy the pub key:
```bash
$ scp .ssh/id_rsa.pub {{ your_ansible_user }}@{{ target_host }}:~/.ssh/authorized_keys
```

Test it:
```bash
$ ssh -T {{ your_ansible_user }}@{{ target_host }}
```

### 3.3. Install this collection

Install this collection:
```bash
$ ansible-galaxy collection install goldeagle.metrics
```

By default, the collection will be installed here:  
```bash
~/.ansible/collections/ansible_collections/goldeagle/metrics/

### 3.4. Create a playbook file to use the collection

Then you can use the roles from the collection in your playbooks (playbook.yml etc.):

```yaml
---

- name : configure and deploy the local servers and app codes
  hosts: {{ your_host_group_in_your_inventory }}
  remote_user: {{ your_remote_ansible_user }}
  become: yes
  become_method: sudo

  vars:
    ansible_python_interpreter: /usr/bin/python3

  collections:
    - goldeagle.metrics

  roles:
    - telegraf
    - grafana
    - tdengine
```

Run the playbook:

```bash
$ ansible-playbook -i <your_hosts_file> playbook.yml -K
```

## 4. Software Lists <a id="chapter-4"></a>

### 4.1. Dashboard <a id="chapter-4-1"></a>

- [x] chronograf
- [x] grafana

### 4.2. Time Series Database<a id="chapter-4-2"></a>

- [x] influxdb
- [x] loki
- [x] prometheus
- [x] tdengine

### 4.3. Stream Process<a id="chapter-4-3"></a>

- tell me some