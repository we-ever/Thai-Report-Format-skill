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
