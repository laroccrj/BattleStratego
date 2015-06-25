# Setting up symlinks

## Windows

You need to create symlinks pointing from your dota mods folders to the repo:

Content: `mklink /j "PATH\TO\STEAM\LIBRARY\SteamLibrary\steamapps\common\dota 2 beta\content\dota_addons\Battle Stratego" "PATH\TO\GIT\REPO\BattleStratego\content\dota_addons\Battle Stratego"`

Game: `mklink /j "PATH\TO\STEAM\LIBRARY\SteamLibrary\steamapps\common\dota 2 beta\game\dota_addons\Battle Stratego" "PATH\TO\GIT\REPO\BattleStratego\game\dota_addons\Battle Stratego"`


# Barebones Starter Mod Kit

## Introduction
Barebones is meant to be a jumping off point for creating a mod with all (or nearly all) of the boilerplate taken care of for you.
Barebones sets up the necessary files to create a basic mod (from a scripting persective), allowing you to simply find the places to put your Lua logic in order for you mod to operate.
Barebones currently provides limited examples for performing different tasks, and limited examples for unit/ability/item creation.
Barebones divides scripts up into several sections: Core Files, Libraries, Examples and Internals.

## Installation
Barebones can be installed by downloading this git repository and ensuring that you merge the "content" and "game" folder from this repo with your own "content" and "game" folders.  These should be located in your "<SteamLibraryDirectory>\SteamApps\common\dota 2 beta\" folder.  **Be sure you don't use the "dota_ugc" folder!**

##Core Files
Core Files are the primary files which you should modify in order to get your basic game mode up and running.  There are 4 major files:

###settings.lua
This file contains many special settings/properties created for barebones that allows you to define the high-level behavior of your game mode.
You can define things like respawn times, number of teams on the map, rune spawn times, etc.  Each property is commented to help you understand it.

###gamemode.lua
This is the primary barebones gamemode script and should be used to assist in initializing your game mode.
This file contains helpful pseudo-event functions prepared for you for frequently needed initialization actions.

###events.lua
This file contains a hooked version of almost every event that is currently known to fire in the DotA 2 Lua vscript code.
You can drop your event handler functions in there to have your game mode react to events.

###addon_game_mode.lua
This is the entry-point to your game mode and should be used primarily to precache models/particles/sounds/etc.

##Libraries
I've included some helpful libraries with barebones that may prove useful in your game mode.

###timers.lua
This library allow for easily delayed/timed actions without the messiness of thinkers and dealing with pauses.

###physics.lua
This library can be used for advancted physics/motion/collision of units.  See PhysicsReadme.txt for more information.

###projectiles.lua
This library can be used for advanced 3D projectile systems.  Documentation is currently limited.

##Internals
Barebones uses a few internal lua files in order to put together and handle the properties and pseudo-events systems.  You will likely not have to adjust these files at all.
These files are found in the internal directory.

##Debugging
Barebones now only prints out (spams) debugging information when told to, either by setting the BAREBONES_DEBUG_SPEW value in gamemode.lua to true or adjusting the 'barebones_spew' cvar.
You can change the 'barebones_spew' cvar at any time by typing 'barebones_spew 0' (for off) or 'barebones_spew 1' (for on) in your console.


##Additional Information
- Barebones also comes with a sample loading screen implementation in panorama which you can view and edit via the content panorama directory.
- You can change the name of the multiteams used at the Game Setup screen by editing the game/barebones/panorama/localization/addon_english.txt file.
- You can adjust the number of players allowed on each of your maps by editing addoninfo.txt.

If you have any questions or concerns, leave an issue or mail me (bmddota@gmail.com).
