---
description: Scope Atlassian Rovo MCP to personal Confluence space for testing
---

# Atlassian Rovo MCP — Personal Space Testing

This instruction scopes the Atlassian MCP integration to **only** the personal Confluence space for safe testing.

---

## Target Space

| Property | Value |
|----------|-------|
| **Site** | `ntldigital.atlassian.net` |
| **Cloud ID** | `4556ed1b-6dee-47c7-8973-1f7b872300b6` |
| **Space Key** | `~712020dbde0c9560d0470a8ae25673a252dcde` |
| **Space URL** | https://ntldigital.atlassian.net/wiki/spaces/~712020dbde0c9560d0470a8ae25673a252dcde/overview |
| **Purpose** | Personal sandbox for hackathon testing |

---

## Rules for AI Agent

1. **Always use this Cloud ID**: `4556ed1b-6dee-47c7-8973-1f7b872300b6`
2. **Only operate on this space key**: `~712020dbde0c9560d0470a8ae25673a252dcde`
3. **Do NOT** read, write, or search pages in any other Confluence space.
4. **Do NOT** modify any Jira issues unless explicitly requested by the user.
5. When creating or editing Confluence pages, always set `spaceId` to the personal space.
6. **Always use Markdown format** when creating or updating pages — set `contentFormat` to `"markdown"` and write the body in standard Markdown (headings, tables, code blocks, etc.). **Never** use Confluence storage format (XHTML) or raw HTML.

---

## Allowed Operations

| Operation | Tool | Constraint |
|-----------|------|------------|
| Read pages | `getConfluencePage` | Only pages in personal space |
| List child pages | `getConfluencePageDescendants` | Only under personal space homepage |
| Create pages | `createConfluencePage` | Must target personal space |
| Update pages | `updateConfluencePage` | Only pages in personal space |
| Search | `searchConfluenceUsingCql` | Filter with `space.key = "~712020dbde0c9560d0470a8ae25673a252dcde"` |
| Comments | `createConfluenceFooterComment`, `createConfluenceInlineComment` | Only on pages in personal space |

---

## Page Structure

| Page | ID | Parent |
|------|----|--------|
| Database Schema Documentation Hub | `1584824361` | Overview (homepage) |
| Schema Overview — Insurance OLTP (ins_oltp) | `1584726099` | Hub |
| Table — customers | (child of Schema Overview) | Schema Overview |
| Table — policies | (child of Schema Overview) | Schema Overview |
| Table — claims | (child of Schema Overview) | Schema Overview |
| AI Prompt Templates — Database Repository | `1584824380` | Hub |

---

## Quick Test Commands

Use these prompts to verify the setup:

1. **List pages in personal space**:
   > "แสดงหน้าทั้งหมดใน personal space ของฉัน"

2. **Read schema documentation**:
   > "อ่านหน้า Schema Overview — Insurance OLTP จาก personal space ของฉัน"

3. **Generate code from schema**:
   > "อ่าน Table — customers จาก Confluence แล้วสร้าง Prisma schema model"

4. **Search in personal space only**:
   > "ค้นหาหน้าที่มีคำว่า 'customers' ใน personal space ของฉัน"

---

## Example CQL Filters

When searching Confluence, always include the space filter:

```
space.key = "~712020dbde0c9560d0470a8ae25673a252dcde" AND type = "page"
```

```
space.key = "~712020dbde0c9560d0470a8ae25673a252dcde" AND title ~ "Table"
```
