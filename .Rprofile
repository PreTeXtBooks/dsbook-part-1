# Install and load all packages used throughout this book so that
# sage cells work without requiring individual library() calls.

local({
  cran_pkgs <- c(
    # Core data science
    "dslabs", "tidyverse", "ggplot2", "dplyr", "readr", "tidyr",
    "stringr", "forcats", "lubridate", "purrr",
    # Extended tidyverse / data manipulation
    "data.table", "janitor",
    # Visualization
    "ggthemes", "ggrepel", "RColorBrewer", "scales",
    "gridExtra", "ggridges", "geomtextpath", "scatterplot3d",
    # Datasets
    "NHANES", "Lahman",
    # Text / NLP
    "tidytext", "textdata", "gutenbergr", "english",
    # Web / file I/O
    "readxl", "pdftools", "rvest", "httr2", "jsonlite",
    # Other
    "countrycode"
  )

  missing_pkgs <- cran_pkgs[!vapply(cran_pkgs, requireNamespace, logical(1), quietly = TRUE)]
  if (length(missing_pkgs) > 0) {
    install.packages(missing_pkgs, repos = "https://cloud.r-project.org")
  }

  # ggflags is GitHub-only
  if (!requireNamespace("ggflags", quietly = TRUE)) {
    if (!requireNamespace("devtools", quietly = TRUE)) {
      install.packages("devtools", repos = "https://cloud.r-project.org")
    }
    devtools::install_github("jimjam-slam/ggflags")
  }

  # Load the packages most commonly needed across all chapters.
  # Note: loading "tidyverse" already loads ggplot2, dplyr, readr, tidyr,
  # stringr, forcats, lubridate, and purrr.
  pkgs_to_load <- c(
    "dslabs", "tidyverse",
    "data.table", "ggthemes", "ggrepel", "RColorBrewer", "scales",
    "gridExtra"
  )
  for (pkg in pkgs_to_load) {
    tryCatch(
      suppressPackageStartupMessages(library(pkg, character.only = TRUE)),
      error = function(e) message("Could not load package '", pkg, "': ", conditionMessage(e))
    )
  }

  dslabs::ds_theme_set()
})
