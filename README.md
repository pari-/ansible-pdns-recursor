# pdns-recursor

[![Build Status](https://travis-ci.org/pari-/ansible-pdns-recursor.svg?branch=master)](https://travis-ci.org/pari-/ansible-pdns-recursor)

An Ansible role which installs and configures PowerDNS recursor

<!-- toc -->

- [Requirements](#requirements)
- [Example](#example)
- [Defaults](#defaults)
- [Dependencies](#dependencies)
- [License](#license)
- [Author Information](#author-information)

<!-- tocstop -->

## Requirements

Currently this role is developed for and tested on Debian GNU/Linux (release: jessie). It is assumed to work on other Debian distributions as well.

Ansible version compatibility: [Dockerfile](https://github.com/pari-/docker-debian-ansible/blob/master/debian/stretch/Dockerfile)

## Example

```yaml
---

- hosts: "all"
  vars:
    _timeout: 5
    _host: "google.com"
  roles:
    - role: "ansible-pdns-recursor"
      tags:
        - "pdns-recursor"
  post_tasks:
    - block:
        - include: "tests/test_dns_resolving.yml"
      tags:
        - "tests"
```

## Defaults

Available variables are listed below, along with default values (see defaults/main.yml). They're generally prefixed with `pdns_recursor_` (which I deliberately leave out here for better formatting).

variable | default | notes
-------- | ------- | -----
`cache_valid_time` | `3600` | `Update the apt cache if its older than the set value (in seconds)`
`config_file` | `/etc/powerdns/recursor.conf` | `Absolute path to pdns_recursor's configuration file`
`config_opts` | ` ` | `Configuration hash holding pdns-recursors's configuration optons`
`default_release` | `{{ ansible_distribution_release\|lower }}` | `The default release to install packages from`
`package_list` | `['pdns_recursor']` | `The list of packages to be installed`
`pre_default_release` | `{{ pdns_recursor_default_release }}` | `The default release to install packages (pre_package_list) from`
`pre_package_list` | `[]` | `The list of prerequisite packages to be installed`
`repo_list` | `[]` | `Source string for the repositories`
`service_name` | `pdns-recursor` | `Name of the (pdns_recursor) service`
`supported_distro_list` | `['stretch']` | `A list of distribution releases this role supports`
`update_cache` | `yes` | `Run the equivalent of apt-get update before the operation`

## Dependencies

None

## License

MIT

## Author Information

* Patrick Ringl
