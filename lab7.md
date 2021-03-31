# การทดลองที่ 7 เรื่อง การตั้งเวลาเปิด-ปิด WiFi และการเชื่อมต่อ WiFi อัตโนมัติ

## วัตถุประสงค์
1. เพื่อให้เข้าใจการเขียนโปรแกรมลงในไมโครคอนโทรลเลอร์
2. เพื่อให้ไมโครคอนโทรลเลอร์ปล่อย WiFi และตั้งเวลาในการเปิด-ปิด WlFi
3. เพื่อสร้างอุปกรณ์ในการเชื่อมต่อ WiFi อัตโนมัติ

## อุปกรณ์ที่ใช้
1. ไมโครคอนโทรลเลอร์ ESP-01 2 บอร์ด
2. USB to serial port 2 บอร์ด
3. อุปกรณ์ต่อพ่วง USB 2 สาย
4. Adapter ต่อพอร์ตเชื่อม LED เปล่งแสง
5. อุปกรณ์เขียนโปรแกรม เช่น คอมพิวเตอร์ โน้ตบุ๊ค ฯลฯ

## ศึกษาข้อมูลเบื้องต้น
1. การติดตั้งโปรแกรม
   * [การเตรียมโปรแกรม](https://youtu.be/9aF0upI9Gic)
   * [ตัวอย่างการลงโปรแกรม](https://youtu.be/ocrGdJoP90Y)
2. ข้อมูลเกี่ยวกับซอร์ฟแวร์ที่จะใช้เขียนโปรแกรม  
   * [platform io](https://platformio.org/)
3. [ข้อมูลเกี่ยวกับไมโครคอนโทรลเลอร์ ESP-01](https://docs.platformio.org/en/latest/boards/espressif8266/esp01_1m.html)
4. อ้างอิง 
   * [การใช้งาน ESP8266](http://99thai.com/data/up_show.php?id=1523293577&web=epost)
   * [ESP8266WiFi](https://arduino-esp8266.readthedocs.io/en/latest/esp8266wifi/readme.html)

## วิธีการทำการทดลอง
* ตอนแรก 
1. เริ่มจากการต่อ USB to serial port เข้ากับคอมพิวเตอร์โดยอุปกรณ์พ่วง USB และต่อ USB to serial port เข้ากับ Adapter สุดท้ายต่อ Adapte เข้ากับไมโครคอนโทรลเลอร์
2. อัปโหลด  code โปรแกรมลงในโฟลเดอร์ของเครื่องคอมพิวเตอร์

```C
#include <ESP8266WiFi.h>
//#include <WiFiClient.h>
#include <ESP8266WebServer.h>

const char* ssid = "ESP_WIFI";
const char* password = "oopieces7512";

IPAddress local_ip(192, 168, 1, 1);
IPAddress gateway(192, 168, 1, 1);
IPAddress subnet(255, 255, 255, 0);

ESP8266WebServer server(80);

int cnt = 0;

void setup() 									//เป็นการ setup ตัว Adapter
{
	Serial.begin(115200);
	pinMode(0, OUTPUT);
	Serial.println("\n\n\n");
}
	
void setup(void) 								//เป็นการ setup การปล่อย WiFi
{
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

void loop()
{
	cnt++;
	if(cnt <= 6) 								//เมื่อ cnt น้อยกว่าเท่ากับ 6 หรือ เวลาอยูในช่วง 1 นาที
	{
		Serial.println("========== ON ===========");			//ขึ้นสถานะ ON
		digitalWrite(0, HIGH);						//หลอดไฟเปล่งแสง
		
		void loop(void)							//เรียกใช้งาน WiFi ที่ได้ setup ไว้
		{
  			server.handleClient();
		}
	} 
	
	else 
	{
		Serial.println("========== OFF ===========");			//ขึ้นสถานะ OFF
		digitalWrite(0, LOW);						//หลอดไฟดับ
	}
	delay(10*1000); 							//delay เป็น 10 วินาที
}
```
3. เปิด command prompt เข้าไปยังโฟลเดอร์ที่มีตัวอย่างโปรแกรม แล้ว **cd ชื่อไฟล์โปรแกรม**
4. อัปโหลดโปรแกรมลงในไมโครคอนโทรเลอร์ โดยใช้คำสั่ง **pio run -t upload**
5. ในขณะที่โปรแกรมกำลังรัน ให้ไปกดที่ปุ่มดำของบอร์ดค้างไว้ แล้วกดปุ่มแดง 1 ครั้ง เพื่อรีเซ็ท และให้ตัวไมโครคอนโทรลเลอร์รับ code เข้าไป
6. เมื่อโปรแกรมรันเสร็จให้ใช้คำสั่ง **pio device monitor** เพื่อดูผลลัพธ์ที่แสดงผลออกมาจากคอมพิวเตอร์
7. ให้กดปุ่มรีเซ็ท (ปุ่มแดง) แล้วเปิดการค้นหา WiFi จากโทรศัพท์ บันทึกผล

* ตอนสอง
1. เริ่มจากการต่ออุปกรณ์ที่เหลือ USB to serial port เข้ากับคอมพิวเตอร์โดยอุปกรณ์พ่วง USB และนำไมโครคอนโทรลเลอร์ต่อเข้ากับ USB to serial port
2. อัปโหลด  code โปรแกรมลงในโฟลเดอร์ของเครื่องคอมพิวเตอร์

```C
#include <ESP8266WiFi.h>
int cnt = 0;

void setup() 									//เป็นการ setup การค้นหา WiFi
{
	Serial.begin(115200);
	WiFi.mode(WIFI_STA);
	WiFi.disconnect();
	delay(100);
	Serial.println("\n\n\n");
}

void loop()
{
	Serial.println("========== เริ่มต้นแสกนหา Wifi ===========");
	int n = WiFi.scanNetworks(); 						// n แทนจำนวน WiFi ที่พบในบริเวณนั้น
	if(n == 0) {
		Serial.println("NO NETWORK FOUND");
	} 
	else { 									// เจอ WiFi
		for(int i=0; i<n; i++) {
			Serial.print(i + 1);
			Serial.print(": ");
			Serial.print(WiFi.SSID(i));
			Serial.print(" (");
			Serial.print(WiFi.RSSI(i));
			Serial.println(")");
			delay(10*1000);
		}
		
		if (WiFi.SSID(i) == ESP_WIFI) { 				// เจอสัญญาณ WiFi ที่ชื่อ ESP_WIFI
			void setup()
			{
  				Serial.begin(115200);
  				Serial.println();

  				WiFi.begin("ESP_WIFI", "oopieces7512"); 	//เข้าใช้งาน ESP_WIFI รหัส oopiece7512

  				Serial.print("Connecting"); 			//แสดงผลทางหน้าจอว่า Connecting
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
		}
	}
}

```
3. เปิด command prompt เข้าไปยังโฟลเดอร์ที่มีตัวอย่างโปรแกรม แล้ว **cd ชื่อไฟล์โปรแกรม**
4. อัปโหลดโปรแกรมลงในไมโครคอนโทรเลอร์ โดยใช้คำสั่ง **pio run -t upload**
5. ในขณะที่โปรแกรมกำลังรัน ให้ไปกดที่ปุ่มดำของบอร์ดค้างไว้ แล้วกดปุ่มแดง 1 ครั้งเพื่อรีเซ็ท และให้ตัวไมโครคอนโทรลเลอร์รับ code เข้าไป
6. เมื่อโปรแกรมรันเสร็จให้ใช้คำสั่ง **pio device monitor** เพื่อดูผลลัพธ์ที่แสดงผลออกมาจากคอมพิวเตอร์
7. สังเกตการทำงานหลังจากที่กด reset จากตอนที่ 1

## การบันทึกผลการทดลอง
* ตอนแรก หลังจากกดปุ่ม reset หน้าจอมอนิเตอร์ขึ้นสาถานะ ON หลอดไฟเปล่งแสง และจากหน้าจอโทรศัพท์มือถือ ค้นพบ WiFi ที่ชื่อ ESP_WIFI เป็นเวลา 1 นาที หลังจาก 1 นาที หน้าจอมอนิเตอร์ขึ้นสาถานะ OFF หลอดไฟดับ และจากหน้าจอโทรศัพท์มือถือ ไม่พบ WiFi ที่ชื่อ ESP_WIFI  
* ตอนสอง หน้าจอจะแสดงชื่อ WiFi ที่อยู่บริเวณนั้น และเมื่อพบ WiFi ที่ชื่อ "ESP_WIFI" หน้าจอขึ้น Connected, IP address: ที่อยู่ IP และหลังจากการ 1 นาทีหลังจากการกด reset ของตอนที่ 1 แล้วนั้น จะขึ้นชื่อ WiFi ต่าง ๆ เรื่อย ๆ ทุก ๆ 10 วินาที
   
## อภิปรายผลการทดลอง
   จากการทดลอง 
   * ตอนแรก เมื่อหลอดไฟเปล่งแสง จากหน้าจอโทรศัพท์มือถือ ค้นพบ WiFi ที่ชื่อ ESP_WIFI จริง และเมื่อทำการล็อกอินเข้าไป จะให้ป้อนรหัสคือ oopieces7512 จึงจะสามารถเข้าใช้งานได้ หลังจาก 1 นาทีที่กด reset หลอดไฟดับ และจะไม่พบสัญญาณ WiFi ที่ชื่อ ESP_WIFI
   * ตอนสอง เมื่อทำการรัน **pio device monitor** หน้าจอจะแสดงชื่อ WiFi ที่อยู่บริเวณนั้น และเมื่อพบ WiFi "ESP_WIFI" จะเข้า login เข้าใช้งานโดยอัตโนมัติ เนื่องจากเรา set code ให้เข้าใช้งาน ESP_WIFI ไว้แล้ว หากไม่พบก็จะเกิดการค้นหาไปเรื่อย ๆ

## การนำความรู้ไปใช้ในชีวิตประจำวัน
โดยผู้ใช้งานสามารถเปลี่ยนที่ delay ของ code ในตอนที่ 1 เป็น  
```C
	if(cnt <= 6) 								//เมื่อ cnt น้อยกว่าเท่ากับ 6 หรือ เวลาอยูในช่วง 6 ชั่วโมง
	{
		.								//ละตัวโปรแกรมไว้
		.
		.
	}
	delay(60*60*1000); 							//delay เป็น 1 ชั่วโมง
}
```
เป็นต้น ดังนั้นผู้ใช้จึงสามารถกำหนดเวลาการเปิด-ปิด WiFi ได้ และสามารถควบคุมการเชื่อมต่อ WiFi อัตโนมัติ ของอุปกรณ์ที่ต้องใช้อินเตอร์เน็ตได้ 

## คำถามหลังการทดลอง
* จงอธิบายความหมายของ SSID และ RSSI พอสังเขป

   ตอบ SSID (service set identifier) ของสัญญาณเน็ต หรือก็คือ "ชื่อเครือข่าย" และ RSSI (Received Signal Strength Indication) เป็นการวัดความแรงหรือความเข้มของสัญญาณตัวรับ มีหน่วยเป็น dBm ยิ่งติดลบน้อยยิ่งดี
