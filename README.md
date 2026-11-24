# GoSLIDEEDIT — PowerPoint & Google Slides Intersection-Compatible Presentation Editor

> **Copyright (c) 2026 GoXEDIT Project (Lung2478). All Rights Reserved.**  
> **Single-File Offline Desktop Presentation Editor + Official AI Headless CLI (`GoSLIDEEDIT.exe`)**

---

## Product Overview / 產品總覽

**GoSLIDEEDIT** is an offline, portable single-file desktop presentation editor (`GoSLIDEEDIT.exe`) engineered around the **strict Microsoft PowerPoint ∩ Google Slides compatibility intersection**. Presentations created or normalized with GoSLIDEEDIT open cleanly across both Microsoft PowerPoint (Windows desktop) and Google Slides (browser) with zero font drift, zero chart misalignment, and zero broken single-vendor effects.

**GoSLIDEEDIT** 是一款本機離線運作、免安裝的單一執行檔（`GoSLIDEEDIT.exe`）商業簡報編輯器，嚴格遵循 **Microsoft PowerPoint ∩ Google Slides 最大交集相容規範**，徹底解決企業在桌面版 PowerPoint 與雲端 Google Slides 之間交換 `.pptx` 檔案時的字型跑版、圖表錯位與單邊特效失效痛點。

### Core Highlights / 核心特色
* **Offline & Portable (`GoSLIDEEDIT.exe`)**：Zero installation, zero cloud uploads, zero telemetry, zero external CDN requests — confidential corporate decks never leave your PC.
* **Strict PowerPoint ∩ Google Slides Intersection**：
  * **15 Cross-Platform Safe Fonts + Dual CJK/Latin Font Splitting (`<a:ea>` + `<a:latin>` + `<a:cs>`)**：Independently configure Chinese and English/numeric fonts with 4 built-in business presets.
  * **Grouped-Shape Vector Charts (`<p:grpSp>`) & Freeform Polygons (`<a:custGeom>`)**：Bar, line, pie, and donut charts compile into native OpenXML vector shapes with 0-pixel cross-platform drift.
  * **4 Intersection Transitions + 8 Core Animations** & **2x Offline Visual Snapshots** for incompatible external elements (SmartArt, Excel charts, OLE objects).
* **Official AI Automation Interface (Headless CLI)**：Run `GoSLIDEEDIT.exe --cli` to inspect, outline-extract, or non-destructively batch-normalize hundreds of legacy corporate `.pptx` decks (including batch `--apply-master`, `--ea-font`, `--latin-font`, and structured JSON audit reports).

---

## Download & Quick Start / 下載與快速上手

1. **Download Latest Release / 下載最新單一執行檔**：  
   Go to **[GitHub Releases](https://github.com/Lung2478/GoSLIDEEDIT/releases/latest)** and download:
   * `GoSLIDEEDIT.exe` — Standalone portable Windows 10/11 executable (requires Windows built-in Edge WebView2)
   * `QuickStart_GoSLIDEEDIT.pptx` — 11-slide interactive bilingual tutorial deck (also built into `GoSLIDEEDIT.exe`)
   * `QUICK_START.zh-TW.md` / `QUICK_START.en.md` — Bilingual Quick Start Manuals
   * `SHA256SUMS.txt` — Integrity verification checksums
2. **Verify Integrity (Optional / 驗證檔案完整性)**：
   ```powershell
   Get-FileHash .\GoSLIDEEDIT.exe -Algorithm SHA256
   ```
   Compare the output hash against `SHA256SUMS.txt` in the release package.
3. **Read the Quick Start Manuals / 閱讀快速上手指南**：
   * 繁體中文指南：[`docs/QUICK_START.zh-TW.md`](./docs/QUICK_START.zh-TW.md)
   * English Manual：[`docs/QUICK_START.en.md`](./docs/QUICK_START.en.md)

---

## Official AI Automation Interface (Headless CLI & Agent Skill)

External AI models and enterprise automation scripts can operate `GoSLIDEEDIT.exe` directly via the official **Headless CLI** (no GUI window, non-destructive by default, fully local and offline):

```powershell
# Example: Batch-normalize legacy corporate .pptx decks with unified Slide Master & dual fonts
.\GoSLIDEEDIT.exe --cli normalize .\legacy_decks --output .\clean_decks --recursive `
  --apply-master .\corp_master.pptx --ea-font "Microsoft JhengHei" --latin-font "Calibri" `
  --report .\migration_report.json
```

* **Complete CLI Reference / 完整 CLI 規格書**：[`ai-interface/CLI_SPEC.md`](./ai-interface/CLI_SPEC.md)
* **Ready-to-Load AI Agent Skill / AI 代理人標準技能檔**：[`ai-interface/SKILL.md`](./ai-interface/SKILL.md)
* Documentation and Skill templates inside `ai-interface/` are licensed under the **MIT License** ([`ai-interface/LICENSE-MIT.txt`](./ai-interface/LICENSE-MIT.txt)) for frictionless integration into your AI workflows.

---

## License & Commercial Use / 授權與商業合作

* **Software Binary (`GoSLIDEEDIT.exe`)**：Licensed under the **GoXEDIT Proprietary Freeware EULA** — **free for personal and internal enterprise use**, including automated single-file or batch invocation by internal AI agents via official CLI interfaces. Commercial redistribution, white-labeling, OEM embedding, hosted SaaS/API wrapping, and reverse engineering are strictly prohibited without a Commercial License.
  * English Authoritative License: [`LICENSE`](./LICENSE)
  * 繁體中文參考譯本: [`LICENSE.zh-TW.md`](./LICENSE.zh-TW.md)
  * Third-Party Open-Source Notices: [`THIRD_PARTY_NOTICES.txt`](./THIRD_PARTY_NOTICES.txt)
* **Official AI Interface Docs & Skills (`ai-interface/`)**：Licensed separately under the MIT License ([`ai-interface/LICENSE-MIT.txt`](./ai-interface/LICENSE-MIT.txt)).

> **商業授權與企業服務聲明 / Commercial Licensing Notice**：  
> 本免費授權涵蓋標準版之個人與企業內部使用。若貴公司需要 OEM 內嵌整合、專屬客製開發、企業級大量舊檔重製顧問、或專屬技術支援與 SLA，請聯繫 GoXEDIT 官方取得商業授權。  
> *(This free license covers personal and internal enterprise use of the Standard Edition. For OEM embedded integration, custom development, enterprise-scale legacy document migration consulting, or dedicated technical support and SLA, please contact GoXEDIT Official for a Commercial License.)*
>
> * **Contact / 聯繫管道**：GoXEDIT Official Website Contact Form / [GitHub Issues (`commercial-inquiry`)](https://github.com/Lung2478/GoSLIDEEDIT/issues)

---

## Disclaimer / 免責聲明

1. **AS IS**：This software and all accompanying documentation are provided "AS IS" without warranty of any kind, express or implied.
2. **Backup Responsibility**：Always maintain backups of original `.pptx` files before running manual edits or automated Headless CLI batch conversions, and verify converted outputs before formal delivery.
3. **Limitation of Liability**：GoXEDIT Project (Lung2478) shall not be liable for any data loss, corrupted files, business interruption, or indirect/consequential damages arising from use of the software.
4. **Trademarks**：Microsoft PowerPoint and Microsoft Office are trademarks of Microsoft Corporation. Google Slides and Google Workspace are trademarks of Google LLC. GoXEDIT is an independent software project not affiliated with or endorsed by Microsoft or Google.
