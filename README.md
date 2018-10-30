# Mac Development Ansible Playbook

Ansible based solution to simplify the setup of a mbp. The roles were written in such a way to make the playbook idempotent. This playbook is composed of the following roles:

  1. `mac-osx-settings`: fine tuning detailed aspects of OSX (example: dock auto hide, finder appearance, etc)
  2. `homebrew-setup`: installs homebrew + required taps + casks
  3. `global-packages`: installs global npm and pip packages
  4. `miscellaneous`: installs and conigures oh-my-zsh + SpaceVim

## Usage

  1. Ensure Apple's command line tools are installed (`xcode-select --install` to launch the installer)
  2. [Install Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#latest-releases-via-pip).
  3. Clone this repository to your local drive.
  4. Run `ansible-playbook bootstrap.yml` inside this directory. Enter your account password when prompted (sudo might be required for setting up some specific tasks)

### Running a specific set of tagged tasks

You can filter which part of the provisioning process to run by specifying a set of tags. For example: `ansible-playbook bootstrap.yml --tags miscellaneous` flag. Available tags are: `mac-osx-settings`, `homebrew-setup`, `global-packages` and `miscellaneous`.

## Overriding Defaults

Not everyone's development environment and preferred software configuration is the same.

You can customize which packages need to be installed or settings should be configured by modifying the following files:
  1. `mac-osx-settings`: https://github.com/ranimufid/mbp-setup-ansible/blob/master/vars/mac_osx_settings.yml
  2. `homebrew-setup`: https://github.com/ranimufid/mbp-setup-ansible/blob/master/vars/homebrew_packages.yml
  3. `global-packages`: https://github.com/ranimufid/mbp-setup-ansible/blob/master/vars/global_packages.yml

## Dotfile management

I currently use [mackup](https://github.com/lra/mackup) for managing my dotfiles, and other specific app-relate config. The full list of supported apps can be found [here](https://github.com/lra/mackup#supported-applications). I currently run mackup manually to control to which config/dot files are restored from the cloud!

