# vpm

This is a tiny script I use to manage vim plugins installed from GitHub to be
managed by [pathogen][].

You can use it like this:

* `vpm ls` prints a list of installed plugins.
* `vpm install url` installs a plugin from the given url. You can also a pass a
  GitHub user/repo as a shorthand (e.g. `vpm install tpope/vim-fugitive`).
* `vpm update plugin` (e.g. `vpm update vim-fugitive`) updates a plugin.
* `vpm update` without specifying a plugin updates all installed plugins.
* `vpm outdated` lists plugins that can be updated.
* `vpm uninstall plugin` uninstalls one or more plugins.
* `vpm export` writes a shell script to stdout with vpm commands to install the
  currently installed plugins.

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
