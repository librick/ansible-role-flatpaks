# Ansible Role: Flatpaks
[![pre-commit](https://img.shields.io/badge/pre--commit-enabled-brightgreen?logo=pre-commit)](https://github.com/pre-commit/pre-commit)

This role installs and customizes flatpaks on Debian-based Linux systems. It:
 - Ensures that flatpak is installed
 - Ensures that flatpak packages are installed system-wide
 - Ensures that flatpak packages are installed locally for a provided user
 - Ensures that flatpak packages are configured

## Role Variables
See [defaults/main.yml](./defaults/main.yml) for a comprehensive list of role variables.  
Some of the most pertinent variables are:
- `flatpaks_user`
- `flatpaks_xdg_config_home`  
- `flatpaks_xdg_data_home`  
- `flatpaks_system_flatpaks`  
- `flatpaks_user_flatpaks`

## Testing
Testing is performed using Molecule.  
See the [molecule](./molecule/) directory for more information.

## Linting
Linting is done automatically via [https://pre-commit.com/](https://pre-commit.com/).  
After setting up a virtual environment and installing `requirements.txt`, run  
`pre-commit run --all-files`  
See: https://github.com/ansible/ansible-lint  
See: https://github.com/pre-commit/pre-commit

## Example Playbook
    - hosts: servers
      vars_files:
        - vars/main.yml
      roles:
        - librick.flatpaks

*Inside `vars/main.yml`*:

    flatpaks_user: johndoe
    flatpaks_xdg_config_home: "/home/{{ flatpaks_user }}/.config"
    flatpaks_xdg_data_home: "/home/{{ flatpaks_user }}/.local/share"  
    flatpaks_system_flatpaks: []  
    flatpaks_user_flatpaks:
      - cc.arduino.IDE2


## License

MIT Licensed

## Author Information

This role was created in 2023 by [Eric McDonald](https://juniperspring.xyz/).
