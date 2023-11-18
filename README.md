# Ansible Playbook for Papermerge DMS


## Ansible Inventory

Ansible inventory file is not included. You have to [create one](https://docs.ansible.com/ansible/latest/inventory_guide/intro_inventory.html).


## Ansible Config

Ansible config is not included. Here is sample ``ansible.cfg`` file:

  [defaults]

  inventory = inventory
  host_key_checking = False
  deprication_warnings = False
  remote_user = vagrant
  private_key_file = .vagrant/machines/default/virtualbox/private_key


## Ansible Cheatsheet


  $ ansible all -m ping
  $ ansible all --list-hosts
  $ ansible all -m gather_facts
