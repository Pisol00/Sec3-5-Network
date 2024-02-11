# Wireless Adapter Configuration

## The `iw` Command

ก่อนที่จะเริ่มใช้งาน command นี้เราควรโหลด package iw มาก่อนโดยใช้คำสั่ง

```bash
$ sudo apt install iw
```

คำสั่ง `iw` (ย่อมาจาก "Wireless") เป็นเครื่องมือบรรทัดคำสั่งสำหรับการแสดงและจัดการอุปกรณ์ไร้สายบนระบบ Linux โดยจัดเตรียมชุดคำสั่งย่อยสำหรับดำเนินการต่างๆ ที่เกี่ยวข้องกับการจัดการเครือข่ายไร้สาย เช่น การสแกนหาเครือข่ายไร้สายที่มีอยู่ การเชื่อมต่อกับเครือข่ายไร้สาย และการรับสถานะของการเชื่อมต่อไร้สายในปัจจุบัน

### **โครงสร้างคำสั่ง**

```powershell
$ iw [Options] Command
```

| Command | Description |
| --- | --- |
| iw dev | คำสั่งนี้แสดงรายการอุปกรณ์ไร้สายที่มีอยู่ในระบบ |
| iw scan | คำสั่งนี้จะสแกนหาเครือข่ายไร้สายที่มีอยู่ และแสดงข้อมูลเกี่ยวกับเครือข่ายเหล่านั้น เช่น SSID ความแรงของสัญญาณ และประเภทการเข้ารหัส |
| iw connect | คำสั่งนี้เชื่อมต่อกับเครือข่ายไร้สายเฉพาะ |
| iw link | คำสั่งนี้แสดงสถานะของการเชื่อมต่อไร้สายในปัจจุบัน รวมถึง SSID ของเครือข่ายที่เชื่อมต่อ ความแรงของสัญญาณ และประเภทการเข้ารหัส |
| iw config | คำสั่งนี้อนุญาตให้ผู้ใช้กำหนดค่าอุปกรณ์ไร้สาย เช่น การตั้งค่าช่องสัญญาณของอุปกรณ์ บิตเรต หรือกำลังส่ง |

`iw` ยังสามารถใช้เพื่อกำหนดการตั้งค่าไร้สายขั้นสูง เช่น การสร้างเครือข่ายตาข่ายไร้สาย การตั้งค่าฮอตสปอต หรือการตั้งค่าการ์ดไร้สายในโหมดจอภาพ เครื่องมือ iw ได้รับการออกแบบมาให้เรียบง่ายและใช้งานง่าย และมีให้ใช้งานบน Linux เกือบทุกรุ่น สามารถใช้เป็นทางเลือกหรือเสริมกับเครื่องมือการจัดการไร้สายอื่นๆ เช่น iwctl, wpa_supplicant และ NetworkManager

### ตัวอย่างการใช้คำสั่ง

- แสดงข้อมูลรายละเอียด interface ทั้งหมด

```java
User@ubuntu:~# iw dev wlp scan
```

- เข้าร่วมเครือข่ายไร้สายแบบเปิด

```java
User@ubuntu:~# iw dev wlp connect SSID
```

- ปิดการเชื่อมต่อปัจจุบัน

```java
User@ubuntu:~# iw dev wlp disconnect
```

- แสดงข้อมูลเกี่ยวกับการเชื่อมต่อปัจจุบัน

```java
User@ubuntu:~# iw dev wlp link
```

# การประยุกต์ใช้คำสั่งกับการใช้งาน

- ดูอินเทอร์เฟซของคุณและที่อยู่ IP ที่กำหนดค่า

```java
$ ifconfig
$ ip addr show
```

- ดู routing table

```java
$ ip route show
```

- รับข้อมูลพื้นฐานเกี่ยวกับอะแดปเตอร์ WLAN

```java
$ sudo iw dev
```

- ทำการสแกนหารายการเครือข่ายใกล้เคียง

```java
# iw wlan0 scan // โชว์ข้อมูลที่เราไม่ต้องการมากมาย
# iw wlan0 scan | grep -i ssid // สำหรับรายการ SSID เท่านั้น
```

- รับข้อมูลเกี่ยวกับการเชื่อมต่อ WLAN (อัตราข้อมูล, SSID, ช่องสัญญาณ (MHz), ความแรงของสัญญาณ ฯลฯ)

```java
# iw wlan0 info
```

- ตั้งค่า wlan0 เป็นโหมดมอนิเตอร์ (ด้วยตนเอง)

```java
$ sudo ip link set dev wlan0 down
$ sudo iw dev wlan0 set type monitor
$ sudo ip link set dev wlan0 up
```

- เปลี่ยนช่องของอะแดปเตอร์ WLAN

```java
# iw dev wlan0 set channel <channel-number>
```

- ดัมพ์ความสามารถทั้งหมดของอแด็ปเตอร์ WLAN

```java
$ iw dev phy0 info
```

- เปลี่ยนช่องและตั้งค่า Bandwidth

```java
# iw dev wlan0 set channel 40 HT20|HT40+|HT40-|80MHz
```

- ดูแคช arp

```java
$ ip neighbor
$ sudo arp -n
```

- ดูข้อมูลเลเยอร์ 2 สำหรับอะแดปเตอร์

```java
$ sudo ip link
$ sudo ip link show wlan0
```

- ตรวจสอบว่าอะแดปเตอร์ได้รับการยอมรับจากระบบหรือไม่

```java
$ lspci // for PCI adapters
$ lsusb // for USB adapters
```

> คุณยังสามารถดูผลลัพธ์ของ dmesg หลังจากที่คุณใส่อะแดปเตอร์แล้วด้วยการใช้คำสั่ง `sudo dmesg`
> 
- รับข้อมูลเกี่ยวกับอะแดปเตอร์ WLAN ของคุณ (ไดรเวอร์ เวอร์ชันไดรเวอร์ สถานะไร้สาย ฯลฯ)

```java
$ sudo lshw -C network
```

- หาก Network Manager ทำงานอยู่ คุณจะได้รับรายการ WLAN ที่พร้อมใช้งาน

```java
$ nmcli dev wifi
```

- รับข้อมูลเกี่ยวกับคุณภาพลิงค์ WLAN

```java
$ cat /proc/net/wireless
```

- รับข้อมูลเกี่ยวกับคุณภาพลิงค์ WLAN ที่อัปเดตทุกวินาทีเช่นนี้

```java
$ watch -n 1 cat /proc/net/wireless
```

- ติดตั้งเวฟมอน มันให้อินเทอร์เฟซที่เรียบง่ายพร้อมข้อมูลที่เป็นประโยชน์เกี่ยวกับการเชื่อมต่อของคุณ

```java
$ sudo apt get install wavemon
$ sudo wavemon // เพื่อให้มีความพร้อมในการสแกนเครือข่ายหรือเพียงแค่ wavemon
```

## การตั้งค่า Wireless adapter บน Linux

การตั้งค่า Wireless adapter บน Linux จะแตกต่างไปตามการ์ดเครือข่ายที่ใช้ แต่ทั่วไปแล้ว ขั้นตอนพื้นฐานสำหรับการตั้งค่า Wireless adapter บน Linux ประกอบด้วย

1. **ตรวจสอบว่า Wireless adapter ถูกติดตั้งแล้วหรือไม่ :** คำสั่ง `iwconfig` สามารถใช้เพื่อตรวจสอบว่ามี Wireless adapter ใดๆ ติดตั้งอยู่บนระบบ Linux หรือไม่
2. **สแกน Wireless network** : ใช้คำสั่ง `iwlist <interface_name> scan` เพื่อสแกนหา Wireless networks ที่อยู่ในระยะที่ Wireless adapter ของคุณสามารถรับสัญญาณได้
3. **กำหนดค่า Wireless adapter**: ใช้คำสั่ง **`iw`** หรือ **`iwconfig`** เพื่อกำหนดค่าต่างๆ ของ Wireless adapter เช่น การตั้งค่า SSID, การเชื่อมต่อ, การใช้งานการ์ด, การตั้งค่าการเชื่อมต่อไร้สาย เป็นต้น
4. **การใช้งาน Network Manager**: หากคุณใช้งาน Network Manager คุณสามารถใช้เครื่องมือ GUI เพื่อจัดการการเชื่อมต่อไร้สายได้ง่ายขึ้น โดยใช้โปรแกรมเช่น **`nm-connection-editor`** เพื่อเพิ่มหรือแก้ไขการเชื่อมต่อไร้สาย
5. **การกำหนด IP Address และการเชื่อมต่อ**: หลังจากที่คุณได้ตั้งค่า Wireless adapter แล้ว คุณอาจต้องกำหนด IP address และการเชื่อมต่อโดยใช้คำสั่ง **`ifconfig`** หรือ **`ip`** หรือสามารถใช้ Network Manager สำหรับการกำหนดค่าเชื่อมต่อเครือข่าย
6. **ทดสอบการเชื่อมต่อ**: ทดสอบการเชื่อมต่อโดยใช้คำสั่ง **`ping`** เพื่อตรวจสอบว่าสามารถเชื่อมต่อกับอุปกรณ์หรือเซิร์ฟเวอร์ได้หรือไม่
7. **การตั้งค่าการเชื่อมต่ออัตโนมัติ**: คุณอาจต้องกำหนดการเชื่อมต่อไร้สายให้เชื่อมต่อโดยอัตโนมัติเมื่อระบบ Linux ทำการบูต โดยการเพิ่มคำสั่งในไฟล์การกำหนดค่าของเครื่องใน **`/etc/netplan`**หรือการใช้ Network Manager

> คำสั่งและวิธีการต่างๆ สามารถแตกต่างกันไปขึ้นอยู่กับการ์ดเครือข่ายและเวอร์ชันของระบบ Linux ที่คุณใช้ การค้นหาข้อมูลเพิ่มเติมเกี่ยวกับการตั้งค่าที่เหมาะสมสำหรับการ์ดเครือข่ายและเวอร์ชันของระบบ Linux ของคุณเป็นสิ่งที่ดีที่สุด
> 

## Reference

1. iw Command Examples in Linux**.** [https://www.thegeekdiary.com/iw-command-examples-in-linux/](https://www.thegeekdiary.com/iw-command-examples-in-linux/)
2. Useful Linux Command for Wireless. ****[https://www.itdojo.com/courses-linux/linuxwifi/](https://www.itdojo.com/courses-linux/linuxwifi/)
3. Network configuration/Wireless. [https://wiki.archlinux.org/title/Network_configuration/Wireless](https://wiki.archlinux.org/title/Network_configuration/Wireless)
4. Ben Richardson. (2023). .How to Enable Wireless Network Connectivity for Windows Virtual Machines. [https://zuli.io/how-to-enable-wireless-network-connectivity-for-windows-virtual-machines](https://zuli.io/how-to-enable-wireless-network-connectivity-for-windows-virtual-machines)
5. ChatGPT. [https://chat.openai.com/share/70f25cc4-b103-4ab7-9b8a-66f49b7283b2](https://chat.openai.com/share/70f25cc4-b103-4ab7-9b8a-66f49b7283b2)