### This file contains important information about the basics of Ansible and Ansible systax

- {start:end} – to create multiple hosts or IPs with less typing.
- List modules – ansible-doc module –l  , ansible-doc copy – info about copy module.
- Check if a package is installed on a remote host: ansible -a 'yum list installed mariadb*'
- Use inventory_hostname in groups['mailservers']  -- use this to check if a mailservers group is present in inventory

#### Error Handling:

- Handlers: 
    - Add with_items and notify in line with the module name.
    - Handlers keyword is placed in line with the keyword tasks.  

- ignore_errors: yes -- add this to ignore any errors in a task and move ahead with the rest of the playbook.
- force_handlers: yes -- if mentioned then the notified handlers will still run even if any task fails.
- failed_when: run a task, get an output, read the output - and decide using failed_when keyword.
- changed_when: false -- only report if the output is ok or failed. Set to true to run a handler regardless.
- block and tags/when: add the keyword block under tasks and then use the keyword tags/when at the end to decide if a play can be run 

    - block: Defines the main tasks to run.
    - rescue: Defines the tasks that will be run if the tasks defined in the block clause fails.
    - always: Defines the tasks that will always run independently of the success or failure of tasks
defined in the block and rescue clauses.

#### See contents of a file using the following Ansible command
- ansible everyone -m command -a 'cat /etc/motd' –u

#### Tags
Tags let you run playbooks on specific plays only instead of running the whole playbook with all tasks.

- ansible-playbook web playbook.yml --tags dev -- run tasks from this playbook whose tag is labelled as dev 
- ansible-playbook web playbook.yml --skip-tags prod -- skip tasks whose tag is prod.

#### How to define dependencies:

``` yml
--- 
dependencies:
  - { role: common, some_parameter: 3 }
  - { role: apache, apache_port: 80 }
```

#### Set local variable and call a role in the main playbook:

roles:
- role: myapache
apache_enable: true

#### Delegate tasks to a different host:

Delegate to localhost
delegate_to: localhost
local_action: command ps (the command ps will be run on localhost)
add_host:
  name: Lolo
  ansible_host: 172.16.23.12
  ansible_user: devops