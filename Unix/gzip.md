Gzip
============

File compression and decompression tool. The g stands for gratis.

Options
----------

### -1, --fast, -2, -3, -4, -5, -6, -7, -8 -9, --best
  + Change the compression level used.
  + -1 option is optimized for speed and the -9 is optimized for best compression.
  + The default compression level is 6.

### -c, --stdout, --to-stdout
  + Specifies that output will go to the standard output stream, leaving files intact.

### -d, --decompress, --uncompress
  + Select decompression rather than compression.

### -f, --force
  + Force Mode
  + Allows files with multiple links, symbolic links to regular files, overwriting of pre-existing files, reading from or writing to a terminal.
  + When combined with the -c option, allowing non-compressed data to pass through unchanged.

### -k, --keep
  + Keep input files during compression or decompression.

### -l, --list
  + Displays information about the file's compressed and uncompressed size, ratio, uncompressed name.
  + With the -v option, it also displays the compression method, CRC, date and time embedded in the file.

### -N, --name
  + Causes the stored filename in the input file to be used as the output file.

### -t, --test
  + Test compressed files for integrity.

Sample Commands
---------------

`gzip file`: Compress 'file' with gzip

`gzip -d file.gz`: Decompress file.gz
