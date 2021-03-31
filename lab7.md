# การทดลองที่ 7 เรื่อง การเชื่อมต่อ WIFI อัตโนมัติ

## วัตถุประสงค์
1. เพื่อให้เข้าใจการเขียนโปรแกรมลงในไมโครคอนโทรลเลอร์
2. เพื่อสร้างอุปกรณ์ในการเชื่อมต่อ WIFI อัตโนมัติ

## อุปกรณ์ที่ใช้
1. ไมโครคอนโทรลเลอร์ ESP-01
2. USB to serial port
3. อุปกรณ์ต่อพ่วง USB
4. อุปกรณ์เขียนโปรแกรม เช่น คอมพิวเตอร์ โน้ตบุ๊ค ฯลฯ

## ศึกษาข้อมูลเบื้องต้น
1. การติดตั้งโปรแกรม
   * [การเตรียมโปรแกรม](https://youtu.be/9aF0upI9Gic)
   * [ตัวอย่างการลงโปรแกรม](https://youtu.be/ocrGdJoP90Y)
2. ข้อมูลเกี่ยวกับซอร์ฟแวร์ที่จะใช้เขียนโปรแกรม  
   * [platform io](https://platformio.org/)
3. [ข้อมูลเกี่ยวกับไมโครคอนโทรลเลอร์ ESP-01](https://docs.platformio.org/en/latest/boards/espressif8266/esp01_1m.html)
4. อ้างอิง
   *[การใช้งาน ESP8266](http://99thai.com/data/up_show.php?id=1523293577&web=epost)

## วิธีการทำการทดลอง
1. เริ่มจากการต่อ USB to serial port เข้ากับคอมพิวเตอร์โดยอุปกรณ์พ่วง USB และนำไมโครคอนโทรลเลอร์ต่อเข้ากับ USB to serial port
2. อัปโหลด  code โปรแกรมลงในโฟลเดอร์ของเครื่องคอมพิวเตอร์
3. เปิด command prompt เข้าไปยังโฟลเดอร์ที่มีตัวอย่างโปรแกรม แล้ว **cd ชื่อไฟล์โปรแกรม**
4. อัปโหลดโปรแกรมลงในไมโครคอนโทรเลอร์ โดยใช้คำสั่ง **pio run -t upload**
5. ในขณะที่โปรแกรมกำลังรัน ให้ไปกดที่ปุ่มดำของบอร์ดค้างไว้ แล้วกดปุ่มแดง 1 ครั้งเพื่อรีเซ็ท
6. เมื่อโปรแกรมรันเสร็จให้ใช้คำสั่ง **pio device monitor** เพื่อดูผลลัพธ์ที่แสดงผลออกมาจากคอมพิวเตอร์
7. ให้กดปุ่มรีเซ็ท (ปุ่มแดง) บันทึกผลการทดลอง

## การบันทึกผลการทดลอง
   

## อภิปรายผลการทดลอง
   จากการทดลอง 
## คำถามหลังการทดลอง
* 

   ตอบ