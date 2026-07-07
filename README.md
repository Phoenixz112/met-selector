# MET Selector 🛗

**เครื่องมือเลือกลิฟต์และบันไดเลื่อน Mitsubishi Electric Thailand**

🔗 **เข้าใช้งาน:** https://phoenixz112.github.io/met-selector/

---

## เกี่ยวกับ App นี้

MET Selector คือเครื่องมือภายในสำหรับพนักงานและคู่ค้าของ Mitsubishi Electric Thailand เพื่อ:
- ค้นหารุ่นลิฟต์ที่เหมาะกับขนาด Shaft ที่มีอยู่
- ดูข้อมูล Specification ครบถ้วนของแต่ละรุ่น
- คำนวณขนาด Beam-to-Beam ของบันไดเลื่อน

---

## ประเภทสินค้า

| ประเภท | Series |
|--------|--------|
| 🛗 ลิฟต์โดยสาร | NEXIEZ-MRL II, NEXIEZ-FIT, NEXIEZ-S, NEXIEZ-MR, NEXWAY-S-AP II, NEXWAY Package R, NEXIEZ-MR BED |
| 🏠 ลิฟต์บ้าน | SHA, SVC |
| 🏭 ลิฟต์บรรทุก | GFM-T (Melina), GFCL2/GFCL3 (TMEC), LEHY (SMEC) |
| 🪜 บันไดเลื่อน | Smart K-II (S1200/S1000/S800) |

---

## วิธีใช้งาน

1. **กรอกข้อมูลผู้ใช้** — ชื่อบริษัทและประเภทบริษัท
2. **เลือกประเภทสินค้า** — ลิฟต์โดยสาร / ลิฟต์บ้าน / ลิฟต์บรรทุก / บันไดเลื่อน
3. **เลือกโหมดค้นหา**
   - **By Shaft Size** — กรอกขนาด AH × BH × TR → ระบบแสดงรุ่นที่เข้าได้พร้อม Tolerance
   - **By Model** — เลือก Series → กำหนด Spec → ดู Drawing และ Dimension ครบถ้วน

**การเผื่อขนาด Shaft (Tolerance)**
- TR ≤ 60m → เผื่อด้านละ ±50mm
- TR > 60m → เผื่อด้านละ ±100mm
- 2-Gate: ด้านลึก BH เผื่อเฉพาะด้านหลัง +50mm เท่านั้น

---

## การจัดการข้อมูล

ข้อมูลสินค้าทั้งหมดเก็บใน **Google Sheets** — แก้ไขได้โดยไม่ต้องแตะ Code

📊 **Google Sheets:** [MET Selector Data](https://docs.google.com/spreadsheets/d/1OjCye8QlxaNXojs6fckuyjIK9wQ3F-L5QIfwHemvQps)

### โครงสร้าง Sheets

| Sheet | รายละเอียด |
|-------|-----------|
| `PASSENGER_HORIZONTAL` | ขนาด Shaft ของลิฟต์โดยสารทุกรุ่น |
| `PASSENGER_VERTICAL` | OH, PD, HM แยกตาม Speed และ Travel |
| `HOME_ELEVATOR` | ขนาด Shaft และ Vertical ของลิฟต์บ้าน SHA/SVC |
| `FREIGHT` | Specification ลิฟต์บรรทุก |
| `ESCALATOR_SETS` | TJ/TK Sets และข้อมูล Model บันไดเลื่อน |
| `ESCALATOR_RANGES` | Rise Range แยกตาม Model/Angle/Speed |
| `LOG` | บันทึกการใช้งานอัตโนมัติ |

### วิธีแก้ไขข้อมูล

1. เปิด Google Sheets ด้านบน
2. เลือก Sheet ที่ต้องการแก้ไข
3. แก้ไขข้อมูลได้เลย (แถวที่ 1 คือ Header — ห้ามแก้)
4. บันทึก → App จะดึงข้อมูลใหม่อัตโนมัติทุกครั้งที่เปิด

---

## เทคโนโลยีที่ใช้

| ส่วน | เทคโนโลยี |
|------|-----------|
| Frontend | HTML / CSS / JavaScript (ไม่ใช้ Framework) |
| Hosting | GitHub Pages |
| ข้อมูล | Google Sheets (Visualization API) |
| Log | Google Apps Script Web App |

> ใช้ไฟล์เดียว (`index.html`) เพื่อให้ทีมที่ไม่ใช่ Developer ดูแลรักษาได้ง่าย

---

## การ Deploy

```
Repository : https://github.com/phoenixz112/met-selector
Branch     : main
File       : index.html
URL        : https://phoenixz112.github.io/met-selector/
```

หลังแก้ไข `index.html` → รอ ~2 นาที → GitHub Pages Deploy อัตโนมัติ

---

## Roadmap

### ✅ Phase 0 — Setup
- สร้าง App โครงสร้างหลัก, เชื่อม Google Sheets, Deploy GitHub Pages

### 🔄 Phase 1 — Data (กำลังดำเนินการ)
- เพิ่มข้อมูลลิฟต์ให้ครบทุก Series และทุก Spec
- ตรวจสอบความถูกต้องของข้อมูลกับ Catalog จริง
- เพิ่มข้อมูล MESE (NEXWAY, NEXWAY-S, NEXIEZ-MRL)
- เพิ่มข้อมูลบันไดเลื่อน Smart K-II ครบทุก Configuration

### ⏳ Phase 2 — UX/UI
- ปรับ UX/UI ให้เหมาะกับกลุ่มเป้าหมาย
- พิจารณาว่าลูกค้าแต่ละกลุ่มควรได้รับข้อมูลในระดับไหน
- ปรับ Flow การใช้งานให้เหมาะกับ Mobile

### ⏳ Phase 3 — คู่มือการใช้งาน
- จัดทำคู่มือสำหรับผู้ใช้งาน (User Manual)
- จัดทำคู่มือสำหรับผู้ดูแลระบบ (Admin Manual)
- วิธีแก้ไขข้อมูลใน Google Sheets

### ⏳ Phase 4 — เชื่อม Catalog
- เพิ่ม Link ไปยัง Catalog ของแต่ละรุ่น
- เชื่อมโยงข้อมูล Spec กับเอกสาร PDF

### ⏳ Phase 5 — Production Deploy
- Deploy ขึ้นเว็บไซต์บริษัท
- วางแผนระบบหลังบ้าน (Backend)
- ระบบ Authentication สำหรับผู้ใช้งาน
- ระบบวิเคราะห์ข้อมูล Log

---

## บันทึก Log การใช้งาน

ทุกครั้งที่ค้นหา ระบบจะบันทึกลง Sheet `LOG` อัตโนมัติ ประกอบด้วย:
- วันเวลา, ชื่อบริษัท, ประเภทบริษัท
- โหมดค้นหา, Series, Capacity, Door, Gate, Speed, Travel
- ขนาด Shaft ที่ค้นหา และจำนวน Result ที่พบ

ใช้วิเคราะห์ได้ว่าลูกค้ากลุ่มไหนสนใจลิฟต์ประเภทไหนมากที่สุด

---

*สร้างโดย Mitsubishi Electric Thailand · ใช้งานภายในองค์กร*
