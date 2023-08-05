# ansible-infra
Collection ansible roles and playbooks

### Install ansible

Debian like
```
apt -y install ansible sshpass
```

Centos
```
yum -y install epel-release
yum -y install ansible sshpass
```

Fedora
```
dnf -y install ansible sshpass
```

### Inventory
https://docs.ansible.com/ansible/2.8/user_guide/playbooks_best_practices.html#alternative-directory-layout

Show inventory
````
ansible-inventory -i inventories/test --list
````

### Examples usage

For example tests inventory

Install key on remote hosts (root)
```
ansible-playbook playbooks/upload-sshkey.yml -i inventories/test -e username="root" -u root -k
```
Special user sa (Ubuntu)
```
ansible-playbook playbooks/upload-sshkey.yml -i inventories/test -e username="sa" -l ubuntu.test.lab -u sa -k -b -K
```

Check alive hosts
```
ansible -i inventories/test -m ping all -u root
```
