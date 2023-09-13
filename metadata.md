As previously explained in the overview, metadata is everything besides the object and sound effect data. 

If you've already read over this and/or know what everything is, here's a nice little table that summarizes the raw information on everything:
| Property| Byte type | Byte Start | Byte End | Byte Size |
|--------------------|-----------|------------|----------|-----------|
| Version| u64| `0x00`| `0x07`| 8|
| Checksum| u32| `0x08`|          |           |
| [Creation Year](https://github.com/c08oprkiua/SMM-Level-Format-Documentation/blob/main/metadata.md#creation-date-and-time)| u16|`0x10`|`0x11`| 2|
| [Creation Month](https://github.com/c08oprkiua/SMM-Level-Format-Documentation/blob/main/metadata.md#creation-date-and-time)| u8|`0x12`|`0x12`| 1|
| [Creation Day](https://github.com/c08oprkiua/SMM-Level-Format-Documentation/blob/main/metadata.md#creation-date-and-time)| u8|`0x13`|`0x13`| 1|
| [Creation Hour](https://github.com/c08oprkiua/SMM-Level-Format-Documentation/blob/main/metadata.md#creation-date-and-time)| u8|`0x14`|`0x14`| 1|
| [Creation Minute](https://github.com/c08oprkiua/SMM-Level-Format-Documentation/blob/main/metadata.md#creation-date-and-time)| u8|`0x15`|`0x15`| 1|
| [Level Name](https://github.com/c08oprkiua/SMM-Level-Format-Documentation/blob/main/metadata.md#level-name)| u16| `0x28`|          | 66|
| [Level Game](https://github.com/c08oprkiua/SMM-Level-Format-Documentation/blob/main/metadata.md#level-game)|           | `0x6A`|`0x6B`| 2|
| [Level Theme](https://github.com/c08oprkiua/SMM-Level-Format-Documentation/blob/main/metadata.md#level-theme)| u8|`0x6D`|`0x6D`| 1|
| [Time Limit](https://github.com/c08oprkiua/SMM-Level-Format-Documentation/blob/main/metadata.md#time-limit)| u16|`0x70`|`0x71`| 2|
| [Autoscroll Setting](https://github.com/c08oprkiua/SMM-Level-Format-Documentation/blob/main/metadata.md#autoscroll-setting) | u8|`0x72`|`0x72`| 1|
| [Flag](https://github.com/c08oprkiua/SMM-Level-Format-Documentation/blob/main/metadata.md#flag)|           |`0x73`|`0x73`| 1|
| [Level Width](https://github.com/c08oprkiua/SMM-Level-Format-Documentation/blob/main/metadata.md#level-width)|u32|`0x74`|`0x77`| 4|
| [Mii Hex Data](https://github.com/c08oprkiua/SMM-Level-Format-Documentation/blob/main/metadata.md#mii-hex-data)|           | `0x78`|          | 66|
| [Object Count](https://github.com/c08oprkiua/SMM-Level-Format-Documentation/blob/main/metadata.md#mii-hex-data)| u32| `0xEC`|`0xEF`| 4|


# Version
The first 8 bytes of the file are the version, stored as an unsigned 64 bit integer, which will look something like `00 00 00 00 00 00 00 0B` in a hex editor.


# Checksum
Next is the file's checksum, from the bytes `0x8` to `0x9`. This is a CRC32 checksum of the whole file, sans the bytes from this value and before (so, anything before `0xA`).


# Creation date and time
Next is the various bytes of information relating to timestamps of the level's creation date. They go as follows:
* Year: unsigned 16 bit integer, located at byte offset `0x10`, with a length of 2 bytes

The following are all 8 bit integers:
* Month: located at byte offset `0x12`, with a length of 1 byte
* Day: located at byte offset `0x13`, with a length of 1 byte
* Hour: located at byte offset `0x14`, with a length of 1 byte
* Minute: located at byte offset `0x15`, with a length of 1 byte


# Level Name
The name of the level is something you can actually likely see yourself if you load the .cdt into a hex editor. It starts at the byte offset `0x28` and continues for 66 bytes, with a 1 byte gap of information between each character, which I'm guessing is for the sake of properly reading each character or something. This, if my math is right, means that there is a hard coded limit of about 33 characters for a level name. 


# Level Game
The level game, referring to which Mario game the level is in, starts at offset `0x6A`, with a length of 2 bytes. These two bytes will translate to two characters, as follows:
* M1: Super Mario Bros.
* M3: Super Mario Bros. 3
* MW: Super Mario World
* MU: New Super Mario Bros. U


# Level Theme
The level theme is an unsigned 8 bit integer located at byte offset `0x6D`, and will be a number between 0 and 5, corresponding to which visual theme the level uses;
* 0: Overworld theme
* 1: Underground theme
* 2: Castle theme
* 3: Airship theme
* 4: Underwater theme
* 5: Haunted House theme


# Time Limit
The time limit on the course is stored at offset `0x70` as an unsigned 16 bit integer, and is 2 bytes long. 


# Autoscroll Setting
The autoscroll setting on the course area is set in offset `0x72`, and similarly to the theme, is an 8 bit unsigned integer, this time being a number between 0 and 3, representing one of the following:
* 0: No autoscroll 
* 1: Slow autoscroll
* 2: Medium Autoscroll
* 3: Fast Autoscroll


# Flag
Next is the flag byte, at offset `0x73`, with a byte length of 1. Not sure what this does, however I have seen it used in some projects, so it probably means... something.


# Level Width
The width of the level, i.e. how long the course is from start to flagpole, is an unsigned 32 bit integer at offset `0x74`, with a byte duration of 4 bytes.


# Mii Data
Next is the Mii data, which starts at `0x78` and goes for 66 bytes. This includes the information about the Mii of the level's author. 


# Object Count
The object count is at offset `0xEC` and goes for 4 bytes. THis will be an unsigned 32 bit integer, with a presumed max value of a little under 2600 (2513 to be exact...?) because that's what the max object count in official Mario Maker is. You could try to increase this number for fun I guess, but I am not liable if your console explodes because of it.
