# pdns-recursor

[![Build Status](https://travis-ci.org/pari-/ansible-pdns-recursor.svg?branch=master)](https://travis-ci.org/pari-/ansible-pdns-recursor)

An Ansible role which installs and configures PowerDNS recursor

<!-- toc -->

## Requirements

Currently this role is developed for and tested on Debian GNU/Linux (release: jessie). It is assumed to work on other Debian distributions as well.

Ansible version compatibility:

- __2.3.1.0__ (current version in use for development of this role) 
- 2.2.3.0
- 2.1.6.0
- 2.0.2.0

## Example

```yaml
---

- hosts: "{{ hosts_group | default('all') }}"

  vars:

  roles:
    - { role: "{{ role_name | default('ansible-pdns_recursor') }}", tags: ['pdns_recursor'] }

```

The following shows an example regarding the usage of `pdns_server_config_opts`:

```yaml
---

- hosts: "{{ hosts_group | default('all') }}"

  vars:
    pdns_recursor_config_opts:
      allow-from:
        - "127.0.0.0/8"
        - "10.0.0.0/8"
        - "168.63.129.16"
      client-tcp-timeout: 2
      config-dir: "/etc/powerdns/"
      daemon: "yes"
      forward-zones-recurse: ".=8.8.4.4;8.8.8.8"
      local-address: "127.0.0.1,{{ ansible_default_ipv4.address }}"
      local-port: 53
      log-common-errors: "yes"
      logging-facility: 0
      loglevel: 3
      max-cache-entries: 1000000
      max-cache-ttl: 86400
      max-mthreads: 2048
      max-negative-ttl: 0
      max-packetcache-entries: 500000
      max-tcp-clients: 128
      max-tcp-per-client: 0
      network-timeout: 1500
      packetcache-servfail-ttl: 60
      packetcache-ttl: 3600
      pdns-distributes-queries: "no"
      query-local-address: "{{ ansible_default_ipv4.address }}"
      quiet: "yes"
      security-poll-suffix: ""
      serve-rfc1918: "yes"
      setgid: "pdns"
      setuid: "pdns"
      single-socket: "no"
      socket-dir: "/var/run/"
      threads: 2
      trace: "no"

  roles:
    - { role: "{{ role_name | default('ansible-pdns_recursor') }}", tags: ['pdns_recursor'] }
```

## Role Variables

Available variables are listed below, along with default values (see defaults/main.yml). They're generally prefixed with `pdns_recursor_` (which I deliberately leave out here for better formatting).

variable | default | notes
-------- | ------- | -----
`cache_valid_time` | `3600` | `Update the apt cache if its older than the set value (in seconds)`
`config_file` | `/etc/powerdns/recursor.conf` | `Absolute path to pdns_recursor's configuration file`
`config_opts` | `` | `Configuration hash holding pdns-recursors's configuration optons`
`default_release` | `jessie` | `The default release to install packages from`
`host_bin` | `/usr/bin/host` | `Absolute path to the the 'host'-binary`
`host_timeout` | `5` | `A resolving timeout (in seconds)`
`host_target` | `galaxy.ansible.com` | `The target which is tried to become resolved in the test run`
`package_list` | `['pdns_recursor']` | `The list of packages to be installed`
`pre_default_release` | `{{ pdns_recursor_default_release }}` | `The default release to install packages (pre_package_list) from`
`pre_package_list` | `[]` | `The list of prerequisite packages to be installed`
`repo_list` | `[]` | `Source string for the repositories`
`run_tests` | `True` | `If true, try to determine the installed application's functionality`
`service_name` | `pdns-recursor` | `Name of the (pdns_recursor) service`
`supported_distro_list` | `['jessie']` | `A list of distribution releases this role supports`
`update_cache` | `yes` | `Run the equivalent of apt-get update before the operation`

## Dependencies

None

## License

MIT

## Author Information

* Patrick Ringl
