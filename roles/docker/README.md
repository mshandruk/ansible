docker
=========

* Linux
* ansible 2.10.8

Supported dists:

* Ubuntu22.04
* Debian11
* Centos7
* Centos9
* Fedora37

Role Variables
--------------

#### Optional

````
bip: <bridge_ip/prefix>
base_net: <base network ip/prefix>
size_nets: <the size of the created networks>
docker_user: <username>
````

Example Playbook
----------------

    - hosts: dockers
      roles:
         - { role: docker }

Quick start
-------

1. Clone this repository

2. Install public ssh-key on remote host

```
ssh-copy-id -i ~/.ssh/id_rsa.pub root@remote_address
```

3. Generate inventory

```bash
cat <<EOF  > inventory
[dockers]
debian.test.lab
EOF
```

4. Generate playbook

```bash
cat <<EOF  > play-docker.yml
- hosts: dockers
  roles:
     - { role: docker }
EOF
```

5. Run playbook

````
ansible-playbook -i inventory play-docker.yml -u root
````

Installation options
---------------
Install on local host:

```
sudo ansible-playbook -c local  docker.yml
```

Install on remote host:

```
ansible-playbook -i <address your host>, docker.yml
```

Install and add user in docker group:

``` 
ansible-playbook -i <address your host>, docker.yml -e docker_user=<your username>
```

Install with another docker network:

``` 
ansible-playbook -i <address your host>, docker.yml -e bip=10.30.0.0/16 -e base_net=10.0.0.0/8 -e size_nets=16
```

License
-------

MIT
