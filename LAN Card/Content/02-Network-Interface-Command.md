# 02-Network-Interface-Command

## **The `ifconfig` command**

ก่อนที่จะเริ่มใช้งาน command นี้เราควรโหลด package net-tool มาก่อนโดยใช้คำสั่ง

```bash
$ sudo apt install net-tools
```

สามารถใช้คำสั่ง `ifconfig` เพื่อกำหนดค่าของอินเทอร์เฟซเคอร์เนลที่อยู่ในระบบ kernel มักถูกใช้ในเวลาเริ่มต้นของระบบเพื่อตั้งค่าอินเทอร์เฟซตามที่จำเป็น หลังจากนั้น มันมักจะใช้เฉพาะเมื่อมีการแก้ปัญหาหรือเมื่อต้องการปรับแต่งระบบ

### **โครงสร้างคำสั่ง**

```powershell
$ ifconfig [-v] [-a] [-s] [interface]
$ ifconfig [-v] interface [aftype] options | address ...
```

| Command | Description |
| --- | --- |
| ifconfig  | แสดงข้อมูลรายละเอียด interface ทั้งหมดที่ถูก Activate |
| ifconfig -a | แสดงข้อมูลรายละเอียด interface ทั้งหมดถึงแม้จะไม่ Activate |
| ifconfig -v | แสดงข้อมูล interface ที่เกิด error condition ทั้งหมด |
| ifconfig -s | แสดงข้อมูล interface ทั้งหมดเป็น list แบบย่อ |
| ifconfig [interface] | แสดงข้อมูล interface ที่เฉพาะเจาะจงตามที่ระบุไว้ |
| ifconfig [interface] up | เปิดการใช้งาน interface ที่ระบุ |
| ifconfig [interface] down | ปิดการใช้งาน interface ที่ระบุ |
| ifconfig [interface] [IP address] netmask [Subnet mask] broadcast [Broadcast IP] | กำหนดค่า configure ของ interface โดยรวมทั้งหมด |
| ifconfig [interface] promisc | เปิดใช้งาน promiscous mode บน network interface ที่ระบุไว้ |
| ifconfig [interface] promisc | ปิดใช้งาน promiscous mode บน network interface ที่ระบุไว้ |
| ifconfig [interface] [IP address] | กำหนดที่อยู่ IP เฉพาะให้กับอินเทอร์เฟซเครือข่ายที่ระบุไว้ |
| ifconfig [interface] mtu [rate] | เพื่อตั้งค่าหน่วยการส่งข้อมูลสูงสุดให้เป็นอินเทอร์เฟซเครือข่าย |
| ifconfig [interface]:[subinterface] [IP address] | หากต้องการเพิ่มที่อยู่ IP เพิ่มเติมให้กับอินเทอร์เฟซเครือข่าย คุณสามารถกำหนด sub-interface ได้ |
| ifconfig [interface]:[subinterface] down | ลบหรือปิดการใช้งานของ sub-interface นั้น |

> Promiscous mode คือ โหมดที่จะยอมรับทุกแพ็กเก็ตทั้งหมดที่ไหลผ่านการ์ดเครือข่ายมาเก็บไว้ โดยถ้าเป็นโหมดปกติ เมื่อแพ็กเก็ตถูกรับโดยการ์ดเครือข่าย มันจะตรวจสอบว่ามันเป็นของตัวเองหรือไม่ หากไม่ใช่ มันจะปกติทิ้งแพ็กเก็ตไป
> 

### ตัวอย่างการใช้คำสั่ง

- แสดงข้อมูลรายละเอียด interface ทั้งหมด

```powershell
User@ubuntu:~$ ifconfig -a
```

*OUTPUT*

![*[ภาพที่ 1] การแสดงผลคำสั่ง ifconfig -a*](../assets/ifconfig.png)

*[ภาพที่ 1] การแสดงผลคำสั่ง ifconfig -a*

- สร้าง sub-interface แล้วให้ IP Address, Subnet mask, Broadcast Address

```java
User@ubuntu:~$ sudo ifconfig enp0s3:0 192.168.1.120 netmask 255.255.255.128 broadcast 192.168.1.127
```

*OUTPUT*

![*[ภาพที่ 2] การแบ่ง sub-interfaces* ](../assets/subinterface.png)

*[ภาพที่ 2] การแบ่ง sub-interfaces* 

## The `ip` command

คำสั่ง **`ip`** เป็นคำสั่งที่มีอยู่ในไดเร็กทอรี่ **`/sbin`** หรือ **`/usr/sbin`** ซึ่งเป็นไดเร็กทอรี่ที่เก็บคำสั่งที่ต้องการสิทธิ์ root (superuser) เพื่อใช้งานได้ ดังนั้นเมื่อใช้งาน **`ip`** ควรเรียกใช้โดยใช้สิทธิ์ root โดยการใช้คำสั่ง **`sudo ip`** หรือเข้าสู่ระบบด้วยบัญชี root ก่อนเพื่อใช้งานคำสั่งได้อย่างถูกต้อง ไม่ต้องติดตั้ง Package เพิ่มเติมในการใช้งาน

### **โครงสร้างคำสั่ง**

```powershell
$ ip [OPTIONS] OBJECT {COMMAND | help}
```

มีองค์ประกอบดังนี้

- **OPTIONS** : ตัวเลือกเพิ่มเติมที่ปรับเปลี่ยนพฤติกรรมของ nmcli
- **OBJECT** : ระบุเป้าหมายของการดำเนินการ (เช่น การเชื่อมต่อ อุปกรณ์ ฯลฯ)
- **COMMAND** : กำหนดการกระทำที่จะดำเนินการกับวัตถุที่ระบุ

| Object | Description |
| --- | --- |
| ip link, l | แสดงและแก้ไข network interface IPv6 |
| ip address, addr | แสดงและแก้ไข IP Address ในอินเตอร์เฟซ |
| ip addrlabel, addrl | การกำหนดค่าป้ายกำกับสำหรับการเลือกที่อยู่ของโปรโตคอล |
| ip neighbour, n | แสดงและจัดการวัตถุข้างเคียง (ตาราง ARP) |
| ip route, r | แสดงและแก้ไขตารางเส้นทาง (routing table) |
| ip rule, ru  | กฎเกณฑ์ในฐานข้อมูลเกี่ยวกับนโยบายการกำหนดเส้นทาง |
| ip maddress, maddr | Multicast address |
| ip mroute, mr | Multicast routing cache entry |
| ip tunnel, t | แสดงและแก้ไข Tunnel ที่ผ่านบน IP |
| ip xfrm, x | Framework ของ IPsec protocol |

> ในคำสั่งต่างๆสามารถพิมพ์รูปแบบย่อได้ เช่น ip address → ip a / ip addr เป็นต้น
> 

ใช้คำสั่ง ip เพื่อแสดงและ **กำหนดค่าพารามิเตอร์เครือข่าย** สำหรับอินเทอร์เฟซของโฮสต์ ดังนี้:

1. หาว่าอินเทอร์เฟซใดบ้างที่ถูกกำหนดค่าบนระบบ
2. สอบถามสถานะของอินเทอร์เฟซ IP
3. กำหนดค่า loop-back ภายใน, Ethernet และอินเทอร์เฟซ IP อื่น ๆ
4. เปลี่ยนสถานะอินเทอร์เฟซเป็น up หรือ down

```java
# ip link set {interface-name} {up|down}
```

5. กำหนดค่าและแก้ไขการส่ง static route และ default route
    - Add a new **static route**
    
    ```java
    # ip route add {NETWORK/MASK} via {GATEWAYIP}
    # ip route add {NETWORK/MASK} dev {DEVICE}
    ```
    
    - Add a new **default route**
    
    ```java
    # ip route add default {NETWORK/MASK} via {GATEWAYIP}
    # ip route add default {NETWORK/MASK} dev {DEVICE}
    ```
    
    - Delete a route
    
    ```java
    ip route del default
    ```
    
6. ติดตั้ง tunnel ผ่าน IP
7. แสดงรายการแคช ARP หรือ NDISC
8. กำหนด, ลบ, ตั้งค่า IP Address, routes, subnet และข้อมูล IP อื่น ๆ ไปยัง IP interfaces
    - **กำหนดค่า IP address ให้กับ interface**
    
    ```java
    # ip a add {ip_addr/mask} dev {interface-name}
    ```
    
    - **set broadcast address**
    
    ```java
    # ip addr add broadcast {brd_address} dev {interface}
    ```
    
    - **ลบ IP Address ออกจาก Interface**
    
    ```java
    # ip a del {ip_addr/mask} dev {interface-name}
    ```
    
9. แสดงรายการที่อยู่ IP และข้อมูลคุณสมบัติ

```java
# ip add show
```

10. จัดการและแสดงสถานะของเครือข่ายทั้งหมด

```java
$ sudo ip -br -c addr show
```

11. เก็บข้อมูลที่อยู่ IP เป็นหมวดหมู่
12. แสดงวัตถุเพื่อนบ้าน กล่าวคือ แคช ARP, ทำให้แคช ARP เป็นโมฆะ, เพิ่มรายการเข้าแคช ARP และอื่น ๆ
    - **Display neighbour/arp cache**
    
    ```java
    $ ip neigh show
    ```
    
    - **Add a new ARP entry**
    
    ```java
    # ip neigh add {IP-HERE} lladdr {MAC/LLADDRESS} dev {DEVICE} nud {STATE}
    ```
    
    - **Delete a ARP entry**
    
    ```java
    # ip neigh del {IPAddress} dev {DEVICE}
    ```
    
    - **Flush ARP entry**
    
    ```java
    # ip -s -s n f {IPAddress}
    ```
    
13. ตั้งค่าหรือลบรายการส่งเส้นทาง
14. หา route address (เช่น 8.8.8.8)

```java
$ ip route list
```

15. กำหนดความยาวของคิวการส่ง
    
    ```java
    # ip link set txqueuelen {NUMBER} dev {DEVICE}
    ```
    
    - สำหรับเครือข่ายกิกะบิต คุณสามารถตั้งค่า *maximum transmission units (MTU)* เพื่อประสิทธิภาพเครือข่ายที่ดีขึ้น
    
    ```java
    # ip link set mtu {NUMBER} dev {DEVICE}
    ```
    

> อาจมีการเพิ่ม option ก่อนตัว object ระบุไว้ก่อนด้านหน้า เพื่อ
> 

### ตัวอย่างการใช้คำสั่ง

- แสดงข้อมูลรายละเอียดของ interface โดยให้ highlight state และ IP address แสดงเฉพาะ IPv4 เท่านั้น

```java
User@ubuntu:~$ ip -4 -c addr show
```

*OUTPUT*

![*[ภาพที่ 3] ใช้ -c กับ ip addr เพื่อโชว์สีในส่วนของ IP และ state*](../assets/-cshow.png)

*[ภาพที่ 3] ใช้ -c กับ ip addr เพื่อโชว์สีในส่วนของ IP และ state*

- ในการกำหนดที่อยู่ IP ให้กับอินเทอร์เฟซนั้นๆ หรือการแบ่ง subnet

```java
User@ubuntu:~$ sudo ip addr add 192.168.1.120/25 dev enp0s3
```

*OUTPUT*

![*[ภาพที่ 4] กำหนดค่า subnet ใหม่ใน network interface*](../assets/assignnewip.png)

*[ภาพที่ 4] กำหนดค่า subnet ใหม่ใน network interface*

## The `nmcli` command

nmcli เป็นเครื่องมือ CLI ที่ใช้ในการควบคุม NetworkManager คำสั่ง nmcli ยังสามารถใช้เพื่อแสดงสถานะอุปกรณ์เครือข่าย สร้าง แก้ไข เปิด/ปิดใช้งาน และลบการเชื่อมต่อเครือข่าย

### **โครงสร้างคำสั่ง**

```powershell
$ nmcli [OPTIONS] OBJECT {COMMAND | help}
```

มีองค์ประกอบดังนี้

- **OPTIONS** : ตัวเลือกเพิ่มเติมที่ปรับเปลี่ยนพฤติกรรมของ nmcli
- **OBJECT** : ระบุเป้าหมายของการดำเนินการ (เช่น การเชื่อมต่อ อุปกรณ์ ฯลฯ)
- **COMMAND** : กำหนดการกระทำที่จะดำเนินการกับวัตถุที่ระบุ

| Command | Description |
| --- | --- |
| nmcli general { status, hostname, permissions, logging } [ARGUMENTS...] | ใช้คำสั่งนี้เพื่อแสดงสถานะ NetworkManager และการอนุญาต |
| nmcli networking { on, off, connectivity } [ARGUMENTS...] | สอบถามสถานะเครือข่าย NetworkManager เปิดใช้งานและปิดใช้งานเครือข่าย |
| nmcli connection { show, up, down, modify, add, edit, clone, delete, monitor, reload, load, import, export } [ARGUMENTS...] | สามารถใช้การเชื่อมต่อเพิ่มเติมเพื่อให้สามารถสลับระหว่างเครือข่ายและการกำหนดค่าต่างๆ ได้อย่างรวดเร็ว |
| nmcli connection show | แสดงรายการการเชื่อมต่อเครือข่ายทั้งหมดที่มีอยู่ในระบบของคุณ โดยให้รายละเอียดต่างๆ เช่น ชื่อการเชื่อมต่อ UUID อุปกรณ์ ประเภท และสถานะ |
| nmcli connection add type <connection_type> ifname <interface_name> con-name <connection_name> | เพิ่มการเชื่อมต่ออีเทอร์เน็ตใหม่  |
| nmcli connection modify <connection_name> <setting_name> <setting_value> | ปรับการตั้งค่าการเชื่อมต่อ |
| nmcli device { status, show, set, connect, reapply, modify, disconnect, delete, monitor, wifi, lldp } [ARGUMENTS...] | แสดงและจัดการอินเทอร์เฟซเครือข่าย |
| nmcli dev status | แสดงสถานะปัจจุบันของอุปกรณ์เครือข่ายทั้งหมดบนระบบของคุณ |
| nmcli device show <device_name> | แสดงรายละเอียดอุปกรณ์ตาม interface ที่ระบุ |
| nmcli radio { all, wifi, wwan } [ARGUMENTS...] | แสดงสถานะสวิตช์วิทยุ หรือเปิดและปิดสวิตช์ |
| nmcli monitor | สังเกตกิจกรรม NetworkManager ติดตามการเปลี่ยนแปลงสถานะการเชื่อมต่อ อุปกรณ์ หรือโปรไฟล์การเชื่อมต่อ |
| nmcli agent { secret, polkit, all } | รัน nmcli ในฐานะตัวแทนลับของ NetworkManager หรือตัวแทน polkit |

### ตัวอย่างการใช้คำสั่ง

- เพิ่มการเชื่อมต่ออีเธอร์เน็ตแบบไม่โต้ตอบที่เชื่อมโยงกับอินเทอร์เฟซ enp0s3 พร้อมการกำหนดค่า IP อัตโนมัติ (DHCP) และปิดใช้งานการตั้งค่าสถานะการเชื่อมต่ออัตโนมัติของการเชื่อมต่อ

```java
User@ubuntu:~$ nmcli connection add type ethernet autoconnect no ifname enp0s3
```

![*[ภาพที่ 5] กำหนดค่าใหม่ใน network interface*](../assets/nmcliex.png)

*[ภาพที่ 5] กำหนดค่าใหม่ใน network interface*

- ส่งออกโปรไฟล์ NetworkManager VPN corp-vpnc เป็นการกำหนดค่ามาตรฐานของ Cisco (vpnc)

```java
User@ubuntu:~$ nmcli con export corp-vpnc /home/joe/corpvpn.conf
```

## Reference

1. Bobby Iliev. (2021). 101 Linux commands Open-source eBook. [https://github.com/bobbyiliev/101-linux-commands-ebook/tree/main](https://github.com/bobbyiliev/101-linux-commands-ebook/tree/main)
2. saixiii. (2017). ifconfig – Linux Command คำสั่งแสดงข้อมูลและเปลี่ยนค่า interface server. [https://saixiii.com/ifconfig-linux-command/](https://saixiii.com/ifconfig-linux-command/)
3. Vivek Gite. (2023). Linux ip Command Examples. [https://www.cyberciti.biz/faq/linux-ip—command-examples-usage-syntax/](https://www.cyberciti.biz/faq/linux-ip-command-examples-usage-syntax/)
4. ChatGPT. (2024). Linux Network Interface Configuration. [https://chat.openai.com/share/31898e1f-ee5c-4f0e-844a-a8d61edc9fc8](https://chat.openai.com/share/31898e1f-ee5c-4f0e-844a-a8d61edc9fc8)
5. Gabriel Ramugila. (2023). nmcli Linux Command | NetworkManager Usage Guide. ****[https://ioflood.com/blog/nmcli-linux-command/](https://ioflood.com/blog/nmcli-linux-command/)
6. GNOME Devleoper. [https://developer-old.gnome.org/NetworkManager/stable/nmcli.html](https://developer-old.gnome.org/NetworkManager/stable/nmcli.html)

เขียนและเรียบเรียงเนื้อหาโดย นายภควัฒณ์ พันธ์ุภักดีวงษ์ 65070165 สื่อที่เป็นรูปภาพทั้งหมดในหัวข้อนี้เป็นของตัวผู้เขียนเอง อนุญาตให้นำไปใช้ได้
