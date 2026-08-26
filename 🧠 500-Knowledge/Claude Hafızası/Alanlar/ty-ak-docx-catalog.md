---
title: ty-ak-docx-catalog
created: 2026-08-26
modified: 2026-08-26
type: note
status: active
tags: [claude-import, claude-memory]
source: "Claude memories export"
---

---
name: ty-ak-docx-catalog
description: Building a Word (.docx) document from TY.AK series images — image + description + title + keywords layout, searchable via Ctrl+F
sources: [chat, backfill]
aliases: [TY.AK serisi, TY.AK docx]
---

- [stated] Will send TY.AK series images to be cropped/edited and compiled into a .docx file openable in Microsoft Word
- [stated] Layout: image with accompanying description (not full-page images alone)
- [stated] Images need to be large scale, high resolution/pixel quality since raw images look bad when dropped directly into docx
- [stated] May send images already enhanced by another AI tool if needed
- [stated] Wants a title, description, and keywords for each image so the document is searchable with Ctrl+F
- [stated] Prefers Claude to suggest title/description/keywords based on each image rather than supplying them himself
- [stated] Wants a cover/home page and a table of contents at the start of the document for easy navigation
- [stated] Processing 74 TY.AK series test procedure images into a searchable Word file using Python/PIL image enhancement and python-docx