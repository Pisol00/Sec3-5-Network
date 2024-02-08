# 00-Introduce-to-LAN-Card-NIC

## What is LAN Card ?

**Local Area Network (LAN) Card** หรือที่เรียกว่าการ์ดส่วนต่อประสานเครือข่าย **(Network Interface card/NIC)** เป็นอุปกรณ์ฮาร์ดแวร์ที่ออกแบบมาเพื่อให้คอมพิวเตอร์สามารถสื่อสารกันผ่านระบบเครือข่ายได้ ทำให้คอมพิวเตอร์มีการเชื่อมต่อกับเครือข่ายอย่างเสถียรและตลอดเวลา

<aside>
♻️ การ์ด LAN (LAN card) เป็นหนึ่งในประเภทของ Network Interface Card (NIC) อาจสามารถต่อด้วยสาย Ethernet หรือเป็นแบบไร้สายก็ได้ (Wireless LAN card)

</aside>

**Ethernet LAN Card**

![*[ภาพที่ 1]* LAN Card TP-Link Network TX201 2.5 Gigabit PCIe Network Adapter](00-Introduce-to-LAN-Card-NIC%205efda9b228a7417c907c5e43f34080aa/LanCard_ethernet.jpg)

*[ภาพที่ 1]* LAN Card TP-Link Network TX201 2.5 Gigabit PCIe Network Adapter

**Wireless LAN card**

![*[ภาพที่ 2]* LAN Card TP-Link AX3000 (ARCHER TX55E) WI-FI 6 Bluetooth 5.2 PCIE Adapter](00-Introduce-to-LAN-Card-NIC%205efda9b228a7417c907c5e43f34080aa/LanCard_wireless.jpg)

*[ภาพที่ 2]* LAN Card TP-Link AX3000 (ARCHER TX55E) WI-FI 6 Bluetooth 5.2 PCIE Adapter

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

## sdfsdf

A Network Interface Card (NIC) is a physical component that connects to a computer's expansion slot, facilitating network communication. Modern computers and wireless devices often have an integrated network adapter, which can be an Ethernet controller on the motherboard or a small wireless chip. Network adapters can also be peripherals connecting to a USB port. While "NIC" and "network adapter" are often used interchangeably, a NIC is a type of network adapter, but not all network adapters are NICs.

## Reference

1. Mary McMahon. (2024). How Does a LAN Card Work? [https://www.easytechjunkie.com/how-does-a-lan-card-work.htm](https://www.easytechjunkie.com/how-does-a-lan-card-work.htm)
2. Prashant. What is NIC (Network Interface Card)? How NIC works? [https://thestudygenius.com/what-is-nic-network-interface-card/](https://thestudygenius.com/what-is-nic-network-interface-card/)
3. What is LAN card? ****[https://www.assignmenthelp.net/assignment_help/what-is-lan-card](https://www.assignmenthelp.net/assignment_help/what-is-lan-card)
4. [ภาพที่ 1]. BaNANA. TP-Link Network TX201 2.5 Gigabit PCIe Network Adapter. [https://www.bnn.in.th/th/p/tp-link-network-tx201-25-gigabit-pcie-network-adapter-4897098687833-87_zvevok?srsltid=AfmBOorGXfY7-bVVdNbO9mEdbKyMkGTaTjf0cksPQK6kMmYSuV2_b-5e9HQ](https://www.bnn.in.th/th/p/tp-link-network-tx201-25-gigabit-pcie-network-adapter-4897098687833-87_zvevok?srsltid=AfmBOorGXfY7-bVVdNbO9mEdbKyMkGTaTjf0cksPQK6kMmYSuV2_b-5e9HQ)
5. [ภาพที่ 2]. iHAVECPU. TP-Link AX3000 (ARCHER TX55E) WI-FI 6 Bluetooth 5.2 PCIE Adapter. [https://www.ihavecpu.com/detailproduct/9976/TP-LINK-AX3000-(ARCHER-TX55E)-WI-FI-6-BLUETOOTH-5.2-PCIE-ADAPTER?srsltid=AfmBOopH4t2LKtuuiLhQdTmL2owMlPvkC8R9t8GKU2wJJqMpRLJvt9RMMMg](https://www.ihavecpu.com/detailproduct/9976/TP-LINK-AX3000-(ARCHER-TX55E)-WI-FI-6-BLUETOOTH-5.2-PCIE-ADAPTER?srsltid=AfmBOopH4t2LKtuuiLhQdTmL2owMlPvkC8R9t8GKU2wJJqMpRLJvt9RMMMg)