# การนำเข้า

การนำเข้า สามารถเข้าถึงได้ เฉพาะสำหรับ ผู้ใช้ ที่เป็นผู้ดูแลระบบ เท่านั้น การดูแลระบบ > นำเข้า คุณสามารถนำเข้า เฉพาะจาก ไฟล์ CSV

## ขั่นตอน ที่ 1

เลือก ประเภทข้อมูลที่ คุณต้องการนำเข้า (Entity Type field).
เลือก CSV ไฟล์  ไฟล์ ควรได้รับการฟอร์แมตด้วย `UTF-8`.
เลือก `What to do?`ตัวเลือก ที่สามารถใช้งานได้: 'สร้าง เท่านั้น', 'สร้าง & อัปเดต', 'อัปเดต เท่านั้น'.

* `Create Only` - เลือก หากคุณต้องการ สร้างการบันทึกเท่านั้น.
* `Create & Update` - บันทึกจะถูกสร้างขึ้น แต่ถ้า บันทึกที่มีค่าฟิลด์ที่ตรงกัน จะพบว่าบันทึกนั้น ได้รับการอัปเดต คุณสามารถตรวจสอบได้ ว่าจะให้ฟิลด์ใดตรงกัน เมื่อเปิด  _Step 2_.
* `Update only` - เฉพาะ บันทึกที่มีค่าฟิลด์ที่ตรงกันเท่านั้น ถึงจะมีการอัปเดต

เมื่อคุณเลือกไฟล์ csv คุณจะสามารถดูว่า ควรจะแยกการวิเคราะห์ ในแผงแสดงตัวอย่าง อย่างไร เมื่อ คุณเปลี่ยนคุณสมบัติพรีวิวจะได้รับการอัปเดต

* `Header Row` - ไฟล์ CSV แถวแรก มีชื่อฟิลด์หรือไม่
* `Execute in idle` - แนะนำถ้าคุณมีบันทึกที่จะนำเข้าเป็นกลุ่มใหญ่
 การนำเข้าจะประมวลผลผ่าน cron สถานะจะเป็น "เสร็จสิ้น" เมื่อกระบวนการนำเข้าเสร็จสิ้น
* `Skip searching for duplicates` - มันจะลดการนำเข้าตามเวลา

คลิก ปุ่ม  _Next_ เพื่อดำเนินการ _Step 2_ต่อไป

![1](https://raw.githubusercontent.com/espocrm/documentation/master/docs/_static/images/administration/import/step-1.png)

## ขั้นตอน ที่ 2

ตั้งค่า field mapping: ฟิลด์ จะตรงกับ คอลัมน์ของไฟล์ CSV อย่างไร คุณสามารถข้ามคอลัมน์ ที่ไม่จำเป็นได้ ที่นี่
ในกรณีของ 'สร้าง & อัปเดต' และ 'อัปเดต เท่านั้น' คุณต้องตรวจสอบ fields โดยบันทึก ควรเป็นอัปเดต จึงจะค้นพบ เพิ่มค่าเริ่มต้น ที่คุณต้องการให้บันทึกใหม่ และ อัปเดตบันทึก ที่จะตั้งค่าด้วย เช่น  คุณสามารถระบุฟิลด์ ผู้ใช้ หรือ ทีม ที่ได้รับมอบหมาย


หลังจากนำเข้าเสร็จแล้วคุณจะสามารถเปลี่ยนแปลงบันทึกที่สร้างขึ้นใหม่ได้, ดูรายการที่ซ้ำกันและรบันทึกที่ได้อัปเดต. สำเนา หมายความว่า มีบันทึก ที่คล้ายกัน ในระบบ คุณสามารถ นำรายการที่ซ้ำกันทั้งหมด สามารถ นำเข้าออกได้พร้อมกัน หมายเหตุ: การย้อนกลับไม่ทำงานกับบันทึกที่อัปเดตไปแล้ว

คลิกที่ปุ่ม _Run Import_ เพื่อดำเนินการต่อ อาจใช้เวลาสักครู่หนึ่ง ก่อนที่ขั้นตอน การนำเข้าจะเสร็จสิ้น ถ้าคุณต้องการนำเข้าบันทึกเป็นจำนวนมาก (ขึ้นอยู่กับการกำหนดค่าเซิร์ฟเวอร์ของคุณ,ปกติถ้ามากกว่า 200 บันทึก) คุณต้องแน่ใจว่า php parameter `set_time_limit` นั้นมีพื้นที่มากพอ.

![2](https://raw.githubusercontent.com/espocrm/documentation/master/docs/_static/images/administration/import/step-2.png)

## วิธีการนำเข้าสู่รายการเป้าหมาย

เมื่อคุณนำเข้าที่อยู่เพื่อติดต่อ, โอกาสในการขาย หรือ บัญชีของคุณ สามารถเพิ่มลงในรายการเป้าหมายได้. ในขั้นตอนที่ 2 คุณต้องเพิ่มรายการเป้าหมายลงใน field `Default Values` และเลือกบันทึกรายการเป้าหมายที่ต้องการ คุณยังสามารถใช้`Update only` หรือ `Create & Update` นำเข้าเพื่อเพิ่มเป้าหมายที่มีอยู่แล้ว ในรายการเป้าหมาย
