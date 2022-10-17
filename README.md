ansible-nfs
=========

This ansible role installs the NFS server and utilities.

Requirements
------------

Ansible 2.10.8

Role Variables
--------------

|Variable|Description|
|--------|-----------|
| nfs_exports | A list of exports which will be placed in the `/etc/exports` file. See Ubuntu's simple [Network File System (NFS)](https://ubuntu.com/server/docs/service-nfs) guide for more info and examples. (Simple example: `nfs_exports: [ "/mnt/public *(rw,sync,no_root_squash)" ]`). |
| owner | Configure a custom user for NFS shares, default: `www-data` |
| group | Configure a custom group for NFS shares, default: `www-data` |
| mode | Configure a custom permission for NFS shares, default: `u=rwX,g=rX,o=rX` |
| nfs_server_daemon | NFS daemon name in systemd |


Dependencies
------------
N/A

Example of how to use the role
----------------

    - hosts: localhost
      become: true
      gather_facts: yes
      
      vars:
        nfs_exports: [ "/mnt/public 10.17.1.0/255.255.255.0(rw,insecure,nohide,all_squash,anonuid=33,no_subtree_check)" ]
    roles:
      - role: ansible-nfs

License
-------

MIT

Author Information
------------------
[Yurii Onuk](https://onuk.org.ua)