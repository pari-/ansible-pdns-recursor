# ansible-pdns-recursor

An Ansible role which installs and configures PowerDNS recursor 

## Requirements

Currently this role is developed for and tested on Debian GNU/Linux (release: jessie). It is assumed to work on other Debian distributions as well.

Ansible version in use for development: 2.2.0

## Example

```yaml
- hosts: pdns-recursors

  roles: 
    - { role: ansible-pdns-recursor }
```

## Role Variables

Available variables are listed below, along with default values (see defaults/main.yml):

TBD

### Role Internals

- `pdns_recursor_prerequisites_supported_distribution_releases`

  > A list of distribution releases this role supports.
  >
  > `['wheezy', 'jessie', 'precise', 'trusty', 'utopic', 'vivid', 'wily', 'xenial', 'yakkety']`

- `pdns_recursor_prerequisites_apt_packages`

  > A list of apt package dependencyies.
  >
  > `[]`

- `pdns_recursor_prerequisites_apt_state`

  > Indicates the desired package state.
  >
  > `"present"`

- `pdns_recursor_prerequisites_apt_update_cache`

  > Run the equivalent of apt-get update before the operation.
  >
  > `"yes"`

- `pdns_recursor_prerequisites_apt_cache_valid_time`

  > Update the apt cache if its older than the x seconds.
  >
  > `3600`

- `pdns_recursor_install_apt_packages`

  > A list of apt package dependencyies.
  >
  > `['pdns-recursor']`

- `pdns_recursor_install_apt_state`

  > Indicates the desired package state.
  >
  > `"present"`

- `pdns_recursor_install_apt_update_cache`

  > Run the equivalent of apt-get update before the operation.
  >
  > `"yes"`

- `pdns_recursor_install_apt_cache_valid_time`

  > Update the apt cache if its older than the x seconds.
  >
  > `3600`

- `pdns_recursor_config_template_dest`

  > The path of the 'pdns_recursor'-configuration file
  >
  > `/etc/powerdns/recursor.conf`

## Dependencies

None

## License

MIT

## Author Information

* Patrick Ringl
