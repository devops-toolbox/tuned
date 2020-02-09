Role Name
=========

tuned: Tuned

[![Build Status](https://travis-ci.org/cmihai-ansible/tuned.svg?branch=master)](https://travis-ci.org/cmihai-ansible/tuned)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.tuned](https://galaxy.ansible.com/devopstoolbox.tuned)

```bash
ansible-galaxy install devopstoolbox.tuned
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
tuned_packages_state: present
tuned_remove_packages: true
tuned_enable_service: true
tuned_enable_selinux: true
tuned_copy_templates: true
tuned_firewall_configure: true
tuned_firewall_rules:
  - service: ssh
  - port: 3389
tuned_users:
  - user: devops
    group: docker
tuned_selinux_booleans:
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
- name: Install tuned on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: tuned is configured
      import_role:
        name: devopstoolbox.tuned
      vars:
        tuned_packages_state: present
        tuned_remove_packages: true
        tuned_enable_service: true
        tuned_enable_selinux: true
        tuned_copy_templates: true
        tuned_firewall_configure: true
        tuned_firewall_rules:
          - service: ssh
          - port: 3389
        tuned_users:
          - user: devops
            group: docker
        tuned_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: tuned
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devopstoolbox.)
