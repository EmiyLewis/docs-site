<h1>Client Functions</h1>

-----

Client functions exclusive to the extendedmode framework

!!! Note
    For these functions to work you must be using the extendedmode method of importing functions.
	To do this simply add `shared_script '@extendedmode/imports.lua'` to your fxmanifest.lua.
-----
## ExM.Game.PlayAnim
```lua
ExM.Game.PlayAnim(animDict, animName, upperbodyOnly, duration)
```

This function is a quick and easy way to play any animation you want without having to request animation dictionaries or specify a heap of parameters.
<h3>Parameters</h3>

| Argument 		| Data Type | Optional 	| Default Value 		| Description |
| ------------- | --------- | ----------| --------------------- | ----------- |
| animDict 		| string 	| No 		| - 					| The animation dictionary |
| animName 		| string 	| No 		| - 					| The animation in the dictionary to play |
| upperbodyOnly | boolean 	| Yes 		| false 				| If you want the animation to only affect the upperbody |
| duration 		| integer 	| Yes 		| -1 (full animation) 	| Duration in ms you want the animation to run for |

<h3>Example</h3>
```lua
ExM.Game.PlayAnim("mini@sprunk", "plyr_buy_drink_pt1", false, 1500)
```

------

## ExM.Game.CreatePed
```lua
ExM.Game.CreatePed(pedModel, pedCoords, isNetworked, pedType)
```

This function is a quick and easy way to create a ped without having to request models or anything, you can choose whether or not to store the ped in a variable or not.
<h3>Parameters</h3>

| Argument 		| Data Type | Optional 	| Default Value 		| Description |
| ------------- | --------- | ----------| --------------------- | ----------- |
| pedModel 		| hash	 	| No 		| - 					| The model of the ped you want to spawn |
| pedCoords 	| vector3/4	| No 		| - 					| You can use a vector3 or vector4 here, if only using a vector3 the heading will default to 0.0 |
| isNetworked 	| boolean 	| Yes 		| false 				| If you want the ped to be networked or not |
| pedType 		| integer 	| Yes 		| 4 (PED_TYPE_CIVMALE)	| The type of ped you want to use. [List of Ped Types](https://hastebin.com/mecuguxipo) |

<h3>Example</h3>
```lua
local coords = GetEntityCoords(PlayerPedId())
local ped = ExM.Game.CreatePed(`a_m_m_acult_01`, vec4(coords.xyz, 180.0), true, 27)
```

------

## ExM.Markers.Add
```lua
ExM.Markers.Add(mType, mPos, red, green, blue, alpha, rangeToShow, bobUpAndDown, mScale, mRot, mDir, faceCamera, textureDict, textureName)
```

This function is a quick and easy way to create a marker and to draw it appropriately and efficiently without degrading performance
<h3>Parameters</h3>

| Argument 		| Data Type | Optional 	| Default Value | Description |
| ------------- | --------- | ----------| ------------- | ----------- |
| mType 		| integer 	| No 		| - 			| The type of marker you want to use [List of Marker Types](https://docs.fivem.net/docs/game-references/markers/) |
| mPos		 	| vector3	| No 		| - 			| The position of where the marker is, you must use a vector3 here |
| red 			| integer	| No 		| - 			| The red channel of the colour you want the marker (0-255) |
| green 		| integer	| No 		| - 			| The green channel of the colour you want the marker (0-255) |
| blue 			| integer	| No 		| - 			| The blue channel of the colour you want the marker (0-255) |
| alpha			| integer	| No 		| - 			| The alpha channel of the colour you want the marker (0-255) |
| rangeToShow 	| integer 	| Yes 		| 50.0			| The range at which you want the marker to show |
| bobUpAndDown 	| boolean 	| Yes 		| false			| If you want the marker to bob up and down |
| mScale	 	| vector3 	| Yes 		| vec(1, 1, 1)	| The size of the marker |
| mRot	 		| vector3 	| Yes 		| vec(0, 0, 0)	| The rotation of the marker |
| mDir	 		| vector3 	| Yes 		| vec(0, 0, 0)	| The direction of the marker |
| faceCamera	| boolean 	| Yes 		| false			| If you want the marker to face the camera |
| textureDict	| string 	| Yes 		| nil			| A custom texture dictionary if you want your own marker type |
| textureName	| string 	| Yes 		| nil			| The name of the texture in the texture dictionary |

<h3>Example</h3>
```lua
-- This would create and store the marker in a variable, this is using custom textures from a Rockstar texture dictionary
local marker = ExM.Markers.Add(1, vec(1224.128, 2710.614, 38.00576), 255, 0, 0, 100, 100.0, false, vec(5, 5, 2), vec(0, 0, 0), vec(0, 0, 0), false, "mpmissmarkers256", "special_vehicle_race_series")

-- Or if you want a more simple circular marker you could do the following which only needs the marker type, pos and rgba values. It will use the default values for everything else
local marker2 = ExM.Markers.Add(1, vec(1224.128, 2710.614, 38.00576), 255, 0, 0, 100)
```

------

## ExM.Markers.Remove
```lua
ExM.Markers.Remove(markerVar)
```

This function is for removing a marker you previously created with [ExM.Markers.Add](#exmmarkersadd)
<h3>Parameters</h3>

| Argument 		| Data Type | Optional 	| Default Value | Description |
| ------------- | --------- | ----------| ------------- | ----------- |
| markerVar 	| integer 	| No 		| - 			| The variable of the marker you want to remove |

<h3>Example</h3>
```lua
-- Create the marker
local marker = ExM.Markers.Add(1, vec(1224.128, 2710.614, 38.00576), 255, 0, 0, 100)

-- Remove it later when you don't need it anymore
ExM.Markers.Remove(marker)
```

------

## ExM.Markers.In
```lua
ExM.Markers.Remove(markerVar)
```

This function is for checking if you're in a marker you previously created with [ExM.Markers.Add](#exmmarkersadd)
<h3>Parameters</h3>

| Argument 		| Data Type | Optional 	| Default Value | Description |
| ------------- | --------- | ----------| ------------- | ----------- |
| markerVar 	| integer 	| No 		| - 			| The variable of the marker you want to check |

<h3>Example</h3>
```lua
-- Create the marker
local marker = ExM.Markers.Add(1, vec(1224.128, 2710.614, 38.00576), 255, 0, 0, 100)

-- Check if you're standing in the marker (run this in a loop)
if ExM.Markers.In(marker) then
	-- You're in the marker, do some stuff here
end
```

------
