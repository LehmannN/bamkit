# Installation
To install bamkit from the source code, you need to first download/compile 
htslib, setup the corresponding environmental variables,
and then compile the source code of bamkit.


## Install htslib
Download htslib [(license)](https://github.com/samtools/htslib/blob/develop/LICENSE)
from (http://www.htslib.org/) with version 1.5 or higher.
Choose a directory for installation and set the environment variable `HTSLIB` for that.
For example, for Unix platforms, do the following:
```
export HTSLIB="/directory/to/your/htslib/install"
```
Use the following to build `libhts.a`:
```
autoheader
autoconf
./configure --disable-bz2 --disable-lzma --disable-gcs --disable-s3 --enable-libcurl=no --prefix=$HTSLIB
make
make install
```

## Compile bamkit
The compilation of `bamkit` requires `automake` and `autoconf` packages.
If they have not been installed, on linux platform, do the following:
```
sudo apt-get install autoconf
sudo apt-get install automake
```

bamkit might also requires other libraries, such as `libbz`, depending on
your system. Install them if you encounter errors when compiling.

After that run the script `build.sh`, which will generate the executable file `src/src/bamkit`.


# Usage

The usage of `bamkit` is:
```
./bamkit <count|strand> <input.bam>
```

When the first parameter is set as count, `bamkit` shall do a statistic about the
number of reads and basepairs aligned in the given bam file, and report the results
to the standard output.
When the first parameter is set as strand, `bamkit` shall check the strandness of the
given bam file and report the results to the standard output.
