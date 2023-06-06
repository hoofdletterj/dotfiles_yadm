# Scripts & dotfiles for clean install
- YADM managed dotfiles
- installation scripts

## pre-installation setup
```
xcode-select --install
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

## install personal apps
```
curl https://gist.githubusercontent.com/hoofdletterj/44cca73ea1aa88cfa903c1da0ec0d560/raw/2c3ab3c92a29d8fcc21fed240f16a24f27f24786/Brewfile_play -s -o Brewfile
sudo brew bundle install
```

## install work apps
```
curl https://gist.githubusercontent.com/hoofdletterj/44cca73ea1aa88cfa903c1da0ec0d560/raw/d0a5a12d13c5b4cf8ee9c37155f554391a8a1cdf/Brewfile_dev -s -o Brewfile
sudo brew bundle install
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

## Setup 
- turn on brew autoupdate 
`brew autoupdate start 86400`
- Selective sync Apps & App settings folders on Dropbox & make available offline
- connect 1password to Dropbox
