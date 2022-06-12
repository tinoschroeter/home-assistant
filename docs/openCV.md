# Install opencv, python and open kinect (libfreenect)

```shell
sudo apt-get update
sudo apt-get upgrade
```

## Install the necessary dependencies 

```shell
sudo apt-get install git-core cmake freeglut3-dev vim \
     pkg-config build-essential libxmu-dev libxi-dev libusb-1.0-0-dev
```

## Clone the libfreenect repository to your system

```shell
git clone git://github.com/OpenKinect/libfreenect.git
```

##  Install libfreenect

```shell
cd libfreenect
mkdir build
cd build
cmake -L ..
make
sudo make install
sudo ldconfig /usr/local/lib64/
```

## To use Kinect as a non-root user do the following

```shell
sudo adduser $USER video
sudo adduser $USER plugdev
```

## Also make a file with rules for the Linux device manager

```shell

sudo vim /etc/udev/rules.d/51-kinect.rules

# ATTR{product}=="Xbox NUI Motor"
SUBSYSTEM=="usb", ATTR{idVendor}=="045e", ATTR{idProduct}=="02b0", MODE="0666"
# ATTR{product}=="Xbox NUI Audio"
SUBSYSTEM=="usb", ATTR{idVendor}=="045e", ATTR{idProduct}=="02ad", MODE="0666"
# ATTR{product}=="Xbox NUI Camera"
SUBSYSTEM=="usb", ATTR{idVendor}=="045e", ATTR{idProduct}=="02ae", MODE="0666"
# ATTR{product}=="Xbox NUI Motor"
SUBSYSTEM=="usb", ATTR{idVendor}=="045e", ATTR{idProduct}=="02c2", MODE="0666"
# ATTR{product}=="Xbox NUI Motor"
SUBSYSTEM=="usb", ATTR{idVendor}=="045e", ATTR{idProduct}=="02be", MODE="0666"
# ATTR{product}=="Xbox NUI Motor"
SUBSYSTEM=="usb", ATTR{idVendor}=="045e", ATTR{idProduct}=="02bf", MODE="0666"
```

## Log out and back in. Run the following command in a terminal to test if libfreenect is correctly installed

```shell
freenect-glview
```

This should cause a window to pop up showing the depth and RGB images. Pressing ‘w’ 
on the keyboard causes the kinect to tilt up and pressing ‘x’ causes the kinect to tilt down. 
There are several other control options that are listed in the terminal when “freenect-glview” is run

## In order to use the Kinect with opencv and python, 

the python wrappers for libfreenct need to be installed. Before doing that, install the necessary dependencies

```shell
sudo apt-get install cython3 python3-dev python3-numpy pip
```

## Go to the directory ~/libfreenect/wrappers/python and run the following command

```shell
sudo python3 setup.py install
```

## install-opencv-3-on-raspbian

[install-opencv-3-on-raspbian](https://pyimagesearch.com/2015/10/26/how-to-install-opencv-3-on-raspbian-jessie/)


https://github.com/xxorde/librekinect


https://www.npmjs.com/package/opencv4nodejs#automating-lights-by-people-detection-through-classifier

https://medium.com/softway-blog/automating-lights-with-computer-vision-nodejs-fb9b614b75b2
