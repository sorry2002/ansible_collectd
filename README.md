# Ansible : Playbook Collectd

The aim of this project is to deploy a Collectd instance on Vagrant instances.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

What things you need to run this Ansible playbook :

*   [Vagrant](https://www.vagrantup.com/docs/installation/) must be installed on your computer
*   Update the Vagrant file based on your computer (CPU, memory), if needed
*   Update the operating system to deploy in the Vagrant file (default: Ubuntu)
*   Download the Ansible requirements:

```bash
$ ansible-galaxy install -r requirements.yml
```

### Usage

A good point with Vagrant is that you can create, update and destroy all architecture easily with some commands.

Be aware that you need to be in the Vagrant directory to be able to run the commands.

#### Deployment

To deploy Collectd on Vagrant instance, just run this command :

```bash
$ vagrant up
```

If everything run as expected, you should be able to list the virtual machine created :

```bash
$ vagrant status

Current machine states:

collectd01                   running (virtualbox)
```

If everything run as expected, you should connect to the Vagrant instance and run collectd command :

```bash
$ collectd
option = Hostname; value = collectd01;
option = FQDNLookup; value = False;
option = BaseDir; value = /var/lib/collectd;
Done parsing /usr/share/collectd/types.db
option = AutoLoadPlugin; value = True;
option = Interval; value = 60.000000;
option = Timeout; value = 2.000000;
option = ReadThreads; value = 5.000000;
option = WriteThreads; value = 5.000000;
Created new plugin context.
```

#### Destroy

To destroy the Vagrant resources created, just run this command :

```bash
$ vagrant destroy
```

### How-To

This section list some simple command to use and manage the playbook and the Vagrant hosts.

#### Update with Ansible

To update the Collectd instance configuration with Ansible, you just have to run the Ansible playbook collectd.yml with this command :

```bash
$ ansible-playbook collectd.yml
```

#### Update with Vagrant

To update the Collectd instance configuration with Vagrant, you just have to run provisioning part of the Vagrant file :

```bash
$ vagrant provision
```

#### Connect to Vagrant instance

To be able to connect to a Vagrant instance, you should use the CLI which is configured to automatically use the default SSH key :

```bash
$ vagrant ssh collectd01
```

## Author

Member of Wikitops : https://www.wikitops.io/

## Licence

This project is licensed under the Apache License, Version 2.0. For the full text of the license, see the LICENSE file.
