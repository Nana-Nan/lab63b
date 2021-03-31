# การทดลองที่ 7 เรื่อง การเชื่อมต่อ WIFI อัตโนมัติ

## วัตถุประสงค์
1. เพื่อให้เข้าใจการเขียนโปรแกรมลงในไมโครคอนโทรลเลอร์
2. เพื่อสร้างอุปกรณ์ในการเชื่อมต่อ WIFI อัตโนมัติ
3. เพื่อให้ไมโครคอนโทรลเลอร์ปล่อยไวไฟ

## อุปกรณ์ที่ใช้
1. ไมโครคอนโทรลเลอร์ ESP-01 2 บอร์ด
2. USB to serial port 2 บอร์ด
3. อุปกรณ์ต่อพ่วง USB 2 สาย
4. อุปกรณ์เขียนโปรแกรม เช่น คอมพิวเตอร์ โน้ตบุ๊ค ฯลฯ

## ศึกษาข้อมูลเบื้องต้น
1. การติดตั้งโปรแกรม
   * [การเตรียมโปรแกรม](https://youtu.be/9aF0upI9Gic)
   * [ตัวอย่างการลงโปรแกรม](https://youtu.be/ocrGdJoP90Y)
2. ข้อมูลเกี่ยวกับซอร์ฟแวร์ที่จะใช้เขียนโปรแกรม  
   * [platform io](https://platformio.org/)
3. [ข้อมูลเกี่ยวกับไมโครคอนโทรลเลอร์ ESP-01](https://docs.platformio.org/en/latest/boards/espressif8266/esp01_1m.html)
4. อ้างอิง 
   * [การใช้งาน ESP8266](http://99thai.com/data/up_show.php?id=1523293577&web=epost)

## วิธีการทำการทดลอง
* ตอนแรก (Lab6.md)
1. เริ่มจากการต่อ USB to serial port เข้ากับคอมพิวเตอร์โดยอุปกรณ์พ่วง USB และนำไมโครคอนโทรลเลอร์ต่อเข้ากับ USB to serial port
2. อัปโหลด  code โปรแกรมลงในโฟลเดอร์ของเครื่องคอมพิวเตอร์

```C
#include <ESP8266WiFi.h>
//#include <WiFiClient.h>
#include <ESP8266WebServer.h>
#include <Arduino.h>

const char* ssid = "ESP_WIFI";
const char* password = "oopieces7512";

IPAddress local_ip(192, 168, 1, 1);
IPAddress gateway(192, 168, 1, 1);
IPAddress subnet(255, 255, 255, 0);

ESP8266WebServer server(80);

int cnt = 0;

void setup(void){
	Serial.begin(115200);

	WiFi.softAP(ssid, password);
	WiFi.softAPConfig(local_ip, gateway, subnet);
	delay(100);

	server.onNotFound([]() {
		server.send(404, "text/plain", "Path Not Found");
	});

	server.on("/", []() {
		cnt++;
		String msg = "Hello cnt: ";
		msg += cnt;
		server.send(200, "text/plain", msg);
	});

	server.begin();
	Serial.println("HTTP server started");
}

void loop(void){
  server.handleClient();
}
```
3. เปิด command prompt เข้าไปยังโฟลเดอร์ที่มีตัวอย่างโปรแกรม แล้ว **cd ชื่อไฟล์โปรแกรม**
4. อัปโหลดโปรแกรมลงในไมโครคอนโทรเลอร์ โดยใช้คำสั่ง **pio run -t upload**
5. ในขณะที่โปรแกรมกำลังรัน ให้ไปกดที่ปุ่มดำของบอร์ดค้างไว้ แล้วกดปุ่มแดง 1 ครั้งเพื่อรีเซ็ท และให้ตัวไมโครคอนโทรลเลอร์รับ code เข้าไป
6. เมื่อโปรแกรมรันเสร็จให้ใช้คำสั่ง **pio device monitor** เพื่อดูผลลัพธ์ที่แสดงผลออกมาจากคอมพิวเตอร์
7. ให้กดปุ่มรีเซ็ท (ปุ่มแดง) แล้วเปิดการค้นหาไวไฟจากโทรศัพท์ บันทึกผล

* ตอนสอง
1. เริ่มจากการต่ออุปกรณ์ที่เหลือ USB to serial port เข้ากับคอมพิวเตอร์โดยอุปกรณ์พ่วง USB และนำไมโครคอนโทรลเลอร์ต่อเข้ากับ USB to serial port
2. อัปโหลด  code โปรแกรมลงในโฟลเดอร์ของเครื่องคอมพิวเตอร์

```C
#include <ESP8266WiFi.h>

void setup()
{
  Serial.begin(115200);
  Serial.println();

  WiFi.begin("ESP_WIFI", "oopieces7512");

  Serial.print("Connecting");
  while (WiFi.status() != WL_CONNECTED)
  {
    delay(500);
    Serial.print(".");
  }
  Serial.println();

  Serial.print("Connected, IP address: ");
  Serial.println(WiFi.localIP());
}

void loop() {}
```
3. เปิด command prompt เข้าไปยังโฟลเดอร์ที่มีตัวอย่างโปรแกรม แล้ว **cd ชื่อไฟล์โปรแกรม**
4. อัปโหลดโปรแกรมลงในไมโครคอนโทรเลอร์ โดยใช้คำสั่ง **pio run -t upload**
5. ในขณะที่โปรแกรมกำลังรัน ให้ไปกดที่ปุ่มดำของบอร์ดค้างไว้ แล้วกดปุ่มแดง 1 ครั้งเพื่อรีเซ็ท และให้ตัวไมโครคอนโทรลเลอร์รับ code เข้าไป
6. เมื่อโปรแกรมรันเสร็จให้ใช้คำสั่ง **pio device monitor** เพื่อดูผลลัพธ์ที่แสดงผลออกมาจากคอมพิวเตอร์

## การบันทึกผลการทดลอง
* ตอนแรก จากหน้าจอโทรศัพท์มือถือ ค้นพบ WiFi ที่ชื่อ ESP_WIFI 
* ตอนสอง หน้าจอจะแสดงชื่อ WiFi ที่อยู่บริเวณนั้น และเมื่อพบ WiFi ที่ชื่อ "ESP_WIFI" หน้าจอขึ้น Connected, IP address: ที่อยู่ IP
   
## อภิปรายผลการทดลอง
   จากการทดลอง 
   * ตอนแรก จากหน้าจอโทรศัพท์มือถือ ค้นพบ WiFi ที่ชื่อ ESP_WIFI จริง และเมื่อทำการล็อกอินเข้าไป จะให้ป้อนรหัสคือ oopieces7512 จึงจะสามารถเข้าใช้งานได้
   * ตอนสอง เมื่อทำการรัน **pio device monitor** หน้าจอจะแสดงชื่อ WiFi ที่อยู่บริเวณนั้น และเมื่อพบ WiFi "ESP_WIFI" จะเข้า login เข้าใช้งานโดยอัตโนมัติ
## คำถามหลังการทดลอง
* 

   ตอบ
