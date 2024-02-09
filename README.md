# Network-5

Subject - Computer Organization and Operating System Assignment (06016412)

List of Linux Components for Students Assignment - (Chapter: Network, Sec: 3)


## GroupMembers

| STUDENT ID|Name|Subcomponents|
|-----------|----|-------------|
|65070127 |นางสาวปณาลี จุกสีดา     |Interface Devices (Part2)|
|65070147 |นายพรเสก ชื่นมี         |Telnet SSH|
|65070157 |นางสาวพิราภรณ์ ประเสิริฐ  |Routing, Gateway|
|65070158 |นายพิศลย์ อุตตาลกาญจนา |IP Setup|
|65070165 |นายภควัฒณ์ พันธุ์ภักดีวงษ์ |Interface Devices (Part1)|
|65070168 |นางสาวภัณฑิรา ปิ่นกิ่งทอง  |DNS|
|65070170 |นางสาวภัทรภร จิตต์ปราณี  |Intro network to linux|


## Present
<div>
<img alt="Sumet" src="/members-and-teacher/Sumet.jpg" width="250">
  <p>ผู้ช่วยศาสตราจารย์ ดร. สุเมธ ประภาวัต</p>
</div>
<br>


# Introduction to Linux Networking

## บทนำ
รายงานนี้มีเนื้อหาเกี่ยวกับระบบปฏิการ Linux ที่เกี่ยวข้องกับเนื้อหา Network เน้นที่การอธิบายเกี่ยวกับเครือข่ายที่มีการเชื่อมต่อกันของคอมพิวเตอร์ซึ่งแบ่งปันข้อมูลและทรัพยากรร่วมกัน การเชื่อมต่อเครือข่ายไม่เพียงแค่การกำหนดค่าและให้บริการ แต่ยังเน้นไปที่กระบวนการแก้ไขปัญหาและการใช้คำสั่งของ Linux ในการจัดการปัญหาต่าง ๆ ในเครือข่ายอีกด้วย โดยจะเน้นการศึกษาจากองค์ประกอบที่ทำให้เกิดการทำงาน: Interface Devices, Wireless Adaptor, Aircard Adaptor, IP Setup, Routing, Gateway, LAN Cardและ DNS

## Overview
เกี่ยวกับเครือข่ายเน้นที่การเรียนรู้เกี่ยวกับองค์ประกอบที่ทำให้ระบบเครือข่ายทำงานได้ โดยที่จะกล่าวถึงมีดังนี้
1.  **Interface Devices**
    -   ในเนื้อหาเครือข่าย Interface Devices หรืออุปกรณ์ส่วนต่อประสานคืออุปกรณ์ที่ใช้ในการเชื่อมต่อระหว่างคอมพิวเตอร์หรืออุปกรณ์ต่าง ๆ ในเครือข่าย
2.  **Wireless Adaptor**
    -   เป็นอุปกรณ์ที่ใช้ในการเชื่อมต่อเครือข่ายไร้สาย ทำให้เครือข่ายสามารถให้บริการการเชื่อมต่อและการสื่อสารไร้สายได้
3.  **Aircard Adaptor**
    -   อุปกรณ์ที่ใช้เพื่อเชื่อมต่อกับเครือข่ายมือถือ (mobile network) ส่วนใหญ่ใช้ในการเชื่อมต่อกับอินเทอร์เน็ต.
4.  **IP Setup**
    -   การตั้งค่าที่ใช้กำหนดที่อยู่ IP (Internet Protocol) ให้กับอุปกรณ์ในเครือข่าย เพื่อให้สามารถระบุตัวตนและติดต่อสื่อสารกันได้
5.  **Routing**
    -   การกำหนดเส้นทางการส่งข้อมูลในเครือข่าย ซึ่งระบบเครือข่ายจะต้องทราบว่าข้อมูลจะถูกส่งไปยังที่ไหนในเครือข่าย
6.  **Gateway**
    -   อุปกรณ์ที่ทำหน้าที่เป็นทางเข้าหรือทางออกระหว่างเครือข่าย ทำให้ข้อมูลสามารถถูกส่งออกหรือเข้าเครือข่ายอื่น ๆ
7.  **LAN Card**
    -   Network Interface Card (NIC) ที่ใช้สำหรับเชื่อมต่อกับ Local Area Network (LAN) ซึ่งเป็นเครือข่ายที่มีขนาดจำกัดในระยะใกล้
8.  **DNS (Domain Name System)**
    -   ระบบที่ใช้แปลงชื่อโดเมน (Domain Name) เป็นที่อยู่ IP เพื่อให้คอมพิวเตอร์สามารถรู้จักและติดต่อกันในเครือข่าย

## Sysadmin Commands

**Ping** : จะช่วยให้เรารู้ว่าเครื่องคอมพิวเตอร์ที่ใช้งานอยู่นั้นมีการเชื่อมต่อกับระบบเครือข่ายปลายทางหรือไม่ ช่วยบอกได้ว่าระบบเครือข่ายที่เชื่อมต่อนั้นอยู่ระยะไหน และบอกความเสถียรอุปกรณ์ปลายทาง ทำให้สามารถวิเคราะห์ปัญหาที่เกิดขึ้นได้

ถ้าจะ execute ping
```
ping 8.8.8.8
```

ใน Linux เราสามารถใช้ตัวเลือก -c เพื่อส่งออก ping จำนวน n ครั้ง
```
ping -c n 8.8.8.8
```
เพื่อส่ง ping n ครั้งและแสดงเฉพาะสถิติ
```
ping -c n -q 8.8.8.8
```
  
ใช้ตัวเลือก -q เพื่อแสดงเฉพาะสถิติ

เราสามารถเลือกที่จะรัน ping ด้วย interface ที่ระบุได้ หากมีมากกว่าหนึ่ง interface โดยเขียน

```
ping -I wlan0 8.8.8.8
```

ที่นี่ wlan0 เป็น interface ที่เชื่อมต่อแบบไร้สาย

เรายังสามารถระบุเวอร์ชัน IP (4 หรือ 6) ได้โดยใช้ตัวเลือก -4 หรือ -6 ตามลำดับ



**netstat** : สามารถพิมพ์ข้อมูล Network connections, Routing tables, Interface statistics และอื่น ๆ
```
netstat
```
สามารถ list รายการทุกพอร์ตและการเชื่อมต่อได้โดย
```
netstat -a
```
TCP ports ทั้งหมด
```
netstat -at
```
listenin TCP ports
```
netstat -lt
```
ดู UDP ports ทั้งหมด
```
netstat -au
```
listenin UDP ports
```
netstat -lu
```
ในกรณีที่จะระบุการจบกระบวนการต้องใช้ PID ของกระบวนการนั้นๆ เพื่อระบุ PID ของกระบวนการแต่ละตัว เราสามารถใช้คำสั่งต่อไปนี้เพื่อแสดงรายการกระบวนการทั้งหมดพร้อมกับ PID ของแต่ละกระบวนการ
```
netstat -tp
```

**nslookup** : คำสั่งที่ใช้ค้นหาเซิร์ฟเวอร์ (name server lookup) มักถูกใช้ในการดำเนินการคิวรี DNS และรับรายการ DNS เจาะจง เช่น ชื่อโดเมน หรือที่อยู่ IP

มี syntax ดังนี้
```
nslookup [-option] [name | -] [server]
```
เพื่อตรวจสอบว่าที่อยู่ IP เชื่อมโยงกับโดเมนหรือไม่
```
nslookup 10.0.4.15
```
A-record ทำการ maps ชื่อ host กับที่อยู่ IP ในการดูว่ามีรายการกี่รายการและดูการ maps ของพวกเขาไปที่ที่อยู่ IP เราเขียน
```
nslookup google.com
```
NS-record ระบุเซิร์ฟเวอร์ชื่อที่รับผิดชอบใน DNS zone สำหรับการกำหนดค่า DNS ที่ถูกต้อง NS-records ที่กำหนดค่าในโซน DNS ต้องตรงกับการกำหนดค่าเป็นชื่อเซิร์ฟเวอร์ที่ผู้ให้บริการชื่อโดเมนกำหนด
```
nslookup -type=ns example.com
```

