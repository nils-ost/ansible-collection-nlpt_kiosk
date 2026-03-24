# nils_ost.nlpt_kiosk.rpi

**configures Raspberry Pi to be a Kiosk, connected to NLPT-Kiosk-Controller**

Version added: 1.0.0

- [nils\_ost.nlpt\_kiosk.rpi](#nils_ostnlpt_kioskrpi)
  - [Synopsis](#synopsis)
  - [Role Variables](#role-variables)
  - [Full Example](#full-example)
    - [Playbook](#playbook)
    - [Group Vars](#group-vars)


## Synopsis

A role for configuring a Raspberry Pi to act as a Kiosk, that is connected to NLPT-Kiosk-Controller.

Before executing this role you have to flash an SD-Card with Raspberry Pi OS including the Desktop in the 64bit variant.  
After bootup configure the following basics:

  * enable and start ssh(-daemon)
  * Hostname
  * IP-address
  * Default-Gateway
  * DNS-Server

> [!TIP]
> The usage of a Raspberry Pi 4 or 5 with at least 2GB of RAM is strongly recommended.

> [!CAUTION]
> This role only supports Debian-Trixie and -Bookworm based Raspberry Pi OS. Other versions will cause an error.

> [!IMPORTANT]
> The Ansible variable `inventory_hostname` is set as the unique name identifying the Kiosk at the Controller.  
> The Ansible variable `ansible_user` is used for some file-permissions, therefore prefer using user `pi` to login and `become` root, see the full example below.


## Role Variables

| Variable                 | Type | Default                             | Comment                                                              |
| ------------------------ | ---- | ----------------------------------- | -------------------------------------------------------------------- |
| nkc_timezone             | str  | Europe/Berlin                       | timezone to be set for Kiosk                                         |
| nkc_kiosk_enable_vnc     | bool | false                               | wether to enable or disable (default) the VNC-server on Raspberry Pi |
| nkc_kiosk_ntp_server     | str  | kiosk-controller.domain             | Domain of NLPT-Kiosk-Controller to be used a NTP-server              |
| nkc_kiosk_controller_url | str  | "http://{{ nkc_kiosk_ntp_server }}" | Full URL where NLPT-Kiosk_Controller is reachable                    |
| nkc_kiosk_boot_mode      | str  | kiosk                               | wether to boot pi to "desktop" or in "kiosk" mode                    |

> [!NOTE]
> `nkc_kiosk_boot_mode` only affects the wayland autostart feature, everything else is configured as usual for a Kiosk

## Full Example

### Playbook

`play_kiosks.yml`

```yaml
---
- name: Setup RaspberryPis to serve as a Kiosk
  hosts: kiosks
  become: true

  roles:
    - nils_ost.nlpt_kiosk.rpi
```

### Group Vars

`group_vars/kiosks.yml`

```yaml
---
ansible_user: pi
nkc_kiosk_ntp_server: some.local.controller
```
