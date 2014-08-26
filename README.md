# vpm

This is a tiny script I use to manage vim plugins installed from GitHub to be
managed by [pathogen][].

You can use it like this:

* `vpm ls` prints a list of installed plugins.
* `vpm install url` installs one or more plugins from the given urls. You can
  also a pass GitHub user/repos as a shorthand
  (e.g. `vpm install tpope/vim-fugitive`).
* `vpm update plugin` downloads any updates to the specified plugins, without
  applying them, and outputs the names of any outdated plugins. The incoming
  changes can then be inspected with `vpm incoming plugin`, or applied with
  `vpm upgrade plugin`. If no plugin is specified, all installed plugins are
  updated.
* `vpm incoming plugin` provides a summary of any incoming (downloaded but
  unapplied) changes to the specified plugins. In particular, if the plugin
  originates from a GitHub repo, a link to the relevant compare view is
  provided. If no plugin is specified, incoming changes for all outdated
  plugins are summarized.
* `vpm upgrade plugin` applies any incoming changes to the specified plugins.
  If no plugin is specified, all outdated plugins are upgraded.
* `vpm uninstall plugin` uninstalls one or more plugins.
* `vpm export` writes a shell script to stdout with vpm commands to install the
  currently installed plugins.

Some example sessions:

```
$ vpm install tpope/vim-fugitive
Installing vim-fugitive...
```

```
$ vpm update
vim-fugitive
$ vpm incoming
Can upgrade vim-fugitive from 5d1c219 to 90ee6fb:
5aaa657 Browse handler API
24d4098 Change arity of browse API
7423d72 Ensure clipboard support before using * register
04fe4bf Set nobuflisted in blame buffers
90ee6fb Pass line1 and line2 as 0 for :Gbrowse without range
View changes on GitHub: https://github.com/tpope/vim-fugitive/compare/5d1c219...90ee6fb
$ vpm upgrade
Upgraded vim-fugitive to 90ee6fb.
```

### Installation

The `vpm` script is relatively standalone (the only dependency is git), so just
stick it somewhere on your `$PATH`. You can download it [from this URL][raw],
or clone this repo and create a symlink.

### Why use this as opposed to [Vundle][]?

Vundle has more features, is integrated with vim, has been around longer, is
actively maintained, etc. By contrast, this is a small shell script I largely
threw together in an afternoon, and I am the only user so far (let me know when
this isn't true anymore!).

My initial motivation for writing this was that I didn't want to have to
declare anything in my `.vimrc` like Vundle makes you do. I don't really have a
good argument against this practice though. I just don't like the aesthetic.

### Dealing with non-git plugins

This script assumes all the plugins under `$HOME/.vim/bundle` are git repos.
For plugins that aren't, I use a separate bundle directory that I manage
manually. pathogen supports multiple bundle directories; my `.vimrc` starts
with:

```
execute pathogen#infect('bundle/{}', 'bundle-manual/{}')
```

### License
MIT

[raw]: https://raw.githubusercontent.com/isbadawi/vpm/master/vpm
[pathogen]: https://github.com/tpope/vim-pathogen
[Vundle]: https://github.com/gmarik/Vundle.vim
