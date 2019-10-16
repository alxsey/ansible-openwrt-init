Role Name
=========

Initializes OpenWrt based router. Sets up basics, like enabling ssh (setting up password) and setting up networking. 

Routers are identified by MAC address.

Requirements
------------

There is few requirements. JMESPath libraries, as well as telnet, ping and arp executables 

Role Variables
--------------

By default router is assumed to be at "192.168.1.1" (initial_ip) which is defined by variabes in defaults/main.yml
as well as netmask "255.255.255.0" (default_netmask), default user "root"  (user) and default password "openwrt" (password). 
Router is idetified by MAC address (main_mac) in the inventory. 

ansible_host could define router IP address (not initial). Also inventory could supply user and password to override defaults.
Rest of routers settings are defined in dictionaries that resembles uci settings (same as in lefant.openwrt- roles)

At the moment only supported:
dhcp.lan.ignore
network.lan.netmask

If information above does not exist - will disable dhcp unless routers IP address is same as ansible host default gateway.
Netmask will be defaulted to 255.255.255.0

Dependencies
------------

Depends on lefant.openwrt-uci role in order to use uci commands.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: localhost
      roles:
         - { role: lefant.openwrt-uci }
         - { role: alxsey.openwrt_init }

License
-------

GPLv2

Author Information
------------------

Alex Ryabtsev
