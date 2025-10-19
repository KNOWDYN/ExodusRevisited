# Exodus, Revisited — Metadata Evidence Archive

This repository contains the **metadata-level dataset** used in  
*Exodus, Revisited: How Old Empires Shaped Cultural Memory into Religious Text.*

It serves as the transparent evidence ledger behind the book’s meta-analysis of archaeological, textual, bioarchaeological, and environmental studies related to the Exodus and the Hyksos expulsion.

---

## 📘 Purpose

To provide open, citable metadata for every peer-reviewed source included in the study corpus.  
Each row represents a single published study screened under the project’s PRISMA-style inclusion criteria.

---

## 📂 Contents

| File | Description |
|------|--------------|
| `exodus_studies_master.csv` | Primary dataset of all studies passing inclusion thresholds. Includes bibliographic data, domain classification, dating control, and quality rating. |
| `scorecard_summary.csv` | Condensed evidence-weighting table (Strong/Medium/Weak × High/Medium/Low confidence) aggregated by domain. |
| `excluded_studies.csv` | Studies screened but excluded, with exclusion reason for transparency. |
| `criteria_reference.csv` | Definitions of PRISMA criteria and evidence-rating schema used across the dataset. |

> ⚠️ This repository hosts **data only** — no scripts, notebooks, or figures.

---

## 🧭 Data Schema

**Core fields in `exodus_studies_master.csv`:**

| Column | Type | Description |
|---------|------|-------------|
| `study_id` | string | Unique internal reference key |
| `citation` | string | Full bibliographic reference |
| `year` | integer | Year of publication |
| `domain` | categorical | One of: Archaeology, Texts, Toponymy, Epigraphy, Environment, CulturalMemory |
| `region` | categorical | Egypt, Sinai, SouthernLevant |
| `temporal_scope` | string | Date range covered (BCE) |
| `method_type` | string | e.g. excavation, isotope, textual analysis |
| `dating_reliability` | string | High / Medium / Low |
| `data_transparency` | boolean | Whether methods and sample sizes are reported |
| `strength` | string | Evidence strength rating (S/M/W) |
| `confidence` | string | Evidence confidence rating (H/M/L) |
| `notes` | text | Summary of relevance or limitations |
| `included_in_meta` | boolean | Flag if used in quantitative synthesis |

---

## 🧪 Example Usage

```python
import pandas as pd

df = pd.read_csv("exodus_studies_master.csv")

# Filter for high-confidence archaeological studies
arch = df[(df["domain"] == "Archaeology") & (df["confidence"] == "H")]

print(arch[["citation", "strength", "confidence"]])
