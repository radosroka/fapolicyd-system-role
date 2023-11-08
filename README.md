# Fapolicyd

Fapolicyd System Role 

## Requirements

This role is only supported on RHEL8.1+/CentOS8.1+ and Fedora distributions. Consider reading fapolicyd documentation before setting it up.

### Collection requirements

None.

## Role Variables

### fapolicyd_setup_enable_service

Default `false` - if set to `true` the variable makes the service started 
and enabled fapolicyd service after successful deployment.

### fapolicyd_setup_trust

Default `rpmdb,file` - there can be list of sources for trust option `file`, `rpmdb` or `deb`(if compiled with debian support).
The option specifies which sources of trust a loaded and in which order.

### fapolicyd_setup_integrity

Default `none` - there are four supported types of integrity. No integrity `none`, defined by `size` of the file, defined by hash of the file `sha256` and defined by hashes of files but generated from `ima` kernel subsystem. Note that IMA needs to be set up separately and this system role does not cover it.

### fapolicyd_setup_permissive

Default `false` - if set to `true` deploys the daemon in permissive mode. 

### fapolicyd_add_trusted_file

Default `[]` - it can take list of files that will be marked as trusted.

## Example Playbook


```
---
- name: Example fapolicyd role invocation
  hosts: all
  vars:
    fapolicyd_setup_enable_service: true
    fapolicyd_setup_integrity: sha256
    fapolicyd_setup_trust: rpmdb,file
    fapolicyd_add_trusted_file:
      - /etc/passwd
      - /etc/fapolicyd/fapolicyd.conf
      - /etc/krb5.conf
  roles:
    - fapolicyd
```



## License

MIT

## Author Information

Radovan Sroka @rsroka

Marko Myllynen @myllynen

