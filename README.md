# CCD2 — Binance TH Content Checker (Claude.ai Distribution)

> System C2 ของ Binance TH AI Content Platform
> ตรวจ กลต. compliance + typo ผ่าน Claude.ai chat (รองรับ free tier)

---

## 🔗 ใช้งานทันที

**Loader page:** https://charlottehortonx-tech.github.io/CCD2

```
1. กด 📋 Copy Prompt
2. เปิด claude.ai → New Chat → Paste → ส่ง
3. วาง content / แนบ PDF / DOCX
4. ตรวจต่อใน chat เดียวกันได้ไม่จำกัด
```

> 1 chat = ตรวจได้หลายชิ้น | เปิด chat ใหม่ค่อย paste prompt อีกรอบ

---

## 📂 โครงสร้าง

```
CCD2/
├── check-content-prompt.md  ← prompt ฝัง กลต. rules + typo rules
├── docs/
│   └── index.html           ← loader page (GitHub Pages)
└── README.md
```

---

## 🔍 ตรวจอะไรบ้าง

**กลต. Compliance** (อ้างอิงประกาศ นป. 2/2568):
- ❌ FAIL: "รับประกัน" / % ผลตอบแทนไม่มีคำเตือน / แนะนำซื้อ-ขาย coin / ข้อความเร่งรัด
- ⚠️ WARNING: ข้อมูลบวกไม่มีคำเตือนความเสี่ยง / ขาด disclaimer

**Typo (11 หมวด):** brand names, ศัพท์ regulatory, คำทับศัพท์, คำไทย crypto, สระ ใ/ไ, keyboard typos, วรรณยุกต์, number format, spacing, วงเล็บ, consistency

---

## 🔄 เมื่อกฎ กลต. อัปเดต

แก้ `check-content-prompt.md` → push → ทีมเปิด chat ใหม่ + paste = ใช้กฎใหม่ทันที (single source of truth)

---

## ระบบที่เกี่ยวข้อง

- **CCD1** — Google Apps Script in-Doc checker (สำหรับตรวจในเอกสาร)
- **System A** (private) — News pipeline auto-generate content
- **System B** (private) — Drive cron compliance check (final gate)
