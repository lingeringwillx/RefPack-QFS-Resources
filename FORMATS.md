### Formats

Refpack was originally developed by EA Canada, and it received some updates over time that changed it slightly. It was also passed to the various studios that worked with or published games under EA, who modified it to work as they like. Most of the times they just changed the header, but in some cases they changed the method of encoding and decoding as well.

#### EAC

The header for EA Canada has the following format:

```
1 byte flags:

  bit 0b10000000: 4 bytes are used for the decompressed size if enabled, 3 bytes are used if disabled

  bit 0b01000000: unknown, used in Spore

  bit 0b00010000: Always set

  bit 0b00000001: compressed size added to header

1 byte magic: 0xFB

if flags 0b10000000 and 0b00000001 set: 4 bytes compressed size (big endian)

else if flag 0b00000001 set: 3 bytes compressed size (big endian)

if flag 0b10000000 set: 4 bytes uncompressed size (big endian)

else: 3 bytes uncompressed size (big endian)
```

For old 90's titles, alternative algorithms could be used in place of RefPack depending on the flags. This includes Huffman Encoding, Byte-Pair Encoding, and Run-Length Encoding. For more information:

1. [C&C Generals source code](https://github.com/electronicarts/CnC_Generals_Zero_Hour/tree/main/Generals/Code/Libraries/Source/Compression/EAC)

2. [Martin Korth](https://problemkaputt.de/psxspx-cdrom-file-compression-ea-methods.htm)

3. [Stunts Wiki](https://wiki.stunts.hu/wiki/Compression#EAC_packing)

#### Maxis

In the early to mid 2000's, Maxis deviated from the standard EAC header by adding the compressed size before the flags and magic character. Later Maxis games use the regular header.

```
4 bytes compressed size (little endian)

2 bytes magic header: 0x10FB

3 bytes uncompressed size (big endian)
```

#### Fusion

Refpack is also used in TT Fusion's games on the PSP and DS consoles[^lego]. They likely obtained the algorithm through its predecessor, Warthog Games, which developed some games that are published by EA[^warthog].

Files can be compressed in multiple chunks, with the size of each chunk mentioned in the header.

##### Standard

The earliest header uses the same encoding as the standard EAC implementation, however the header has the following format:

```
2 bits compression method: 01 for refpack

30 bits chunk size (big endian)
```

##### Modified v1

This has the same header as the standard version, but the byte encoding is different. For more information, refer to the [implementations](https://github.com/lingeringwillx/RefPack-QFS-Resources#Implementations).

##### Modified v2

Also uses the modified refpack encoding, but has a different header.

```
27 bits chunk size (big endian)

5 bits flags:

  3 bits unknown

  2 bits compression method: 01 for refpack
```

#### Notes

- 0xFB likely stands for Frank Barchard, the developer of the algorithm.

- According to EA's source code, support for the `0b10000000` flag was added in 2001[^refabout]. Older titles are limited to 3 bytes for the uncompressed size in the header, which means that the maximum size of the resources that they can compress is 16 MB.

- The uncompressed size is stored in big endian even in games that natively use little endian.

- I have not seen the `0b00000001` flag in any game files. It's likely never or rarely used. EA's source code shows that the decompressor supports this flag[^refdecode]. However, the compressor doesn't produce any assets with the flag[^refencode].

[^lego]: [ZenHAX](https://zenhax.com/viewtopic.php@t=380.html)

[^warthog]: [Wikipedia](https://en.wikipedia.org/wiki/Warthog_Games#List_of_games)

[^refabout]: [C&C Generals source code: refabout.cpp](https://github.com/electronicarts/CnC_Generals_Zero_Hour/blob/main/Generals/Code/Libraries/Source/Compression/EAC/refabout.cpp)

[^refdecode]: [C&C Generals source code: refdecode.cpp](https://github.com/electronicarts/CnC_Generals_Zero_Hour/blob/main/Generals/Code/Libraries/Source/Compression/EAC/refdecode.cpp)

[^refencode]: [C&C Generals source code: refencode.cpp](https://github.com/electronicarts/CnC_Generals_Zero_Hour/blob/main/Generals/Code/Libraries/Source/Compression/EAC/refencode.cpp)
