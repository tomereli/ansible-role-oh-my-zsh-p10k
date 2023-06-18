# Ansible Role: oh_my_zsh_p10k

[![Build Status](https://travis-ci.org/tomereli/ansible-role-oh-my-zsh-p10k.svg?branch=master)](https://travis-ci.org/tomereli/ansible-role-oh-my-zsh-p10k)
[![Ansible Galaxy](http://img.shields.io/badge/galaxy-tomereli.oh_my_zsh_p10k-660198.svg)](https://galaxy.ansible.com/tomereli/oh_my_zsh_p10k)

An Ansible role that installs and configures [oh-my-zsh](https://github.com/ohmyzsh/ohmyzsh) with [powerlevel10k](https://github.com/romkatv/powerlevel10k) theme for specified users. You can provide your own `.zshrc` and `.p10k.zsh` files or use the provided ones.

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

    # default .p10k.zsh file
    p10k_src_file: .p10k.zsh # Points to the default file delivered with this role

## Dependencies

None, only builtin modules are being used.

## Example Playbook

The following playbook configures oh-my-zsh with powerlevel10k theme for `testuser1` and `testuser2`:

```yaml
- hosts: all
  roles:
    - role: tomereli.oh_my_zsh_p10k
      vars:
        users:
            - username: testuser1
            - username: testuser2
```

If you want to provide your own template for the `.zshrc` file, you can change the `zshrc_src_template` variable so it points to your custom template. For example, store your template under `templates/custom.zshrc.j2` in your repo directory and use this playbook:

```yaml
- hosts: all
  roles:
    - role: tomereli.oh_my_zsh_p10k
      vars:
        users:
            - username: testuser1
        zshrc_src_template: custom.zshrc.j2
```

> **Note**: Do not use `.zshrc.j2` as your custom template filename as it will just pick the default template instead.

Similarly, you can also provide your own version of the `.p10k.zsh` by setting the `p10k_src_file` variable. The recommended approach is to generate your own file by running `p10k configure` on a system which already has oh-my-zsh with powerlevel10k installed, then copy the generated file (found at `~/.p10k.zsh`) into your project directory, for example at `files/custom.p10k.zsh`.

> **Notes**:
>
> - Do not use `.p10k.zsh` as your custom filename as it will just pick the default template instead.
> - Contrarily to the `.zshrc.j2` template, the custom `.p10k.zsh` will be copied **without** further modification, i.e. Jinja2 syntax is **not** supported in this file.

## License

MIT / BSD

## Author Information

This role was created in 2020 by [Tomer Arbel-Eliyahu](https://github.com/tomereli)
