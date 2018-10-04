# Ubuntu 18.04 Environmental settings

### Network connection

Option -> Network -> Wired option -> IPv4 -> input (Address, Netmask, Gateway, DNS)

### Software updater

Search -> software update

### Graphic card

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

### Language setting (Korean only)



[[**reference**]](http://snowdeer.github.io/linux/2018/07/11/ubuntu-18p04-install-korean-keyboard/)

### Adaconda install



### pytorch install

[[**reference**]](https://pytorch.org/)

### other programs

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



### cuda and cudnn

Install CUDA 9.0

https://medium.com/@taylordenouden/installing-tensorflow-gpu-on-ubuntu-18-04-89a142325138

### tensorflow install

https://www.tensorflow.org/install/install_linux#InstallingAnaconda


