# Ubuntu 18.04 Environmental settings


# Table of Contents
- [Network connection](###Network-connection)
- [Software updater](###Software-updater)
- [Graphic card driver](###Graphic-card-driver)
- [Language setting (Korean only)](###Language-setting-(Korean-only))
- [Adaconda](###Adaconda)
- [Pytorch](###Pytorch)
- [Other programs](###Other-programs)
- [Useful command](###Useful-command)
- [Cuda and cudnn](###Cuda-and-cudnn)
- [Tensorflow](###Tensorflow)



### Network connection

- Settings
- Network
- Wired option
- IPv4
  - Input (Address, Netmask, Gateway, DNS)

---

### Software updater

- Searching window
- software update

---

### Graphic card driver

```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo ubuntu-drivers autoinstall
sudo reboot
```
(after reboot)
```
sudo nvidia-settings
```
[[**reference**]](http://optic.tistory.com/119)

---

### Language setting (Korean only)

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

[[**reference**]](http://snowdeer.github.io/linux/2018/07/11/ubuntu-18p04-install-korean-keyboard/)

---

### Adaconda




### Pytorch

[[**reference**]](https://pytorch.org/)

### Other programs

```
pip install scipy
pip install sacred
pip install matplotlib
pip install opencv-python
pip install pillow
pip install numpy
```

### Useful command


```
nvidia-sim -l 1
```
Visualize gpu situation



### Cuda and cudnn

Install CUDA 9.0

https://medium.com/@taylordenouden/installing-tensorflow-gpu-on-ubuntu-18-04-89a142325138

### Tensorflow

https://www.tensorflow.org/install/install_linux#InstallingAnaconda


