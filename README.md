# Ansible Role: Proxy

[![Build Status](https://travis-ci.org/tomereli/ansible-role-oh-my-zsh-p10k.svg?branch=master)](https://travis-ci.org/tomereli/ansible-role-oh-my-zsh-p10k)
[![Ansible Galaxy](http://img.shields.io/badge/galaxy-tomereli.oh_my_zsh_p10k-660198.svg)](https://galaxy.ansible.com/tomereli/oh_my_zsh_p10k)

An Ansible role that configures oh-my-zsh with powerlevel10k theme.

## Requirements

Internet access - if running behind proxy, consider using `tomereli.proxy` role before this one.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):
    
    # default theme
    oh_my_zsh_theme: powerlevel10k

    # default plugins
    oh_my_zsh_plugins:
        - git
        - zsh-autosuggestions
        - zsh-syntax-highlighting

## Dependencies

None.

## Example Playbook

The following playbook configures oh-my-zsh with powerlevel10k theme for `testuser1` and `testuser2`:

```yaml
- hosts: all
  roles:
    - role: tomereli.oh-my-zsh-p10k
      vars:
        users:
            - username: testuser1
            - username: testuser2
```

## License

MIT / BSD

## Author Information

This role was created in 2020 by [Tomer Arbel-Eliyahu](https://github.com/tomereli)
