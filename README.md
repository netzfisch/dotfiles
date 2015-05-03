netzfisch does also dotfiles
============================

These dotfiles personalize my system, which are based + inspired by
[thoughtbot/dotfiles](https://github.com/thoughtbot/dotfiles) and work together
using the [`*.local`](http://robots.thoughtbot.com/manage-team-and-personal-dotfiles-together-with-rcm)
convention.

The dotfiles focus on ruby development with tools like git, tmux, vim and
Ethan Schoonover [solarized-theme](https://github.com/altercation/solarized) in
a [Lubuntu](http://lubuntu.net) Xfce4-terminal environment.

See also the unofficial guide to [dotfiles on GitHub](http://dotfiles.github.io/),
why you want to track down your dotfiles and how to get started with a bootstrap!

Requirements
------------

Set zsh as your login shell:

    chsh -s /bin/zsh

Set the color scheme to solarized in LXterminal:

    [Edit] > [Settings] > [Colors] > [Presets > Solarized(dark)]

Probably change single colors like light-green to #55FF55 and light-blue to #5555FF.

**Heads-up** - If you run into trouble concerning **terminal colors**, check this
excellent [post](http://push.cx/2008/256-color-xterms-in-ubuntu) for a general
overview - "how things supposed to work"!

Install [rcm](https://github.com/mike-burns/rcm):

    sudo add-apt-repository ppa:martin-frost/thoughtbot-rcm
    sudo apt-get update
    sudo apt-get install rcm

Install
-------

Clone onto your laptop:

    cd ~/Development
    git clone git://github.com/netzfisch/dotfiles.git
    git clone git://github.com/thoughtbot/dotfiles.git dotfiles/thoughtbot

Install:

    env RCRC=$HOME/Development/dotfiles/rcrc rcup

This will create symlinks for config files in your home directory.

Update
------

Do once:

    cd ~/Development/dotfiles/thoughtbot
    git remote add upstream git@github.com:thoughtbot/dotfiles.git

Each time you want to update from upstream/master:

    git fetch upstream
    git rebase upstream/master

You can safely run `rcup` multiple times to update.

What's in it?
-------------

**Everything** listed at ThoughtBot's [content](https://github.com/thoughtbot/dotfiles#whats-in-it)
section and ...

[git](http://git-scm.com/) configuration:

* aliases
  * `l` for tight, colored, log output
* name and email

[vim](http://www.vim.org/) configuration:

* [lean & mean status/tabline](https://github.com/bling/vim-airline)
* [solarized color scheme](https://github.com/croaky/vim-colors-github)

[zsh](http://zsh.sourceforge.net/FAQ/zshfaq01.html) configuration:

* aliases
  * `tde`, `ted`, `tds`, `tsd` to translate between englisch, german and
    spanisch with [termit][termit]
  * `todo` to edit a plain text todo-file, located in the Dropbox folder
* `PATH` additions for
  * [rbenv][rbenv]
  * [Heroku toolbelt][heroku]
  * [node modules][nvm]
  * [Android SDK][android]

[termit]: https://github.com/pawurb/termit
[rbenv]: https://github.com/sstephenson/rbenv
[heroku]: https://toolbelt.heroku.com
[nvm]: https://github.com/creationix/nvm#manual-install
[android]: https://developer.android.com/sdk/installing/index.html?pkg=tools

Credits
-------

Thanks to [thoughtbot](http://thoughtbot.com/) and all contributors!

These dotfiles are free software and may be redistributed under the terms
specified in the [LICENSE](LICENSE).
