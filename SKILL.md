---
name: paper-to-obsidian
description: Reads an academic paper PDF and saves a structured Korean summary note to the user's Obsidian vault. Trigger when the user says things like "이 논문 요약해서 옵시디언에 저장해줘", "논문 요약 노트 만들어줘", "이 PDF 옵시디언에 정리해줘", "논문 읽고 요약해줘", "이 논문 정리해줘". The user provides a PDF file path; Claude reads it, summarizes in Korean with 3 structured sections, and writes a markdown note to the Obsidian vault.
---

# Paper to Obsidian

Reads a research paper PDF and saves a structured Korean summary note to Obsidian.

## Vault Location

Default: `C:\Users\lihwa\Documents\Obsidian Vault\`

If the user specifies a subfolder (e.g., `VR_reference/Introduction`), save there instead.

## Workflow

### Step 1 — Get the PDF

The user provides a PDF file path directly. Ask for it if not given.

For papers in the local Zotero storage, the path typically looks like:
`C:\Users\lihwa\Zotero\storage\[8-char-key]\[filename].pdf`

### Step 2 — Read the paper

Use the `Read` tool on the PDF file path. For papers longer than 20 pages, read in this order of priority:
- Abstract + Introduction (first 4 pages)
- Methodology section
- Results / Experiments section
- Conclusion

### Step 3 — Summarize in Korean (3 sections)

Write summaries using the **exact Korean headers** below. Be specific and detailed.

| Section | What to include |
|---|---|
| **핵심 문제** | The exact limitation(s) of prior work the paper targets. Use bullet points with `→` to show how each limitation is addressed |
| **방법론** | Specific tool names, model architectures, algorithms, datasets (keep in English); description in Korean. Include key performance numbers |
| **인용 문장** | A single citation-ready sentence in Korean, third-person academic style, with `[ ]` citation placeholders |

See [note-template.md](references/note-template.md) for exact format and examples.

### Step 4 — Determine the filename

Format: `[Full Paper Title](Year).md`

Use the paper's actual title and publication year. Do not abbreviate.

Examples:
- `Geometry- and Appearance-Based Reasoning of Construction Progress Monitoring(ASCE2018).md`
- `Automated Construction Progress Monitoring Using Image Segmentation(2024).md`

### Step 5 — Write the note

Write the file to `C:\Users\lihwa\Documents\Obsidian Vault\[filename]` using the Write tool.

## Language Rules

- All summary content in **Korean**
- Model names, algorithm names, tool names, acronyms: **keep in English**
- Citation sentence: third-person, academic style, ends with `[ ]` placeholder
