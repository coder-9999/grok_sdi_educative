## Disk Related concepts ##
If you know about structs in C, when you define an struct you can always know in advance how many bytes it will take and even the alignment of each field. This allows to read and write those structs directly from and to disk.
These structures are the origin of the concept of file.

In order to understand alignment, it's important to differentiate 2 things:
  - **(SECTOR)**  -> is a physical spot on a formatted disk that holds information. Normally, it's 512 bytes.
  - **(BLOCK)** -> a group of sectors that the operating system can address (point to). It is usually 1, 2, 4, 8, 16 sectors or another power of 2 (but the same amount for all blocks in the disk).

**So why are there blocks. Why doesn't the operating system just point straight to the sectors?**
Because there are limits to the number of blocks, or drive addresses, that an operating system can address. So, A block is the smallest unit of data that an operating system can either write to a file or read from a file.
Thus, disk are divided in blocks, which are assigned to files to hold their contents. When a file is created with size 0, it doesn't have any block. When the first byte is written, the first block is assigned. When the second byte is written, no new block is assigned because the first block should still have a lot of space available (say 4,095 bytes). When byte number 4,096 is written, it still fits in the first block, but when byte 4,097 is written, a second block is assigned to the file and the new byte is written in its first position. And so on. On average, half of a block is always wasted per each file, specifically in its last block.

**What exactly is a page?**
Pages are used by some operating systems instead of blocks. A page is basically a virtual block. And, pages have a fixed size – 4K and 2K are the most commonly used sizes. So, the two key points to remember about pages is that they are virtual blocks and they have fixed sizes.

**Why pages may be used instead of blocks??**
Pages are used because they make processing easier when there are many storage devices, because each device may support a different block size. With pages the operating system can deal with just a fixed size page, rather than try to figure out how to deal with blocks that are all different sizes. So, pages act as sort of a middleman between operating systems and hardware drivers, which translate the pages to the appropriate blocks. But, both pages and blocks are used as a unit of data storage.

## File Formats ##
A file format is a standard way that information is encoded for storage in disk. It specifies how bits are used to encode information in a digital storage medium and how they should be interpreted when being read. If you want to create a format, it’s easy. Open a file handle and start writing bits to the disk. When you are done writing bits, stop. If you would like to be able to read them back, document what each of the bits mean.

There are existing text file formats like txt, csv, xml and other binary file formats. When the existing file formats do not meets the requirements of application forr minium I/O and seeks, application go for their own file formats. This is what most storage engines also do.

**Parquet** is also an binary encoding/binary file format constructed to optimize for storage and querying. Here, row groups maps to disk blocks and column chunks to an array of OS pages.
Some great documentation can be found here- http://cloudsqale.com/2020/05/29/how-parquet-files-are-written-row-groups-pages-required-memory-and-flush-operations/
and https://medium.com/swlh/insights-into-parquet-storage-ac7e46b94ffe
parquet vs other file formats like avro, thrift, proto ->https://dzone.com/articles/understanding-how-parquet
