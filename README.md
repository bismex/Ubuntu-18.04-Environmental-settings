# Ubuntu 18.04 Environmental settings
   
 
## Table of Contents
   
**Basic setting**
- [Ubuntu installation](#ubuntu-installation)
- [Network connection](#network-connection) 
- [Software updater](#software-updater)
- [Graphic card driver](#graphic-card-driver)
- [Language setting](#language-setting) 
- [Anaconda](#anaconda)  

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
- [KakaoTalk](#KakaoTalk)
- [Wheel speed](#wheel-speed)

**[Useful command](#useful-command)**
  
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
  - Add (+ button) Korean(Hangul)  <- If 'Korean(Hangul)' (not 'Korean') does not exist, click 'Manage Installed Languages' and install it
  - Delete (- button) English 
  
**(Optional - shortcut setting)**
- Input sources
- Click Korean(Hangul) 
- Option button (It exists only in 'Korean(Hangul)' not ' Korean')
- Hangul toggle key
  - Add HAN/ENG key (Alt-R or Hangul)

---

# Anaconda
## Version : Python 3.7 version (64bit) 
## [[**reference**]](https://www.anaconda.com/download/#linux)

- Download anaconda (click the reference)

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
- Confirm toolkit location
- run with 'sudo'? [yes]
- symbolic link? [no]
- Cuda samples? [no]
- Confirm sample location

```
nvcc --version
```

## Version 10.2

- Install CUDA 10.2 [[**Link**]](https://developer.nvidia.com/cuda-10.2-download-archive?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1804&target_type=runfilelocal)
   - wget http://developer.download.nvidia.com/compute/cuda/10.2/Prod/local_installers/cuda_10.2.89_440.33.01_linux.run
   - sudo sh cuda_10.2.89_440.33.01_linux.run
   - Graphic driver? [no] (important) / symbolic link ? [no] (directly connect individual version by bashrc)


**(Optional - install multiple CUDA versions)**

- When installing one version according to the above procedure and installing another one, the following error message may occur. (ex: Ubuntu 18.04 + CUDA8.0)

```
# Command lines
===========
= Summary =
===========
Driver: Not Selected
Toolkit: Installation Failed
Samples: Installation Failed

Logfile is /tmp/cuda_install_13486.log
Signal caught, cleaning up

# Log file
Uncompressing NVIDIA CUDA....................................................................................

Can't locate InstallUtils.pm in @INC (you may need to install the InstallUtils module) (@INC contains: /etc/perl /usr/local/lib/x86_64-linux-gnu/perl/5.26.1 /usr/local/share/perl/5.26.1 /usr/lib/x86_64-linux-gnu/perl5/5.26 /usr/share/perl5 /usr/lib/x86_64-linux-gnu/perl/5.26 /usr/share/perl/5.26 /usr/local/lib/site_perl /usr/lib/x86_64-linux-gnu/perl-base) at ./install-linux.pl line 6.

BEGIN failed--compilation aborted at ./install-linux.pl line 6.

Verifying archive integrity... All good.

Uncompressing NVIDIA CUDA Samples.......................................................................................

Can't locate InstallUtils.pm in @INC (you may need to install the InstallUtils module) (@INC contains: /etc/perl /usr/local/lib/x86_64-linux-gnu/perl/5.26.1 /usr/local/share/perl/5.26.1 /usr/lib/x86_64-linux-gnu/perl5/5.26 /usr/share/perl5 /usr/lib/x86_64-linux-gnu/perl/5.26 /usr/share/perl/5.26 /usr/local/lib/site_perl /usr/lib/x86_64-linux-gnu/perl-base) at ./install-sdk-linux.pl line 6.

BEGIN failed--compilation aborted at ./install-sdk-linux.pl line 6.
'uninstall_cuda_8.0.pl' -> '/usr/local/cuda-8.0/bin/uninstall_cuda_8.0.pl'
```
- Type the following command and reinstall the CUDA.
  - Unpack .run file `./cuda*.run --tar mxvf`
  - Copy InstallUtils.pm file `cp InstallUtils.pm /usr/lib/x86_64-linux-gnu/perl-base`
  - `export $PERL5LIB`
  
**[(optional - install CUDA 10.0 + CUDNN 7.5)](https://greedywyatt.tistory.com/106)**

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
sudo chmod a+r /usr/local/cuda-9.0/include/cudnn.h /usr/local/cuda-9.0/lib64/libcudnn*
```
- Install libcupti

```
sudo apt-get install libcupti-dev
```

- Do the CUDA post-install actions

```
gedit ~/.bashrc
```
- Write the below commands
```
export PATH="/usr/local/cuda-9.0/bin:$PATH"
export LD_LIBRARY_PATH="/usr/local/cuda-9.0/lib64:$LD_LIBRARY_PATH"
```
- Restart ! or `source ~/.bashrc`


**(Optional - Other version)**
- Other version [[**reference**]](https://developer.nvidia.com/rdp/cudnn-archive)


**(Optional - CUDNN PATH)**
- Download CUDNN and UNPACK
- move "lib64 and include folders" to `/home/$pID/cudnn/$version`
- Add the below commands
` export LD_LIBRARY_PATH="/home/$pID/cudnn/$version/lib64:$LD_LIBRARY_PATH" `

---


# Tensorflow 
## [[**reference**]](https://www.tensorflow.org/install/install_linux#InstallingAnaconda)

- Create virtual environment for Tensorflow by Anaconda
```
conda create -n py36_tensorflow python=3.6
conda activate py36_tensorflow
conda deactivate
```

- Install tensorflow (latest version)
```
conda activate py36_tensorflow
pip install --upgrade tensorflow-gpu
python -c "import tensorflow as tf; print(tf.__version__)"
```
---

- Download other versions
```
# example
pip install tensorflow-gpu==1.4.0
```


# Pytorch 
## [[**reference**]](https://pytorch.org/)


- Create virtual environment for Pytorch by Anaconda
- Install pytorch (various versions)
```
conda create -n seokeon_py36_torch041 python=3.6
source activate seokeon_py36_torch041
conda install pytorch=0.4.1 cuda90 -c pytorch
source deactivate
```

```
conda create -n seokeon_py27_torch041 python=2.7
source activate seokeon_py27_torch041
conda install pytorch=0.4.1 cuda90 -c pytorch
source deactivate
```

```
conda create -n seokeon_py36_torch031 python=3.6
source activate seokeon_py36_torch031
conda install pytorch=0.3.1 cuda90 -c pytorch
source deactivate
```


```
conda create -n seokeon_py27_torch031 python=2.7
source activate seokeon_py27_torch031
conda install pytorch=0.3.1 cuda90 -c pytorch
source deactivate
```

- Install pytorch (latest version)
```
conda install pytorch-cpu torchvision-cpu -c pytorch
conda install pytorch torchvision cudatoolkit=8.0 -c pytorch
conda install pytorch torchvision cudatoolkit=9.0 -c pytorch
conda install pytorch torchvision cudatoolkit=10.0 -c pytorch
```


---

# Pycharm
## [[**reference**]](https://linuxconfig.org/how-to-install-pycharm-on-ubuntu-18-04-bionic-beaver-linux)

- Install pycharm using Snaps

```
sudo snap install pycharm-community --classic 
# or sudo snap install pycharm-professional --classic
```
- pop up the message "pycharm-community 2017.3.3 from 'jetbrains' installed"

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
    - comment : ctrl+R
    - run : F5 
    - debug : F6
    - resume program : F7
    - close (Editor Tabs) : ctrl+W
    - Quick Evaluate Expression : Shift+F8
    - Evaluate Expression : F8
    - step over : F10
    - step into : F11
    - step out : shift + F11
    - Toggle line breakpoint : F12
  
    
- Run/Debug configurations
  - Python interpreter (python directory in the virtual environment)
  - Environment variables (optional.. for TensorFlow)
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
conda install -c pytorch torchvision
conda install -c anaconda pyyaml
conda deactivate
```

# Teamviewer
## [[**reference**]](https://www.teamviewer.com/ko/download/linux/?pid=google.tv.kr_sn_desk_brand_teamviewerlinux_ex_repeat.s.kr&gclid=Cj0KCQjwl9zdBRDgARIsAL5Nyn1AoUmfQIIfCaSWNBGA2IFXQRqn_SCEocnXth97RuNmHQr56DWnsVEaAkEZEALw_wcB)



# KakaoTalk
## [[**reference**]](https://hiseon.me/2018/07/02/ubuntu-kakaotalk/)

- **Caution!** An error may occur

- Install Wine and environmental settings

```
sudo apt install wine-stable cabextract
WINEARCH=win32 WINEPREFIX=~/.wine wine wineboot
wget  https://raw.githubusercontent.com/Winetricks/winetricks/master/src/winetricks
chmod +x winetricks
./winetricks --optout
```

- Select the default winprefix
- Install a Windows DLL or component
- Select (gdiplus, riched30, wmp9, msxml6)

- Copy Gulim font (window to ubuntu)
- copy C:/Windows/Fonts/gulim.ttf (or ttc) -> ~/.wine/drive_c/windows/Fonts
(using cp -i or something else)

```
chmod 644 ~/.wine/drive_c/windows/Fonts/gulim.ttf
gedit ~/.wine/system.reg
```

Change from
```
"MS Shell Dlg"="Tahoma"
"MS Shell Dlg 2"="Tahoma"
```
to
```
"MS Shell Dlg"="Gulim"
"MS Shell Dlg 2"="Gulim"
```

- Install kakaoTalk
```
winecfg
```
- Confirm the version of window
- Download the file (version check) [[Download]](https://www.kakaocorp.com/service/KakaoTalk)
- Install it
```
wine-stable KakaoTalk_Setup.exe
```

- Change language setting
```
gedit ~/.local/share/applications/wine/Programs/KakaoTalk/KakaoTalk.desktop
```
Change from
```
Exec=env WINEPREFIX="/home/ubuntu/.wine" wine-stable C:\\\\windows\\\\command\\\\start.exe /Unix /home/ubuntu/.wine/dosdevices/c:/ProgramData/Microsoft/Windows/Start\\ Menu/Programs/KakaoTalk/KakaoTalk.lnk
```
to
```
Exec=env WINEPREFIX="/home/ubuntu/.wine" LANG="ko_KR.UTF-8" wine-stable C:\\\\windows\\\\command\\\\start.exe /Unix /home/ubuntu/.wine/dosdevices/c:/ProgramData/Microsoft/Windows/Start\\ Menu/Programs/KakaoTalk/KakaoTalk.lnk
```
- Notably, LANG="ko_KR.UTF-8" is Only added

- Solving the problem of broken font

``` 
cd "/home/ubuntu/.wine/dosdevices/c:/Program Files/Kakao/KakaoTalk"
LANG="ko_KR.UTF-8" wine-stable KakaoTalk.exe
```

- Setting system tray

```
sudo apt install gnome-shell-extension-top-icons-plus
```
- Extensions
  - Topicons plus (check!)
 


# Wheel speed
## [[**reference**]](https://minjejeon.github.io/learningstock/2016/07/08/change-mouse-wheel-speed-using-imwheel.html)

```
sudo apt-get install imwheel
imwheel
sudo gedit /etc/X11/imwheel/startup.conf
```
- Change ‘IMWHEEL_START=0’ to ‘IMWHEEL_START=1’
```
gedit ~/.imwheelrc
```
- Copy all the contents in [[ref]](https://www.apt-browse.org/browse/debian/wheezy/main/i386/imwheel/1.0.0pre12-9/file/etc/X11/imwheel/imwheelrc)

- Add below commands (the number 3 means wheel speed)
```
".*"
None,      Up,   Button4, 3 
None,      Down, Button5, 3
```
- End
```
imwheel -k
```

# Useful command

- compress files : zip -r zipname.zip filename
- unzip : tar -xvzf "file name"
- unzip all 'zip' files : 
```
for file in `ls *.zip`; do unzip "${file}" -d "${file:0:-4}"; done
for file in `ls *.zip`; do unzip "${file}" -d "./"; done
for file in `ls *.rar`; do unrar e "${file}"; done

```
- zip by 7z:
   - sudo apt-get install p7zip-full
   - 7z a data.7z data.txt (zip)
   - 7z x data.7z (unzip, ) 
- remove folder : rm -rf "folder name"
- remove 해당 디렉토리 내의 특정파일 삭제: find . -type f -name "*.zip" -exec rm {} \;
- make folder : mkdir "folder name"
- copy folder : cp -r "folder a" "folder b"
- copy folder (w/o overwrite) : rsync -a -v --ignore-existing src dst 
- move folder : mv "folder a" "folder b"
- list subdirectories : 
`tree -d -L 1`
`find src -mindepth 2 -maxdepth 3 -type d > list.txt`

- Visualize gpu situation (auto update)
```
nvidia-smi -l 1
```

- **Caution!** Removing "Alt" function from "Han/Eng" key on the keyboard. [[reference]](http://hyoungx.tistory.com/38)
```
xmodmap -e 'remove mod1 = Alt_R'
xmodmap -e 'keycode 108 = Hangul'
```
> Option -> Region & Language -> Korean (Hangul) -> Option -> Shortkey (Alt+R -> Hangul)

- Chrome auto scroll [[reference]](https://chrome.google.com/webstore/detail/autoscroll/occjjkgifpmdgodlplnacmkejpdionan)

- Symbolic (soft) link : `ln -s target_path(old) link_path(new)`
  - `ln -s ../../../DB/reid/old_DB ./` 하면 `./` 위치에 `old_DB` 라는 폴더 생성
  - `ln -sf ../../../DB/reid/old_DB ./new_DB` 하면 `./` 위치에 `new_DB` 라는 폴더 생성

- Count the number of files in the certain path `find /path/to -type f | wc -l`

- Count the number of files in the present path `find . -type f | wc -l`

- Remove conda env `conda env remove -n ENV_NAME`

- Personal PATH `export PPATH="/path/to"` in ~/.bashrc

- Add 'new document' option when right clicking `touch ~/Templates/Empty\ Document`

- Change ":" to "," in filename `find . -name "*:*" -exec rename 's|:|,|g' {} \;`
  - sudo apt install rename

- GPU temperature
  - nvidia-smi -q -d temperature -l 1
  
- 우분투 APT repository 제거하기 [[ref](https://m.blog.naver.com/PostView.nhn?blogId=opusk&logNo=220986301109&proxyReferer=https%3A%2F%2Fwww.google.com%2F)]
  - sudo add-apt-repository --remove ppa:~~~~~ (지우길 원하는 프로그램 이름명)

- 터미널 열었을 때 (base) 있는 경우
  - conda config --show | grep auto_activate_base
  - conda config --set auto_activate_base False
  
- 디스크 용량 체크
  - df -h
- 폴더 내의 용량 체크
  - du -h

- 빠른 삭제
   - sudo rm -r -f /path/

- Compression
   - (install) sudo apt-get install p7zip-full
   - (compress) 7z a /created_file_name/ /folder_name or */
   - (check) 7z l /7z_file/
   - (extract) 7z e /7z_file/ 
   
- Memory check
   - watch -d free / watch -n 1 free
   
- 파일 수 세기
   - find . -type f | wc -l
   
- 해당 조건 파일 옮기기
   - find path_A -name '*.jpg' -exec mv -t path_B {} +
   - maxdepth 1 
   
- Pycharm deployment
   - deploy먼저
   - interpreter
   
- pip 이용한 설치중 Cannot uninstall '~~~' 에러발생
   - sudo pip install pwntools 대신에 sudo pip install --ignore-installed pwntools
   
- ppt FHD 동영상 저장 방법 (https://m.blog.naver.com/PostView.nhn?blogId=radiobj5&logNo=220345624061&proxyReferer=https:%2F%2Fwww.google.com%2F)
   - 동영상 녹음 후에
   - Alt + F11
   - 삽입 -> 모듈
   
```
Sub MkVideo()
    If ActivePresentation.CreateVideoStatus <> ppMediaTaskStatusInProgress Then
    ActivePresentation.CreateVideo FileName:=Environ("USERPROFILE") & "\Desktop\test.mp4", _
    UseTimingsAndNarrations:=True, _
    VertResolution:=1080, _
    FramesPerSecond:=25, _
    Quality:=100
    Else:
    MsgBox "There is another conversion to video in progress"
    End If
    End Sub

```
   - F5
- server 관리
   - ssh 명령어 short-cut관리: gedit ~/.ssh/config
   - ssh 바로 접근: ssh username@ip_adress
   - id 생성
      - 서버 root계정으로 로그인
      - sudo adduser id_name
   - CUDA 설정
      - vim ~/.bashrc
         - Cuda path
            - export PATH="/usr/local/cuda-10.0/bin:$PATH"
            - export LD_LIBRARY_PATH="/usr/local/cuda-10.0/lib64:$LD_LIBRARY_PATH"
         - Anaconda path
            - export PATH="/home/ROOT_NAME/anaconda3/bin:$PATH"
            - export LD_LIBRARY_PATH="/home/ROOT_NAME/anaconda3/lib64:$LD_LIBRARY_PATH"
      - source ~/.bashrc
   - error control
      - anaconda 가상환경 설정시 permission error: sudo chmod -R 777 anaconda3
      - slurm에서 sbatch 안먹을때 (sinfo 입력했을때 drain인경우)
        - 돌아가는 job 있을때: scontrol update nodename=node10 state=resume
        - 돌아가는 job 없을때: scontrol update nodename=node10 state=idle
   - 서버에서 다른 cuda version 쓰고 싶을 때 (10.2 기준)
      - CUDA 파일 다운로드: wget http://developer.download.nvidia.com/compute/cuda/10.2/Prod/local_installers/cuda_10.2.89_440.33.01_linux.run
      - CUDA 설치: sudo sh cuda_10.2.89_440.33.01_linux.run
         - EULA? [accept]
         - Unsupported configuration? [yes]
         - Graphic driver? [no] (important) 
         - Cuda toolkit? [yes]
         - run with 'sudo'? [yes]
         - symbolic link? [no] (directly connect individual version by bashrc)
         - Cuda samples? [no]
      - CUDNN 파일 다운로드
      - CUDNN 설치
      - CUDNN 이동
         - move "lib64 and include folders" to `/home/choi/cudnn/$version`
      - link
         - `vim ~/.bashrc`
            - `export PATH="/usr/local/cuda-10.2/bin:$PATH"`
            - `export LD_LIBRARY_PATH="/usr/local/cuda-9.0/lib64:$LD_LIBRARY_PATH"`
            - `export LD_LIBRARY_PATH="/home/choi/cudnn/$version/lib64:$LD_LIBRARY_PATH" `
         - `source ~/.bashrc`
   - 남은 용량 확인
      - du -sh *
         

- conda activate 가 안되고 source activate만 되는 경우
  - source ~/anaconda3/etc/profile.d/conda.sh 

- nvidia graphic driver 다른 버전 쓰고 싶을 때 (https://codechacha.com/ko/install-nvidia-driver-ubuntu/)
  - 자동 버전 설치
    - sudo add-apt-repository ppa:graphics-drivers/ppa
    - sudo apt update
    - sudo ubuntu-drivers autoinstall
    - sudo reboot
  - 기존 삭제(만약 기존 설치된 프로그램과 출동한다면): sudo apt --purge autoremove nvidia*

- Automatic mixed precision 쓰는 법 (https://hoya012.github.io/blog/Image-Classification-with-Mixed-Precision-Training-PyTorch-Tutorial/)
  - CUDA10.1 버전 이상만 pytorch1.6 지원
  - CUDA10.1 버전 이상 설치 / CUDNN 설치 (필수인지는 확실하지 않음)
  - conda create -n seokeon_torch16 python=3.6
  - conda activate seokeon_torch16  
  - conda install pytorch torchvision cudatoolkit=10.1 -c pytorch  (10.2도 가능)
  - nvidia graphic driver 업그레이드
  - 코드에서 변경해야 하는 부분
    - AMP_flag = True
    - if AMP_flag:
      - self.scaler = torch.cuda.amp.GradScaler() [추가된부분]
    - dataloader iteration 내부에서
      - if AMP_flag:
         - with torch.cuda.amp.autocast(): [추가된부분]
            - outputs = self.model(inputs)
            - loss = self.criterion(outputs, labels)
            - self.optimizer.zero_grad()
            - self.scaler.scale(loss).backward() [변경된부분]
            - self.scaler.step(self.optimizer) [변경된부분]
            - self.scaler.update() [변경된부분]
      - else:
         - outputs = self.model(inputs)
         - loss = self.criterion(outputs, labels)
         - self.optimizer.zero_grad()
         - loss.backward()
         - self.optimizer.step()
  
  
- Mount 완련!!
   - bootloader가 켜지지 않고 grup gnu terminal 창만 나오는 경우ㅜ
     - ubuntu booting USB로 부팅(try ubuntu without installing)
     - 인터넷연결
     - sudo add-apt-repository ppa:yannubuntu/boot-repair
     - sudo apt-get update
     - sudo apt-get install -y boot-repair
     - boot-repair
     - Click Recommended repair
   - gpt to mbr (https://www.linuxtopic.com/2017/02/convert-partition-table-gpt-to-mbr-in.html)
     - install gdisk
     - gdisk /dev/sda
     - command: r
     - Recovery/transformation command? g
     - (MBR command: p)
     - MBR command: w
     - coverted 1 paritions. Finalize and exit? (Y/N): y
     - (command: w)
     - reboot
   - 4TB이상 하드를 사서 리눅스를 설치할꺼면? (http://blog.naver.com/PostView.nhn?blogId=5bpa&logNo=220460531819)
   - 하드디스크 처음 마운트 (https://seongkyun.github.io/others/2019/03/05/hdd_mnt/)
      - sudo fdisk -l 에서 하드 확인
      - 용량이 2TB 이하인 경우
         - sudo fdisk /dev/sda
         - command: n
         - select: p
         - Partition number: 1
         - First sector: (enter)
         - Last sector: (enter)
         -> created a new partition ~~
         - command: p
         - command: w
      - format
         - sudo mkfs.ext4 /dev/sda1
      - uuid 확인
         - 해당 disk의 UUID 복사
      - mount
         - sudo mkdir /mnt/directory-to-mount
         - sudo vim /etc/fstab
           - UUID=~~~~~ /directory-to-mount ext4 defaults 0 0
           - 맨 아랫줄에 입력
         - sudo mount -a
         - df -h (마운트 확인)
      - symbolic link
         - sudo ln -s /directory-to-mount /home/choi/
         - cd ~/directory-to-mount
         - sudh chmod 777 ~/directory-to-mount
   - Change mount position
      ```
      lsblk # check disk position
      sudo xdg-open /etc/fstab # change disk position
      ```
      > Add /dev/sdc /mnt/hard1 ntfs-3g defaults 0 2 (??? not completed)
   - Unrecognized mount option "default"
      - vim /etc/fstab
      - 에서 default라고 적힌것 defaults로
   - hard가 read-only 인경우 (window caches 에 의해서)
      - https://askubuntu.com/questions/462381/cant-mount-ntfs-drive-the-disk-contains-an-unclean-file-system
      - https://hidekuma.github.io/ec2/ubuntu/linux/remount-ebs/
      - $ cat /proc/mounts 에서 해당 디스크 ro로 되어있는지 확인
      - $ sudo umount /dev/sdXY 
      - $ sudo ntfsfix /dev/sdXY (두번?)
      - $ sudo mount -o rw /dev/sdXY
      
      
- 다른 서버 폴더 접근
   - 폴더 gui에서 
   - connect to server
      - sftp://ID@ip
- 가상환경이나 현재 python에 pip으로 설치된 패키지 목력정보 만들기
   - pip freeze > requirement.txt (문서생성)
   - pip install -r requirements.txt (pip install)
   
- Git 관련
   - git clone ~~~
   - 파일 수정
   - git add --all
   - git commit -m "Fix ~~ or Update ~~"
   - git push origin master
   - pycharm 과 연동
      https://lsjsj92.tistory.com/364
   
   
   
