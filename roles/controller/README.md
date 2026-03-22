# nils_ost.nlpt_kiosk.controller

**installs NLPT-Kiosk-Controller within docker**

Version added: 1.0.0

- [nils\_ost.nlpt\_kiosk.controller](#nils_ostnlpt_kioskcontroller)
  - [Synopsis](#synopsis)
  - [Role Variables](#role-variables)
  - [Example](#example)


## Synopsis

A role for installing NLPT-Kiosk-Controller as a docker container with the help of compose.

This role mainly just creates the compose directory, places the compose-file and executes `docker compose up`.
It requires docker to be already installed on target system, including the compose plugin.
You might want to take a look at [geerlingguy.docker](https://github.com/geerlingguy/ansible-role-docker) to install docker on your system.


## Role Variables

| Variable                     | Type | Default         | Comment                                                                                           |
| ---------------------------- | ---- | --------------- | ------------------------------------------------------------------------------------------------- |
| nkc_timezone                 | str  | Europe/Berlin   | timezone to be set for containers                                                                 |
| nkc_controller_compose_dir   | str  | /opt/nkc        | location where compose-file and volume directorys are created                                     |
| nkc_controller_release       | str  | latest          | release-train (latest, beta, alpha) or specific release version (v1.0.0) if NLPT-Kiosk-Controller |
| nkc_controller_auto_upgrade  | bool | false           | whether container image is updated on role run or not                                             |
| nkc_controller_bind_ip       | str  | 0.0.0.0         | IP at which NLPT-Kiosk-Controller should be available at on the server, 0.0.0.0 equals to all     |
| nkc_controller_monitoring_ip | str  | 0.0.0.0         | If you have a separate monitoring network, bind the corresponding IP here                         |
| nkc_controller_ntp_server    | str  | de.pool.ntp.org | Upstream timeserver(s) for the builtin timeserver                                                 |


## Example

`group_vars/kiosk_controller.yml`

```yaml
---
nkc_controller_compose_dir: /opt/services/nkc
nkc_controller_release: v1.1.0
nkc_controller_auto_upgrade: true
```
