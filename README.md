# DOOM-FX
Doom/FX for Super Nintendo with SuperFX GSU2A  

## To assemble:  

``MAKE SURE your WinUAE config is loaded, and any changes you make to the config are saved!!``  

1. Set up an emulated Amiga 4000 in WinUAE. [Follow this tutorial up to 4:09 to set up the A4000.](https://youtu.be/Cqu2NAZ9dgg)  

2. in RAM settings, increase Chip to 8 MB and 32-bit chip to 16 MB. (The build process puts the object files to be linked in a RAMdisk, so we need enough free space to link everything)  

3. Install SAS/C  
- Extract the included SAS/C zip in ``prereqs``.  
- Mount the first disk, open it, and run the installer program.  
- Do not touch any of the options, and click "proceed".  
- Ensure it is installing to hard disk and click "proceed".  
- When asked to choose a directory, set the drive to ``system:``, and click "proceed".  
- keep clicking "proceed" until it asks you for the next disk. Mount the disk that it asks you to, and click "proceed".  
- when you see a window reading "the following assigns have been created", click "proceed".  
- Installation complete!  

4. Mount the source directories as virtual drives  
- Download or clone the repo if you haven't already. If you downloaded as a zip, extract it somewhere.  
- Shut down the emulated Amiga by opening the configuration window and clicking "restart".  
- Mount the drives as follows:  (do not remove the SYSTEM drive)

| Device | Volume | Path                                      |
|--------|--------|-------------------------------------------|
| HD     | HD     | [path to repo]\REALITY                    |
| HD2    | HD2    | [path to repo]\REALITY2                   |
| ACCESS | ACCESS | [path to repo]\ACCESS                     |

- Start the emulated Amiga again.

5. Build the game!  
In Workbench:  
go to ``System -> System -> Shell``  
in AmigaShell:  
Change to the HD by typing ``hd:``  
Setup paths: ``execute setup`` (this only needs to be done once per session, if you restart WinUAE, you will have to run this again)  
Build the ROM: ``smake rl``  
To build the ROM and write shell output to a log file located in REALITY/compbi: ``execute buildtolog``

In the REALITY/compbi directory, there should be a .sfc ROM file present if everything worked successfully.  
