gateway
=========

A simple internet gateway

Role Variables
--------------
IFACE_LAN - name interface of Local Area Network

IFACE_WAN - name interface of World Area Network

Example Playbook
----------------

    - hosts: servers
      roles:
         - gateway

```
ansible-playbook gateway.yml -e IFACE_LAN=enp7s0 -e IFACE_WAN=enp1s0 -i addres,
```
License
-------

MIT
