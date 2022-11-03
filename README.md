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

    # default .zshrc template
    zshrc_src_template: .zshrc.j2 # Points to the default template delivered with this role

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

If you want to provide your own template for the `.zshrc` file, you can change the `zshrc_src_template` variable so it points to your custom template. For example, store your template under `templates/custom.zshrc.j2` in your repo directory and use this playbook:

```yaml
- hosts: all
  roles:
    - role: tomereli.oh-my-zsh-p10k
      vars:
        users:
            - username: testuser1
        zshrc_src_template: custom.zshrc.j2
```

> **Note**: Do not use `.zshrc.j2` as your custom template filename as it will just pick the default template instead.

## License

MIT / BSD

## Author Information

This role was created in 2020 by [Tomer Arbel-Eliyahu](https://github.com/tomereli)
