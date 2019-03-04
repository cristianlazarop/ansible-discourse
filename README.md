

git clone https://github.com/cristianlazarop/ansible-discourse.git

sudo su

ansible-galaxy install -r ansible-discourse/requirements.yml


ansible-playbook ansible-discourse/playbooks/main.yml
(Couple of times)


cd /var/discourse

./launcher rebuild app
(So no config questions)


Why I have to run ansible-playbook playbooks/main.yml  more than once to run?
