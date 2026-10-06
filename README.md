# :bookmark_tabs:  .dotfiles 

... for Bash / ZSH / Git Bash (Windows) / Cygwin (Windows) / Bash on Ubuntu on Windows

--> [Screenshots & Screencasts](https://github.com/voku/dotfiles/wiki/Images)

## Installation

### Using Git and the bootstrap script

You can clone the repository wherever you want. (I like to keep it in `~/Projects/dotfiles`, with `~/dotfiles` as a symlink.) The bootstrapper script will pull in the latest version and copy the files to your home folder.

```bash
# get the code
cd ~ ; git clone https://github.com/voku/dotfiles.git; cd dotfiles

# only for Debian based e.g. Ubuntu, Lubuntu, Kubuntu etc.
./firstInstallDebianBased.sh

# only for Cygwin (Windows)
./firstInstallCygwin.sh

# copy the dotfiles into your home directory
./bootstrap.sh
```

To update, `cd` into your local `dotfiles` repository and then:

```bash
./bootstrap.sh
```

### Add custom commands without creating a new fork

If `~/.config_dotfiles` does not exists, the "bootstrap.sh"-script will create a default config for you.

My `~/.config_dotfiles` looks something like this:

```bash
#!/bin/sh

CONFIG_DEFAULT_USER="lars"
CONFIG_ZSH_PLUGINS="(git zsh-completions zsh-syntax-highlighting)"
CONFIG_BASH_PLUGINS="(git)"
CONFIG_ZSH_THEME="voku"
CONFIG_BASH_THEME="voku"
CONFIG_CHARSET_UTF8=true
CONFIG_LANG="en_US"
CONFIG_TERM_LOCAL="" # terms: screen byobu tmux
CONFIG_TERM_SSH=""
```

If `~/.extra` exists, it will be sourced along with the other files. You can use this to add a few custom commands without the need to fork this entire repository, or to add commands you don’t want to commit to a public repository.

My `~/.extra` looks something like this:

```bash
#!/bin/sh

export DOTFILESSRCDIR="/home/lmoelleken/dotfiles/"

GIT_AUTHOR_NAME="Lars Moelleken"
GIT_COMMITTER_NAME="$GIT_AUTHOR_NAME"
git config --file=$HOME/.gitconfig.extra user.name "$GIT_AUTHOR_NAME"

GIT_AUTHOR_EMAIL="lars@moelleken.org"
GIT_COMMITTER_EMAIL="$GIT_AUTHOR_EMAIL"
git config --file=$HOME/.gitconfig.extra user.email "$GIT_AUTHOR_EMAIL"

git config --file=$HOME/.gitconfig.extra push.default simple
```

You could also use `~/.extra` to override settings, functions and aliases from my dotfiles repository. It’s probably better to [fork this repository](https://github.com/voku/dotfiles/fork) instead, though. And you can use `~/.vimrc.extra` to edit the vim settings without touching the main configuration.

## Run the tests

e.g.:
```bash
bash .redpill/tests/functions-tests.sh
zsh .redpill/tests/functions-tests.sh
```

## Feedback

Suggestions/improvements
[welcome](https://github.com/voku/dotfiles/issues)!


#
fsdf
*