# ansible-ubuntu-common
Ansible role to configure basic parameters on linux (Ubuntu) server

## Installation

Create requirements.yml file

```
# Include ubuntu-common role
- src: https://github.com/FastMT/ansible-ubuntu-common.git
  name: ubuntu-common
  version: "v1.0.13"
```

Install external module into ~/.ansible/roles folder

```
ansible-galaxy install -r requirements.yml
```

## Usage

playbook.yml:

```
# Configure Ubuntu common parameters
- role: "ubuntu-common"
    vars:
      # Optional parameter - not ask password on sudo (default: yes)
      linux_sudo_nopasswd: true

      # Optional parameter - password authentication (default: no)
      linux_ssh_password_auth: false

      # Optional parameter - custom ssh port (default: 22)
      linux_ssh_port: 122

      # Optional parameter - install Chrony time sync service (default: yes)
      linux_install_chrony: true

      # Optional parameter - install QEMU / KVM guest agent (default: yes)
      linux_qemu_guest: true

      # Optional parameter - timezone (default: 'UTC')
      linux_timezone: 'UTC'

      # Optional parameter - disable IPv6 (default: yes)
      linux_disable_ipv6: true

      # Optional parameter - sysctl config
      linux_sysctl:
        - { name: "systctl.config.parameter",     value: 1 }      

      # Optional parameter - PAM limits
      linux_pam_limits:
        - { pam_item: "nofile", domain: "*", type: "soft", limit: 1048576 }
        - { pam_item: "nofile", domain: "*", type: "hard", limit: 1048576 }

```   
