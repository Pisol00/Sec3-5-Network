# What is DNS?
DNS (Domain Name Server) คือ ระบบที่มีไว้สำหรับบริหารจัดการข้อมูลของ Domain Name
หรือชื่อเว็บไซต์ของเราที่ตั้งขึ้นมาเพื่อให้ง่ายต่อการจดจำ แล้วใช้งานได้สะดวกเมื่อต้องการค้นหน้าเว็บไซต์
ไม่จำเป็นต้องใช้งานเป็น IP เพราะยากต่อการจดจำ
## หน้าที่ของ DNS
ทำหน้าที่ในการแปลง Domain Name เป็นหมายเลข IP Address เพื่อนำหมายเลขไอพีดังกล่าวไปติดต่อยัง Sever อื่น ๆ ที่ต้องการ  Sever Email Hosting , Server Web Hosting เป็นต้น
## การติดตั้ง DNS Server
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
> IP Address `192.168.10.2` เป็นของเครื่องคอมพิวเตอร์ตัวอย่าง
### 4. Primary Server
แก้ไขไฟล์ /etc/bind/named.conf.local เพื่อเพิ่ม DNS zone ให้กับ BIND9
```
sudo nano /etc/bind/named.conf.local
```
โดยการสร้าง Zone File:
```
zone "example.com" {
    type master;
    file "/etc/bind/db.example.com";
};
```
### 5. Copy ไฟล์ของ db.local เป็นไฟล์ db.example.com
```
sudo cp /etc/bind/db.local /etc/bind/db.example.com
```
สร้าง record สำหรับ base domain และ ns.example.com
```
;
; BIND data file for example.com
;
$TTL    604800
@       IN      SOA     example.com. root.example.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL

@       IN      NS      ns.example.com.
@       IN      A       192.168.10.2
@       IN      AAAA    ::1
ns      IN      A       192.168.10.2
```
> IP Address `192.168.10.2` เป็นของเครื่องคอมพิวเตอร์ตัวอย่าง
### 6. Reverse Zone File
เพิ่ม Reverse Zone File เพื่ออนุญาตให้ DNS แก้ไขที่อยู่เป็นชื่อ
```
sudo nano /etc/bind/named.conf.local
```
และทำการแก้ไข Zone File:
```
zone "10.168.192.in-addr.arpa" {
    type master;
    file "/etc/bind/db.192";
};
```
> `10.168.192` เป็น IP Address 3 octets แรกของเครื่องคอมพิวเตอร์ตัวอย่าง
#### สร้างไฟล์ db.192
โดยการ copy ไฟล์ของ db.127 เป็นไฟล์ชื่อ db.192
```
sudo cp /etc/bind/db.127 /etc/bind/db.192
```
ทำการแก้ไขไฟล์ db.192:
```
;
; BIND reverse data file for local 192.168.1.XXX net
;
$TTL    604800
@       IN      SOA     ns.example.com. root.example.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.
2      IN      PTR     ns.example.com.

```
> เลข `2` เป็น octets สุดท้ายของ IP Address

### 7. แก้ไข resolv.conf
```
sudo nano /etc/resolv.conf
```
เพิ่ม Nameserver Addresses ไปยัง network clients:
```
nameserver 192.168.10.2
search example.com
```
### 8. Restart the DNS server
```
sudo systemctl restart bind9.service
```
## การทดสอบ
ทดสอบความถูกต้องของ DNS ที่ได้ทำการสร้างขึ้นมา
```
ping example.com
```
