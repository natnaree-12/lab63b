# การทดลองที่ 1 เรื่อง การเขียนโปรแกรมเพื่อรันบนไมโครคอนโทรเลอร์

## วัตถุประสงค์
1.เพื่อทำความเข้าใจเกี่ยวกับการเขียนโปรแกรมเพื่อรันบนไมโครคอนโทรเลอร์

2.เพื่อทำความเข้าใจเกี่ยวกับการต่อไมโครคอนโทรเลอร์ที่นำมาเขียนโปรแกรม

## อุปกรณ์ที่ใช้ 
1.microcontroller ESP01

2.USB

3.Serial Port Computer

4.Computer

## ศึกษาข้อมูลเบื้องต้น
* https://www.youtube.com/watch?v=NLIUsWLEpmg&ab_channel=TANI-IOT

## วิธีการทำการทดลอง
1.ต่อสาย USB เข้า Serial Port Compuuter 

![image](https://user-images.githubusercontent.com/80879788/112309445-e9996900-8cd5-11eb-8f4c-da72cbde1663.png)


2.เสียบ microcontroller ESP01 ลงบน Serial Port Compuuter

![image](https://user-images.githubusercontent.com/80879788/112309332-cd95c780-8cd5-11eb-91ec-f39c35bd417c.png)


3.เขียนโปรแกรม ดูตัวอย่างโปรแกรม ที่โฟรเดอร์ pattani
  
  * พิมพ์ cd pattani เพื่อไปที่โฟลเดอร์ ซึ่งมีโปรแกรมตัวอย่าง 9 โปรแกรม
  * จากนั้นไปที่ตัวอย่างที่ 1 
    * พิมพ์ cd 01_Serial Monitor กดEnter
    * พิมพ์ vi src/main.cpp กดEnter
    
![image](https://user-images.githubusercontent.com/80879788/112310657-6aa53000-8cd7-11eb-8d70-da7305c4f50d.png)
    
4.แสดงโปรแกรมทดสอบ 15 บรรทัด 

![image](https://user-images.githubusercontent.com/80879788/112311363-341be500-8cd8-11eb-9818-4add5548f275.png)

5.พิมพ์ vi po\latformio.ini เพื่อเป็นการตรวจสอบข้อมูลของ platform

![image](https://user-images.githubusercontent.com/80879788/112312032-ece22400-8cd8-11eb-9b5a-df2ae9d06a45.png)

6. ทำการอัปโหลดโปรแกรม 01_Serial Monitor
  * พิมพ์ pio run -t upload กด Enter
  * ขณะที่ run เพิ่อให้ microcontroller รับข้อมูลใหม่เข้าไป ให้กดปุ่มดังรูป
  
  ![image](https://user-images.githubusercontent.com/80879788/112314503-af32ca80-8cdb-11eb-93fa-6a50fb3912f6.png)

7.เมื่อโปรแกรมทำการดาวน์โหลดเสร็จแล้ว
  * พิมพ์ pio device monitor กด Enter เพื่อดูผลลัพธ์จากคอมพิวเตอร์
 
## การบันทึกผลการทดลอง
ทำการทดลองแล้ว พบว่า เมื่อทำการพิมพ์ pio device monitor กด Enter เพื่อดูผลลัพธ์จากคอมพิวเตอร์ จะเห็นได้ว่าตัวแปรเคาท์ทำการนับเพิ่มทีละ1 ไปเรื่อย จากน้อยไปมาก และจะแสดงผลทุกๆ 1 วินาที 

![image](https://user-images.githubusercontent.com/80879788/112316240-7dbafe80-8cdd-11eb-9863-59ed1356b1c7.png)

เมื่อกดปุ่มรีเซทโปรแกรมจะเริ่มนับ 1 ใหม่

![image](https://user-images.githubusercontent.com/80879788/112316743-f9b54680-8cdd-11eb-88cb-b0add704c60c.png)

## อภิปรายผลการทดลอง

ในการทดลองนี้ใช้ microcontroller ESP01 ซึ่งมีทั้ง CPU และเสาสำหรับรับ wifi ใช้ Serial Port Compuuter เป็นตัวป้อนโปรแกรมใส่ microcontroller ESP01 ในการทดลองนี้จะเลือกตัวอย่างโปรแกรม 01_Serial Monitor เพื่อนำมา run โดยในตัวอย่างโปรแกรมนี้มี 15 บรรทัด มี 2 ส่วน หรือ 2 ฟังก์ชัน คือ c language และ c plus+ language ในส่วนของ setup จะทำการ run ครั้งเดียว โดยจะเซท Serial Port ที่ความเร็ว 115200  ส่วน loop จะเพิ่มตัวแปร cnt ขึ้นเรื่อยๆ โดยจะแสดงตัวแปร cnt และจะหน่วงเวลา 1 วินาที ในแต่ละโปรแกรมเมื่อใช้ platfomio จะมี configuration file ชื่อว่า vi platfomio.ini สามารถบอกถึงข้อมูลเกี่ยวกับ platform ได้ และเมื่อทำการดาวน์โหลดข้อมูลสำเร็จ และทำการrunโปรแกรม จะเห็นได้ว่าตัวแปรเคาท์ทำการนับเพิ่มทีละ1 ไปเรื่อย จากน้อยไปมาก และจะแสดงผลทุกๆ 1 วินาที เมื่อกดปุ่มรีเซทโปรแกรมจะเริ่มนับ 1 ใหม่



