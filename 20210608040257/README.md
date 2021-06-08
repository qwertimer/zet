# Working with Tar files

An interesting side bit i found out today is that tar in itself is not a compression program. It is designed to join multiple files into one large file. The flags that are provided actually pipe the output of the tar join to underlying compression utilities such as gzip or bzip2. This is due to the origirnal design of tar being for tape archives and additional modification used the linux philosophy of being able to pipe stdout to other locations. Tar is an interesting tool that has the ability to uncompress some file formats it however does not have the ability to unzip zip files.

