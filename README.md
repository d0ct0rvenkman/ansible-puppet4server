# ansible-puppet4server

## Purpose
`ansible-puppet4server` is an Ansible playbook that deploys a Puppet 4 server, puppetdb, puppetboard, and r10k to a CentOS (maybe RHEL?) 7 installation. It installs all necessary packages, and should leave you with a working Puppet master upon successful completion.

## Prerequisites
* A clean CentOS 7 install with at least 3GB of RAM allocated.
* * `puppetserver`'s configuration defaults to starting with a 2GB java heap size, and having an insufficient amount of RAM will prevent it from starting. It can be adjusted downwards after it's installed, but trying to modify it while the playbook is running is dicey.
* Ansible installed and in working order on a separate host/workstation with a properly populated inventory

## Usage
* Clone this repo somewhere on the machine where you will initiate the playbook
* Configure your ansible inventory to have the soon-to-be puppet 4 server in a group called `puppet4servers`
* Make sure you have SSH keys deployed to the puppet server hosts
* Run the playbook!
```bash
$ ansible-playbook ~/git/ansible-puppet4server/puppet4server.yaml -i ~/ansible/inventory/hosts.yaml
```
* At this point, you'll probably want to customize puppet to your environment by editing/deploying the Hiera and r10k configuration files on your new puppet server.

## To-Do
* Make sure all config files are only written once so the playbook won't blow away customizations.
* Accept runtime configuration for things like postgres user/password
