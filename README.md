# Ansible
###### __... a suite of software tools that enables infrastructure as code.__
### _Ansible playbooks for my personal use..._



Ansible documentation: https://docs.ansible.com/
This setup is testet in my production enviroment. Please adjust to your own enviroment and preferences.

## Hardware setup

### _My server setup setup:_
- Ubuntu 22.04
- Raspberry Pi v. [1, 2, 3, 4]
- Intel Nuc

### _My Ansible host setup:_
- Arch Linux
- Generic laptop

## Installation

Install OpenSSH and corresponding ssh-keys at your servers

```sh
sudo apt install openssh-server
```

Install Ansible

```sh
pacman -S ansible-core
```

Ajust hosts and ansible.cfg in /etc/ansible/ to your needs

Check if all the nodes listed in the inventory are alive by running the command below

```sh
$ ansible all -m ping
```

## Ansible cmd examples
Dry run
```sh
$ ansible-playbook -K update_pb.yml --extra-vars="nodes=<HOST>" --check
```
Update server single node or group in HOST
```sh
$ ansible-playbook -K update_pb.yml --extra-vars="nodes=<HOST>"
```
Install <PACKAGE> with apt on server single node or group in HOST
```sh
$ ansible-playbook apt-install_pb.yml -K --extra-vars="nodes=<HOST>, package=<PACKAGE>"
```
Remove PACKAGE with apt on server single node or group in HOST
```sh
$ ansible-playbook apt-remove_pb.yml -K --extra-vars="nodes=<HOST>, package=<PACKAGE>"
```
Skip HOST in inventory group
```sh
$ ansible-playbook ping-all_pb.yml --limit '!<HOST>'
```
List the inventory in a "graph" way
```sh
$ ansible-inventory --graph -i hosts
```

## Note!!!

Ansible {options] :

- -K -> elevate user calling sudo
- -l -> runs specific group from inventory file
- -i -> path to inventory file
- --check -> dry run
- --limit -> override og add spicific host to use with playbook

## License


**Free Software... But of Course!**

Copyright [2023] [PeterWeissDK]

This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program. If not, see <https://www.gnu.org/licenses/>.

###### _I used [Apostrophe](https://apps.gnome.org/Apostrophe/) to create this file_

[//]: # (misc. -comments)

