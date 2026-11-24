# GoSLIDEEDIT Official Headless CLI Specification (`v1.9.0`)

> **License**: This interface specification (`ai-interface/`) is licensed under the MIT License (`LICENSE-MIT.txt`). The `GoSLIDEEDIT.exe` software binary itself is governed by the GoXEDIT Proprietary Freeware EULA (`../LICENSE`).  
> **Offline Execution**: All CLI operations execute locally with zero network requests and zero GUI windows.

---

## 1. Overview / 介面總覽

`GoSLIDEEDIT.exe` provides a dedicated **Headless CLI** mode designed for AI agents, enterprise IT scripts, and automated CI/migration pipelines to inspect, outline-extract, and batch-normalize legacy `.pptx` presentations into **Microsoft PowerPoint ∩ Google Slides intersection-compatible `.pptx`** files.

### Invocation / 呼叫方式

```powershell
# Explicit --cli flag (recommended for scripts and AI agents)
GoSLIDEEDIT.exe --cli <subcommand> [arguments]

# Check version or help
GoSLIDEEDIT.exe --version
GoSLIDEEDIT.exe --cli --help
GoSLIDEEDIT.exe --cli <subcommand> --help
```

> **Note**: Invoking `GoSLIDEEDIT.exe` without `--cli` (or with a `.pptx` path directly) launches the interactive Desktop GUI editor as usual.
>
> **Windows PowerShell Synchronous Execution Tip**: Because `GoSLIDEEDIT.exe` is compiled as a Windows GUI-subsystem binary (so double-clicking never flashes a black console window), interactive PowerShell does not block unless output is piped or `Start-Process -Wait` is used. In PowerShell scripts, pipe to `| Out-String` (or invoke via Python `subprocess.run(..., capture_output=True)` / `Start-Process -Wait -PassThru`) to wait synchronously and capture `$LASTEXITCODE` and stdout cleanly.

---

## 2. Exit Codes / 標準結束代碼

| Exit Code | Meaning / 意義 | Recommended AI Handling / AI 建議處置 |
| :---: | :--- | :--- |
| **`0`** | All target `.pptx` files processed successfully. | Read JSON output or `--report` file and summarize results. |
| **`1`** | Partial or per-file processing failure (`failed > 0`). | Inspect `files[]` entries with `"ok": false` in the JSON report and report specific errors. |
| **`2`** | Fatal argument error, missing input path, empty directory, or safety overwrite refusal. | Fix CLI flags/paths (do NOT force `--overwrite` without explicit user consent). |

---

## 3. Subcommands Reference / 三大子指令完整規格

### A. `normalize` — Single or Batch Compatibility Normalization（單檔／資料夾批次正規化）

Loads legacy `.pptx` deck(s), automatically maps non-whitelisted fonts to the 15 safe cross-platform fonts, downgrades unsupported single-vendor transitions/animations, captures incompatible external elements (SmartArt, native Excel charts, OLE objects) as clean 2x `.png` snapshots with Remake Assistant metadata, sanitizes `docProps/core.xml` metadata to `GoSLIDEEDIT`, and writes deterministic integer-EMU OpenXML `.pptx` outputs.

```powershell
GoSLIDEEDIT.exe --cli normalize <input_path> --output <dir_or_file> [options]
```

| Flag | Required | Description / 說明 |
| :--- | :---: | :--- |
| `<input_path>` | Yes | Single `.pptx` file OR directory containing `.pptx` files. Automatically skips Office lock files (`~$*.pptx`). |
| `--output`, `-o <path>` | **Yes** | Destination directory (preserves relative subfolder layout in recursive mode) or destination `.pptx` path for single-file input. **Strictly non-destructive by default.** |
| `--recursive`, `-r` | No | Recursively discover `.pptx` files in subdirectories. |
| `--overwrite` | No | Explicitly allow overwriting existing destination files (or same-path source files). **Never pass without explicit user approval.** |
| `--apply-master <template.pptx>` | No | Extract Slide Master settings (background, accent bar, corner logo, footer, page numbers `1..N`, master fonts/colors) from `<template.pptx>` and apply to every normalized deck. |
| `--ea-font <font>` | No | Override East Asian / CJK font (`<a:ea>`) across all text, shapes, tables, and charts (normalized to safe whitelist). |
| `--latin-font <font>` | No | Override Western / Latin font (`<a:latin>`) across all text, shapes, tables, and charts (normalized to safe whitelist). |
| `--json` | No | Print full structured JSON result to stdout. |
| `--report <path.json>` | No | Atomically write the full structured JSON audit report to disk (recommended for Windows reliability). |

#### Example: Enterprise Legacy Deck Migration One-Liner / 企業舊簡報批次重製範例

```powershell
.\GoSLIDEEDIT.exe --cli normalize .\legacy_decks `
  --output .\migrated_decks `
  --recursive `
  --apply-master .\templates\Corp_Master_2026.pptx `
  --ea-font "Microsoft JhengHei" `
  --latin-font "Calibri" `
  --report .\migrated_decks\migration_report.json `
  --json
```

#### `normalize` JSON Report Schema

```json
{
  "ok": true,
  "command": "normalize",
  "version": "1.9.0",
  "inputPath": "C:\\work\\legacy_decks",
  "outputPath": "C:\\work\\migrated_decks",
  "totalFiles": 12,
  "succeeded": 12,
  "failed": 0,
  "appliedMaster": "Corp_Master_2026.pptx",
  "requestedFonts": {
    "eaFont": "Microsoft JhengHei",
    "latinFont": "Calibri"
  },
  "elapsedMs": 1420.5,
  "files": [
    {
      "ok": true,
      "inputPath": "C:\\work\\legacy_decks\\Q1_Report.pptx",
      "outputPath": "C:\\work\\migrated_decks\\Q1_Report.pptx",
      "aspectRatio": "16:9",
      "slideCount": 14,
      "elementCount": 68,
      "noticeCount": 3,
      "noticesByCategory": {
        "font-mapped": 2,
        "transition-downgraded": 1
      },
      "incompatibleSnapshotCount": 1,
      "appliedMaster": "Corp_Master_2026.pptx",
      "appliedFonts": {
        "eaFont": "Microsoft JhengHei",
        "latinFont": "Calibri"
      },
      "elapsedMs": 118.4
    }
  ]
}
```

---

### B. `inspect` — Read-Only Compatibility Audit（唯讀相容性診斷）

Performs a read-only compatibility and structural scan without modifying or creating any `.pptx` files. Ideal as Step 1 before deciding whether a batch migration needs `--apply-master` or manual attention for incompatible elements.

```powershell
GoSLIDEEDIT.exe --cli inspect <input_path> [--recursive] [--json] [--report <audit.json>]
```

#### `inspect` Per-File JSON Fields
* `aspectRatio` (`"16:9"` | `"16:10"` | `"4:3"`)
* `slideCount`, `elementCount`, `elementCounts` (`textbox`, `shape`, `image`, `table`, `chart`)
* `fontsDetected` (sorted list of fonts)
* `isFullyCompatible` (`true` when `noticeCount == 0` and `incompatibleSnapshotCount == 0`)
* `notices` (detailed array of font mappings, downgraded transitions/animations)
* `incompatibleElements` (list of slide index, element ID, `originalType`, `reasonEn`, `reasonZh`)

---

### C. `export-outline` — Structured Text & Notes Extraction（純文字／JSON 大綱擷取）

Extracts all slide text, table rows, chart series summaries, and speaker notes (automatically skipping master decorative elements) so AI models can read, summarize, translate, or QA presentation content without parsing raw XML.

```powershell
# Print clean outline for a single deck to stdout
GoSLIDEEDIT.exe --cli export-outline .\deck.pptx

# Batch extract JSON outlines with speaker notes into a folder
GoSLIDEEDIT.exe --cli export-outline .\decks --output .\outlines --format json --recursive --report .\outline_report.json
```

| Flag | Description / 說明 |
| :--- | :--- |
| `--output`, `-o <path>` | Output file (`.txt`/`.json`) for single deck, or output directory for batch mode. |
| `--format txt\|json` | Output format (default: `txt`). |
| `--recursive`, `-r` | Recursively scan subdirectories. |
| `--no-notes` | Omit speaker notes from output. |
| `--overwrite` | Allow overwriting existing output files. |
| `--json` / `--report <path>` | Emit structured summary JSON. |

---

## 4. 15 Cross-Platform Safe Fonts Whitelist（安全字型白名單）

When using `--ea-font` or `--latin-font`, prefer these 15 PowerPoint ∩ Google Slides intersection fonts (any non-whitelisted font is deterministically mapped to the closest whitelisted equivalent):

* **Traditional Chinese / East Asian (3)**：`Microsoft JhengHei`、`PMingLiU`、`DFKai-SB`
* **Western / Latin (12)**：`Arial`、`Arial Black`、`Calibri`、`Verdana`、`Tahoma`、`Trebuchet MS`、`Impact`、`Times New Roman`、`Georgia`、`Cambria`、`Garamond`、`Courier New`

---

## 5. Safety & Operational Rules for AI Agents / AI 操作安全守則

1. **Always `inspect` before `normalize`**：Run `inspect --report` first on unfamiliar corporate folders to report scope and incompatible SmartArt/Excel elements to the user.
2. **Always use a separate `--output` directory**：Never pass `--overwrite` targeting the user's original directory unless explicitly instructed by the user.
3. **Always pass `--report <path.json>`**：When running on Windows, reading the written JSON report file guarantees reliable UTF-8 data capture regardless of terminal code page settings.
4. **Always remind users to review `incompatibleSnapshotCount > 0` files**：Any legacy SmartArt or native Excel chart is safely preserved as a 2x `.png` snapshot and can be rebuilt into native editable charts/text in GoSLIDEEDIT's Remake Assistant.
