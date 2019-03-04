# Ansible-discourse

Provisioning [Discourse](https://github.com/discourse/discourse) with Vagrant, Ansible, [Discourse Docker](https://github.com/discourse/discourse_docker) and AWS.

* For the installation on AWS see section [Deployment on AWS](#deployment-on-aws)
* For local installation with vagrant see section [Local Deployment with Vagrant](#local-deployment-with-vagrant)

# Local Deployment with Vagrant

## Requirements

* Vagrant (tested with *1.8.1*)
* Ansible (tested with *1.9.3*)


## Basic Setup

1) Clone this project:

```
git clone --recursive git@github.com:xpeppers/ansible-discourse.git
```

2) Add an entry to your `/etc/hosts` file that maps the domain `discourse.dev` to the IP of the virtual machine:

```
192.168.11.3    discourse.dev
```

3) Start the virtual machine with vagrant:

```
vagrant up
```

4) Install the ansible roles (execute from the host machine):

```
[sudo] ansible-galaxy install -r requirements.yml
```

5) Edit playbooks/roles/discourse/files/app.yml file filling <> parameters:

6) (Optional) Configure backup:

```
cp playbooks/roles/discourse/files/backup.cron.template.sh playbooks/roles/discourse/files/backup.cron.sh
```

Fill the API key in `backup.cron.sh` with the key you find here: https://<DISCOURSE_HOST>/admin/api/keys

7) (Optional) If you want to change the default (`/var/discourse`) installation directory of Discourse, you can change the value in `playbooks/vars/main.yml` and change the value of volumes in `app.yml` too.


## Provisioning

Provision with

```
# Vagrant host
scripts/provision_vagrant
# or
scripts/provision_vagrant_only_machine
# or
scripts/provision_vagrant_only_discourse



## Utility scripts

### Manual/Automatic Backups

Run this command to trigger a backup:

```
scripts/cmd_aws "sudo sh /home/discourse/backup.cron.sh"
```

Additionally there is a cron configured that runs automatic backups at 9:00, 14:00 and 20:00. For additional configuration see `playbooks/roles/discourse/tasks/main.yml`.



### Gather info about the machine

```
scripts/info_vagrant


git clone https://github.com/cristianlazarop/ansible-discourse.git

sudo su

ansible-galaxy install -r requirements.yml


ansible-playbook playbooks/main.yml 
(Couple of times)


cd /var/discourse

./launcher rebuild app
(So no config questions)


Why I have to run ansible-playbook playbooks/main.yml  more than once to run?