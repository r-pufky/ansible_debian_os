# Debian
Base debian OS configuration.

## Requirements
[supported platforms](https://github.com/r-pufky/ansible_debian/blob/main/meta/main.yml)

## Role Variables
[defaults](https://github.com/r-pufky/ansible_debian/blob/main/defaults/main)

## Dependencies
**galaxy-ng** roles cannot be used independently. Part of
[r_pufky.deb](https://github.com/r-pufky/ansible_collection_deb) collection.

## Example Playbook
Apply base OS configuration optimizations to a Debian instance. These are
generally small one-off changes that are always applied fleetwide. Should be
applied before any additional configuration is done to setup the system in a
known state (users, services, apt, etc).

Debian defaults are used unless there are explicit security concerns; see
defaults for all default values.

group_vars/all/vars/debian.yml
``` yaml
os_locales:
  - 'en_US.UTF-8'
os_default_system_locale: 'en_US.UTF-8'
os_timezone: 'Etc/UTC'
os_motd: ''
os_motd_extended_reboot_warning: 21
os_inotify_limit: 1048576
os_skeleton_files: 'group_vars/all/debian/skel'
os_reboot: '1month'
os_lockdown_home: true
os_tmp_ram: '1%'
```

Apply the base role
``` yaml
- name: 'Apply base configuration'
  ansible.builtin.include_role:
    name: 'r_pufky.deb.os'
```

## Development
Configure [environment](https://github.com/r-pufky/ansible_collection_docs/blob/main/ansible/environment.md)

Run all unit tests:
``` bash
molecule test --all
```

### Releases
Major release versions track Debian release versions:

* **[13.x.x](https://github.com/r-pufky/ansible_debian_os)**: 13 Trixie.
* **[12.x.x](https://github.com/r-pufky/ansible_debian_os/tree/12.x)**: 12 Bookworm.

### Issues
Create a bug and provide as much information as possible.

Associate pull requests with a submitted bug.

## License
[AGPL-3.0 License](https://www.tldrlegal.com/license/gnu-affero-general-public-license-v3-agpl-3-0)
 [(direct link)](https://github.com/r-pufky/ansible_debian/blob/main/LICENSE)

## Author Information
PGP Fingerprint: [466EEC2B67516C7117C85CE3A0BC35D16698BAB9](https://keys.openpgp.org/vks/v1/by-fingerprint/466EEC2B67516C7117C85CE3A0BC35D16698BAB9)
| [github gist](https://gist.github.com/r-pufky/a8df36977c55b5bb20829267c4c49d22)
