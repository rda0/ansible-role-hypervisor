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
