### RefPack/QFS Resources

Resources for those interested in the RefPack/QFS compression algorithm used in many EA games. Also maintains links to known implementations of the compression for easy reference.

#### About

RefPack is a compression algorithm based on the LZ77/LZSS compression written by Frank Barchard for use in games made by EA[^refabout]. It can be found in games as early as FIFA International Soccer (1993)[^segaretro]. The algorithm uses different encoding schemes based on the length and position of the data that's being compressed, which allows it to achieve a higher compression ratio compared to other LZ-based algorithms.

The name QFS comes from a file format used in old Need for Speed games in which this algorithm was used. However, the actual name of the algorithm is RefPack[^refabout].

#### Resources

[Niotso Wiki](http://wiki.niotso.org/RefPack): Generic information on the compression algorithm.

[Source Code](https://github.com/electronicarts/CnC_Generals_Zero_Hour/blob/main/Generals/Code/Libraries/Source/Compression/EAC): Official code released by EA as a part of the public release of the source code of Command and Conquer: Generals - Zero Hour.

[Explanation of LZ77/LZSS Compression](https://go-compression.github.io/algorithms/lzss/): RefPack is based on the LZ77 compression algorithm.

[Explanation of zlib](https://www.euccas.me/zlib/): zlib is a popular compression library and a lot of the techniques employed in zlib are also utilized in RefPack compression code.

#### Implementations

List of known implementations of the compression algorithm organized by language and [format](https://github.com/lingeringwillx/RefPack-QFS-Resources/blob/main/FORMATS.md) and for easy reference. A lot of those are rewrites of the same code in another programming language. The quality varies from one implementation to another.

| Language/Format | EAC | EAC (w/ 32-bit size) | Maxis | Fusion |
|-|:-:|:-:|:-:|:-:|
| C | [Denis Auroux](https://math.mit.edu/~auroux/software/fshtool.zip) ||| [aluigi](https://github.com/LittleBigBug/QuickBMS/blob/master/src/compression/refpack.c)[^decompression] |
| C# | [0xC0000054](https://github.com/0xC0000054/DBPFSharp/blob/main/src/DBPFSharp/QfsCompression.cs)<br>[Venomalia](https://github.com/Venomalia/AuroraLib.Compression/blob/main/src/AuroraLib.Compression/Algorithms/RefPack.cs)<br>[rivit](https://github.com/Killeroo/QFS.net/blob/master/QFS_rivit.cs) | [Venomalia](https://github.com/Venomalia/AuroraLib.Compression/blob/main/src/AuroraLib.Compression/Algorithms/RefPack.cs)<br>[GlitcherOG](https://github.com/GlitcherOG/SSX-Collection-Multitool/blob/main/FileHandlers/RefpackHandler.cs)<br>[pljones & Tiger](https://sourceforge.net/p/s3pi/git/ci/master/tree/s3pi/Package/Compression.cs)<br>[gibbed](https://github.com/gibbed/Gibbed.RefPack) | [0xC0000054](https://github.com/0xC0000054/DBPFSharp/blob/main/src/DBPFSharp/QfsCompression.cs)<br>[Venomalia](https://github.com/Venomalia/AuroraLib.Compression/blob/main/src/AuroraLib.Compression/Algorithms/RefPack.cs)<br>[Afr0](https://github.com/riperiperi/FreeSO/blob/master/Other/tools/SimsLib/SimsLib/FAR3/Decompresser.cs)<br>[ambertation](https://github.com/luki122/simpe/blob/master/fullsimpe/SimPe%20Packages/PackedFile.cs) | [AcK77](https://github.com/AcK77/TTGames-Explorer-Rebirth/blob/main/src/TTGamesExplorerRebirthLib/Compression/UnRefpack.cs)[^decompression] |
| C++ || [EA Games](https://github.com/electronicarts/CnC_Generals_Zero_Hour/tree/main/Generals/Code/Libraries/Source/Compression/EAC)<br>[OmniBlade](https://github.com/TheAssemblyArmada/Thyme/blob/develop/src/game/common/compression/refpack.cpp)<br>[KUDr](https://github.com/MicaelJarniac/RefPack-Tool)<br>[J.M. Pescado](https://gist.github.com/uyjulian/bd24b98a4c97b775c9ab) | [benrg](http://www.moreawesomethanyou.com/smf/index.php/topic,8279.0.html) ||
| Go | [marcboudreau](https://github.com/marcboudreau/godbpf/blob/master/qfs/qfs.go) ||||
| Java | [emd4600](https://github.com/emd4600/SporeModder-FX/blob/master/src/sporemodder/file/dbpf/RefPackCompression.java) || [java_dwarf](https://github.com/memo33/jDBPFX/blob/master/src/jdbpfx/util/DBPFPackager.java) ||
| JavaScript | [sebamarynissen](https://github.com/sebamarynissen/qfs-compression) ||||
| Kotlin || [DarkAtra](https://github.com/DarkAtra/bfme2-modding-utils/blob/main/refpack/src/main/kotlin/de/darkatra/bfme2/refpack/RefPackInputStream.kt)[^decompression] |||
| Pascal || [Banshee](https://github.com/forcecore/ZHModLauncher/blob/6d0db2847ed08c6b81229e61103bf7ac8990ce40/src/BIG_File.pas)[^decompression] |||
| PHP ||| [Delphy](https://modthesims.info/wiki.php?title=DBPF_Compression#Example_Code)[^decompression] ||
| Python ||| [lingeringwillx](https://github.com/lingeringwillx/sims2lib/blob/main/dbpf.py)[^bindings]<br>[lah7](https://github.com/lah7/sims2-4k-ui-patch/blob/master/sims2patcher/qfs.py) | [yukinogatari](https://github.com/yukinogatari/Reverse-Engineering/blob/master/Lego/fib_dec.py)[^decompression] |
| Rust || [actioninja](https://github.com/actioninja/refpack-rs) | [actioninja](https://github.com/actioninja/refpack-rs) ||
| Scala ||| [memo33](https://github.com/memo33/scdbpf/blob/master/src/main/scala/scdbpf/internal/QfsCompression.scala) ||

[^refabout]: [C&C Generals source code: refabout.cpp](https://github.com/electronicarts/CnC_Generals_Zero_Hour/blob/main/Generals/Code/Libraries/Source/Compression/EAC/refabout.cpp)

[^segaretro]: [Sega Retro](https://segaretro.org/RefPack_compression)

[^decompression]: Decompression code only

[^bindings]: C Bindings
