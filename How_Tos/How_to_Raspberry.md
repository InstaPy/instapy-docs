# Tutorial for Raspberry Pi3B+: Install InstaPy with Python 3.x

## Basic Raspbian Configuration
NOTE: _If you add an empty file named ssh to the boot directory, ssh will be enabled when you first start your RPi (more info on the official website - section 3 - [here](https://www.raspberrypi.org/documentation/remote-access/ssh/)). If you do this, you can connect your RPi via ethernet, ssh in (once you have your ip) and skip right to the update step below (step 7). If you do not want to do this, follow the initial setup instructions to connect peripherals below._

1. connect rpi3 to monitor via HDMI
2. connect internet via cat5
3. insert usb for wireless keyboard and mouse (if using)
4. plug in rpi3 with sd card installed with Raspbian Stretch or Buster with desktop
5. select country & configure Raspbian
6. open terminal --> ```sudo raspi-config``` -->interfacing options --> SSH -->enable (allows ssh connection from MacBook); then navigate to VNC --> enable (allows GUI access)
7. ```sudo apt-get update -y && sudo apt-get upgrade -y```

## Install Firefox
```sudo apt-get install firefox-esr```

## Install GeckoDriver 
The latest versions of InstaPy automatically install geckodriver. For RaspberryPi you need ARM support in your geckodriver, which is why you'll need to download a specific version (0.23.0) of the driver here:

_GeckoDriver releases can be found in:_ https://github.com/mozilla/geckodriver/releases. The latest ARM release as of 2019-08-16 is v0.23.

Follow these steps:

1. ```wget https://github.com/mozilla/geckodriver/releases/download/v0.23.0/geckodriver-v0.23.0-arm7hf.tar.gz```
2. ```tar -xvzf geckodriver-v*```
3. ```chmod +x geckodriver```
4. ```sudo cp geckodriver /usr/local/bin/``` 
5. Ensure that /usr/local/bin is in your shell PATH.

## Install InstaPy

1. ```sudo apt-get install python3-pip```
2. ```python3 -m pip install --user instapy```
3. ```sudo reboot``` (optional)
4. ```nano quickstart.py```
5. Edit quickstart file with your credentials/ add functions you want to use, documentation in the [Readme](https://github.com/timgrossmann/InstaPy/blob/master/README.md)
6. ```python3 quickstart.py```

## Update InstaPy

```pip3 install instapy --upgrade --user```


## Finishing up the Firefox installation
_Encountered some errors when trying to run the quickstart.py and ran the next 3 commands (all may not be necessary)_
1. ```sudo pip3 install future```
2. ```sudo apt-get install xvfb```
3. ```sudo pip3 install pyvirtualdisplay```
4. ```sudo reboot``` (may not be required, but no harm)

_Assuming you've modified quickstart.py to your liking and added your Instagram login to quickstart.py_

5. ```sudo xvfb-run python3 quickstart.py```

_I installed TMUX to help run this headless, so that I can disconnect from the session and have the program continue to run on the rpi3_

6. ```sudo apt-get install tmux``` (more info found here: https://github.com/tmux/tmux)
