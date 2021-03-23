# การทดลองที่ 5 เรื่อง การเขียนโปรแกรมเชื่อมต่อไวไฟและเว็บเซอร์เวอร์

## วัตถุประสงค์
1. เพื่อเขียนโปรแกรมลงในไมโครคอนโทรลเลอร์ 
2. เพื่อที่จะสร้างเว็บเซิร์ฟเวอร์ผ่านไวไฟ

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
4. [ตัวอย่างการทดลอง](https://youtu.be/VX-QNQcO-b4)

## วิธีการทำการทดลอง
1. เริ่มจากการต่อ USB to serial port เข้ากับคอมพิวเตอร์โดยอุปกรณ์พ่วง USB และนำไมโครคอนโทรลเลอร์ต่อเข้ากับ USB to serial port
   ![Image](https://github.com/Nana-Nan/image/blob/main/1-3.jpg)
2. เปิด command prompt เข้าไปยังโฟลเดอร์ที่มีตัวอย่างโปรแกรม โดยในที่นี้จะใช้ตัวอย่าง 05_Wifi-Web-Server
3. อัปโหลดโปรแกรมลงในไมโครคอนโทรเลอร์ โดยใช้คำสั่ง **pio run -t upload**
4. ในขณะที่โปรแกรมกำลังรัน ให้ไปกดที่ปุ่มดำของบอร์ดค้างไว้ แล้วกดปุ่มแดง 1 ครั้งเพื่อรีเซ็ท
5. เข้า web browser
      **คลิปมีปัญหา**
