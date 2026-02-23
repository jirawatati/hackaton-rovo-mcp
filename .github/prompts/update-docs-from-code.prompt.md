---
description: อัพเดท documentation บน Confluence ให้ตรงกับ code ปัจจุบัน
agent: ค้นหาหน้า Auto-Generated Code Documentation บน Confluence อ่าน source code ปัจจุบัน แล้วอัพเดทเนื้อหาให้ตรงกับ code ล่าสุด
tools:
  - mcp_atlassian-mcp_searchConfluenceUsingCql
  - mcp_atlassian-mcp_getConfluencePage
  - mcp_atlassian-mcp_updateConfluencePage
---

# Update Documentation from Code Changes

อ่าน source code ทั้งหมดในโปรเจกต์นี้ แล้วอัพเดทหน้า **"Auto-Generated Code Documentation"** ใน **personal space** (space key: `~712020dbde0c9560d0470a8ae25673a252dcde`) ให้ตรงกับ code ปัจจุบัน

## ขั้นตอน

1. **ค้นหาหน้าที่มีอยู่** — ใช้ CQL: `space.key = "~712020dbde0c9560d0470a8ae25673a252dcde" AND title = "Auto-Generated Code Documentation"`
2. **อ่าน code ปัจจุบัน** — Scan ไฟล์ทั้งหมดในโปรเจกต์
3. **เปรียบเทียบ** — ดูว่ามีอะไรเปลี่ยนแปลง (ไฟล์ใหม่, ไฟล์ที่ลบ, ไฟล์ที่แก้ไข)
4. **อัพเดท Confluence page** — แก้ไขเนื้อหาให้ตรงกับ code ล่าสุด

## สิ่งที่ต้องอัพเดท

- Project structure (ถ้ามีไฟล์/โฟลเดอร์ใหม่)
- Configuration files (ถ้ามีการเปลี่ยนแปลง)
- Instruction files (ถ้ามีการเพิ่ม/แก้ไข)
- Prompt files (ถ้ามีการเพิ่ม/แก้ไข)
- Dependencies

## Format

- ใส่ "Last updated: {วันที่ปัจจุบัน}" ที่ด้านบนของหน้า
- ใส่ changelog section สั้นๆ ว่าอัพเดทอะไรบ้าง
- คงรูปแบบเดิมของ doc ไว้
