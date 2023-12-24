# Ansible Playbook for Papermerge DMS


## Requirements

- Remote host with ssh access and Debian12 / Ubuntu 22.04 LTS
- On your local computer you need to have `ansible` == 2.15


## Ansible Inventory

Ansible inventory file is not included. You have to [create one](https://docs.ansible.com/ansible/latest/inventory_guide/intro_inventory.html).

All but sensible variables are provided in ``group_vars/all``.
Sensible variables should be provided in inventory file (which is not in the repo)...
At least this is where I put sensible variable.

Here is example of my (you need to adjust to your own setup) inventory file:

```
192.168.56.99 secret_key=abc superuser_password=1234 superuser_username=eugen database_url="postgresql://scott:tiger@db/mydatabase"  db_pass=tiger
```


## Usage

Install Papermerge DMS:

```
$ ansible-playbook install.yml
```

Application will be accessible via http://localhost:<web_app_port>.

In order to create a backup:

```
$ ansible-playbook backup.yml
```

In order to restore the backup:

```
ansible-playbook restore.yml --extra-vars "backup_file=/backup/backup_20_11_2023-07_33_03.tar.gz"
```

The backup file path is the one from inside docker container.

## Contribute

The playbooks were created having in mind Ubuntu 22.04 host. You will need to adjust ansible playbooks in case you use another host e.g. Debian, CentOS etc.

I am happy to accept your pull requests!

## Ansible Config

Ansible config is not included. Here is sample ``ansible.cfg`` file:

```
[defaults]
inventory = inventory
host_key_checking = False
deprication_warnings = False
remote_user = vagrant
private_key_file = .vagrant/machines/default/virtualbox/private_key
```

Of course you need to adjust above ``ansible.cfg`` to your own specific setup.

## Ansible Cheatsheet

```
$ ansible all -m ping
$ ansible all --list-hosts
$ ansible all -m gather_facts
$ ansible all -m apt -a name=vim --become --ask-become-pass
```
