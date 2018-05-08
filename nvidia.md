# Install Nvidia drivers, CUDA Toolkit, CUDA and TensorFlow

## How To Switch Between Intel and Nvidia Graphics Card on Ubuntu
https://www.linuxbabe.com/desktop-linux/switch-intel-nvidia-graphics-card-ubuntu
 
## Check what graphics card your laptop has.
```sh
lspci -k | grep -A 2 -i "VGA"


## Switch to Nvidia Graphics Card
```sh
sudo prime-select nvidia
sudo prime-select intel
```

## Check which card is being used right now
```sh
prime-select query
```

## How to check which GPU is active in Linux?
```sh
https://unix.stackexchange.com/questions/16407/how-to-check-which-gpu-is-active-in-linux
```

## To check which GPU is currently in command (that means which is an active VGA controller) type in
```sh
lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/' | grep VGA
```
- Any controller with [VGA controller] at the end is your currently active GPU. The others are switched off


### Link with guy with same problem as me
https://gist.github.com/Brainiarc7/03c188cb045253ff7caf


## Install Tensorflow 1.7 on Cuda

Until step 9 follow the instructions of [this](http://www.python36.com/install-tensorflow141-gpu/) link that are more or less similar with the [official](https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html) ones.

Instead of step 6 where he installs Cuda 9.1, I had to install Cuda 9.0 to make it run as suggested in [this](https://github.com/tensorflow/tensorflow/issues/15604) issue.

So step 6 is as follows: 

Download cuda-9-0 from [here](https://developer.nvidia.com/cuda-90-download-archive)

```sh
sudo dpkg -i cuda-repo-ubuntu1604_9.0.176-1_amd64.deb
sudo apt-key adv --fetch-keys \
http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/7fa2af80.pub
sudo apt-get update
sudo apt-get install cuda-9-0

export PATH=/usr/local/cuda-9.0/bin${PATH:+:${PATH}}
export LD_LIBRARY_PATH=/usr/local/cuda9.0/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}

```
