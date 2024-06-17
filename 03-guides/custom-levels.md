# Importing Custom Levels

1. Make or modify your level in Doom Builder. Make sure the format is ``Doom: Doom (Doom format)``. The map has to be fully Doom 1 compatible. If your map is already prepared for Doom 1, skip to Step 2. Otherwise, if you are porting maps from another Doom engine game, use dilligence to ensure that your linedef actions, THING types, and texture usage are valid in Doom 1. An additional limitation of the Reality Engine to be aware of is the lack of support for transparent midtextures. Refer to troubleshooting for additional guidance. As an additional tip, remember that flats in the SNES engine are flat colours, so you don't have to be too picky about flat usage. For something like a grass flat in a Doom 2 map, you could use a marble floor, as that would be a green texture. The WAD doesn't have to be complete, it only has to be the lumps for the level(s) you want to import.

2. Copy your level to ``02-extra-tools/idbsp``, then drag-and-drop the WAD over WADBuilder.bat. Make sure you overwrite your WAD file when prompted by IDBSP, otherwise your lumps will be duplicated in the same file.

3. In AmigaShell, set up the paths if you haven't already (from ``HD:source``, run ``execute setuprl``). 

4. Switch to ``HD2:`` and execute the command ``execute rl:make/ripwad``.  

5. Go to ``HD2/DOOMDATA`` and copy the folder with your level's map number to ``HD2/DOOM/1.666/WAD.DATA/LEVELS``. 

6. Convert the level from Doom format to Reality Engine format by switching to ``rl:binaries`` and running ``execute rl:make/level eX mY`` where X is the episode number of your level, and Y is the map number. If you see any error messages about ``touch``, disregard them.  

7. Switch back to ``HD:source`` and run ``smake rl`` to build the game.  

# Troubleshooting

## "Can't FIT section" error
Try disabling some levels in ``HD/source/rage.i``.  
You can also enable ``useE1M1ONLY`` if you're only replacing the first map and don't care about any others.  

## The emulator freezes when I try to convert a level!
You may be using engine features in your level that ``RIPDOOM`` does not support. Usually this is due to the usage of Doom II linedef actions such as fast doors. In this instance, you would have to change the linedef action type from the (Fast) to Normal variant in Doom Builder. To avoid breaking map functionality, ensure that the trigger type is also equivalent, such as Switch or Walkover, Once or Repeatable, etc.
