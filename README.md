# Ubuntu 18.04 Environmental settings


## Table of Contents

**Basic setting**
- [Ubuntu installation](#ubuntu-installation)
- [Network connection](#network-connection)
- [Software updater](#software-updater)
- [Graphic card driver](#graphic-card-driver)
- [Language setting](#language-setting)
- [Adaconda](#adaconda)

**Tensorflow**
- [CUDA](#cuda)
- [CUDNN](#cudnn)
- [Tensorflow](#tensorflow)
  
**Pytorch**
- [Pytorch](#pytorch)
  
**ETC**
- [Pycharm](#pycharm)
- [Pytorch tutorial](#pytorch-tutorial)
- [Other programs](#other-programs)
- [Useful command](#useful-command)
- [Teamviewer](#teamviewer)

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
```

---

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

```
nvcc --version
```

---

# CUDNN
## Version 7.0.5
## [[**reference**]](https://medium.com/@taylordenouden/installing-tensorflow-gpu-on-ubuntu-18-04-89a142325138)

- Download this [**“cuDNN v7.0.5 Library for Linux”**](https://developer.nvidia.com/compute/machine-learning/cudnn/secure/v7.0.5/prod/9.0_20171129/cudnn-9.0-linux-x64-v7)
- Unpack the archive and move it the contents into the directory where you install CUDA 9.0

```
# Unpack the archive
tar -zxvf cudnn-9.0-linux-x64-v7.tgz
# Move the unpacked contents to your CUDA directory
sudo cp -P cuda/lib64/libcudnn* /usr/local/cuda-9.0/lib64/
sudo cp  cuda/include/cudnn.h /usr/local/cuda-9.0/include/
# Give read access to all users
sudo chmod a+r /usr/local/cuda-9.0/include/cudnn.h /usr/local/cuda/lib64/libcudnn*
```
- Install libcupti

```
sudo apt-get install libcupti-dev
```

- Do the CUDA post-install actions

```
export PATH=/usr/local/cuda-9.0/bin${PATH:+:${PATH}}
export LD_LIBRARY_PATH=/usr/local/cuda/lib64:${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
```

- Restart !

---

# Tensorflow 
## [[**reference**]](https://www.tensorflow.org/install/install_linux#InstallingAnaconda)

- Create virtual environment for Tensorflow by Anaconda
```
conda create -n tensorflow36 python=3.6
conda activate tensorflow36
conda deactivate
```

- Install tensorflow
```
conda activate tensorflow36
pip install --upgrade tensorflow-gpu
python -c "import tensorflow as tf; print(tf.__version__)"
conda deactivate
```
---


# Pytorch 
## [[**reference**]](https://pytorch.org/)


- Create virtual environment for Pytorch by Anaconda
```
conda create -n pytorch36 python=3.6
conda activate pytorch36
conda deactivate
```

- Install pytorch
```
conda activate pytorch36
conda install pytorch torchvision -c pytorch
conda deactivate
```


---

# Pycharm
## [[**reference**]](https://linuxconfig.org/how-to-install-pycharm-on-ubuntu-18-04-bionic-beaver-linux)

- Install pycharm using Snaps

```
sudo snap install pycharm-community --classic
pycharm-community 2017.3.3 from 'jetbrains' installed
```

- Start
```
pycharm-community
```
- Make new project
- Environmental settings
  - File
  - Settings
  - Project interpreter
  - Select the virtual environment where you installed pytorch
- Change pycharm keymap
  - File
  - Settings
  - Keymap
- Run/Debug configurations
  - Python interpreter (python directory in the virtual environment)
  - Environment variables
    - Add (Name : LD_LIBRARY_PATH / Value : /usr/local/cuda-9.0/lib64)
  - Working directory
    - /home/user_name/PycharmpProjects/your_project/
    
  
---

# Pytorch tutorial
## [[**reference**]](https://pytorch.org/tutorials/)

  

# Other programs


- In the vitual environment (anaconda)
```
conda activate pytorch36
pip install scipy
pip install sacred
pip install matplotlib
pip install opencv-python
pip install pillow
pip install numpy
conda deactivate
```

---

# Useful command

- Visualize gpu situation (auto update)
```
nvidia-smi -l 1
```

---

# Teamviewer
## [[**reference**]](https://www.teamviewer.com/ko/download/linux/?pid=google.tv.kr_sn_desk_brand_teamviewerlinux_ex_repeat.s.kr&gclid=Cj0KCQjwl9zdBRDgARIsAL5Nyn1AoUmfQIIfCaSWNBGA2IFXQRqn_SCEocnXth97RuNmHQr56DWnsVEaAkEZEALw_wcB)







