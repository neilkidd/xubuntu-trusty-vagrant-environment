(X)Ubuntu Trusty Vagrant Environment
====================================
This repo is a vagrant vm container for (X)Ubuntu Post Install Script development.
Inspired by the rails repo. (Link required)

## Prerequisites
* Vagrant
* Atlas account
* Access to neil_kidd/xubuntu-14043-desktop


##Usage:

vagrant login (follow the prompts to log in to atlas)
vagrant box add neil_kidd/xubuntu-14043-desktop

git clone https://github.com/neilkidd/xubuntu-trusty-dev-setup.git (or your own fork!)

vagrant up
vagrant ssh
host$ cd /vagrant/xubuntu-trusty-dev-setup
host$ sudo ./install.sh

When you have finished a run - you can edit your sources and then:
vagrant destroy
vagrant up

	
##TODO
* Add link to rails repo - thanks
* Think about full workflow scripts fro both windows and linux hosts
* Add shell provisoning - so a single vagrant up will do all the work
* Consider snapshots - they may be faster than vagrant destroy