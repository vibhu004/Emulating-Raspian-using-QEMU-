​<h1 align="center"> 🇪‌🇲‌🇺‌🇱‌🇦‌🇹‌🇮‌🇴‌🇳‌</h1>

<details>
<summary><h2>𝓐𝓘𝓜</h2></summary>
<br>
Aim is to understand the concept of Emulation.<br>
How Emulation works ?<br>
And to emulate a linux based operating system on arm64 architecture
</details>
<br>

<details>
<summary><h2>𝓟𝓻𝓮𝓻𝓮𝓺𝓾𝓲𝓼𝓲𝓽𝓮</h2></summary>
<br>
Below are some prerequisite to achieve our aim.

- sudo permission to the system
- Emulator [we will be using QEMU] 
- Image file of Operating System to emulate
</details>
<br>
<details>
<summary><h2>𝓒𝓸𝓷𝓬𝓮𝓹𝓽 𝓸𝓯 𝓔𝓶𝓾𝓵𝓪𝓽𝓲𝓸𝓲𝓷 & 𝓗𝓸𝔀 𝓔𝓶𝓾𝓵𝓪𝓽𝓲𝓸𝓷 𝔀𝓸𝓻𝓴𝓼</h2></summary>
<br>
Emulation is a software that enables one computer system to behave like another computer system.<br>
It enables a host system to run software or use peripheral devices designed for the guest system.<br>
It refers to the ability of a computer program in an electronic device to emulate (or imitate) another program or device.
<br>
Emulation works by emulating(copying) behaviour of some another computer system architecture and run its program on some different kind of computer system(which is capable of emulating)
So the guest system programs think they are running on the same architecture for which they are designed but in reality emulator is imitating the architecture. 
</details>
<br>
<details>
<summary><h2>𝓔𝓶𝓾𝓵𝓪𝓽𝓲𝓷𝓰 𝓪 𝓵𝓲𝓷𝓾𝔁 𝓫𝓪𝓼𝓮𝓭 𝓸𝓹𝓮𝓻𝓪𝓽𝓲𝓷𝓰 𝓼𝔂𝓼𝓽𝓮𝓶 𝓸𝓷 𝓪𝓻𝓶64 𝓪𝓻𝓬𝓱𝓲𝓽𝓮𝓬𝓽𝓾𝓻𝓮<h2></summary>
<br>
We will be Emulating a Raspian OS
<p>

STEP 1  -  Downloading Qemu emulator

$ sudo yum install qemu

<br>

STEP 2 - Getting OS Image <br>

Download a raspian image from official 
[link](https://www.raspberrypi.org/software/operating-systems/ "link")
<br>
I have used lite version (2021-05-07-raspios-buster-armhf-lite.zip)

<br>

STEP 3 - Unzip the img 

$ sudo unzip 2021-05-07-raspios-buster-armhf-lite.zip

<br>

STEP 4 - Modifying Image

$ qemu-img convert -f raw -O qcow2 2021-05-07-raspios-buster-armhf-lite.img raspios-buster-armhf-lite.qcow

$ qemu-img resize raspios-buster-armhf-lite.qcow +4G

<br>

STEP 5 - Download kernel and dtb for the image 

Use this [link](https://github.com/dhruvvyas90/qemu-rpi-kernel/ "link") and download kernel and dtb file accordingly.

<br>

STEP 6 - BOOTING THE IMAGE 

$ sudo qemu-system-aarch64 \
    -kernel kernel-qemu-4.19.50-buster \
    -append "root=/dev/sda2 panic=1 rootfstype=ext4 rw" \
    -hda 2021-05-07-raspios-buster-armhf-lite.qcow \
    -dtb versatile-pb-buster.dtb \
    -cpu arm1176 -m 256 \
    -M versatilepb \
    -no-reboot \
    -serial stdio \
    -net nic -net user \
    -net tap,ifname=vnet0,script=no,downscript=no

NOTE : DOWNLOAD ALL THE FILES STATED IN THIS DOCUMENT TO A SINGLE FOLDER OR ELSE MODIFY THE STEP 6 COMMAND ACCORDING TO YOUR DOWNLOADED FILE PATHS.
</p>
</details>
<br>
<details>
<summary><h2>𝓒𝓸𝓷𝓬𝓵𝓾𝓼𝓲𝓸𝓷</h2></summary>
We have successfully emulated an linux based raspbian image on arm64 architecture.
If you have any suggestions or you found any errors or mistake in this document please feel free to contact by clicking below image. Any kind of updates are welcome too.


<a href="mailto:vatsv070@gmail.com"><img src="https://raw.githubusercontent.com/vibhu004/supportingfiles/main/mail.gif" alt="logo" height="40" width="40"></a>
</details>
