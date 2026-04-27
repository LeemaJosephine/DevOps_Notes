# Day 5 - Logging on to the systems

**Archiving**
Combining multiple files/folders into a single file

**Windows Comparison**
|Linux |Windows|
|------|-------|
|.tar| ZIP file|
|.tar.gz |Compressed zip file|

**Archiving vs Compression**

Archiving: Combining files

Compression: Reducing the size

**Examples:**

.tar (tape archive) -> archive only
.tar.gz -> archive + compressed
.tar.bz2 -> Stronger compression

Basic Syntax:
tar [options] archive_name files_or_folder
|Option| Meaning|
|------|--------|
|-c|Create archive|
|-x|extract archive|
|-v |Verbose (show files)|
|-f |filename|
|-z |gzip compression|
|-j |bzip2 compression|
|-C |Extract to directory|
