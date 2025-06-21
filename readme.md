# Autopath

Automatically `:set path=...` in the project, so we can `:find <search>` without relying on fuzzy finder plugins.

- It will use `fd`, if exists.
- If not, then it will use `git ls-files` if it is currently inside a git project.
- Otherwise, it will `set path=**` as fallback.

## Why

This approach is suitable for those looking for a way to _fuzzy_ find files in neovim but don't want to rely on external fuzzy finder.

## Installation

Using lazy.nvim:

```lua
{
  "pirey/autopath",
  opts = { set_keymap = true }
}
```

## Usage

```lua
require('autopath').setup({
  set_keymap = true
})
```

## Keymaps

By default this plugin will set a keymap, `<leader>f` as a shortcut to invoke `:find `.

We can skip the keymap creation by passing `{ set_keymap = false }` when calling `setup()`

