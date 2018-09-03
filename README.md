# set-my-env

### PIP
```
curl https://bootstrap.pypa.io/get-pip.py | sudo -H python
pip completion --bash >> ~/.bashrc
```

### PYPI CACHE
```
pip install --user --upgrade devpi-server
```

```
devpi-server --init
devpi-server --start --threads `nproc`
(crontab -l 2>/dev/null; echo "@reboot $HOME/.local/bin/devpi-server --start --threads `nproc`") | crontab -
```

### PIPENV

```
curl https://raw.githubusercontent.com/kennethreitz/pipenv/master/get-pipenv.py | sudo -H python
echo 'eval "$(pipenv --completion)"' >> ~/.bashrc
```

### VIRTUALENWRAPPER (deprecated, prefer pipenv)
```
pip install --user --upgrade virtualenvwrapper
```

```
cat >> .bashrc << 'EOF'

export WORKON_HOME=$HOME/.virtualenvs
export PROJECT_HOME=$HOME/Projets
source ~/.local/bin/virtualenvwrapper.sh

EOF
```

### GIT-LEGIT
```
pip install --user --upgrade legit
legit --install
```

### GIT-LINT
```
pip install --user --upgrade git-lint
```

```
git config --global init.templatedir '~/.git-templates'
mkdir -p ~/.git-templates/hooks
ln -s `which pre-commit.git-lint.sh` ~/.git-templates/hooks/pre-commit
chmod a+x ~/.git-templates/hooks/pre-commit
sudo ln -s `which pre-commit.git-lint.sh` /usr/share/git-core/templates/hooks/pre-commit
```

### GIT WEBUI
```
curl https://raw.githubusercontent.com/alberthier/git-webui/master/install/installer.sh | bash
```

### POWERLINE-SHELL
[powerline-shell](https://github.com/banga/powerline-shell)

```
wget https://github.com/Lokaltog/powerline/raw/develop/font/PowerlineSymbols.otf
sudo mv PowerlineSymbols.otf /usr/share/fonts/

wget https://github.com/Lokaltog/powerline/raw/develop/font/10-powerline-symbols.conf
sudo mv 10-powerline-symbols.conf /etc/fonts/conf.d/

sudo fc-cache -vf
```

```
git clone https://github.com/Lokaltog/powerline-fonts.git
sudo mv powerline-fonts/ /usr/share/fonts/

sudo fc-cache -vf
```

```
pip install --user powerline-shell
```

```
cat >> .bashrc << 'EOF'

function _update_ps1() {
    PS1="$(powerline-shell $?)"
}

if [ "$TERM" != "linux" ]; then
    PROMPT_COMMAND="_update_ps1; $PROMPT_COMMAND"
fi

EOF
```

### NODE & NPM
```
curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
sudo apt-get install -y nodejs
```

### HEROKU CLI
```
curl https://cli-assets.heroku.com/install-standalone.sh | sh
```
```
heroku update && heroku plugins:install autocomplete && heroku autocomplete
```
```
printf "$(heroku autocomplete:script bash)" >> ~/.bashrc; source ~/.bashrc
```
