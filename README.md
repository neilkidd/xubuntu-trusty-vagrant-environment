(X)Ubuntu Trusty Vagrant Environment
====================================
This repo is a vagrant vm container for [(X)Ubuntu Trusty Dev Setup](https://github.com/neilkidd/xubuntu-trusty-dev-setup) script development.

## Introduction
I needed to create a set of scripts for fast and easy provisioning of a broad development environment.

I was inspired by the work from [rails/rails-dev-box](https://github.com/rails/rails-dev-box) that uses [Vagrant](https://www.vagrantup.com/) and [Virtualbox (5)](https://www.virtualbox.org/) to achieve a rapidly, repeatable and disposable environment. Additionally, in theory, this should work from any host OS. I often find myself in both [Windows   &trade;](https://www.microsoft.com/en-us/windows) and [Linux](http://xubuntu.org/) environments.

I already had a baseline [xubuntu box](https://github.com/neilkidd/vagrant-atlas-xubuntu-14.04-desktop)  hosted in [Hashicorp's Atlas](https://atlas.hashicorp.com) so "tying it all together" was natural progression.

## Requirements
* [Virtualbox (5)](https://www.virtualbox.org/)
* [Vagrant](https://www.vagrantup.com/) installed
* An [Atlas](https://atlas.hashicorp.com) account
* Read access to [neil_kidd/xubuntu-14043-desktop](https://atlas.hashicorp.com/neil_kidd/boxes/xubuntu-14043-desktop)

## Usage
From a command line:

Login to [Atlas](https://atlas.hashicorp.com) , following the prompts.
```shell
$ vagrant login
```

Add the base box to your machine.
```shell
$ vagrant box add neil_kidd/xubuntu-14043-desktop
```

If you haven't already, clone [this](https://github.com/neilkidd/xubuntu-trusty-vagrant-environment) repo and cd into it.
```shell
$ git clone https://github.com/neilkidd/xubuntu-trusty-vagrant-environment.git
$ cd xubuntu-trusty-vagrant-environment
```

Clone the provisioning [repo](https://github.com/neilkidd/xubuntu-trusty-dev-setup). ( Or create a fork :smile:)
```shell
$ git clone https://github.com/neilkidd/xubuntu-trusty-dev-setup.git
```
Bring up the vm for the first time.  
**Important:**  '--no-provison' is required here as we intend to create an un-provisioned snapshot.
```shell
$ vagrant up --no-provision
```

Create a [snapshot](https://www.vagrantup.com/docs/cli/snapshot.html).
```shell
$ vagrant snapshot save clean_base
```

Excellent - we are now good to iterate. So stop the vm.
```shell
$ vagrant halt
```
### Iterating
To bring up the vm with the shell provisioning specified in the  [Vagrantfile](Vagrantfile):
```shell
$ vagrant snapshot restore clean_base
```
From within your host, you can now edit the provisioning code as you wish and cleanly bring up the vm with the above command.

### Cleaning Up
Issuing a ``` $ vagrant destroy ``` in the root directory will completely remove the local vm, along with any snapshots. This will not remove the base box from vagrant, so you may quickly start afresh.

## Credits
* [rails/rails-dev-box](https://github.com/rails/rails-dev-box) - for the formula and inspiration.
* [Hashicorp](https://www.hashicorp.com/) - for the amazing tooling.
* [Virtualbox](https://www.virtualbox.org/) - and I guess Oracle &trade; for the vm tech.


## License

Released under the [MIT License](LICENSE), Copyright (c) 2016–<i>ω</i> Neil Kidd.
