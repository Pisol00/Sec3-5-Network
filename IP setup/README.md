# คู่มือการกำหนดค่าเครือข่าย IP บนระบบ Linux (Configuring networks)

Ubuntu มาพร้อมกับโปรแกรมกราฟิกต่าง ๆ เพื่อกำหนดค่าอุปกรณ์เครือข่ายของคุณ แต่เอกสารนี้เหมาะสำหรับผู้ดูแลเซิร์ฟเวอร์และจะเน้นการจัดการเครือข่ายของคุณผ่านคำสั่งบน command line

## อินเทอร์เฟซอีเทอร์เน็ต (Ethernet interfaces)

อินเทอร์เฟซอีเทอร์เน็ตถูกระบุโดยระบบโดยใช้ชื่ออินเทอร์เฟซเครือข่ายที่เป็นไปได้อย่างที่คาดการณ์ไว้ ชื่อเหล่านี้อาจปรากฏเป็น eno1 หรือ enp0s25 อย่างไรก็ตาม ในบางกรณี อินเทอร์เฟซอาจยังใช้รูปแบบการตั้งชื่อแบบ eth# ของเคอร์เนลได้ในบางกรณีโดยยังคงมีการใช้ชื่อเหล่านี้อยู่

## ระบุอินเทอร์เฟซเครือข่ายอีเธอร์เน็ต (Identify Ethernet interfaces)

เพื่อระบุอินเทอร์เฟซเครือข่ายอีเธอร์เน็ตทั้งหมดที่พร้อมใช้งานได้อย่างรวดเร็ว คุณสามารถใช้คำสั่ง `ip a` ตามที่แสดงด้านล่างได้:

```
ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp0s25: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 00:16:3e:e2:52:42 brd ff:ff:ff:ff:ff:ff link-netnsid 0
    inet 10.102.66.200/24 brd 10.102.66.255 scope global dynamic eth0
       valid_lft 3257sec preferred_lft 3257sec
    inet6 fe80::216:3eff:fee2:5242/64 scope link
       valid_lft forever preferred_lft forever
```

แอปพลิเคชันอีกตัวที่ช่วยในการระบุอินเทอร์เฟซเครือข่ายทั้งหมดที่มีให้ระบบของคุณคือคำสั่ง lshw คำสั่งนี้จะให้ข้อมูลรายละเอียดเพิ่มเติมเกี่ยวกับความสามารถของฮาร์ดแวร์ของอะแดปเตอร์แต่ละตัว เช่นในตัวอย่างด้านล่าง lshw แสดงอินเทอร์เฟซอีเธอร์เน็ตเดียวที่มีชื่อเลขที่ตรรกะว่า eth4 พร้อมกับข้อมูลเกี่ยวกับบัส รายละเอียดของไดรเวอร์ และความสามารถที่รองรับทั้งหมด

## ชื่อตรรกะของอินเทอร์เฟซอีเทอร์เน็ต (Ethernet Interface logical names)
ชื่อตรรกะของอินเทอร์เฟซอีเทอร์เน็ต สามารถกำหนดค่าได้ผ่านการกำหนดค่า Netplan เช่นกัน หากคุณต้องการควบคุมว่าอินเทอร์เฟซใดจะได้รับชื่อตรรกะแบบใด คุณสามารถใช้คีย์ match และ set-name ได้ เคีย์ match ใช้ในการค้นหาอะแดปเตอร์โดยใช้เกณฑ์บางประการเช่น ที่อยู่ MAC, ไดรเวอร์ เป็นต้น และเคีย์ set-name สามารถใช้เปลี่ยนอุปกรณ์เป็นชื่อตรรกะที่ต้องการได้

```
network:
  version: 2
  renderer: networkd
  ethernets:
    eth_lan0:
      dhcp4: true
      match:
        macaddress: 00:11:22:33:44:55
      set-name: eth_lan0
```

## การตั้งค่าอินเทอร์เฟซอีเทอร์เน็ต (Ethernet Interface settings)
ethtool เป็นโปรแกรมที่แสดงและเปลี่ยนการตั้งค่าการ์ดเอเธอเน็ต เช่น การตั้งค่าการต่อสายอัตโนมัติ (auto-negotiation), ความเร็วพอร์ต, โหมดดูเพล็กซ์, และ Wake-on-LAN ต่อไปนี้คือตัวอย่างของวิธีการดูคุณลักษณะที่รองรับและการตั้งค่าที่กำหนดไว้ของอินเทอร์เฟซเอเธอเน็ต
```
sudo ethtool eth4
Settings for eth4:
    Supported ports: [ FIBRE ]
    Supported link modes:   10000baseT/Full
    Supported pause frame use: No
    Supports auto-negotiation: No
    Supported FEC modes: Not reported
    Advertised link modes:  10000baseT/Full
    Advertised pause frame use: No
    Advertised auto-negotiation: No
    Advertised FEC modes: Not reported
    Speed: 10000Mb/s
    Duplex: Full
    Port: FIBRE
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: off
    Supports Wake-on: d
    Wake-on: d
    Current message level: 0x00000014 (20)
                   link ifdown
    Link detected: yes
```

# การในการกำหนดที่อยู่ IP (IP addressing)

ส่วนต่อไปนี้อธิบายกระบวนการกำหนดค่าที่อยู่ IP และเกตเวย์เริ่มต้นของระบบของคุณที่จำเป็นสำหรับการสื่อสารในเครือข่ายพื้นที่ใกล้เคียงและบนอินเทอร์เน็ต

## การกำหนดที่อยู่ IP ชั่วคราว (Temporary IP address assignment)
สำหรับการกำหนดค่าเครือข่ายชั่วคราว คุณสามารถใช้คำสั่ง ip ซึ่งพบได้ในระบบปฏิบัติการ GNU/Linux ในส่วนมาก คำสั่ง ip ช่วยให้คุณกำหนดค่าที่มีผลทันที แต่ไม่มีความต่อทนและจะสูญหายหลังจากที่รีบูต

ในการกำหนดที่อยู่ IP ชั่วคราว คุณสามารถใช้คำสั่ง ip ดังต่อไปนี้ ปรับแต่งที่อยู่ IP และเน็ตมาสก์เพื่อให้ตรงกับความต้องการของเครือข่ายของคุณ

```
sudo ip addr add 10.102.66.200/24 dev enp0s25
```

คำสั่ง ip สามารถใช้ในการเปิดหรือปิดลิงก์ได้ตามต้องการ
```
ip link set dev enp0s25 up
ip link set dev enp0s25 down
```

เพื่อทำการตรวจสอบการกำหนดค่าที่อยู่ IP ของอินเทอร์เฟซ enp0s25 คุณสามารถใช้คำสั่ง ip ดังต่อไปนี้:

```
ip address show dev enp0s25
10: enp0s25: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 00:16:3e:e2:52:42 brd ff:ff:ff:ff:ff:ff link-netnsid 0
    inet 10.102.66.200/24 brd 10.102.66.255 scope global dynamic eth0
       valid_lft 2857sec preferred_lft 2857sec
    inet6 fe80::216:3eff:fee2:5242/64 scope link
       valid_lft forever preferred_lft forever6
```

เพื่อกำหนดเกตเวย์เริ่มต้น คุณสามารถใช้คำสั่ง ip ตามวิธีดังต่อไปนี้ ปรับแก้ที่อยู่เกตเวย์เริ่มต้นให้ตรงกับความต้องการของเครือข่ายของคุณ

```
sudo ip route add default via 10.102.66.1
```


คุณยังสามารถใช้คำสั่ง ip เพื่อตรวจสอบการกำหนดค่าเกตเวย์เริ่มต้นของคุณได้ดังนี้
```
ip route show
default via 10.102.66.1 dev eth0 proto dhcp src 10.102.66.200 metric 100
10.102.66.0/24 dev eth0 proto kernel scope link src 10.102.66.200
10.102.66.1 dev eth0 proto dhcp scope link src 10.102.66.200 metric 100
```

หากคุณต้องการ DNS สำหรับการกำหนดค่าเครือข่ายชั่วคราวของคุณ คุณสามารถเพิ่มที่อยู่ IP ของเซิร์ฟเวอร์ DNS ในไฟล์ /etc/resolv.conf โดยทั่วไปการแก้ไข /etc/resolv.conf โดยตรงไม่แนะนำ แต่นี่เป็นการกำหนดค่าชั่วคราวและไม่คงทน ตัวอย่างด้านล่างแสดงวิธีการเพิ่มเซิร์ฟเวอร์ DNS สองเซิร์ฟเวอร์ใน /etc/resolv.conf ซึ่งควรเปลี่ยนเป็นเซิร์ฟเวอร์ที่เหมาะสมสำหรับเครือข่ายของคุณ คำอธิบายที่ยาวนานมากของวิธีการกำหนดค่าลูกค้า DNS (ที่คงทน) จะอยู่ในส่วนถัดไป
```
nameserver 8.8.8.8
nameserver 8.8.4.4
```

หากคุณไม่ต้องการการกำหนดค่านี้อีกต่อไปและต้องการล้างการกำหนดค่า IP ทั้งหมดจากอินเทอร์เฟซ คุณสามารถใช้คำสั่ง ip พร้อมกับตัวเลือก flush ได้
```
ip addr flush eth0
```

## การกำหนดที่อยู่ IP แบบไดนามิก (Dynamic IP address assignment)

เพื่อกำหนดให้เซิร์ฟเวอร์ของคุณใช้ DHCP เพื่อกำหนดที่อยู่ IP แบบไดนามิก ให้สร้างการกำหนดค่า Netplan ในไฟล์ /etc/netplan/99_config.yaml ดังต่อไปนี้ ตัวอย่างต่อไปนี้ถือว่าคุณกำลังกำหนดค่าสำหรับอินเทอร์เฟซเอเธอเน็ตตัวแรกของคุณซึ่งถูกระบุว่าเป็น enp3s0
```
network:
  version: 2
  renderer: networkd
  ethernets:
    enp3s0:
      dhcp4: true
```
การกำหนดค่าสามารถใช้คำสั่ง netplan เพื่อให้เกิดผลในการกำหนดค่าได้
```
sudo netplan apply
```

## การกำหนดที่อยู่ IP แบบคงที่ (Static IP address assignment)
พื่อกำหนดระบบให้ใช้การกำหนดที่อยู่ IP แบบคงที่ ให้สร้างการกำหนดค่า netplan ในไฟล์ /etc/netplan/99_config.yaml ตัวอย่างด้านล่างนี้ถือว่าคุณกำลังกำหนดค่าสำหรับอินเทอร์เฟซเอเธอเน็ตแรกของคุณซึ่งระบุว่าเป็น eth0 ปรับเปลี่ยนค่าที่อยู่ IP, เส้นทาง, และค่าเซิร์ฟเวอร์ DNS เพื่อตรงกับความต้องการของเครือข่ายของคุณและชื่อของคุณหรือเรียกใช้งานต่าง ๆ ที่เหมาะสม
```
network:
  version: 2
  renderer: networkd
  ethernets:
    eth0:
      addresses:
        - 10.10.10.2/24
      routes:
        - to: default
          via: 10.10.10.1
      nameservers:
          search: [mydomain, otherdomain]
          addresses: [10.10.10.1, 1.1.1.1]
```
การกำหนดค่าสามารถนำไปใช้โดยใช้คำสั่ง netplan ได้เลย โดยการใช้คำสั่ง netplan apply
```
sudo netplan apply
```

อินเทอร์เฟซ loopback ถูกระบุโดยระบบเป็น lo และมีที่อยู่ IP เริ่มต้นคือ 127.0.0.1 คุณสามารถดูได้โดยใช้คำสั่ง ip 
```
ip address show lo
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
```

# การแปลงชื่อ (Name resolution)
การแปลงชื่อ (Name resolution) เกี่ยวข้องกับเครือข่ายไอพี(IP networking) คือกระบวนการในการแปลงชื่อโฮสต์เป็นที่อยู่ IP และตรงกันข้าม ซึ่งทำให้ง่ายต่อการระบุทรัพยากรบนเครือข่าย ส่วนต่อไปนี้จะอธิบายวิธีการกำหนดค่าระบบของคุณอย่างถูกต้องสำหรับการแก้ไขชื่อโดเมนโดยใช้ DNS และบันทึกชื่อโดเมนโดยใช้ชื่อแม่แบบคงที่

## การกำหนดค่าลูกค้า DNS (DNS client configuration)
โดยปกติแล้ว ไฟล์ /etc/resolv.conf เป็นไฟล์การกำหนดค่าแบบคงที่ที่มักไม่จำเป็นต้องเปลี่ยนแปลงบ่อยๆ หรือจะเปลี่ยนแปลงโดยอัตโนมัติผ่าน DCHP client hooks ส่วน systemd-resolved จะจัดการกำหนดค่า nameserver และควรจะใช้คำสั่ง systemd-resolve เพื่อทำการจัดการกับ systemd-resolved ซึ่ง Netplan จะกำหนดค่าให้ systemd-resolved ในการสร้างรายการของ nameservers และ domains ที่จะใช้ไปยัง /etc/resolv.conf ซึ่งเป็น symlink

```
/etc/resolv.conf -> ../run/systemd/resolve/stub-resolv.conf
```

เพื่อกำหนด resolver ให้เพิ่มที่อยู่ IP ของ nameservers ที่เหมาะสมสำหรับเครือข่ายของคุณลงในไฟล์การกำหนดค่า netplan คุณยังสามารถเพิ่ม optional DNS suffix search-lists เพื่อให้ตรงกับชื่อโดเมนของเครือข่ายของคุณ ไฟล์ที่เกิดขึ้นอาจมีรูปแบบดังต่อไปนี้
```
network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s25:
      addresses:
        - 192.168.0.100/24
      routes:
        - to: default
          via: 192.168.0.1
      nameservers:
          search: [mydomain, otherdomain]
          addresses: [1.1.1.1, 8.8.8.8, 4.4.4.4]
```

ตัวเลือก search ยังสามารถใช้ได้กับหลายชื่อโดเมนเพื่อให้การค้นหา DNS ถูกต่อท้ายตามลำดับที่ป้อนเข้ามา เช่น เครือข่ายของคุณอาจมีหลายซับโดเมนที่จะค้นหา มีโดเมนหลักเป็น example.com และซับโดเมนที่เป็น sales.example.com และ dev.example.com ไฟล์ที่เกิดขึ้นอาจมีรูปแบบดังต่อไปนี้

```
network:
  version: 2
  ethernets:
    eth0:
      addresses:
        - 192.168.1.10/24
      gateway4: 192.168.1.1
      nameservers:
        addresses: [8.8.8.8, 8.8.4.4]
        search: [sales.example.com, dev.example.com, example.com]
```

ถ้าคุณพยายามใช้คำสั่ง ping เพื่อเชื่อมต่อกับโฮสต์ที่มีชื่อว่า server1 ระบบของคุณจะทำการค้นหา Fully Qualified Domain Name (FQDN) ของโฮสต์นั้นๆ ผ่านระบบ DNS โดยอัตโนมัติตามลำดับดังนี้
1. server1.example.com
2. server1.sales.example.com
3. server1.dev.example.com

หากไม่พบการตรงความ ซึ่งหมายความว่าไม่พบรายการที่ตรงกับคำค้นหาใน DNS เซิร์ฟเวอร์ DNS จะให้ผลลัพธ์เป็น "not found" และการค้นหา DNS จะล้มเหลว

## การโฮสต์แบบคงที่ (Static hostnames)

Static hostnames คือ การกำหนดชื่อโฮสต์แบบคงที่ที่ถูกกำหนดไว้ในการแมปชื่อโฮสต์กับ IP ตั้งอยู่ในไฟล์ /etc/hosts รายการในไฟล์ hosts จะมีความสำคัญกว่า DNS โดยค่าเริ่มต้น นั่นหมายความว่าหากระบบของคุณพยายามในการแก้ไขชื่อโฮสต์และมันตรงกับรายการใน /etc/hosts ระบบจะไม่พยายามที่จะค้นหาเรคคอร์ดใน DNS ในการกำหนดค่าบางรายการ โดยเฉพาะเมื่อไม่จำเป็นต้องใช้งานอินเทอร์เน็ต เซิร์ฟเวอร์ที่ติดต่อกับจำนวนจำกัดของทรัพยากรสามารถกำหนดให้ใช้ชื่อโฮสต์แบบคงที่แทนการใช้ DNS ได้สะดวกสบาย

ต่อไปนี้คือตัวอย่างของไฟล์ hosts ที่เครื่องแม่ข่ายหลายตัวได้รับการระบุด้วยชื่อโฮสต์ง่ายๆ โดยมีชื่อเล่นและชื่อโดเมนแบบเต็ม (Fully Qualified Domain Names - FQDN's) เทียบเท่ากัน:

```
127.0.0.1   localhost
127.0.1.1   ubuntu-server
10.0.0.11   server1 server1.example.com vpn
10.0.0.12   server2 server2.example.com mail
10.0.0.13   server3 server3.example.com www
10.0.0.14   server4 server4.example.com file
```

## การกำหนดค่าระบบบริการชื่อ (Name Service Switch configuration)
การเรียงลำดับที่ระบบของคุณเลือกวิธีการแปลงชื่อโฮสต์เป็นที่อยู่ IP ควบคุมโดยไฟล์กำหนดค่า Name Service Switch (NSS) /etc/nsswitch.conf ตามที่กล่าวถึงในส่วนก่อนหน้านี้ โดยทั่วไปชื่อโฮสต์แบบคงที่ที่กำหนดไว้ในไฟล์ /etc/hosts ของระบบจะมีความสำคัญกว่าชื่อที่แปลงมาจาก DNS ต่อไปนี้คือตัวอย่างของบรรทัดที่รับผิดชอบสำหรับลำดับการค้นหาชื่อโฮสต์ในไฟล์ /etc/nsswitch.conf.

```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```


เพื่อปรับเปลี่ยนลำดับของวิธีการแก้ไขชื่อเหล่านี้ คุณสามารถเปลี่ยน string ของ hosts: เป็นค่าตามที่คุณต้องการได้โดยง่าย ตัวอย่างเช่น หากคุณต้องการใช้การแก้ไขชื่อ DNS แบบ unicast เดิม คุณสามารถเปลี่ยน string ใน /etc/nsswitch.conf ดังต่อไปนี้
```
hosts:          files dns [NOTFOUND=return] mdns4_minimal mdns4
```

# การเชื่อมต่อระหว่างอินเตอร์เฟซหลายตัว (Bridging multiple interfaces)
การสร้างสะพาน (Bridging) เป็นการกำหนดค่าที่ขั้นสูงมาก แต่มีประโยชน์มากในสถานการณ์หลายอย่าง หนึ่งในสถานการณ์คือการตั้งค่าสะพานที่มีหลายอินเตอร์เฟซ แล้วใช้ไฟร์วอล (Firewall) เพื่อกรองการจราจรระหว่างเซ็กเมนต์เครือข่ายสองเครือข่าย เคสอื่นๆ คือการใช้สะพานบนระบบที่มีอินเตอร์เฟสเดียวเพื่อให้เครื่องเสมือนมีการเข้าถึงเครือข่ายภายนอกโดยตรง ดังตัวอย่างต่อไปนี้

กำหนดค่าสะพานโดยการแก้ไขการกำหนดค่า netplan ที่คุณพบใน /etc/netplan/ โดยป้อนค่าที่เหมาะสมสำหรับอินเตอร์เฟซทางกายภาพและเครือข่ายของคุณ
```
network:
  version: 2
  renderer: networkd
  ethernets:
    enp3s0:
      dhcp4: no
  bridges:
    br0:
      dhcp4: yes
      interfaces:
        - enp3s0
```

จากนั้นกำหนดค่าเพื่อเปิดใช้งานสะพานนี้
```
sudo netplan apply
```

# networkd-dispatcher สคริปต์แบบฮุก (networkd-dispatcher for hook scripts)


ผู้ใช้ของ ifupdown เก่าอาจคุ้นเคยกับการใช้สคริปต์ฮุก (เช่น pre-up, post-up) ในไฟล์อินเทอร์เฟซของพวกเขา Netplan configuration ณ ขณะนี้ไม่รองรับสคริปต์ฮุกในการกำหนดค่าของมัน

แทนที่จะใช้คุณลักษณะนี้ด้วย networkd renderer, ผู้ใช้สามารถใช้ networkd-dispatcher แทน แพ็คเกจจะให้จุดฮุกแก่ผู้ใช้และแพ็คเกจเมื่อสถานะเครือข่ายที่เฉพาะเจาะจงถึง เพื่อช่วยในการตอบสนองต่อสถานะเครือข่าย

คำถามที่พบบ่อยเกี่ยวกับ Netplan มีตารางที่ดีที่สุดที่เปรียบเทียบการทำงานของเหตุการณ์ระหว่าง ```ifupdown/systemd-networkd/network-manager.```

สิ่งสำคัญที่สำคัญต้องรับรู้คือสคริปต์ฮุกเหล่านี้ทำงานแบบไม่เดียวกัน; กล่าวคือ พวกเขาจะไม่บล็อกการเปลี่ยนแปลงไปยังสถานะอื่น

คำถามที่พบบ่อยของ Netplan ยังมีตัวอย่างเกี่ยวกับการแปลงสคริปต์เก่า ```ifupdown``` เป็น ```networkd-dispatcher.```

# Reference
- The [Ubuntu Wiki Network page](https://help.ubuntu.com/community/Network?_gl=1*yktmvq*_gcl_au*OTk3OTMxNTgwLjE3MDc0MDY5MzU.&_ga=2.263849676.1127208396.1707543738-507412952.1707406933) has links to articles covering more advanced network configuration.
- The [Netplan website](https://netplan.io/?_gl=1*1gfulqr*_gcl_au*OTk3OTMxNTgwLjE3MDc0MDY5MzU.&_ga=2.32063614.1127208396.1707543738-507412952.1707406933) has additional [examples](https://netplan.readthedocs.io/en/stable/netplan-yaml/#) and documentation.
- The [Netplan man page](https://manpages.ubuntu.com/manpages/focal/man5/netplan.5.html?_gl=1*dq3wj5*_gcl_au*OTk3OTMxNTgwLjE3MDc0MDY5MzU.&_ga=2.24773626.1127208396.1707543738-507412952.1707406933) has more information on Netplan.
- The [systemd-resolved man page](https://manpages.ubuntu.com/manpages/focal/man8/systemd-resolved.8.html?_gl=1*dq3wj5*_gcl_au*OTk3OTMxNTgwLjE3MDc0MDY5MzU.&_ga=2.24773626.1127208396.1707543738-507412952.1707406933) has more information on systemd-resolved service.
- For more information on bridging see the [netplan.io examples page](https://netplan.readthedocs.io/en/stable/netplan-yaml/#properties-for-device-type-bridges)
- [Configuring networks](https://ubuntu.com/server/docs/network-configuration)
