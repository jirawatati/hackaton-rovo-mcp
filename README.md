# hackaton-rovo-mcp

ใช้ Atlassian Rovo MCP + GitHub Copilot สร้าง documentation อัตโนมัติบน Confluence Wiki

---

## 🚀 Quick Start

1. ติดตั้ง [Node.js v18+](https://nodejs.org) และ [VS Code](https://code.visualstudio.com/)
2. ติดตั้ง extension: **GitHub Copilot**
3. เปิดโปรเจกต์นี้ใน VS Code — MCP Server จะ connect อัตโนมัติจาก `.vscode/mcp.json`
4. เปิด Copilot Chat แล้วใช้คำสั่งด้านล่าง

---

## 📋 Prompt Commands

| Command | File | คำอธิบาย |
|---------|------|----------|
| `/overview` | `generate-project-overview.prompt.md` | สร้างหน้า Project Overview บน Confluence |
| `/architecture` | `generate-tech-architecture.prompt.md` | สร้างหน้า Technical Architecture & Configuration |
| `/howto` | `generate-howto-guide.prompt.md` | สร้าง How-to Guide สำหรับทีม |
| `/codedocs` | `generate-code-docs.prompt.md` | Auto-generate documentation จาก source code |
| `/decisions` | `generate-decision-log.prompt.md` | สร้าง Decision Log template พร้อมตัวอย่าง |
| `/demo` | `generate-demo-script.prompt.md` | สร้าง Demo Script สำหรับ Hackathon Presentation |
| `/sync` | `update-docs-from-code.prompt.md` | อัพเดท documentation ให้ตรงกับ code ปัจจุบัน |
| `/sprint` | `generate-sprint-summary.prompt.md` | ดึง Jira issues มาสรุปเป็น Weekly Sprint Summary |

### วิธีใช้

1. เปิด **Copilot Chat** (`Ctrl+Shift+I`)
2. พิมพ์ `/` แล้วเลือก prompt ที่ต้องการ หรือพิมพ์ชื่อ command โดยตรง
3. Agent จะอ่านโปรเจกต์ → สร้าง/อัพเดทหน้า Confluence อัตโนมัติ

---

## 📁 Project Structure

```
.
├── .github/
│   ├── instructions/
│   │   ├── rovo.instructions.md              # วิธีติดตั้ง MCP Server
│   │   └── rovo-personal-space.instructions.md  # Scope personal space
│   └── prompts/
│       ├── generate-project-overview.prompt.md   # /overview
│       ├── generate-tech-architecture.prompt.md  # /architecture
│       ├── generate-howto-guide.prompt.md        # /howto
│       ├── generate-code-docs.prompt.md          # /codedocs
│       ├── generate-decision-log.prompt.md       # /decisions
│       ├── generate-demo-script.prompt.md        # /demo
│       ├── update-docs-from-code.prompt.md       # /sync
│       └── generate-sprint-summary.prompt.md     # /sprint
├── .vscode/
│   └── mcp.json
└── README.md
```

---

## ⚙️ Configuration

### MCP Server (`.vscode/mcp.json`)

```json
{
  "servers": {
    "atlassian-mcp-server": {
      "url": "https://mcp.atlassian.com/v1/mcp",
      "type": "http"
    }
  }
}
```

### Target Confluence Space

| Property | Value |
|----------|-------|
| **Site** | `ntldigital.atlassian.net` |
| **Cloud ID** | `4556ed1b-6dee-47c7-8973-1f7b872300b6` |
| **Space Key** | `~712020dbde0c9560d0470a8ae25673a252dcde` |
| **Type** | Personal Space (sandbox) |

---

## 📝 Rules

- ทุกหน้าที่สร้างบน Confluence ใช้ **Markdown format** เท่านั้น (`contentFormat: "markdown"`)
- Agent ทำงานเฉพาะใน **personal space** เท่านั้น — ห้ามแก้ไข space อื่น
- ห้ามแก้ไข Jira issues ยกเว้นผู้ใช้สั่งโดยตรง