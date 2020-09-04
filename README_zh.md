# Ansible Collections - goldeagle.metrics | [English](README.md)

指标数据和物联网数据流处理相关的 ansible 集合

[<img src="https://img.shields.io/github/license/goldeagle/ansible-collection-metrics?style=flat-square">](./LICENSE)
<img src="https://img.shields.io/github/repo-size/goldeagle/ansible-collection-metrics?style=flat-square">
<img src="https://img.shields.io/github/last-commit/goldeagle/ansible-collection-metrics?style=flat-square">

## Table of Contents
1. [介绍](#chapter-1)
2. [技术概况](#chapter-2)<br>
  2.1. [软件介绍](#chapter-2-1)<br>
  2.2. [支持的操作系统](#chapter-2-3)
1. [快速开始](#chapter-3)
2. [软件清单](#chapter-4)<br>
  4.1. [数据可视化看板](#chapter-4-1)<br>
  4.2. [时间序列型数据库](#chapter-4-2)<br>
  4.3. [流处理](#chapter-4-3)<br>

## 1. 介绍 <a id="chapter-1"></a>

指标数据和物联网数据流处理相关的 ansible 集合。
包括一些类似 prometheus 或 grafana 这种流行的软件。

## 2. 技术概况 <a id="chapter-2"></a>

### 2.1. 软件介绍<a id="chapter-2-1"></a>

* chronograf - TICK 技术栈中的指标数据可视化看板
* grafana - 最流行的指标数据可视化看板
* influxdb - TICK 技术栈中的时序型数据库
* loki - 参考 prometheus 专门针对 log 场景的时序型数据库
* prometheus - 最流行的时序型数据库
* tdengine - 针对物联网场景的分布式时序型数据库
* telegraf - TICK 技术栈中的指标数据收集代理服务


### 2.2. 支持的操作系统  <a id="chapter-2-3"></a>

* [x] Debian
* [x] Ubuntu
* [x] Kali
* [x] CentOS
* [x] Fedora
* [ ] Gentoo
* [ ] MacOS

## 3. 快速开始  <a id="chapter-3"></a>

### 3.1. 安装 ansible

先下载安装 "ansible"
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

- 从 github 仓库获取:
```bash
$ git clone https://github.com/ansible/ansible
```

### 3.2. 创建个 ansible 的用户

添加用户：
```bash
$ sudo useradd {{ your_ansible_user }}-m -G users,sudo -s /bin/bash
$ sudo passwd {{ your_ansible_user }}
$ mkdir -p ~/.ssh
```

生成用户的密钥对：
```bash
$ ssh-keygen -t rsa -b 4096 -C "{{ your_ansible_user }}"
```

分发公钥：
```bash
$ scp .ssh/id_rsa.pub {{ your_ansible_user }}@{{ target_host }}:~/.ssh/authorized_keys
```

测试一下：
```bash
$ ssh -T {{ your_ansible_user }}@{{ target_host }}
```

### 3.3. 安装集合

安装集合：
```bash
$ ansible-galaxy collection install goldeagle.metrics
```

默认情况下，集合会被安装到：
```bash
~/.ansible/collections/ansible_collections/goldeagle/metrics/
```

### 3.4. 编写执行的剧本
接下来就可以自定一个剧本文件使用集合里面包含的角色，（比如叫 playbook.yml）：

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

执行这个剧本：
```bash
$ ansible-playbook -i <your_hosts_file> playbook.yml -K
```


## 4. 软件清单 <a id="chapter-4"></a>

### 4.1. 数据可视化看板<a id="chapter-4-1"></a>

- [x] chronograf
- [x] grafana

### 4.2. 时间序列型数据库 <a id="chapter-4-2"></a>

- [x] influxdb
- [x] loki
- [x] prometheus
- [x] tdengine

### 4.3. 流处理 <a id="chapter-4-3"></a>

- 跟我说几个吧，我加上去