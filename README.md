# 🚨 Alert Explainer

**Paste any SIEM alert. Understand it in plain English. Know what to do next.**

→ **[Live tool](https://dgiry.github.io/alert-explainer)**

---

## What it does

Paste any alert — JSON, raw log, Splunk event, or structured detection — and get:

| Output | Description |
|--------|-------------|
| **Plain-English summary** | What happened, on which system, who was involved |
| **Real severity** | AI-assessed actual risk vs the alert's stated severity |
| **MITRE ATT&CK** | Mapped techniques with confidence level and evidence |
| **IOC extraction** | IPs, domains, hashes, users — with one-click pivot to IOC Pivot Hub |
| **Investigation steps** | Ordered checklist of what to do first |
| **Recommended actions** | Concrete responses: isolate, reset, block, escalate |
| **False positive likelihood** | Low / Medium / High with reasoning |

---

## Supported formats

Auto-detected from the input — no configuration needed.

| Platform | Detection |
|----------|-----------|
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

4 real-world style alerts ready to load:
- 🦅 **CrowdStrike** — Encoded PowerShell with remote IP and base64 command
- ☁️ **Microsoft Sentinel** — Brute force with successful login from Russia
- 🔵 **Splunk** — Lateral movement with explicit credential use
- 🪟 **Sysmon** — Process injection (`CreateRemoteThread` into lsass.exe)

---

## Usage

```
https://dgiry.github.io/alert-explainer
```

Paste your alert → click **Explain this alert** → get full analysis in seconds.

---

## Part of the SecOps pipeline

```
🧪 defang-ioc  →  🔭 ioc-pivot  →  🔬 cve-enricher  →  🚨 alert-explainer  →  ✍️ sigma-generator
   (extract)        (pivot)           (enrich)              (explain)               (detect)
```

- **[🧪 Defang IOC](https://dgiry.github.io/defang-ioc)** — extract and defang/refang IOCs from threat reports
- **[🔭 IOC Pivot Hub](https://dgiry.github.io/ioc-pivot)** — pivot any IOC to 30+ threat intel platforms
- **[🔬 CVE Enricher](https://dgiry.github.io/cve-enricher)** — full CVE context: KEV, threat actors, patch priority

---

## Deploy your own

Static HTML — works on GitHub Pages, Netlify, Vercel, or any web server.

```bash
git clone https://github.com/dgiry/alert-explainer
# open index.html in your browser
```

Requires an OpenAI API key for AI analysis. Key stored in `localStorage` only — never transmitted anywhere except directly to OpenAI.

## License

MIT
