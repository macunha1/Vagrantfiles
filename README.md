# Vagrantfiles

Combo with a bunch of Vagrantfiles, to setup local and/or ephemeral Virtual machines.

The main motivation was to test [Ansible](https://www.ansible.com/). So, most of the Vagrantfiles carries `python` installed by default.
Also, they have a copy of the host machine default public RSA key, which allows easy connection with `ssh vagrant@$IP` which facilitates Ansible inventory setup

## Getting Started

### Prerequisites

These Vagranfiles create boxes using VirtualBox. So, before all, you need to go [here](https://www.virtualbox.org/wiki/Downloads) to download and install VirtualBox at your machine.

After installing VirtualBox, the [Vagrant download](https://www.vagrantup.com/downloads.html) and installation must be done.

Then, you're setted up!

## Quickstart

### Usage

To download all base vagrant boxes just run the following (assuming that you're on a POSIX/Unix/Linux-based operating system)
```shell
cat */Vagrantfile | awk '/config\.vm\.box/{print $NF}' | xargs -P 4 -I{} vagrant box add {} --provider virtualbox
```

You can configure your VM default values for vCPUs and RAM with:

```shell
export VAGRANT_CPU_CORE=2 # Number of vCPUs to dedicate

export VAGRANT_RAM_GB=4 # Allocated RAM in GB
```

Set those values in your `$HOME/.profile` or `${HOME}/${SHELL}rc` (as you wish) to store the configuration.

After downloading base boxes, you can run your desired operating system with

```shell
cd $DESIRED_OPERATING_SYSTEM && vagrant up
```

## Built With

* [Oracle VirtualBox](https://https://www.virtualbox.org/) - Oracle OpenSource virtualization product
* [HashiCorp Vagrant](https://www.vagrantup.com/) - Wrapper for virtualization

## Authors

* [**Matheus Cunha** ](https://github.com/macunha1)

See also the list of [contributors](https://github.com/macunha1/Vagrantfiles/contributors) who participated in this project.
