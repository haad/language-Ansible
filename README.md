# Ansible Syntax Highlighting Package

This extension add 2 grammars to enable syntax highlighting for Ansible in the Atom Editor.

- `Ansible`: It's based on the [original Ansible Sublime-text package](https://github.com/clifford-github/sublime-ansible) with my own fixes.
- `Ansible (advanced)` : It's based on YAML language of 2015 FichteFoll <fichtefoll2@googlemail.com> with modifications to support :
    - Jinja language
    - Jinja expressions for ansible conditions (`when`, `changed_when`, `failed_when`, `check_mode`)
    - Some YAML block scalar


## Adding ansible yaml file detection

For now both methods doesn't support syntax highlighting based on path see (host_vars/group_vars)
below.

### Using file-types package

After installing _file-types_ package user can define custom syntax associations for proper matching.

#### config.cson

```json
"*":
  "file-types":
    ".*.yml$": "source.ansible"
    ".*/group_vars/.*": "source.ansible"
    ".*/host_vars/.*": "source.ansible"
```

### Atom Custom File Types

Manually defining custom file types.

```json
"*":
  core:
    customFileTypes:
      "source.ansible": [
        "yml"
      ]
```