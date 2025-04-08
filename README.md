## Local Setup

#### Homebrew - brew.sh
```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
mkdir $HOME/workspace
ZSH_PROFILE="$HOME/workspace/zprofile"
echo "# Homebrew" >> $ZSH_PROFILE
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> $ZSH_PROFILE
echo -n '\nsource $HOME/workspace/zprofile\n' >> $HOME/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```
##### Brew debug
```sh
brew config
brew doctor
brew install --debug ets
```
##### Brew issue fix - fatal: not in a git directory
```sh
cd /opt/homebrew
git config --global --add safe.directory /opt/homebrew
git remote add origin https://github.com/Homebrew/brew
```

#### JDKs
```sh
brew install openjdk
sudo ln -sfn /opt/homebrew/opt/openjdk/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk.jdk
```

#### jenv
```sh
brew install jenv
export PATH="$HOME/.jenv/bin:$PATH"
eval "$(jenv init -)"
jenv add /Library/Java/JavaVirtualMachines/openjdk.jdk/Contents/Home
jenv global 23

echo -n "\n# jenv\n" >> $ZSH_PROFILE
echo 'export PATH="$HOME/.jenv/bin:$PATH"' >> $ZSH_PROFILE
echo 'eval "$(jenv init -)"' >> $ZSH_PROFILE
```

#### gnu sed
```sh
brew install gnu-sed
export PATH="/opt/homebrew/opt/gnu-sed/libexec/gnubin:$PATH"

echo -n "\n# gnu sed\n" >> $ZSH_PROFILE
echo 'export PATH="/opt/homebrew/opt/gnu-sed/libexec/gnubin:$PATH"' >> $ZSH_PROFILE
```

#### gnu curl
```sh
brew install curl
export PATH="/opt/homebrew/opt/curl/bin:$PATH"

echo -n "\n# curl\n" >> $ZSH_PROFILE
echo 'export PATH="/opt/homebrew/opt/curl/bin:$PATH"' >> $ZSH_PROFILE
```

#### Iterm2
```sh
brew install --cask iterm2
```

- Oh-my-zsh
```sh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

- omz theme powerlevel10k
```sh
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git "${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k"
```

#### omz settings in .zshrc
```sh
sed -i -e 's|^ZSH_THEME="robbyrussell"$|ZSH_THEME=powerlevel10k/powerlevel10k|' $HOME/.zshrc
grep 'powerlevel10k' $HOME/.zshrc
sed -i -e 's|^plugins=(git)$|plugins=(\
  git\
  colored-man-pages\
  colorize\
  docker\
  gradle\
  jenv\
  pip\
)|' $HOME/.zshrc
grep -A 8 '^plugins=' $HOME/.zshrc
```

#### vi syntax highlighting
```sh
echo -n '\nsyntax on\n' >> .vimrc
```

#### iTerm cursor behavior
1. Open “Preferences”
2. Click on “Profiles” and select “Default”
3. Navigate to “Keys” tab > “Key Bindings” tab
4. Click the “Presets” dropdown and select “Natural Text Editing”


#### Additional Apps ###
```sh
brew install jq
brew install git
brew install --cask git-credential-manager
brew install --cask rectangle
brew install --cask google-chrome
brew install --cask visual-studio-code
brew install --cask intellij-idea-ce
brew install --cask slack
brew install --cask chatgpt
brew install --cask zoom
```

#### Python
```sh
brew install python
brew install poetry
mkdir $ZSH_CUSTOM/plugins/poetry
poetry completions zsh > $ZSH_CUSTOM/plugins/poetry/_poetry
sed -i -e 's|^plugins=($|plugins=(\
  poetry|' $HOME/.zshrc
grep -A 10 '^plugins=' $HOME/.zshrc
```

### VS Code plugins
- GitHub CoPilot
- GitHub CoPilot Chat
- Even Better TOML
- Markdown All In One
