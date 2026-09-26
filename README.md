# Thai Report Format

Skill สำหรับ Codex เพื่อสร้างรายงานภาษาไทย พร้อมตัวอย่าง Word 14 หน้า ใช้ x แทนเนื้อหา มีขนาดกระดาษ A4/A3 ทั้งแนวตั้งและแนวนอน ระยะขอบ 10 ชุด สารบัญ 3 ระดับ สารบัญภาพ สารบัญตาราง และหัว–ท้ายกระดาษ

## สิ่งที่รวมไว้

- `skills/artifact-template-thai-report-format/SKILL.md` คำแนะนำสำหรับ Codex
- `skills/artifact-template-thai-report-format/assets/reference.docx` ไฟล์ตัวอย่างพร้อมใช้งาน
- `skills/artifact-template-thai-report-format/references/format-spec.md` ค่ารูปแบบโดยละเอียด
- `skills/artifact-template-thai-report-format/scripts/new_report.py` สคริปต์สร้างสำเนาและเปิดเลขคำบรรยายอัตโนมัติ

แพ็กเกจนี้ไม่มีรายงานต้นฉบับฉบับเต็ม

## ติดตั้ง

คัดลอกข้อความนี้ไปสั่ง Codex:

```text
ใช้ skill-installer ติดตั้ง skill จาก https://github.com/we-ever/Thai-Report-Format-skill/tree/main/skills/artifact-template-thai-report-format
```

[ดาวน์โหลดไฟล์ Word ตัวอย่าง](skills/artifact-template-thai-report-format/assets/reference.docx) · [อ่านข้อกำหนดรูปแบบ](skills/artifact-template-thai-report-format/references/format-spec.md)


ดาวน์โหลด repository แล้วคัดลอกโฟลเดอร์ `skills/artifact-template-thai-report-format` ไปไว้ใน `~/.codex/skills/` หรือโฟลเดอร์ `skills` ภายใต้ CODEX_HOME ที่กำหนดเอง

Windows โดยทั่วไปคือ `C:\Users\<ชื่อผู้ใช้>\.codex\skills\artifact-template-thai-report-format` หากมี skill ชื่อเดียวกันอยู่แล้ว ให้สำรองฉบับเดิมก่อนแทนที่

เมื่อ Codex โหลดรายการ skill ใหม่ เรียกใช้:

```text
$artifact-template-thai-report-format สร้างรายงานเรื่อง ... โดยใช้เนื้อหาต่อไปนี้ ...
```

สามารถให้ Codex ใช้ skill-installer ติดตั้งจาก URL ของโฟลเดอร์ skill ใน repository นี้ได้เช่นกัน

## ข้อกำหนด

ใช้ Codex ที่รองรับ skills และเครื่องมือสร้างเอกสาร พร้อมฟอนต์ TH Sarabun New การใช้สคริปต์ต้องมี Python และ lxml ควรอัปเดตฟิลด์และตรวจการจัดหน้าใน Microsoft Word ก่อนส่งรายงาน

ตัวอย่างคงเลขภาพและตารางเป็น xx เมื่อสร้างรายงานจริงให้ปลดล็อกฟิลด์ SEQ หรือใช้ `new_report.py --number-captions` แล้วอัปเดตสารบัญใน Word

## ค่าเริ่มต้นสารบัญและการอัปเดต

Table of Contents ใช้ Formats: From template และ Show Levels: 3 โดย TOC1 มี Before text 0 นิ้ว / Hanging 0.6 นิ้ว, TOC2 มี Before text 0.6 นิ้ว / Hanging 0.4 นิ้ว และ TOC3 มี Before text 1 นิ้ว / Hanging 0.5 นิ้ว ทุกระดับมี After text 0 นิ้ว, Spacing Before 0 pt / After 6 pt และ Line spacing Single

ตัวสร้าง `new_report.py` ใช้ค่าเหล่านี้กับสำเนารายงานโดยอัตโนมัติ ค่าแม่แบบด้านอื่นยังคงเดิม ส่วนไฟล์ Word อ้างอิงที่ดาวน์โหลดโดยตรงยังเป็นตัวอย่างเดิม หากต้องการปรับสารบัญของเอกสารที่มีอยู่ ใช้ `scripts/apply_toc_format.py --input input.docx --output output.docx` แล้วอัปเดตสารบัญใน Word

ผู้ที่ติดตั้งไว้แล้วให้ดาวน์โหลดเวอร์ชันล่าสุด สำรอง skill เดิมหากมีการปรับแต่ง แล้วแทนที่โฟลเดอร์ `artifact-template-thai-report-format` ทั้งโฟลเดอร์ในตำแหน่งติดตั้ง ไม่ต้องถอนการติดตั้งก่อน สำเนาที่ติดตั้งไว้ไม่ได้อัปเดตตาม GitHub อัตโนมัติ

## ค่าเริ่มต้นการจัดข้อความและตาราง

ทุกย่อหน้ารวมสารบัญใช้ Spacing After 6 pt หัวตารางทุกเซลล์เป็นตัวหนาและกึ่งกลางแนวนอน ทุกเซลล์จัดข้อความชิดบน (Vertical alignment: Top) เนื้อหาและเซลล์ข้อมูลใช้ Align Left ไม่ใช้ Distributed หรือ Thai Distributed ตั้ง Character Spacing เป็น Normal, Scale 100%, Spacing 0 pt และ Position Normal หัวข้อและคำบรรยายภาพคงการจัดแนวตามแม่แบบ

ตารางเปิด Wrap text ปิด Fit text และให้แถวขยายตามเนื้อหา ใช้การตัดคำไทยและอังกฤษตามขอบเขตคำ ไม่แทรกช่องว่างหรือ Shift+Enter เพื่อจัดแนว หากคำไม่พอดีให้ปรับความกว้างคอลัมน์ภายในขอบกระดาษ ตั้ง Do not check spelling or grammar เฉพาะเอกสาร และตรวจภาพเรนเดอร์ว่าช่องไฟปกติ ไม่มีคำแตกกลางคำ ข้อความไม่ล้นหรือถูกตัดก่อนส่ง

`new_report.py` ใช้ค่าเหล่านี้กับสำเนาโดยอัตโนมัติ สำหรับเอกสารที่มีอยู่หรือหลังใส่เนื้อหาและอัปเดตฟิลด์ ใช้ `scripts/apply_text_layout.py --input input.docx --output final.docx` แล้วตรวจภาพเรนเดอร์ สคริปต์ไม่แก้ข้อความหรือปรับความกว้างคอลัมน์แทนการตรวจหน้า อ่านรายละเอียดใน [ข้อกำหนดการจัดข้อความ](skills/artifact-template-thai-report-format/references/text-layout.md)

ข้อกำหนดการตัดคำไทยเพิ่มเติม: ให้ข้อความไหลต่อเนื่องจนใกล้ขอบขวาหรือขอบเซลล์ ตัดระหว่างคำอย่างเหมาะสม ไม่ย้ายวลีทั้งช่วงเมื่อยังมีพื้นที่ ห้ามแทรก Enter หรือ Shift+Enter เพื่อบังคับตัดบรรทัด คงช่องไฟปกติและ Scale 100% และตรวจผลใน Microsoft Word หลังจัดหน้า โดยรักษาการแบ่งย่อหน้าที่มีความหมาย

ฟอนต์รายการสารบัญ TOC1–3: Latin และ Complex scripts ใช้ TH Sarabun New, Regular, 16 pt สี Automatic (ไม่กำหนดสีเฉพาะ) ไม่มีเส้นใต้หรือสีเส้นใต้ และปิด Effects ทั้งหมด ใช้กับสไตล์และข้อความสารบัญที่มีอยู่ หลังอัปเดตสารบัญให้ใช้ `apply_toc_format.py` อีกครั้งและตรวจผลใน Word
