Let's start at the beginning, literally. Hexidecimal by hexidecimal. 

The first 8 bytes of the file are the version, which will look something like `00 00 00 00 00 00 00 0B` in a hex editor. 

Next is a checksum, from the bytes `0x8` to `0xA`

Next is the various bytes of information relating to timestamps.
