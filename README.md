# 🚨 Alert Explainer

**Paste any SIEM alert. Understand it in plain English. Know what to do next.**

→ **[Live tool](https://dgiry.github.io/alert-explainer)**

---

## What it does

Paste any alert — JSON, raw log, Splunk event, or structured detection — and get:

| Output | Requires | Description |
|--------|----------|-------------|
| **Instant field extract** | ✓ Free | Format detected + fields, entities, MITRE, IOCs shown immediately — no key needed |
| **Export JSON / TXT / MD** | ✓ Free | Download or copy the full analysis — structured JSON, plain-text report, or Markdown ready for Notion / Jira / Confluence |
| **Plain-English summary** | 🤖 AI | What happened, on which system, who was involved |
| **Real severity** | 🤖 AI | AI-assessed actual risk vs the alert's stated severity, with specific signal reasoning |
| **MITRE ATT&CK** | 🤖 AI | All mapped techniques with tactic, confidence, evidence — primary technique highlighted |
| **IOC extraction** | 🤖 AI | IPs, domains, hashes, users — with one-click pivot to IOC Pivot Hub |
| **Investigation steps** | 🤖 AI | 5-7 specific steps referencing actual field values from the alert |
| **Recommended actions** | 🤖 AI | Concrete responses: isolate, reset, block, escalate |
| **False positive likelihood** | 🤖 AI | Low / Medium / High with full reasoning |

---

## AI providers

Uses your own API key — no backend required. Supported providers:

| Provider | Key stored as | Models available |
|----------|--------------|-----------------|
| **OpenAI** | `cv_oai_key` | gpt-4o-mini · gpt-4o · o4-mini |
| **OpenRouter** | `cv_openrouter_key` | Claude Opus 4.5 · Claude Haiku · Gemini Flash · Llama 3.3 70B |
| **Ollama** | `cv_ollama_url` | llama3.1 · mistral · qwen2.5 · gemma3 (local, no key required) |

Provider preference is stored in `cv_provider` and shared across all suite tools.
[OpenRouter](https://openrouter.ai) gives access to Claude, Gemini, and Llama without separate API accounts.

---

## Supported formats

Auto-detected from the input — no configuration needed.

| Platform | Detection |
|----------|-----------|
| 🔺 Trend Vision One | `workbenchId`, `workbenchName`, `riskLevel`, `attackTechniques`, `impactScope` |
| 🦅 CrowdStrike | `DetectionSummaryEvent`, `pattern_id`, `computer_name` |
| ☁️ Microsoft Sentinel | `AlertName`, `WorkspaceId`, `ProviderName` |
| 🔵 Splunk | `index=`, `WinEventLog`, `EventCode` |
| 🪟 Sysmon / Windows Event | `EventID`, `SourceImage`, `TargetImage` |
| 🟣 QRadar | `offense_id`, `type: alert` |
| 📋 CEF / LEEF | Format prefix detection |
| 📄 Raw / Unknown | Any text — AI infers the context |

---

## Junior / Expert mode

| Mode | Audience | Output |
|------|----------|--------|
| 🎓 **Junior** | T1 analysts, new to SOC | Simple language, "What does this mean?", escalation guidance |
| ⚡ **Expert** | T2/T3, detection engineers | Concise, technical, no hand-holding |

---

## Built-in examples

5 real-world style alerts ready to load:
- 🔺 **Trend Vision One** — LSASS credential dump (T1003.001 + T1055 + T1059.001, 3 IOCs)
- 🦅 **CrowdStrike** — Encoded PowerShell with remote IP and base64 command
- ☁️ **Microsoft Sentinel** — Brute force with successful login from Russia
- 🔵 **Splunk** — Lateral movement with explicit credential use
- 🪟 **Sysmon** — Process injection (`CreateRemoteThread` into lsass.exe)

---

## Usage

```
https://dgiry.github.io/alert-explainer
```

Paste your alert → instant field extraction appears immediately → add OpenAI key → click **Explain this alert** → full AI analysis in seconds.

---

## Part of the SecOps pipeline

```
🧪 defang-ioc  →  🔭 ioc-pivot  →  🔬 cve-enricher  →  🚨 alert-explainer  →  ✍️ sigma-generator
   (extract)        (pivot)           (enrich)              (explain)               (detect)
```

- **[🧪 Defang IOC](https://dgiry.github.io/defang-ioc)** — extract and defang/refang IOCs from threat reports
- **[🔭 IOC Pivot Hub](https://dgiry.github.io/ioc-pivot)** — pivot any IOC to 30+ threat intel platforms
- **[🔬 CVE Enricher](https://dgiry.github.io/cve-enricher)** — full CVE context: KEV, threat actors, patch priority
- **[✍️ SIGMA Generator](https://dgiry.github.io/sigma-generator)** — describe an attack, get a detection rule (SIGMA · Splunk · KQL · Elastic · QRadar)

---

## Deploy your own

Static HTML — works on GitHub Pages, Netlify, Vercel, or any web server.

```bash
git clone https://github.com/dgiry/alert-explainer
# open index.html in your browser
```

OpenAI API key required for AI analysis. Key stored in `localStorage` only — never transmitted anywhere except directly to OpenAI. Shared with CVE Enricher (`cv_oai_key`).

## License

MIT
