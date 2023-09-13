A .cdt file is roughtly laid out as:
* (what I'm referring to as) the metadata
* then all the objects of the level
* then the sound effects

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
* Hex data of a Mii associated with the level (the creator's Mii?)
* The number of objects in the level

The objects are every thing placed within the level, be it enemies, blocks, arrow signs, pipes, whatever. These also include some extra bits of data where extra data is needed, such as linking info for linking two warp pipes together, or what sound effect the item uses if it has one. 

The sound effects are every sound effect referenced by an object.
