```
   ▄████████  ▄█    █▄     ▄████████    ▄████████ ████████▄     ▄████████    ▄████████    ▄█   ▄█▄ 
  ███    ███ ███    ███   ███    ███   ███    ███ ███   ▀███   ███    ███   ███    ███   ███ ▄███▀ 
  ███    █▀  ███    ███   ███    █▀    ███    ███ ███    ███   ███    ███   ███    ███   ███▐██▀   
 ▄███▄▄▄     ███    ███  ▄███▄▄▄      ▄███▄▄▄▄██▀ ███    ███   ███    ███  ▄███▄▄▄▄██▀  ▄█████▀    
▀▀███▀▀▀     ███    ███ ▀▀███▀▀▀     ▀▀███▀▀▀▀▀   ███    ███ ▀███████████ ▀▀███▀▀▀▀▀   ▀▀█████▄    
  ███    █▄  ███    ███   ███    █▄  ▀███████████ ███    ███   ███    ███ ▀███████████   ███▐██▄   
  ███    ███ ███    ███   ███    ███   ███    ███ ███   ▄███   ███    ███   ███    ███   ███ ▀███▄ 
  ██████████  ▀██████▀    ██████████   ███    ███ ████████▀    ███    █▀    ███    ███   ███   ▀█▀ 
                                       ███    ███                           ███    ███   ▀        
                                       ---A Vile Affliction---
                                              v0.2.3G
```                                             
A game I'm making for fun meant to be overly complicated under the hood, but look archaic and simple on the surface. (something like Dwarf Fortress).
Secondary objective is to make an RPG where there is limitless roleplay. This will be achieved in many ways, such as Tone Arguments for dialogue.

This version added a GUI, while keeping the old terminal interface optional through commandline arguments.
This version also added an Item system, along with Bodyparts and races.

- a GUI or TUI interface for the user to input commands and have the game display the outcome.

- Creation and spawning of Entities, NPCs within the game, along with some interaction with them (see: Dialogue and Speak command).

- Creation of Maps and handling Player movement through them, accounting for Entities, map features, or changes in elevation preventing the player movement. There is also a framework in place for 'events' that trigger upon
contact. Events are used to teleport player between different maps (like portals), and Events are also thrown during Dialogue, so that your words can influence the world.

- Dialogue routines to handle Player input and branching dialogue trees. (has been reworked using a DialogueTree data structure, and may be continue to be abstracted to allowed more flexibility with menus, such as interactable signs and the like)

- Lying: by appending 'l' (case insensitive) to a dialogue choice, you choose to 'lie' about what you said. This does not work on every dialogue choice, but some dialogue choices have 'optional' consequences, as well as mandatory ones. When lying is used, the Event for the 'optional' consequences is not thrown, but the mandatory consequences will be.

- Routines to handle playing a unique music track for each Map location.

- Character creation.

- A config file to specify screen size and file locations, as well as colour-mode vs. b&w.

- Save files to save the state of the world. Game data is also stored in an 'EverDark.game' file.

Current implemented commands are:

- Move \<direction\>, moves the player character one tile in the direction specified. Command will be performed as many times are there are \<direction\> arguments following the command. i.e - move north west, move north north, etc.
- Speak \<direction\>, speaks to the entity in the adjacent tile in the direciton specified. If the entity has a larger dialogue tree then the player will enter Dialogue-Mode where they will be prompted for dialogue options (chosen with a number). User input that is not a number (or is a number not listed for an option) will prompt an error. 

- Look, prints a textual description of the current map whose level of detail depends on the player character's Perception stat.

- Survey, prints a topographical map of the area, or changes the Map View to topographic mode in the GUI.

- Stats(TUI EXCLUSIVE), prints a little character sheet with all the player's stats, name, and icon, followed by a list of their bodyparts and their statuses.

- Stuff(TUI EXCLUSIVE), prints a list of the player's items, as well as their total weight and value.

- Drop \<item index\>, removes an item from the players inventory at the specified index (index show when using Stuff command or in the inventory screen). Item will not be dropped if it is (locked).

- Save, saves the current GameState to a .ed file in the 'saves' directory specified in config.txt.

- Exit, exits the program.

The main additions in this version are the GUI interface, as well as the Item and Bodypart system.
