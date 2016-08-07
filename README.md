[DevBox]
========

**The Bitaculous Development Box.**

Requirements
------------

* [Ansible]
* [Vagrant]

Quick Start
-----------

1. Clone the DevBox:

    ```
    $ git clone git@github.com:bitaculous/devbox.git
    ```

2. Provision the DevBox:

    ```
    $ cd devbox
    $ vagrant up
    ```

Usage
-----

### Boot-up / stop

```
$ vagrant up
$ vagrant halt
```

### Suspend / resume

```
$ vagrant suspend
$ vagrant resume
```

### Provisioning

```
$ vagrant provision
$ vagrant provision --provision-with ansible
$ vagrant provision --provision-with resume
$ vagrant reload --provision
```

### Secure Shell (SSH)

```
$ vagrant ssh
```

Databases
---------

### Export

```
$ mysqldump -h <HOST> -u <USERNAME> -p <DATABASE> --default-character-set=utf8 -r <NAME>.sql

$ mysqldump -h localhost -u root -p database --default-character-set=utf8 -r ./craft/database.sql
```

### Import

```
$ mysql -h <HOST> -u <USERNAME> -p <DATABASE> --default-character-set=utf8 < <NAME>.sql

$ mysql -h localhost -u root -p database --default-character-set=utf8 < ./craft/database.sql
```

System Configuration
--------------------

* OS: Debian Jessie
* RAM: 2GB

Network Configuration
---------------------

* Hostname: app.loc
* Ports:
    80   → 8080
    443  → 8443

Shares
------

* `craft`
* `htdocs`
* `log`
* `vendor`

Credits
-------

Credit goes to [Sven Lahann] for [vagrant-ansible].

License
-------

DevBox is released under the [MIT License (MIT)], see [LICENSE].

[Ansible]: http://www.ansible.com "The simplest way to automate."
[DevBox]: https://bitaculous.github.io/devbox/ "The Bitaculous Development Box."
[LICENSE]: https://raw.githubusercontent.com/bitaculous/devbox/master/LICENSE "License"
[MIT License (MIT)]: http://opensource.org/licenses/MIT "The MIT License (MIT)"
[Sven Lahann]: https://github.com/svenlahann "Sven Lahann"
[vagrant-ansible]: https://github.com/svenlahann/vagrant-ansible "Simple LAMP stack with Vagrant and Ansible"
[Vagrant]: https://www.vagrantup.com "Development environments made easy."