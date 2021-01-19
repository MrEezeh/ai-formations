# Coordinated Group Movement (AI Formations)

Research on coordinated movement of AI in groups, and certain formations while navigating through a world. Based on RTS games and various other researches, includes RTS style selections and input. 

The project is made using Unity (version 2020.1.13f1) and C# (version 7.3).

## Goal

Coordinated group movement are often used in RTS games, to move a group of units in a pattern fit for the given situation. The main focus of this project is to attempt to recreate this behavior, in my own way and figuring out what the best approach to this would be. Since there are over a hundred different ways to go over formations, I will start with keeping the current formation when selecting a group of units and later look into dealing with obstacles while keeping the formation intact, pre-defined patterns, handling different unit sizes/speeds within the same formation and more. 

To embrace the RTS style, I will also try to simulate some of the input and controls available in these games. A few of these controls being: rectangular (multi-) selection, movement commands, grouping/ungrouping units. This is not part of the actual research, but feels like a perfect fit.

## Project info

**Installation Guide**
1. Download [Unity](https://unity.com/)
2. Install the correct Unity version (2020.1)
3. Download code in [ZIP](https://github.com/MrEezeh/AI-Formations/archive/main.zip)
4. Unpack "AI-Formations-main.zip"
5. Add the "Project" folder in Unity Hub
6. All done, open the project

**Game Controls**
- "WASD", freelook camera
- "LMB", selecting unit (hold for rectangle select)
- "CTRL", add to your current selection
- "RMB", move selection
- "G", group units (limit of four groups)
- "Shift-G", ungroup units

## Implementation process

**Game Engine**

Initially, I wanted to use Unreal Engine due to the already existing top-down template and engine architecture. Due to limited time and no previous knowledge of C++ in the engine, I ended up switching to Unity. 

Unity has decent physics simulation and a component called nav mesh agent, which should suffice for the goal of this project. Since there was no decent template available, I chose to start with a simple 3D empty project. To have some graphical representation, I added Universal Render Pipeline together with some assets from the Unity Asset Store **(see [sources](https://github.com/MrEezeh/AI-Formations#sources))**.

**RTS Selection**

Usually Top-Down RTS games give you the option to click and drag to select multiple units at once, so this is what I tried to recreate. The easiest way I could think of, was to make a plane with a collision attached that would extend upwards. This way I could scale this plane when holding down and dragging the mouse around, and upon releasing get all the overlapping objects. Some additional input: holding down "CTRL" will add more units to your current select, and pressing "ESC" to clear your selection.

To visualise the selected units, I added a green circle underneath them.

<img src="https://github.com/MrEezeh/AI-Formations/blob/main/Gifs/rts-selection.gif" width="500" />

**Navigation**

When it comes to navigating in unity, it's fairly straight forward. All I had to do is: attach a Nav Mesh Agent component to my units, configure some variables and build the Navigation Mesh. Once that was done, I can tell the component to move my unit around.

The result isn't too bad for now, but there is definitely more work to do to properly navigate the units in formation.

<img src="https://github.com/MrEezeh/AI-Formations/blob/main/Gifs/navigation.gif" width="500" />

**Grouping**

One last thing before starting with the real deal, is to add grouping functionality. To group up the units, I made a simple array to keep track of the index used and set a limit of four groups in total. Then I made some materials to distinguish each of the groups and added the code to group and ungroup selected units. I also made sure selecting one unit from a group selects the full group.

<img src="https://github.com/MrEezeh/AI-Formations/blob/main/Gifs/grouping.gif" width="500" />

## Functionality

**Grouping**

**Formations**

**Steering**

**Pathfinding**

**Extra**

## Result

*Video/Gif*

## Sources

**Assets**

[Basic Motions FREE Pack - Kevin Iglesias](https://assetstore.unity.com/packages/3d/animations/basic-motions-free-pack-154271)

**Research**

[Coordinated Movement - Jeremiah Warm](http://www.jeremiahwarm.com/coordinated-movement.php)

[Implementing Coordinated Movement - Dave Pottinger](https://www.gamasutra.com/view/feature/3314/coordinated_unit_movement.php?print=1)

[Group Movement in a RTS game - Marc Latorre](https://marclafr.github.io/Research-Group-Movement-RTS-/)

[RTS Group Movement - Sandra Alvarez](https://sandruski.github.io/RTS-Group-Movement/)
