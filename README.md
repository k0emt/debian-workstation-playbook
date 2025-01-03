# Debian Workstation Playbook

[![License: CC BY-NC 4.0](https://img.shields.io/badge/License-CC%20BY--NC%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc/4.0/)

This project contains ansible resources for setting up a new debian based workstation.

Roles that will be setup are:

- Git User: git, gitk, git-gui, user configuration, ssh keys
- Power User:
  - zsh, oh-my-zsh, extensions, powerlevel10k, plugins
  - numerous command line tools
    - btop, bat, eza, fzf, mc, fastfetch, tldr, tmux, tree, vim, wget...
  - .vimrc file
  - IOSevka fonts installed
- App User: audacity, OBS studio, gimp,inkscape, krita, hexchat, thunderbird
  - Wallpapers
- TODO Amateur Radio: QRQ, OpenSCAD, kiCAD
- WIP Developer: gcc, make, python3, go lang, elixir, rbenv, ruby, rails, podman, podman desktop, VS Code, gitnuro
- TODO AI researcher: gcc, git, python3, numpy, pandas, scikit-learn, keras, matplotlib, ggplot, bokeh
- TODO Database Engineer: pgcli, pgadmin4-desktop, valkey, valkey-doc
- TODO Communicator: Slack, Discord, Zoom, Edge

## Project Structure

```markdown
debian-workstation-playbook/
├── README.md
├── workstation.yml
└── roles/
    ├── role_name/
    │   ├── handlers/
    │   ├── tasks/
    │   │   └── main.yml
    ...
```

## Initial bootstrap

How to do the initial bootstrap of getting ansible on the system:

```shell
sudo apt update
sudo apt install software-properties-common
# sudo add-apt-repository --yes --update ppa:ansible/ansible # for Ubuntu 
sudo apt install ansible
```

## Running the playbook

- Clone the repo onto your computer.
- It is fine to use https at this point.
- Change into the cloned directory.
- To run the playbook on your local workstation, use the following command:

```shell
ansible-playbook -i localhost, -c local workstation.yml --ask-become-pass
```

### Gotchas

If you have already enrolled a fingerprint,
this is likely to block the playbook from properly running.
It can get stuck at gathering facts.
_Delete enrolled fingerprints and try to run again._

If there is a failure downloading during a task, simply run the playbook again.

### Install Custom roles

To run with selected roles, you can modify the `workstation.yml` file or duplicate it.
Alter the duplicated file to have only the roles you want to run.
You can do this by adding a \# before the role name.
On the command line specify the new file name instead of `workstation.yml`

## Post install

Run `p10k configure` in a new terminal if you aren't prompted to set up powerlevel 10K.

### Manual installs

[postgresql server](https://www.postgresql.org/download/linux/debian/) if you want a local server

[nvm](https://github.com/nvm-sh/nvm) node version manager

[SDKMAN!](sdkman.io/install) for JVM developers

[mongodb mongosh](https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-debian/)

[dBeaver]( https://dbeaver.io/download/) database client

[AWS CLI]( https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)

[Iosevka](https://github.com/be5invis/Iosevka) font

[Set up TensorFlow in virtual environment](https://www.tensorflow.org/install/pip)

## Developer Information

How to do a dry run of the playbook

```shell
ansible-playbook -i localhost, -c local workstation.yml --check --ask-become-pass
```

### Testing with WSL2

- [How to test in a WSL2 instance](wsl2-testing.md)

### Testing using Virtualization

You can use Boxes on a Debian Workstation.
NOTE: you would need to install boxes with `sudo apt install gnome-boxes`

Or if you have a Windows Pro OS you can use Hyper-V.
Create a VM with a clean instance of your Debian distribution.
To test your changes, clone down your forked repo.
Switch to the appropriate branch and test installing it.

