
  ขั้นตอนที่ 0 — ตรวจ prerequisite ก่อนติดตั้ง

  dotnet --version
  # → 10.0.301   ✅ ผ่านเกณฑ์ .NET SDK 10+

  dotnet --list-sdks
  # → 10.0.301 [/home/indows-11/.dotnet/sdk]

  command -v dnx
  # → /home/indows-11/.dotnet/dnx   ✅ มีตัวรัน MCP server (มากับ .NET SDK 10)


  ขั้นตอนที่ 1 — ถอน plugin เดิมออกก่อน (ตามที่ขอ)

  claude plugin uninstall canvas-apps@power-platform-skills
  # → ✔ Successfully uninstalled plugin: canvas-apps (scope: user)

  claude plugin list
  # → ยืนยันว่า canvas-apps หายไปจากรายการแล้ว

  ขั้นตอนที่ 2 — เพิ่ม marketplace

  claude plugin marketplace add microsoft/power-platform-skills
  # → ✔ Marketplace 'power-platform-skills' already on disk — declared in user settings
  (คำสั่งเดียวกันเวอร์ชันที่พิมพ์ในหน้าต่าง Claude Code ตอนเปิดแบบ interactive คือ /plugin marketplace add microsoft/power-platform-skills)

  ขั้นตอนที่ 3 — ติดตั้ง plugin

  claude plugin install canvas-apps@power-platform-skills
  # → ✔ Successfully installed plugin: canvas-apps@power-platform-skills (scope: user)
  (เวอร์ชัน interactive: /plugin install canvas-apps@power-platform-skills)

  ขั้นตอนที่ 4 — ตรวจสอบผลการติดตั้งจริง

  claude plugin list
  # → canvas-apps@power-platform-skills  v2.1.0  scope: user  ✔ enabled

  claude plugin details canvas-apps@power-platform-skills
  # → Skills (5): add-data-source, canvas-app, configure-canvas-mcp,
  #               generate-canvas-app, report-issue
  ขั้นตอนที่ 3 — ติดตั้ง plugin

  claude plugin install canvas-apps@power-platform-skills
  # → ✔ Successfully installed plugin: canvas-apps@power-platform-skills (scope: user)
  (เวอร์ชัน interactive: /plugin install canvas-apps@power-platform-skills)

  ขั้นตอนที่ 4 — ตรวจสอบผลการติดตั้งจริง

  claude plugin list
  # → canvas-apps@power-platform-skills  v2.1.0  scope: user  ✔ enabled

  claude plugin details canvas-apps@power-platform-skills
  # → Skills (5): add-data-source, canvas-app, configure-canvas-mcp,
  #               generate-canvas-app, report-issue
  # → Agents (2): canvas-app-planner, canvas-screen-builder
  # → MCP servers (1): canvas-authoring

  ---
  ขั้นตอนที่เหลือ — ต้องทำใน Claude Code แบบ interactive (ทำแทนไม่ได้เพราะต้องมี Power Apps Studio จริงของคุณ)

  ┌──────┬────────────────────────────────────────────────────────────────────┬──────────────────────┐
  │ ลำดับ │                           คำสั่ง/การกระทำ                            │        ทำที่ไหน        │
  ├──────┼────────────────────────────────────────────────────────────────────┼──────────────────────┤
  │ 5    │ เปิดแอปใน Power Apps Studio → Settings > Updates > Coauthoring = On │ เบราว์เซอร์            │
  ├──────┼────────────────────────────────────────────────────────────────────┼──────────────────────┤
  │ 6    │ คัดลอก Designer URL จากแท็บ Studio                                   │ เบราว์เซอร์            │
  ├──────┼────────────────────────────────────────────────────────────────────┼──────────────────────┤
  │ 7    │ /configure-canvas-mcp                                              │ ในหน้าต่าง Claude Code │
  ├──────┼────────────────────────────────────────────────────────────────────┼──────────────────────┤
  │ 8    │ วาง Designer URL เมื่อถูกถาม                                          │ ในหน้าต่าง Claude Code │
  ├──────┼────────────────────────────────────────────────────────────────────┼──────────────────────┤
  │ 9    │ List the available Canvas App controls. (ทดสอบเชื่อมต่อ)              │ ในหน้าต่าง Claude Code │
  ├──────┼────────────────────────────────────────────────────────────────────┼──────────────────────┤
  │ 10   │ /canvas-app (เริ่มสร้าง/แก้ไขแอป)                                      │ ในหน้าต่าง Claude Code │
  └──────┴────────────────────────────────────────────────────────────────────┴──────────────────────┘

 ระบุ Designer URL เพื่อรันข้อ 7-9 ต่อให้ทันที
