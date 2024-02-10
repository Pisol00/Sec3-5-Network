# คู่มือการกำหนดค่า IP บนระบบ Linux

คู่มือนี้จะแสดงขั้นตอนการกำหนดที่อยู่ IP บนระบบ Linux โดยใช้คำสั่งต่างๆ

## 1. กำหนดที่อยู่ IP

เพื่อกำหนดที่อยู่ IP บนระบบ Linux คุณสามารถใช้คำสั่ง `ifconfig` หรือ `ip` ได้ ตัวอย่างการใช้งาน:

**ใช้คำสั่ง ifconfig:**
```bash
# เริ่มหรือรีสตาร์ทอินเทอร์เฟซ
sudo ifconfig eth0 up

# กำหนดที่อยู่ IP
sudo ifconfig eth0 192.168.1.100 netmask 255.255.255.0
```

**ใช้คำสั่ง ip:**
```bash
# เริ่มหรือรีสตาร์ทอินเทอร์เฟซ
sudo ip link set dev eth0 up

# กำหนดที่อยู่ IP
sudo ip addr add 192.168.1.100/24 dev eth0
```

## 2. กำหนด Netmask

เพื่อกำหนด Netmask บนระบบ Linux คุณสามารถใช้คำสั่ง `ifconfig` หรือ `ip` ได้ ตัวอย่างการใช้งาน:

**ใช้คำสั่ง ifconfig:**
```bash
sudo ifconfig eth0 netmask 255.255.255.0
```

**ใช้คำสั่ง ip:**
```bash
sudo ip addr add 192.168.1.100/24 dev eth0
```

## 3. กำหนด Gateway

เพื่อกำหนดเกตเวย์บนระบบ Linux คุณสามารถใช้คำสั่ง `route` หรือ `ip route` ได้ ตัวอย่างการใช้งาน:

**ใช้คำสั่ง route:**
```bash
sudo route add default gw 192.168.1.1
```

**ใช้คำสั่ง ip route:**
```bash
sudo ip route add default via 192.168.1.1
```

## 4. กำหนดเซิร์ฟเวอร์ DNS

เพื่อกำหนดเซิร์ฟเวอร์ DNS บนระบบ Linux คุณสามารถแก้ไขไฟล์ `/etc/resolv.conf` ได้ ตัวอย่างการใช้งาน:

```bash
echo "nameserver 8.8.8.8" | sudo tee -a /etc/resolv.conf
```

## 5. เปลี่ยนที่อยู่ IP ชั่วคราว

เพื่อเปลี่ยนที่อยู่ IP ชั่วคราวบนระบบ Linux คุณสามารถใช้คำสั่ง `ifconfig` หรือ `ip` ได้ ตัวอย่างการใช้งาน:

...

## 6. เปลี่ยนที่อยู่ IP ถาวร

เพื่อเปลี่ยนที่อยู่ IP ถาวรบนระบบ Linux คุณสามารถแก้ไขไฟล์การกำหนด IP ใน `/etc/sysconfig/network-scripts/` หรือ `/etc/network/interfaces`

## 7. กำหนด IP แบบ Dynamic (DHCP)

เพื่อให้ระบบ Linux รับที่อยู่ IP แบบอัตโนมัติจากเซิร์ฟเวอร์ DHCP คุณสามารถใช้คำสั่ง `dhclient` ได้:

```bash
sudo dhclient
```

## 8. ตรวจสอบการกำหนดค่า IP

เพื่อตรวจสอบการกำหนดค่า IP บนระบบ Linux คุณสามารถใช้คำสั่ง `ifconfig` หรือ `ip` ได้:

**ใช้คำสั่ง ifconfig:**
```bash
ifconfig
```

**ใช้คำสั่ง ip:**
```bash
ip addr show
```
