# What is DNS?
DNS (Domain Name Server) คือ ระบบที่มีไว้สำหรับบริหารจัดการข้อมูลของ Domain Name
หรือชื่อเว็บไซต์ของเราที่ตั้งขึ้นมาเพื่อให้ง่ายต่อการจดจำ แล้วใช้งานได้สะดวกเมื่อต้องการค้นหน้าเว็บไซต์
ไม่จำเป็นต้องใช้งานเป็น IP เพราะยากต่อการจดจำ
# หน้าที่ของ DNS
ทำหน้าที่ในการแปลง Domain Name เป็นหมายเลข IP Address เพื่อนำหมายเลขไอพีดังกล่าวไปติดต่อยัง Sever อื่น ๆ ที่ต้องการ  Sever Email Hosting , Server Web Hosting เป็นต้น
# การติดตั้ง DNS Server
### 1. ทำการลง dns server ที่เครื่อง Ubuntu
```
sudo apt-get install bind9
```
### 2. ทำการเช็ค ip ของเครื่อง ubuntu
```
ifconfig
```
### 3. แก้ไขไฟล์ /etc/bind/named.conf.options
เพื่อแก้ไขที่อยู่ IP 
![image](https://github.com/Pisol00/Sec3-5-Network/assets/109954048/cd59590b-44a3-4149-9704-d8a0fa165570)

```
sudo nano /etc/bind/named.conf.options
```
### 
