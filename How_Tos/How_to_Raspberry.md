# Tutorial for Raspberry Pi3b: Install InstaPy with Python 3.x

## Basic Raspbian Configuration
NOTE: _If you add an empty file named ssh to the boot directory, ssh will be enabled when you first start your RPi (more info on the official website - section 3 - [here](https://www.raspberrypi.org/documentation/remote-access/ssh/)). If you do this, you can connect your RPi via ethernet, ssh in (once you have your ip) and skip right to the update step below (step 7). If you do not want to do this, follow the initial setup instructions to connect peripherals below._

1. connect rpi3 to monitor via HDMI
2. connect internet via cat5
3. insert usb for wireless keyboard and mouse (if using)
4. plug in rpi3 with sd card installed with Raspbian Stretch with desktop
5. select country & configure Raspbian
6. open terminal --> ```sudo raspi-config``` -->interfacing options --> SSH -->enable (allows ssh connection from MacBook); then navigate to VNC --> enable (allows GUI access)
7. ```sudo apt-get update && sudo apt-get upgrade```

## Install InstaPy

1. ```sudo apt-get install chromium-browser```
1. ```python3 -m pip install --user instapy```
1. ```python3 -m pip uninstall instapy-chromedriver```
1. ```python3 -m pip install instapy-chromedriver==2.36.post0```
1. ```mkdir InstaPy```
1. ```cd InstaPy```
1. ```nano quickstart.py```
1. Edit quickstart file with your credentials/ add functions you want to use, documentation in the [Readme](https://github.com/timgrossmann/InstaPy/blob/master/README.md)
1. ```python3 quickstart.py```

## For Firefox

_Remove any versions of Firefox as it will conflict with the correct one installed below:_

1. ```sudo apt-get remove firefox-esr```
2. ```sudo apt-get remove iceweasel```
3. ```sudo apt-get remove firefox```

4. ```echo 'deb http://q4os.org/qextrepo q4os-rpi-firefox-cn main' | sudo tee /etc/apt/sources.list.d/qextrepo.list```
5. ```wget -nv -O- http://q4os.org/qextrepo/q4a-q4os.gpg.pub | sudo apt-key add -```
6. ```sudo apt-get update```
7. ```sudo apt-get install firefox```

_Update GeckoDriver if needed. Instructions at the end of this document._

_Firefox is not currently working correctly on Pi 2, to install a working version the following commands should be used:_
Pi2.1. ```wget https://launchpad.net/~ubuntu-mozilla-security/+archive/ubuntu/ppa/+build/10930950/+files/firefox_49.0+build4-0ubuntu0.14.04.1_armhf.deb```

Pi2.2 ```sudo dpkg -i firefox_49.0+build4-0ubuntu0.14.04.1_armhf.deb```

## Finishing up the Firefox installation

_Encountered some errors when trying to run the quickstart.py and ran the next 3 commands (all may not be necessary)_

8. ```sudo pip3 install future```
9. ```sudo apt-get install xvfb```
10. ```sudo pip3 install pyvirtualdisplay```
11. ```sudo reboot (may not be required, but no harm)```

_Assuming you've modified quickstart.py to your liking and added your Instagram login to instapy.py_

12. ```sudo xvfb-run python quickstart.py```

_I installed TMUX to help run this headless, so that I can disconnect from the session and have the program continue to run on the rpi3_

13. ```sudo apt-get install tmux (more info found here: https://github.com/tmux/tmux)```
14. If using firefox, follow the example seen in `examples\firefoxExample.py` to set the default browser as Firefox

## How to update GeckoDriver on Raspbian

_New releases can be found in:_ https://github.com/mozilla/geckodriver/releases

1. ```wget https://github.com/mozilla/geckodriver/releases/download/v0.18.0/geckodriver-v0.18.0-arm7hf.tar.gz```
2. ```tar -xvzf geckodriver-v*```
3. ```chmod +x geckodriver```
4. ```sudo cp geckodriver /usr/local/bin/```
