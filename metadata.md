Let's start at the beginning, literally. Hexidecimal by hexidecimal. 
# Version
The first 8 bytes of the file are the version, which will look something like `00 00 00 00 00 00 00 0B` in a hex editor. 
# Checksum
Next is the file's checksum, from the bytes `0x8` to `0xA`. This is a CRC32 checksum of the whole file, sans the bytes from this value and before (so, anything before `0x10`).
# Creation date and time
Next is the various bytes of information relating to timestamps of the level's creation date. They go as follows:
* Year: located at byte offset `0xA`, with a length of 12 bytes
* Month: located at byte offset `0xC`, with a length of 1 byte
* Day: located at byte offset `0xD`, with a length of 1 byte
* Hour: located at byte offset `0xE`, with a length of 1 byte
* Minute: located at byte offset `0xF`, with a length of 1 byte
# Level Name
The name of the level is something you can actually likely see yourself if you load the .cdt into a hex editor. It starts at the byte offset `0x28` and continues for 66 bytes, with a 1 byte gap of information between each character, which I'm guessing is for the sake of properly reading each character or something. This, if my math is right, means that there is a hard coded limit of about 33 characters for a level name. 
# Level Game
Starting at offset `0x6A` is the mode, with a length of 2 bytes. This refers to which Mario game the level is in. These will be two characters, as follows:
* M1: Super Mario Bros.
* M3: Super Mario Bros. 3
* MW: Super Mario World
* MU: New Super Mario Bros. U
# Level Theme
The level theme is located at byte offset `0x6D`, and will be a number between 0 and 5, corresponding to which visual theme the level uses;
* 0: Overworld theme
* 1: Underground theme
* 2: Castle theme
* 3: Airship theme
* 4: Underwater theme
* 5: Haunted House theme
# Time Limit
The time limit on the course is stored at offset `0x70`, and is 2 bytes long. 
# Autoscroll Setting
The autoscroll setting on the course area is set in offset `0x72`, and similarly to the theme, is a number between 0 and 3, representing one of the following:
* 0: No autoscroll 
* 1: Slow autoscroll
* 2: Medium Autoscroll
* 3: Fast Autoscroll
# Flag
Next is the flag byte, at offset `0x73`, with a byte length of 1. Not sure what this does.

Next is kind of the beginning of the course data, but I will include it here because it's metadata *about the course*. 
# Level Width
The width of the course, i.e. how long the course is from start to flagpole, is at offset `0x74`, with a byte duration of 4 bytes.
# Mii Hex Data
Next is the Mii hex data, which starts at `0x78` and goes for 66 bytes.
# Object Count
The object count is at offset `0xEC` and goes for 4 bytes. THis will be an unsigned 32 bit integer, with a presumed max value of a little under 2600 (2513 to be exact...?) because that's what the max object count in official Mario Maker is. You could try to increase this number for fun I guess, but I am not liable if your console explodes because of it.
