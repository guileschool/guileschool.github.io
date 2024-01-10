---
layout: post
comments: true
title: '비글본블랙 BBB 핸드북'
author: beaglebone
date: 2017-06-01 13:25
tags: [arm,cortex,ti,am3350,beaglebone]
---
<!--more-->
language_tabs:
  - logs
  - shell
  - ruby
  - c
  - python
  - applescript
  
toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:

search: true
---

Getting Started Sitara_Linux_SDK_Training
===
ti-sdk-am335x-evm-08.00.00.00-Linux-x86-Install.bin 파일을 [다운로드](http://software-dl.ti.com/sitara_linux/esd/AM335xSDK/latest/exports/ti-sdk-am335x-evm-08.00.00.00-Linux-x86-Install.bin)한다

## 비글본블랙 TFTP/NFS 부팅을 위한 uEnv.txt
```
#u-boot defaults: uncomment and override where needed

### tftp settings
ipaddr=192.168.0.3
serverip=192.168.0.2
netmask=255.255.255.0
gatewayip=192.168.0.1
uenvcmd=run netboot
ethaddr=6c:ec:eb:ad:89:b4
autoload=no

bootcmd=run findfdt; run mmcboot;setenv mmcdev 1; setenv bootpart 1:2; run netboot;
bootfile=zImage-am335x-evm.bin
fdtfile=am335x-boneblack.dtb
rootpath=/usr/local/arago-2015.02/targetNFS
nfsopts=nolock
###

### static ip
netargs=set bootargs console=${console} ${optargs} root=/dev/nfs nfsroot=${serverip}:${rootpath},${nfsopts} rw ip=${ipaddr}:${serverip}:${gatewayip}:${netmask}::eth0:off netmask=255.255.255.0
netboot=echo Booting from network ...; tftp ${loadaddr} ${bootfile}; tftp ${fdtaddr} ${fdtfile}; run netargs; bootz ${loadaddr} - ${fdtaddr}
```

## 디렉토리 구조
[http://processors.wiki.ti.com/index.php/Processor_SDK_Linux_Directory_Structure](http://processors.wiki.ti.com/index.php/Processor_SDK_Linux_Directory_Structure)

## AM35x EVM Boot from SD/MMC card
[http://wiki.tiprocessors.com/index.php/AM35x_EVM_Boot_from_SD/MMC_card](http://wiki.tiprocessors.com/index.php/AM35x_EVM_Boot_from_SD/MMC_card)

## AM335x Flash Image Builder User's Guide  
[http://wiki.tiprocessors.com/index.php/AM335x_Flash_Image_Builder_User%27s_Guide](http://wiki.tiprocessors.com/index.php/AM335x_Flash_Image_Builder_User%27s_Guide)

###

## Linux Core U-Boot User's Guide  
[http://processors.wiki.ti.com/index.php/Processor_SDK_Linux_U-Boot_Release_Notes](http://processors.wiki.ti.com/index.php/Processor_SDK_Linux_U-Boot_Release_Notes)
[http://processors.wiki.ti.com/index.php/Linux_Core_U-Boot_User%27s_Guide](http://processors.wiki.ti.com/index.php/Linux_Core_U-Boot_User%27s_Guide)

텍사스 인스트루먼츠 주요 자료 링크 모음
===
[http://processors.wiki.ti.com/index.php/Processor_SDK_Linux_Getting_Started_Guide](http://processors.wiki.ti.com/index.php/Processor_SDK_Linux_Getting_Started_Guide)
[http://processors.wiki.ti.com/index.php/Processor_SDK_Linux_Setup_Script](http://processors.wiki.ti.com/index.php/Processor_SDK_Linux_Setup_Script)
[http://processors.wiki.ti.com/index.php/Processor_SDK_Linux_create_SD_card_script#SD_Card_Using_Custom_Images](http://processors.wiki.ti.com/index.php/Processor_SDK_Linux_create_SD_card_script#SD_Card_Using_Custom_Images)
[http://processors.wiki.ti.com/index.php/Processor_SDK_Linux_Software_Developer’s_Guide](http://processors.wiki.ti.com/index.php/Processor_SDK_Linux_Software_Developer’s_Guide)
[http://processors.wiki.ti.com/index.php/Sitara_Linux_Training:_Hands_on_with_the_SDK](http://processors.wiki.ti.com/index.php/Sitara_Linux_Training:_Hands_on_with_the_SDK)
[http://processors.wiki.ti.com/index.php/Sitara_Linux_SDK_Training](http://processors.wiki.ti.com/index.php/Sitara_Linux_SDK_Training)



Flyswatter2 JTAG 디버거의 활용
===
<p align="center">
  <img src="http://d.pr/i/sLeP/5VRPaGJ9+" width="1000" usemap>
</p> 
[Flyswatter2BeagleBoneBlackHowTo-TinCanTools](https://www.tincantools.com/wiki/Flyswatter2_BeagleBone_Black_How_To)

[GDBDebugger-TinCanTools](https://www.tincantools.com/wiki/GDB_Debugger)

[BeagleBoneBlackEclipseandGDB-TinCanTools](https://www.tincantools.com/wiki/BeagleBone_Black_Eclipse_and_GDB)

부팅방법
===
총 **4가지**의 부팅모드를 지원하는데 eMMC Boot, SD Boot, Serial Boot, USB Boot에 대해서 적어본다.

1. **eMMC Boot**...This is the default boot mode and will allow for the fastest boot time.  USB케이블이나 POWER소스로 입력받아 부팅한다.
2. **SD Boot**...This mode will boot from the microSD slot.
유효한 SD카드를 넣고 boot 스위치를 누른채로 부팅한다.
3. **Serial Boot**...This mode will use the serial port to allow downloading of the software direct. SD카드를 꼭 제거해야하며, boot 스위치를 누른채로 부팅한다.
4. **USB Boot**...This mode supports booting over the USB port.
`SD카드`를 꼭 제거해야하며, boot 스위치를 누른채로 부팅한다.

<aside class="notice">
부팅모드의 전환은 리셋버튼에 의해서는 불가능하고 반드시 전원을 내리고 다시 올려야 한다.
</aside>

<aside class="notice">
Software to support USB and serial boot modes is not provided by beagleboard.org.
Please contact TI for support of this feature.
</aside>



X-Loader(U-BOOT's SPL) 소스 컴파일
===

## 방법1
MLO(u-boot-v2015.10-rc2) 파일의 구성 목록

```shell
├── arch
│   └── arm
│       ├── cpu
│       │   ├── armv7
│       │   │   ├── am33xx
│       │   │   │   ├── board.o
│       │   │   │   ├── built-in.o
│       │   │   │   ├── clock.o
│       │   │   │   ├── clock_am33xx.o
│       │   │   │   ├── ddr.o
│       │   │   │   ├── emif4.o
│       │   │   │   ├── mux.o
│       │   │   │   └── sys_info.o
│       │   │   ├── built-in.o
│       │   │   ├── cache_v7.o
│       │   │   ├── cp15.o
│       │   │   ├── cpu.o
│       │   │   ├── lowlevel_init.o
│       │   │   ├── omap-common
│       │   │   │   ├── boot-common.o
│       │   │   │   ├── built-in.o
│       │   │   │   ├── lowlevel_init.o
│       │   │   │   ├── mem-common.o
│       │   │   │   ├── omap-cache.o
│       │   │   │   ├── reset.o
│       │   │   │   ├── timer.o
│       │   │   │   └── utils.o
│       │   │   ├── start.o
│       │   │   └── syslib.o
│       │   └── built-in.o
│       └── lib
│           ├── built-in.o
│           ├── cache-cp15.o
│           ├── cache.o
│           ├── crt0.o
│           ├── eabi_compat.o
│           ├── interrupts.o
│           ├── lib.a
│           ├── reset.o
│           ├── sections.o
│           ├── spl.o
│           ├── stack.o
│           └── vectors.o
├── board
│   └── ti
│       └── am335x
│           ├── board.o
│           ├── built-in.o
│           └── mux.o
├── common
│   ├── aboot.o
│   ├── built-in.o
│   ├── cli.o
│   ├── cli_readline.o
│   ├── cli_simple.o
│   ├── cmd_disk.o
│   ├── cmd_nvedit.o
│   ├── command.o
│   ├── console.o
│   ├── dlmalloc.o
│   ├── env_common.o
│   ├── fb_mmc.o
│   ├── image-android.o
│   ├── image-fdt.o
│   ├── image.o
│   ├── malloc_simple.o
│   ├── memsize.o
│   ├── s_record.o
│   ├── spl
│   │   ├── built-in.o
│   │   ├── spl.o
│   │   ├── spl_ext.o
│   │   ├── spl_fat.o
│   │   ├── spl_mmc.o
│   │   └── spl_ymodem.o
│   ├── stdio.o
│   └── xyzModem.o
├── disk
│   ├── built-in.o
│   ├── part.o
│   ├── part_dos.o
│   └── part_efi.o
├── drivers
│   ├── gpio
│   │   ├── built-in.o
│   │   └── omap_gpio.o
│   ├── i2c
│   │   ├── built-in.o
│   │   ├── i2c_core.o
│   │   ├── muxes
│   │   │   └── built-in.o
│   │   └── omap24xx_i2c.o
│   ├── mmc
│   │   ├── built-in.o
│   │   ├── mmc.o
│   │   └── omap_hsmmc.o
│   ├── power
│   │   ├── built-in.o
│   │   ├── pmic
│   │   │   ├── built-in.o
│   │   │   ├── pmic_tps65217.o
│   │   │   └── pmic_tps65910.o
│   │   └── regulator
│   │       └── built-in.o
│   ├── serial
│   │   ├── built-in.o
│   │   ├── ns16550.o
│   │   ├── serial.o
│   │   └── serial_ns16550.o
│   ├── usb
│   │   └── musb-new
│   │       ├── built-in.o
│   │       ├── musb_core.o
│   │       ├── musb_dsps.o
│   │       ├── musb_gadget.o
│   │       ├── musb_gadget_ep0.o
│   │       ├── musb_host.o
│   │       └── musb_uboot.o
│   └── watchdog
│       ├── built-in.o
│       └── omap_wdt.o
├── fs
│   ├── built-in.o
│   ├── ext4
│   │   ├── built-in.o
│   │   ├── dev.o
│   │   ├── ext4_common.o
│   │   └── ext4fs.o
│   └── fat
│       ├── built-in.o
│       └── fat_write.o
├── include
│   └── autoconf.mk
├── lib
│   ├── built-in.o
│   ├── crc16.o
│   ├── crc32.o
│   ├── ctype.o
│   ├── display_options.o
│   ├── div64.o
│   ├── errno.o
│   ├── hang.o
│   ├── hashtable.o
│   ├── libfdt
│   │   ├── built-in.o
│   │   ├── fdt.o
│   │   ├── fdt_addresses.o
│   │   ├── fdt_empty_tree.o
│   │   ├── fdt_region.o
│   │   ├── fdt_ro.o
│   │   ├── fdt_rw.o
│   │   ├── fdt_strerror.o
│   │   ├── fdt_sw.o
│   │   └── fdt_wip.o
│   ├── linux_compat.o
│   ├── linux_string.o
│   ├── slre.o
│   ├── string.o
│   ├── time.o
│   ├── uuid.o
│   └── vsprintf.o
├── u-boot-spl
├── u-boot-spl.bin
├── u-boot-spl.cfg
├── u-boot-spl.lds
└── u-boot-spl.map

31 directories, 135 files
```

## 방법2  
Did you try linaro-uboot  
: [https://launchpad.net/u-boot-linaro/trunk/13.01/+download/u-boot-linaro-2013.01.1.tar.gz](https://launchpad.net/u-boot-linaro/trunk/13.01/+download/u-boot-linaro-2013.01.1.tar.gz) ?  

I see that it has the config: am335x_evm_config

Please use the patch from below link before compiling u-boot:

[http://permalink.gmane.org/gmane.comp.boot-loaders.u-boot/145116](http://permalink.gmane.org/gmane.comp.boot-loaders.u-boot/145116)

I used its MLO for my BBB board. Hope this could help :)

참조 
[http://www.embedded-bits.co.uk/2011/writeanmlo/](http://www.embedded-bits.co.uk/2011/writeanmlo/)

기트(GIT)의 활용
===
[http://processors.wiki.ti.com/index.php/Linux_Training:Introduction_Git](http://processors.wiki.ti.com/index.php/Linux_Training:Introduction_Git)


부팅장애발생 해결
===
[http://elinux.org/BeagleBoardRecovery](http://elinux.org/BeagleBoardRecovery)

LED 정의
===

| LED | 설명 
| :-----: | :-----
| **USR0** | blink in a heartbeat pattern
| **USR1** | light during microSD card accesses
| **USR2** | during CPU activity
| **USR3** | light during eMMC accesses

<p align="center">
    <img src="http://d.pr/i/b54S/4ulCsT79+" width="1000" usemap>
</p>

프로젝트 :: LED
===
<p align="center">
    <img src="http://d.pr/i/bhYe/TDbfvCNc+" width="1000" usemap>
</p>

프로젝트 :: 7세그먼트
===

<p align="center">
  <img src="http://d.pr/i/UkOh/4WCGZDUZ+" width="1000" usemap>
</p>


<p align="center">
    <img src="http://d.pr/i/ZFwS/NSOTyGWw+" width="1000" usemap>
</p>

<p align="center">
    <img src="http://d.pr/i/oE2O/1X2NtCHm+" width="1000" usemap>
</p>

Beaglebone & Motors
===
[https://www.safaribooksonline.com/library/view/beaglebone-cookbook/9781491915660/ch04.html](https://www.safaribooksonline.com/library/view/beaglebone-cookbook/9781491915660/ch04.html)

WDT(워치도그타이머)
===
7세그먼트 프로젝트 진행시 48초에서 항상 리셋(RESET)이 목격되었다.
WDT에 의한 리셋(RESET)임을 확인하였고, 다음과 같이 문제를 수정한다.

```c
static void prvSetupHardware( void )
{

  /* Initialize GPIOs */

    /* BONE */
    /* Enabling the GPIO0 and GPIO1 clocks */
    (*(REG32(PRCM_REG + CM_PER_GPIO1_CLKCTRL))) =0x2;
. . .
  /* Disable WatchDog */ 
  (*(REG32(WDT_BASE + WDT_WSPR))) = 0xAAAA; // WDT Disable Sequence #1
  while( (*(REG32(WDT_BASE + WDT_WWPS))) & (1<<4) ); //wait till Write pending ready
  (*(REG32(WDT_BASE + WDT_WSPR))) = 0x5555; // WDT Disable Sequence #2
  while( (*(REG32(WDT_BASE + WDT_WWPS))) & (1<<4) ); //wait till Write pending ready
  (*(REG32(WDT_BASE + WDT_WLDR))) = 0x0;
. . .

```


-fomit-frame-pointer의 의미
===

일반적인 컴파일을 수행했을 때의 모습  

```c
 10 static void vBlink(void)
 11 {
 12         unsigned int msDelay= 6;
 13 
 14         serial_puts(msDelay,"blinktask\n");
 15 }
```

arm-none-eabi-gcc -S blink.c

```c
  1         .cpu arm7tdmi-s
  2         .fpu softvfp
  3         .eabi_attribute 20, 1
  4         .eabi_attribute 21, 1
  5         .eabi_attribute 23, 3
  6         .eabi_attribute 24, 1
  7         .eabi_attribute 25, 1
  8         .eabi_attribute 26, 1
  9         .eabi_attribute 30, 6
 10         .eabi_attribute 18, 4
 11         .file   "blink.c"
 12         .section        .rodata
 13         .align  2
 14 .LC0:
 15         .ascii  "blinktask\012\000"
 16         .text
 17         .align  2
 18         .type   vBlink, %function
 19 vBlink:
 20         @ Function supports interworking.
 21         @ args = 0, pretend = 0, frame = 8
 22         @ frame_needed = 1, uses_anonymous_args = 0
 23         stmfd   sp!, {fp, lr}
 24         add     fp, sp, #4
 25         sub     sp, sp, #8
 26         mov     r3, #6
 27         str     r3, [fp, #-8]
 28         ldr     r0, [fp, #-8]
 29         ldr     r1, .L2
 30         bl      serial_puts
 31         sub     sp, fp, #4
 32         ldmfd   sp!, {fp, lr}
 33         bx      lr
 34 .L3:
 35         .align  2
 36 .L2:
 37         .word   .LC0
 38         .size   vBlink, .-vBlink
 39         .section        .rodata
 40         .align  2
 41 .LC1:
 42         .ascii  "Starting BeagleBone\012\000"
 43         .text
 44         .align  2
 45         .global m 
```

프레임 포인터(fp)을 생략한 버전
arm-none-eabi-gcc -S blink.c -fomit-frame-pointer

```c
 19 vBlink:
 20         @ Function supports interworking.
 21         @ args = 0, pretend = 0, frame = 8
 22         @ frame_needed = 0, uses_anonymous_args = 0
 23         str     lr, [sp, #-4]!
 24         sub     sp, sp, #12
 25         mov     r3, #6
 26         str     r3, [sp, #4]
 27         ldr     r0, [sp, #4]
 28         ldr     r1, .L2
 29         bl      serial_puts
 30         add     sp, sp, #12
 31         ldr     lr, [sp], #4
 32         bx      lr
```

Linux Kernel and Driver Development Training
===

## 리눅스 커널소스 얻기  
[TheLinuxKernelArchives](https://www.kernel.org/)

### 1. tarball  
The kernel sources are available from [http://kernel.org/pub/linux/kernel](http://kernel.org/pub/linux/kernel)

### 2. git  
Fetch the entire kernel sources and history  

```bash
git clone git://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git
```

### 3. web  
Web interface available at [http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/.](http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/.)


Fritz 부품 편집(추가)
===
1. 기존 부품을 선택하여 수정한다(명칭, 핀수)
2. BREADBOARD, ICON, SCHEMATIC, PCB 등을 잉크스케이프(WIN32) 도구를 이용하여 편집한다
3. CONNECT 을 편집한다
불필요한 핀(PIN)들은 상단 메뉴(BREADBOARD, SCHEMATIC, PCB, ICON, Metadata, Connector ) 중 Connector에서 제거하면 되는데, 이는 제일 마지막 작업에서 수행한다.


TODO 리스트
===

##  워크샵 1~5일 목차 샘플예  
Workshop Outline  

* Day 1  
  - Lecture 1: Booting Linux  
    Lab 1: Booting Linux via mini-SD Card
  - Lecture 2: Linux Distriubtions and Arago  
    Lab 2: Using the Linux Terminal
  - Lecture 3: Using OpenEmbedded  
    Lab 3: Application Recipe for Bitbake
  - Lecture 4: Application build and debug  
    Lab 4: Using Code Composer Studio version 5

* Day 2
  - Lecture 5: File Manipulation  
    Lab 5: Manipulating GPIO/LED via virtual files
  - Lecture 6: Linux Device Drivers  
    Lab 6: UART Driver read/write
  - Lecture 7: Linux Scheduler  
    Lab 7: pthreads and semaphores
  - Lecture 8: Networking Basics  
    Lab 8: Berkeley Sockets Programming

* Day 3  
  - Lecture 9: Linux Graphics and Video Drivers  
    Lab 9: Driving the LCD with FBDEV Driver
  - Lecture 10: On-Screen Display Development  
    Lab 10: Using Qtopia (qt) to develop a GUI
  - Lecture 11: Using git versioning software  
    Lab 11: Exploring git

## BeagleBoardUbuntu로 시작하기  
[http://elinux.org/Beagleboard:Booting_Ubuntu_on_BeagleBoard_Black](http://elinux.org/Beagleboard:Booting_Ubuntu_on_BeagleBoard_Black)  
[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)  
[http://aiui.tistory.com/12](http://aiui.tistory.com/12)  
[http://egloos.zum.com/entireboy/v/4826166](http://egloos.zum.com/entireboy/v/4826166)  
[http://www.armhf.com/boards/beaglebone-black/](http://www.armhf.com/boards/beaglebone-black/)  
[http://rayhightower.com/blog/2014/01/02/beaglebone-black-ubuntu-part-1/](http://rayhightower.com/blog/2014/01/02/beaglebone-black-ubuntu-part-1/)  
[http://derekmolloy.ie/building-angstrom-for-beaglebone-from-source/](http://derekmolloy.ie/building-angstrom-for-beaglebone-from-source/)  
[http://elinux.org/BeagleBoardUbuntu](http://elinux.org/BeagleBoardUbuntu)  
[https://eewiki.net/display/linuxonarm/BeagleBone](https://eewiki.net/display/linuxonarm/BeagleBone)  

<p align="center">
    <img src="http://d.pr/i/MpKl/1zICletA+" width="1000" usemap>
</p>

## 프로젝트 :: 리모트컨트롤  
비글보드의 eCAP(Input Capture)을 이용한 프로젝트 기획

## FreeBSD for BeagleBoneBlack  
[FreeBSD/arm/BeagleBoneBlack-FreeBSDWiki](https://wiki.freebsd.org/FreeBSD/arm/BeagleBoneBlack "       FreeBSD")

[FreeBSD for BeagleBoneBlack](ftp://ftp.freebsd.org/pub/FreeBSD/snapshots/arm/armv6/ISO-IMAGES/ "       익명으로 로그인")

## BeagleBoneBlack's Capes  
[Beagleboard:BeagleBoneCapes-eLinux.org](http://elinux.org/Beagleboard:BeagleBone_Capes)

## Beagleboard:Android  
[Beagleboard:Android-eLinux.org](http://elinux.org/Beagleboard:Android)

## Beagleboard:MicroSD As Extra Storage  
[Beagleboard:MicroSDAsExtraStorage-eLinux.org](http://elinux.org/Beagleboard:MicroSD_As_Extra_Storage)

## Beagleboard:BoneScript  
[Beagleboard:BoneScript-eLinux.org](http://elinux.org/Beagleboard:BoneScript)

## Beagleboard:LCD  
[CircuitCo:BeagleBoneLCD7-eLinux.org](http://elinux.org/CircuitCo:BeagleBone_LCD7)

부록1.beaglebone 으로 할 수 있는 것들
===

## 메모리제어기  

## 네트워크  
* TCP/IP 네트워크 포팅

## PWM  
* BEEP Generator

## INPUT CAPTURE  
* 리모컨 센서

## MMC  
* FAT 파일 시스템 포팅

## I2C  
* EEPROM 읽기
* TPS65217C

## SPI  

## UART  
한국

## GPIO  
* 7-SEGMENT

## TIMER  
* RTOS 시계

## RTC  
* 시계
* 달력

## WDT  
* 시스템 감시


부록2.beaglebone 깃허브 오픈소스 조사결과  
===

[https://github.com/RobertCNelson](https://github.com/RobertCNelson) <-- 대표 사이트  
[https://github.com/Avedo/Beaglebone/blob/master/arch4bone.sh](https://github.com/Avedo/Beaglebone/blob/master/arch4bone.sh "아치리눅스") <-- 아치리눅스  
[https://github.com/bikerglen/beagle](https://github.com/bikerglen/beagle "single SparkFun / Adafruit 32x32 LED panel") <-- single SparkFun / Adafruit 32x32 LED panel  
[https://github.com/bradfa/beaglebone_pinmux_tables](https://github.com/bradfa/beaglebone_pinmux_tables "BeagleBone Pin Mux Tables 정보") <-- BeagleBone Pin Mux Tables 정보  
[https://github.com/cp15/openwrt-bbb](https://github.com/cp15/openwrt-bbb "비글본 기반 openwrt-bbb") <-- 비글본 기반 openwrt-bbb  
[https://github.com/dalmago/beaglebone](https://github.com/dalmago/beaglebone "net Over USB") <-- net Over USB  
[https://github.com/derekmolloy/exploringBB](https://github.com/derekmolloy/exploringBB "www.exploringbeaglebone.com 샘플예제") <-- www.exploringbeaglebone.com 샘플예제  
[https://github.com/fivdi/bot-io](https://github.com/fivdi/bot-io "노드js로 제어") <-- 노드js로 제어  
[https://github.com/fvdbosch/BeagleboneBlackRadio](https://github.com/fvdbosch/BeagleboneBlackRadio "FM/Internet Radio combo") <-- FM/Internet Radio combo  
[https://github.com/gkaindl/beaglebone-ubuntu-scripts](https://github.com/gkaindl/beaglebone-ubuntu-scripts "우분투개발환경설치스크립트") <-- 우분투개발환경설치스크립트  
[https://github.com/greghaynes/BeagleDrone](https://github.com/greghaynes/BeagleDrone "비글본 드론(DRONE)") <-- 비글본 드론(DRONE)  
[https://github.com/henfos/BBBFreeRTOS](https://github.com/henfos/BBBFreeRTOS "FreeRTOS") <-- FreeRTOS  
[https://github.com/jadonk/beaglebone-getting-started](https://github.com/jadonk/beaglebone-getting-started "맥(Mac) 개발환경 구축") <-- 맥(Mac) 개발환경 구축  
[https://github.com/jadonk/buildroot](https://github.com/jadonk/buildroot "Buildroot for BeagleBone") <-- Buildroot for BeagleBone  
[https://github.com/JavaWantaBe/beagleboneRTC](https://github.com/JavaWantaBe/beagleboneRTC "외부 RTC") <-- 외부 RTC  
    <del>[https://github.com/jerrinsg/RTOS_Bone](https://github.com/jerrinsg/RTOS_Bone "FreeRTOS") <-- FreeRTOS</del>  
[https://github.com/johncobb/watchdog](https://github.com/johncobb/watchdog "Watchdog") <-- Watchdog  
[https://github.com/julianduque/beaglebone-io](https://github.com/julianduque/beaglebone-io "IO Plugin for Johnny-Five") <-- IO Plugin for Johnny-Five  
[https://github.com/keesj/bonecode](https://github.com/keesj/bonecode "bone_mmc") <-- bone_mmc  
[https://github.com/lamunozh/BeagleBone](https://github.com/lamunozh/BeagleBone "Python applications") <-- Python applications  
[https://github.com/lucab0ni/BeagleBoneBlack_Android](https://github.com/lucab0ni/BeagleBoneBlack_Android "BeagleBoneBlack_Android") <-- BeagleBoneBlack_Android  
[https://github.com/magyarm/beaglebone-fpga](https://github.com/magyarm/beaglebone-fpga "beaglebone-fpga") <-- beaglebone-fpga  
[https://github.com/mini-distribution/cross-beaglebone](https://github.com/mini-distribution/cross-beaglebone "크로스컴파일 cross-beaglebone") <-- 크로스컴파일 cross-beaglebone  
[https://github.com/mluckham54/openocd_bbb](https://github.com/mluckham54/openocd_bbb "OpenOCD") <-- OpenOCD  
[https://github.com/Mras2an/Webcam-IP-BeagleBone](https://github.com/Mras2an/Webcam-IP-BeagleBone "Webcam-IP") <-- Webcam-IP  
[https://github.com/NicoEmbed/BeagleBoneBuildingAutomation](https://github.com/NicoEmbed/BeagleBoneBuildingAutomation "BeagleBoneBuildingAutomation") <-- BeagleBoneBuildingAutomation  
[https://github.com/notnyt/beaglebone](https://github.com/notnyt/beaglebone "Ruby Library") <-- Ruby Library  
[https://github.com/photomankc/BeagleBone-Black-Robot-Library](https://github.com/photomankc/BeagleBone-Black-Robot-Library "robot project") <-- robot project  
[https://github.com/piranha32/beaglebone-pinmux-tool/tree/master/doc](https://github.com/piranha32/beaglebone-pinmux-tool/tree/master/doc "pinmux-tool") <-- pinmux-tool  
[https://github.com/PuggleBoard/PuggleLinux](https://github.com/PuggleBoard/PuggleLinux "Real-Time Linux operating system") <-- Real-Time Linux operating system  
[https://github.com/retrospectivelyobvious/beaglebone-basics](https://github.com/retrospectivelyobvious/beaglebone-basics "Getting Started with the BeagleBone") <-- Getting Started with the BeagleBone  
[https://github.com/rookie/beaglebone-poweroff](https://github.com/rookie/beaglebone-poweroff "power off kernel patch") <-- power off kernel patch  
[https://github.com/rutles/bbb](https://github.com/rutles/bbb "BeagleBone Black handling several examples") <-- BeagleBone Black handling several examples  
[https://github.com/saimusdev/bone-rt](https://github.com/saimusdev/bone-rt "RT Kernel") <-- RT Kernel  
[https://github.com/shahidhk/beagleboneblack](https://github.com/shahidhk/beagleboneblack "Library for Beagle Bone Black") <-- Library for Beagle Bone Black  
[https://github.com/spbnick/bbb-poke](https://github.com/spbnick/bbb-poke "BeagleBone Black hardware") <-- BeagleBone Black hardware  
    <del>[https://github.com/steve-kim/BeagleBone](https://github.com/steve-kim/BeagleBone "FreeRTOS") <-- FreeRTOS </del>  
[https://github.com/topnotcher/beaglebone-gpio](https://github.com/topnotcher/beaglebone-gpio "mmaped GPIO") <-- mmaped GPIO  
[https://github.com/ungureanuvladvictor/BeagleBoneBlack-USBFlasher](https://github.com/ungureanuvladvictor/BeagleBoneBlack-USBFlasher "USBFlasher") <-- USBFlasher  
[https://github.com/wytalfred/beaglebone-mag-scope](https://github.com/wytalfred/beaglebone-mag-scope "LCD mag-scope") <-- LCD mag-scope  
[https://github.com/yixuaning/BeagleBone-Black-7.0](https://github.com/yixuaning/BeagleBone-Black-7.0 "TI SDK 7.0") <-- TI SDK 7.0  
[https://github.com/ajaykumarkannan/Beaglebone-I2C](https://github.com/ajaykumarkannan/Beaglebone-I2C "I2C") <-- I2C  
[https://github.com/guileschool/BeagleBoard-exercises](https://github.com/guileschool/BeagleBoard-exercises "BeagleBoard-exercises") <-- 풍부한 예제 제공  


부록3.비 깃허브(Others)
===

[http://omappedia.org/wiki/Bootloader_Project](http://omappedia.org/wiki/Bootloader_Project)  
[https://android.googlesource.com/kernel/lk/+/upstream-master/platform/am335x/ti/drivers/](https://android.googlesource.com/kernel/lk/+/upstream-master/platform/am335x/ti/drivers/ "디바이스드라이버") <-- 디바이스드라이버  


부록4.비글본 자료 링크
===
[http://www.jann.cc/2014/12/04/yocto_project_developer_day_2014.html](http://www.jann.cc/2014/12/04/yocto_project_developer_day_2014.html)  
[http://processors.wiki.ti.com/index.php/AM335x_Trace](http://processors.wiki.ti.com/index.php/AM335x_Trace "AM335x_Trace")  
[http://processors.wiki.ti.com/index.php/AM335x_EMIF_Configuration_tips](http://processors.wiki.ti.com/index.php/AM335x_EMIF_Configuration_tips "AM335x_EMIF")  
[http://processors.wiki.ti.com/index.php/AM335x_Software_Design_Guide](http://processors.wiki.ti.com/index.php/AM335x_Software_Design_Guide "AM335x_Software_Design_Guide")  
[http://www.ti.com/tool/tmdxevm3358](http://www.ti.com/tool/tmdxevm3358 "AM335x Evaluation Module")  
[http://processors.wiki.ti.com/index.php/AM335x_U-Boot_User%27s_Guide](http://processors.wiki.ti.com/index.php/AM335x_U-Boot_User%27s_Guide "AM335x U-Boot User's Guide")  
[http://processors.wiki.ti.com/index.php?title=AM_McSpi&redirect=no](http://processors.wiki.ti.com/index.php?title=AM_McSpi&redirect=no "AM335x McSpi")  
[http://processors.wiki.ti.com/index.php/Linux_Core_PWM_User's_Guide](http://processors.wiki.ti.com/index.php/Linux_Core_PWM_User's_Guide "PWM")  
[http://beagleboard.org/Support/bone101/#cloud9](http://beagleboard.org/Support/bone101/#cloud9 "cloud9")  
[http://elinux.org/BeagleBoardBeginners](http://elinux.org/BeagleBoardBeginners)  
[https://eewiki.net/display/linuxonarm/BeagleBone+Black](https://eewiki.net/display/linuxonarm/BeagleBone+Black)  
[https://www.eewiki.net/display/AOA/BeagleBone%20Black](https://www.eewiki.net/display/AOA/BeagleBone%20Black)  
[http://janaxelson.com/beaglebone.htm](http://janaxelson.com/beaglebone.htm)  
[http://www.embeddedhobbyist.com](http://www.embeddedhobbyist.com)  
[https://github.com/macchina-io/macchina.io](https://github.com/macchina-io/macchina.io)  
[https://github.com/pocoproject/poco](https://github.com/pocoproject/poco)  


부록5.전자 부품 쇼핑몰
===
[Radioshack - Home](http://www.radioshack.com)  
[Adafruit Industries, Unique & fun DIY electronics and kits](https://www.adafruit.com)  
[SparkFun Electronics](https://www.sparkfun.com)  
[mouser](http://www.mouser.com)  
[Maker Shed: Arduino - Raspberry Pi - 3D Printers - Microcontroller Kit](http://www.makershed.com)  

This endpoint retrieves a specific kitten.  

<aside class="warning">If you're not using an administrator API key, note that some kittens will return 403 Forbidden if they are hidden for admins only.</aside>  


부록6.FAQ
===

## "Attempt to erase non block-aligned data" 에러 메시지의 원인과 해결방안  
[https://e2e.ti.com/support/arm/sitara_arm/f/791/t/342667](https://e2e.ti.com/support/arm/sitara_arm/f/791/t/342667)  

(증상)  

```bash
Bytes transferred = 28616 (6fc8 hex)                                                        
U-Boot# setenv bootcmd 'tftp ${fdtaddr} rtosdemo.bin'                                       
U-Boot# setenv bootcmd 'tftp ${fdtaddr} rtosdemo.bin; bootz 0x88000000'                     
U-Boot# saveenv                                                                             
Saving Environment to NAND...                                                               
Erasing NAND...                                                                             
Attempt to erase non block-aligned data                                                     
U-Boot# reset                                                                               
resetting ...   
```

(원인과 해결방안)  
환경변수를 저장하기 위한 NAND 에 문제가 발생하였슴.
대체 방안으로 uEnv.txt 에 환경변수를 정의 할 것.


### HTTP Request  

`GET http://example.com/kittens/<ID>`

### URL Parameters  
Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

# 부록7.SyntaxHighlighter3
<pre class="brush: cpp; highlight: [3,6,11,12,15,16,17,18,19]; title: ; notranslate" title="">
uint8_t CDC1_SendDataBlock(uint8_t *data, uint16_t dataSize)
{
  TMOUT1_CounterHandle timeout;
  uint8_t res = ERR_OK;

  transactionOngoing = TRUE;
  if (USB_Class_CDC_Interface_DIC_Send_Data(CONTROLLER_ID, data, dataSize)!=USB_OK) {
    transactionOngoing = FALSE;
    return ERR_FAULT;
  }
  /* wait for transaction finish */
  timeout = TMOUT1_GetCounter(50/TMOUT1_TICK_PERIOD_MS); /* set up timeout counter */
  while(transactionOngoing) { /* wait until transaction is finished */
    CDC1_RunUsbEngine();
    if (TMOUT1_CounterExpired(timeout)) {
      res = ERR_FAILED;
      break;
    }
    WAIT1_WaitOSms(5); /* wait some time */
  }
  TMOUT1_LeaveCounter(timeout); /* return timeout counter */
  return res;
}
</pre>


