# การทดลองที่ 7 เรื่อง รดน้ำต้นไม้ด้วยสมาร์ทโฟน

## วัตถุประสงค์ 

1.ศึกษาลักษณะวงจรที่นำมาต่อเพื่อสั่งการการรดต้นไม้

2.ศึกษาการเขียนโปรแกรมเพื่อใช้ในการสั่งการรดน้ำต้นไม้

## อุปกรณ์ที่ใช้ 

1.microcontroller ESP 32

![image](https://user-images.githubusercontent.com/80879788/113187378-fcd2a880-9282-11eb-9cc0-1f71daa305b7.png)

2.arduion 

![image](https://user-images.githubusercontent.com/80879788/113188236-fabd1980-9283-11eb-85c6-7caeb375881b.png)

3.บอร์ดขยาย

![image](https://user-images.githubusercontent.com/80879788/113188265-06104500-9284-11eb-8d21-e43802c0ae92.png)

4.Relay - Active Low 5V 10A

![image](https://user-images.githubusercontent.com/80879788/113188316-17595180-9284-11eb-989e-765e5630873b.png)

5.Power Supply 12 V

![image](https://user-images.githubusercontent.com/80879788/113188353-217b5000-9284-11eb-981f-2bac435e71c4.png)

6.โซลินอยต์

![image](https://user-images.githubusercontent.com/80879788/113188379-29d38b00-9284-11eb-8641-8e10df9d3bb3.png)

7.adapter

![image](https://user-images.githubusercontent.com/80879788/113188398-322bc600-9284-11eb-97de-8d323f2d7b1c.png)


8.ปุ่มสวิชต์

![image](https://user-images.githubusercontent.com/80879788/113188428-3bb52e00-9284-11eb-835c-12d227babd0a.png)

9.สายไฟ

![image](https://user-images.githubusercontent.com/80879788/113188462-47085980-9284-11eb-8fca-0eff9eaa7d88.png)


10.เซอร์กิตเบอร์เกอร์

![image](https://user-images.githubusercontent.com/80879788/113188499-5091c180-9284-11eb-95f9-5f6e12d5fd27.png)


## ศึกษาข้อมูลเบื้องต้น 

* http://www.lungmaker.com/%E0%B8%A7%E0%B8%B4%E0%B8%98%E0%B8%B5%E0%B9%83%E0%B8%8A%E0%B9%89-esp8266-esp-01-wifi/

* https://www.youtube.com/watch?v=uSKZbOIMiqw&ab_channel=SaranairChannel

* https://www.youtube.com/watch?v=Ik5TBPh3_Os&ab_channel=SaranairChannel

## วิธีการทำการทดลอง

1. ทำการต่อวงจรดังรูป

![image](https://user-images.githubusercontent.com/80879788/113190676-ca2aaf00-9286-11eb-8aa9-6adf1539653c.png)

2.อัพโหลดโค้ดใส่ ESP 32

* ลงโปรแกรม
* อัพโหลดโค้ด

![image](https://user-images.githubusercontent.com/80879788/113195974-21338280-928d-11eb-9b3f-f1d8b9447b25.png)

![image](https://user-images.githubusercontent.com/80879788/113196286-838c8300-928d-11eb-8466-6c54cb1a7ce0.png)

3.ทดสอบการทำงาน

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


## อภิปรายผลการทดลอง (พร้อมตัวอย่าง)

## คำถามหลังการทดลอง (พร้อมตัวอย่างคำตอบ)
