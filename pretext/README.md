# PreTeXt Conversion

This directory contains PreTeXt (XML) versions of chapters from the Data Science book.

## Overview

PreTeXt is an XML-based authoring and publishing system for scholarly documents. It provides a semantic markup that can be transformed into multiple output formats including HTML, PDF, and EPUB.

## Converted Chapters

- **Chapter 7: The tidyverse** (`chapter-07-tidyverse.ptx`)
  - Original source: `R/tidyverse.qmd`
  - Converted from Quarto format to PreTeXt XML

## Conversion Details

The conversion from Quarto (.qmd) to PreTeXt (.ptx) includes:

1. **Structure conversion:**
   - Main heading (`#`) → `<chapter>` with `xml:id`
   - Section headings (`##`) → `<section>` with `xml:id`
   - Subsection headings (`###`) → `<subsection>` with `xml:id`

2. **Content elements:**
   - Paragraphs → `<p>` elements
   - Code blocks → `<program language="r">` with `<input>` child
   - Inline code → `<c>` elements
   - Emphasis (italic) → `<em>` elements
   - Bold text → `<alert>` elements
   - Math expressions → `<m>` (inline) or `<me>` (display)
   - URLs → `<url href="...">` elements

3. **Special elements:**
   - Quarto callout boxes → `<note>` elements
   - Exercise sections → `<exercise>` elements with `<statement>` children
   - Cross-references → `<xref>` elements (where applicable)

4. **Special character handling:**
   - `<` → `&lt;`
   - `>` → `&gt;`
   - `&` → `&amp;`
   - Pipe operator `|>` → `|&gt;`

## Using PreTeXt Files

To build PreTeXt documents, you'll need the PreTeXt-CLI tool:

```bash
pip install pretextbook
```

For more information about PreTeXt, visit: https://pretextbook.org/

## File Structure

Each PreTeXt file follows this basic structure:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<pretext xmlns:xi="http://www.w3.org/2001/XInclude">
  <chapter xml:id="chapter-id">
    <title>Chapter Title</title>
    <section xml:id="section-id">
      <title>Section Title</title>
      <p>Content...</p>
    </section>
  </chapter>
</pretext>
```

## Notes

- XML IDs are preserved from the original Quarto cross-reference labels where possible
- Code blocks are marked with `language="r"` to indicate R programming language
- The conversion maintains the semantic structure and educational content of the original
- Exercise numbering has been preserved from the original document
