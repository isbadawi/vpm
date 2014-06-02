# vpm

This is a tiny script I use to manage vim plugins installed from GitHub to be
managed by [pathogen][].

You can use it like this:

* `vpm ls` prints a list of installed plugins.
* `vpm install url` installs a plugin from the given url. You can also a pass
a GitHub user/repo as a shorthand (e.g. `vpm install tpope/vim-fugitive`).
* `vpm update plugin` (e.g. `vpm update vim-fugitive`) updates a plugin.
* `vpm update` without specifying a plugin updates all installed plugins.
* `vpm outdated` lists plugins that can be updated.
* `vpm uninstall plugin` uninstalls a plugin.

### Dependencies

This script depends on git 1.8.5 or higher being installed. (It uses the `-C`
argument to git, which lets you run git commands from outside a repo).

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

[pathogen]: https://github.com/tpope/vim-pathogen
