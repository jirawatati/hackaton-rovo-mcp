---
description: สร้างหน้า Project Overview บน Confluence personal space
agent: อ่านไฟล์ทั้งหมดในโปรเจกต์ แล้วสร้างหน้า Project Overview บน Confluence personal space พร้อมเนื้อหาเกี่ยวกับวัตถุประสงค์ สถาปัตยกรรม และวิธี setup
tools:
  - mcp_atlassian-mcp_createConfluencePage
  - mcp_atlassian-mcp_getConfluenceSpaces
  - mcp_atlassian-mcp_searchConfluenceUsingCql
---

# Generate Project Overview on Confluence

อ่านไฟล์ทั้งหมดในโปรเจกต์นี้ แล้วสร้างหน้า Confluence ใน **personal space** (space key: `~712020dbde0c9560d0470a8ae25673a252dcde`) ชื่อ **"Hackathon Rovo MCP — Project Overview"**

## เนื้อหาที่ต้องมี

1. **วัตถุประสงค์ของโปรเจกต์** — อธิบายว่าโปรเจกต์นี้ใช้ Atlassian Rovo MCP เพื่อสร้าง documentation อัตโนมัติบน Confluence
2. **สถาปัตยกรรมระบบ** — วาดภาพรวมของ VS Code + GitHub Copilot + Rovo MCP Server + Confluence Cloud (ใช้ table หรือ diagram)
3. **Tech Stack** — รายการเทคโนโลยีที่ใช้ (Node.js, MCP Protocol, OAuth 2.1, Confluence REST API)
4. **วิธีการติดตั้งและ Setup** — สรุปขั้นตอนจาก instructions ในโปรเจกต์
5. **ข้อจำกัดและ Scope** — อธิบายว่า POC นี้ scope อยู่แค่ personal space เท่านั้น

## Format

- ใช้ Confluence-friendly formatting: headings (h1-h3), tables, bullet lists, code blocks
- เขียนเป็นภาษาไทยปนอังกฤษ (technical terms เป็นภาษาอังกฤษ)
- ใส่ status macro: 🟢 Active
