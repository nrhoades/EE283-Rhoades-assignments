#Lab 2
##File processing in Python
file exists?

```
import os
os.path.isfile('./file')
```
is file is a directory?

```
import os
os.path.isdir('./dir')
```
remove (delete) a file?

```
import os
os.remove('./file')
```
get the size of a file?

```
import os
statinfo = os.stat('file')
statinfo.st_size
```
all the file names matching a pattern?

```
import glob
glob.glob('pattern')
```
all the file names matching a pattern recursively?

```
import glob
glob.glob(/*/'pattern')
```
get an iterator to all files matching a pattern, as opposed to returning a potentially huge list?

```
import glob
glob.iglob('pattern')
```
open gzip-compressed files for reading and for writing?

_reading_

```
import gzip
with gzip.open('file.txt.gz', 'rb') as f:
    file_content = f.read()
```
_writing_

```
import gzip
with gzip.open('file.txt.gz', 'wb') as f:
    file_content = f.write()
```


##In R
file exists?

```
file.exists("file")
```
if file is a directory?

```
dir.exists("dir")
```

remove (delete) a file?

```
file.remove("file")
```
get the size of a file?

```
file.info("file")
```

file names matching a pattern?

```
list.files(pattern="pattern_you_want")
```

all the file names matching a pattern recursively?

```
list.files(pattern="pattern_you_want", recursive=TRUE)
```

open gzip-compressed files for reading and for writing?

```
library(R.utils)
gunzip("file.gz")
```

##Python

```{py}
import glob
import os.path
output=[]
for file in glob.glob('./lab2data/*/*'):
	base=os.path.basename(file)
	rawfile=os.path.splitext(base)[0]
	raw2=rawfile.split(".",1)[1]
	for i in raw2:
		output.append(raw2)
myset = set(output)
my_list = ['outfile.' + x + '.out' for x in myset]
print(my_list)

```

##R

```
library(tidyverse)
files <- list.files(recursive = TRUE, full.names = FALSE)
files <- files %>%
	gsub(., pattern = "data/datafile.", replacement = "") %>%
	gsub(., pattern = "output/outfile.", replacement = '') %>%
	gsub(., pattern = ".txt", replacement = "") %>%
	gsub(., pattern = ".out", replacement = "") %>%
unique_files <- unique(files)
unique_files <- paste0("outfile.", unique_files, ".out")
```
