# ansible-ubuntu-common
Ansible role to configure basic parameters on linux (Ubuntu) server

## Installation

Create requirements.yml file

```
# Include ubuntu-common role
- src: https://github.com/FastMT/ansible-ubuntu-common.git
  name: ubuntu-common
  version: "v1.0.4"
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
      sudo_nopasswd: yes

      # Optional parameter - password authentication (default: no)
      ssh_password_auth: no

      # Optional parameter - install Chrony time sync service (default: yes)
      linux_install_chrony: yes

      # Optional parameter - timezone (default: 'UTC')
      linux_timezone: 'UTC'

      # Optional parameter - disable IPv6 (default: yes)
      linux_disable_ipv6: true

      # Optional parameter - sysctl config
      linux_sysctl:
        - { name: "systctl.config.parameter",     value: 1 }      
```   
