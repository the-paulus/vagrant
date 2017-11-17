Vagrant
=========

Installs vagrant on MacOS and Linux

Requirements
------------

When applying this role to MacOS machines, the homebrew role is required.

Gentoo hosts need to have the common-linux-commands available due to the requirement of using the `euse` command.

Role Variables
--------------

```yml
vagrant_install_manager: yes

# For a full list of providers and plugins see: https://github.com/hashicorp/vagrant/wiki/Available-Vagrant-Plugins
vagrant_providers:
  - vagrant-managed-servers

vagrant_plugins:
  - vagrant-vbguest
  - vagrant-timezone
  - vagrant-clean
  - vagrant-landrush
  - vagrant-compose

vagrant_gentoo_use_flags: []
```

By default, vagrant works with VirtualBox. The `vagrant_install_manager` is a MacOS specific feature that is installed via homebrew.

For any additional providers and plugins see Hashicorp's list of available plugins [page](https://github.com/hashicorp/vagrant/wiki/Available-Vagrant-Plugins)

`vagrant_gentoo_use_flags` is a Gentoo specific variable.

Dependencies
------------

Linux hosts do not require any dependencies with the exception of Gentoo that needs the common-linux-commands role. However, MacOS hosts require that the homebrew role be available.

Example Playbook
----------------

```yml
- hosts: linux-hosts
  roles:
    - the-paulus.vagrant

- hosts: macos-hosts
  roles:
    - the-paulus.homebrew
    - the-paulus.vagrant
```

License
-------

BSD
