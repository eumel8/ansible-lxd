Ansible for LXD
===============

Intro
=====

LXD provides REST API to communicate with LXD container service.
The API includes
* List Container, Networks, Images, Profiles

and create and delete this kind of resources.


Content
=======
Here are some playbooks to demonstrate how to interact with LXD-API.

Documentation: https://github.com/lxc/lxd/blob/master/doc/rest-api.md


Roles
=====
    auth        get or create auth 

Requirements
============
* Ansible 2.0.1.0 (up version 2.2 you can use get_url with client certificate)
* Ubuntu 16.04.  (should work on all other *nix systems)
* credentials for lxd host (password)

Files
=====
| File | Description |
| --- | --- |
| secrets.yml | var file for LXD host and credentials (ansible-vault) |
| vaultpass.txt | password file for ansible-vault. The default password is: linux |
| hosts | host file for ansible (we use only localhost) |
| containers.yml | playbook to list containers |
| networks.yml | playbook to list networks |
| profiles.yml | playbook to list profiles |
| create.yml | playbook to create container |
| operations.yml | playbook to show operation events |
| show.yml | playbook to show container information |


Examples
========

list containers

    ansible-playbook -i hosts containers.yml --vault-password-file vaultpass.txt

show information about a container (u1)

    ansible-playbook -i hosts show.yml -e "CONTAINER=u1" --vault-password-file vaultpass.txt

list networks

    ansible-playbook -i hosts networks.yml --vault-password-file vaultpass.txt

list profiles

    ansible-playbook -i hosts profiles.yml --vault-password-file vaultpass.txt

list containers

    ansible-playbook -i hosts containers.yml --vault-password-file vaultpass.txt

create and start container u1 with Ubuntu 16.04 (Xenia)

    ansible-playbook -i hosts create.yml -e "CONTAINER=u1 VERSION=x" --vault-password-file vaultpass.txt


Contributing
------------

1. Fork it.
2. Create a branch (`git checkout -b my_markup`)
3. Commit your changes (`git commit -am "Added Snarkdown"`)
4. Push to the branch (`git push origin my_markup`)
5. Open a [Pull Request][1]
6. Enjoy a refreshing Diet Coke and wait

