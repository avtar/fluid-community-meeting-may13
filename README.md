# Fluid Community Meeting May13 Demo

This repository contains [Ansible](http://docs.ansible.com/) and [Vagrant](https://www.vagrantup.com/) examples presented at a [Fluid Project Community Meeting](http://wiki.fluidproject.org/display/fluid/Community+workshops) on May 13, 2015. The example playbooks use YAML and not the [Ansible shorthand](https://servercheck.in/blog/yaml-best-practices-ansible-playbooks-tasks) syntax.

## Contents

* [Vagrantfile](http://docs.vagrantup.com/v2/vagrantfile) - upon creating a VM this will upgrade Ansible and then download an [Ansible role](https://github.com/geerlingguy/ansible-role-jenkins) in order to deploy a [Jenkins](http://jenkins-ci.org/) server
* example.yml - playbook containing three example tasks each using a different [Ansible module](http://docs.ansible.com/modules.html)
* jenkins.yml - playbook that will apply the downloaded Jenkins role
* [requirements.yml](http://docs.ansible.com/galaxy.html#installing-multiple-roles-from-a-file) - YAML file containing a list of required roles
* group_vars/all - an example of [group variables](http://docs.ansible.com/intro_inventory.html#splitting-out-host-and-group-specific-data) usage
* templates/demo_file.j2 - an example of [using variables in Jinja2 templates](http://docs.ansible.com/playbooks_variables.html#using-variables-about-jinja2)

## Requirements

You will need to install the following:

* [VirtualBox](https://www.virtualbox.org/)
* Vagrant

## Getting Started

The Vagrantfile allows one to allocate a specific amount of RAM or virtual CPUs using the ``VM_RAM`` and ``VM_CPUS`` environment variables. For example the following will allocate 2Gb of memory and start the VM:

    VM_RAM=2048 vagrant up


