---
description: สร้าง How-to Guide สำหรับทีมบน Confluence
agent: สร้าง step-by-step How-to Guide บน Confluence สำหรับทีม ครอบคลุมการติดตั้ง MCP Server, authentication และตัวอย่าง prompt
tools:
  - mcp_atlassian-mcp_createConfluencePage
  - mcp_atlassian-mcp_searchConfluenceUsingCql
---

# Generate How-to Guide

สร้างหน้า Confluence ใน **personal space** (space key: `~712020dbde0c9560d0470a8ae25673a252dcde`) ชื่อ **"How to Use Rovo MCP with VS Code"** เป็น step-by-step guide สำหรับทีม

## เนื้อหาที่ต้องมี

### Step 1: Prerequisites
- Node.js v18+ (วิธีตรวจสอบ: `node --version`)
- npx (`npx --version`)
- VS Code + GitHub Copilot extension
- Atlassian Cloud account ที่มีสิทธิ์เข้าถึง Confluence

### Step 2: ติดตั้ง MCP Server
อธิบาย 3 วิธี:
1. **VS Code MCP Directory** (แนะนำ) — ผ่าน https://code.visualstudio.com/mcp
2. **Command Palette** — `MCP: Add Server` → HTTP → `https://mcp.atlassian.com/v1/mcp`
3. **Manual mcp.json** — สร้างไฟล์ `.vscode/mcp.json`

### Step 3: Authentication
- อธิบาย OAuth 2.1 flow
- วิธีแก้ปัญหาถ้า auth ไม่ผ่าน

### Step 4: ทดสอบการเชื่อมต่อ
ใส่ตัวอย่าง prompt ที่ใช้งานได้:
- "แสดงหน้าทั้งหมดใน personal space ของฉัน"
- "สร้างหน้าทดสอบ ชื่อ 'Test Page' ใน personal space"
- "ค้นหาหน้าที่มีคำว่า 'test' ใน personal space"

### Step 5: ตัวอย่าง Use Cases
- สร้าง doc จาก code อัตโนมัติ
- สรุป Jira issues เป็น Confluence page
- อัพเดท doc เมื่อ code เปลี่ยน

### ข้อควรระวังและ Best Practices
- ตรวจสอบ space key ก่อนสร้าง/แก้ไขหน้า
- ใช้ CQL filter เสมอเมื่อ search
- ทดสอบใน personal space ก่อน production

## Format

- เขียนเป็น numbered steps ชัดเจน
- ใส่ screenshots placeholders (ถ้าเป็นไปได้)
- ใส่ info/warning boxes สำหรับข้อควรระวัง
- เขียนเป็นภาษาไทย ใช้ technical terms ภาษาอังกฤษ
