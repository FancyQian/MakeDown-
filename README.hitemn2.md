## How to build
Please ensure the value of variable CONFIG_CROSS_COMPILER_PATH in config/mkconfig is equal to your compiler path.

If you want to build, excute the following command:
````bash
make htemn2
````
## How to upgrade image into Flash
## **There are two methods, please choose one.**
### Method One: Use Uboot upgrade version
#### 1. Press '@'("Shift + 2") when the device is starting up, uboot will show the following options
   * 1: Load system code to SDRAM via TFTP.
   * 2: Load system code then write to Flash via TFTP.
   * 3: Boot system code via Flash (default).
   * 4: Entr boot command line interface.
   * 7: Load Boot Loader code then write to Flash via Serial.
   * 9: Load Boot Loader code then write to Flash via TFTP.

#### 2. Choose 4 to set device ip address and tftp server ip address, excute the following command:

````bash
MT7620 # setenv ipaddr 192.168.0.x  
MT7620 # setenv serverip 192.168.0.x
MT7620 # save
````
#### 3. Reset the device, then do step1.
#### 4. Choose 2 to upgrade image into Flash via TFTP, excute the following tips:

````bash
System Load Linux Kernel then write to Flash via TFTP.
Warning!! Erase Linux in Flash then burn new one. Are you sure?(Y/N)
Please Input new ones /or Ctrl-C to discard
Input device IP (192.168.0.2) ==:192.168.0.2
Input server IP (192.168.0.253) ==:192.168.0.253
Input Linux Kernel filename (HT-EMN2-4.3.0.15-160301-g9fdc7a27.img) ==:imagename.img
Input upgrade which image (0:active image 1:buckup image 2:both images default:0) ==:0
````
### Method two: Use Linux command that on the device upgrade version
#### 1. Please set up a simple http file server on your host and put you image file in the server.
#### 2. Boot HT-EMN2, wait HT-EMN2 has enter linux bash. excute the following command:

````bash
# dload http://httpserveraddress/imagename
SWDL: Successed creating the wget process.
Connecting to 192.168.0.253 (192.168.0.253:80)
dloadImage           100% |*******************************|  4413k 00:00:00 ETA
SWDL: Success dload http://192.168.0.253/HT-EMN2-4.3.0.16-160708.img
Commit crc = 44dbb5a
# reboot
````
#### 3. After reboot, HT-EMN2 has been upgraded.

