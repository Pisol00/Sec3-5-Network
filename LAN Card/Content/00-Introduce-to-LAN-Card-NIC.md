# 00-Introduce-to-LAN-Card-NIC

## What is LAN Card ?

**Local Area Network (LAN) Card** หรือที่เรียกว่าการ์ดส่วนต่อประสานเครือข่าย **(Network Interface card/NIC)** เป็นอุปกรณ์ฮาร์ดแวร์ที่ออกแบบมาเพื่อให้คอมพิวเตอร์สามารถสื่อสารกันผ่านระบบเครือข่ายได้ ทำให้คอมพิวเตอร์มีการเชื่อมต่อกับเครือข่ายอย่างเสถียรและตลอดเวลา

> การ์ด LAN (LAN card) เป็นหนึ่งในประเภทของ Network Interface Card (NIC) อาจสามารถต่อด้วยสาย Ethernet หรือเป็นแบบไร้สายก็ได้ (Wireless LAN card)
> 

**Ethernet LAN Card**

![*[ภาพที่ 1] LAN Card TP-Link Network TX201 2.5 Gigabit PCIe Network Adapter*](00-Introduce-to-LAN-Card-NIC%205efda9b228a7417c907c5e43f34080aa/LanCard_ethernet.jpg)

*[ภาพที่ 1] LAN Card TP-Link Network TX201 2.5 Gigabit PCIe Network Adapter*

**Wireless LAN card**

![*[ภาพที่ 2] LAN Card TP-Link AX3000 (ARCHER TX55E) WI-FI 6 Bluetooth 5.2 PCIE Adapter*](00-Introduce-to-LAN-Card-NIC%205efda9b228a7417c907c5e43f34080aa/LanCard_wireless.jpg)

*[ภาพที่ 2] LAN Card TP-Link AX3000 (ARCHER TX55E) WI-FI 6 Bluetooth 5.2 PCIE Adapter*

## Functional of LAN Card

**จุดประสงค์หลัก**ของ LAN Card คือการสร้างการเชื่อมต่อทางกายภาพซึ่งเป็นเสมือนประตูสู่โลกอินเตอร์เน็ต โดยมีฟังก์ชั่นการทำงานดังนี้

1. สร้างการเชื่อมต่อทางกายภาพสำหรับเครือข่ายและทำงานผ่านอินเตอร์เฟซตามที่กำหนดไว้
2. LAN Card ทำหน้าที่ให้ข้อมูลลิงค์ซึ่งเป็นส่วนหนึ่งของการเชื่อมโยงผ่าน Open System Interconnection (OSI) Model
3. LAN Card ส่งและรับข้อมูลแบบไบนารีจากเครือข่ายและตรวจสอบข้อผิดพลาดของข้อมูล โดยแสงสองสีบนการ์ด LAN จะแสดงสถานะการทำงานและการเชื่อมต่อเครือข่าย

**LAN Card** จะทำการสื่อสารกับ router โดยใช้คลื่นวิทยุและเสาอากาศ ซึ่งคอมพิวเตอร์แปลงข้อมูลเป็นรูปแบบไบนารีส่งไปเพื่อให้ router รับได้ และ router จะส่งข้อมูลกลับในรูปแบบแพ็กเก็ตข้อมูล 

> โดยทั่วไปเครือข่ายไร้สายจะส่งสัญญาณที่ความถี่ระหว่าง 2.4 - 5 KHz เพื่อให้เหมาะสมกับการถ่ายโอนข้อมูลปริมาณมากอย่างรวดเร็ว
> 

## Function In LINUX and how is it important ?

| Function | รายละเอียด |
| --- | --- |
| เชื่อมต่อกับเครือข่าย LAN | LAN card เป็นส่วนหนึ่งของ NIC ที่ใช้สำหรับเชื่อมต่อคอมพิวเตอร์กับเครือข่าย LAN โดยใช้สายสัญญาณ Ethernet เพื่อสื่อสารในเครือข่ายในขอบเขตที่ระบุไว้ |
| การกำหนด IP Address | ช่วยให้เครื่อง Linux มี IP address บนเครือข่าย LAN ทำให้สามารถระบุตัวตนและสื่อสารกับอุปกรณ์อื่นในเครือข่ายได้ |
| การส่งและรับข้อมูล | รับผิดชอบในการส่งและรับข้อมูลในเครือข่าย LAN โดยรับข้อมูลจากเครือข่ายและส่งข้อมูลไปยังเครือข่ายให้ถูกต้องตาม protocol ที่ใช้งาน |
| การควบคุมการเชื่อมต่อ | สามารถควบคุมการเชื่อมต่อและการรับส่งข้อมูลในเครือข่าย LAN ได้โดยตรง โดยสามารถใช้ command หรือการตั้งค่าที่เกี่ยวข้องในระบบปฏิบัติการ Linux |
| การจัดการข้อมูลระดับชั้น | รับผิดชอบในการจัดการข้อมูลระดับเชื่อมต่อ (link level) รวมถึงการตรวจสอบข้อผิดพลาดในการส่งและรับข้อมูล เพื่อให้การสื่อสารเป็นไปอย่างเสถียรและมีประสิทธิภาพ |

## What is NIC ?

**การ์ดเครือข่าย (Network Interface Card หรือ NIC)** หรือที่เรียกกันอีกชื่อว่า LAN adapter เป็นอุปกรณ์ฮาร์ดแวร์ที่สำคัญที่ติดตั้งในอุปกรณ์ เช่น คอมพิวเตอร์ เซิร์ฟเวอร์ และเครื่องพิมพ์ เพื่อเปิดใช้งานการเชื่อมต่อเครือข่าย ถ้าไม่มี NIC เครื่องมือนั้นจะไม่สามารถเชื่อมต่อหรือสื่อสารกับอุปกรณ์อื่นในเครือข่ายได้ ทำให้เป็นส่วนประสำคัญสำหรับการเชื่อมต่อเครือข่ายใด ๆ

![*[ภาพที่ 3] **Network Interface Card ที่ใช้เป็นตัวเชื่อมต่อกับระบบเครือข่าย***](00-Introduce-to-LAN-Card-NIC%205efda9b228a7417c907c5e43f34080aa/NIC_Connect.jpg)

*[ภาพที่ 3] **Network Interface Card ที่ใช้เป็นตัวเชื่อมต่อกับระบบเครือข่าย***

**ยกตัวอย่างสถานการณ์ที่ใช้ทำงาน :**

- หากต้องการเชื่อมต่อคอมพิวเตอร์กับเครือข่ายหรือระบบคอมพิวเตอร์อื่น ๆ จำเป็นต้องมีการ์ด NIC ติดตั้งในคอมพิวเตอร์ ซึ่งจะให้คอมพิวเตอร์ได้รับ MAC address ที่ไม่เหมือนกันซึ่งช่วยในการเชื่อมต่อกับผ่านอินเตอร์เน็ตได้
- หากบริษัทที่มีคอมพิวเตอร์หลายร้อยเครื่อง ต้องการสร้างเครือข่ายภายในในบริษัท ก็ต้องการการ์ด NIC บนทุกคอมพิวเตอร์หรือแล็ปท็อปเพื่อให้ทุกคอมพิวเตอร์สามารถเชื่อมต่อกับกันได้ ดังนั้นการ์ด NIC จะให้เราได้รับ network interface

> ทุก NIC card มี MAC address ที่ไม่เหมือนกันซึ่งไม่สามารถเปลี่ยนแปลงได้เนื่องจากที่อยู่นี้ถูกกำหนดให้ที่โรงงานที่ผลิต NIC แล้ว
> 

## What is MAC Address ?

MAC address (Media Access Control address) เป็น physical address ที่ได้รับการกำหนดโดยผู้ผลิตบนการ์ดอินเทอร์เฟซเครือข่าย (Network Interface Card หรือ NIC) ซึ่งใช้เพื่อระบุที่อยู่จำเพาะบนอุปกรณ์โดยมีเลขรหัสไม่ซ้ำกัน

> เป็นเลขชุดที่อยู่ 48 บิต ประกอบด้วยเซ็ตหกชุดของตัวอักษรสิบหกตัวเลขฐานสิบหก ทุกชุดประกอบด้วยที่อยู่ 8 บิต ซึ่งแยกกันด้วยเครื่องหมายโคลอน (:) เช่น 2A:1B:55:23:5A:B3
> 

## Component of NIC

การ์ดเครือข่ายหรือการ์ด LAN ประกอบด้วยส่วนประกอบหลายชิ้น แต่ละส่วนมีหน้าที่ที่แตกต่างกันไป

| Component | หน้าที่ |
| --- | --- |
| ตัวควบคุม (controller) | ประมวลผลข้อมูลที่ได้รับและกำหนดประสิทธิภาพของการ์ดเครือข่าย |
| ช่องสำหรับบูต ROM (boot ROM socket) | ช่วยให้เครื่องทำงานโดยไม่ต้องมีดิสก์ เชื่อมต่อกับเครือข่ายได้ |
| NIC port for cable/transceiver | เชื่อมต่อกับสาย Ethernet หรือตัวรับสัญญาณ (transceiver) ให้สร้างและรับสัญญาณอิเล็กทรอนิกส์ |
| อินเตอร์เฟสของบัส (bus interface) | เชื่อมต่อระหว่างการ์ดเครือข่ายกับคอมพิวเตอร์หรือเซิร์ฟเวอร์ |
| ไฟ LED | แสดงสถานะการทำงานของการ์ดเครือข่าย |
| Profile bracket | มีขนาดสองขนาดช่วยให้การ์ดเครือข่ายติดตั้งในช่องขยายของคอมพิวเตอร์หรือเซิร์ฟเวอร์ได้อย่างมั่นคง |

## Type of NIC

มีการจำแนกได้เป็น 4 ประเภทใหญ่ๆคือ 

1. Bus Interfaces Based Classification
    1. การ์ดเครือข่ายประเภท **ISA** (Industry Standard Architecture) : มีความเร็วของการ์ดที่ต่ำเพียง 9Mbps ตอนนี้อินเทอร์เฟสของบัส ISA ไม่ได้ใช้งานอีกต่อไป
    2. การ์ดเครือข่ายประเภท **PCI** (Peripheral Component Interconnect) : มีความกว้างคงที่ของ 32 บิต (การส่งข้อมูลที่ 133MB/s) และ 64 บิต (การส่งข้อมูลที่ 266MB/s) การ์ด NIC ประเภทนี้เริ่มใช้กับเซิร์ฟเวอร์ก่อนแล้วค่อยๆ ใช้กับ PC ลูกค้า
    3. การ์ดเครือข่ายประเภท **PCI-X** (Peripheral Component Interconnect eXtended) : เป็นเทคโนโลยีบัส PCI ที่ปรับปรุงแล้ว มันทำงานที่ 64 บิต และสามารถถ่ายโอนข้อมูลได้สูงสุดถึง 1064 MB/s
    4. การ์ดเครือข่ายประเภท **PCIe** (Peripheral Component Interconnect Express) เป็นมาตรฐานล่าสุดและในปัจจุบันเป็นที่นิยมในเมนบอร์ดคอมพิวเตอร์และเซิร์ฟเวอร์ การ์ด NIC
    5. USB (Universal Serial Bus) network interface card : เป็นมาตรฐานบัสภายนอก มีรุ่นทั้งหมดสามรุ่นที่มีอัตราการส่งข้อมูลแตกต่างกัน และสามารถทำงานร่วมกับอุปกรณ์หลายรูปแบบได้ นอกจากนี้ การ์ดเครือข่ายไร้สายก็เป็นประเภทหนึ่งของการ์ด NIC ที่ออกแบบสำหรับการเชื่อมต่อ Wi-Fi
2. Application Field Based Classification - Computer NIC และ Server Network card
3. Network Connection Based Classifications - Wired NIC และ Wireless NIC
4. Transmission Speed Based Classifications
    1. **10 Mbps** : เหมาะสำหรับการใช้งานทั่วไป
    2. **100 Mbps** : การใช้งานที่ต้องการความเร็วในระดับนึง เช่น การดาวน์โหลดไฟล์ขนาดใหญ่
    3. **1000 Mbps (1 Gbps)**: เหมาะสำหรับการใช้งานที่ต้องการความเร็วสูง เช่น Streaming video

## Functional of NIC

หน้าที่หลักของ Network Interface Card (NIC) ประกอบด้วย:

1. NIC ให้**ความเชื่อมต่อทางกายภาพระหว่างอุปกรณ์กับเครือข่าย** โดย NIC แบบมีสายจะใช้สาย Ethernet เพื่อเชื่อมต่อกับเครือข่ายในขณะที่ NIC แบบไร้สายจะใช้คลื่นวิทยุในการเชื่อมต่อแบบไร้สาย
2. **เป็นผู้รับผิดชอบในการส่งข้อมูลและรับข้อมูล**ระหว่างอุปกรณ์และอุปกรณ์อื่นในเครือข่าย
3. **แปลงข้อมูลให้อยู่ในรูปแบบที่สามารถส่งผ่านเครือข่ายได้** และจากนั้นกลับมาเป็นรูปแบบที่อุปกรณ์สามารถเข้าใจได้
4. NIC มีความสามารถในการ**ตรวจจับและแก้ไขข้อผิดพลาด**เพื่อให้แน่ใจว่าข้อมูลถูกส่งไปอย่างถูกต้องและเชื่อถือได้ (error detection and correction)
5. NIC จัดการการจราจรในเครือข่ายโดยการกำหนด**ลำดับความสำคัญของข้อมูล**บางประเภทหรือ จำกัดการส่งข้อมูลเพื่อป้องกันการแออัดในเครือข่าย
6. ให้คุณสมบัติ**ด้านความปลอดภัย**ของเครือข่าย เช่น การเข้ารหัสหรือการตรวจสอบสิทธิ์เพื่อป้องกันการเข้าถึงที่ไม่ได้รับอนุญาตหรือการละเมิดข้อมูล

## How NIC transmits and receive the data?

การส่งข้อมูลของ NIC :

- สำหรับข้อมูลที่ออกไป ก่อนอื่นโปรโตคอลเครือข่ายจะถ่ายโอนแพ็กเก็ตไปยังบัฟเฟอร์ที่อยู่บนการ์ด NIC
- จากนั้นที่อยู่ MAC ต้นทางและปลายทางถูกเพิ่มเป็นส่วนหัวของเฟรมและคำนวณ CRC
- **CRC (Cyclic Redundancy Code)** เป็นค่าตัวเลข ซึ่งเป็นชนิดของ checksum ที่มีวัตถุประสงค์ในการตรวจสอบข้อผิดพลาดสุดท้าย NIC จะส่งเฟรมลงไปบนสื่อเป็นสัญญาณบิต

การรับข้อมูลของ NIC :

- สัญญาณบิตเดินทางพร้อมกับสื่อและถูกรับโดย NIC จากนั้นบิตที่ได้รับจะถูกจัดรูปเป็นเฟรม
- ก่อนอื่นจะคำนวณ CRC (ชนิดหนึ่งของ checksum) และเปรียบเทียบกับ CRC ในตัวช่องสัญญาณของเฟรม
- หากพบว่าไม่ตรงกัน นั่นหมายความว่าเฟรมเสียหายหรือเปลี่ยนแปลงและเฟรมจะถูก drop ทิ้ง
- หาก CRC ถูกต้อง จะทำการตรวจสอบที่อยู่ MAC ปลายทาง
- เมื่อที่อยู่ MAC ถูกตรวจสอบและตรวจสอบแล้ว ส่วนหัวและท้ายเฟรมจะถูกนำออกและแพ็กเก็ตจะออกมาจากเฟรม ซึ่งจะถูกส่งให้โปรโตคอลเครือข่ายสำหรับการประมวลผลเพิ่มเติม

## How NIC is important to LINUX ?

![*[ภาพที่ 4] **Network Interface Card ในระบบปฏิบัติการของ linux***](00-Introduce-to-LAN-Card-NIC%205efda9b228a7417c907c5e43f34080aa/LINUXandNIC.jpg)

*[ภาพที่ 4] **Network Interface Card ในระบบปฏิบัติการของ linux***

ในระบบปฏิบัติการ Linux Network Interface Card หรือ NIC เป็นสิ่งสำคัญเมื่อเทียบกับระบบปฏิบัติการอื่น ๆ พื้นฐานแล้ว มันช่วยให้ระบบ Linux เชื่อมต่อและสื่อสารกับเครือข่ายได้ 

NIC รับผิดชอบในการส่งและรับแพ็กเก็ตข้อมูลไปยังและจากเครือข่าย นอกจากนี้ มันยังมีบทบาทสำคัญในการจัดการการจราจรในเครือข่าย การรักษาความสมบูรณ์ของข้อมูล และการให้ความปลอดภัยในเครือข่าย ด้วยปริมาณงานบริการและเครือข่ายที่รันบนระบบ Linux NIC เป็นองค์ประกอบที่ขาดไม่ได้สำหรับการดำเนินงานบน Linux ที่ประสบความสำเร็จ

## Reference

1. Mary McMahon. (2024). How Does a LAN Card Work? [https://www.easytechjunkie.com/how-does-a-lan-card-work.htm](https://www.easytechjunkie.com/how-does-a-lan-card-work.htm)
2. Irving. (2021). What Is a Network Interface Card - NIC Definition, Function & Types. [https://community.fs.com/article/nic-card-guide-for-beginners-functions-types-and-selection-tips.html](https://community.fs.com/article/nic-card-guide-for-beginners-functions-types-and-selection-tips.html)
3. Prashant. What is NIC (Network Interface Card)? How NIC works? [https://thestudygenius.com/what-is-nic-network-interface-card/](https://thestudygenius.com/what-is-nic-network-interface-card/)
4. What is LAN card? ****[https://www.assignmenthelp.net/assignment_help/what-is-lan-card](https://www.assignmenthelp.net/assignment_help/what-is-lan-card)
5. [ภาพที่ 1]. BaNANA. TP-Link Network TX201 2.5 Gigabit PCIe Network Adapter. [https://www.bnn.in.th/th/p/tp-link-network-tx201-25-gigabit-pcie-network-adapter-4897098687833-87_zvevok?srsltid=AfmBOorGXfY7-bVVdNbO9mEdbKyMkGTaTjf0cksPQK6kMmYSuV2_b-5e9HQ](https://www.bnn.in.th/th/p/tp-link-network-tx201-25-gigabit-pcie-network-adapter-4897098687833-87_zvevok?srsltid=AfmBOorGXfY7-bVVdNbO9mEdbKyMkGTaTjf0cksPQK6kMmYSuV2_b-5e9HQ)
6. [ภาพที่ 2]. iHAVECPU. TP-Link AX3000 (ARCHER TX55E) WI-FI 6 Bluetooth 5.2 PCIE Adapter. [https://www.ihavecpu.com/detailproduct/9976/TP-LINK-AX3000-(ARCHER-TX55E)-WI-FI-6-BLUETOOTH-5.2-PCIE-ADAPTER?srsltid=AfmBOopH4t2LKtuuiLhQdTmL2owMlPvkC8R9t8GKU2wJJqMpRLJvt9RMMMg](https://www.ihavecpu.com/detailproduct/9976/TP-LINK-AX3000-(ARCHER-TX55E)-WI-FI-6-BLUETOOTH-5.2-PCIE-ADAPTER?srsltid=AfmBOopH4t2LKtuuiLhQdTmL2owMlPvkC8R9t8GKU2wJJqMpRLJvt9RMMMg)
7. [ภาพที่ 3]. Irving. (2021). What Is a Network Interface Card - NIC Definition, Function & Types. [https://community.fs.com/article/nic-card-guide-for-beginners-functions-types-and-selection-tips.html](https://community.fs.com/article/nic-card-guide-for-beginners-functions-types-and-selection-tips.html)
8. [ภาพที่ 4]. (2018). Syn1588_PCIe_NIC_-_Issue_Linux_kernel_4.14__and_NIC_not_visible.jpg [https://www.oreganosystems.at/about-us/news/syn1588r-pcie-nic-issue-linux-kernel-414-and-nic-not-visible](https://www.oreganosystems.at/about-us/news/syn1588r-pcie-nic-issue-linux-kernel-414-and-nic-not-visible)