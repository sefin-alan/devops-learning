# Level 12-13: The password is stored in the file data.txt, which is a **hexdump** of a file that has been repeatedly compressed

## Password
FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
## Method
Reverse the hexdump file with the XXD program
```
mktemp -d
cp data.txt /tmp/tmp.9mXQpTeqeO
cd /tmp/tmp.9mXQpTeqeO
file data.txt
mv data data.gz
gunzip data.gz
file data
mv data data.bz2
bzip2 -d data.bz2
file data
mv data data.gz
gunzip data.gz
file data
mv data data.tar
tar -xf data.tar
file data5.bin
mv data5.bin data5.tar
tar -xf data5.tar
file data6.bin
mv data6.bin data6.tar
tar -xf data6.tar
mv data6.bin data6.bz2
bzip2 -d data6.bz2
file data6
mv data6 data6.tar
tar -xf data6.tar
file data8.bin
mv data8.bin data8.gz
gunzip data8.gz
file data8
cat data8
```

**What I learned:** Files have to be renamed to reflect their filetype before extracting them with that filetype's extraction option i.e. gzip -d extracts '.gz.' file. When extracting gzip and bzip2 the file is **replaced** by the extracted output, but with tar, the contents are extracted **alongside** the original archive, so a new file/s will appear next to it. A **hexdump** is a representation of a file's binary data displayed in hexadecimal format that is used to inspect raw file content.