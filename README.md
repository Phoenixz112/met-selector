# MET Selector 🛗

**Mitsubishi Elevator & Escalator Selection Tool**  
เครื่องมือเลือกลิฟต์และบันไดเลื่อน Mitsubishi Electric Thailand

🔗 **Live App:** https://phoenixz112.github.io/met-selector/

---

## What is this? / เกี่ยวกับ App นี้

MET Selector is an internal web tool for Mitsubishi Electric Thailand staff and partners to:
- Find elevator models that fit a given shaft size
- View full specifications of any elevator model
- Calculate escalator Beam-to-Beam dimensions

MET Selector คือเครื่องมือภายในสำหรับพนักงานและคู่ค้าของ Mitsubishi Electric Thailand เพื่อ:
- ค้นหารุ่นลิฟต์ที่เหมาะกับขนาด Shaft ที่มีอยู่
- ดูข้อมูล Specification ครบถ้วนของแต่ละรุ่น
- คำนวณขนาด Beam-to-Beam ของบันไดเลื่อน

---

## Product Categories / ประเภทสินค้า

| Category | Series |
|----------|--------|
| 🛗 Passenger Elevator | NEXIEZ-MRL II, NEXIEZ-FIT, NEXIEZ-S, NEXIEZ-MR, NEXWAY-S-AP II, NEXWAY Package R, NEXIEZ-MR BED |
| 🏠 Home Elevator | SHA, SVC |
| 🏭 Freight Elevator | GFM-T (Melina), GFCL2/GFCL3 (TMEC), LEHY (SMEC) |
| 🪜 Escalator | Smart K-II (S1200/S1000/S800) |

---

## How to Use / วิธีใช้งาน

**1. Fill in Profile / กรอกข้อมูลผู้ใช้**
- Enter company name and type
- กรอกชื่อบริษัทและประเภทบริษัท

**2. Select Category / เลือกประเภทสินค้า**
- Choose between Passenger, Home, Freight, or Escalator
- เลือกประเภทสินค้าที่ต้องการ

**3. Query Mode / โหมดค้นหา**
- **By Shaft Size** — Enter AH × BH × TR → Get matching models + tolerance
- **By Model** — Select series → Configure specs → View full drawing & dimensions

**Shaft Tolerance / การเผื่อขนาด Shaft**
- TR ≤ 60m → ±50mm each side
- TR > 60m → ±100mm each side
- 2-Gate: BH rear side only +50mm

---

## Data Management / การจัดการข้อมูล

All product data is stored in **Google Sheets** — no coding required to update.

ข้อมูลสินค้าทั้งหมดเก็บใน **Google Sheets** — แก้ไขได้โดยไม่ต้องแตะ Code

📊 **Google Sheets:** [MET Selector Data](https://docs.google.com/spreadsheets/d/1OjCye8QlxaNXojs6fckuyjIK9wQ3F-L5QIfwHemvQps)

### Sheet Structure / โครงสร้าง Sheets

| Sheet | Description |
|-------|-------------|
| `PASSENGER_HORIZONTAL` | Shaft dimensions for all passenger elevator models |
| `PASSENGER_VERTICAL` | Overhead (OH), Pit depth (PD), Machine room height per speed/travel |
| `HOME_ELEVATOR` | SHA/SVC home elevator dimensions |
| `FREIGHT` | Freight elevator specifications |
| `ESCALATOR_SETS` | TJ/TK sets and model metadata for escalator calculator |
| `ESCALATOR_RANGES` | Rise ranges per model/angle/speed |
| `LOG` | Auto-logged user search history |

### How to Update Data / วิธีแก้ไขข้อมูล

**เพิ่ม/แก้ไขข้อมูลลิฟต์:**
1. เปิด Google Sheets ด้านบน
2. เลือก Sheet ที่ต้องการแก้ไข
3. แก้ไขข้อมูลได้เลย (Row 1 คือ Header ห้ามแก้)
4. บันทึก → App จะดึงข้อมูลใหม่อัตโนมัติทุกครั้งที่เปิด

**เพิ่มข้อมูลด้วย Apps Script (ครั้งแรก):**
- เปิด Google Sheets → Extensions → Apps Script
- รัน Script ที่เกี่ยวข้อง (อยู่ในโฟลเดอร์ `scripts/`)

---

## Technical Stack / เทคโนโลยีที่ใช้

| Component | Technology |
|-----------|------------|
| Frontend | Pure HTML/CSS/JavaScript (no framework) |
| Hosting | GitHub Pages |
| Data | Google Sheets (Visualization API) |
| Logging | Google Apps Script Web App |
| Fonts | Inter, Roboto Mono (Google Fonts) |

**Why no framework? / ทำไมไม่ใช้ Framework?**  
เพื่อให้ทีมที่ไม่ใช่ Developer สามารถดูแลรักษาได้ง่าย ไฟล์เดียว (`index.html`) ดูแลทุกอย่าง

---

## Deployment / การ Deploy

App ใช้ **GitHub Pages** — Deploy อัตโนมัติเมื่อมีการ Push ขึ้น `main` branch

```
Repository: https://github.com/phoenixz112/met-selector
Branch: main
File: index.html
URL: https://phoenixz112.github.io/met-selector/
```

**หลังแก้ไข `index.html`:**
1. Upload ไฟล์ขึ้น GitHub (หรือ Edit ใน GitHub โดยตรง)
2. รอ ~2 นาที ให้ GitHub Pages Deploy
3. ตรวจสอบสถานะที่ `Actions` tab

---

## Logging / การบันทึก Log

ทุกครั้งที่ User ค้นหา ระบบจะบันทึกข้อมูลลง Sheet `LOG` อัตโนมัติ ประกอบด้วย:
- Timestamp, Company, Company Type
- Query Mode (By Shaft / By Model)
- Series, Capacity, Door, Gate, Speed, Travel
- Shaft dimensions searched / results found

ใช้ดูได้ว่า User สนใจลิฟต์กลุ่มไหนมากที่สุด

---

## Contact / ติดต่อ

**Mitsubishi Electric Thailand (MET)**  
สอบถามข้อมูลเพิ่มเติมเกี่ยวกับ App ติดต่อทีม MET โดยตรงครับ

---

*Last updated: 2025 · Built for internal use at Mitsubishi Electric Thailand*
