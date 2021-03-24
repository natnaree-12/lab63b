# การทดลองที่ 6 เรื่อง การเขียนโปรแกรมสร้างไวไฟแอคเซสพอยต์ (Wifi AP)

## วัตถุประสงค์
1.เพื่อทำความเข้าใจเกี่ยวกับการเขียนโปรแกรมเชื่อมต่อไวไฟและเว็บเซอร์เวอร์

2.เพื่อทำความเข้าใจเกี่ยวกับการทำงานของการเชื่อมต่อไวไฟและเว็บเซอร์เวอร์

## อุปกรณ์ที่ใช้ 
1.microcontroller ESP01

2.USB

3.Serial Port Compuuter

4.Commuter

## ศึกษาข้อมูลเบื้องต้น
* https://www.youtube.com/watch?v=VX-QNQcO-b4&ab_channel=TANI-IOT

## วิธีการทำการทดลอง
1.ต่อสาย USB เข้า Serial Port Compuuter 

![image](https://user-images.githubusercontent.com/80879788/112309445-e9996900-8cd5-11eb-8f4c-da72cbde1663.png)


2.เสียบ microcontroller ESP01 ลงบน Serial Port Compuuter

![image](https://user-images.githubusercontent.com/80879788/112309332-cd95c780-8cd5-11eb-91ec-f39c35bd417c.png)

3.เตรียมดาวน์โหลดโปรแกรม
  * พิมพ์ vi src/main.cpp กด Enter แสดงโปรแกรมดังรูป

![image](https://user-images.githubusercontent.com/80879788/112382349-5173a200-8d1e-11eb-80a3-6351907f6122.png)

ซึ่งจำเป็นต้องตั้งชื่อไวไฟ และรหัสผ่าน จากนั้นต้องกำหนด IPAddress เพื่อปล่อยไวไฟให้คนอื่นมาเชื่อมต่อได้ เปิด serverที่ port 80 เริ่มจากการเปลี่ยนเว็บเซิร์ฟเวอร์ไว้ 1 ตัว แล้วสร้าง AP ด้วยคำสั่ง WiFi.softAP(ssid, password) และบอก ip ว่าเป็นเท่าไร

4.อัปโหลดโปรแกรมเข้าสู่ microcontroller
  * พิมพ์ pio run -t upload กด Enter
  * ขณะที่ run เพื่อให้ microcontroller รับข้อมูลใหม่เข้าไป ให้กดปุ่มดังรูป

![image](https://user-images.githubusercontent.com/80879788/112379750-1e7bdf00-8d1b-11eb-84c6-0128585dde14.png)

5.พิมพ์ pio device monitor กด Enter และกดรีเซทใหม่ ทดสอบการหาไวไฟด้วยโทรศัพท์มือถือ

## การบันทึกผลการทดลอง
จะเห็นได้ว่าเมื่อทำการค้นหาไวไฟด้วยโทรศัพท์มือถือ เจอAP ชื่อของตัวไวไฟที่ตั้งค่าเอาไว้และสามารถเชื่อมต่อไวไฟได้

![image](https://user-images.githubusercontent.com/80879788/112384203-b3350b80-8d20-11eb-8091-997d854c53ce.png)

## อภิปรายผลการทดลอง
จากการทดลอง run โปรแกรมด้วย microcontroller สามารถสรุปได้ว่า สามารถนำmicrocontroller เป็นตัวกระจายไวไฟเพื่อเชื่อมต่อสัญญาณได้
