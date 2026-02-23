---
description: "/codedocs" — Generate documentation จาก source code อัตโนมัติแล้วสร้างบน Confluence
agent: Scan source code ทั้งหมดในโปรเจกต์ วิเคราะห์โครงสร้าง config และไฟล์สำคัญ แล้วสร้าง Auto-Generated Code Documentation บน Confluence
tools:
  - mcp_atlassian-mcp_createConfluencePage
  - mcp_atlassian-mcp_searchConfluenceUsingCql
---

# `/codedocs` — Auto-Generate Code Documentation

อ่าน source code **ทั้งหมด**ในโปรเจกต์นี้ แล้วสร้างหน้า Confluence ใน **personal space** (space key: `~712020dbde0c9560d0470a8ae25673a252dcde`) ชื่อ **"Auto-Generated Code Documentation"**

> **⚠️ Mandatory:** เมื่อสร้างหรืออัพเดทหน้า Confluence ต้องใช้ `contentFormat: "markdown"` เสมอ และเขียน body เป็น **Markdown** เท่านั้น ห้ามใช้ HTML หรือ Confluence storage format (XHTML)

## ขั้นตอน

1. **Scan โปรเจกต์** — อ่านโครงสร้างไฟล์ทั้งหมด
2. **วิเคราะห์ไฟล์สำคัญ** — อ่านเนื้อหาของแต่ละไฟล์
3. **สร้าง documentation** — เขียน doc ครอบคลุมทุกส่วน
4. **Publish ลง Confluence** — สร้างหน้าใน personal space

## เนื้อหาที่ต้องมี

### 1. Project Structure
- แสดง folder tree ของทั้งโปรเจกต์
- อธิบายวัตถุประสงค์ของแต่ละ directory

### 2. Configuration Files
แต่ละไฟล์ config ให้อธิบาย:
- ชื่อไฟล์และ path
- วัตถุประสงค์
- ค่าสำคัญและความหมาย
- ตัวอย่าง snippet

### 3. Instruction Files
สรุป `.github/instructions/*.md` แต่ละไฟล์:
- ชื่อและ description
- Rules/constraints สำคัญ
- ตัวอย่างการใช้งาน

### 4. Prompt Files
สรุป `.github/prompts/*.prompt.md` แต่ละไฟล์:
- ชื่อและ description
- เมื่อไหร่ควรใช้
- Tools ที่เกี่ยวข้อง

### 5. Dependencies & Requirements
- Node.js version
- VS Code extensions ที่จำเป็น
- External services (Atlassian Cloud, MCP Server)

## Format

- **ใช้ Markdown เท่านั้น** — tables, code blocks (` ```lang `), headings (`#`)
- ต้องส่ง `contentFormat: "markdown"` ทุกครั้งที่เรียก `createConfluencePage` หรือ `updateConfluencePage`
- ใช้ tables สำหรับ file listings
- ใส่ code blocks พร้อม syntax highlighting (` ```sql `, ` ```json `, etc.)
- เขียนเป็นภาษาไทยปนอังกฤษ
- ใส่ timestamp ที่ generated: วันที่ปัจจุบัน
