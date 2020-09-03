# Ansible Tower Vagrant project
## Synopsis

This project provides a Vagrant machine with Ansible Tower installed.

## Requirements

 - Vagrant
 - Your choice of Vagrant provider (`libvirt` in this case)
 - A valid Red Hat subscription

## Usage

First, amend the *Vagrantfile* according to your environment, and prepare a 
hosts file that references your machine (e.g. tower.local).

Then, execute the following commands:
```bash
$ export RH_SUB_USER="myrhuser"
$ export RH_SUB_PASS="myrhpass"
$ vagrant up
$ ansible-playbook -i hosts \
                   -l tower provision-tower.yml \
                   -u root \
                   -e rh_sub_pass=$RH_SUB_PASS \
                   -e rh_sub_user=$RH_SUB_USER
```

The provisioning playbook should take 15-20 minutes on a fast machine with
a decent Internet connection.

### Optional: custom virtual environments

You may also want to provision an extra virtual env for use in Tower. Take
a look at the `provision-custom-venvs.yml` playbook for more information.

