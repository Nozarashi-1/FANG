

# FANG — LLM & AI Security Testing Platform

**Break AI. Before it breaks you.**

[![Python](https://img.shields.io/badge/Python-3.10+-purple?style=flat-square&logo=python&logoColor=white)](https://python.org)
[![Flask](https://img.shields.io/badge/Flask-3.0-ff2ded?style=flat-square&logo=flask&logoColor=white)](https://flask.palletsprojects.com)
[![OWASP LLM Top 10](https://img.shields.io/badge/OWASP-LLM%20Top%2010-red?style=flat-square)](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
[![MITRE ATLAS](https://img.shields.io/badge/MITRE-ATLAS-9b00ff?style=flat-square)](https://atlas.mitre.org)
[![License](https://img.shields.io/badge/License-MIT-00ffe5?style=flat-square)](LICENSE)
[![For Authorized Use](https://img.shields.io/badge/⚠-Authorized%20Use%20Only-ff3a3a?style=flat-square)]()

<br/>

> The definitive **LLM & AI red-team platform**. 64+ curated payloads covering all OWASP LLM Top 10 categories, multi-AI payload generation, obfuscation mutation engine, response analysis, attack chain builder, session history, and one-click professional pentest report export.

<br/>

[📖 **Installation**](#-installation) · [✨ **Features**](#-features) · [🗺️ **OWASP Coverage**](#️-owasp-llm-top-10-coverage) · [🐛 **Issues**](../../issues)

</div>

---

## ⚡ What is FANG?

FANG is a **localhost web platform** for authorized security testing of Large Language Models and AI systems. Built for:

- 🔬 **Security researchers** probing LLM deployments for vulnerabilities
- 🎯 **Red teams** running structured AI penetration tests
- 🐛 **Bug bounty hunters** targeting AI-powered applications
- 🎓 **Students and educators** learning about AI security in practice

FANG is **not an automated scanner**. It is a **payload arsenal, mutation engine, analysis workbench, and reporting platform**. You remain in full control of what gets sent, to whom, and when.

---

## 🖥️ Platform Overview

FANG runs as a local Flask server with a full **cyberpunk-themed UI**. Nine interconnected pages:

```
┌──────────────────────────────────────────────────────────────────┐
│  ⚡ Home    ◈ Payloads    ⚙ Tools ▾             📁 Ops ▾        │
│                           ├─ ✦ Generator        ├─ 🔗 Chains    │
│                           ├─ 🧬 Mutator         ├─ 🕐 History   │
│                           ├─ 🩺 Analyzer        └─ 📝 Report    │
│                           └─ ▶ Playground                        │
└──────────────────────────────────────────────────────────────────┘
```

**Home page** features a live animated neural-network background, a typewriter hero sequence, real-time terminal output, and a threat intelligence feed with recent LLM attack vectors.

---

## ✨ Features

### ◈ Payload Browser

64+ hand-crafted security test payloads with full metadata:

- **MITRE ATLAS** technique IDs on every card (AML.T0054, AML.T0048, etc.)
- **Variable editor** — swap `[INSTRUCTION]`, `[PERSONA]`, `[TARGET]` live in the UI
- **Resolved preview** shows the final payload text before you copy it
- Full-text search, multi-filter by severity and OWASP category, sort controls
- Export filtered results as JSON for external tooling

<br/>

### ✦ Multi-AI Payload Generator

Generate custom, context-aware payloads using your preferred AI provider:

| Provider | Default Model | Notes |
|----------|--------------|-------|
| 🟣 **Anthropic** | claude-opus-4-6 | Highest quality, most creative |
| 🟢 **OpenAI** | gpt-4 | Reliable, well-tested |
| ⚡ **Groq** | llama3-70b-8192 | Fastest inference |
| 🏠 **Ollama** | llama3 | Local, free, no API key |
| 🔧 **Custom** | Any model | Any OpenAI-compatible endpoint |

Configurable per-generation: OWASP category, attack surface, additional context, specific constraints to bypass, and count (1–15 payloads).

<br/>

### 🧬 Payload Mutator

Paste any payload → receive **obfuscated variants** to bypass input filters, content policies, and WAFs:

| Technique | What it Does |
|-----------|-------------|
| **Base64 Encode** | Wraps payload with a decode-and-execute instruction |
| **Unicode Escape** | Full `\u0041\u0042\u0043` character-level encoding |
| **Leetspeak** | `a→4 e→3 i→1 o→0 s→5 t→7` substitution |
| **Zero-width Inject** | Invisible `\u200c` chars inserted between each character |
| **ROT13** | Caesar-13 with a decode instruction |
| **Reverse + Hint** | Reversed string with decode instruction prepended |
| **HTML Entities** | `&#105;&#110;&#106;&#101;&#99;&#116;` encoding |

Every variant has a direct **COPY** and **▶ Test in Playground** button.

<br/>

### 🩺 Response Analyzer

Paste a payload + the LLM's response → FANG automatically classifies the result using **14 pattern-matching indicators**:

**Success indicators detect:** system prompt leakage, instruction disclosure, jailbreak persona acceptance, credential patterns, debug mode activation, unconditional agency compliance, and more.

**Failure indicators detect:** standard refusal boilerplate, policy violation flagging, system prompt denial, and typical safety guardrail language.

**Verdict:** `🔴 PAYLOAD LIKELY SUCCEEDED` / `🟡 POSSIBLE PARTIAL BYPASS` / `🟢 PAYLOAD BLOCKED` / `⚪ INCONCLUSIVE`

Results go directly to the Report Builder with one click.

<br/>

### 🔗 Attack Chain Builder

Build **multi-step attack sequences** — a feature unique to FANG in the LLM security tooling space.

- Browse the payload library and click to add steps to your chain
- Each step: expandable card with full payload, analyst notes, and expected outcome field
- Reorder steps with ↑↓ controls, delete individually, or clear the full chain
- Chain metadata panel: name, target system, objective
- **Export as Markdown Playbook** (`.md`) — formatted step-by-step document
- **Export as JSON** — for programmatic use and integration

<br/>

### 🕐 Session History

Every Playground request is **automatically logged to localStorage** — no setup required:

- Searchable and filterable by payload text, target URL, or HTTP status
- **View** any entry in a full detail modal (payload + response)
- **Replay** — loads any past request back into Playground instantly
- **Add to Report** — pushes any finding to the Report Builder evidence basket
- Export the full session history as JSON

<br/>

### 📝 Pentest Report Builder

Collect evidence → generate a **professional, standalone HTML pentest report**:

**Engagement metadata:** client name, tester, target system, date, scope, executive summary

**Evidence basket:** findings collected from Analyzer verdicts, Playground responses, and Session History — each editable with title, severity, and analyst notes before export

**Generated report includes:**
- Cover page with engagement details and finding counts
- Executive summary with severity breakdown table
- Detailed findings: payload used, model response, OWASP ID, MITRE ATLAS technique, analyst notes, remediation references
- Professional dark-themed styling — printable to PDF

<br/>

### ▶ Live Playground

Test payloads against real LLM endpoints with full visibility:

- Supports any **OpenAI-compatible API**
- Displays HTTP status code, response time (ms), model name
- Toggle between parsed response and raw JSON
- Quick-load buttons for the top 5 payloads from the library
- **🩺 Analyze** — sends current request directly to the Response Analyzer
- **📝 Add to Report** — adds the current finding to the Report Builder

---

## 🗺️ OWASP LLM Top 10 Coverage

| ID | Category | Payloads | MITRE ATLAS ID |
|----|----------|:--------:|:--------------:|
| **LLM01** | Prompt Injection | 15 | AML.T0054 |
| **LLM02** | Insecure Output Handling | 9 | AML.T0048 |
| **LLM03** | Training Data Poisoning | 5 | AML.T0020 |
| **LLM04** | Model Denial of Service | 5 | AML.T0034 |
| **LLM05** | Supply Chain Vulnerabilities | 4 | AML.T0010 |
| **LLM06** | Sensitive Information Disclosure | 7 | AML.T0057 |
| **LLM07** | Insecure Plugin Design | 5 | AML.T0048 |
| **LLM08** | Excessive Agency | 5 | AML.T0047 |
| **LLM09** | Overreliance | 4 | AML.T0054 |
| **LLM10** | Model Theft | 5 | AML.T0056 |
| | **Total** | **64+** | |

---

## 🚀 Installation

**Requirements:** Python 3.10+, pip

```bash
# 1. Clone the repository
git clone https://github.com/Nozarashi-1/FANG.git
cd FANG

# 2. Install dependencies (3 packages total)
pip install -r requirements.txt

# 3. Start FANG
python app.py

# 4. Open in your browser
#    http://localhost:4919
```

No database. No config files. No environment variables required. Runs entirely offline — only the AI Generator and Playground require external network access (to reach your chosen AI provider or target endpoint).

---

## 🔌 Supported Endpoints

### Generator & Playground

| Provider | Endpoint URL |
|----------|-------------|
| OpenAI | `https://api.openai.com/v1/chat/completions` |
| Groq | `https://api.groq.com/openai/v1/chat/completions` |
| Ollama (local) | `http://localhost:11434/v1/chat/completions` |
| LM Studio | `http://localhost:1234/v1/chat/completions` |
| vLLM | `http://localhost:8000/v1/chat/completions` |
| Any OpenAI-compatible | Enter custom URL in the UI |

---

## 🧱 Project Structure

```
FANG/
├── app.py                  # Flask server + 6 API routes
├── requirements.txt        # flask, requests (2 dependencies)
├── data/
│   └── payloads.py         # Curated payload database
├── templates/
│   └── index.html          # 9-page single-page app
└── static/
    ├── css/style.css       # Full cyberpunk UI stylesheet
    └── js/app.js           # Complete frontend logic
```

**API surface:**

| Route | Description |
|-------|-------------|
| `GET /api/payloads` | Search, filter, and sort the payload library |
| `GET /api/payloads/random` | Return a random payload |
| `GET /api/payloads/stats` | Severity and category counts |
| `POST /api/generate` | Generate payloads via AI provider |
| `POST /api/playground/test` | Proxy a payload to a target LLM |
| `POST /api/report/export` | Render a full HTML pentest report |

---

## ➕ Adding Custom Payloads

Add entries to `data/payloads.py` following this schema:

```python
{
    "id":       "PI-016",              # Unique identifier
    "cat":      "LLM01",               # OWASP category (LLM01–LLM10)
    "sev":      "HIGH",                # CRITICAL | HIGH | MEDIUM | LOW
    "category": "Authority Claim",     # Human-readable subcategory
    "chars":    85,                    # Approximate character count
    "payload":  "Your payload with [VARIABLE] placeholders",
    "vars":     {"VARIABLE": "default value"},
    "tags":     ["social-eng", "auth"],
    "notes":    "What this tests and why it might succeed."
}
```

---

## ⚠️ Legal & Ethical Disclaimer

**FANG is for authorized security testing only.**

| ✅ Permitted | ❌ Not Permitted |
|-------------|-----------------|
| Systems you own | Systems without explicit written permission |
| Authorized penetration test engagements | Any unauthorized access attempts |
| CTF competitions and lab environments | Causing disruption or harm |
| Security research with IRB approval | Violating terms of service |

Unauthorized use may violate the **Computer Fraud and Abuse Act (CFAA)**, **Computer Misuse Act (UK)**, **Section 202 StGB (Germany)**, or equivalent legislation in your jurisdiction. The authors assume **no liability** for misuse.

---

## 📚 References

- [OWASP Top 10 for LLM Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
- [MITRE ATLAS — ATT&CK for AI](https://atlas.mitre.org)
- [NIST AI Risk Management Framework](https://www.nist.gov/system/files/documents/2023/01/26/NIST-AI-RMF-1.0.pdf)
- [NVIDIA Garak — LLM Vulnerability Scanner](https://github.com/NVIDIA/garak)
- [Microsoft PyRIT — Python Risk Identification Toolkit](https://github.com/Azure/PyRIT)
- [HackAPrompt Research Dataset](https://github.com/Nhaga/HackAPromptDataset)

---

## 🤝 Contributing

Pull requests welcome — especially for new payloads, new OWASP coverage, mutation techniques, and UI improvements.

1. Fork the repo
2. Create your branch: `git checkout -b feature/new-payloads`
3. Make your changes
4. Open a PR with a clear description

---

## 📄 License

MIT License — see [LICENSE](LICENSE) for full text.

**For authorized security testing and educational research only.**

---

<div align="center">

Built for the security community 🔥

**[⬆ Back to top](#)**

</div>
