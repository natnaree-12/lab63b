# การทดลองที่ 5 เรื่อง การเขียนโปรแกรมเชื่อมต่อไวไฟและเว็บเซอร์เวอร์

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
  * พิมพ์ cd 05_Wifi-Web-Server 
  * พิมพ์ ls กด Enter แสดง platformio.ini src  
  * พิมพ์ vi src/main.cpp กด Enter แสดงโปรแกรมดังรูป

![image](https://user-images.githubusercontent.com/80879788/112378377-6e59a680-8d19-11eb-8f17-e433f647b25e.png)

![image](https://user-images.githubusercontent.com/80879788/112378477-91845600-8d19-11eb-83fe-0e5a5195534f.png)

4.อัปโหลดโปรแกรมเข้าสู่ microcontroller
  * พิมพ์ pio run -t upload กด Enter
  * ขณะที่ run เพื่อให้ microcontroller รับข้อมูลใหม่เข้าไป ให้กดปุ่มดังรูป

![image](https://user-images.githubusercontent.com/80879788/112379750-1e7bdf00-8d1b-11eb-84c6-0128585dde14.png)

5.เปิดเว็บบราวเซอร์ในการแสดงผลัพธ์

6.โดยการให้ copy ip address ไปที่บราวเซอร์ในการทดสอบและบันทึกผล

## การบันทึกผลการทดลอง
จะเห็นไดว่าจากคำสั่ง pio device monitor เพื่อดูผลลัพธ์ของการ run โปรแกรมใน microcontroller จะได้ตัว ip address เป็นตัวเดิม และเมื่อ copy ip address ไปที่บราวเซอร์ก็จะเป็น Hello 1 โดย count ก็จะเปลี่ยนตัวแปรไปเรื่อยๆ

## อภิปรายผลการทดลอง
จากการทดลอง run โปรแกรมด้วย microcontroller สามารถสรุปได้ว่า สามารถนำmicrocontroller เชื่อมต่อไวไฟและเว็บเซิร์ฟเวอร์ ซึ่งสามารถทำงานได้เหมือนเว็บเซิร์ฟเวอร์ปกติทั่วไป
