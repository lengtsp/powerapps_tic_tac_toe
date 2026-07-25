# คู่มือการติดตั้งและตั้งค่า Power Platform Canvas Apps Plugin บน Claude Code

เอกสารนี้รวบรวมขั้นตอนการตรวจสอบความพร้อม การติดตั้ง plugin และการเชื่อมต่อ Power Apps Studio เข้ากับ Claude Code

---

## 📋 ขั้นตอนที่ 0: ตรวจสอบ Prerequisite ก่อนติดตั้ง

ตรวจสอบเวอร์ชันของ .NET SDK และ MCP Server runner ในระบบ Terminal:

```bash
dotnet --version
# → 10.0.301  ✅ ผ่านเกณฑ์ .NET SDK 10+

dotnet --list-sdks
# → 10.0.301 [/home/indows-11/.dotnet/sdk]

command -v dnx
# → /home/indows-11/.dotnet/dnx  ✅ มีตัวรัน MCP server (มากับ .NET SDK 10)
```

---

## 🗑️ ขั้นตอนที่ 1: ถอน Plugin เดิมออกก่อน

หากเคยติดตั้ง plugin ไว้ ให้ถอนการติดตั้งเวอร์ชันเดิมออกก่อน:

```bash
claude plugin uninstall canvas-apps@power-platform-skills
# → ✔ Successfully uninstalled plugin: canvas-apps (scope: user)

claude plugin list
# → ยืนยันว่า canvas-apps หายไปจากรายการแล้ว
```

---

## 🛒 ขั้นตอนที่ 2: เพิ่ม Marketplace

เพิ่ม Marketplace `microsoft/power-platform-skills` เข้าสู่ระบบ:

```bash
claude plugin marketplace add microsoft/power-platform-skills
# → ✔ Marketplace 'power-platform-skills' already on disk — declared in user settings
```

> **Note (Interactive Mode):** หากใช้งานผ่านหน้าต่าง Claude Code แบบ Interactive สามารถใช้คำสั่ง:
> `/plugin marketplace add microsoft/power-platform-skills`

---

## 📦 ขั้นตอนที่ 3: ติดตั้ง Plugin

ทำการติดตั้ง plugin `canvas-apps`:

```bash
claude plugin install canvas-apps@power-platform-skills
# → ✔ Successfully installed plugin: canvas-apps@power-platform-skills (scope: user)
```

> **Note (Interactive Mode):** หากใช้งานผ่านหน้าต่าง Claude Code แบบ Interactive สามารถใช้คำสั่ง:
> `/plugin install canvas-apps@power-platform-skills`

---

## ✅ ขั้นตอนที่ 4: ตรวจสอบผลการติดตั้ง

ตรวจสอบรายการ plugin และรายละเอียดการติดตั้ง:

```bash
claude plugin list
# → canvas-apps@power-platform-skills  v2.1.0  scope: user  ✔ enabled

claude plugin details canvas-apps@power-platform-skills
# → Skills (5): add-data-source, canvas-app, configure-canvas-mcp, generate-canvas-app, report-issue
# → Agents (2): canvas-app-planner, canvas-screen-builder
# → MCP servers (1): canvas-authoring
```

---

## 🚀 ขั้นตอนที่เหลือ: การตั้งค่าใน Claude Code (Interactive Mode)

> [!IMPORTANT]
> ขั้นตอนถัดไปต้องทำใน Claude Code แบบ Interactive ร่วมกับ Power Apps Studio บนเบราว์เซอร์ของคุณ

| ลำดับ | คำสั่ง / การกระทำ | ทำที่ไหน |
| :---: | :--- | :--- |
| **5** | เปิดแอปใน Power Apps Studio → **Settings** > **Updates** > ตั้งค่า **Coauthoring = On** | เบราว์เซอร์ |
| **6** | คัดลอก **Designer URL** จากแท็บ Studio | เบราว์เซอร์ |
| **7** | `/configure-canvas-mcp` | ในหน้าต่าง Claude Code |
| **8** | วาง **Designer URL** เมื่อถูกถาม | ในหน้าต่าง Claude Code |
| **9** | `List the available Canvas App controls.` *(ทดสอบเชื่อมต่อ)* | ในหน้าต่าง Claude Code |
| **10** | `/canvas-app` *(เริ่มสร้าง/แก้ไขแอป)* | ในหน้าต่าง Claude Code |

---

💡 **หมายเหตุ:** โปรดระบุ **Designer URL** เพื่อรันข้อ 7–9 ต่อได้ทันที
