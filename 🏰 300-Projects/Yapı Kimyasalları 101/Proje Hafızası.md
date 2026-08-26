---
title: Yapı Kimyasalları 101 — Proje Hafızası
created: 2026-08-26
modified: 2026-08-26
type: note
status: active
tags: [yapi-kimyasallari, claude-import, claude-memory]
source: "Claude memories export"
---

**Purpose & context**

Mehmet Akif works in quality control at Weber Yapı Kimyasalları's Antalya facility, producing dry mortar and construction chemicals products. Core standards in scope: TS EN 12004 (ceramic tile adhesives), TS EN 998-1 (plaster mortars), TS 13566 (thermal insulation adhesives), TS 13687 (thermal insulation plasters), TS EN 13888 (grout). Career goal is to transition to a QC or production manager role at a different company; advancement at the current employer is structurally limited. Educational background: chemistry technician associate degree; prior roles in food QC and crushing-screening operations.

**Key people & context:** Works within a Weber facility where management makes unilateral decisions on certain QC practices (e.g., visual color assessment instead of spectrophotometric measurement). Operates with SAP (ERP), QDMSNET, and internal document systems. Cultural preference: presents AI-assisted work as own professional output, which is appropriate given the genuine learning and reasoning involved.

**Important working principle:** When discussing standards, Claude must not rely solely on Mehmet Akif's summary files for factual claims — those files may contain errors or omissions. Verify against actual standard texts when accuracy is in question.

---

**Current state**

- **Standards reference library:** Comprehensive summary documents exist for TS EN 12004 (21-page rebuild including EN 12004-1, EN 12004-2, and linked standards), TS EN 998-1, TS 13687 (9-page detailed summary including T1:2019 amendment and µ conversion formula), TS 13566, TS EN 13888, TS EN 1015 series, and TY.AK test methods reference document (67 pages, verbatim from SAP/QDMSNET screenshots). All uploaded to project knowledge for searchability.

- **QC Excel tooling:** Two workbooks built — raw materials (hammadde) QC database and finished product (ürün) QC database, both in QP02 format with internal hyperlink navigation. Product categorization matches physical archive binder structure (Klasör 1–6: Therm, Sıva, Seramik C1, Seramik C2, Seramik Beyaz, Derz groups).

- **PSD analysis workbook (ceramic adhesives):** `PSD_Analiz_Seramik_Yapistirici.xlsx` with 20 product sheets (8 C1, 12 C2) plus ANASAYFA index. Methodology: recipe-weighted theoretical PSD from ölçekleme.xlsx as the basis for n coefficient and spec min/max derivation — **not** raw material batch variability from KIRMA_ELEME. This correction is the key open methodological point requiring continuation.

- **Chemical additives reference document:** "Kimyasal Katkı Maddeleri Referans Dokümanı" covering cellulose ethers (Bölüm 1), aggregates (Bölüm 2), polymers/RDP (Bölüm 3), and other chemicals (Bölüm 4), each in layered "Basit Anlatım / Teknik Detay" format with product comparison appendices cross-referenced to qp02_hammaddeler entries.

- **Compliance gap tracking:** Confirmed missing products from Antalya Teknik Dosya/SharePoint versus ölçekleme.xlsx, organized by standard. TS 13687 gap may be intentional (only webertherm B Flex holds TSE/ministry approval in Antalya).

---

**On the horizon**

- **PSD Excel expansion (planned):** Add a sieve analysis (PSD) section to the PSD Excel folder or qp02_hammaddeler.xlsx, structured similarly to the PARTOZ/KIRMA_ELEME files.
- **Chemical additives mechanism research (ongoing):** Deep literature/mechanism-focused study of dry mortar additives (polymers, cellulose ethers, redispersible powders, etc.) — goal is understanding working mechanisms and integrating into formulation knowledge, not supplier comparison. This is the current primary learning focus.
- **Career development:** Certification pathway identified — IASSC ICGB accessible immediately; ASQ CSSGB requires ~36 months relevant experience (approaching eligibility depending on whether prior roles qualify); ISO 9001 internal auditor training and Six Sigma Green Belt flagged as strategic. LinkedIn technical visibility as a differentiating move.
- **Management visibility:** Build documented "business case" from identified QC gaps (e.g., color measurement issue) rather than raising informally.

---

**Key learnings & principles**

- **Slip/adhesion problem is resolved — do not revisit or reopen root cause analysis.** Focus has shifted entirely to chemical additive mechanism research.
- Cellulose ether iso-dosage substitution across chemistry classes (MHEC→HPMC) and viscosity grades is an unvalidated assumption; potency ratio ~1.9x was quantified using TY.AK.160 concentration table.
- TS 13687 and TS 13566 are Turkish national standards (single-class structure); CS I-IV and W0/W1/W2 class codes do not apply to them — distinct from EN 998-1.
- Internal spec limits (sieve analysis, bulk density thresholds) reflect company QA system decisions, not the standards themselves.
- Weber's tozuma test (TY.AK.105) is entirely proprietary — no EN/TS standard reference exists for it.
- For EN 12004: fire reaction classification (Clause 4.4) is mandatory and appears in Table 6 and all ZA annexes — an earlier summary error that was corrected and updated in the document.
- PSD variation matters far more for ceramic adhesives (0-200µm limestone at ~52.5% of recipe) than for plasters where the same material appears at ~1.9%.

---

**Approach & patterns**

- Prefers "draft in conversation first, then export to file" workflow for document creation.
- Iterative correction model: Claude proposes, Mehmet Akif corrects over time ("ileride ürün ürün seni uyarırım düzeltiriz").
- Consistent document visual format: dark teal (#1F4E5F) headers, Arial font, left-bordered italic notes, alternating row color tables.
- Connects new chemical mechanism learning directly to active formulation decisions rather than studying in isolation.
- Presents AI-assisted outputs as own professional work — appropriate given genuine learning and reasoning involved.
- Prefers substantive, differentiated guidance; not interested in generic advice already independently planned.

---

**Tools & resources**

- **Project files (at `/mnt/project/`):** `ölçekleme.xlsx` (36-product recipe scaling), `PARTOZ_2026_yeni.xlsx` (production QC batch data), `KIRMA_ELEME_2026_yeni.xlsx` (raw material sieve data), `qp02_database.xlsx` (product spec sheets), `qp02_hammaddeler_guncel-son_hali.xlsx` (raw material specs), `HAMMADDE_2026_yeni.xlsx`
- **File parsing note:** Project xlsx files are pseudo-xlsx plain text exports with `## Sheet: SheetName` delimiters — must be parsed via raw UTF-8 text splitting, not openpyxl. For internal Excel hyperlinks, use `Hyperlink(ref=cell.coordinate, location="'SheetName'!A1")` with no `target` parameter.
- **Systems:** SAP (ERP, QA32/QM entry), QDMSNET (document management), Miro (mind mapping via `diagram_create` with flowchart type)
- **Internal document codes:** TY.AK series (test methods), MA.AK series (drafted gap procedures), MGF.AK (material safety data sheets), QP02 format (quality plan/spec sheets), TY.AK.105 (tozuma — proprietary Weber method)
- **Key raw material trade names in use:** Tylose (MHEC/HEMC), Walocel MKS20000PF30 (HPMC), VINNAPAS series (RDP), Casucol Fix1, Emset KH-6, Arbocel PWC500, Mullet 2517/Octopus (process oils)