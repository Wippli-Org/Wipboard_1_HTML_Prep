# Wipboard HTML Templates

HTML templates for Wippli WipBoards. Fetched at runtime by n8n workflows and populated with client-specific data.

## Templates

| File | Used by | Fields required |
|---|---|---|
| [moorestrat.html](moorestrat.html) | Moore + More (MooreStrat) | See "Fields" below |

## How it works

1. n8n workflow completes AI analysis + doc generation
2. HTTP Request node fetches `https://raw.githubusercontent.com/Wippli-Org/Wipboard_1_HTML_Prep/main/moorestrat.html`
3. Code node replaces `{{token}}` placeholders with values from `CAPTURE_All`
4. Populated HTML is sent to the client webhook as the WipBoard page

## Token syntax

Simple Mustache-style: `{{field_name}}`

## Fields

### Document
- `{{doc_share_url}}` — shareable download link
- `{{doc_web_url}}` — direct web URL
- `{{doc_view_only_url}}` — view-only link
- `{{doc_name}}` — filename
- `{{preso_edit_url}}` — PPT edit link

### Client / Analysis
- `{{client_name}}` — e.g. "Brand X"
- `{{website}}` — client website
- `{{wippli_id}}` — numeric Wippli ID
- `{{report_generated_at}}` — date
- `{{section_count}}` — number of report sections
- `{{problem_count}}` — strategic problems
- `{{initiative_count}}` — strategic initiatives
- `{{strengths}}` / `{{weaknesses}}` / `{{opportunities}}` / `{{threats}}` — SWOT counts
- `{{swot_total}}` — sum of SWOT

### Creator branding
- `{{creator_company_name}}` — e.g. "Moore + More"
- `{{creator_logo_url}}` — full URL to logo image
- `{{brand_primary}}` — hex color
- `{{brand_background}}`, `{{brand_accent}}`, `{{brand_contrast}}`, `{{brand_copyText}}`, `{{brand_whiteCards}}`, `{{brand_placeholder}}` — hex colors

### Links
- `{{creator_url_form}}` — Wippli form URL
- `{{creator_url_productStore}}` — product page
- `{{creator_url_store}}` — creator store page
- `{{quick_action_store}}` — HUB store link
- `{{New_Wippli}}` — new task link

## Editing

1. Edit the HTML file directly on GitHub (or via local clone → push)
2. Changes are picked up on the next n8n workflow run (no deploy needed)
3. To cache-bust immediately, the n8n HTTP node appends `?ts=<timestamp>` to the raw URL

## Related

- n8n workflow: `H6Pb0WUyVGcDSDT5` on wippli-moore-n8n
- Node that fetches: `Wipboard_1_HTML_Fetch` (HTTP Request)
- Node that populates: `Wipboard_1_HTML_Prep` (Code)
