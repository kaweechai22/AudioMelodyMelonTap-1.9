# MelodyMelonTap Clean Stable v19

Clean rebuild: ตัดโค้ดซ้ำ/โค้ดเก่า/เอฟเฟกต์ออก เหลือระบบหลักที่เสถียร


## v19.1 Audio Retry Fix
- ปรับเงื่อนไข “ผลการวัดยังไม่นิ่ง” ไม่ให้เข้มเกินไป
- หากสัญญาณไม่นิ่งเล็กน้อย แอปจะแสดงผลต่อ พร้อมหมายเหตุให้วัดซ้ำเพื่อยืนยัน
- จะบังคับวัดใหม่เฉพาะกรณีสัญญาณแย่มากจริง ๆ


## v20 Raw2 Logic Restore
- กลับมาใช้สมการ Brix/Firmness/Juice/Hollow และ classifyRipenessAI จากชุด Raw2/v7 ซึ่งผู้ทดสอบพบว่าแม่นกว่า
- คง UI clean, 5 taps, audiofix และ AI Voice แบบธรรมชาติไว้
- ยกเลิกการใช้ Perfect Ripe เป็นตัวตัดสินระดับการสุกหลัก

## Voice Fix OK
- ปรับ AI Voice ให้ไม่อ่านคำว่า “ความกรอบ”
- ใช้คำว่า “เนื้อแน่น...” จาก crispText โดยตรง
- เว้นจังหวะด้วย comma
- ปรับความเร็วเสียงเป็น rate = 0.96
- Version: v2026.05.12-raw2-logic-v20-voicefix


## v22 Hybrid Audio120
- ใช้โครงสร้าง UI/Voice แบบ v20 ที่เสถียร
- ใส่สมการ RidgeCV จากข้อมูล Audio120
- เพิ่ม feature เสียง deployable: band energy, rolloff, peak count, peak2 ratio, attack/decay
- ใช้ Logistic Regression จาก Audio120 สำหรับระดับสุก

## v22.1 Ripeness Fix
- แก้ระดับการสุกไม่ตรง โดยไม่ใช้ Audio120 classifier เป็นตัวตัดสินหลัก
- ใช้ Raw2/v20 classifyRipenessAI เป็นตัวหลัก เพราะเสถียรกว่าในสนามจริง
- Audio120 ยังใช้ทำนาย Brix/Firmness/Juice/Hollow และแสดงผลใน debug
- เพิ่ม guard rule กันกรณีแอปบอก “ดิบ” ทั้งที่ Brix/Juice/Hollow ชี้ว่าใกล้สุกหรือสุกพอดี
