#### Ansible-VMware Playbooks

This repository contains my Ansible playbooks which I created to manage VMware, JIRA, and networking environments.

Dependencies:
- pyvmomi
- python > 2.6

Special settings:
- validate_certs: no

Create passwordless access to VMs:
- On a Ansible host, run the "ssh-keygen" command to a SSH key.
- The public key will be stored at "~/.ssh/id_rsa.pub"
- cat ~/.ssh/id_rsa.pub | ssh root@IP 'cat >> /etc/ssh/keys-root/authorized_keys' (on ESXi hosts)
- cat ~/.ssh/id_rsa.pub | ssh root@IP 'cat >> /root/.ssh/authorized_keys' (on Linux hosts)
- Type the root password when prompted.
- Passwordless login is now enabled from the Ansible host VM/server.

VMware environment:
- ESXi 6.5

Modules used:
- vmware_host_ntp					 set ntp servers
- vmware_vmotion					 vmotion vms	
- vmware_host_service_manager 	 check ntp service status
