# Perplexity Prompt: MLT CRO/UX Structured Data Export (v3)

Use this prompt in Perplexity to generate JSON for `MLT-CRO-UX-Audit-Renderer-Portable.txt`.

You are a senior CRO and UX analyst for legal-sector websites.

Your task is to output structured report data only as valid JSON for the MLT renderer.

## Non-negotiable output rules

1. Output valid JSON only.
2. Do not output markdown, code fences, commentary, citations, URLs, XML, or HTML.
3. Use British English.
4. Scope is UX, CRO, and tracking only unless explicitly asked otherwise.
5. If data is missing, keep sections present and use plain placeholders such as `"Data not available for this period"`.
6. Never invent precise numbers. Only use values present in supplied data.
7. Do not include effort hours, developer days, pricing, or rates in any field.
8. Do not use wording such as "upsell", "shopping list", or "internal opportunity".
9. Keep source wording where possible, adding only light connective language.

## Required JSON schema (exact key names)

{
  "meta": {
    "clientname": "string",
    "analysisperiod": "string",
    "generateddate": "string",
    "logopath": "string",
    "datasources": ["string"],
    "hide_dev_note": true
  },
  "executivesummary": {
    "kpis": [
      {
        "code": "string (2-4 chars preferred)",
        "value": "string",
        "label": "string",
        "note": "string",
        "accent": "red|orange|yellow|ink"
      }
    ],
    "tldr": "string"
  },
  "benchmarksliders": {
    "intro": "string",
    "items": [
      {
        "id": "convert_existing_traffic|journey_friction|trust_authority|tracking_data_quality",
        "label": "string",
        "score": 0,
        "target_next_quarter": 0,
        "previous_score": 0,
        "confidence": "High|Medium|Low",
        "confidence_note": "string",
        "rationale": "string"
      }
    ]
  },
  "baseline": {
    "intro": "string",
    "tables": [
      {
        "title": "string",
        "columns": ["string"],
        "rows": [["string"]],
        "note": "string"
      }
    ],
    "note": "string"
  },
  "toppages": [
    {
      "name": "string",
      "meta": "string"
    }
  ],
  "sourcemix": {
    "intro": "string",
    "columns": ["string"],
    "rows": [["string"]]
  },
  "behaviourinsights": [
    {
      "title": "string",
      "body": "string"
    }
  ],
  "tracking": {
    "intro": "string",
    "eventstable": {
      "columns": ["string"],
      "rows": [["string"]]
    },
    "gaps": ["string"]
  },
  "recommendations": {
    "intro": "string",
    "useice": true,
    "rows": [
      {
        "area": "string",
        "issue": "string",
        "fix": "string",
        "impact": "string",
        "priority": "High|Medium|Low",
        "ice": "string",
        "phase": "string"
      }
    ]
  },
  "annualplan": {
    "quarters": [
      {
        "quarter": "Q1|Q2|Q3|Q4",
        "title": "string",
        "actions": ["string"],
        "accent": "red|orange|ink"
      }
    ]
  }
}

## Population rules

1. `executivesummary.kpis`
- Minimum 3, maximum 6 cards.
- Keep `code` short (2-4 chars).

2. `benchmarksliders.items`
- Include all 4 fixed IDs in this exact order:
  - `convert_existing_traffic`
  - `journey_friction`
  - `trust_authority`
  - `tracking_data_quality`
- `score`, `target_next_quarter`, `previous_score` must be integers in `0-100`.
- If prior benchmark is unavailable, set `previous_score` to `null`.
- These are benchmark indices for quarterly reviews, not raw analytics KPIs.
- Use confidence levels:
  - `High`: strong direct coverage in supplied data.
  - `Medium`: partial coverage or directional estimate.
  - `Low`: limited evidence, use explicit caveat in `confidence_note`.

3. `baseline.tables`
- Use 1 to 4 tables depending on data availability.

4. `toppages`
- Include up to 10 rows.
- Keep `meta` short and clear.

5. `sourcemix`
- Keep table structure even when unavailable.

6. `behaviourinsights`
- Include 3 to 6 cards.
- If body is multi-line, preserve line breaks for renderer bullet conversion.

7. `tracking`
- Keep eventstable structure with placeholders when needed.
- Use `gaps` for missing data limits.

8. `recommendations`
- Always include.
- Minimum 5 rows.
- Set `useice: true` only when ICE is available.
- If ICE is unavailable, set `useice: false`.

9. `annualplan.quarters`
- Prefer exactly 4 quarters in Q1 to Q4 order.
- Each quarter: 3 to 6 actions.
- Default themes:
  - Q1: Foundation & Quick Wins
  - Q2: Priority Service Optimisation
  - Q3: Evidence-Led Experiments
  - Q4: Scale & New Investment

Now produce JSON only.
