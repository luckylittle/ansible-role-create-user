Role Name
=========

A brief description of the role goes here.

Requirements
------------

```bash
# Log in as root and run
sed -i 's/^#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config
systemctl reload sshd
# Copy SSH key from your workstation to your target host
ssh-copy-id root@host
# Test if Ansible works
ansible seedbox -m ping -i inventory -u root
```

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
---
- hosts: seedbox
  remote_user: root
  vars:
    add_user: redhat
    add_user_passwd: redhat1
  roles:
    - ansible-role-create-user
```

Then run:

```bash
ansible-playbook -i inventory --vault-password-file=password site.yml
```

or

```bash

```

License
-------

MIT

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
