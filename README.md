ansible-role-create-user
=========

Adds user to a brand new RHEL system for use with Ansible. It automatically creates a local user with defined password and also distributes the SSH public key of the user who runs this role (it assumes `~/.ssh/id_rsa.pub`).

Requirements
------------

* It is expected, that you have a brand new RHEL system and have `root` access. In order for this role to be able to work, the following changes need to be made first:

```bash
# Log in as root and run. This role will revert this back at the end, so don't worry:
sed -i 's/^#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config
systemctl reload sshd
exit

# Copy SSH key from your workstation to your root user on target host
ssh-copy-id root@host

# Test if Ansible ping works now without a password
ansible seedbox -m ping -i host, -u root
```

Role Variables
--------------

`defaults/main.yml`:

* `add_user` - defines the user to be added, default is `redhat`
* `add_user_passwd` - defines the password of the newly created user, default is `r3dh4t`

Dependencies
------------

None

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
---
- hosts: seedbox
  remote_user: root
  vars:
    add_user: seedbox
    add_user_passwd: supersecretpassword
  roles:
    - ansible-role-create-user
```

Then run:

```bash
echo 'password1' > password
```

```bash
ansible-playbook -i inventory --vault-password-file=password site.yml
```

Another example of the same:

```bash
ansible-playbook -i 192.168.1.1, -e add_user=seedbox -e add_user_passwd=supersecretpassword site.yml
```

License
-------

MIT

Author Information
------------------

Lucian Maly <<lmaly@redhat.com>>
