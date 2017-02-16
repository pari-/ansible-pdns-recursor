# pdns-recursor

An Ansible role which installs and configures PowerDNS recursor

<!-- toc -->

- [Requirements](#requirements)
- [Example](#example)
- [Role Variables](#role-variables)
  * [Role Internals](#role-internals)
- [Dependencies](#dependencies)
- [License](#license)
- [Author Information](#author-information)

<!-- tocstop -->

## Requirements

Currently this role is developed for and tested on Debian GNU/Linux (release: jessie). It is assumed to work on other Debian distributions as well.

Ansible version in use for development: 2.2.1

## Example

```yaml
- hosts: pdns-recursors

  roles: 
    - { role: ansible-pdns-recursor }
```

The following is a complete example of the overall configuration dict:

```yaml
pdns_recursor_config:
  allow-from:
    - "10.0.0.0/8"
    - "172.16.0.0/12"
    - "192.168.0.0/16"
  allow-from-file:
  any-to-tcp: "no"
  auth-zones:
  carbon-interval: 30
  carbon-ourname:
  carbon-server:
  chroot:
  client-tcp-timeout: 2
  config-dir:
  config-name:
  daemon: "yes"
  delegation-only:
  disable-edns: "yes"
  disable-packetcache: "no"
  dont-query:
    - "127.0.0.0/8"
    - "10.0.0.0/8"
    - "100.64.0.0/10"
    - "169.254.0.0/16"
    - "192.168.0.0/16"
    - "192.0.0.0/24"
    - "192.0.2.0/24"
    - "198.51.100.0/24"
    - "203.0.113.0/24"
    - "240.0.0.0/4"
    - "172.16.0.0/12"
    - "0.0.0.0/8"
    - "::1/128"
    - "fc00::/7"
    - "fe80::/10"
    - "::/96,"
    - "::ffff:0:0/96"
    - "100::/64"
    - "2001:db8::/32"
  entropy-source: "/dev/urandom"
  etc-hosts-file: "/etc/hosts"
  export-etc-hosts: "no"
  export-etc-hosts-search-suffix:
  forward-zones:
  forward-zones-file:
  forward-zones-recurse:
  hint-file:
  include-dir:
  latency-statistic-size: 10000
  local-address: "127.0.0.1"
  local-port: 53
  log-common-errors: "no"
  logging-facility:
  loglevel: 4
  lua-dns-script:
  max-cache-entries: 1000000
  max-cache-ttl: 86400
  max-mthreads: 2048
  max-negative-ttl: 3600
  max-packetcache-entries: 500000
  max-tcp-clients: 128
  max-tcp-per-client: 0
  minimum-ttl-override: 0
  network-timeout: 1500
  packetcache-servfail-ttl: 60
  packetcache-ttl: 3600
  pdns-distributes-queries: "no"
  query-local-address: "0.0.0.0"
  query-local-address6:
  quiet: "yes"
  serve-rfc1918: "yes"
  server-down-max-fails: 64
  server-down-throttle-time: 60
  server-id: "{{ ansible_fqdn }}"
  setgid:
  setuid:
  single-socket: "no"
  socket-dir:
  socket-owner:
  socket-group:
  socket-mode:
  spoof-nearmiss-max: 20
  stack-size: 200000
  threads: 2
  trace: "no"
  udp-truncation-threshold: 1680
  version:
  version-string: "powerdns recursor version number"
```

__blank keys will be converted to comments i.e.__

```yaml
...
chroot:
...
```

becomes:

```yaml
#chroot
```
in `pdns_recursor_config_file`` 

For more information about each option, please see [Upstream Recursor Settings](https://github.com/PowerDNS/pdns/blob/master/docs/markdown/recursor/settings.md)

## Role Variables

Available variables are listed below, along with default values (see defaults/main.yml) - all variables are prefixed with `pdns_recursor_` (which I deloberately leave out here for formatting reasons).

variable | default | notes
-------- | ------- | -----
`config` | `{}` | `tbd`

### Role Internals

variable | default | notes
-------- | ------- | -----
`cache_valid_time` | `'3600'` | `tbd`
`config_file` | `'/etc/powerdns/recursor.conf'` | `tbd`
`default_release` | `'jessie-backports'` | `tbd`
`package_list` | `['pdns-recursor']` | `tbd`
`packages_state` | `'present'` | `tbd`
`repo_list` | `['deb http://ftp.debian.org/debian jessie-backports main']` | `tbd`
`repo_state` | `'present'` | `tbd`
`service_name` | `'pdns-recursor'` | `tbd`
`supported_distro_list` | `['jessie']` | `tbd`
`update_cache` | `'yes'` | `tbd`

## Dependencies

None

## License

MIT

## Author Information

* Patrick Ringl
