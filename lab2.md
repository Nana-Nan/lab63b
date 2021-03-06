# การทดลองที่ 2 เรื่อง การเขียนโปรแกรมค้นหาไวไฟ

## วัตถุประสงค์
1. เพื่อทำการค้นหาไวไฟที่อยู่บริเวณนั้นโดยใช้ไมโครคอนโทรลเลอร์
2. เพื่อทำความเข้าใจการเขียนโปรแกรมลงในไมโครคอนโทรลเลอร์

## อุปกรณ์ที่ใช้
1. ไมโครคอนโทรลเลอร์ ESP-01

   ![Image](https://cdn-images-1.medium.com/max/1200/1*RMM4luR-BC8yrsDbmSlkBA.png)

2. USB to serial port

   ![Image](https://daneshjookit.com/5924-home_default/esp8266-to-usb.jpg)

3. อุปกรณ์ต่อพ่วง USB
4. อุปกรณ์เขียนโปรแกรม เช่น คอมพิวเตอร์ โน้ตบุ๊ค ฯลฯ

## ศึกษาข้อมูลเบื้องต้น
1. การติดตั้งโปรแกรม
   * [การเตรียมโปรแกรม](https://youtu.be/9aF0upI9Gic)
   * [ตัวอย่างการลงโปรแกรม](https://youtu.be/ocrGdJoP90Y)
   * [ไฟล์ตัวอย่างโปรแกรม](https://github.com/choompol-boonmee/lab63b/tree/master/examples)
2. ข้อมูลเกี่ยวกับซอร์ฟแวร์ที่จะใช้เขียนโปรแกรม  
   * [platform io](https://platformio.org/)
3. [ข้อมูลเกี่ยวกับไมโครคอนโทรลเลอร์ ESP-01](https://docs.platformio.org/en/latest/boards/espressif8266/esp01_1m.html)
4. [ตัวอย่างการทดลอง](https://youtu.be/yBjab0UNuB8)

## วิธีการทำการทดลอง
1. เริ่มจากการต่อ USB to serial port เข้ากับคอมพิวเตอร์โดยอุปกรณ์พ่วง USB และนำไมโครคอนโทรลเลอร์ต่อเข้ากับ USB to serial port
   ![Image](https://github.com/Nana-Nan/image/blob/main/1-3.jpg)
2. เปิด command prompt เข้าไปยังโฟลเดอร์ที่มีตัวอย่างโปรแกรม โดยในที่นี้จะใช้ตัวอย่าง 02_Scan-Wifi
3. อัปโหลดโปรแกรมลงในไมโครคอนโทรเลอร์ โดยใช้คำสั่ง **pio run -t upload**
   ![Image](https://github.com/Nana-Nan/image/blob/main/2-1.jpg)
4. ในขณะที่โปรแกรมกำลังรัน ให้ไปกดที่ปุ่มดำของบอร์ดค้างไว้ แล้วกดปุ่มแดง 1 ครั้งเพื่อรีเซ็ท
   ![Image](https://github.com/Nana-Nan/image/blob/main/2-2.jpg)
5. เมื่อโปรแกรมรันเสร็จให้ใช้คำสั่ง **pio device monitor** เพื่อดูผลลัพธ์ที่แสดงผลออกมาจากคอมพิวเตอร์
   ![Image](https://github.com/Nana-Nan/image/blob/main/2-3.jpg)
6. ให้กดปุ่มรีเซ็ท (ปุ่มแดง) บันทึกผลการทดลอง

## การบันทึกผลการทดลอง
   เจอสัญญาณไวไฟดังภาพ
   ![Image](https://github.com/Nana-Nan/image/blob/main/2-4.jpg)
   
## อภิปรายผลการทดลอง
   จากการทดลอง ในการค้นหาไวไฟโดยใช้โปรแกรมจากตัวไมโครคอนโทรลเลอร์ ในหน้าต่างแสดงผลเจอสัญญาณไวไฟอยู่เรื่อย ๆ ตามสัญญาณที่เข้ามา ณ ขณะนั้น โดยเมื่อกดปุ่ม reset จะเป็นการเริ่มทำการค้นหาใหม่
## คำถามหลังการทดลอง
* จงยกตัวอย่างสาเหตุที่ทำสัญญาณไวไฟขาด ๆ หาย ๆ
   
   ตอบ
   * มีคลื่นสัญญาณอื่นรบกวน
   * สัญญาณไวไฟมีระยะ และกำลังส่งไม่พอ
   
