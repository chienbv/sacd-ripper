# Introduction #

The ScarletBook is Philips and Sony's 1999 specification document for Super Audio Compact Disc ( SACD ), a high-resolution audio format that features multi-channel sound. SACD discs can contain two different versions of the same material.

# Pit Signal Processing #

SACD includes various copy protection measures of which the most prominent is Pit Signal Processing (PSP), a physical watermarking feature that contains a digital watermark modulated in the width of pits on the disc (data are stored in the pit length). The optical pickup must contain special circuitry to read the PSP watermark, which is then compared to information on the disc to make sure it is legitimate. Because the majority of DVD players and all DVD-ROM drives use an optical pickup that lacks this specialized watermark detection circuitry, although they can read the data on the SACD layer, they cannot decode the audio of a protected SACD disc. With one exception: The first two generations of Sony's Playstation 3 (PS3) game console are capable of reading SACD ScarletBook and bypass the copy protection.

# Specification #

A ScarletBook disk always contains a Master Table of Contents (TOC). This Master TOC is stored several times to insure there is a backup in case of disc corruption. The Master (TOC) stores all information related to the disc, this includes position & size to two or multi channel TOCs, album title, album artist and genre data.

Track data is stored in a continuous stream and consists of 1 or 2 areas. The following combinations of areas on a disc are allowed:
  * 2-channel area
  * 5-channel area
  * 6-channel area
  * 2-channel and 5-channel area
  * 2-channel and 6-channel area

The Two or Multi Channel TOC referred by the Master TOC, include track count, disc and track titles, track artist and ISRC codes, genre data and (optional) Super Audio CD text information which can be displayed during playback.

There is lot's of speculation about an UDF filesystem for SACDs, but UDF is not part of the specification as most discs don't have it.

### ScarletBook SACD Example ###

```

//                  Start LSN    Size     Comment
//                  -----------  -------  ---------------------------------------------
// File System      0            510      Only some SACD's have UDF data, so ignore..
// Master TOC-1     510          10
// Master TOC-2     520          10
// Master TOC-3     530          10
// 2 Channel
//   Area TOC-1     -            -        position & size is stored in Master TOC
//   Track Area     -            -        position, size is stored in Channel Area TOC
//   Area TOC-2     -            -        position & size is stored in Master TOC
// Multi Channel
//   Area TOC-1     -            -        position & size is stored in Master TOC
//   Track Area     -            -        position, size is stored in Channel Area TOC
//   Area TOC-2     -            -        position & size is stored in Master TOC
//
//

```

Numbers are stored in big endian format.

### Block Addressing (LSN) ###

A ScarletBook disk is broken up into a number of 2048-byte blocks which we call frames. The way ScarletBook addresses a block is to use its LSN or "logical sector number." ScarletBook numbers the blocks from 0 on.

## Master TOC ##

For the lastest detailed scarletbook specifications check the following [c header file](http://code.google.com/p/sacd-ripper/source/browse/trunk/libs/libsacd/scarletbook.h).