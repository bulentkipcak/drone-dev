# Installing Ardupilot and MAVProxy Ubuntu 20.04

## Video Tutorial at https://youtu.be/1FpJvUVPxL0

## Clone ArduPilot

In home directory:
```
cd ~
sudo apt install git
sudo apt-get install gitk git-gui
git clone https://github.com/ArduPilot/ardupilot.git
cd ardupilot
```

## Install dependencies:
```
cd ardupilot
Tools/environment_install/install-prereqs-ubuntu.sh -y
```

reload profile
```
. ~/.profile
```
## If the next step "git submodule update" fails
```
git config --global url.https://.insteadOf git://
```

## Checkout Latest Copter Build
```
git checkout Copter-4.0.4
git submodule update --init --recursive
```
## Install MAVProxy
```
sudo pip3 install future pymavlink MAVProxy
```

## Update bash
```
gedit ~/.bashrc
export PATH=$PATH:$HOME/ardupilot/Tools/autotest
export PATH=/usr/lib/ccache:$PATH
. ~/.bashrc
```

Run SITL (Software In The Loop) once to set params:
```
cd ~/ardupilot/Tools/autotest
sim_vehicle.py -v ArduCopter -f gazebo-iris --console
```





