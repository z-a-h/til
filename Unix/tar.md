Tar
==================

Tar is a software utility for creating and manipulating streaming many file into an archive file for distribution or backup. The name is derived from **T**ape **AR**chive

Flags
-----
### -c
  + Create a new archive containing the specified items.

### -r
  + Like -c, but new entries are appended to the archive.
  + Only works on uncompressed archives stored in regular files.
  + The -f option is required.

### -t
  + List archive contents to stdout.

### -u
  + Like -r, but new entries are added only if they have a modification date newer than the corresponding entry in the archive.
  + Only works on uncompressed archives stored in regular files.
  + The -f option is required.

### -x
  + Extract to disk from the archive.
  + If a file with the same name appears more than once in the archive, each copy will be extracted, with later copies overwriting earlier copies.


Sample Commands
----------------

`tar cf file.tar files`: Create a tar 'file.tar' with 'files'

`tar xf file.tar`: Extract files from 'file.tar'

`tar czf file.tar.gz files`: Create tar with gzip compression

`tar xzf file.tar.gz`: Extract files from file.tar.gz
