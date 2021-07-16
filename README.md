![made-with-python](https://img.shields.io/badge/Made%20with-Python3-brightgreen)

<!-- LOGO -->
<br />
<p align="center">
  <img src="https://user-images.githubusercontent.com/1237743/125965643-35d4eefd-963f-475b-9b36-c95564329e03.png" alt="Logo" width="140" height="110">
  <h3 align="center">FastColabCopy</h3>

  <p align="center">
    Python3 script transfer files in Google Colab 10-50x faster.
    <br />
    </p>
</p>

## About The Project
FastColabCopy is a Python script for parallel (multi-threading) copying of files between two locations. Currently developed for Google-Drive to Google-Colab transfers where copying numerous small files can take a long time. This script achieves 10-50x speed improvements.

My last test. 52 PDF files (540mb total). `RSync|1:46` | `FastColabCopy|0:04` so.. almost 27x faster


## Getting Started
To copy files on Colab, you will need to have google drive mounted and FastColabCopy imported 

### Mounting
Skipping the fact that I'd assume you already know how to do this. Here is the code to mount.
```
from google.colab import drive
drive.mount('/gdrive', force_remount=False)
import os
```

### Importing
Import from GitHub.   
```
!wget https://raw.githubusercontent.com/L0garithmic/fastcolabcopy/main/fastcopy.py
import fastcopy
```

Import from Google Drive
```
!cp /gdrive/MyDrive/fastcopy.py .
import fastcopy
```


## Usage
```sh
usage: fast-copy.py [-h HELP] source destination [-d DELETE] [-s SYNC] [-r REPLACE ]

optional arguments:
  -h, --help            show this help message and exit
  source                the drive you are copying from
  destination           the drive you are copying too
  -d --delete           delete the source files after copy
  -s --sync             remove files from destination if they do not exist in source
  -r --replace          replace files if they exist
```
The `source` and `destination` fields are required. Everything else is optional.

## Example
```
from google.colab import drive
drive.mount('/gdrive', force_remount=False)
import os
!wget -q https://raw.githubusercontent.com/L0garithmic/fastcolabcopy/main/fastcopy.py
import fastcopy
!python fastcopy.py /gdrive/Shareddrives/SourceDrive/. /gdrive/Shareddrives/DestDrive --sync
```
If you want to see copy execution time
```
!pip install -q ipython-autotime
%load_ext autotime
```


Credit to [ikonikon](https://github.com/ikonikon/fast-copy) for the base multi-threading code.   
Thanks to [@Ostokhoon](https://www.freelancer.com/u/Ostokhoon) for the -d, -s, -r and folder hierarchy functionality.
