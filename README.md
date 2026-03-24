# Ansible Collection - nils_ost.nlpt_kiosk

This repository contains the `nils_ost.nlpt_kiosk` Ansible Collection. For installing a [NLPT-Kiosk-Controller](https://github.com/nlptournament/nlpt-kiosk) and connected Raspberry Pi based Kiosks.

<!--start requires_ansible-->
<!--end requires_ansible-->

## External requirements

Requires python library `jsonschema` to validate variables. Please install via pip on ansible controller.

## Included content

<!--start collection content-->
<!--end collection content-->

### Roles

Name | Description
--- | ---
[nils_ost.nlpt_kiosk.controller](https://github.com/nils-ost/ansible-collection-nlpt_kiosk/blob/main/roles/controller/README.md)|installs NLPT-Kiosk-Controller within docker
[nils_ost.nlpt_kiosk.rpi](https://github.com/nils-ost/ansible-collection-nlpt_kiosk/blob/main/roles/rpi/README.md)|configures Raspberry Pi to be used as Kiosk

## Using this collection

```bash
ansible-galaxy collection install nils_ost.nlpt_kiosk
```

You can also include it in a `requirements.yml` file and install it via
`ansible-galaxy collection install -r requirements.yml` using the format:

```yaml
collections:
  - name: nils_ost.nlpt_kiosk
```

To upgrade the collection to the latest available version, run the following
command:

```bash
ansible-galaxy collection install nils_ost.nlpt_kiosk --upgrade
```

You can also install a specific version of the collection, for example, if you
need to downgrade when something is broken in the latest version (please report
an issue in this repository). Use the following syntax where `X.Y.Z` can be any
[available version](https://galaxy.ansible.com/nils_ost/nlpt_kiosk):

```bash
ansible-galaxy collection install nils_ost.nlpt_kiosk:==X.Y.Z
```

See
[Ansible Using Collections](https://docs.ansible.com/ansible/latest/user_guide/collections_using.html)
for more details.

## Release notes

See the
[changelog](CHANGELOG.md).

## Roadmap

This collection is mainly intended to be used by and for NLPT. But other LAN-Partys (or people who need a Kiosk-System) are welcome to adopt our system.
If you like to see some automation added to this collection feel free, to open an issue at [https://github.com/nils-ost/ansible-collection-nlpt_kiosk/issues](https://github.com/nils-ost/ansible-collection-nlpt_kiosk/issues). The NLPT-Kiosk-Controller itself is maintained under [https://github.com/nlptournament/nlpt-kiosk](https://github.com/nlptournament/nlpt-kiosk) check out it's README for more information about this project.

## Licensing

GNU General Public License v3.0 or later.

See [LICENSE](LICENSE) to see the full text.
