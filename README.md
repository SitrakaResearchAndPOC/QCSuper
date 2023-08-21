# QCSuper and QCSuperLXD
## Hardware setup
* Rooted Samsung S5 phone with android 4.4.2
  
## Installation QCSuper Without LXC using debian
* Follow this official [installation](https://github.com/P1sec/QCSuper) or [fork](https://github.com/SitrakaResearchAndPOC/fork_QCSuper)
* Install wireshark by apt
* chmod +x dumpcap

## Installation with LXC  using ubuntu
```
apt update
```
```
apt-get install lxd lxd-client
```


## Installation with LXC  using DragonOS
```
apt update
```
```
apt-get install snapd  
```
```
snap install lxd  
```

```
snap install lxd-client  
```

## Initialisation of LXD
```
lxd init  
```
For questions please follow the default option, an image illustration is at [image](https://github.com/SitrakaResearchAndPOC/QCSuper/blob/main/screen.jpg) 
  
User need to be in group lxd :
```
sudo usermod -a G lxd $USER  
```
or  
```
sudo /usr/sbin/usermod lxd $USER  
```

$PATH need to contains /usr/local/bin, verify with :  
```
echo $PATH  
```

if not, setup this, or add this in your .bashrc or .zshrc or ...  

```
export PATH=$PATH:/usr/local/bin  
```


## SETUP
```
cd
```
``` 
mkdir tempdir  
```
```
cd tempdir  
```
```
git clone --depth 1 https://github.com/henintsoa98/QCSuperLXD  
```
```
cd QCSuperLXD  
```
```
chmod +x lxd-device lxd-image  
```
```
sudo cp lxd-device lxd-image /usr/local/bin
```
```
wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=1nlfxKUWMWXk-DziegP4e8R3gepsNGxpA' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=1nlfxKUWMWXk-DziegP4e8R3gepsNGxpA" -O 885cab44d2a87c24e6bacb746dfd89b317839bc9398fa62e266aeb565913affe.tar.gz   && rm -rf /tmp/cookies.txt  
```

If Download doesn't begin;
Download manually this [image](https://drive.google.com/file/d/1nlfxKUWMWXk-DziegP4e8R3gepsNGxpA/view?usp=sharing) and copy it to ~/tempdir/QCSuperLXD  that we create
```
lxd-image import QCSuper 885cab44d2a87c24e6bacb746dfd89b317839bc9398fa62e266aeb565913affe.tar.gz  
```
After import, Log should be 
```
Image imported with fingerprint: 885cab44d2a87c24e6bacb746dfd89b317839bc9398fa62e266aeb565913affe
Creating QCSuper
Retrieving image: Unpack: 100% (26.55MB/s)
Starting QCSuper                           
Profile gui created            
Profile gui added to QCSuper
```
## exit if it enter into the container, to finish setup and restart the terminal
```
sudo su
```

## plug your rooted device and enable adb debugging
```
lxd-device add QCSuper newADB
```
## select an number that is your device in the list
Have a look on this [image](https://github.com/SitrakaResearchAndPOC/QCSuper/blob/main/screen2.jpg)

## RUN
just type :  
```
lxc exec QCSuper -- run
```
## Remark : This remark is not an error [image](https://github.com/SitrakaResearchAndPOC/QCSuper/blob/main/screen3.jpg)
```
You don't have permission to read the file "IOR.txt"
```

## Documentations
* https://medium.com/@623yuxiang/qcsuper-installation-manual-in-ubuntu16-04-18-04-a5b28a349cb9
* https://medium.com/@googler_ram/open-source-lte-5g-packet-capture-tool-4bd3d360aa0
* https://github.com/P1sec/QCSuper
* https://www.pinterest.com/pin/261419953356588743/
* https://forum.sailfishos.org/t/cellular-protocol-logging-with-sailfish-os/3661
* https://web.facebook.com/1231669760337079/posts/qcsuper-a-tool-communicating-with-qualcomm-based-phones-and-modems-allowing-to-c/2129156123921767/?_rdc=1&_rdr
* https://www.scribd.com/document/628502219/qcsuper-ims-registration-capture-sample-Buscar-con-Google
* https://etda.libraries.psu.edu/files/final_submissions/25032
