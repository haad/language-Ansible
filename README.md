# Ansible Syntax Highlighting Package

This extension adds two grammars to enable syntax highlighting for Ansible in the Atom Editor:

- `Ansible`: It's based on the [original Ansible Sublime-text package](https://github.com/clifford-github/sublime-ansible) with my own fixes.
- `Ansible (advanced)`: It's based on YAML language of 2015 FichteFoll <fichtefoll2@googlemail.com> with modifications to support:
    - Jinja language
    - Jinja expressions for ansible conditions (`when`, `changed_when`, `failed_when`, `check_mode`)
    - Some YAML block scalar


## Adding ansible yaml file detection

By default the `Ansible` grammar matches any file with the `.yml` extension and `Ansible (advanced)`
must be explicitly configured to match anything (see below).

The `.yml` file extension will likely trigger the core `language-yaml` grammar to be used instead of
`language-ansible`. To force `language-ansible` to be used, define `customFileTypes` in
[config.cson](https://flight-manual.atom.io/using-atom/sections/basic-customization/#global-configuration-settings):

```json
"*":
  core:
    customFileTypes:
      "source.ansible": ["yml"] # replace `source-ansible` with `source.ansible-advanced` if you want the advanced grammar instead).
```

For now, neither grammar supports syntax highlighting based on file path (host_vars/group_vars) out
of the box. However, this can be achieved with the [file-types](https://atom.io/packages/file-types)
package.  After installing `file-types` define custom syntax associations for proper matching. Add
the following to your Atom `config.cson`:

```json
"*":
"file-types":
  "**/ansible/**/*.yml": "source.ansible"
  "**/group_vars/**.yml": "source.ansible"
  "**/host_vars/**.yml": "source.ansible"
```
