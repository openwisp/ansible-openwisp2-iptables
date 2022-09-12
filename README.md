ansible-openwisp2-iptables
==========================

[![Galaxy](https://img.shields.io/badge/galaxy-openwisp.openwisp2--iptables-blue.svg?style=flat-square)](https://galaxy.ansible.com/openwisp/openwisp2-iptables/)

Ansible role that sets iptables firewall rules to protect an openwisp2 instance (see [ansible-openwisp2](https://github.com/openwisp/ansible-openwisp2)) on **debian** and **ubuntu** systems.

Usage
=====

```yaml
- hosts: all

  roles:
  - openwisp.openwisp2-iptables

  vars:
    # Allowed SSH port, defaults to 22
    openwisp2_iptables_ssh_port: 22
    # Configure rules to allow traffic for VPN interfaces.
    # You can specify port, protocol and interface name
    # for multiple VPN interfaces as show below
    openwisp2_iptables_vpn_rules:
      # OpenVPN
      - protocol: udp
        port: 1194
        interface: tun0
      # WireGuard:
      - protocol: udp
        port: 51820
        interface: wg0
    # Configure ports to allow traffic for the SMTP mail server
    openwisp2_iptables_smtp_ports: [25, 587]
    # Configure ports to allow traffic for the FreeRADIUS server
    openwisp2_iptables_freeradius_ports: [1812, 1813]
    # Configure port to allow traffic for the WireGuard updater
    # Flask app
    openwisp2_iptables_wireguard_flask_port: 8081
    # Configure port to allow traffic (both TCP and UDP) for
    # the Iperf3 server
    openwisp2_iptables_iperf_port: 5201
    # Configure port to allow traffic for the OWLP internet mode
    # webpage
    openwisp2_iptables_owlp_internet_mode_port: null
    # Configure additional iptables rule using the following variable
    openwisp2_iptables_additional_rules: []
```

**Note:** By default, all incoming traffic is dropped except
for SSH, HTTP and HTTPS. If you don't configure any of the variables
above, then traffic for that service will be dropped.
