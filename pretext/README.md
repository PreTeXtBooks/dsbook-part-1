# PreText Textbook Structure

This repository contains a PreText version of "Introduction to Data Science" in the `PreText/` folder.

## File Organization

The book is now organized into multiple files for better maintainability within the `PreText/` directory:
- The `PreText/source/main.ptx` file uses XInclude to reference separate content files
- Each major section (Preface, Acknowledgements, Introduction, and the four Parts) is in its own file
- This structure makes it easier to navigate, edit, and collaborate on different sections of the book

### Image Assets

Images for the PreText book are stored in the repository root directories (`dataviz/`, `wrangling/`, `productivity/`, `R/`) and are accessed via symbolic links in the `PreText/assets/` directory. This allows PreTeXt to properly copy images to the output during the build process. The images are referenced in the PTX source files with paths relative to these directories (e.g., `dataviz/img/Bush-cuts.png`, `wrangling/img/joins.png`).

## Structure

The PreText textbook follows the same structure as the Quarto files in the main repository:

- **Title**: Introduction to Data Science
- **Preface**: Introductory material
- **Introduction**: Overview of the book

### Part 1: R (Chapters 1-6)
1. Getting started
2. R basics
3. Programming basics
4. The tidyverse
5. data.table
6. Importing data

### Part 2: Data Visualization (Chapters 7-10)
7. Visualizing data distributions
8. ggplot2
9. Data visualization principles
10. Data visualization in practice

### Part 3: Data Wrangling (Chapters 11-17)
11. Reshaping data
12. Joining tables
13. Parsing dates and times
14. Locales
15. Extracting data from the web
16. String processing
17. Text analysis

### Part 4: Productivity Tools (Chapters 18-20)
18. Organizing with Unix
19. Git and GitHub
20. Reproducible projects

## Files

### Source Files (tracked in git)
- `PreText/source/main.ptx` - Main PreText book file (uses XInclude to reference separate files)
- `PreText/source/preface.ptx` - Preface content
- `PreText/source/acknowledgements.ptx` - Acknowledgements content
- `PreText/source/introduction.ptx` - Introduction chapter
- `PreText/source/r.ptx` - Part 1: R (includes all R chapters)
- `PreText/source/data-visualization.ptx` - Part 2: Data Visualization (includes all visualization chapters)
- `PreText/source/data-wrangling.ptx` - Part 3: Data Wrangling (includes all wrangling chapters)
- `PreText/source/productivity-tools.ptx` - Part 4: Productivity Tools (includes all productivity chapters)
- `PreText/project.ptx` - Project configuration file (updated to specify `source="source"` directory)
- `PreText/publication/publication.ptx` - Publication settings (specifies external assets directory)
- `PreText/executables.ptx` - Executables configuration
- `PreText/assets/` - Symbolic links to image directories (dataviz, wrangling, productivity, R)
- `requirements.txt` - Python dependencies (PreTeXt 2.32.0)

### Build Artifacts (ignored in git)
- `PreText/output/` - Generated HTML/PDF output (not committed)
- `PreText/logs/` - Build logs (not committed)
- `PreText/.cache/` - Build cache (not committed)
- `PreText/.error_schema.log` - Error logs (not committed)

## Building the Book

To build this PreText book, you need to have PreText CLI installed. Install dependencies first:

```bash
pip install -r requirements.txt
```

Then navigate to the PreText directory and build the book:

```bash
cd PreText
pretext build web
```

For PDF output:
```bash
cd PreText
pretext build print
```

The output will be generated in the `PreText/output/` directory.

## Troubleshooting

### Runestone Services Error

If you encounter an error about "runestone services" or "webpack_static_imports.xml" during the build, this is because the build process attempts to download services from `runestone.academy` which may not be accessible. To work around this:

1. Create a minimal cache file:
```bash
mkdir -p ~/.ptx/2.32.0/rs_cache
cat > ~/.ptx/2.32.0/rs_cache/rs_services.xml << 'EOF'
<all>
	<js type="list">
	</js>
	<css type="list">
	</css>
	<cdn-url type="str">https://runestone.academy/cdn/runestone/</cdn-url>
	<version type="str">7.10.0</version>
</all>
EOF
```

2. Then retry the build command.

## Notes

This is a skeleton structure. Content placeholders have been added to each chapter and can be filled in as needed.

Images are properly configured and will render correctly in the HTML output.
