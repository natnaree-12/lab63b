# การทดลองที่ 7 เรื่อง รดน้ำต้นไม้ด้วยสมาร์ทโฟน

## วัตถุประสงค์ 

1.ศึกษาลักษณะวงจรที่นำมาต่อเพื่อสั่งการการรดต้นไม้

2.ศึกษาการเขียนโปรแกรมเพื่อใช้ในการสั่งการรดน้ำต้นไม้

## อุปกรณ์ที่ใช้ 

1.microcontroller ESP 32

![image](https://user-images.githubusercontent.com/80879788/113187378-fcd2a880-9282-11eb-9cc0-1f71daa305b7.png)

2.บอร์ดขยาย

![image](https://user-images.githubusercontent.com/80879788/113188265-06104500-9284-11eb-8d21-e43802c0ae92.png)

3.Relay - Active Low 5V 10A

![image](https://user-images.githubusercontent.com/80879788/113188316-17595180-9284-11eb-989e-765e5630873b.png)

4.Power Supply 12 V

![image](https://user-images.githubusercontent.com/80879788/113188353-217b5000-9284-11eb-981f-2bac435e71c4.png)

5.โซลินอยต์

![image](https://user-images.githubusercontent.com/80879788/113188379-29d38b00-9284-11eb-8641-8e10df9d3bb3.png)

6.adapter

![image](https://user-images.githubusercontent.com/80879788/113188398-322bc600-9284-11eb-97de-8d323f2d7b1c.png)

7.ปุ่มสวิชต์

![image](https://user-images.githubusercontent.com/80879788/113188428-3bb52e00-9284-11eb-835c-12d227babd0a.png)

8.สายไฟ

![image](https://user-images.githubusercontent.com/80879788/113188462-47085980-9284-11eb-8fca-0eff9eaa7d88.png)


9.เซอร์กิตเบอร์เกอร์

![image](https://user-images.githubusercontent.com/80879788/113188499-5091c180-9284-11eb-95f9-5f6e12d5fd27.png)


## ศึกษาข้อมูลเบื้องต้น 

* http://www.lungmaker.com/%E0%B8%A7%E0%B8%B4%E0%B8%98%E0%B8%B5%E0%B9%83%E0%B8%8A%E0%B9%89-esp8266-esp-01-wifi/

* https://www.youtube.com/watch?v=uSKZbOIMiqw&ab_channel=SaranairChannel

* https://www.youtube.com/watch?v=Ik5TBPh3_Os&ab_channel=SaranairChannel

## วิธีการทำการทดลอง

### 1. ทำการต่อวงจรดังรูป

![image](https://user-images.githubusercontent.com/80879788/113323486-34ebf100-9340-11eb-87bd-17e64eef1942.png)

ต่อ Relay กับปุ่มข้างหน้ากล่อง

![image](https://user-images.githubusercontent.com/80879788/113274378-d4d95880-9307-11eb-8934-fa849d851cd5.png)

### 2.อัพโหลดโค้ดใส่ ESP 32

##### ลงโปรแกรม

* เรียกใช้งานไลบรารี ESP32WiFi.h เพื่อเชื่อมต่อกับเครือข่าย WiFi ของ ESP32  หลังจากนั้นเรายังเรียกใช้ไลบรารี ESP32WebServer.h เพื่อช่วยให้เราตั้งค่าเซิร์ฟเวอร์และจัดการคำขอ HTTP

      #include <ESP32WiFi.h>

      #include <ESP32WebServer.h>

* เนื่องจากเรากำลังตั้งค่า ESP32 ใช้งานในโหมด(AP)เพื่อสร้างเครือข่าย WiFi ดังนั้นเราต้องตั้งค่า SSID, รหัสผ่าน, ที่อยู่ IP, IP ซับเน็ตมาสก์และ IP เกตเวย์

      const char* ssid = "ENG_12";  // Enter SSID here

      const char* password = "12345678";  //Enter Password here

      IPAddress local_ip(192, 168, 1, 1);

      IPAddress gateway(192, 168, 1, 1);

      IPAddress subnet(255, 255, 255, 0);

* เรียก object ของไลบรารี ESP32WebServer เพื่อให้เราสามารถเข้าถึงฟังก์ชั่นของมัน ตัวสร้างของวัตถุนี้ใช้พอร์ตเป็นพารามิเตอร์ เนื่องจาก 80 เป็นพอร์ตเริ่มต้นสำหรับ HTTP เราจะใช้ค่านี้ 
ESP32WebServer server(80);

      uint8_t Generator pin = 0;
* ทำการประกาศขาของ ESP32 ที่มีการเชื่อมต่ออยู่และสถานะเริ่มต้น
     
      bool Generator status = LOW;

      uint8_t Generator pin = 2;

      bool Generator status = LOW;

#### ฟังก์ชั่น Setup 

* ตั้งค่าเวิร์ฟเวอร์และค่าของoutput จากนั้นเราตั้งค่าจุดเชื่อมต่อ Access Point (soft-AP) เพื่อสร้างเครือข่าย Wi-Fi โดยการตรวจสอบ SSID, รหัสผ่าน, ที่อยู่ IP, IP ซับเน็ตมาสก์และ IP เกตเวย์ เพื่อจำกัดการเข้า HTTP จำเป็นต้องระบุรหัสที่จะดำเนินการเมื่อมีการเข้าชม URL หากผู้ใช้งานร้องขอ URL อื่นใดนอกเหนือจากที่ระบุไว้ใน server.on จะแสดงข้อมูลว่า server.onNotFound 

      void setup() 
      
      {
  
        Serial.begin(115200);
 
        pinMode (Generator, OUTPUT)

        WiFi.softAP(ssid, password);
  
        WiFi.softAPConfig(local_ip, gateway, subnet);
  
        delay(100);

        server.on("/", handle_OnConnect);
  
        server.on("/Generatoron", handle_led1on);
  
        server.on("/Generatoroff", handle_led1off); 
  
        server.onNotFound(handle_NotFound);

* เริ่มต้นเรียกการใช้งานของเซิร์ฟเวอร์
          
        server.begin();
  
        Serial.println("HTTP server started");
      }

#### ฟังก์ชัน Loop 

* เรียก object ของไลบรารี ESP32WebServer แล้วป้อนสถานะ Generator status ในLoop นี้

      void loop() {
  
        server.handleClient();
  
        if (Generatorstatus)
  
      {
    
        digitalWrite(Generatorpin, HIGH);
  
      }
  
      else
  
      {
   
       digitalWrite(Generatorpin, LOW);
  
      }
 
* ต่อไปสร้างฟังก์ชั่นที่เราแนบไปกับรูท (/) URL ด้วยเซิร์ฟเวอร์ เพื่อตอบสนองต่อ HTTP ซึ่งในที่นี้เรากำลังส่งรหัส 200 (รหัสสถานะ HTTP) ซึ่งสอดคล้องกับการตอบสนอง จากนั้นเราระบุประเภทเนื้อหาเป็น“ text / html“  ฟังก์ชั่นที่กำหนดเองซึ่งสร้างหน้า HTML แบบไดนามิกที่มีสถานะของการเปิด-ปิดน้ำ

      void handle_OnConnect() 
      
      {
  
        Generator status = LOW;
  
        Serial.println("Generator Status: OFF ");
  
        server.send(200, "text/html", SendHTML(Generatorstatus));
      }

* ในทำนองเดียวกันเพื่อจัดการคำขอเปิด-ปิด น้ำ และหน้าข้อผิดพลาด

       void handle_ Generatoron() 
       
       {
  
          Generatorstatus = HIGH;
  
          Serial.println(" Generator Status: ON");
  
          server.send(200, "text/html", SendHTML(true));
      }

       void handle_ Generatoroff() 
       
       {
 
          Generatorstatus = LOW;
  
          Serial.println(" Generator Status: OFF");
  
          server.send(200, "text/html", SendHTML(false));

       }

       void handle_NotFound()

       {
  
          server.send(404, "text/plain", "Not found");

       }

#### การแสดงเว็บเพจ HTML

* ฟังก์ชัน SendHTML () มีหน้าที่สร้างหน้าเว็บทุกครั้งที่เว็บเซิร์ฟเวอร์ เมื่อได้รับคำขอจากโค้ดในฟังก์ชัน loop คือ ฟังก์การรับสถานะการเปิด-ปิดน้ำ เป็นพารามิเตอร์ในการสร้างเนื้อหา HTML แบบไดนามิก บรรทัดแรกเป็นการระบุว่าเรากำลังส่งรหัส HTML คือ < ! DOCTYPE >

      String SendHTML(uint8_t Generatorstat) 

      {

      String ptr = "<!DOCTYPE html> <html>\n";

* ถัดไปคือ < meta > ที่ทำให้หน้าเว็บตอบสนองในเว็บเบราว์เซอร์ใด ๆ ในขณะที่แท็ก < title > จะตั้งชื่อของหน้า

       ptr += "<head><meta name=\"viewport\" content=\"width=device-width, initial-scale=1.0, user-scalable=no\">\n";
  
       ptr += "<title> Control</title>\n";
  
       ptr += "<style>html { font-family: Helvetica; display: inline-block; margin: 0px auto; text-align: center;}\n";

* ต่อไปเป็นการตั้งค่าสีแบบอักษรและระยะขอบรอบ ๆ ในตัวเว็บเพจ

       ptr += "body{margin-top: 50px;} h1 {color: #444444;margin: 50px auto 30px;} h3 {color: #444444;margin-bottom: 50px;}\n";

       ptr += ".button {display: block;width: 80px;background-color: #1abc9c;border: none;color: white;padding: 13px 30px;text-decoration: none;font-size: 25px;margin: 0px 

* การจัดแต่งหน้าเว็บ คือ กำหนดลักษณะปุ่มและลักษณะที่ปรากฏของหน้าเว็บ เลือกแบบอักษร กำหนดเนื้อหาที่จะแสดงเป็นบล็อกอินไลน์และจัดตำแหน่งที่กึ่งกลาง

      auto 35px;cursor: pointer;border-radius: 4px;}\n";
  
         ptr += ".button-on {background-color: #1abc9c;}\n";
  
         ptr += ".button-on:active {background-color: #16a085;}\n";
  
         ptr += ".button-off {background-color: #34495e;}\n";
  
         ptr += ".button-off:active {background-color: #2c3e50;}\n";

         ptr += "p {font-size: 14px;color: #888;margin-bottom: 10px;}\n";
  
         ptr += "</style>\n";
  
         ptr += "</head>\n";
  
         ptr += "<body>\n";

* ตั้งค่าหัวเรื่องของหน้าเว็บ เป็นการใส่ข้อความที่ต้องการแสดงบนหน้าเว็บเพจ

         ptr += "<h1>ENG_12 Web Server</h1>\n";
  
         ptr += "<h3>Using Access Point(AP) Mode</h3>\n";

* การแสดงปุ่มและสถานะที่เกี่ยวข้องบนหน้าเว็บเพจ

      if Generatorstat)
  
         {ptr += "<p> Generator Status: ON</p><a class=\"button button-off\" href=\"/ Generatoroff\">OFF</a>\n";}
  
       else
  
         {ptr += "<p> Generator Status: OFF</p><a class=\"button button-on\" href=\"/ Generatoron\">ON</a>\n";}
  
       ptr += "</body>\n";
  
       ptr += "</html>\n";
  
       return ptr;

      }

##### อัพโหลดโค้ด

![image](https://user-images.githubusercontent.com/80879788/113195974-21338280-928d-11eb-9b3f-f1d8b9447b25.png)

![image](https://user-images.githubusercontent.com/80879788/113196286-838c8300-928d-11eb-8466-6c54cb1a7ce0.png)

### 3.ทดสอบการทำงาน

* ใช้ สมาร์ทโฟน ไปที่การตั้งค่า Wi-Fi

![image](https://user-images.githubusercontent.com/80879788/113198037-a0c25100-928f-11eb-99db-2d8958c71fdb.png)

* เลือกเครือข่าย Wi-Fi เป็น ENG_12

![image](https://user-images.githubusercontent.com/80879788/113198160-c8b1b480-928f-11eb-9f23-b7cfe517a498.png)

* ใส่รหัสผ่านเครือข่าย = 12345678 จากนั้นกดเชื่อมต่อ

![image](https://user-images.githubusercontent.com/80879788/113198244-e717b000-928f-11eb-90cc-598399380201.png)

* แสดงการเชื่อมต่อเครือข่าย Wi-Fi เป็น ENG_12

![image](https://user-images.githubusercontent.com/80879788/113198503-3231c300-9290-11eb-92d1-c8123d9f9120.png)

* เปิดเว็บบราวเซอร์ ที่ URL ป้อนไอพี : 192.168.1.1

## การบันทึกผลการทดลอง 

 * ยังไม่ได้กดเปิด 
  
![image](https://user-images.githubusercontent.com/80879788/113199179-0531e000-9291-11eb-9810-765cd8049e6d.png)

  ตัวสปริงเกอร์ไม่จ่ายน้ำ
  
  ![image](https://user-images.githubusercontent.com/80879788/113271012-49aa9380-9304-11eb-92a7-7362e7a87c82.png)

 * กดเปิดแล้ว

![image](https://user-images.githubusercontent.com/80879788/113199221-11b63880-9291-11eb-9852-903d10ecf8aa.png)

  ตัวสปริงเกอร์จ่ายน้ำ

![image](https://user-images.githubusercontent.com/80879788/113271114-5e872700-9304-11eb-8b1f-976cf991c615.png)


## อภิปรายผลการทดลอง 

จากผลการทดลอง พบว่า เราสามารถนำไมโครคอนโรเลอร์โดยตัวที่เลือกมา คือ ESP32 มาใช้กับความรู้เรื่องการเขียนโปรแกรมสร้างไวไฟแอคเซสพอยต์ (Wifi AP) เพื่อนำมาใช้ในการการการสั่งการการเปิดปิดน้ำได้ โดยในที่นี้จะใช้โซลินอยต์วาวล์แทนปั๊ม เพราะตัวโซลินอยต์ไม่จำเป็นต้องใชไฟมากและมีราคาที่ถูกกว่า นอกจากนี้ยังนำความรู้การเขียน HTML มากใช้ในการเขียนหน้าเว็บเพจอีกด้วย โดยรวมแล้วถ้าหากสามารถนำมาใช้ทางการเกษตรได้ จะทำให้เกษตกรประหยัดเวลาในการรดน้ำ จากที่ต้องเดินไปเปิดวาวล์น้ำทุกตัวก็สามารถสั่งการผ่านทางสมาร์ทโฟนได้


