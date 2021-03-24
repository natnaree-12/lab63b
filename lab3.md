# การทดลองที่ 3 เรื่อง การเขียนโปรแกรมเอ้าพุทสัญญาณดิจิทัล
## วัตถุประสงค์
1.เพื่อทำความเข้าใจเกี่ยวกับการเขียนโปรแกรมเอ้าพุทสัญญาณดิจิทัล

2.เพื่อทำความเข้าใจเกี่ยวกับการทำงานของไมโครคอนโทรเลอร์ กับ Adapter

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
  * ขณะที่ run เพื่อให้ microcontroller รับข้อมูลใหม่เข้าไป ให้กดปุ่มดังรูป
  
![image](https://user-images.githubusercontent.com/80879788/112356324-14e57d80-8d01-11eb-8933-16e3e6031db3.png)

5.เมื่อโปรแกรมทำการดาวน์โหลดเสร็จแล้ว
  * พิมพ์ pio device monitor กด Enter เพื่อดูผลลัพธ์จากคอมพิวเตอร์

## การบันทึกผลการทดลอง
เมื่อทำการพิมพ์ pio device monitor กด Enter เพื่อดูผลลัพธ์จากคอมพิวเตอร์ จะเห็นได้ว่าโปรแกรมจะขึ้น ON หรือ OFF สลับกัน และหลอดไฟ LED ที่ถูกต่อกับสายสีขาวหรือ port0 จะไฟติดเมื่อโปรแกรมเป็น ON ส่วนหลอดสีน้ำเงินที่ต่อกับสายสีเหลืองจะไม่ติด เพราะป้อน output ไปที่ port0 และเมื่อทำการกดปุ่มรีเซท โปรแกรมก็จะเริ่มทำงานใหม่

![image](https://user-images.githubusercontent.com/80879788/112356970-b076ee00-8d01-11eb-8df2-ae989d0a6ddd.png)

## อภิปรายผลการทดลอง
ในการทดลองนี้ใช้ microcontroller ESP01 ซึ่งมีทั้ง CPU และเสาสำหรับรับ wife ใช้ Serial Port Compuuter เป็นตัวป้อนโปรแกรมใส่ microcontroller ESP01 นอกจากนี้ในการทดลองนี้ยังมีการใช้ Adapter เข้ามาเป็นตัวสังเกตการทำงานของ microcontroller ซึ่งเมื่อการอัปโหลดข้อมูลและrunโปรแกรม พบว่า โปรแกรมจะขึ้น ON หรือ OFF สลับกัน และหลอดไฟ LED ที่ถูกต่อกับสายสีขาวหรือ port0 จะไฟติดเมื่อโปรแกรมเป็น ON ส่วนหลอดสีน้ำเงอนที่ต่อกับสายสีเหลืองจะไม่ติดเพราะป้อน output ไปที่ port0 เมื่อทำการกดปุ่มรีเซท โปรแกรมก็จะเริ่มทำงานใหม่
