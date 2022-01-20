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

Than `echo $0` will tell you `/usr/bin/zsh` :-)

Set in the LXterminal the color scheme to Solarized or any other prefered one:

    [Edit] > [Settings] > [Colors] > [Presets > Solarized(dark)]

**Heads-up** - If you run into trouble concerning **terminal colors**, check this
excellent [post](http://push.cx/2008/256-color-xterms-in-ubuntu) from Peter
Harkins for a general overview and "how things supposed to work" or a more
specific approach concerning
[256 colors in vim](http://vim.wikia.com/wiki/256_colors_in_vim)!

Get [rcm](https://github.com/mike-burns/rcm):

    sudo add-apt-repository ppa:martin-frost/thoughtbot-rcm
    sudo apt-get update && apt-get install rcm

Or on iOS run `brew install rcm`!

Install
-------

Clone onto your laptop:

    cd ~/Development
    git clone git@github.com:netzfisch/dotfiles.git
    git clone git@github.com:thoughtbot/dotfiles.git dotfiles/thoughtbot

Generate the "glue":

    env RCRC=$HOME/Development/dotfiles/rcrc rcup

This will create symlinks for config files in your home directory. To list all
created ones use `lsrc` or delete all with `rcdn`! See `man rcup` for the
full feature set.

Update
------

Do once:

    cd ~/Development/dotfiles/thoughtbot
    git remote add upstream git@github.com:thoughtbot/dotfiles.git

Each time you want to update from upstream/master:

    git fetch upstream
    git rebase upstream/master

To install more or update VIM plugins do

    rcup
    vim$ :PlugInstall

You can safely run `$ rcup` multiple times to update.

What's in it?
-------------

[zsh](http://zsh.sourceforge.net/FAQ/zshfaq01.html) configuration:

* `b` for `bundle`.
* `g` with no arguments is `git status` and with arguments acts like `git`.
* `migrate` for `bin/rails db:migrate db:rollback && bin/rails db:migrate db:test:prepare`.
* `mcd` to make a directory and change into it.
* `replace foo bar **/*.rb` to find and replace within a given list of files.
* `tat` to attach to tmux session named the same as the current directory.
* `v` for `$VISUAL`.
* local additions
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

[tmux](http://robots.thoughtbot.com/a-tmux-crash-course)
configuration:

* Improve color resolution.
* Remove administrative debris (session name, hostname, time) in status bar.
* Set prefix to `Ctrl+s`
* Soften status bar color from harsh green to light gray.

[git](http://git-scm.com/) configuration:

* Adds a `create-branch` alias to create feature branches.
* Adds a `delete-branch` alias to delete feature branches.
* Adds a `merge-branch` alias to merge feature branches into master.
* Adds an `up` alias to fetch and rebase `origin/master` into the feature
  branch. Use `git up -i` for interactive rebases.
* Adds `post-{checkout,commit,merge}` hooks to re-index your ctags.
* Adds `pre-commit` and `prepare-commit-msg` stubs that delegate to your local
  config.
* Adds `trust-bin` alias to append a project's `bin/` directory to `$PATH`.
* local additions:
  * Adds a `l` alias for tight, colored, log output
  * configures 'name and email'

[Ruby](https://www.ruby-lang.org/en/) configuration:

* Add trusted binstubs to the `PATH`.
* Load the ASDF version manager.

[vim](http://www.vim.org/) configuration:

* [fzf](https://github.com/junegunn/fzf.vim) for fuzzy file/buffer/tag finding.
* [Rails.vim](https://github.com/tpope/vim-rails) for enhanced navigation of
  Rails file structure via `gf` and `:A` (alternate), `:Rextract` partials,
  `:Rinvert` migrations, etc.
* Run many kinds of tests [from vim]([https://github.com/janko-m/vim-test)
* Set `<leader>` to a single space.
* Switch between the last two files with space-space.
* Syntax highlighting for Markdown, HTML, JavaScript, Ruby, Go, Elixir, more.
* Use [Ag](https://github.com/ggreer/the_silver_searcher) instead of Grep when
  available.
* Map `<leader>ct` to re-index ctags.
* Use [vim-mkdir](https://github.com/pbrisbin/vim-mkdir) for automatically
  creating non-existing directories before writing the buffer.
* Use [vim-plug](https://github.com/junegunn/vim-plug) to manage plugins.
* local added plugins:
  * [lean & mean status/tabline](https://github.com/bling/vim-airline)
  * [github color scheme](https://github.com/croaky/vim-colors-github)
  * [typescript syntax highlighting](https://github.com/leafgarland/typescript-vim)
  * [NERDTree](https://github.com/preservim/nerdtree)
  * find further plugins at [VimAwesome](https://vimawesome.com/)

Credits
-------

Thanks to [ThoughtBot](http://thoughtbot.com/) and all contributors!

These dotfiles are free software and may be redistributed under the terms
specified in the [LICENSE](LICENSE).
