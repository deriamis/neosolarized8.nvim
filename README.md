# neosolarized8.nvim

This is a theme plugin for NeoVim with an extra `midnight` theme that's even darker than `solarized-dark`.

## Features

* TrueColor support for terminal, and works well in NeoVim GUI.
* Defines color for neovim's embedded terminal.
* Defines colors for several common NeoVim plugins, including TreeSitter and CMP

## Requirements

* NeoVim with package support (`nvim -c "echo has('packages')" -c qa` should report `1`)
* [ColorBuddy](https://github.com/tjdevries/colorbuddy.nvim)

For best results, ensure your terminal emulator supports TrueColor. I've tested this with [Alacritty](https://github.com/alacritty/alacritty) both with and without [TMUX](https://github.com/tmux/tmux/wiki) and with [kitty](https://sw.kovidgoyal.net/kitty/). There are probably other terminals that can do this as well, but I have not personally configured them for it.

## Installation

### Packer (recommended)
If you nave not installed [Packer](wbthomason/packer.nvim) yet, follow the directions to installed it. Then, put the following somewhere in your Packer configuration:
```lua
use {
    'deriamis/neosolarized8.nvim'
    requires = { 'tjdevries/colorbuddy.nvim' }
}
```

If you don't have Packer configured to auto-update after saving, run `:PackerSync` to finish the installation.

### vim-plug
Make sure vim-plug is installed and then put the following before the `call plug#end()` line after [ColorBuddy](https://github.com/tjdevries/colorbuddy.nvim) is loaded:
```vim
Plug 'deriamis/neosolarized8.nvim'`
```
Exit NeoVim and run `nvim --headless +PlugInstall +qa` to complete the installation.

### Vundle
First, install [Vundle](https://github.com/VundleVim/Vundle.vim) and then place the following before `call vundle#end()` and after [ColorBuddy](https://github.com/tjdevries/colorbuddy.nvim) is loaded:
```vim
Plugin 'deriamis/neosolarized8.nvim'
```
Exit NeoVim and run `nvim --headless +PluginInstall +qa` to complete the installation.

### Manual

If don't use or don't wish to use a package manager, you can simply clone the repository into your NeoVim packages directory:
```bash
git clone https://github.com/deriamis/neosolarized8.nvim.git "${XDG_DATA_HOME}/nvim/site/pack/neosolarized8.nvim"
```
Be sure you have also installed [ColorBuddy](https://github.com/tjdevries/colorbuddy.nvim) as well.

## Configuration

> ❗️ configuration needs to be set **BEFORE** loading the color scheme with `colorscheme neosolarized8`

| Option          | Default  | Choices                     | Notes                          |
| ----------------| -------- | ----------------------------|--------------------------------|
| theme           | `light`  | `light`, `dark`, `midnight` |                                |
| transparent     | `false`  | `false`, `true`             | Sets background color to NONE  |
| comment_italics | `false`  | `false`, `true`             |                                |
| visibility      | `normal` | `normal`, `low`, `high`     | Adjusts for better visibility  |
| diffmode        | `normal` | `normal`, `low`, `high`     | Sets visibility for diffmode   |
| statusline      | `normal` | `normal`, `low`, `high`     | Sets visibility for statusline |

### Examples

#### Lua
```lua
local colorscheme = require('neosolarized8').setup {
    theme = "midnight",
    transparent = true,
    comment_italics = true,
}
colorscheme.apply()

-- or --
vim.g.neosolarized8_theme = "midnight"
vim.g.neosolarized8_transparent = true
vim.g.neosolarized8_comment_italics = true
require('colorbuddy').colorscheme('neosolarized8')
```

#### VimScript
```vim
let g:neosolarized8_theme = "midnight"
let g:neosolarized8_transparent = true
let g:neosolarized8_comment_italics = true
colorscheme neosolarized8
```

## Lualine Integration

This plugin provides a [Lualine](https://github.com/nvim-lualine/lualine.nvim) theme. To use it, add
the following after setting up your color scheme:
```lua
require('lualine').setup {
    options = {
        theme = 'neosolarized8',
    }
}
```
