## More Examples
#### Mount Google Drive, install autotime/fastcolabcopy, list shared drives
```py
#@markdown <center><h5>Mount/Prerequisites</h5></center>

#load timer and fastcopy
print('\n''--Installing Prerequisites--')
!pip install -q ipython-autotime
%load_ext autotime
!wget -q https://raw.githubusercontent.com/L0garithmic/fastcolabcopy/main/fastcopy.py
import fastcopy

#mount drive
print('\n''--Mounting Drive--')
from google.colab import drive
drive.mount('/gdrive', force_remount=False)
import os

#list drives
print('\n''--Available Drives--')
!ls /gdrive/Shareddrives
print('\n')
```

Mirror drives, input for source and dest. Splits the process up.
```py
sourcedrive = "LargeFiles4" #@param {type:"string"}
destdrive = "LargeFilesShare" #@param {type:"string"}

print('\n''--Small Files--')
!python fastcopy.py "/gdrive/Shareddrives/$sourcedrive/". "/gdrive/Shareddrives/$destdrive" --thread 20 --size-limit 400mb
print('\n''--Medium Files--')
!python fastcopy.py "/gdrive/Shareddrives/$sourcedrive/". "/gdrive/Shareddrives/$destdrive" --thread 3 --size-limit 600mb
print('\n''--Large Files--')
!rsync -r -h --info=progress2 --update "/gdrive/Shareddrives/$sourcedrive/". "/gdrive/Shareddrives/$destdrive" --delete
```


## Off Topic Snippets

#### Delete junk sys files
Did you know you can delete large, unnecessary folders in the colab root 
(Sadly, This does not appear to add to available space)
```py
#cleanup installation
print('--Removing Junk--')

!rm -rf usr/local/lib/python2.7
!rm -rf usr/local/cuda-*
!rm -rf tensorflow-2.0.0
!rm -rf opt/nvidia
```

#### Export file names to txt file (recursive), ignoring errors.
```py
import os
import glob

#Replace DIRNAME with folder you'd like to make file list of. 
#Replace DIRNAME with * if you want all directories

for filename in glob.iglob('DIRNAME/**/*', recursive=True):
    try:
        dd = os.path.abspath(filename), os.stat(filename).st_uid  
        print(dd, file=open("tools.txt", "a"))
    except:
        pass # do nothing on exception
```

#### Clears the display in colab. Equivalent to CLS on batch file.
```py
from IPython.display import clear_output; clear_output()
```
