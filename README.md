# Ansible Collection - tectonic.android

## Description
Collection for Android emulation in Tectonic cyber range.

## Roles

This collection includes the following roles:

- **install**: Install and configure Android emulation. Invoke in *base_config* phase.

Each role has its own README with detailed usage instructions and variables.

**Usage:**
```yaml
- hosts: all
  become: yes
  roles:
    - role: tectonic.android.install
      vars:
        android_user: "{{ ansible_user }}"
        cli_tools_url: "https://dl.google.com/android/repository/commandlinetools-linux-13114758_latest.zip"
        api_level: "24"
        avd_device: "pixel"
        vnc_port: 5902
        vnc_pass: "tectonic"

```

## Requirements

Android emulation is supported only on Ubuntu-like systems and x86_64 architecture. Additionally, for it to work with KVM, it is necessary to define an advanced XLS file at the scenario level, containing something similar to the following:

```
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
    <xsl:output method="xml" indent="yes"/>

    <xsl:template match="@*|node()">
        <xsl:copy>
            <xsl:apply-templates select="@*|node()"/>
        </xsl:copy>
    </xsl:template>

    <xsl:template match="/domain/cpu">
        <cpu mode="host-passthrough" check='none' migratable='on'/>
    </xsl:template>
</xsl:stylesheet>
```