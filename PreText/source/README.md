# PreText Source Files

This directory contains the source files for the PreText version of "Introduction to Data Science".

## File Structure

The book content is organized into separate files for better maintainability:

### Main File
- **`main.ptx`** - The main book file that uses XInclude to reference all other files

### Content Files
- **`preface.ptx`** - Preface section
- **`acknowledgements.ptx`** - Acknowledgements section  
- **`introduction.ptx`** - Introduction chapter

### Parts
- **`r.ptx`** - Part 1: R
  - Includes chapters: Getting started, R basics, Programming basics, The tidyverse, data.table, Importing data
  
- **`data-visualization.ptx`** - Part 2: Data Visualization
  - Includes chapters: Visualizing data distributions, ggplot2, Data visualization principles, Data visualization in practice
  
- **`data-wrangling.ptx`** - Part 3: Data Wrangling
  - Includes chapters: Reshaping data, Joining tables, Parsing dates and times, Locales, Extracting data from the web, String processing, Text analysis
  
- **`productivity-tools.ptx`** - Part 4: Productivity Tools
  - Includes chapters: Organizing with Unix, Git and GitHub, Reproducible projects

## Benefits of This Structure

1. **Easier Navigation**: Each major section is in its own file, making it easier to find and edit specific content
2. **Better Collaboration**: Multiple people can work on different sections simultaneously without merge conflicts
3. **Improved Maintainability**: Smaller files are easier to review, edit, and maintain
4. **Modular Organization**: Content is logically separated following the book's structure

## How XInclude Works

The `main.ptx` file uses XInclude to reference the separate files:

```xml
<xi:include href="preface.ptx"/>
<xi:include href="acknowledgements.ptx"/>
<xi:include href="introduction.ptx"/>
<xi:include href="r.ptx"/>
<xi:include href="data-visualization.ptx"/>
<xi:include href="data-wrangling.ptx"/>
<xi:include href="productivity-tools.ptx"/>
```

When the book is built, PreText automatically resolves these includes and combines all files into a single document.
