# Debian
Base debian OS configuration.

## Requirements
[supported platforms](https://github.com/r-pufky/ansible_debian/blob/main/meta/main.yml)

[collections/roles](https://github.com/r-pufky/ansible_debian/blob/main/meta/requirements.yml)

## Role Variables
[defaults](https://github.com/r-pufky/ansible_debian/blob/main/defaults/main)

## Dependencies
Part of the [r_pufky.srv](https://github.com/r-pufky/ansible_collection_srv)
collection.

## Example Playbook
Apply base OS configuration optimizations to a Debian instance. These are
generally small one-off changes that are always applied fleetwide. Should be
applied before any additional configuration is done to setup the system in a
known state (users, services, apt, etc).

Debian defaults are used unless there are explicit security concerns; see
defaults for all default values.

group_vars/all/vars/debian.yml
``` yaml
debian_locales:
  - 'en_US.UTF-8'
debian_default_system_locale: 'en_US.UTF-8'
debian_timezone: 'Etc/UTC'
debian_motd: ''
debian_motd_extended_reboot_warning: 21
debian_inotify_limit: 1048576
debian_skeleton_files: 'group_vars/all/debian/skel'
debian_reboot: '1month'
debian_lockdown_home: true
debian_tmp_ram: '1%'
```

Apply the base role
``` yaml
- name: 'Apply base configuration'
  ansible.builtin.include_role:
    name: 'r_pufky.srv.debian'
```

## Development
Configure [environment](https://github.com/r-pufky/ansible_collection_srv/blob/main/docs/dev/environment/README.md)

Run all unit tests:
``` bash
molecule test --all
```

### Issues
Create a bug and provide as much information as possible.

Associate pull requests with a submitted bug.

## License
[AGPL-3.0 License](https://www.tldrlegal.com/license/gnu-affero-general-public-license-v3-agpl-3-0)
 [(direct link)](https://github.com/r-pufky/ansible_debian/blob/main/LICENSE)

## Author Information
PGP Fingerprint: [466EEC2B67516C7117C85CE3A0BC35D16698BAB9](https://keys.openpgp.org/vks/v1/by-fingerprint/466EEC2B67516C7117C85CE3A0BC35D16698BAB9)
| [github gist](https://gist.github.com/r-pufky/a8df36977c55b5bb20829267c4c49d22)
