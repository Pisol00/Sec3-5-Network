#  Aircard Adapter คืืออะไร?
Aircard adapter หรือที่เรียกอีกชื่อหนึ่งว่า **USB modem adapter** เป็นอุปกรณ์ที่ใช้ในการเชื่อมต่ออินเทอร์เน็ตผ่านทางสัญญาณเครือข่ายมือถือ ซึ่งสามารถเสียบเข้ากับพอร์ต USB ของคอมพิวเตอร์ได้ มีบางรุ่นที่สามารถใช้งานบน Linux ได้ด้วยการติดตั้ง driver หรือโปรแกรมเสริมต่างๆ
> **การใช้งาน Aircard adapter บน Linux อาจจะมีความซับซ้อนกว่าการใช้งานบนระบบปฏิบัติการอื่น เนื่องจากบางรุ่นอาจจะไม่มี driver ที่เข้ากันได้สำหรับ Linux**


# คุณสมบัติที่ควรมีใน AirCard Adapter

 - สามารถรองรับระบบปฏิบัติการได้หลากหลายระบบ ใช้งานโดยเสียบเข้ากับ Port USB ได้ หรือช่อง PCMCIA ของ Laptop 
 -   สามารถอัพเกรดfirm wareได้ โดยใช้งานได้กับเครือข่าย UMTS / EDGE / GSM
 -   สามารถรองรับซิมของระบบโทรศัพท์มือถือบ้านเราได้ทุกค่าย รองรับระบบ 3G  และ EDGE Class 12  / GPRS Class 12 
 -   รองรับการใช้งาน Voice หรือส่ง SMS
 -   รองรับการใช้งานด้านโทรศัพท์ และการใช้งานแฟ็กซ์

# วิธีติดตั้ง Aircard Adapter บน linux

 **1. ตรวจสอบความเข้ากันได้ :** ก่อนที่จะซื้อ Aircard adapter ให้ตรวจสอบว่ารุ่นนั้นสามารถใช้งานกับ Linux ได้หรือไม่ โดยการตรวจสอบในเว็บไซต์ของผู้ผลิตหรือในฐานข้อมูลที่รวบรวมข้อมูลเกี่ยวกับการใช้งานอุปกรณ์บน Linux เช่น Linux Hardware Compatibility List (Linux HCL) หรือ Linux Wireless LAN Support.
 **2.ติดตั้ง Driver:** หาก Aircard adapter มาพร้อมกับ driver สำหรับ Linux ให้ทำการติดตั้งโดยใช้คำสั่งใน terminal โดยส่วนมากจะเป็นการใช้คำสั่ง
 
    sudo make install

   หรือ
   

    sudo ./configure && make && make install
>โดยใช้ไฟล์ติดตั้งที่มากับ driver
>**ส่วนมากdriver จะถูกติดตั้งมาโดยอัตโนมัติอยู่แแล้ว แต่ถ้าเป็นกรณีที่จำเป็นต้องติดตั้งdriver ก็สามารถทำได้ดังนี้**
## How to download driver

|      ****Kernel version****          |****Driver Version****                        |****TRU-Install Patch****                       |
|----------------|-------------------------------|-----------------------------|
|2.6.20|[v.1.7.40](https://www.downloads.netgear.com/files/aircard/v1.7.40_kernel-2.6.32.serial.tar)          |[patch](https://www.downloads.netgear.com/files/aircard/patch-swoc-temp-unusualdevs-only.zip)           |
|2.6.21          |[v.1.7.40](https://www.downloads.netgear.com/files/aircard/v1.7.40_kernel-2.6.32.serial.tar)          |[patch](https://www.downloads.netgear.com/files/aircard/patch-swoc-temp-unusualdevs-only.zip)          |
|2.6.22       |[v.1.7.40](https://www.downloads.netgear.com/files/aircard/v1.7.40_kernel-2.6.32.serial.tar)|[patch](https://www.downloads.netgear.com/files/aircard/patch-swoc-temp-unusualdevs-only.zip)|
|2.6.23       |[v.1.7.40](https://www.downloads.netgear.com/files/aircard/v1.7.40_kernel-2.6.32.serial.tar)|Not required
|2.6.24       |[v.1.7.40](https://www.downloads.netgear.com/files/aircard/v1.7.40_kernel-2.6.32.serial.tar)|Not required
|2.6.24       |[v.1.7.40](https://www.downloads.netgear.com/files/aircard/v1.7.40_kernel-2.6.32.serial.tar)|Not required
|2.6.25       |[v.1.7.40](https://www.downloads.netgear.com/files/aircard/v1.7.40_kernel-2.6.32.serial.tar)|Not required
|2.6.26       |[v.1.7.40](https://www.downloads.netgear.com/files/aircard/v1.7.40_kernel-2.6.32.serial.tar)|Not required
|2.6.27       |[v.1.7.40](https://www.downloads.netgear.com/files/aircard/v1.7.40_kernel-2.6.32.serial.tar)|Not required
|2.6.28       |[v.1.7.40](https://www.downloads.netgear.com/files/aircard/v1.7.40_kernel-2.6.32.serial.tar)|Not required
|2.6.29       |[v.1.7.40](https://www.downloads.netgear.com/files/aircard/v1.7.40_kernel-2.6.32.serial.tar)|Not required
|2.6.30       |[v.1.7.40](https://www.downloads.netgear.com/files/aircard/v1.7.40_kernel-2.6.32.serial.tar)|Not required
|2.6.31       |[v.1.7.40](https://www.downloads.netgear.com/files/aircard/v1.7.40_kernel-2.6.32.serial.tar)|Not required
|2.6.32       |[v.1.7.40](https://www.downloads.netgear.com/files/aircard/v1.7.40_kernel-2.6.32.serial.tar)|Not required
|2.6.33       |[v.1.7.40](https://www.downloads.netgear.com/files/aircard/v1.7.40_kernel-2.6.32.serial.tar)|Not required
|2.6.34       |[v.1.7.40](https://www.downloads.netgear.com/files/aircard/v1.7.40_kernel-2.6.32.serial.tar)|Not required
|2.6.35       |[v.1.7.40](https://www.downloads.netgear.com/files/aircard/v1.7.40_kernel-2.6.32.serial.tar)|Not required
|2.6.36       |[v.1.7.40](https://www.downloads.netgear.com/files/aircard/v1.7.40_kernel-2.6.32.serial.tar)|Not required
|2.6.38       |[v.1.7.40](https://www.downloads.netgear.com/files/aircard/v1.7.40_kernel-2.6.32.serial.tar)|Not required
|3.0.x       |[v.1.7.40](https://www.downloads.netgear.com/files/aircard/v1.7.40_kernel-2.6.32.serial.tar)|Not required




## How to install driver

ก่อนที่จะติดตั้งไดรเวอร์ คุณต้องดาวน์โหลดโค้ดต้นฉบับของเคอร์เนลลงใน /usr/src/linux ตำแหน่งของโค้ดต้นฉบับของเคอร์เนลจะแตกต่างขึ้นอยู่กับการกระจายของ Linux ของคุณ อย่างไรก็ตาม พอร์ตแพ็คเกจของการกระจาย (เช่น yum, yast, หรือ apt) สามารถช่วยคุณค้นหาได้ (ลองค้นหาในพอร์ตแพ็คเกจเพื่อ "kernel source")

**มาติดตั้งdriverกันเถอะ**

 1. เริ่มต้นโดยเข้าไปที่ไดเรกทอรีที่มีไดรเวอร์ sierra และแยกไฟล์โดยใช้คำสั่งต่อไปนี้
 **bash**
		
        tar -xvf v.x.y.z_kernel2.6.y.tar ( ตัวอย่างเช่น tar -xvf v.1.7.x_kernel2.6.28.tar )
        cd kernel-2.6.y

 2. จากนั้นคอมไพล์และติดตั้งไดรเวอร์ใหม่โดยใช้คำสั่งต่อไปนี้:
**bash**
    `make sudo make install`

(ถ้าถูกต้อง จะมีข้อความให้ป้อนรหัสผ่านที่คุณใช้เข้าสู่ระบบ Linux)
เท่านี้แปลว่า **ไดรเวอร์ถูกติดตั้งแล้ว**

**TRU-Install Patch Instructions**
หากคุณใช้เคอร์เนล 2.6.23 หรือเวอร์ชันใหม่กว่า คุณสามารถข้ามส่วนนี้ได้ 
คุณสามารถตรวจสอบเวอร์ชันเคอร์เนลได้โดยใช้คำสั่ง

    uname -r
เนื่องจากLinux รุ่นเก่ามีปัญหาเกี่ยวกับความเข้ากันได้นี้และต้องใช้แพทช์ หากคุณมีอุปกรณ์ TRU-Install และเคอร์เนลที่ไม่มี TRU-Install คุณจะต้องใช้แพทช์ TRU-Install
>TRU-Install devices: AirCard 597E, USB 598, Compass 597, USB Connect881(AirCard 881U), USB Connect Mercury (Compass 885).

**ขั้นตอนมีดังนี้**

 1. แยกไฟล์เคอร์เนลโดยใช้คำสั่งต่อไปนี้
     **bash**
     `tar -jxf linux-2.6.x.x.tar.bz2`
  
 2. ดาวน์โหลดและแยกไฟล์แพทช์จากที่นี่และนำเข้าไปยังไดเรกทอรีหลักเดียวกันที่คุณแยกไฟล์เคอร์เนลไป
 3. ปรับใช้แพทช์โดยใช้คำสั่งต่อไปนี้
     **bash**
     `cd linux-2.6.x.x patch -p1< ../the-patch-file.patch (ดาวน์โหลดแพทช์ที่นี่ Driver Downloads)`
    
 4. คัดลอกไดรเวอร์ sierra.c ไปยังไดเรกทอรี usbserial (Linux-2.6.x.x/drivers/usb/serial)
 5. คอมไพล์และติดตั้งเคอร์เนล
  **bash**
  `make clean`
   `sudo make modules SUBDIRS=drivers/usb/storage`
   `sudo make modules_install SUBDIRS=drivers/usb/storage`
   
 6. รีบูตและแทรกอุปกรณ์ TRU-Install เข้าไป ควรจะระบุเป็นอุปกรณ์โมเด็ม USB

  

## Example -  How to install driver Huawei aircard 3G /7.2Mb E303

 1. ดาวน์โหลด โปรแกรมที่ใช้ในการตั้งค่า
 
    `sudo apt-get install -y ppp usb-modeswitch`
    `wget "http://downloads.sourceforge.net/p…/vim-n4n0/sakis3g.tar.gz…" -O sakis3g.tar.gz -4`
    `wget "http://zool33.uni-graz.at/…/umtskeeper/src/umtskeeper.tar.gz" -4`
    
 2. แตกไฟล์ที่ดาวน์โหลดมาข้างต้น
 `sudo tar xzvf umtskeeper.tar.gz && sudo tar xzvf sakis3g.tar.gz`
     `sudo chmod +x sakis3g && sudo chmod +x umtskeeper
    usbmodem='lsusb | grep Huawei | cut -d" " -f6' `
    
 3. lsusb เรียกดู ID ของอุปกรณ์ จะเห็นว่าอุปกรณ์ แอร์การ์ดของเรามี ID 12d1:140c ดังนี้
   ![enter image description here](https://3.bp.blogspot.com/-9YR9yiQOZjY/VcG6ewTb5GI/AAAAAAAAWAE/ObAfExhqcg8/s1600/10730804_1013456601998808_413162644410666694_n.jpg)
   Bus 001 Device 006: ID 12d1:140c Huawei Technologies Co., Ltd.
 4. นำ ID ไปใส่ใน USBMODEM=''
 ```
 sudo /home/pi/sakis3g/umtskeeper --sakisoperators "USBINTERFACE='0' 
 OTHER='USBMODEM' USBMODEM='12d1:140c' APN="CUSTOM_APN" CUSTOM_APN="
 [www.dtac.co.th](http://www.dtac.co.th/)" APN_USER='dtac' APN_PASS='dtac'
 " --sakisswitches "--sudo --console" --devicename 'Huawei' --log --nat 'no' --httpserver
 ```
![enter image description here](https://2.bp.blogspot.com/-HALXXANeq-4/VcG6e7qfCWI/AAAAAAAAWAM/Wb4E1oqTk68/s1600/1901578_892867970724339_6402322546612677301_n.jpg)
 5. ถ้ารันแล้วโค๊ดเรียกหาโฟลเดอร์ umtskeeper ให้พิมพ์
 `mkdir ~/umtskeeper`
 รันใหม่อีกครั้ง หรือ รีสตาร์ท sudo reboot แล้วรันใหม่
 
 6. ทดสอบพิมพ์คำสั่ง ping 8.8.8.8 เพื่อทำการ ping ไปยังเว็ป google

    
## How to Connecting the Network

  
เราจะขอกล่าวถึง 3 วิธีในการเชื่อมต่อกับเครือข่าย:

1.  Network Manager
2.  KPPP - หน้าต่าง GUI ที่ใช้กำหนดค่า pppd
3.  การตั้งค่า pppd ด้วยตนเอง

**1.การเชื่อมต่อโดยใช้ Network Manager**

แอปพลิเคชัน Network Manager ได้รวมอยู่ใน Ubuntu 8.10, 9.04, 9.10, 10.4, Fedora 11 ซึ่งเป็นการสนับสนุนของ Linux ในบางกรณี Network Manager บน Linux อาจจะรองรับ Aircard adapter โดยอัตโนมัติ ให้เสียบ Aircard adapter เข้ากับพอร์ต USB และ Network Manager จะตรวจจับอุปกรณ์และเปิดใช้งานอัตโนมัติ หากไม่เปิดใช้งานโดยอัตโนมัติ สามารถใช้คำสั่ง

    sudo service NetworkManager restart
เพื่อรีสตาร์ท Network Manager แต่ถ้าไม่ได้ผล ให้มาลองวิธีต่อไปนี้

 1. เชื่อมต่อกับ Aircard โดยใช้ Terminal ของ Linux โดยใช้คำสั่ง
  `# minicom –s` ที่root
  ไปที่ Serial port Setup และใช้: /dev/ttyUSB2 หรือ /dev/ttyUSB3 ขึ้นอยู่กับโมเด็มและเฟิร์มแวร์
  เพื่อตรวจสอบว่าโมเด็มตอบสนองหรือไม่ พิมพ์ `ati5 `จะแสดงหมายเลข IMEI และ Firmware ของโมเด็ม
  ใช้คำสั่ง` ATE1` เพื่อเปิดใช้งานการแสดงข้อความที่พิมพ์
  
 2. ตั้งค่า APN 
 ตรวจสอบว่ามีโปรไฟล์ถูกสร้างขึ้นหรือไม่โดยใช้คำสั่ง at+cgdcont?
 โดยปกติแล้วการ์ดยี่ห้อต่างๆจะมีโปรไฟล์หมายเลข 1 ถูกสร้างขึ้นมาพร้อมกับ APN มาตรฐานอยู่แล้ว หากไม่มีโปรไฟล์หรือบัญชี SIM ใช้ APN ที่แตกต่างกัน สามารถแก้ไขหรือสร้างโปรไฟล์ใหม่ได้โดยใช้คำสั่ง
  `at+cgdcont=<pid>,"IP","APN"`
  โดยที่ "PID" คือรหัสของโปรไฟล์ที่ระบุโปรไฟล์ โดยทั่วไปจะเป็นโปรไฟล์หมายเลข 1
  
      โมเด็มควรตอบกลับด้วยข้อความ "OK" ในกรณีที่สำเร็จ
      เช่น
```
    AT&T: at+cgdcont=1,”IP”,”broadband”

    Telstra: at+cgdcont=1,”IP”,”Telstra.internet”

    Rogers LTE: at+cgdcont=1,”IP”,”lteinternet.apn “

    Rogers: at+cgdcont=1,”IP”,”internet.com “

    Telus: at+cgdcont=1,"IP","isp.telus.com"

    Bell: at+cgdcont=1,"IP","inet.bell.ca"
```    

> **Optional step** ตั้งค่าวิธีการยืนยันตัวตน (Authentication method) โดยใช้คำสั่ง
>`AT$QCPDPP=1,1,"password","username"`

 3. เปิดใช้งานเราดิโอด้วยคำสั่ง
 ```
 at+cfun =1
 ```
 
 4. สร้างการเชื่อมต่อแบบด้วยตนเองโดยใช้คำสั่ง
  ```
 at!scact=1,<pid> (เพื่อเชื่อมต่อ) 
 at!scact=0,<pid> (เพื่อตัดการเชื่อมต่อ)
 ```
 Aircard สามารถเชื่อมต่อโดยอัตโนมัติหลังจากเปิดใช้งานหรือรีเซ็ตโดยใช้โปรไฟล์เริ่มต้น
 เพื่อตั้งโปรไฟล์เริ่มต้นใช้คำสั่งต่อไปนี้: `at!scdftprof=<pid>`
 คุณสามารถเปิดใช้งานการเชื่อมต่ออัตโนมัติในโปรไฟล์เริ่มต้นโดยใช้คำสั่ง:
 `at!scprof=<pid>,"",1,0,0,0`
 
 5.ที่อยู่ IP ที่ได้รับจากผู้ให้บริการ
 
 เพื่อตรวจสอบที่อยู่ IP ที่โมเด็มได้รับจากเครือข่าย ให้ใช้คำสั่ง
 `at!scpaddr=<pid>`
 ตัวอย่างเช่นเพื่อตรวจสอบที่อยู่ IP ในโปรไฟล์หมายเลข 1 ใช้คำสั่ง
  `at!scpaddr=1`  
  
 6.การส่งผ่านที่อยู่ IP ไปยังคอมพิวเตอร์

ขึ้นอยู่กับโมเด็ม บางครั้งอาจจะไม่ได้เปิดใช้งาน DHCP ผ่านซอฟต์แวร์ของโมเด็มไว้ โดย Network Manager จะดูแลขั้นตอนนี้ แต่หากคุณต้องการใช้คำสั่งผ่าน Command Line คุณอาจต้องใช้คำสั่งต่อไปนี้ในหน้าต่าง Terminal ของ Linux อื่น
```
#ifconfig wwan0 up **  
#ifup wwan0  
#ifconfig
```
จะแสดงอินเตอร์เฟส wwan0 พร้อมที่อยู่ IP เหมือนกับที่แสดงในขั้นตอนที่ 5.

> หากแสดงข้อผิดพลาด "interface wwan0 not configured" เราขอแนะนำให้เพิ่มบรรทัดต่อไปนี้ในไฟล์อินเตอร์เฟสที่ตั้งอยู่ที่: /etc/network/interfaces โดยใช้โปรแกรมแก้ไขข้อความใดก็ได้
```
auto wwan0 
iface wwan0 inet dhcp
```

 7. สรุป
 สรุปคำสั่งเพื่อสร้างโปรไฟล์และ**เชื่อมต่อด้วยตนเอง(manual)**โดยใช้โปรไฟล์หมายเลข 3
```
at+cfun=1

at+cgdcont=3,"IP","CustomAPN"

at!scdftprof=3

at!scprof=3,"",0,0,0,0

at!scact=1,3

at!scpaddr=3
```
 สรุปคำสั่งเพื่อสร้างโปรไฟล์หมายเลข 3 และใช้คุณลักษณะ **Auto Connect**
```
at+cfun=1 (เปิดการใช้งานโมดูล) 
at+cgdcont=3,"IP","CustomAPN" (กำหนดการติดต่อข้อมูลด้วยโปรไฟล์ 3) 
at!scdftprof=3 (ตั้งโปรไฟล์เริ่มต้นเป็น 3) 
at!scprof=3," ",1,0,0,0 (เปิดการเชื่อมต่ออัตโนมัติในโปรไฟล์ 3)
  ```
  

> คำสั่งเพื่อตรวจสอบสถานะโมเด็ม: `at!gstatus?`


**2.การเชื่อมต่อโดยใช้ KPPP**
ก่อนที่จะใช้งาน KPPP คุณต้องทำการติดตั้งก่อน หากยังไม่ได้ทำการติดตั้ง ลองใช้งาน package manager ของคุณเพื่อทำการติดตั้ง (เช่น yum, apt, หรือ yast)

เปลี่ยนไปใช้สิทธิ์ root และเริ่มต้นใช้งาน KPPP โดยพิมพ์คำสั่งต่อไปนี้:
```
$ su 
# kppp &
```
**ทำการกำหนดค่าบัญชีดังนี้:**

 - คลิกที่ "Configure" หรือ "Setup"
 - เลือกแท็บ "Accounts" และคลิก "New"
 - คลิก "Manual Setup"
 - พิมพ์ "WWAN" ในช่อง "Connection name"
 - กรอกหมายเลขโทรศัพท์ในช่อง
     -->สำหรับอุปกรณ์ GSM/UMTS: *99#
     -->สำหรับอุปกรณ์ CDMA: #777
  
 - เลือก "PAP/CHAP" เป็นวิธีการยืนยันตัวตน
 - คลิก "OK"
 
 **ทำการกำหนดค่าโมเด็มดังนี้:**
 
 1.คลิกที่ "Configure" เพื่อเปิดหน้าต่าง "Configuration"
2. เลือกแท็บ "Modems" และคลิก "New"
3.พิมพ์ชื่อโมเด็มในช่อง "Modem name"
4.เลือก "/dev/ttyUSBx" เป็นอุปกรณ์ที่ใช้งาน โดยที่ x คือหมายเลข Data Port สำหรับโมเด็ม Serra Wireless ของคุณ    ซึ่งสามารถตรวจสอบได้ในตารางใต้หัวข้อ "GSM/UMTS AT Commands"    ตัวอย่างเช่น สำหรับโมเด็ม Mercury-Compass 885 หมายเลข Data Port คือ    /dev/ttyUSB4
5.ตรวจสอบให้แน่ใจว่า flow control ถูกตั้งค่าเป็น Hardware
6.กรณีที่ใช้งานอุปกรณ์ GSM/UMTS:
   ->คลิกที่แท็บ "Modem" แล้วคลิกปุ่ม "Modem Commands…"
   ->พิมพ์ "at+cgdcont=1,"IP","APN"" ในช่อง 'Initialization String 1' โดยที่ APN คือชื่อ Access Point ของผู้ให้บริการของคุณ
7.บันทึกการเปลี่ยนแปลงและออกจากหน้าต่าง "Configuration"
8.ป้อนชื่อผู้ใช้และรหัสผ่านของคุณ (ติดต่อผู้ให้บริการหากคุณไม่ทราบข้อมูลเหล่านี้)
9.คลิก "Connect"

 
**3.การเชื่อมต่อโดยใช้วิธีmanual pppd** 
เพื่อเชื่อมต่อโดยใช้วิธี pppd ด้วยตนเอง คุณจำเป็นต้องดาวน์โหลดสคริปต์ pppd [ตรงนี้](https://www.downloads.netgear.com/files/aircard/ppp-scripts.tar.gz?_ga=2.91777689.282871542.1707468066-1159533268.1707468066)
  

 - เข้าไปยังไดเร็กทอรีที่มีไฟล์ pppd-scripts.tar.gz และแตกไฟล์ที่ตำแหน่งเริ่มต้นโดยพิมพ์คำสั่งต่อไปนี้
 ```
 $ cd "directory"  
 $ tar -zxf pppd-scripts.tar.gz
 ```
 
 - เปลี่ยนเป็น root และคัดลอกไฟล์ไปยังไดเร็กทอรี ppp/peers โดยพิมพ์คำสั่งต่อไปนี้
  ```
# su 
 # cp -r ./ppp /etc/  
 # cd /etc/ppp  
 # chmod a+x ip-up.local ip-down.local
 ```
 
 - หากใช้อุปกรณ์ GSM/UMTS กรุณาปฏิบัติตามขั้นตอนเหล่านี้เพื่อตั้งค่าการยืนยันตัวตน ถ้าไม่งั้นข้ามขั้นตอนนี้:
 ```
 # cd /etc/ppp/peers  
 # vi ./gsm_chat (คุณสามารถใช้โปรแกรมแก้ไขอื่น ๆ เช่น emacs หรือ gedit เพื่อแก้ไขสคริปต์)
 ```
       
> ไปที่ส่วน APN และแทนที่ APN ที่ระบุด้วยของผู้ให้บริการของคุณ (เช่น หากผู้ให้บริการของคุณคือ AT&T คุณจะพิมพ์ isp.cingular)
 
> มีบางบรรทัด APN ตัวอย่างที่ระบุในสคริปต์ที่สามารถลองใช้ได้

> บันทึกและออก

 - ทดสอบการเชื่อมต่อโดยพิมพ์คำสั่งต่อไปนี้ (คุณอาจจำเป็นต้องใช้บัญชี root เพื่อเรียกใช้ pppd): 
 -สำหรับอุปกรณ์ CDMA:
 ```
 # pppd call cdma
 ```
 -สำหรับอุปกรณ์ GSM/UMTS:
 ```
 # pppd call gsm
 ```
 -สำหรับ Aircard 885E, MC8785, C885:
 ```
 # pppd call gsm885
 ```
 - หากการทดสอบการเชื่อมต่อไม่ประสบความสำเร็จ อาจจะต้องมีการยืนยันตัวตนเพิ่มเติม
  ```
 # vi ./gsm (คุณสามารถใช้โปรแกรมแก้ไขอื่น ๆ เช่น emacs หรือ gedit เพื่อแก้ไขสคริปต์)
 ```
 --ใส่ '#' ถัดจากบรรทัด "noauth" (สิ่งนี้จะปิดการใช้งานบรรทัด)
 --ลบ '#' ที่ต่อจากบรรทัด user และ password
 --พิมพ์ชื่อผู้ใช้และรหัสผ่านที่เหมาะสม (ติดต่อผู้ให้บริการหากคุณไม่ทราบข้อมูลเหล่านี้)
 --บางรุ่นของ pppd อาจไม่ติดตั้งการกำหนดค่า dynamic DNS ได้อย่างถูกต้อง เป็นไปได้ที่จะต้องคัดลอกหรือเชื่อมโยง /etc/ppp/resolv.conf ไปยัง /etc/resolv.conf

#  References

 - https://www.mindphp.com/%E0%B8%84%E0%B8%B9%E0%B9%88%E0%B8%A1%E0%B8%B7%E0%B8%AD/73-%E0%B8%84%E0%B8%B7%E0%B8%AD%E0%B8%AD%E0%B8%B0%E0%B9%84%E0%B8%A3/4047-what-is-air-card.html
 - https://kb.netgear.com/22827/Can-I-use-my-NETGEAR-AirCard-modem-on-a-Linux-operating-system-v-1-7-40
 - https://sittikron-big-rmutt.blogspot.com/2015/08/how-to-install-driver-huawei-aircard-3g.html
 - https://kb.netgear.com/22869/Can-I-use-a-NETGEAR-AirCard-Modem-on-Linux-Machines-direct-IP-modems


