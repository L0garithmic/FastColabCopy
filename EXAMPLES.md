## More Examples
```
#load stuff
!pip install -q ipython-autotime
%load_ext autotime
!wget -q https://raw.githubusercontent.com/L0garithmic/fastcolabcopy/main/fastcopy.py
import fastcopy

#mount drive
from google.colab import drive
drive.mount('/gdrive', force_remount=False)
import os

#list drives
print('\n''--Available Drives--')
!ls /gdrive/Shareddrives
print('\n')

```
If you want to see copy execution time
```
!pip install -q ipython-autotime
%load_ext autotime
```


Credit to [ikonikon](https://github.com/ikonikon/fast-copy) for the base multi-threading code.   
Thanks to [@Ostokhoon](https://www.freelancer.com/u/Ostokhoon) for the -d, -s, -r and folder hierarchy functionality.
