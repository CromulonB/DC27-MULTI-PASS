# Software Update 2

MultiPassFix2.img is the latest firmware and the last I'll be releasing here. This firmware brings the badge back in line with the other devices on the badge.team platform and future updates can be installed with the OTA update functionality on the badge itself. The app installer is also functional now. You can still download apps from the [repo](https://badge.team/) manually and install them with [MPFSHELL](https://github.com/wendlers/mpfshell) if you want to but the installer on the badge obviously has less steps. The installation of this firmware is the same as the last one just use the newest .img file.

## Installation

The directions below are how to flash the new image using [esptool](https://github.com/espressif/esptool). It is a python tool to communicate with ESP chips. If you prefer a GUI then [NodeMCU PyFlasher](https://github.com/marcelstoer/nodemcu-pyflasher) is super easy. With both tools you will need to power cycle or press the reset button once the write is complete.

For esptool you will need [either Python 2.7 or Python 3.4 or newer](https://www.python.org/downloads/) installed on your system.

The latest stable esptool.py release can be installed from [pypi](http://pypi.python.org/pypi/esptool) via pip:

```
$ pip install esptool
```

With some Python installations this may not work and you'll receive an error, try `python -m pip install esptool` or `pip2 install esptool`.

After installing, you will have `esptool.py` installed into the default Python executables directory and you should be able to run it with the command `esptool.py`.

Once esptool is installed simply download MultiPassFix2.img and run the command to write the image to your badge.
```
sudo  python ~/.local/lib/python2.7/site-packages/esptool.py --port /dev/ttyUSB0 --baud 921600 write_flash 0x00000 MultiPassFix2.img
```

After the write completes the badge will restart and it will go through a "Factory test" process. Make sure to leave the badge plugged into USB for the duration of this process. During this tests it will ask you to press each input in order to confifure the baselines. It will continue to test and configure the badge and completes when the screen shows some random lines on top. Just press the reset button on the rear of the badge and it will start working correctly.
