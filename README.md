# js-obc
minecraft one block command generator...in javascript

This gives you a convenient editor that can create so called 'one command block' creations: you place down one command block, paste in an enormous command script, and let the code do the rest.

This is a fork of MaudDibb's project, who was heavliy inspired by the methods used by TheRedEngineer to easily create these scripts. I (NiceMarkMC) adapted it to work in newer versions.
Note that this only supports Minecraft 1.14 and above command syntax.

# Installation 
just download index.html and open in your favorite browser.

# Usage
enter your commands, one line at a time, into the big box in the middle of the screen. It's OK if the lines wrap around, as long as each command is on its own line, and most importantly, *separated by carriage returns*. Do not lump multiple commands into one line. Let the script do that for you. Click on 'One Command!' to generate the command string in the text box on the bottom of the page. Open Minecraft (1.14 and above), start a map, give yourself a command block and copy-pasta this command into the command block gui in Minecraft, and activate the block. that's it.

# How it works
A falling block entity set to the id of an activator rail is summoned, the entity has "passengers" - command block minecarts with commands. There are a few extra commands added to every one command creation to clean up the setup. 
What happens when you power on the command block that you placed is this falling activator rail entity is summoned, it falls onto the command block and becomes a block, it also becomes powered. The command block minecarts that were initially "passengers" of the activator rail fall onto the powered activator rail and start executing commands. They will execute your commands first and then they will execute a few additional commands to destroy themselves and remove the setup.

# Lag with many repeating command blocks

Some creations may need repeating blocks...some may need MANY repeating command blocks (my lights out game uses almost 50). If you do use them, *please* make sure you add TrackOutput:0b to their datatags...this will eliminate lag as these blocks (in always active mode) run at 20 ticks per second..when you have many of these ticking along at that speed, they will constantly update their previous output field (open one and look at the command gui, that text box showing previous output..ya. thats the one), causing a lot of chunk updates. You might consider doing that to any other blocks chained off those repeating command blocks.
