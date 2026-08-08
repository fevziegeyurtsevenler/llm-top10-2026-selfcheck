# OWASP LLM Top 10 (2026) Self-Assessment

**Canlı demo / Live demo:** https://huggingface.co/spaces/fevziegeyurtsevenler/llm-top10-2026-selfcheck

An interactive, single-file self-assessment checklist for the **OWASP Top 10 for
LLM Applications 2026** (LLM01–LLM10). It runs entirely in your browser: check
off the controls you have in place and see a per-risk and overall coverage
posture. Nothing is uploaded — state is kept in `localStorage` and can be
exported as JSON.

## Contents

- `index.html` — a generic, XSS-safe renderer over `data.json` (EN/TR toggle,
  light/dark theme, sticky score bar, JSON copy/download, `localStorage` state).
- `data.json` — the framework content: meta plus the ten risks LLM01:2026 …
  LLM10:2026, each with an English (official) title, an unofficial Turkish
  translation, a concise editorial summary, the 2025 → 2026 change note, and
  3–5 concrete yes/no self-assessment controls.

## Run it

Because the page loads `data.json` over `fetch`, serve the folder over HTTP
rather than opening the file directly:

```
python3 -m http.server 8080
# then open http://localhost:8080/
```

## What it is — and is not

This is a **self-assessment aid, not an audit or certification**. It helps you
reason about coverage; it does not measure it.

- **English risk titles and IDs are official** and belong to the OWASP GenAI
  Security Project.
- **The Turkish text is an unofficial community translation.** The authoritative
  source is the English OWASP document.
- The summaries and the yes/no controls are editorial: they are grounded in the
  controls described by the OWASP source, phrased as actionable questions.
- The **2025 → 2026 change** note on each risk reflects how the official 2026
  list reorders or renames the 2025 edition. No statistics, CVEs, incidents, or
  MITRE ATLAS mappings are invented in this project.

This project is independent and is **not affiliated with, sponsored by, or
endorsed by OWASP**.

## Source

OWASP Top 10 for LLM Applications 2026 — OWASP GenAI Security Project:
<https://genai.owasp.org/resource/owasp-genai-llm-top-10-2026/>
(published 2026-08-04).

## İlgili yazılar / Related articles

- [OWASP LLM Top 10 2026 CISO Özeti — Yöneticiler İçin Karar Rehberi](https://altaysec.com.tr/arastirmalar/owasp-llm-top10-2026-ciso-yonetici-ozeti)
- [OWASP LLM Top 10 2026 mı, Agentic Top 10 mı? Hangi Liste Ne Zaman](https://altaysec.com.tr/arastirmalar/llm-top10-2026-vs-agentic-top10)

## Licensing

- **Text and data** (`data.json` content, this README's framework text):
  Creative Commons Attribution-ShareAlike 4.0 (**CC BY-SA 4.0**), matching the
  ShareAlike license of the OWASP source. See `NOTICE`.
- **Application code** (`index.html` and the rest of the tooling): **MIT**. See
  `LICENSE`.

## Privacy and security

- Fully static; no backend, no analytics, no external asset URLs.
- All dynamic text is inserted via `textContent` — no `innerHTML`,
  `outerHTML`, `document.write`, or `insertAdjacentHTML`.
- A strict inline Content-Security-Policy meta tag and a `<noscript>` fallback
  are included.
