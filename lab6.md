# การทดลองที่ 6 เรื่อง การเขียนโปรแกรมสร้างไวไฟแอคเซสพอยต์ (Wifi AP)

## วัตถุประสงค์
1. เพื่อเขียนโปรแกรมลงในไมโครคอนโทรลเลอร์
2. เพื่อสร้างสัญญาณไวไฟ โดยใช้ไมโครคอนโทรลเลอร์ในการปล่อยสัญญาณ

## อุปกรณ์ที่ใช้
1. ไมโครคอนโทรลเลอร์ ESP-01

   ![Image](https://cdn-images-1.medium.com/max/1200/1*RMM4luR-BC8yrsDbmSlkBA.png)

2. USB to serial port

   ![Image](https://daneshjookit.com/5924-home_default/esp8266-to-usb.jpg)

3. อุปกรณ์ต่อพ่วง USB
4. อุปกรณ์เขียนโปรแกรม เช่น คอมพิวเตอร์ โน้ตบุ๊ค ฯลฯ

## ศึกษาข้อมูลเบื้องต้น

## วิธีการทำการทดลอง
1. เริ่มจากการต่อ USB to serial port เข้ากับคอมพิวเตอร์โดยอุปกรณ์พ่วง USB และนำไมโครคอนโทรลเลอร์ต่อเข้ากับ USB to serial port

   ![Image](https://github.com/Nana-Nan/image/blob/main/1-3.jpg)
   
2. เปิด command prompt เข้าไปยังโฟลเดอร์ที่มีตัวอย่างโปรแกรม โดยในที่นี้จะใช้ตัวอย่าง 06_Wifi-AP-Web-Server

   ![Image](https://github.com/Nana-Nan/image/blob/main/6-1.jpg)

3. อัปโหลดโปรแกรมลงในไมโครคอนโทรเลอร์ โดยใช้คำสั่ง **pio run -t upload**

   ![Image](https://github.com/Nana-Nan/image/blob/main/6-2.jpg)

4. ในขณะที่โปรแกรมกำลังรัน ให้ไปกดที่ปุ่มดำของบอร์ดค้างไว้ แล้วกดปุ่มแดง 1 ครั้งเพื่อรีเซ็ท

   ![Image](https://github.com/Nana-Nan/image/blob/main/6-3.jpg)

5. เมื่อโปรแกรมรันเสร็จให้ใช้คำสั่ง **pio device monitor** เพื่อดูผลลัพธ์ที่แสดงผลออกมาจากคอมพิวเตอร์

   ![Image](https://github.com/Nana-Nan/image/blob/main/6-4.jpg)

6. ใช้โทรศัพท์มือถือค้นหาไวไฟ บันทึกผลการทดลอง

## การบันทึกผลการทดลอง
   จากการทดลองเมื่อรันโปรแกรมเสร็จเรียบร้อย
   
   ![Image](https://github.com/Nana-Nan/image/blob/main/6-5.jpg)
   
   และเมื่อทำการค้นหาจากโทรศัพท์
   
   ![Image](https://github.com/Nana-Nan/image/blob/main/6-6.jpg)   

## อภิปรายผลการทดลอง
   จากการทดลองตัวไมโครคอนโทรลเลอร์ ESP-01 สามารถสร้างไวไฟได้จริง เมื่อทำการค้นหาจากโทรศัพท์สามารถพบชื่อไวไฟตามที่ตั้งไว้คือ "TUENG-ESP-WIFI" และมีรหัสคือ "choompol"

## คำถามหลังการทดลอง
* 
