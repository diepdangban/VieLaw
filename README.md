# 🏛️ VieLaw: Vietnamese Legal Dataset

![Status](https://img.shields.io/badge/Status-Protected-orange)
![Format](https://img.shields.io/badge/Format-JSON-blue)
![License](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-green)

> **⚠️ CRITICAL TECHNICAL NOTICE**
>
> **The dataset is provided "as-is." To protect intellectual property and prevent unauthorized crawling, all data files contain a hidden watermark. Users MUST implement the pre-processing steps detailed in the "Data Access" section to avoid `JSONDecodeError` failures.**

---

## 📖 Abstract

**VieLaw** is a specialized benchmark corpus designed to facilitate research and development in Natural Language Processing (NLP) within the Vietnamese legal domain. The dataset addresses the scarcity of high-quality, structured legal data for low-resource languages.

It serves as a testbed for evaluating three core competencies of Legal LLMs:
* **Legal Text Classification** (Understanding)
* **Legal Information Retrieval** (Memorization)
* **Legal Reasoning & Application** (Application)

---

## 📊 Dataset Statistics & Cognitive Levels

The VieLaw benchmark consists of **1,580 instances** categorized by cognitive complexity, moving from basic memorization to complex application.

| Cognitive Level | Task Type | Legal Domains | Instances |
| :--- | :--- | :--- | :--- |
| **Memorization** | Multiple-choice QA | Criminal, Civil, Administrative | **800** |
| **Understanding** | Classification | Criminal, Administrative | **320** |
| **Application** | Generative Reasoning | Criminal, Administrative | **460** |
| **Total** | — | — | **1,580** |

---

## 📂 Repository Structure

```text
VieLaw/
├── task1/
│   ├── dansu_task1.json
│   ├── hanhchinh_task01.json
│   └── hinhsu_task1.json
├── task2/
│   ├── hanhchinh_task02.json
│   └── hinhsu_task02.json
└── task3/
    ├── boluathinhsu_antu.json
    ├── boluathinhsu_dieuluat.json
    ├── boluathinhsu_toidanh.json
    └── hanhchinh_task03.json

```
---

## 🛠️ Data Access Guide

To ensure data integrity and prevent unauthorized scraping, the dataset files contain hidden artifacts that render standard reading methods ineffective. Attempting to use `json.load()` directly will result in errors.

**Requirement:** You must explicitly remove the **Zero Width Space (`\u200b`)** character located at the beginning of the file before parsing the JSON content.

### ✅ Python Snippet
Use the following reference implementation to correctly load and sanitize the data:

```python
import json

def load_vielaw_data(file_path):
    """
    Load VieLaw dataset handling the hidden protection character.
    """
    try:
        with open(file_path, 'r', encoding='utf-8') as f:
            content = f.read()
            
            # Remove hidden Zero Width Space (\u200b) if present
            if content.startswith('\u200b'):
                content = content[1:]
                
            return json.loads(content)
            
    except Exception as e:
        pass

# Usage
data = load_vielaw_data('path/to/hinhsu_task1.json')
```
---
## 📜 Citation

If you use **VieLaw** in your research or software projects, please cite it as follows:

```bibtex
```
---
# ⚖️ License
