# Building PreTeXt Documents

This guide explains how to build and view the PreTeXt version of Chapter 7.

## Prerequisites

Install the PreTeXt CLI tool:

```bash
pip install pretextbook
```

## Quick Start

### Option 1: View as HTML (Recommended)

1. Create a simple project structure:

```bash
cd pretext
mkdir -p source publication
cp chapter-07-tidyverse.ptx source/
```

2. Create a publication file `publication/publication.ptx`:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<publication>
    <source>
        <directories external="../assets" generated="../generated-assets"/>
    </source>
</publication>
```

3. Create a project manifest `project.ptx`:

```xml
<?xml version="1.0" encoding="utf-8"?>
<project>
    <targets>
        <target name="html">
            <format>html</format>
            <source>source/chapter-07-tidyverse.ptx</source>
            <publication>publication/publication.ptx</publication>
            <output-dir>output/html</output-dir>
        </target>
    </targets>
</project>
```

4. Build the HTML output:

```bash
pretext build html
```

5. View in browser:

```bash
pretext view html
```

### Option 2: Build PDF

To build a PDF version (requires LaTeX installation):

```bash
pretext build pdf
```

## Structure

The PreTeXt file includes:

- **1 Chapter**: "The tidyverse" 
- **11 Sections**: Including "Tidy data", "The pipe", "Summarizing data", etc.
- **13 Subsections**: Detailed topic breakdowns
- **75 Code blocks**: R code examples with proper syntax highlighting
- **23 Exercises**: Converted from the original Quarto document
- **240 Inline code references**: Formatted as `<c>` elements
- **164 Paragraphs**: Full chapter content preserved

## Conversion Notes

The conversion from Quarto to PreTeXt maintains:
- ✓ All section structure and hierarchy
- ✓ All R code examples with language tagging
- ✓ All exercises with proper statement formatting
- ✓ Inline code, emphasis, and alert styling
- ✓ Mathematical expressions
- ✓ Cross-reference IDs for linking
- ✓ Note/callout boxes

## Validation

The XML has been validated and confirmed to be well-formed. Key statistics:

```
✓ XML is well-formed
✓ Found 1 chapter
✓ Found 11 sections
✓ Found 23 exercises
✓ Found 75 code blocks
```

## Further Resources

- PreTeXt Documentation: https://pretextbook.org/
- PreTeXt Guide: https://pretextbook.org/doc/guide/html/
- PreTeXt Schema: https://github.com/PreTeXtBook/pretext

## Troubleshooting

If you encounter issues:

1. Verify PreTeXt CLI is installed: `pretext --version`
2. Check XML validity: Use any XML validator or the Python script in this repo
3. Review PreTeXt documentation for element usage
4. Check that all file paths in project.ptx are correct
