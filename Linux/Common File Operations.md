Some common file operations that are very useful.

    ls -lh file.name

    Returns the file permissions, owner, group and other permissions (octal format), number of hard links pointing to the file, the file owner, group owner, file size, last modified date, and file name.

    state file.name

    Stat returns file name, file size, the size of the IO (filesystem) block, file type, the inodeid, links, file permissions, UID, GID, the access timestamp, the modification timestamp, the change timestamp, and the original creation date of the file.

    If you don't need all that information you can pare it down to what you need by passing flags to the file such as below.
    
    stat -c "%a %A %U:%G %n" /path/to/folder/or/file

