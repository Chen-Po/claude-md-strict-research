# 🛡️ Claude Code Strict Research & Data Rules (CLAUDE.md)

[![GitHub stars](https://shields.io)](https://github.com)
[![License: MIT](https://shields.io)](https://opensource.org)

> **Tired of Claude "confident guessing" and messing up your data analysis, plotting, or biological metrics?**

This repository provides an enterprise-grade `CLAUDE.md` template tailored specifically for **Data Science, Bioinformatics, Software Engineering, and Academic Research** where absolute accuracy, reproducibility, and traceability are paramount.

---

## 🚀 Quick Start (30 Seconds)

1. **Copy** the full content of [`CLAUDE.md`](./CLAUDE.md) from this repo.
2. **Paste** it into the **root directory** of your project.
3. **Name the file** exactly `CLAUDE.md`.
4. **Run** your Claude Code, Antigravity IDE, or any supported Claude interface. Watch Claude transform from a "creative guesser" into a "rigorous scientific auditor."

---

## ✨ Core Features & Safeguards

### 1. Truth Classification System (The Ultimate Shield)
Breaks the AI hallucination loop by legally forcing Claude to categorize all factual conclusions into four distinct tiers:
* `VERIFIED`: Directly supported by inspected files, command outputs, or cited documentation.
* `LIKELY`: Supported by partial evidence but not fully checked.
* `UNVERIFIED`: Plausible but not yet checked (No guessing allowed!).
* `FAILED`: Contradicted by evidence.

### 2. Mandatory Evidence Block
Before delivering any critical conclusion, Claude is forced to generate a structured evidence block detailing exactly what it checked, ensuring it **uses tools first and talks second**:
```text
- Files inspected: [paths]
- Commands run: [terminal commands]
- Key output: [raw results]
- Conclusion: [tiered status]
- Remaining uncertainty: [blind spots]
```

### 3. Rigorous Plotting & Provenance Audit
Includes a built-in markdown verification table requirement. Claude must trace variables (`source column` ➡️ `displayed label`) before regenerating plots, preventing accidental axis mismatches or data distortion.

### 4. Smart Context Switching (Optimized)
* **Casual Q&A:** Keeps replies concise and immediate to save you time.
* **Deep Analysis/Debugging:** Automatically triggers maximum rigor mode.

---

## 📊 Ideal for Domain Fields

* 🧬 **Bioinformatics:** Explicit rules handling GWAS, QTL, cell/sample-level mapping, and log-odds without conflating significance with effect size.
* 📈 **Data Science & ML:** Sanity checks for row counts, join duplicate checks, missing value counters, and random seed requirements.
* 📝 **Academic Writing:** Polishes text for scholarly tone without ever introducing unverified citations or compromising scientific precision.

---

## 🛠️ Supported Environments

Optimized and thoroughly tested on:
* **Anthropic Claude Code CLI** (Native system prompt loading)
* **Antigravity IDE**
* **Cline / Roo Code / Cursor** (Can be copied into project instructions)

## 📄 License
This project is licensed under the MIT License - feel free to fork, adapt, and share with your research teams!
