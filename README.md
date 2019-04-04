NetCon Ansible Manager V1.6.0
=============================

A commandline GUI based on dialog to manage Ansible settings in complex environments.
It allows management of Inventories, Groups, Roles, ansible config settings and even ansible vault from a single interface.

<p align="center">
  <img src="https://raw.githubusercontent.com/netcon-consulting/nam/master/images/nam.png">
</p>



<p align="center">
  <img src="https://raw.githubusercontent.com/netcon-consulting/nam/master/images/group.png ">
</p>



<p align="center">
  <img src="https://raw.githubusercontent.com/netcon-consulting/nam/master/images/role.png">
</p>



<p align="center">
  <img src="https://raw.githubusercontent.com/netcon-consulting/nam/master/images/vault.png">
</p>


## Prerequisites:

* **vim**, **dialog**, **ansible**  
* additionally **gawk**, **gsed** if run on MacOS

We expect a SSH config file at **~/.ssh/config** and the following structure for the Ansible directory

```bash
ansible/
├── roles/
│   ├── some.role/
│   └── another.role/
├── inventory/
│   ├── hosts
│   ├── groups
│   └── companies (optional)
├── group_vars/
│   └── all/
│       └── vault.yml (optional)
├── ansible.cfg
└── site.yml
```
The Ansible configuration file **ansible.cfg** points to the **inventory** directory (config option _inventory = inventory_) which holds the files **hosts** containing the individual hosts, **groups** containing the functional groups and **companies** containing groups for different companies. The file **site.yml** is the main playbook and **vault.yml** the Ansible vault.

## Installation:

Copy **nam.sh** script to your Ansible directory.

## Usage notes:
* Adding a new host of type **production** will add the host parameters to the **hosts** file and SSH config. For host type **testing** a new host file named after the corresponding inventory host name will be created in the **inventory** directory.

* The **Company groups** menu is only available if a **companies** file exists. The **Export** function will create a tgz-archive with a custom Ansible directory for the selected company group. The function _company_export_ in the script probably will need some individual adjustment if you plan on using that feature.
