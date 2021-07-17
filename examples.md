## More Examples
```
#@markdown <center><h5>Mount/Prerequisites</h5></center>

#changing dir and clearing console to remove ugly /
%cd ..
from IPython.display import clear_output; clear_output()

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

This does not appear to add to available space, but it lets you delete large, unnecessary folders in the colab root   
I am unsure if it is useless, so I run it (takes 12 seconds). I put it after `import fastcopy` and before '#mount drive'
```
#cleanup installation
print('--Removing Junk--')

!rm -rf usr/local/lib/python2.7
!rm -rf usr/local/cuda-*
!rm -rf tensorflow-2.0.0
!rm -rf opt/nvidia
```
