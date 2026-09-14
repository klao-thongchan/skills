---
name: document-office-automation
description: "Use when processing office documents and meeting artifacts: PDFs/OCR, PowerPoint decks, Teams meeting summaries, and document cleanup/export workflows."
version: 1.0.0
author: Hermes Agent
license: MIT
platforms: [linux, macos, windows]
metadata:
  hermes:
    tags: [documents, pdf, ocr, powerpoint, office, teams, meetings]
    related_skills: [google-workspace, notion]
---

# Document & Office Automation

## Overview

This umbrella covers document-centric productivity work: extracting text from PDFs/scans, editing PDFs, creating or modifying PowerPoint decks, and operating meeting-summary pipelines. The shared requirement is artifact integrity: inspect the input, transform with the right tool, then verify the resulting file/content.

## When to Use

- OCR or text extraction from PDFs, scans, or document images.
- PDF cleanup, small text/title fixes, and export validation.
- Creating, reading, editing, or cleaning `.pptx` decks.
- Preparing slides from notes or summaries.
- Running Teams meeting transcript/summary pipelines.

## PDF and OCR

Prefer text-layer extraction first; use OCR/marker-style extraction for scans or layout-heavy documents. Preserve page numbers and cite extraction uncertainty when quality is poor.

```bash
python scripts/extract_pymupdf.py input.pdf
python scripts/extract_marker.py input.pdf
```

For PDF edits, use a purpose-built PDF editor/CLI and verify by re-extracting text or rasterizing the changed page.

## PowerPoint

Use `.pptx` tooling for structured deck edits rather than binary patching. Verify slide count, titles, notes, images, and XML/package validity after modification. Keep templates/assets with the deck when handing off.

## Teams Meeting Pipelines

Treat meeting artifacts as a pipeline: ingest transcript/recording, normalize speakers/timestamps, summarize decisions/actions/risks, write outputs to the requested destination, and verify delivery.

## Common Pitfalls

1. **Assuming PDFs have text.** Detect scanned pages and switch to OCR.
2. **Breaking Office package structure.** Validate `.pptx` files after low-level edits.
3. **Dropping provenance.** Preserve page/slide/timestamp references in summaries.
4. **Overwriting originals.** Work on copies unless the user explicitly requests in-place edits.
5. **Claiming document edits without re-opening/extracting.** Verify transformed artifacts.

## Verification Checklist

- [ ] Input file exists and type/quality were inspected.
- [ ] Transformation produced the expected output path.
- [ ] Output was re-read, opened, extracted, or otherwise validated.
- [ ] Important provenance (page/slide/timestamp) is preserved.
