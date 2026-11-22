---
name: goslideedit-cli-operator
description: >-
  Official AI Agent Skill for operating GoSLIDEEDIT.exe in Headless CLI mode.
  Use when inspecting, extracting outlines from, or batch-normalizing legacy
  .pptx presentations into Microsoft PowerPoint and Google Slides 100%
  intersection-compatible decks completely offline.
---

# GoSLIDEEDIT Official Headless CLI Operator (`goslideedit-cli-operator`)

> **License**: This Skill file is licensed under the MIT License (`LICENSE-MIT.txt`).
> The `GoSLIDEEDIT.exe` software binary is proprietary freeware for personal and
> internal enterprise use (see `../LICENSE`).

Use this skill whenever the user asks you to audit, extract content from, or
batch-convert `.pptx` presentations using **GoSLIDEEDIT** so they render cleanly
with zero layout/font drift in both Microsoft PowerPoint and Google Slides.

## 1. Pre-Flight Checklist

1. Locate `GoSLIDEEDIT.exe` on the user's machine (ask the user if not in PATH or current folder).
2. Verify availability and version:
   ```powershell
   & "<path-to>\GoSLIDEEDIT.exe" --version
   ```
3. Never modify or overwrite the user's original `.pptx` files in place unless the user explicitly asks you to pass `--overwrite`.

## 2. Standard 3-Step AI Batch Migration Workflow

### Step 1: Read-Only Compatibility Audit (`inspect`)
Always inspect the target file or folder first and write a JSON report:
```powershell
& "<path-to>\GoSLIDEEDIT.exe" --cli inspect "<input_dir_or_pptx>" --recursive --report "<work_dir>\inspect_report.json" --json
```
Read `inspect_report.json` and report to the user:
- Total `.pptx` files found and slide counts.
- How many files have non-whitelisted fonts or single-vendor transitions/animations (`noticeCount`).
- Which files contain incompatible external elements (`incompatibleElements`, such as SmartArt or native Excel charts) that will be preserved as 2x `.png` visual snapshots.

### Step 2: Non-Destructive Batch Normalization (`normalize`)
Output normalized decks into a **new separate folder** (`--output`):
```powershell
& "<path-to>\GoSLIDEEDIT.exe" --cli normalize "<input_dir_or_pptx>" `
  --output "<new_output_dir>" `
  --recursive `
  --report "<new_output_dir>\migration_report.json" `
  --json
```

Optional enterprise standardization flags (use when requested by the user):
- Apply a corporate Slide Master template: `--apply-master "<corp_master.pptx>"`
- Enforce unified CJK + Latin safe fonts: `--ea-font "Microsoft JhengHei" --latin-font "Calibri"`
  - Safe CJK fonts: `Microsoft JhengHei`, `PMingLiU`, `DFKai-SB`
  - Safe Latin fonts: `Calibri`, `Arial`, `Arial Black`, `Verdana`, `Tahoma`, `Trebuchet MS`, `Impact`, `Times New Roman`, `Georgia`, `Cambria`, `Garamond`, `Courier New`

### Step 3: Verify Results & Report to User
1. Check process exit code (`0` = all succeeded, `1` = partial per-file errors, `2` = fatal argument/safety error).
2. Read `migration_report.json` and summarize:
   - Succeeded vs. failed file counts and output directory path.
   - Summary of font mappings and effect downgrades (`noticesByCategory`).
   - Any files with `incompatibleSnapshotCount > 0` so the user knows which slides to visually double-check (or rebuild using GoSLIDEEDIT's Remake Assistant).

## 3. Reading Presentation Content (`export-outline`)

When the user wants you to summarize, review, or QA `.pptx` files without writing XML parsers:
```powershell
& "<path-to>\GoSLIDEEDIT.exe" --cli export-outline "<input.pptx>" --format json --report "<work_dir>\outline_report.json" --json
```
Use `--format txt` for compact human-readable outlines, or `--no-notes` to omit speaker notes.

## 4. Non-Negotiable Safety Guardrails

- **Never pass `--overwrite`** targeting the original source directory without explicit user confirmation.
- **Always pass `--report <path.json>`** on Windows so UTF-8 results are captured losslessly regardless of terminal encoding.
- **Synchronous Execution in PowerShell**: Because `GoSLIDEEDIT.exe` is a Windows GUI-subsystem binary, append `| Out-String` (or use `Start-Process -Wait -PassThru` / `subprocess.run`) when invoking from PowerShell so the shell waits for completion and populates `$LASTEXITCODE`.
- **Keep original files untouched** and remind the user to visually inspect converted decks before formal external delivery.
- For complete CLI schemas and flags, consult `CLI_SPEC.md`.
