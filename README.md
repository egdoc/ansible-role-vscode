Ansible role: vscode
=========

Ansible role to install Visual Studio Code on Linux.

Requirements
------------

The role doesn't have any requirements, however the gpg binary must be
installed on Debian-based systems for the installation to succeed, since
it is used in the package post-install script.

In order to avoid using the command or shell modules and break
idempotence, this role downloads the gpg key in `/etc/apt/keyrings/` without
de-armoring it on Debian-based systems. The key in this format can only be used
by SecureApt in version 1.4 or later (which appeared in stretch), as
stated [here](https://wiki.debian.org/DebianRepository/UseThirdParty#OpenPGP_certificate_distribution).

Role Variables
--------------

    vscode_gpg_key_url: https://packages.microsoft.com/keys/microsoft.asc
    vscode_gpg_key_fingerpint: BC528686B50D79E339D3721CEB3E94ADBE1229CF

The Visual Studio Code gpg key URL and fingerprint.

    vscode_rpm_repository_url: https://packages.microsoft.com/yumrepos/vscode
    vscode_apt_repository_url: deb [arch=amd64,arm64,armhf signed-by=/etc/apt/keyrings/packages.microsoft.asc] https://packages.microsoft.com/repos/code stable main

The Visual Studio Code apt and rpm repositories URL.


Dependencies
------------

None

Example Playbook
----------------

    - hosts: all
      roles:
         - role: egdoc.vscode

License
-------

GPL-2.0

Author Information
------------------

Role created by Egidio Docile