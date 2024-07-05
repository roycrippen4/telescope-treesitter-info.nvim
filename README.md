# Telescope Treesitter Info

👎 Are you tired of the crappy experience navigating the builtin `TSInstallInfo` window? 👎

👍 When you just want to search to see if you have a parser installed? 👍

🚫 But instead you have to scroll, scroll, and scroll some more until you find the language you're looking for? 🚫

| ![shit](https://github.com/roycrippen4/telescope-treesitter-info.nvim/blob/images/old.png "Old") |
| :----------------------------------------------------------------------------------------------: |
|                  Searching to see if a parser is installed with `TSInstallInfo`                  |

What if I told you it didn't have to be this way?

What if I told you that you could browse, install, and uninstall treesitter parsers from the comfort telescope.nvim?

##### :rocket: WELL SEARCH NO MORE! :rocket:

Well, I guess I mean continue to search, but specifically for treesitter parsers inside telescope... I digress.

## INTRODUCING Treesitter Install Info!

| ![good](https://github.com/roycrippen4/telescope-treesitter-info.nvim/blob/images/picker.png "New") |
| :-------------------------------------------------------------------------------------------------: |
|                      Searching for a parser using `:Telescope treesitter_info`                      |

### Installation

Setup is as easy as adding the extension as a dependency to your telescope config!

```lua
-- using lazy.nvim
return {
  'nvim-telescope/telescope.nvim',
  ...
  dependencies = {
    'nvim-lua/plenary.nvim',
    'roycrippen4/telescope-treesitter-info.nvim',
  },
  ...
  config = function()
    require('telescope').load_extension('treesitter_info')
  end
```

## Configuration

We don't support configuration! SIMPLE

## Usage

Use the following command to open the treesitter parser list in telescope!

```lua
:Telescope treesitter_info
```

We also took the liberty of deciding you don't need the old command anymore now that you are stuck in our walled garden!

:fire: You can also use the original command to open the parser list in telescope because **we overrode it**! :fire:

```lua
:TSInstallInfo
```

You can even set it up as a keymap!!!

```lua
  vim.keymap.set(
      'n',
      '<leader>fp',
      '<cmd> Telescope treesitter_info <CR>',
      { desc = 'Find treesitter info' }
  )
```

### Not Convinced?

Well let me tell you this!

You can select a language with `<cr>` in telescope's results and the plugin will autofill the corresponding Install or Uninstall command for that language in the command line!

Let's say you don't have the `java` parser installed (because who would, am I right?).

You can open the picker using any of the methods described above, search for `java`, and hit `<cr>`.

The plugin will have autofilled `:TSInstall java`.
All you have to do now, and this is important, is hit `<esc>` to exit, because why the _fuck_ would you install the parser for java! It's that simple!
