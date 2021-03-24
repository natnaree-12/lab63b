# การทดลองที่ 5 เรื่อง การเขียนโปรแกรมเชื่อมต่อไวไฟและเว็บเซอร์เวอร์

## วัตถุประสงค์
1.เพื่อทำความเข้าใจเกี่ยวกับการเขียนโปรแกรมเชื่อมต่อไวไฟและเว็บเซอร์เวอร์

2.เพื่อทำความเข้าใจเกี่ยวกับการทำงานของ

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
  
![image](https://user-images.githubusercontent.com/80879788/112314503-af32ca80-8cdb-11eb-93fa-6a50fb3912f6.png)  
5.เมื่อโปรแกรมทำการดาวน์โหลดเสร็จแล้ว
  * พิมพ์ pio device monitor กด Enter เพื่อดูผลลัพธ์จากคอมพิวเตอร์

6.จากนั้นต่อเซนเซอร์ตรวจจับแสง ดังรูป

![image](https://user-images.githubusercontent.com/80879788/112372079-e8862d00-8d11-11eb-9ade-6c8f9703f542.png)

7.ต่อสายไฟสีขาวที่จุดที่นิ้วชี้อยู่ และสังเกตผล จากนั้นนำนิ้วมาบังเซนเซอร์ตรวจจับแสง และสังเกตผล

![image](https://user-images.githubusercontent.com/80879788/112372466-677b6580-8d12-11eb-84f8-9f6c075dfe84.png)

## การบันทึกผลการทดลอง
* เมื่อทำการพิมพ์ pio device monitor กด Enter เพื่อดูผลลัพธ์จากคอมพิวเตอร์ จะเห็นได้ว่าโปรแกรมจะขึ้น read 1 เมื่อไม่ได้จิ้มสายไฟสีขาว แต่ถ้านำไปจิ้มในช่องที่สายไฟสีแดง สีดำและสีเหลืองตัวโปรแกรมก็จะขึ้น read 0 
* เมื่อจิ้มสายไฟไปที่ช่องที่มีสายไฟสีดำก็จะทำให้หลอดไฟติด และถ้าหากกดปุ่มีดำค้างเอาไว้ตัวโปรแกรมก็จะขึ้น read 0 ทำให้เมื่อเรากดปุ่มสีดำค้างเอาไว้หลอดไฟก็จะติดตลอดเวลา 
* เมื่อนำตัวเซนต์เซอร์ตัวจับแสงไปต่อ พบว่า เมื่อนำนิ้วมือไปบังแสงโปรแกรมจะขึ้น read 1 คือไฟไม่ติด แต่เมื่อเอานิ้วมือออก พบว่า โปรแกรมจะขึ้น read 0 คือไฟติด

  * read 1

![image](https://user-images.githubusercontent.com/80879788/112370685-43b72000-8d10-11eb-944e-f383f3891d6f.png)

  * read 0

![image](https://user-images.githubusercontent.com/80879788/112370799-6812fc80-8d10-11eb-82c4-37a1b3540403.png)

 * เมื่อไม่ได้บังแสงเซนเซอร์ตรวจจับแสง
 
 ![image](https://user-images.githubusercontent.com/80879788/112373771-e9b85980-8d13-11eb-9f4e-b3cb7dbce397.png)

 * เมื่อบังแสงเซนเซอร์ตรวจจับแสง
 
 ![image](https://user-images.githubusercontent.com/80879788/112373981-22f0c980-8d14-11eb-9521-c3dc396e1e03.png)


## อภิปรายผลการทดลอง
