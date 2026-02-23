---
description: "/demo" — สร้าง Demo Script สำหรับ Hackathon Presentation บน Confluence
agent: สร้าง Demo Script บน Confluence สำหรับ Hackathon Presentation ครอบคลุมบทนำ setup live demo สรุปผล และ next steps
tools:
  - mcp_atlassian-mcp_createConfluencePage
  - mcp_atlassian-mcp_searchConfluenceUsingCql
---

# `/demo` — Generate Hackathon Demo Script

สร้างหน้า Confluence ใน **personal space** (space key: `~712020dbde0c9560d0470a8ae25673a252dcde`) ชื่อ **"Hackathon Demo Script"**

> **⚠️ Mandatory:** เมื่อสร้างหรืออัพเดทหน้า Confluence ต้องใช้ `contentFormat: "markdown"` เสมอ และเขียน body เป็น **Markdown** เท่านั้น ห้ามใช้ HTML หรือ Confluence storage format (XHTML)

## โครงสร้าง Demo

### 🎯 Part 1: บทนำ (2 นาที)
- **ปัญหา**: การเขียน documentation เป็นงานที่ใช้เวลานาน, ข้อมูลใน doc มักไม่ตรงกับ code
- **สถิติ**: Developer ใช้เวลา ~20% ไปกับการเขียนและอัพเดท doc
- **Solution**: ใช้ AI + Rovo MCP สร้าง doc อัตโนมัติจาก code → Confluence

### 🔧 Part 2: แสดง Setup (1 นาที)
- โชว์ `.vscode/mcp.json` configuration
- โชว์ `.github/instructions/` — rules ที่ควบคุม AI
- โชว์ `.github/prompts/` — reusable prompts

### 🚀 Part 3: Live Demo (5 นาที)
**Demo 1**: สร้าง Project Overview อัตโนมัติ
- ใช้ prompt `generate-project-overview`
- แสดงผลลัพธ์บน Confluence

**Demo 2**: Auto-generate Code Documentation
- ใช้ prompt `generate-code-docs`
- AI อ่าน source code → สร้าง doc → publish ลง Confluence

**Demo 3**: สร้าง Decision Log
- ใช้ prompt `generate-decision-log`
- โชว์ว่า template + ข้อมูลถูกสร้างอัตโนมัติ

### 📊 Part 4: สรุปผลลัพธ์ (2 นาที)
- เปรียบเทียบ: เขียน doc manual vs. AI-generated
- เวลาที่ประหยัด: จาก ~2 ชั่วโมง → 5 นาที
- คุณภาพ: consistent format, ไม่มี typo, อัพเดทง่าย

### 💡 Part 5: Next Steps (1 นาที)
- Scale จาก personal space → team space
- เพิ่ม CI/CD pipeline สำหรับ auto-update docs เมื่อ code เปลี่ยน
- Integrate กับ Jira สำหรับ sprint documentation

## สิ่งที่ต้องเตรียม

- [ ] Confluence personal space ว่างเปล่า (ลบ test pages)
- [ ] VS Code เปิดโปรเจกต์นี้
- [ ] MCP Server connected และ authenticated
- [ ] Internet connection stable

## Backup Plan

ถ้า live demo มีปัญหา ให้เตรียม screenshots ของผลลัพธ์ไว้ล่วงหน้า

## Format

- **ใช้ Markdown เท่านั้น** — headings, bullet lists, checkboxes (`- [ ]`), bold
- ต้องส่ง `contentFormat: "markdown"` ทุกครั้งที่เรียก `createConfluencePage` หรือ `updateConfluencePage`
- เขียนภาษาไทยปนอังกฤษ
