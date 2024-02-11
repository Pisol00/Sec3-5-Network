# Gateway

คือ จุดเชื่อมต่อของเครือข่ายทำหน้าที่เป็นทางเข้าสู่ระบบเครือข่ายต่างๆ เป็นส่วนสำคัญในโลกของเทคโนโลยีสารสนเทศและการสื่อสาร เพราะมันช่วยให้การเชื่อมต่อระหว่างเครือข่ายต่าง ๆ เป็นไปอย่างมีประสิทธิภาพและปลอดภัยมากยิ่งขึ้น โดยไม่ว่าจะเป็นในองค์กรหรือในระบบเครือข่ายโลกอินเทอร์เน็ต (Internet)

## หน้าที่ของ Gateway

เป็นอุปกรณ์ที่ทำหน้าที่เชื่อมต่อเครือข่ายต่าง ๆ เข้าด้วยกัน ไม่ว่าเครือข่ายนั้นจะใช้โปรโตคอลตัวใดก็ตามเนื่องจากว่า Gateway สามารถแปลงรูปแบบแพ็คเก็ตของโปรโตคอลหนึ่งไปเป็นรูปแบบของอีกโปรโตคอลหนึ่ง เพื่อให้เหมาะสมกับการใช้งานในเครือข่ายได้ เช่น แปลงรูปแบบแพ็คเก็ตของ TCP/IP ไปเป็น Apple Talk เป็นต้น ทำให้สามารถเชื่อมต่อกับเครือข่ายอื่น ๆ ได้อย่างไม่มีข้อจำกัดแต่ในปัจจุบันนี้ ได้รวมการทำงานของ Gateway ไว้ใน Router แล้ว ทำให้ Router สามารถทำงานเป็น Gateway ได้จึงไม่จำเป็นต้องซื้ออุปกรณ์ตัวนี้อีกแล้ว

## Gateway in Linux 🐧

ในระบบ Linux, Gateway มักจะเป็นเครื่องคอมพิวเตอร์หรืออุปกรณ์ที่มีสองหรือมากกว่าสองอินเทอร์เฟซเครือข่าย (Network Interface) โดยมีหน้าที่เป็นตัวกลางในการส่งข้อมูลระหว่างเครือข่ายภายในและภายนอก โดยเซ็ตค่า IP Routing และการส่งข้อมูลให้แก่อุปกรณ์ในเครือข่ายภายนอกได้ 

นอกจากนี้ Gateway ยังมักจะเป็นจุดเข้าถึงอินเทอร์เน็ตในเครือข่ายภายในขององค์กรด้วย โดยเป็นตัวกลางในการส่งข้อมูลออกไปยังอินเทอร์เน็ตจริง ๆ จากเครือข่ายภายใน.

การกำหนด Gateway ในระบบ Linux สามารถทำได้ผ่านการตั้งค่าไอพีเราท์และการเปิดใช้งาน IP Forwarding ในไฟล์การกำหนดค่าของเคอร์เนล **(/etc/sysctl.conf)** และการกำหนดค่าในไฟล์การกำหนดค่าเครือข่าย **(/etc/network/interfaces)** หรือใช้คำสั่ง route เพื่อกำหนดเส้นทางของการส่งข้อมูล.

### Commands ในการดู Gateway ใน Linux

```markdown
ip r
ip route
```

### **Commands default Gateway IP ใน Linux**

```markdown
ip r | grep default
```

***ตัวอย่าง***

![gate1](gate1.png)

แต่เราสามารถเข้าไปตั้ง Gateway ให้ interface เองได้โดยใช้คำสั่ง

```markdown
sudo nano /etc/netplan/ (TAB) ex.00-installer-config.yaml
sudo netplan apply
```

***ตัวอย่าง***

![gate2](gate2.png)

![gate3](gate3.png)

//กรณียังไม่ได้ติดตั้ง netplan ต้องติดตั้งก่อน

```markdown
sudo apt-get install net-tools
```

***ตัวอย่างการใช้คำสั่งอีกครั้ง***

![gate4](gate4.png)

### Commands ดูตาราง Route,Gateway

```markdown
route -n
netstat -r -n
```

![gate5](gate5.png)

## **Commands สำหรับการตั้งค่า Gateway**

### ลบ **Default Gateway**

```markdown
sudo ip route delete default
ip r
```

### เพิ่ม **Default Gateway**

```markdown
sudo ip route add default via 192.168.10.1 dev enp0s8
```

## ความแตกต่างระหว่าง Route กับ Gateway

ความแตกต่างระหว่าง Route กับ Gateway คือ Route เป็นการกำหนดเส้นทางการส่งข้อมูลภายในเครือข่าย ในขณะที่ Gateway เป็นจุดเชื่อมต่อระหว่างเครือข่ายภายในและภายนอกที่ใช้ในการส่งข้อมูลไปยังเครือข่ายภายนอกของระบบ

## **References (ﾐ╹ᴥ╹ﾐ)**

[https://www.cyberciti.biz/faq/how-to-find-gateway-ip-address/](https://www.cyberciti.biz/faq/how-to-find-gateway-ip-address/)

[https://www.howtouselinux.com/post/linux-command-get-network-gateway](https://www.howtouselinux.com/post/linux-command-get-network-gateway)

[https://www.howtogeek.com/799588/how-to-set-the-default-gateway-in-linux/#configuring-the-default-gateway](https://www.howtogeek.com/799588/how-to-set-the-default-gateway-in-linux/#configuring-the-default-gateway)

https://chat.openai.com
