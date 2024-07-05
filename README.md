# Telescope Treesitter Info

Are you tired of the crappy experience navigating the builtin `TSInstallInfo` window?
When you just want to search to see if you have a parser installed?
But instead you have to scroll and scroll until you find the language you're looking for?

| ![help](https://github.com/roycrippen4/telescope-treesitter-info.nvim/blob/images/old.png "Old") |
| :----------------------------------------------------------------------------------------------: |
|                  Searching to see if a parser is installed with `TSInstallInfo`                  |

What if I told you it didn't have to be this way?
What if I told you that you could browse, install, and uninstall treesitter parsers from the comfort telescope.nvim?

#### WELL SEARCH NO MORE!

Well, I guess I mean continue to search, but with my extension, but also specifically for just treesitter parsers... I digress.

## Using help

| ![Telescope helptags](https://github.com/catgoose/telescope-helpgrep.nvim/blob/7c52e4840ee0f404d8f79d3a457d6214a073c1e9/helpgrep1.png "Telescope help_tags") |
| :----------------------------------------------------------------------------------------------------------------------------------------------------------: |
|                                   Searching for help the help topic: `vim.api.nvim_open_win` using `:Telescope help_tags`                                    |

| ![Telescope helpgrep](https://github.com/catgoose/telescope-helpgrep.nvim/blob/7c52e4840ee0f404d8f79d3a457d6214a073c1e9/helpgrep2.png "Telescope helpgrep") |
| :---------------------------------------------------------------------------------------------------------------------------------------------------------: |
|                                     Grepping through help files for `vim.api.nvim_open_win` with `:Telescope helpgrep`                                      |

## Alternative

Of course you can use the built in `helpgrep`, but I wanted something more
"Telescopic" rather than having to filter through quickfix.

## Usage

Defaults to `live_grep` picker:

```lua
:Telescope helpgrep
```

Uses `Telescope live_grep` builtin:

```lua
:Telescope helpgrep live_grep
```

Uses `Telescope grep_string` builtin:

```lua
:Telescope helpgrep grep_string
```

### Example

In Telescope setup:

```lua
local actions = require("telescope.actions")
local builtin = require("telescope.builtin")

telescope.setup({
  ...
  extensions = {
    helpgrep = {
      ignore_paths = {
        vim.fn.stdpath("state") .. "/lazy/readme",
      },
      mappings = {
        i = {
          ["<CR>"] = actions.select_default,
          ["<C-v>"] = actions.select_vertical,
        },
        n = {
          ["<CR>"] = actions.select_default,
          ["<C-s>"] = actions.select_horizontal,
        }
      },
      default_grep = builtin.live_grep,
    }
  }
})
```

```lua
require("telescope").load_extension("helpgrep")
```

No paths are ignored by default, but if you use `lazy.nvim` it is recommended
to add `vim.fn.stdpath("state") .. "/lazy/readme"` to the `ignore_paths` table

## TODO

- [ ] Set win/buffer optsions for help window, configurable by setup opts

## Extra

My other neovim projects

- [neovim config](https://github.com/catgoose/nvim)
- [do-the-needful.nvim](https://github.com/catgoose/do-the-needful.nvim)
- [vue-goto-definition](https://github.com/catgoose/vue-goto-definition.nvim)
