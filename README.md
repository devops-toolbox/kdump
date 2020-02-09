Role Name
=========

kdump: Kdump

[![Build Status](https://travis-ci.org/cmihai-ansible/kdump.svg?branch=master)](https://travis-ci.org/cmihai-ansible/kdump)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devops-toolbox.kdump](https://galaxy.ansible.com/devops-toolbox.kdump)

```bash
ansible-galaxy install devops-toolbox.kdump
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
kdump_packages_state: present
kdump_remove_packages: true
kdump_enable_service: true
kdump_enable_selinux: true
kdump_copy_templates: true
kdump_firewall_configure: true
kdump_firewall_rules:
  - service: ssh
  - port: 3389
kdump_users:
  - user: devops
    group: docker
kdump_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install kdump on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: kdump is configured
      import_role:
        name: devops-toolbox.kdump
      vars:
        kdump_packages_state: present
        kdump_remove_packages: true
        kdump_enable_service: true
        kdump_enable_selinux: true
        kdump_copy_templates: true
        kdump_firewall_configure: true
        kdump_firewall_rules:
          - service: ssh
          - port: 3389
        kdump_users:
          - user: devops
            group: docker
        kdump_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: kdump
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devops-toolbox.)
