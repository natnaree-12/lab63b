# การทดลองที่ 3 เรื่อง การเขียนโปรแกรมเอ้าพุทสัญญาณดิจิทัล
## วัตถุประสงค์
1.เพื่อทำความเข้าใจเกี่ยวกับการเขียนโปรแกรมเอ้าพุทสัญญาณดิจิทัล

2.เพื่อทำความเข้าใจเกี่ยวกับการต่อไมโครคอนโทรเลอร์

## อุปกรณ์ที่ใช้ 
1.microcontroller ESP01

2.USB

3.Serial Port Compuuter

4.Commuter

5.adapter

## ศึกษาข้อมูลเบื้องต้น
* https://www.youtube.com/watch?v=CCnN1WJsXQY&ab_channel=TANI-IOT

## วิธีการทำการทดลอง
1.ต่อสาย USB เข้า Serial Port จากนั้นเสียบ Adapter ทับลงบน Serial Port

![image](https://user-images.githubusercontent.com/80879788/112347789-c1236600-8cf9-11eb-86db-a88de73a826b.png)

2.เสียบ microcontroller ESP01 ลงบน Adapter

![image](https://user-images.githubusercontent.com/80879788/112348112-1a8b9500-8cfa-11eb-9a3d-aa04c43143b6.png)

3.เตรียมดาวน์โหลดโปรแกรม
  * พิมพ์ ls กด Enter แสดง platformio.ini src
  * พิมพ์ pwd กด Enter

![image](https://user-images.githubusercontent.com/80879788/112354866-b2d84880-8cff-11eb-9cc4-10073d46a679.png)
  
  * พิมพ์ vi src/main.cpp กด Enter แสดงโปรแกรมดังรูป

![image](https://user-images.githubusercontent.com/80879788/112355130-f16e0300-8cff-11eb-9ac2-f8b57ca0a611.png)

4.อัปโหลดโปรแกรมเข้าสู่ microcontroller
  * พิมพ์ pio run -t upload กด Enter

![image](https://user-images.githubusercontent.com/80879788/112343763-034aa880-8cf6-11eb-89ea-113483a506f6.png)

  * ขณะที่ run เพิ่อให้ microcontroller รับข้อมูลใหม่เข้าไป ให้กดปุ่มดังรูป
  
![image](https://user-images.githubusercontent.com/80879788/112314503-af32ca80-8cdb-11eb-93fa-6a50fb3912f6.png)

5.เมื่อโปรแกรมทำการดาวน์โหลดเสร็จแล้ว
  * พิมพ์ pio device monitor กด Enter เพื่อดูผลลัพธ์จากคอมพิวเตอร์

![image](https://user-images.githubusercontent.com/80879788/112344323-8ec43980-8cf6-11eb-9477-7eed3f2175dc.png)

## การบันทึกผลการทดลอง
ทำการทดลองแล้ว พบว่า เมื่อทำการพิมพ์ pio device monitor กด Enter เพื่อดูผลลัพธ์จากคอมพิวเตอร์ จะเห็นได้ว่าตัวแปรเคาท์ทำการนับเพิ่มทีละ1 ไปเรื่อย จากน้อยไปมาก และจะแสดงผลทุกๆ 1 วินาที 

![image](https://user-images.githubusercontent.com/80879788/112316240-7dbafe80-8cdd-11eb-9863-59ed1356b1c7.png)

เมื่อกดปุ่มรีเซทโปรแกรมจะเริ่มนับ 1 ใหม่

![image](https://user-images.githubusercontent.com/80879788/112316743-f9b54680-8cdd-11eb-88cb-b0add704c60c.png)

## อภิปรายผลการทดลอง

ในการทดลองนี้ใช้ microcontroller ESP01 ซึ่งมีทั้ง CPU และเสาสำหรับรับ wife ใช้ Serial Port Compuuter เป็นตัวป้อนโปรแกรมใส่ microcontroller ESP01 ในการทดลองนี้จะเลือกตัวอย่างโปรแกรม 01_Serial Monitor เพื่อนำมา run โดยในตัวอย่างโปรแกรมนี้มี 15 บรรทัด
มี 2 ส่วน หรือ 2 ฟังก์ชัน คือ c language และ c plus+ language ในส่วนของ setup จะทำการ run ครั้งเดียว โดยจะเซท Serial Port ที่ความเร็ว 115200  ส่วน loop จะเพิ่มตัวแปร cnt ขึ้นเรื่อยๆ โดยจะแสดงตัวแปร cnt และจะหน่วงเวลา 1 วินาที ในแต่ละโปรแกรมเมื่อใช้ platfomio จะมี configuration file ชื่อว่า vi platfomio.ini สามารถบอกถึงข้อมูลเกี่ยวกับ platform ได้ และเมื่อทำการดาวน์โหลดข้อมูลสำเร็จ และทำการrunโปรแกรม จะเห็นได้ว่าตัวแปรเคาท์ทำการนับเพิ่มทีละ1 ไปเรื่อย จากน้อยไปมาก และจะแสดงผลทุกๆ 1 วินาที เมื่อกดปุ่มรีเซทโปรแกรมจะเริ่มนับ 1 ใหม่

## คำถามหลังการทดลอง
