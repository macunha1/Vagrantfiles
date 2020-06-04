# Vagrantfiles

Combo with a bunch of Vagrantfiles, to setup local and/or ephemeral Virtual
machines.

The main motivation was to test [Ansible](https://www.ansible.com/). So, most
of the Vagrantfiles carries `python` installed by default.
Also, they have a copy of the host machine default public RSA key, which allows
easy connection with `ssh vagrant@$IP` facilitating Ansible inventory setup

## Getting Started

### Prerequisites

Install a VM provider supported by Vagrant, most popular is [VirtualBox](https://www.virtualbox.org/wiki/Downloads).

For libvirt support the following plugin is necessary

```bash
vagrant plugin install vagrant-libvirt
```

Last step is (of course) [Vagrant](https://www.vagrantup.com/downloads.html).

Then, you're setted up!

## Quickstart

### Usage

To download all base vagrant boxes just run the following (assuming that
you're on a POSIX/Unix/Linux-based operating system)

```shell
find . -name Vagrantfile -type f \
    -exec awk '/config\.vm\.box/{print $NF}' {} + | \
    sort | uniq | \
    xargs -P 4 -I{} vagrant box add {} \
        --provider "${VAGRANT_PROVIDER:-virtualbox}"
```

You can configure your VM default values for vCPUs and RAM with:

```shell
export VAGRANT_CPU_CORE=2 # Number of vCPUs to dedicate
export VAGRANT_RAM_GB=4 # Allocated RAM in GB
export VAGRANT_PROVIDER=libvirt # alternative VM provider
export VAGRANT_IPV4_ADDRESS=192.168.50.111 # default Ipv4 address for VM
```

Set those values in your `$HOME/.profile` or `${HOME}/${SHELL}rc` (as you wish)
to store the configuration.

After downloading base boxes, you can run your desired operating system with

```shell
cd $DESIRED_OPERATING_SYSTEM && vagrant up
```

## Contribute

[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)

- Feel free to fill [an issue with feature request(s)](https://github.com/macunha1/vagrantfiles/issues),
or to send me a Pull request, I will be happy to collaborate.

- If the code don't work, or if you found some bug during the execution, let me know.

[![](https://sourcerer.io/fame/macunha1/macunha1/vagrantfiles/images/0)](https://sourcerer.io/fame/macunha1/macunha1/vagrantfiles/links/0)[![](https://sourcerer.io/fame/macunha1/macunha1/vagrantfiles/images/1)](https://sourcerer.io/fame/macunha1/macunha1/vagrantfiles/links/1)[![](https://sourcerer.io/fame/macunha1/macunha1/vagrantfiles/images/2)](https://sourcerer.io/fame/macunha1/macunha1/vagrantfiles/links/2)[![](https://sourcerer.io/fame/macunha1/macunha1/vagrantfiles/images/3)](https://sourcerer.io/fame/macunha1/macunha1/vagrantfiles/links/3)[![](https://sourcerer.io/fame/macunha1/macunha1/vagrantfiles/images/4)](https://sourcerer.io/fame/macunha1/macunha1/vagrantfiles/links/4)[![](https://sourcerer.io/fame/macunha1/macunha1/vagrantfiles/images/5)](https://sourcerer.io/fame/macunha1/macunha1/vagrantfiles/links/5)[![](https://sourcerer.io/fame/macunha1/macunha1/vagrantfiles/images/6)](https://sourcerer.io/fame/macunha1/macunha1/vagrantfiles/links/6)[![](https://sourcerer.io/fame/macunha1/macunha1/vagrantfiles/images/7)](https://sourcerer.io/fame/macunha1/macunha1/vagrantfiles/links/7)
