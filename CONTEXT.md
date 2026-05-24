# CCD2 — Context for Claude Code

## ภาพรวม

CCD2 = **System C2** ของ Binance TH AI Content Platform
ทำหน้าที่ distribute compliance + typo checker prompt ให้ทีม content ใช้บน Claude.ai (free tier)

---

## วิธีทำงาน

```
ทีม content → loader page → copy prompt → paste ใน Claude.ai
                                              ↓
                                  drop content / file → ผลตรวจ
```

**Constraint:** Claude.ai free tier — ไม่มี Projects, ไม่มี URL fetch
→ ใช้กลยุทธ์ embed full prompt + 1-click clipboard copy ผ่าน loader page

---

## ไฟล์หลัก

| ไฟล์ | หน้าที่ |
|---|---|
| `check-content-prompt.md` | Single source of truth — prompt + กลต. rules + typo rules + output format |
| `docs/index.html` | Loader page (GitHub Pages) — fetch raw .md + copy to clipboard |
| `README.md` | User-facing docs |

---

## URL / Endpoint

- **Repo:** https://github.com/charlottehortonx-tech/CCD2
- **Loader (live):** https://charlottehortonx-tech.github.io/CCD2 *(ต้อง enable GitHub Pages: Settings → Pages → Source: main / docs)*
- **Raw prompt:** https://raw.githubusercontent.com/charlottehortonx-tech/CCD2/main/check-content-prompt.md

---

## วิธีอัปเดตกฎ

1. แก้ `check-content-prompt.md` (เนื้อใน code fence ```` ... ````)
2. Commit + push main
3. Loader page sync อัตโนมัติ (fetch raw URL ตอน user กด copy)
4. แจ้งทีม: เปิด chat ใหม่ + paste = ใช้กฎใหม่ทันที

---

## ความสัมพันธ์กับระบบอื่น

```
System A (news)        CCD2 / CCD1 (draft check)       System B (final)
auto-generate     →    self-serve checker        →    Drive cron + report
                       (Claude.ai / Google Doc)        (audit trail ก่อน publish)
```

- **CCD2** = ตรวจใน Claude.ai chat (ไฟล์/text)
- **CCD1** = ตรวจในเอกสาร Google Doc โดยตรง (Apps Script)
- ทั้งสองใช้ rules จาก `docs/sec-compliance-rules.md` ของ thnew/ เป็นต้นทาง

---

## ไฟล์อ้างอิงต้นทาง (อยู่ใน Next.js project ที่ thnew/)

- `docs/sec-compliance-rules.md` — ประกาศ กลต. นป. 2/2568 (ground truth)
- `lib/ai/compliance-file.ts` — compliance check logic (System B)
- `lib/ai/typo-check.ts` — typo check logic (System B)
- `SYSTEM_OVERVIEW.md` — architecture เต็มของ 3 systems
