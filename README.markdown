ansible-role-hypervisor
=======================

Deploy hypervisor hosts.

Supported hypervisors
---------------------

- kvm

Configuration
-------------

The hypervisor type and whether it should allocate hugepages must be explicitely enabled:

```yaml
hypervisor_hugepages_enabled: True
hypervisor_hugepages_at_boot: True
hypervisor_types:
  - kvm
```

The amount of hugepages must be manually specified on a per host basis:

```yaml
hypervisor_hugepages_gb: 32
```

This role depends on `bootloader` to correctly set the appropriate kernel boot parameters (hugepages) applied vie role vars.

Local updates
-------------

Usually on new debian releases some debian packages are missing required info for installing the release itself.

### Debootstrap

Update `hypervisor_debootstrap_distributions` to override required symlinks for debootstrapping a release.

### OsInfo Database

Use `hypervisor_osinfo_database_url` and `-e '{"hypervisor_osinfo_update":True}'` to update the local osinfo db.

This is needed if a release is missing in:

```bash
virt-install --osinfo list
osinfo-query os
```
