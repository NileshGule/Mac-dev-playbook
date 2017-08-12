# Mac Development Ansible Playbook

[![Build Status](https://travis-ci.org/NileshGule/Mac-dev-playbook.svg?branch=master)](https://travis-ci.org/NileshGule/Mac-dev-playbook)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/NileshGule/Mac-dev-playbook/master/LICENSE)


This work is inspired by [geerlingguy](https://github.com/geerlingguy/mac-dev-playbook) work on automating the setup for Mac Book. For installing the [oh my zsh](http://ohmyz.sh) package I took inspiration from [RaymiiOrg](https://github.com/RaymiiOrg/ansible/blob/master/oh-my-zsh/ohmyzsh.yml).

This playbook installs and configures most of the software I use on my Mac for software development. I combined the two ansible automated setups and added my own tools like Github Desktop & Tabset. The complete list of softwares are listed below.

I have also automated the installation of Atom packages. This is inspired from the playbook of [Fusion](https://gist.github.com/Fusion/c45fdd8857c84440d55f)
The details related to Atom packages can be found in atom-packages-setup.yml file.

This is a work in progress, and is mostly a means for me to document my current Mac's setup. I'll be evolving this set of playbooks over time.

## Installation

  1. Ensure Apple's command line tools are installed (`xcode-select --install` to launch the installer).
  2. [Install Ansible](http://docs.ansible.com/intro_installation.html).
  3. Clone this repository to your local drive.
  4. Run `$ ansible-galaxy install -r requirements.yml` inside this directory to install required Ansible roles.
  5. Run `ansible-playbook main.yml -i inventory -K` inside this directory. Enter your account password when prompted.

> Note: If some Homebrew commands fail, you might need to agree to Xcode's license or fix some other Brew issue. Run `brew doctor` to see if this is the case.

### Running a specific set of tagged tasks

You can filter which part of the provisioning process to run by specifying a set of tags using `ansible-playbook`'s `--tags` flag. The tags available are `dotfiles`, `homebrew`, `mas`, `extra-packages` and `osx`.

    ansible-playbook main.yml -i inventory -K --tags "dotfiles,homebrew"

## Overriding Defaults

Not everyone's development environment and preferred software configuration is the same.

You can override any of the defaults configured in `default.config.yml` by creating a `config.yml` file and setting the overrides in that file. For example, you can customize the installed packages and apps with something like:

    homebrew_installed_packages:
      - cowsay
      - git
      - go

    mas_installed_apps:
      - { id: 443987910, name: "1Password" }
      - { id: 498486288, name: "Quick Resizer" }
      - { id: 557168941, name: "Tweetbot" }
      - { id: 497799835, name: "Xcode" }

    composer_packages:
      - name: hirak/prestissimo
      - name: drush/drush
        version: '^8.1'

    gem_packages:
      - name: bundler
        state: latest

    npm_packages:
      - name: webpack

    pip_packages:
      - name: mkdocs

Any variable can be overridden in `config.yml`; see the supporting roles' documentation for a complete list of available variables.

## Included Applications / Configuration (Default)

Applications (installed with Homebrew Cask):
  - [Atom](https://atom.io)
  - [Adobe Acrobat Reader](https://acrobat.adobe.com/sea/en/acrobat/pdf-reader.html)
  - [CheetSheet](https://www.mediaatelier.com/CheatSheet/)
  - [Docker](https://www.docker.com/)
  - [Dropbox](https://www.dropbox.com/)
  - [Firefox](https://www.mozilla.org/en-US/firefox/new/)
  - [Github Desktop](https://desktop.github.com)
  - [Google Chrome](https://www.google.com/chrome/)
  - [iTerm2](https://www.iterm2.com)
  - [Java](https://www.java.com/en/)
  - [MacPass](http://mstarke.github.io/MacPass/)
  - [Spectacle](https://www.spectacleapp.com)
  - [Sublime Text](https://www.sublimetext.com/)
  - [Vagrant](https://www.vagrantup.com/)
  - [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
  - [Visual Studio Code](https://code.visualstudio.com)

Packages (installed with Homebrew):

  - [autoconf](http://brewformulas.org/Autoconf)
  - [bash-completion](http://brewformulas.org/BashCompletion)
  - [chromedriver](http://brewformulas.org/Chromedriver)
  - [git](https://git-scm.com)
  - gpg
  - [mas](https://libraries.io/homebrew/mas)
  - [maven](https://maven.apache.org)
  - [molecule](https://molecule.readthedocs.io/en/master/)
  - [node](http://brewformulas.org/Node)
  - [nvm](http://brewformulas.org/Nvm)
  - [tree](http://brewformulas.org/Tree)
  - [zsh](http://zsh.sourceforge.net)
  - [zsh-completions](https://github.com/zsh-users/zsh-completions)

Atom packages and Themes (installed with hnakamu role)

  - change-tabs
  - color-tabs
  - [file-icons](https://atom.io/packages/file-icons)
  - [atom-material-ui](https://github.com/atom-material/atom-material-ui)
  - [atom-material-syntax-dark](https://github.com/atom-material/atom-material-syntax-dark)
  - [wakatime](https://wakatime.com/atom)

Visual Studio Code extensions
  - [autoimport](https://marketplace.visualstudio.com/items?itemName=steoates.autoimport)
  - [vscode-docker](https://marketplace.visualstudio.com/items?itemName=PeterJausovec.vscode-docker)
  - [csharp](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp)
  - [vscode-icons](https://marketplace.visualstudio.com/items?itemName=robertohuertasm.vscode-icons)
  - [githistory](https://marketplace.visualstudio.com/items?itemName=donjayamanne.githistory)
  - [vscode-auto-open-markdown-preview](https://marketplace.visualstudio.com/items?itemName=hnw.vscode-auto-open-markdown-preview)
  - [docker-explorer](https://marketplace.visualstudio.com/items?itemName=formulahendry.docker-explorer)
  - [ansible-autocomplete](https://marketplace.visualstudio.com/items?itemName=timonwong.ansible-autocomplete)
  - [python](https://marketplace.visualstudio.com/items?itemName=donjayamanne.python)
  - [vscode-yaml-validation](https://marketplace.visualstudio.com/items?itemName=djabraham.vscode-yaml-validation)
  - [vscode-flake8](https://marketplace.visualstudio.com/items?itemName=jaysonsantos.vscode-flake8)
  - [one-monokai](https://marketplace.visualstudio.com/items?itemName=azemoh.one-monokai)
  - [wakatime](https://marketplace.visualstudio.com/items?itemName=WakaTime.WakaTime)
  - [MarkdownLint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint)
  - [EditorConfig](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig)
  - [gitignore](https://marketplace.visualstudio.com/items?itemName=codezombiech.gitignore)
  - [Language support for Java by Redhat](https://marketplace.visualstudio.com/items?itemName=redhat.java)
  - [code-spell-checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)
  - [Java Language support using Compiler API](https://marketplace.visualstudio.com/items?itemName=georgewfraser.vscode-javac)

As per the original playbook from geerlingguy, there is an option to configure the dotfiles. I have disabled this option by setting the configure_dotfiles: no flag.

Ansible role [hnakamu](https://github.com/hnakamur/ansible-role-atom-packages) is used for managing Atom packages.


I faced problems while setting zsh as the default shell. I have commented the lines in oh-my-zsh-setup.yml file which tries to set the default shell. The original oh-my-zsh setup file had user name passed as a variable. I changed this a bit to use the current user from environment variables.

Finally, there are a few other preferences and settings added on for various apps and services.

Note that the Spectacle application installs successfully but it requires access to Accessibility settings. Because of this it reports failure. I ran the playbook once to overcome this problem and then comment the line in the config which installs this app. Rerunning the playbook installs all the other packages and tools.

## Future additions
Next step is to automate the installation of plugins for Sublime.

### Things that still need to be done manually

It's my hope that I can get the rest of these things wrapped up into Ansible playbooks soon, but for now, these steps need to be completed manually (assuming you already have Xcode and Ansible installed, and have run this playbook).

  1. Set JJG-Term as the default Terminal theme (it's installed, but not set as default automatically).
  2. Install [Sublime Package Manager](http://sublime.wbond.net/installation).
  3. Install all the apps that aren't yet in this setup (see below).
  4. Remap Caps Lock to Escape (requires macOS Sierra 10.12.1+).
  5. Set trackpad tracking rate.
  6. Set mouse tracking rate.
  7. Configure extra Mail and/or Calendar accounts (e.g. Google, Exchange, etc.).

### Applications/packages to be added:

I was able to install IntelliJ Idea. There is a Ansible role by GantSign for installing plugins for IntelliJ. I am facing some problem getting the role to work properly. For time being I have installed the plugins using IDE. In future will work to fix the issue with role and automate the deployment of plugin as well.

### Configuration to be added:

  - In order for iTerm2 terminal to pick oh my zsh as the default shell the command needs to be customized:
    ```
    In the preferences for iTerm2 select the startup command as /bin/zsh --login
    ```

  - The CheetSheet & Specktacle applications require access to Accesibility settings. These need to be manually configured for time being.

## Testing
The project is [continuously tested using Travis CI's MacOS infrastructure](https://travis-ci.org/NileshGule/Mac-dev-playbook).

## Author

[Nilesh Gule](http://nileshgule.blogspot.com/), 2017 (originally inspired by following authors)
- [geerlingguy](https://github.com/geerlingguy/mac-dev-playbook) 
- [Raymiiorg](https://github.com/RaymiiOrg/ansible/blob/master/oh-my-zsh/ohmyzsh.yml)
- [Gantsign Ansible role for VS Code](https://github.com/gantsign/ansible-role-visual-studio-code)