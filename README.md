# Debian
Base debian OS configuration.

## [Requirements][i]
Requires [r_pufky.deb][g] galaxy-ng collection.

See [reference documentation][h] for specific Debian configuration.

## Role Variables
Detailed variable use documented in defaults. See usage for role operation.

* [defaults][j] - User configurable options.

## Usage
Debian defaults are used unless there are explicit security concerns.

These are generally small one-off changes that are always applied fleet wide.
Should be applied before any additional configuration is done to setup the
system in a known state (users, services, apt, etc).

### Example Playbooks

group_vars/all/vars/debian.yml
``` yaml
os_cfg_locales:
  - 'en_US.UTF-8'
os_cfg_default_system_locale: 'en_US.UTF-8'
os_cfg_timezone: 'Etc/UTC'
os_cfg_motd: ''
os_cfg_motd_extended_reboot_warning: 21
os_cfg_inotify_limit: 1048576
os_cfg_skeleton_files: 'group_vars/all/debian/skel'
os_cfg_reboot: '1month'
os_cfg_lockdown_home: true
os_cfg_tmp_ram: '1%'
```

Apply the base role
``` yaml
- name: 'Configure base Debian installation'
  ansible.builtin.include_role:
    name: 'r_pufky.deb.os'
```

## Development
Configure [environment][a].

``` bash
# Run all tests.
molecule test --all
```

### [Releases][b]

  Release | Debian | Ansible | Notes
 ---------|--------|---------|-------
  3.x.x   | 13     | 2.20    | Ansible 2.20, semantic versioning.
  2.x.x   | 13     | 2.18    | Migrate to Debian Trixie.
  1.x.x   | 12     | 2.18    | Use standardized libraries.
  0.x.x   | 12     | 2.11    | Migration from private repository.

## Issues
Create a bug and provide as much information as possible.

Associate pull requests with a submitted bug.

## License
[AGPL-3.0 License][c] | [direct link][f]

## Author Information
PGP: [466EEC2B67516C7117C85CE3A0BC35D16698BAB9][d] | [github gist][e]

[a]: https://r-pufky.github.io/ansible_docs
[b]: https://semver.org/spec/v2.0.0
[c]: https://www.tldrlegal.com/license/gnu-affero-general-public-license-v3-agpl-3-0
[d]: https://keys.openpgp.org/vks/v1/by-fingerprint/466EEC2B67516C7117C85CE3A0BC35D16698BAB9
[e]: https://gist.github.com/r-pufky/a8df36977c55b5bb20829267c4c49d22

[f]: https://github.com/r-pufky/ansible_debian_os/blob/main/LICENSE
[g]: https://github.com/r-pufky/ansible_collection_deb
[h]: https://r-pufky.github.io/docs/os/debian
[i]: https://github.com/r-pufky/ansible_debian_os/blob/main/meta/main.yml
[j]: https://github.com/r-pufky/ansible_debian_os/blob/main/defaults/main/main.yml