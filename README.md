ansible-openwisp2-iptables
==========================

iptables rules to protect an openwisp2 instance (see [ansible-openwisp2](https://github.com/nemesisdesign/ansible-openwisp2)) on **debian** and **ubuntu** systems.

Usage
=====

```yaml
- hosts: all

  roles:
  - nemesisdesign.openwisp2-iptables

  vars:
    # allowed SSH port, defaults to 22
    openwisp2_iptables_ssh_port: 22
    # by default VPN specific rules are disabled
    # if you want to enable them just tweak the following vars:
    openwisp2_iptables_vpn: false  # set this to true
    openwisp2_iptables_vpn_interface: "br-vpn"  # put here the vpn interface name
    openwisp2_iptables_vpn_port: 1194  # put here the vpn port
```
