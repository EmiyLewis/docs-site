<h1>Using extendedmode</h1>

!!! danger
	extendedmode is in the **BETA** stage and is not yet recommended for production use however, if you know  what you're doing, you should be fine.
	
	Please report any bugs with as much detail as possible by [making an issue](https://github.com/extendedmode/extendedmode/issues/new) on the extendedmode repository!

## Requirements
- An installation of FXServer artifact 2371 or greater (You can find the latest artifacts here; [Windows](https://runtime.fivem.net/artifacts/fivem/build_server_windows/master/) or [Linux](https://runtime.fivem.net/artifacts/fivem/build_proot_linux/master/))
- A fully configured installation of [fivem-mysql-async](https://github.com/brouznouf/fivem-mysql-async) (or equivalent) version 3.2.0 or greater 

If you are installing extendedmode on a fresh installation of FXServer then follow the [Standard Installation](#standard-installation) guide.  
Otherwise, if you are replacing ESX with extendedmode then follow the [Migration to extendedmode](#migration-to-extendedmode) guide.

Both guides assume that you have knowledge of how to configure FXServer and that you know how to install resources so make sure you do.

-----

## Standard Installation

Installing extendedmode is almost exactly the same as installing ESX so if you've already done that before, this is a piece of cake!  
If you haven't, don't worry, it's not *that* hard.

This guide assumes that you have already installed the  **latest** version of FXServer (preferably  following [this](https://docs.fivem.net/docs/server-manual/setting-up-a-server/) guide) and that you have a MySQL server setup and configured correctly with the `mysql-async` resource.  
If you don't have those setup yet, go and do that first!

<h3>Downloading</h3>

First, you need to download extendedmode and ESX's UI resources, you can do this one of two ways:

- Manually downloading the latest releases from GitHub, easiest for beginners
- Cloning using Git, the preferred method as it simplifies the update process down the track

<h4>Manually</h4>

!!! note
	While it is recommended that you organise your resources into sub directories, FXServer allows you to place resources anywhere in the `resources` provided that you do not place them within other resources or directories with names not surrounded by `[]`.

- Download [extendedmode](https://github.com/extendedmode/extendedmode/releases/latest) into the `resources` directory
- Download [esx_menu_default](https://github.com/ESX-Org/esx_menu_default/releases/latest) into the `resources` directory
- Download [esx_menu_dialog](https://github.com/ESX-Org/esx_menu_dialog/releases/latest) into the `resources` directory
- Download [esx_menu_list](https://github.com/ESX-Org/esx_menu_list/releases/latest) into the `resources` directory

<h4>Using Git</h4>

Running the following commands while within your server's `resources` directory will download all of the resources.
```sh
git clone https://github.com/extendedmode/extendedmode extendedmode
git clone https://github.com/ESX-Org/esx_menu_default esx_menu_default
git clone https://github.com/ESX-Org/esx_menu_dialog esx_menu_dialog
git clone https://github.com/ESX-Org/esx_menu_list esx_menu_list
```

<h3>Installation</h3>

1. Import `extendedmode.sql` into your SQL database
2. Add the following items to your `server.cfg`

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

Now start your server as normal.  
If all goes well, you will see the message `[ExtendedMode] [INFO] ExtendedMode has been initialized` appear in your server console without any errors.

-----
 
## Migration to extendedmode

One of the goals of the extendedmode project is complete backwards compatibility with ESX and EssentialMode.  
This means that the installation is essentially a drag and drop process, provided that all the dependencies are up-to-date.

Before doing anything, **take a backup**.  
extendedmode is **beta** software and while nothing bad *should* happen, if it does, a full backup of both your server and database will save you.  

<h3>Additional Requirements</h3>

- An installation of [EssentialMode](https://github.com/kanersps/essentialmode) >= version 6.4.0

<h3>Installation</h3>

1. Make **absolutely sure** that **all** of the requirements are met.  
	The easiest way to do this is to update FXServer, EssentialMode and MySQL Async to their **latest** versions.  
	extendedmode **will not** work on outdated versions of the dependencies.  
	<br/>

2. Delete the `es_extended` folder from your `resources` folder. (may also be located in the `[essential]` folder)  
<br/>

3. Download extendedmode into your `resources` folder.  
	You can do this by either creating a folder named `extendedmode` in the resources folder and unzipping the content of [this zip](https://github.com/extendedmode/extendedmode/archive/master.zip) into it or, if you have Git installed,  
	running the command `git clone https://github.com/extendedmode/extendedmode extendedmode` while in the `resources` folder.  
	<br/>

4. Add the following items to your `server.cfg`:

```
add_principal group.admin group.user
add_ace resource.extendedmode command.add_ace allow
add_ace resource.extendedmode command.add_principal allow
add_ace resource.extendedmode command.remove_principal allow
```

Now start your server as normal.  
If all goes well, you will see the message `[ExtendedMode] [INFO] ExtendedMode has been initialized` appear in your server console without any errors.

-----

## Troubleshooting

Please make sure that you followed the appropriate guide and that you followed the guide's instructions exactly.  
If you still can't not working or you are getting errors in your server console, please ask for help in the [ExM Discord](https://discord.gg/qKYBQH8) in the #support channel and be sure to provide as much detail as possible!

If there are any common things people get stuck on or easily fixed errors, we'll add work arounds here!