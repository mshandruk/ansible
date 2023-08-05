Kvm
=========

A role kvm

Role Variables
--------------
username: <username add to groups: libvirt, libvirt-qemu>

Example Playbook
----------------

    - hosts: kvm
      become: true
      roles:
         - { role: kvm }

1. Clone this repository

2. Install public ssh-key on remote host

```
ssh-copy-id -i ~/.ssh/id_rsa.pub root@debian.test.lab
```

3. Generate inventory

```bash
cat <<EOF  > inventory
[kvm]
debian.test.lab
EOF
```

4. Generate playbook

```
cat <<EOF  > play-kvm.yml
- hosts: kvm
  become: true
  roles:
     - { role: kvm }
EOF
```

5. Run playbook

Install kvm

````
ansible-playbookkvm.yml -i inventory -u root
````

Install kvm and virt-manager(for GUI)

````
ansible-playbookkvm.yml -i inventory -u root --tags=virt-manager
````

License
-------

MIT
