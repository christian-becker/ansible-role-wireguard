wireguard
=========

This role installs and configures wireguard vpn and creates a suitable peer configuration. 
It can be used for initial installation or just for generating new keys. 

The following steps are performed: 
* install wireguard
* generate private and public keys for host and peer
* configure wireguard
* setup local firewall (ufw)
* enable and start services (ufw and wireguard)
* enable ip forwarding
* show infos about peer configuration


Requirements
------------

This role has no special requirements.


Role Variables
--------------

Here is a list of variables defined in **defaults/main.yml**: 

1.) Variables for wireguard host:
```
#optional - manually set external ip of host:
wg_local_externalip: 1.2.3.4

# vpn network address of host:
wg_local_address: 10.11.1.1/32
# port where wireguard listens:
wg_local_listenport: 51820
# vpn network interface of host:
wg_local_wgint: wg0
# physical network interface of host:
wg_local_ethint: eth0
```

2.) Variables for wireguard peer:
```
# vpn network address of peer:
wg_peer_address: 10.11.2.1/32
# vpn network interface of peer:
wg_peer_wgint: wg0
# dns server which the peer uses if connected via wireguard:
wg_peer_dns: 1.1.1.1
```


Dependencies
------------

This role has no dependencies.


Example Playbook
----------------

This role can be used e.g. with the following playbook: 
```
---
- name: installs and configures wireguard vpn and creates a suitable peer configuration
  hosts: all
  remote_user: root
  roles:
    - wireguard
```


License
-------

MIT


Author Information
------------------

* **Christian Becker** - [christian-becker](https://github.com/christian-becker)  

