# MLT CRO & UX Audit Report Tool

This repository contains a simple report tool that turns Perplexity output into a branded, client-ready PDF.

You do **not** need coding skills to use it.

## What this tool does

1. You generate structured audit data in Perplexity.
2. You import that data into the report page.
3. You export a polished PDF for client delivery.

## Who this is for

- MLT team members preparing CRO/UX audits
- Anyone creating client-facing legal sector audit reports

## Files you need to know

- `MLT-CRO-UX-Audit-Renderer-Portable.html`
  - Main report page (open this in your browser)
- `Perplexity-Master-Prompt-v2.txt`
  - Master instruction set for Perplexity
- `Perplexity-MLT-Structured-Data-Prompt.txt`
  - Strict JSON schema prompt for Perplexity

## Quick start (5 steps)

### Step 1: Open Perplexity

Use your normal Perplexity workspace/thread.

### Step 2: Use the prompt files

Load or paste instructions from:

- `Perplexity-Master-Prompt-v2.txt`
- `Perplexity-MLT-Structured-Data-Prompt.txt`

Important: Perplexity must return **JSON only** (not HTML).

### Step 3: Save Perplexity output

- Copy the JSON output
- Save it as a `.json` file
- Example filename: `bto-audit-feb-2026.json`

### Step 4: Open the renderer

Open:

- `MLT-CRO-UX-Audit-Renderer-Portable.html`

Then click:

- `Import JSON`

Select your saved `.json` file.

### Step 5: Export client PDF

Click:

- `Export to PDF`

Use these print settings:

- Paper size: **A4**
- Background graphics: **On**
- Scale: **100%**

Save the file.

## Team workflow (recommended)

1. Analyst prepares Perplexity JSON
2. Reviewer checks report on-screen
3. Reviewer exports final PDF
4. PDF is shared with client/internal team

## Common issues and fixes

### 1) "No content" or blank report

Cause: JSON format is invalid or incomplete.

Fix:

- Confirm Perplexity returned valid JSON only
- Re-run with strict prompt
- Re-import JSON file

### 2) Only 3 quarterly boxes appear

Cause: JSON includes only 3 roadmap items (legacy format).

Fix:

- Ensure JSON includes `annual_plan.quarters` with Q1, Q2, Q3, Q4

### 3) Logo missing

The portable renderer has embedded logo fallback.
If missing, refresh page and re-import JSON.

### 4) PDF layout looks wrong

Check print settings:

- A4 paper
- Background graphics on
- 100% scale

If still wrong, try Chrome or Safari.

## Quarterly section format (required)

Reports should include 4 quarter cards under:

- **Annual Action Plan (Quarterly)**

Expected quarter themes:

- Q1: Foundation & Quick Wins
- Q2: Priority Service Optimisation
- Q3: Evidence-Led Experiments
- Q4: Scale & New Investment

Each quarter should have:

- Title
- 3 to 6 action bullets

## Governance reminders

- Default scope is CRO/UX/tracking only
- Do not include SEO/content recommendations unless explicitly requested
- Use British English
- Keep wording client-safe and clear

## Versioning and updates

When updating prompts or renderer:

1. Commit changes to this repo
2. Update team to use latest files
3. Re-test with one sample JSON before client delivery

## Support

If something looks wrong in output:

- Keep the JSON file
- Keep the PDF export
- Raise it internally with both files attached

That allows quick diagnosis and fixes.
