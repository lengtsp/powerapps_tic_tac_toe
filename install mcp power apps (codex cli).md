
# ติดตั้ง Power Apps (Canvas Apps) MCP Plugin บน Codex CLI
 
สรุปขั้นตอนติดตั้งและตรวจสอบ `canvas-apps` plugin สำหรับเชื่อมต่อ Power Apps Canvas App ผ่าน Codex CLI
 
## 1. ตรวจ Prerequisite
 
```bash
dotnet --version
dotnet --list-sdks
command -v dnx
codex --version
```
 
ตัวอย่างค่าที่ต้องพบ:
 
```text
.NET SDK: 10.0.301
dnx:      /home/indows-11/.dotnet/dnx
```
 
## 2. ถอน Plugin เดิมและติดตั้งใหม่
 
```bash
# ถอน plugin เดิม (ถ้ามี)
codex plugin remove canvas-apps@power-platform-skills --json
 
# เพิ่ม Microsoft Power Platform marketplace
codex plugin marketplace add microsoft/power-platform-skills --json
 
# ติดตั้ง Canvas Apps plugin
codex plugin add canvas-apps@power-platform-skills --json
 
# ตรวจสอบผลการติดตั้ง
codex plugin list
```
 
ผลลัพธ์ที่ต้องการ:
 
```text
canvas-apps@power-platform-skills
status:  installed, enabled
version: 2.1.1
```
 
## 3. ตรวจ MCP Registration
 
```bash
codex mcp get canvas-authoring
codex mcp list
```
 
หากพบ registration เก่าที่ชี้ไปยัง wrapper หรือ workspace เดิม ให้ลบออกก่อน:
 
```bash
codex mcp remove canvas-authoring
```
 
หลังติดตั้ง plugin สำเร็จ MCP ที่ใช้งานจริงคือ:
 
```text
Name:    canvas-authoring
Command: dnx
Args:    Microsoft.PowerApps.CanvasAuthoring.McpServer
         --yes
         --prerelease
         --source
         https://api.nuget.org/v3/index.json
```
 
---
 
✅ เมื่อครบทั้ง 3 ขั้นตอนนี้ ถือว่า plugin และ MCP server สำหรับ Canvas Apps พร้อมใช้งานบน Codex CLI
