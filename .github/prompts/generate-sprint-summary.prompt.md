---
description: ดึง Jira issues แล้วสร้างสรุป Sprint บน Confluence
agent: ค้นหา Jira issues ที่ assign ให้ฉันในสัปดาห์นี้ จัดกลุ่มตาม status แล้วสร้าง Weekly Sprint Summary บน Confluence
tools:
  - mcp_atlassian-mcp_searchJiraIssuesUsingJql
  - mcp_atlassian-mcp_getJiraIssue
  - mcp_atlassian-mcp_createConfluencePage
  - mcp_atlassian-mcp_searchConfluenceUsingCql
---

# Generate Sprint Summary from Jira

ค้นหา Jira issues ที่ assign ให้ฉัน แล้วสร้างหน้า Confluence ใน **personal space** (space key: `~712020dbde0c9560d0470a8ae25673a252dcde`) ชื่อ **"Weekly Sprint Summary — {สัปดาห์ปัจจุบัน}"**

## ขั้นตอน

1. **ค้นหา Jira issues** — ใช้ JQL: `assignee = currentUser() AND updated >= -7d ORDER BY status ASC, priority DESC`
2. **อ่านรายละเอียด** — ดึงข้อมูลแต่ละ issue (summary, status, priority, description)
3. **จัดกลุ่ม** — แยกตาม status: To Do, In Progress, Done
4. **สร้าง Confluence page** — สรุปเป็น sprint report

## เนื้อหาที่ต้องมี

### Summary
- จำนวน issues ทั้งหมด
- แยกตาม status (Done / In Progress / To Do)
- % completion

### Issues by Status

#### ✅ Done
ตารางแสดง issues ที่เสร็จแล้ว: Key, Summary, Priority, Resolved Date

#### 🔄 In Progress
ตารางแสดง issues ที่กำลังทำ: Key, Summary, Priority, Days in Progress

#### 📋 To Do
ตารางแสดง issues ที่ยังไม่เริ่ม: Key, Summary, Priority, Created Date

### Blockers & Risks
- สรุปปัญหาหรือ blockers (ถ้ามี)

### Next Week Plan
- Issues ที่จะทำสัปดาห์หน้า

## Format

- ใช้ tables เป็นหลัก
- ใส่ progress bar หรือ percentage
- Link กลับไปหา Jira issue แต่ละตัว
- เขียนภาษาไทย
