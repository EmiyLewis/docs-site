<h1>Server Functions</h1>

-----

Server functions exclusive to the extendedmode framework

!!! Note
    For these functions to work you must be using the extendedmode method of importing functions.
	To do this simply add `shared_script '@extendedmode/imports.lua'` to your fxmanifest.lua.
-----
## ExM.Game.SpawnVehicle

!!! warning ""
	OneSync Only

```lua
ExM.Game.SpawnVehicle(model, coords)
```
This function is a quick and easy way to create a vehicle from the server, no model requesting needed as it's serverside. You can choose whether or not to store the vehicle in a variable.
<h3>Parameters</h3>

| Argument 		| Data Type | Optional 	| Default Value 		| Description |
| ------------- | --------- | ----------| --------------------- | ----------- |
| model 		| hash	 	| No 		| - 					| The model of the vehicle you want to create, can be a hash or a string |
| coords 		| vector3/4	| No 		| - 					| You can use a vector3 or vector4 here, if only using a vector3 the heading will default to 0.0 |

<h3>Example</h3>
```lua
local coords = vec4(-383.644, -1864.176, 20.5, 335.2)
local vehicle = ExM.Game.SpawnVehicle(`jester`, coords)
```
-----
## ExM.Game.CreatePed

!!! warning ""
	OneSync Only

```lua
ExM.Game.CreatePed(pedModel, pedCoords, pedType)
```
This function is a quick and easy way to create a ped from the server, no model requesting needed as it's serverside. You can choose whether or not to store the ped in a variable.
<h3>Parameters</h3>

| Argument 		| Data Type | Optional 	| Default Value 		| Description |
| ------------- | --------- | ----------| --------------------- | ----------- |
| pedModel 		| hash	 	| No 		| - 					| The model of the ped you want to spawn |
| pedCoords 	| vector3/4	| No 		| - 					| You can use a vector3 or vector4 here, if only using a vector3 the heading will default to 0.0 |
| pedType 		| integer 	| Yes 		| 4 (PED_TYPE_CIVMALE)	| The type of ped you want to use. [List of Ped Types](https://hastebin.com/mecuguxipo) |

<h3>Example</h3>
```lua
local coords = vec4(-383.644, -1864.176, 20.5, 335.2)
local ped = ExM.Game.CreatePed(`a_m_m_acult_01`, coords.xyzw, 27)
```
-----
## ExM.Game.SpawnObject

!!! warning ""
	OneSync Only

```lua
ExM.Game.SpawnObject(object, coords, dynamic)
```
This function is a quick and easy way to create an object from the server, no model requesting needed as it's serverside. You can choose whether or not to store the object in a variable.
<h3>Parameters</h3>

| Argument 		| Data Type | Optional 	| Default Value 		| Description |
| ------------- | --------- | ----------| --------------------- | ----------- |
| object 		| hash	 	| No 		| - 					| The model of the object you want to spawn |
| coords	 	| vector3	| No 		| - 					| The coordinates of where to spawn the object |
| dynamic 		| boolean 	| Yes 		| true					| If you want the object to be dynamic or not |

<h3>Example</h3>
```lua
local coords = vec3(-383.644, -1864.176, 20.5)
local object = ExM.Game.SpawnObject(`prop_bin_05a`, coords.xyz, false)
```
------