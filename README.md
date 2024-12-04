# Mac Server Ansible Playbook

This playbook installs and configures most of software and configuration required to setup my Mac server. This playbook is designed to be run remotely from another system with Ansible installed. Somethings in MacOS are slightly difficult to automate, so I will document them here.

## Ansible control host setup

1. Clone or download this repository to your local drive.
2. Install Ansible using your [preferred method](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#)
3. Run `ansible-galaxy install -r requirements.yml` inside playbook directory to install required Ansible roles.

> [!TIP]
> If your preferred ansible install method is pip, I have a requirements.txt file that can be used that includes ansible-lint and some other nice adds. `pip3 install --user -r requirements.txt` can be used to install it.

> [!WARNING]
> If your ansible control host is MacOS as of Sequoia it ships with Python 3.9.6, Ansible 9.x and higher has a minimum requirement of Python 3.10 or higher. You can install python from homebrew or alternatively use python provided by python.org offical installers.

## Server Pre-setup

1. Complete MacOS initial guided setup
2. Ensure Apple's command line tools are installed `xcode-select -install`
3. Enable remote login via ssh `sudo systemsetup -setremotelogin on`
4. Run `ansible-playbook run.yml --ask-become-pass` to configure the system, entering you MacOS account password when prompted for the 'BECOME' password.

> [!NOTE]
> If some Homebrew commands fail, you might need to agree to Xcode's license or fix some other Brew issue. Run `brew doctor` to see if this is the case.

> [!TIP]
> If you need to supply an SSH password (if you don't use SSH keys), make sure to pass the `--ask-pass` parameter to the `ansible-playbook` command.

## Author 

This project was inspired by [Jeff Geerling's](https://github.com/geerlingguy/mac-dev-playbook) which was originally inspired by [MWGriffin/ansible-playbooks](https://github.com/MWGriffin/ansible-playbooks)).