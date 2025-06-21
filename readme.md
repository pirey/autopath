# Autopath

This is a neovim plugin which automatically `:set path=...` in the project, make it possible to use `:find <search>` without relying on fuzzy finder plugins.

See `:h :find` for more information.

- It will use `fd`, if exists.
- If not, then it will use `git ls-files` if it is currently inside a git project.
- Otherwise, it will `set path=**` as fallback.

## Why

Did you know that vim has a built-in file finder? Here's me browsing files in *the neovim* project, using nothing but vim's `:find` cmd.

https://github.com/user-attachments/assets/cb79174e-7cba-4da5-98f3-bfdf6627e06e

This approach is suitable for those looking for a way to _fuzzy_ find files in neovim but don't want to rely on external fuzzy finder.

## Installation

```lua
-- lazy.nvim
{
  "pirey/autopath",
  opts = { set_keymap = true }
}
```

```lua
-- setup manually
require('autopath').setup({
  set_keymap = true
})
```

## Usage

Type in `:find ` followed by partial filename or pattern, then press `<tab>` to find any matches.

For example:

```vimscript
:find main<tab>
```

_fuzzy_ match using pattern

```vimscript

:find long*filename<tab>
```

> NOTE: this does not support real fuzzy matching,
> i.e. if the filename is "my_long_filename" we cannot type `:find myfile<tab>`
> but we can type `:find my*file<tab>` and it will match

## Keymaps

By default this plugin will set a keymap, `<leader>f` as a shortcut to invoke `:find `.

We can skip the keymap creation by passing `{ set_keymap = false }` when calling `setup()`.

