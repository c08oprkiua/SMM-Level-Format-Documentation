A .cdt file is a big-endian file, roughtly laid out as:
| Category| First Byte | Last Byte | Byte Size |
|---------------|------------|-----------|-----------|
| Metadata|`0x00`|`0xEF`|           |
| Objects|`0xF0`|           |           |
| Sound Effects|`0x045F0`|           |           |

The "metadata" is a blanket term that I'm using to describe all the information about a level that is not actual object information, which includes, in order:
* Version
* The level's checksum
* The creation date and time of the level
* The level's name
* The level's author
* Which theme the level uses
* Which Mario game the level uses
* The time limit in the level
* What autoscroll speed the level is set to
* How wide the course is
* Mii Data of the creator's Mii (seems to be platform dependent)
* The number of objects in the level

The objects are every thing placed within the level, be it enemies, blocks, arrow signs, pipes, whatever. These also include some extra bits of data where extra data is needed, such as linking info for linking two warp pipes together, or what sound effect the item uses if it has one. 

The file will then contain empty space between the last object used and the start of the sound effects, for every object slot not used, likely to retain specific byte offsets and/or universal file sizing. 

The sound effects are every sound effect referenced by an object.
