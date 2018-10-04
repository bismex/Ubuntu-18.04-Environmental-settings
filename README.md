# Ubuntu 18.04 Environmental settings


## Table of Contents
- [Ubuntu installation](#ubuntu-installation)
- [Network connection](#network-connection)
- [Software updater](#software-updater)
- [Graphic card driver](#graphic-card-driver)
- [Language setting](#language-setting)
- [Adaconda](#adaconda)
- [CUDA](#cuda)
- [CUDNN](#cudnn)
- [Pytorch](#pytorch)
- [Other programs](#other-programs)
- [Useful command](#useful-command)
- [Tensorflow](#tensorflow)

---

# Ubuntu installation 
## Version : 18.04
## [[**reference**]](http://vire.tistory.com/25?category=678504)

- Download ubuntu 18.04 [[**Link**]](https://www.ubuntu.com/download/desktop)
- Prepare USB
- Create booting disk [[**Link(Korean)**]](http://crescentupon.tistory.com/383)
- Turn off *Windows Quick Start* [[**Link(Korean)**]](https://prolite.tistory.com/1253)
- BIOS
  - Boot Ubuntu USB
- Install Ubuntu
  - Welcome : English
  - Keyboard layout : ENG(US)
  - Updates and other software : Normal installation / Download updates while installing Ubuntu
  - Installation type : something else 
    - I installed it on the remaining hard disk.
    - And, I partitioned it into 'partition swap' and 'ext4'. [[**Link**]](https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
  - Where are you : seoul
  - Who are you : write your information


---

# Network connection

- Settings
- Network
- Wired option
- IPv4
  - Input (Address, Netmask, Gateway, DNS)

---

# Software updater

- Searching window
- software update

---

# Graphic card driver 
## [[**reference**]](http://optic.tistory.com/119)

```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo ubuntu-drivers autoinstall
sudo reboot
```
(after reboot)
```
sudo nvidia-settings
```


---

# Language setting 
## **(Korean only)**
## [[**reference**]](http://snowdeer.github.io/linux/2018/07/11/ubuntu-18p04-install-korean-keyboard/)

- Settings
- Region & Language
- Input sources
  - Delete English
  - Add Korean(Hangul)
  
**(Optional)**
- Input sources
  - Click Korean(Hangul)
- Option button
- Hangul toggle key
  - Add Hangul



---

# Adaconda
## Version : Python 3.7 version (64bit) 
## [[**reference**]](https://www.anaconda.com/download/#linux)

```
cd
cd Downloads/
bash Anaconda3-5.3.0-Linux-x86_64.sh
```
- License agreement
- Confirm install location
- /root/.bachrc? [yes]
- VSCode? [No]

(after reboot)

```
conda --version
conda create -n new_name python=3.6
conda activate pytorch36
conda deactivate
```


# CUDA
## Version 9.0
## [[**reference**]](https://medium.com/@taylordenouden/installing-tensorflow-gpu-on-ubuntu-18-04-89a142325138)

- Install CUDA 9.0 [[**Link**]](https://developer.nvidia.com/cuda-90-download-archive)
  - Linux / x86_64 / Ubuntu / 17.04 (18.04 is not supported) / runfile (local)
  - Base Installer (Download 1.6GB)
  
```
cd
cd Downloads/
sudo chmod +x cuda_9.0.176_384.81_linux.run
./cuda_9.0.176_384.81_linux.run --override
```

- EULA? [accept]
- Unsupported configuration? [yes]
- Graphic driver? [no]
- Cuda toolkit? [yes]
- run with 'sudo'? [yes]
- Confirm toolkit location
- symbolic link? [yes]
- Cuda samples? [yes]
- Confirm sample location

# CUDNN

# Pytorch 
## [[**reference**]](https://pytorch.org/)



# Other programs

```
pip install scipy
pip install sacred
pip install matplotlib
pip install opencv-python
pip install pillow
pip install numpy
```

# Useful command


```
nvidia-sim -l 1
```
Visualize gpu situation






# Tensorflow 
## [[**reference**]](https://www.tensorflow.org/install/install_linux#InstallingAnaconda)




