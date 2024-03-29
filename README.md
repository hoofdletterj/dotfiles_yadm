# Scripts & dotfiles for clean install
- YADM managed dotfiles
- bootstrap installation scripts for clean installs

# Bootstrapping a Fresh MacOS Install
Yadm needs to be installed prior to using this repo, and the bootstrap scripts herein. Please follow the next steps to get up and running
- Open the App Store and Sign-in using your Apple credentials.
- Install Command Line Tools for Xcode.

```
xcode-select --install
```
- Update MacOS including Command Line Tools for Xcode:
```
softwareupdate --all --install --force
```
- Install yadm temporarily (the definitive version is installed with Homebrew) in the bootstrap scripts 
```
curl -fLo /tmp/yadm https://github.com/TheLocehiliosan/yadm/raw/master/yadm && chmod a+x /tmp/yadm 
/tmp/yadm clone --bootstrap https://github.com/hoofdletterj/dotfiles.git
```

# MacOS Desktop and Application Settings
yadm boostrap is used to configure all aspects of the environment except the MacOS desktop and applications settings. Starting from Mathias Bynens's dotfiles/.macos configuration, I created a macos-settings bootstrap script. This should only be run as needed to avoid unexpected behaviour during the normal bootstrap process.

## pre-installation setup
```
xcode-select --install
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

## install personal apps
```
curl https://raw.githubusercontent.com/hoofdletterj/dotfiles_yadm/main/.config/homebrew/.Brewfile_play -s -o Brewfile
brew bundle install
```

## install work apps
```
curl https://raw.githubusercontent.com/hoofdletterj/dotfiles_yadm/main/.config/homebrew/.Brewfile_work -s -o Brewfile
brew bundle install
```

## SSH keys
```
sudo mkdir ~/.ssh & sudo vi ~/.ssh/id_rsa
chmod 600 ~/.ssh/id_rsa
gpg —-import /path/to/public-key-backup(Dropbox most likely)
gpg —-import /path/to/secret-key-backup(Dropbox most likely)
```

## GIT configuration
I need to update/migrate this to GIT standards
```
git config --global user.name "Jarno Dijkstra"
git config --global user.email "connect@hoofdletterj.nl"
git config --global help.autocorrect 1
```

## Oh-my-zsh
```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
git clone https://github.com/TamCore/autoupdate-oh-my-zsh-plugins $ZSH_CUSTOM/plugins/autoupdate
git clone https://github.com/Aloxaf/fzf-tab ~ZSH_CUSTOM/plugins/fzf-tab
source ~/.zshrc
```

## System configuration

# Disable the sound effects on boot
```
sudo nvram SystemAudioVolume=" "
```

Run the configuration script
```
${HOME}/.config/macos/macos-settings
```

## What steps do I need to automate?
- turn on brew autoupdate 
`brew autoupdate start 86400`
- install 1password for CLI
- Selective sync Apps & App settings folders on Dropbox & make available offline
- add Karabiner settings to .config folder
- sync Alfred to settings in Apps folder on Dropbox
- sign in to Firefox and sync settings
