# What is DNS?
DNS (Domain Name Server) คือ ระบบที่มีไว้สำหรับบริหารจัดการข้อมูลของ Domain Name
หรือชื่อเว็บไซต์ของเราที่ตั้งขึ้นมาเพื่อให้ง่ายต่อการจดจำ แล้วใช้งานได้สะดวกเมื่อต้องการค้นหน้าเว็บไซต์
ไม่จำเป็นต้องใช้งานเป็น IP เพราะยากต่อการจดจำ
# หน้าที่ของ DNS
ทำหน้าที่ในการแปลง Domain Name เป็นหมายเลข IP Address เพื่อนำหมายเลขไอพีดังกล่าวไปติดต่อยัง Sever อื่น ๆ ที่ต้องการ  Sever Email Hosting , Server Web Hosting เป็นต้น
# การติดตั้ง DNS Server
### 1. Install dns server ที่เครื่อง Ubuntu
```
sudo apt-get install bind9
```
ติดตั้ง `dnsutils` package สำหรับการทดสอบและแก้ไขปัญหา DNS
```
sudo apt install dnsutils
```
### 2. ทำการเช็ค ip ของเครื่อง ubuntu
```
ifconfig
```
### 3. Caching Nameserver
แก้ไขไฟล์ /etc/bind/named.conf.options
```
sudo nano /etc/bind/named.conf.options
```
โดยการแก้ไขที่อยู่ IP forwarders ให้เป็น IP ของเครื่อง Ubuntu
```
forwarders {
    192.168.10.2;
};
```
> IP Address 192.168.10.2 เป็นของเครื่องคอมพิวเตอร์ตัวอย่าง
### 4. Restart the DNS server
```
sudo systemctl restart bind9.service
```
### 5. Primary Server


