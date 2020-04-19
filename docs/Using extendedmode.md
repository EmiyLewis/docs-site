<h1>Using extendedmode</h1>

-----

Be warned that extendedmode is in ALPHA stages and is **not** ready for production use.

If you already have an ESX installation please see [this]() guide! (coming soon!)

-----

## Downloading

While it is recommended that you organise your resources into sub directories, FXServer allows you to place resources anywhere in the `resources` provided that you do not place them within other resources or directories with names not surrounded by `[]`.

-----

<h3>Using Git</h3>

- `cd resources`
- `git clone https://github.com/extendedmode/extendedmode extendedmode`
- `git clone https://github.com/ESX-Org/esx_menu_default esx_menu_default`
- `git clone https://github.com/ESX-Org/esx_menu_dialog esx_menu_dialog`
- `git clone https://github.com/ESX-Org/esx_menu_list esx_menu_list`

-----

<h3>Manually</h3>

- Download [extendedmode](https://github.com/extendedmode/extendedmode/releases/latest) into the `resources` directory
- Download [esx_menu_default](https://github.com/ESX-Org/esx_menu_default/releases/latest) into the `resources` directory
- Download [esx_menu_dialog](https://github.com/ESX-Org/esx_menu_dialog/releases/latest) into the `resources` directory
- Download [esx_menu_list](https://github.com/ESX-Org/esx_menu_list/releases/latest) into the `resources` directory

-----

## Installation

!!! IMPORTANT
    You **must** be running server artifact `2371` or higher  
	Find the latest artifacts here; [Windows](https://runtime.fivem.net/artifacts/fivem/build_server_windows/master/) or [Linux](https://runtime.fivem.net/artifacts/fivem/build_proot_linux/master/)

- Import `extendedmode.sql` in an SQL database
- Add the follow items to your `server.cfg`

```
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