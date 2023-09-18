# Object Layout
Objects are 32 byte long chunks of data, stored one after the other, starting at offset `0xF0`, which take up a majority of the data in the file for obvious reasons. They contain information about the coordinates of the object, the type of object it is, the size if it's resizable, sound effects if any are applied, an ID specifically used for warp pipes and others to link two or more objects to each other, and more. 

Objects sometimes can have child objects in their data. This, for example, would be the case for a ? block that has a mushroom inside of it; The block is the parent and the mushroom is the child. 

All the byte offsets on this page are going to be relative, i.e. I am going to be speaking about them as if the very first byte of the object data is offset `0x00`, because otherwise this information would be annoying to work with, and not easy to universalize to every object.

# Object Coordinates
These parameters are in the very first bunch of bytes in the object's data. The X axis, starting at offset `0x00` and ending at `0x03`, and the Z axis, starting at offset `0x04` and ending at `0x07`, are unsigned 32 bit integers, and the Y axis, which starts at `0x08` and ends at `0x09`, is an unsigned 16 bit integer.

# Object Size
The width and height of an object are stored in bytes `0x0A` and `0x0B` respectively, as signed 8 bit integers. The position is in blocks.
# Object Flags

# Extended Object Data
This is used for specific data for some objects, such as the initial rotation value of a fire bar

# Object Type

# Object Link ID

# Sound Effect Index

# Unknown flag

# Child Object's Transformation ID
This is a special field specifically used by the Mystery Mushroom, for assigning which costume it gives Mario upon consumption. It is a signed 8 bit integer, with values ranging from 0 to 98. 

