# Learn Lua Programming Language

Learn lua for config neovim editor 😜

## What is Lua?

Lua is a procedural programming language used to develop
software, work with machine learning and create all sorts
of games, from a basic text game all the way to VR games.

Lua projects

- Adobe Photoshop Lightroom
- Apache HTTP server
- Awesome WM
- Roblox
- Angry Birds
- ...

Install `lua`: `brew install lua`

Test `lua` installation: `lua -v`

## Basics

### Print text to screen

```lua
print("Hello World")
```

To run script: `lua main.lua`

For writing comments

```lua
-- single line comment
print("Hello World")

--[[
    this is multiline comment
]]
```

To concatenate some strings, use `..` operator

```lua
print('Hello' .. ' ' .. 'World' .. '!')
```

### Data types and variables

Some types

- `nil`: nothing
- `number`: 1, 1.24, 0.1, 44,..
- `string`: 'hello', "hello"
- `boolean`: true - false
- `table`: array - dictionary

To define new variable, use `local` keyword

```lua
local my_name = 'Hieu Nguyen Trong'
print(my_name)

local a
print(a) -- zero value: nil

a = 2
local b = 3
print(a + b)

a = 'hieu'
a = true
```

`local` will create a variable in local scope.

```lua
local name = 'hieu'
local surname = 'trong'
local fullname = surname .. ' ' .. name

local = description = [[
    Multiline string
]]
```

You can also think of a box as a `file`, if you use multiple
`lua` files in your program, then `local` variables can only
be accessed in their respective files, but `global` scope
variables can be accessed from outside the file, meaning your
variable `names` may overwrite the variable `name` inside another file.

```lua
-- global scope variable
Name = 'Hieu Nguyen Trong'
_G.Name = 'Hieu Nguyen Trong'

-- local scope variable
local name = 'Hieu Nguyen Trong'
```

Get type of variables

```lua
str = 'hieu'

print(type(str))
```

### Math in Lua

Converting a string to number

```lua
local str = '1'
print(type(str)) -- string

local n = tonumber(str)
print(type(n)) -- number
```

Operators

- `+`
- `-`
- `*`
- `/`
- `%`: modulus
- `^`: power

Get PI

- `math.pi`: get PI

Get random number

```lua
math.randomseed(os.time())
math.random() -- random value between 0 and 1
math.random(1, 100) -- random value between 0 and 1
```

Get min values

```lua
print(max.min(10, 1, 2, 3, 4))
print(max.max(10, 1, 2, 3, 4))
```

### Strings in Lua

```lua
local str = 'Hello World!'
print(str)
print(type(str)) -- string

local multi = [[
    multiline
    string
]]
print(multi)
```

Get length of the string (number of bytes)

```lua
local str = "Hello World"
print(#str)
```

Convert number to string

```lua
local x = 22
local str = tostring(x)
print(str)
```

Newline character

```lua
print('Hello\nWorld')
```

Some string functions

```lua
local str = "Hello World"

print(string.lower(str))
print(string.upper(str))
print(string.len(str))
```

Substring

```lua
local str = "Hello World"
print(string.sub(str, 1, 5))
```

Get ASCII character

```lua
print(string.char(97))
print(string.byte("a"))
```

Variable pattern

```lua
local str = 'Hello World'
local begin, ending = string.find(str, 'orl')

print('Begin: '..begin.."\nEnd: "..ending)
```

### `If` statements

```lua
if true then
    print('True')
elseif true then
    print('True')
else
    print('False')
end
```

Comparison operator

- `>`
- `<`
- `>=`
- `<=`
- `==`
- `~=`

Logical operators

- `and`
- `or`
- `not`

### Loops

Loop from `1` to `10`, each time plus `i` to `1`

```lua
for i = 1, 10, 1 do
    print(i)
end
```

Loop backward

```lua
local start_val, end_val, step_val = 1, 10, 1

for i = start_val, end_val, step_val do
    print(i)
end
```

Loop over array

```lua
local arr = {1,2,3,4,5}

for i = 1, #arr do
    print(arr[i])
end
```

While loop

```lua
local peeps = 10
while peeps > 0 do
    print('People left at party: ' .. peeps)
    peeps = peeps - 1
end
```

Infinite loop

```lua
while True do
    print('Inifinite loop')
end
```

Repeat .. Until

```lua
local x = 1

repeat
    print('hello')
    x = x + 1
until x > 10
```

### Get user input

```lua
print("What's your name? ")
local input = io.read()

print("Hello " .. input)

io.write('Print one the same line: ')
io.write('Hello')
```

### Tables

Tables represent things like

- array
- record
- set
- list

A table is almost like a container for multiple variables.

Create a table with `{}`

```lua

-- table or array (for convinient)
local arr = {1,2,3,4,5}
print(arr)

-- index from 1
print(arr[1])
print(arr[2])
print(arr[3])
print(arr[4]) -- nil
```

Sort values

```lua
local arr = {1,2,3}
table.sort(arr)

for i = 1, #arr do
    print(arr[i])
end
```

Add new item into an array

```lua
local arr = {1,2,3}

table.insert(arr, 4)
table.remove(arr, 1)

print(arr)
```

Joining table to a string

```lua
local arr = {'hello', 'world'}
print(table.concat(arr, ' ')) -- hello world
```

2D array

```lua
local matrix = {
    {1,2,3},
    {4,5,6},
    {7,8,9}
}

print(matrix[1][1])
```

### Functions

Local functions

```lua
local function greet()
    print('Hello World')
end

greet()
```

Global functions

```lua
_G.function Greet()
    print('Hello World')
end
```

Function params

```lua
local function greet(name)
    print('Hello ' .. name)
end

greet('Hieu')
```

Set default value

```lua
local function greet(name)
    name = name or 'Stranger'
    print('Hello ' .. name)
end

greet()
greet('Hieu')
```

Return value from functions

```lua
local function sum(n1, n2)
    local y = n1 + n2
    return y
end

sum(1,2)

-- y is local scope, cannot be accessed here
print(y)
```

Assign function

```lua
local fn = function ()
    print('Hello World')
end

fn()
```

Return multiple value

```lua
local fn = function ()
    return 1, 2
end

local n1, n2 = fn()
print(n1, n2)

local _, n3 = fn()
print(n3)
```

Function return function

```lua
local function counter()
    local count = 0

    return function()
        count = count + 1
        return count
    end
end

local fn = counter()
print(fn())
```

Pass multiple params

```lua
local function sum(...)
    local sum = 0

    for _, value in pairs({...}) do
        sum += value
    end

    return sum
end
```

### Co-Routines

```lua
local routine_1 = coroutine.create(
    function ()
        for i=1, 10, 1 do
            print('Routine 1')

            if i == 5 then
                coroutine.yield()
            end
        end
    end
)

local routine_func = function ()
    for i = 11, 20 do
        print('Routine2')
    end
end

local routine_2 = coroutine.create(routine_func())

coroutine.resume(routine_1)
print(coroutine.status(routine_1))
coroutine.resume(routine_1)
print(coroutine.status(routine_1))
```

### Working with files

Write to file

```lua
io.output('myfile.txt')
io.write('Hello World')
io.close()
```

Read file

```lua
io.input('myfile.txt')
local file = io.read("*all")
-- local file = io.read("*line")
io.close()

print(file)
```

## The `os` module

```lua
print(os.time())
print(os.time({
    year = 2000,
    month = 10,
    day = 1,
    hour = 13,
    min = 20,
    sec = 10
}))

print(os.date())
print(os.getenv('PATH'))
print(os.rename('myfile.txt', 'rename.txt'))
print(os.remove('rename.txt'))
print(os.execute('ls'))
```

## Custom modules

A module is basically a lua file that returns a single
table when called.

A package is a collection of modules.

Create new file `mymath.lua`. Now we have 2 files

- `main.lua`
- `mymath.lua`

```lua
-- mymath.lua

mmath = {}

-- global function
function mmath.add(x, y)
    return x + y
end

return mmath
```

```lua
-- main.lua

local mod = require('mymath')

print(mod.add(1,2))
```

## OOP

```lua
local function Pet(name)
    name = name or 'Luis'

    return {
        name = name,
        status = 'hungry'

        feed = function(self)
            self.status = 'full'
        end
    }
end

local cat = Pet('Kitty')
print(cat.name)
print(cat.status)

cat.feed()
print(cat.status)
```

Inheritance

```lua
local function Dog(name, breed)
    local dog = Pet(name)

    dog.breed = brred
    dog.loyalty = 0

    dog.isLoyal = function(self)
        return self.loyalty >= 10
    end

    dog.bark = function(self)
        print('Woof')
    end

    return dog
end

local dog = Dog('Doggy', 'Poodle')

if dog:isLoyal() then
    print('Loyal')
end
```

## Meta methods

```lua
local function addTableValues(x, y)
    return x.num + y.num
end

local tbl1 = { num = 50 }
local tbl2 = { num = 10 }

-- overload operator
local metatable = {
    __add = addTableValues
    __sub = function (x, y)
        return x.num - y.num
    end
}

setmetatable(tbl1, metatable)

local asn = tbl1 + tbl2

print(ans)
```

## Next?

- LuaRocks: online package repository
- Love2d: game engine

## Setup Neovim with Lua

Prebuild vim

- AstroVim
- LunarVim

Required

- iTerm2
- Nerd Fonts: Meslo Nerd font

Install NeoVim v0.8: `brew install neovim`

Checking neovim: `nvim --version`

Config directory

- `.config/`
  - `nvim/`
    - `init.lua`
    - `lua/`
      - `[you name]/`
        - `core/`
          - `colorscheme.lua`
          - `options.lua`
          - `keymaps.lua`
        - `plugins/`
          - `lualine.lua`
          - `telescope.lua`
          - `vim-tree.lua`
          - `...`
        - `plugins-setup.lua`

## Basic options & settings

Import core files to `init.lua`

```lua
require('lua.dalatcoder.core.options')
require('lua.dalatcoder.core.keymaps')
require('lua.dalatcoder.core.colorscheme')
```

Add some options in `lua.dalatcoder.core.options`

```lua
-- opt table ref
local opt = vim.opt

-- line numbers
opt.relativenumber = true
opt.number = true

-- tabs & indentation
opt.tabstop = 2
opt.shiftwidth = 2
opt.expandtab = true
opt.autoindent = true

-- line wrapping
opt.wrap = false

-- search settings
opt.ignorecase = true
opt.smartcase = true

-- cursor line
opt.cursorline = true

-- appearance
opt.termguicolors = true
opt.background = "dark"
opt.signcolumn = "yes"

-- backspace
opt.backspace = "indent,eol,start"

-- clipboard
opt.clipboard:append("unnamedplus")

-- split windows
opt.splitright = true
opt.splitbelow = true

-- daw include -
opt.iskeyword:append("-")
```

Packer Plugin Manager

Require in `init.lua`

```lua
require('lua.dalatcoder.plugins-setup')
require('lua.dalatcoder.core.options')
require('lua.dalatcoder.core.keymaps')
require('lua.dalatcoder.core.colorscheme')
```

Setup `packer` in `lua.dalatcoder.plugins-setup`

```lua
-- auto install packer if not installed
local ensure_packer = function()
  local fn = vim.fn
  local install_path = fn.stdpath("data") .. "/site/pack/packer/start/packer.nvim"
  if fn.empty(fn.glob(install_path)) > 0 then
    fn.system({ "git", "clone", "--depth", "1", "https://github.com/wbthomason/packer.nvim", install_path })
    vim.cmd([[packadd packer.nvim]])
    return true
  end
  return false
end
local packer_bootstrap = ensure_packer() -- true if packer was just installed

-- autocommand that reloads neovim and installs/updates/removes plugins
-- when file is saved
vim.cmd([[
  augroup packer_user_config
    autocmd!
    autocmd BufWritePost plugins-setup.lua source <afile> | PackerSync
  augroup end
]])

-- import packer safely
local status, packer = pcall(require, "packer")
if not status then
  return
end

-- add list of plugins to install
return packer.startup(function(use)
  -- packer can manage itself
  use("wbthomason/packer.nvim")

  use("bluz71/vim-nightfly-guicolors") -- preferred colorscheme

  if packer_bootstrap then
    require("packer").sync()
  end
end)
```

Configure colorscheme in `lua.dalatcoder.core.colorscheme`

```lua
vim.cmd("colorscheme nightfly")
```

But, to be safety, we can check before active the theme

```lua
-- set colorscheme to nightfly with protected call
-- in case it isn't installed
local status, _ = pcall(vim.cmd, "colorscheme nightfly")

if not status then
  print("Colorscheme not found!") -- print error if colorscheme not installed
  return
end
```

Custom keymaps in `lua.dalatcoder.core.keymaps`

```lua
-- set leader key to space
vim.g.mapleader = " "

-- set key in insert mode
-- use jk to exit insert mode
keymap.set("i", "jk", "<ESC>")

-- set key in normal mode
-- clear search highlights
keymap.set("n", "<leader>nh", ":nohl<CR>")
```

Window related plugins:

- `vim-tmux-navigator`: uses `Ctr-h,j,k,l` to move between
  windows and tmux

- `vim-maximizer`: maximize splits and restore them back to their
  original size

Essential plugins

- `vim-surround`
- `ReplaceWithRegister`
- `Comment.nvim`

Comment plugin

- Create plugin config file at: `dalatcoder.plugins.comment.lua`

```lua
-- import comment plugin safely
local setup, comment = pcall(require, "Comment")
if not setup then
  return
end

-- enable comment
comment.setup()
```

Import config file in `init.lua`

```lua
-- plugin configurations
require("dalatcoder.plugins.comment")
```

Use cases:

- Comment current line: `gcc`
- Comment 5 lines below: `gc5j`

Plenary plugin includes lua functions that many plugins use

File explorer with `nvim-tree`

- Config plugin at `dalatcoder.plugins.nvim-tree.lua`
- Import plugin config file at `init.lua`
- Create keymap to open/close quickier at `dalatcoder.core.keymaps`

VScode Like Icons with `nvim-web-devicons`

Config status line with `lualine.nvim`

- Config plugin at `dalatcoder.plugins.lualine.lua`
- Import plugin config file at `init.lua`

Config Telescope Fuzzy Finder

- Install `ripgrep`: `brew install ripgrep`
- Add plugin `telescope-fzf-native`
- Add plugin `telescope.nvim`
- Config plugin at `dalatcoder.plugins.telescope.lua`
- Import plugin config file at `init.lua`
- Create keymap to active telescope at `dalatcoder.core.keymaps`

Setup basic autocompletion

- Add plugin `nvim-cmp`: autocompletion
- Add plugin `cmp-buffer`: recommend text from current buffer
- Add plugin `cmp-path`: recommend file path
- Add plugin `LuaSnip`: snippet engine
- Add plugin `cmp_luasnip`: recommend snippets
- Add plugin `friendly-snippets`: collections of useful snippets
- Config plugin at `dalatcoder.plugins.nvim-cmp.lua`
- Import plugin config file at `init.lua`

Configuring LSP - Language Server Protocol, it'll give us the
ability to have really smart auto code completion and also
the ability to perform code actions to fix problems in our code.

Add plugins for managing and installing LSP servers

- Add `mason.nvim` plugin, use this plugin as the source of truth
  to manage LSP servers
- LSP is built into neovim but the LSP servers themselves need to
  be installed
- Add `nvim-lspconfig` for configuring LSP servers
- Add `mason-lspconfig` as an adapter between `mason` and `lspconfig` plugins
- Add `cmp-nvim-lsp` config LSP servers so that they appear in
  Auto Completion
- `lspsaga.nvim` will add enhanced UI to our LSP experience
- `typescript.nvim` to add more functionality to the TS server
- `lspkind.nvim` add vscode like icons to our Auto Completion
- Create all related config files at `dalatcoder.plugins.lsp`
  - `lsp.mason.lua`
  - `lspconfig.lua` for configuring all LSP servers
  - `lspsaga.lua` for configuring LSP Saga
- Import plugin config file at `init.lua`

Open neovim, press command `:Mason` to install `LSP` servers

Formating and Linting

- Add `null-ls.nvim`: used to config formatter and linter
- Add `mason-null-ls.nvim`: adapter
- Config plugin at `dalatcoder.plugins.lsp.null-ls`

Highlighting with TreeSitter `nvim-treesitter`

Auto closing with `nvim-autopairs` and `nvim-ts-autotag`
