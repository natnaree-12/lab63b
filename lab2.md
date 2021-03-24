# การทดลองที่ 2 เรื่อง การเขียนโปรแกรมค้นหาไวไฟ

## วัตถุประสงค์
1.เพื่อทำความเข้าใจเกี่ยวกับการเขียนโปรแกรมค้นหาไวไฟ

2.เพื่อทำความเข้าใจเกี่ยวกับการต่อไมโครคอนโทรเลอร์ที่นำมาเขียนโปรแกรม

## อุปกรณ์ที่ใช้ 
1.microcontroller ESP01

2.USB

3.Serial Port Compuuter

4.Computer

## ศึกษาข้อมูลเบื้องต้น
* https://www.youtube.com/watch?v=yBjab0UNuB8&ab_channel=TANI-IOT

## วิธีการทำการทดลอง
1.ต่อสาย USB เข้า Serial Port Compuuter 

![image](https://user-images.githubusercontent.com/80879788/112309445-e9996900-8cd5-11eb-8f4c-da72cbde1663.png)


2.เสียบ microcontroller ESP01 ลงบน Serial Port Compuuter

![image](https://user-images.githubusercontent.com/80879788/112309332-cd95c780-8cd5-11eb-91ec-f39c35bd417c.png)


3.เตรียมดาวน์โหลดโปรแกรม
  * พิมพ์ ls กด Enter แสดง platformio.ini src
  * พิมพ์ vi src/main.cpp กด Enter แสดงโปรแกรมดังรูป

![image](https://user-images.githubusercontent.com/80879788/112343184-76075400-8cf5-11eb-9166-62e11abab0a3.png)

4.อัปโหลดโปรแกรมเข้าสู่ microcontroller
  * พิมพ์ pio run -t upload กด Enter

![image](https://user-images.githubusercontent.com/80879788/112343763-034aa880-8cf6-11eb-89ea-113483a506f6.png)

  * ขณะที่ run เพื่อให้ microcontroller รับข้อมูลใหม่เข้าไป ให้กดปุ่มดังรูป
  
![image](https://user-images.githubusercontent.com/80879788/112314503-af32ca80-8cdb-11eb-93fa-6a50fb3912f6.png)

5.เมื่อโปรแกรมทำการดาวน์โหลดเสร็จแล้ว
  * พิมพ์ pio device monitor กด Enter เพื่อดูผลลัพธ์จากคอมพิวเตอร์

## การบันทึกผลการทดลอง
เมื่อทำการพิมพ์ pio device monitor กด Enter เพื่อดูผลลัพธ์จากคอมพิวเตอร์ พบว่า เมื่อเริ่มต้นการสแกนเพื่อค้นหาไวไฟ เจอไวไฟ 2 หรือ4 ตัว ดังรูป

![image](https://user-images.githubusercontent.com/80879788/112344881-2033ab80-8cf7-11eb-8e27-4617f42e8c30.png)

เมื่อกดปุ่มรีเซทโปรแกรม โปรแกรมจะเริ่มการค้นหาไวไฟใหม่ ดังรูป

![image](https://user-images.githubusercontent.com/80879788/112344806-0e520880-8cf7-11eb-9eb4-679e556f90a0.png)


## อภิปรายผลการทดลอง

ในการทดลองนี้ใช้ microcontroller ESP01 ซึ่งมีทั้ง CPU และเสาสำหรับรับ wife ใช้ Serial Port Compuuter เป็นตัวป้อนโปรแกรมใส่ microcontroller ESP01 ในการทดลองนี้จะมีตัวโปรแกรมอยู่ 2 ส่วน คือ ตัวแรก setup ใช้สำหรับการเตรียมพร้อเพื่อค้นหาไวไฟ ส่วนที่2 คือส่วน loop ใช้สำหรับเก็บข้อมูลเมื่อเจอไวไฟ ว่าเจอกี่ตัว ชื่ออะไรบ้าง และจะวนloopไปเรื่อยๆจนกระทั่งไม่เจอไวไฟแล้ว ซึ่งเมือทำการติดตั้งและเริ่มการค้นหาไวไฟ พบว่า เจอไวไฟ2 หรือ 4 ตัว และเมื่อทำการกดปุ่มรีเซท โปรแกรมจะเริ่มการค้นหาไวไฟใหม่ทันที

