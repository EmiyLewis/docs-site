# extendedmode
extendedmode is a community edition fork of es_extended (better known as ESX) and will be maintained by various trusted members of the FiveM community.

## Goals
- Allow even versions of ESX scripts pre 1.2 to continue to function with as few edits as possible.
- Ensure backwards compatibility/new features at the same time as adding optimisations and general other boosts.

## About
es_extended is a roleplay framework for FiveM. ESX is short for EssentialMode Extended. The to-go framework for creating an economy based roleplay server on FiveM and most popular on the platform, too!

ESX was initially developed by Gizz back in 2017 for his friend as the were creating an FiveM server and there wasn't any economy roleplaying frameworks available. The original code was written within a week or two and later open sourced, it has ever since been improved and parts been rewritten to further improve on it.

## Links

- [FiveM Forum Thread]() (coming soon!)
- [ESX Migration Guide]() (coming soon!)
- [FiveM Native Reference](https://runtime.fivem.net/doc/reference.html)

## Requirements

- A fully configured installation of [mysql-async](https://github.com/brouznouf/fivem-mysql-async) (or equivalent)

## Features

- Weight based inventory system
- Weapons support, including support for attachments and tints
- Supports different money accounts (defaulted with cash, bank and black money)
- Many official resources available in our GitHub
- Job system, with grades and clothes support
- Supports multiple languages, most strings are localized
- Easy to use API for developers to easily integrate EX to their projects
- Register your own commands easily, with argument validation, chat suggestion and using FXServer ACL

### Exclusive Features

We have made some exclusive features for extendedmode only, find them all here: ![Functions](functions.md)

## Using extendedmode

Be warned that extendedmode is in ALPHA stages and is **not** ready for production use.

If you already have an ESX installation please see [this]() guide! (coming soon!)

### Downloading

While it is recommended that you organise your resources into sub directories, FXServer allows you to place resources anywhere in the `resources` provided that you do not place them within other resources or directories with names not surrounded by `[]`.

#### Using Git

- `cd resources`
- `git clone https://github.com/extendedmode/extendedmode extendedmode`
- `git clone https://github.com/ESX-Org/esx_menu_default esx_menu_default`
- `git clone https://github.com/ESX-Org/esx_menu_dialog esx_menu_dialog`
- `git clone https://github.com/ESX-Org/esx_menu_list esx_menu_list`

#### Manually

- Download [extendedmode](https://github.com/extendedmode/extendedmode/releases/latest) into the `resources` directory
- Download [esx_menu_default](https://github.com/ESX-Org/esx_menu_default/releases/latest) into the `resources` directory
- Download [esx_menu_dialog](https://github.com/ESX-Org/esx_menu_dialog/releases/latest) into the `resources` directory
- Download [esx_menu_list](https://github.com/ESX-Org/esx_menu_list/releases/latest) into the `resources` directory

### Installation

- Import `extendedmode.sql` in an SQL database
- Configure your `server.cfg` like the example below

```lua
# The included fivem resource needs to be disabled at the moment due to a known issue with mapmanager, this will be fixed soon
#ensure fivem

add_principal group.admin group.user
add_ace resource.extendedmode command.add_ace allow
add_ace resource.extendedmode command.add_principal allow
add_ace resource.extendedmode command.remove_principal allow

ensure mysql-async
ensure extendedmode

ensure esx_menu_default
ensure esx_menu_list
ensure esx_menu_dialog
```

If all goes well, you will see the message `[ExtendedMode] [INFO] ExtendedMode has been initialized` appear in your server console without any errors.