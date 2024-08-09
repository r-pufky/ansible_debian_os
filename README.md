# Debian
Fleetwide base debian OS configuration.

## Requirements
[supported platforms](https://github.com/r-pufky/ansible_debian/blob/main/meta/main.yml)

[collections/roles](https://github.com/r-pufky/ansible_debian/blob/main/meta/requirements.yml)

## Role Variables
[defaults](https://github.com/r-pufky/ansible_debian/blob/main/defaults/main)

## Dependencies
N/A

## Example Playbook
Apply base OS configuration to a Debian instance. Generally this should be
applied before any additional configuration is done to setup the system in a
known state (users, services, apt, etc).

Debian defaults are used unless there are explicit security concerns; see
defaults for all default values.

group_vars/all/vars/debian.yml
```
debian_apt_sources:
  - name: 'debian'
    types:
      - 'deb'
      - 'deb-src'
    uris: 'http://deb.debian.org/debian'
    suites:
      - 'bookworm'
      - 'bookworm-updates'
      - 'bookworm-backports'
    components:
      - 'main'
      - 'contrib'
      - 'non-free'
      - 'non-free-firmware'
    signed_by: '/usr/share/keyrings/debian-archive-keyring.gpg'
  - name: 'debian-security'
    types:
      - 'deb'
      - 'deb-src'
    uris: 'http://deb.debian.org/debian-security'
    suites:
      - 'bookworm-security'
    components:
      - 'main'
      - 'contrib'
      - 'non-free'
      - 'non-free-firmware'
    signed_by: '/usr/share/keyrings/debian-archive-keyring.gpg'
debian_apt_dist_upgrade_enable: true
debian_core_packages:
  - 'vim'
  - 'git'
  - 'git-lfs'
  - 'curl'
  - 'htop'
  - 'tmux'
debian_core_packages_absent:
  - 'mdadm'
debian_container_packages:
  - 'rng-tools5'
  - 'haveged'
debian_vm_packages:
  - 'haveged'
debian_unattended_enable: true
debian_unattended_upgrades: 1
debian_unattended_upgrade_origins_pattern:
  - origin: 'Debian'
    codename: 'S(distro_codename)-updates'
  - origin: 'Debian'
    codename: '${distro_codename}'
    label: 'Debian'
  - origin: 'Debian'
    codename: '${distro_codename}'
    label: 'Debian-Security'
  - origin: 'Debian'
    codename: '${distro_codename}-security'
    label: 'Debian-Security'
debian_ipv6_enable: true
debian_optimizations_tcp_bbr_enable: true
debian_optimizations_inotify_limit: 1048576
debian_optimizations_motd: ''
debian_optimizations_motd_extended_reboot: 21
debian_optimizations_lockdown_home: true
debian_optimizations_reboot: '1month'
debian_optimizations_reboot_variance: 300
debian_optimizations_tmp_ram: '1%'
debian_gpu_passthrough: false
debian_accounts:  # see r_pufky.srv.users.
  - 'ansible'
  - 'root'
  - 'some_user'
```

Apply the base role
``` yaml
- name: 'Apply base configuration'
  ansible.builtin.include_role:
    name: 'r_pufky.srv.debian'
```

## Unit Testing
Test framework requires molecule and rootless podman setup.

Run all unit tests:
``` bash
molecule test --all
```

## Issues
Create a bug and provide as much information as possible.

Associate pull requests with a submitted bug.

## License
[AGPL-3.0 License](https://www.tldrlegal.com/license/gnu-affero-general-public-license-v3-agpl-3-0)
 [(direct link)](https://github.com/r-pufky/ansible_fonts/blob/main/LICENSE)

## Author Information
PGP Fingerprint: [466EEC2B67516C7117C85CE3A0BC35D16698BAB9](https://keys.openpgp.org/vks/v1/by-fingerprint/466EEC2B67516C7117C85CE3A0BC35D16698BAB9)
| [github gist](https://gist.github.com/r-pufky/a8df36977c55b5bb20829267c4c49d22)


