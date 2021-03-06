#Public repository of custom item descriptions for Extended Viewscreen script.

The script: https://github.com/Raidau/public_scripts/blob/master/nb_item_info.lua

Place this folder in your Dwarf Fortress/raw and Dwarf Fortress/data/save/<saved_world>/raw folders.


Files in this folder are used by nb_item_info script to add custom descriptions to items. 

Use "nb_item_info debug" command to run script in debug mode. This will allow you see the required custom file path when you view the item in-game.

Modding guide:

NOTE: It is important to separate description into short lines, because script does not perform any word wrap.

Item descriptions:

Description is read line-by-line from the txt files. Filename must match desired item's type code (like those used for custom reactions). If the item has no subtypes (Table, Chair, Barrel etc.) the file is searched in main folder.

For every item that has subtypes (Weapons, Tools etc.) there is a folder containing corresponding item subtype desctiptions (filename must match subtype code, as defined in raw file, for example ITEM_WEAPON_BATTLE_AXE.txt in WEAPON folder)

item_descriptions/TABLE.txt - will be added to description of any table in game, even artifacts
item_descriptions/TRAPPARTS.txt - mechanisms
item_descriptions/AMMO/ITEM_AMMO_BOLTS.txt - bolts
item_descriptions/AMMO/ITEM_AMMO_ARROWS.txt - arrows

Material descriptions:

Material description files and folders are contained in "Material" folder. The sub-folders use the same logic as custom reactions material definitions. (and the same tokens, except folder names "CREATURE" and "PLANT")

1.Built-in materials (like lye, glass, amber) descriptions are placed in "item_descriptions/Material" folder, 

for example:
	item_descriptions/Material/GLASS_GREEN.txt - green glass
	item_descriptions/Material/LYE.txt - lye

2. Inorganics are in INORGANIC folder

for example:
	item_descriptions/Material/INORGANIC/IRON.txt is the custom description of iron

3. Creature and plant materials. They have CREATURE and PLANT folders, in which you must create a folder for the creature (or plant). The folder name must match that creature (or plant) raw id. The materials are in that folder, filenames are material ids within creature (or plant) raw.

for example:
	item_descriptions/Material/CREATURE/DRAGON/SCALE.txt scale of dragon, (CREATURE_MAT:DRAGON:SCALE)
	item_descriptions/Material/PLANT/MUSHROOM_HELMET_PLUMP/STRUCTURAL.txt basic material of a plump helmet, (PLANT_MAT:MUSHROOM_HELMET_PLUMP:STRUCTURAL)
	item_descriptions/Material/PLANT/OAK/WOOD.txt (PLANT_MAT:OAK:WOOD)

4. Custom filenames are defined within material raw. The script will look for reaction class starting with CUSTOM_DESCR= in the item's material definition. That filename is relative to item_descriptions/Material/. The same reaction class may be added to several materials, but if material has multiple CUSTOM_DESCR= reaction classes only the first one will be picked.
This section is loaded after the item description and before the individial material data

for example:
	if you add [REACTION_CLASS:CUSTOM_DESCR=leather.txt] to several leather materials (or the leather template) the script will load and show addtional description lines from that file.

Several example files are included.
