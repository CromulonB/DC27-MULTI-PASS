# First Software Update

This firmware should fix the touch issues. The app installer is still not functional on this version but you can download apps from the [repo](https://badge.team/) manually and install them with [MPFSHELL](https://github.com/wendlers/mpfshell) if you want to play around.

The easiest way to flash the new image is with [esptool](https://github.com/espressif/esptool). It is a python tool to communicate with ESP chips.

You will need [either Python 2.7 or Python 3.4 or newer](https://www.python.org/downloads/) installed on your system.

The latest stable esptool.py release can be installed from [pypi](http://pypi.python.org/pypi/esptool) via pip:

```
$ pip install esptool
```

With some Python installations this may not work and you'll receive an error, try `python -m pip install esptool` or `pip2 install esptool`.

After installing, you will have `esptool.py` installed into the default Python executables directory and you should be able to run it with the command `esptool.py`.

Once esptool is installed simply download MultiPassFix1.img and run the command to write the image to your badge.
```
sudo  python ~/.local/lib/python2.7/site-packages/esptool.py --port /dev/ttyUSB0 --baud 921600 write_flash 0x00000 MultiPassFix1.img
```

After the write completes the badge will restart and it will go through a "Factory test" process. During this process it will ask you to press each input in order to confifure the baselines. It will continue to test and configure the badge. When it completes the screen will show some random lines on top. Just press the reset button on the rear of the badge and it will start working correctly.
