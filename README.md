#### Ansible-VMware Playbook

This repository contains my Ansible playbooks which I created to manage a VMware environment.

Dependencies:
pyvmomi
python > 2.6

Special settings:
validate_certs: no

VMware environment:
ESXi 6.5

Modules used:
vmware_host_ntp					 set ntp servers
vmware_vmotion					 vmotion vms	
vmware_host_service_manager 	 check ntp service status
