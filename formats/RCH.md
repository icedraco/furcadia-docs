---
classification: public
---

# RCH - Furcadia Container / Archive
## Overview
RCH files are normally used to upload and download dreams. They serve as a
container for the multiple files in the dream package and allow each file to be
passed through different algorithms such as XOR255+LZW, XOR255 or BZip2.

## Format
### General Format
| Offset | Size | Type     | Description                              |
| -----: | ---: | -------- | ---------------------------------------- |
|      0 |    4 | char\[4] | `FR01` - RCH magic number                |
|      4 |    4 | uint32   | Container version                        |
|      8 |    4 | uint32   | Creation timestamp (always `0` - unused) |
|     12 |    4 | u\|int32 | Reserved (`0`)                           |
|     16 |    4 | u\|int32 | Reserved (`0`)                           |
|     20 |    4 | u\|int32 | Reserved (`0`)                           |
|     24 |    4 | u\|int32 | Reserved (`0`)                           |
|     28 |    * | File\[]  | File blocks                              |

### File Block
| Offset |  Size | Type         | Description                                                      |
| -----: | ----: | :----------- | ---------------------------------------------------------------- |
|      0 |     2 | char\[2]     | `FZ` - File Block magic number                                   |
|      2 |    40 | char\[40]    | Filename (NULL-padded)                                           |
|     42 |     4 | uint32       | File version (`1`)                                               |
|     46 |     4 | uint32       | Timestamp (always `0` - unused)                                  |
|     50 |     4 | uint32       | Payload size                                                     |
|     54 |     4 | uint32       | CRC32 checksum of the payload                                    |
|     58 |     4 | uint32       | Compression algorithm<br>(0 = XOR255+LZW, 1 = XOR255, 2 = BZip2) |
|     62 | pSize | byte\[pSize] | Payload                                                          |

## Tools
* [Ezoa's Resource Content Handler Archiver](https://ezoa.page/projects/ERCHA/) (ERCHA) - RCH packer/unpacker
	* [GitHub Project](https://github.com/ezoa-page/ERCHA)

## Example Code (Ezoa)
```python
import struct
import os
import zlib
import bz2
import argparse
import sys

RCH_MAGIC = b'FR01'
BLOCK_MAGIC = b'FZ'
COMPRESSION_BZIP2 = 2

def pack_rch(output_filename, input_files, compression_level=9):
    """Packs multiple files into a single RCH archive with BZip2 compression."""
    with open(output_filename, 'wb') as rch_file:
        # Write RCH header
        rch_file.write(RCH_MAGIC)
        rch_file.write(struct.pack('<I', 1))  # Container version
        rch_file.write(struct.pack('<I', 0))  # Creation timestamp (unused)
        rch_file.write(b'\x00' * 16)          # Reserved

        # Write file blocks
        for input_file in input_files:
            with open(input_file, 'rb') as f:
                file_data = f.read()
                filename = os.path.basename(input_file).encode('utf-8')

                # Compress the file data using BZip2 with specified compression level
                compressor = bz2.BZ2Compressor(compression_level)
                compressed_data = compressor.compress(file_data) + compressor.flush()
                compressed_size = len(compressed_data)
                crc32 = zlib.crc32(file_data) & 0xFFFFFFFF  # CRC32 checksum of the original data
                compression_algo = COMPRESSION_BZIP2

                # Write block header
                rch_file.write(BLOCK_MAGIC)
                rch_file.write(filename.ljust(40, b'\x00'))  # Filename, null-padded
                rch_file.write(struct.pack('<I', 1))         # Version
                rch_file.write(struct.pack('<I', 0))         # Timestamp (unused)
                rch_file.write(struct.pack('<I', compressed_size))  # Filesize of compressed data
                rch_file.write(struct.pack('<I', crc32))     # CRC32 checksum of original data
                rch_file.write(struct.pack('<I', compression_algo))  # Compression algorithm

                # Write compressed file data
                rch_file.write(compressed_data)

        print(f"Packed files into {output_filename}")

def unpack_rch(rch_filename, output_directory):
    """Unpacks an RCH archive into the specified directory."""
    with open(rch_filename, 'rb') as rch_file:
        # Read and validate RCH header
        if rch_file.read(4) != RCH_MAGIC:
            raise ValueError("Invalid RCH file format")

        container_version = struct.unpack('<I', rch_file.read(4))[0]
        creation_timestamp = struct.unpack('<I', rch_file.read(4))[0]
        reserved = rch_file.read(16)

        # Read file blocks
        while True:
            block_magic = rch_file.read(2)
            if not block_magic:
                break  # EOF

            if block_magic != BLOCK_MAGIC:
                raise ValueError("Invalid block magic number")

            filename = rch_file.read(40).split(b'\x00', 1)[0].decode('utf-8')
            version = struct.unpack('<I', rch_file.read(4))[0]
            timestamp = struct.unpack('<I', rch_file.read(4))[0]
            filesize = struct.unpack('<I', rch_file.read(4))[0]
            crc32_stored = struct.unpack('<I', rch_file.read(4))[0]
            compression_algo = struct.unpack('<I', rch_file.read(4))[0]
            
            file_data = rch_file.read(filesize)
            
            # Decompress data if necessary
            if compression_algo == COMPRESSION_BZIP2:
                decompressed_data = bz2.decompress(file_data)
            else:
                decompressed_data = file_data

            # CRC check to ensure integrity of the decompressed data
            crc32_computed = zlib.crc32(decompressed_data) & 0xFFFFFFFF
            if crc32_computed != crc32_stored:
                raise ValueError(f"CRC32 checksum does not match for {filename}: "
                                 f"expected {crc32_stored}, got {crc32_computed}")

            output_path = os.path.join(output_directory, filename)
            os.makedirs(output_directory, exist_ok=True)
            with open(output_path, 'wb') as out_file:
                out_file.write(decompressed_data)
                print(f"Extracted {filename} to {output_path}")

def main():
    parser = argparse.ArgumentParser(description='RCH File Packer and Unpacker with BZip2 Compression and CRC Check')
    subparsers = parser.add_subparsers(dest='command')

    # Sub-parser for the pack command
    pack_parser = subparsers.add_parser('pack', help='Pack files into an RCH archive')
    pack_parser.add_argument('output', help='Output RCH file name')
    pack_parser.add_argument('input_files', nargs='+', help='List of input files to pack')
    pack_parser.add_argument('--compression', type=int, default=9, help='BZip2 compression level (1-9)')

    # Sub-parser for the unpack command
    unpack_parser = subparsers.add_parser('unpack', help='Unpack files from an RCH archive')
    unpack_parser.add_argument('rch_file', help='RCH file to unpack')
    unpack_parser.add_argument('output_dir', help='Directory to extract files to')

    args = parser.parse_args()

    if args.command == 'pack':
        pack_rch(args.output, args.input_files, compression_level=args.compression)
    elif args.command == 'unpack':
        unpack_rch(args.rch_file, args.output_dir)
    else:
        parser.print_help()
        sys.exit(1)

if __name__ == '__main__':
    main()
```
