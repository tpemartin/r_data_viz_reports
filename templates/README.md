# Templates

- `template.qmd` is the base Quarto document. It sets the project root for knitting (`knitr::opts_knit$set(root.dir = rprojroot::find_rstudio_root_file())`) and loads the Noto Sans TC font via `showtext`.
- When creating any new `.qmd` file in this repo, copy from this template first (e.g., `cp templates/template.qmd reports/<new-report>.qmd`) and then edit the title and content.
- If additional template types are added (e.g., for scripts or notebooks), document them here and follow the same rule: new files of a covered type should start from the matching template.
