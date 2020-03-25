# FortiADC python library for ansible
## INFO:
* Version: 0.3
* Date: 03/08/2019
* Author: JieLi <jieli@forinet.com>
* Supprt Version: 
1. Ansible v2.8.0.dev0
	* commit: b971ebd343c71aed705eb7b5a576c28e6dc9dee0
2. Ansible v2.7.8

## Installation Guide:
### Install Ansible from source:
1. git clone https://github.com/ansible/ansible.git --recursive
2. cd ./ansible
3. git reset --hard b971ebd343c71aed705eb7b5a576c28e6dc9dee0
4. source ./hacking/env-setup

[Ansible Installation Guide Page](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#running-from-source)

### Install fadcos library:
#### For from source
1. Copy the "lib/" to Ansible code base
#### For Latest Releases via Apt (Ubuntu)
1. Copy the folder "lib/ansible/plugins/ to "~/.ansible/" or "/usr/share/ansible/"
	* If "~/.ansible/" or "/usr/share/ansible/" are not exist please run "mkdir ~/.ansible/" or "mkdir /usr/share/ansible/"
2. Change "/etc/ansible/ansible.cfg"
	* library= \<lib base\>/lib/ansible/modules/
	* module_utils= \<lib base\>/lib/ansible/module_utils/


## Lib file tree:
	lib/
	└── ansible
	    ├── modules
	    │   └── network
	    │       └── fadcos
	    │           ├── fadcos_admin.py
	    │           ├── fadcos_backup_config.py
	    │           ├── fadcos_interface.py
	    │           ├── fadcos_nat_pool_member.py
	    │           ├── fadcos_nat_pool.py
	    │           ├── fadcos_real_server_pool_member.py
	    │           ├── fadcos_real_server_pool.py
	    │           ├── fadcos_real_server.py
	    │           ├── fadcos_route_static.py
	    │           ├── fadcos_shoutdown.py
	    │           ├── fadcos_system_setting.py
	    │           ├── fadcos_vdom.py
	    │           ├── fadcos_virtual_server_basic.py
	    │           ├── fadcos_virtual_server.py
	    │           └── __init__.py
	    ├── module_utils
	    │   └── network
	    │       └── fadcos
	    │           ├── fadcos.py
	    │           └── __init__.py
	    └── plugins
	        └── httpapi
	            └── fadcos.py
