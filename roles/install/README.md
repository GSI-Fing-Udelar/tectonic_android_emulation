install
=========

Install and configure Android emulation


Role Variables
--------------

- android_user: user for whom the Android emulation is installed
- cli_tools_url: Android Command Line Tools download URL
- api_level: Android API level
- avd_device: AVD device name
- vnc_port: VNC port
- vnc_pass: VNC password

Requirements
------------

Operating System: Ubuntu-like 
Architecture: x86_64


Example Playbook
----------------

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


License
-------

GPL-3.0-only