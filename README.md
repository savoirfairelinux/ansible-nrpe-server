# ansible-nrpe-server

*Provisions a Nagios NRPE server, SFL style.*

## Requirements

* Ansible 2.0+
* Debian Jessie on the target system
* A provisioning that runs [ansible-common][ansible-common] before this.

## Usage

You call this role as with any other roles. See [vars file](defaults/main.yml) for customisation
options.

Here's an example usage for a local development environment:

```yaml
---
- name: Install a fully functional Nagios NRPE server
  hosts: nrpe-server-test

  roles:
    - role: nrpe-server
      nagios_nrpe_server_port: 5667
      nagios_nrpe_server_allowed_hosts:
        - 127.0.0.1
      nagios_nrpe_commands:
        - name: check_disk
          command: /usr/lib/nagios/plugins/check_disk -w 20% -c 10%
        - name: check_mem
          command: /usr/lib/nagios/plugins/check_mem -u -w 90 -c 95

```


[ansible-common]: https://gitlab.savoirfairelinux.com/devops/ansible-common
