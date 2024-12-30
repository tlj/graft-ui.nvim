# graft-ui.nvim

An extension to [graft.nvim](https://github.com/tlj/graft.nvim) to add a simple UI to show the status of the plugins loaded
by `graft.nvim`.

## Installation

See [graft.nvim](https://github.com/tlj/graft.nvim) for a simple `init.lua` method which can be used to ensure 
both `graft.nvim` and other extensions like `graft-ui.nvim` are automatically installed.

Or you can follow the manual installation method below.

Add graft-git.nvim as a git submodule in your Neovim configuration:

```bash
:execute '!git -C ' .. stdpath('config') .. ' submodule add https://github.com/tlj/graft-ui.nvim pack/graft/start/graft-ui.nvim'
```

## Usage

Basic setup in your init.lua. This will automatically install all plugins defined by graft.nvim setup,
and remove any plugins which are installed whithout being defined.

```lua
-- Use graft tools to automatically 
require("graft-ui").setup()

-- The defined plugin will be automatically added as a submodule by graft-git.nvim
require("graft").setup({ 
  now = {
    "catppuccin/nvim", 
    { name = "catppuccin", setup = function() vim.cmd("colorscheme catppuccin-mocha") end } }
  },
})
```

Now you can use `:GraftInfo` to get a floating window with information about defined plugins and if they are currently
loaded.

