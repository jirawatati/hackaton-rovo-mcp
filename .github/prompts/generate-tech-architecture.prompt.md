---
description: สร้างหน้า Technical Architecture & Configuration บน Confluence
agent: อ่าน config และ instruction files แล้วสร้างหน้า Technical Architecture & Configuration บน Confluence อธิบาย MCP Server, Auth flow, Space scope และ CQL filters
tools:
  - mcp_atlassian-mcp_createConfluencePage
  - mcp_atlassian-mcp_searchConfluenceUsingCql
---

# Generate Technical Architecture Doc

อ่านไฟล์ `.vscode/mcp.json` และ `.github/instructions/` ทั้งหมดในโปรเจกต์นี้ แล้วสร้างหน้า Confluence ใน **personal space** (space key: `~712020dbde0c9560d0470a8ae25673a252dcde`) ชื่อ **"Technical Architecture & Configuration"**

## เนื้อหาที่ต้องมี

### 1. MCP Server Configuration
- อธิบาย `mcp.json` แต่ละ field
- Server URL และ protocol ที่ใช้ (HTTP-based MCP)

### 2. Authentication Flow
- อธิบาย OAuth 2.1 flow ตั้งแต่ต้นจนจบ
- วิธีสร้าง API token (ถ้าใช้แทน OAuth)
- Link ไปหน้า manage tokens

### 3. Confluence Space Scope & Constraints
- Cloud ID: `4556ed1b-6dee-47c7-8973-1f7b872300b6`
- Space Key: `~712020dbde0c9560d0470a8ae25673a252dcde`
- อธิบายว่าทำไมต้อง scope แค่ personal space

### 4. Allowed Operations
- สร้างตาราง operations ที่อนุญาต (Read, Create, Update, Search, Comment)
- ระบุ tool ที่ใช้และ constraint ของแต่ละ operation

### 5. CQL Filters
- ตัวอย่าง CQL queries ที่ใช้ค้นหาภายใน personal space
- Best practices สำหรับ CQL

## Format

- ใช้ tables สำหรับข้อมูลที่เป็นโครงสร้าง
- ใส่ code blocks สำหรับ config และ CQL
- เขียนเป็นภาษาไทยปนอังกฤษ
