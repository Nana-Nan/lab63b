# การทดลองที่ 3 เรื่อง การเขียนโปรแกรมเอ้าพุทสัญญาณดิจิทัล
## วัตถุประสงค์
1. เพื่อเขียนโปรแกรมลงในไมโครคอนโทรลเลอร์ และนำไปใช้งานในอุปกรณ์อื่น
2. เพื่อควบคุมการทำงานของรีเลย์

## อุปกรณ์ที่ใช้
1. ไมโครคอนโทรลเลอร์ ESP-01

   ![Image](https://cdn-images-1.medium.com/max/1200/1*RMM4luR-BC8yrsDbmSlkBA.png)

2. USB to serial port

   ![Image](https://daneshjookit.com/5924-home_default/esp8266-to-usb.jpg)

3. อุปกรณ์ต่อพ่วง USB
4. อุปกรณ์เขียนโปรแกรม เช่น คอมพิวเตอร์ โน้ตบุ๊ค ฯลฯ
5. Adapter ต่อ LED
6. รีเลย์

   ![Image](https://github.com/Nana-Nan/image/blob/main/3-6.jpg)

## ศึกษาข้อมูลเบื้องต้น
1. การติดตั้งโปรแกรม
   * [การเตรียมโปรแกรม](https://youtu.be/9aF0upI9Gic)
   * [ตัวอย่างการลงโปรแกรม](https://youtu.be/ocrGdJoP90Y)
   * [ไฟล์ตัวอย่างโปรแกรม](https://github.com/choompol-boonmee/lab63b/tree/master/examples)
2. ข้อมูลเกี่ยวกับซอร์ฟแวร์ที่จะใช้เขียนโปรแกรม  
   * [platform io](https://platformio.org/)
3. [ข้อมูลเกี่ยวกับไมโครคอนโทรลเลอร์ ESP-01](https://docs.platformio.org/en/latest/boards/espressif8266/esp01_1m.html)
4. ตัวอย่างการทดลอง
   [part 1](https://youtu.be/6JnhaUILGuw)
   [part 2](https://youtu.be/nFqoZT26U5k)
5. [รีเลย์ (relay)](http://www.psptech.co.th/%E0%B8%A3%E0%B8%B5%E0%B9%80%E0%B8%A5%E0%B8%A2%E0%B9%8Crelay%E0%B8%84%E0%B8%B7%E0%B8%AD%E0%B8%AD%E0%B8%B0%E0%B9%84%E0%B8%A3-15696.page)

## วิธีการทำการทดลอง
1. เริ่มจากการต่อ USB to serial port เข้ากับคอมพิวเตอร์โดยอุปกรณ์พ่วง USB และต่อ USB to serial port เข้ากับ Adapter สุดท้ายต่อ Adapte เข้ากับไมโครคอนโทรลเลอร์
  
  ![Image](https://github.com/Nana-Nan/image/blob/main/3-1.jpg)

2. เปิด command prompt เข้าไปยังโฟลเดอร์ที่มีตัวอย่างโปรแกรม โดยในที่นี้จะใช้ตัวอย่าง 03_Output-Port

3. อัปโหลดโปรแกรมลงในไมโครคอนโทรเลอร์ โดยใช้คำสั่ง **pio run -t upload**
   
   ![Image](https://github.com/Nana-Nan/image/blob/main/3-2.jpg)

4. ในขณะที่โปรแกรมกำลังรัน ให้ไปกดที่ปุ่มดำของบอร์ดค้างไว้ แล้วกดปุ่มแดง 1 ครั้งเพื่อรีเซ็ท
   
   ![Image](https://github.com/Nana-Nan/image/blob/main/3-3.jpg)

5. เมื่อโปรแกรมรันเสร็จให้ใช้คำสั่ง **pio device monitor** เพื่อดูผลลัพธ์ที่แสดงผลออกมาจากคอมพิวเตอร์
  
  ![Image](https://github.com/Nana-Nan/image/blob/main/3-4.jpg)

6. ให้กดปุ่มรีเซ็ท (ปุ่มแดง) บันทึกผลการทดลอง

7. ถอดไมโครคอนโทรลเลอร์จาก Adapter มาเสียบที่ช่องซีเรียลของรีเลย์
   
   ![Image](https://github.com/Nana-Nan/image/blob/main/3-7.jpg)

8. จ่ายไฟจากแบตเตอรี่สำรองให้กับรีเลย์
   
   ![Image](https://github.com/Nana-Nan/image/blob/main/3-1.jpg)

9. บันทึกผล

## การบันทึกผลการทดลอง
   จากการทดลอง โดยการรันโปรแกรมของไมโครคอนโทรลเลอร์ได้แสดงผล ดังนี้
   
   ![Image](https://github.com/Nana-Nan/image/blob/main/3-5.jpg)
   
   และเมื่อทำการต่อรีเลย์เข้ากับไมโครคอนโทรลเลอร์ ได้แสดงผลดังนี้
   
   ![Image](https://github.com/Nana-Nan/image/blob/main/3-8.jpg)

## อภิปรายผลการทดลอง
* จากการทดลอง โดยการรันโปรแกรมของไมโครคอนโทรลเลอร์ จะได้ว่าในทุก ๆ ครึ่งวินาที จะเกิดการส่ง output ออกมาเป็น on และ off ไปเรื่อย ๆ ในขณะที่ส่งสัญญาณเป็น on หลอดไฟ LED ที่พอร์ตสีขาวจะติด และในขณะที่ off หลอดไฟ LED จะดับ ทำให้เห็นว่าหลอดไฟกะพริบทุก ๆ ครึ่งวินาที

* จากการทดลอง เมื่อนำไมโครคอนโทรลเลอร์ที่ลงโปรแกรมไว้แล้วไปต่อกับรีเลย์ และจ่ายไฟให้รีเลย์ รีเลย์จะเปิด-ปิดสวิตช์ตามสัญญาณ on และ off  
   
## คำถามหลังการทดลอง
* เมื่อสัญญาณ on รีเลย์จะทำงานอย่างไร

   ตอบ เมื่อสัญญาณ on จะไปกระตุ้นให้เกิดสนามแม่เหล็กในส่วนของขดลวดรีเลย์ ให้ผลักเข็มสาย common ไปสัมผัสกับ normal open เหมือนกับปิดสวิตช์ในวงจรทำให้กระแสไหลครบวงจร หลอดไฟจึงสว่างขึ้น
