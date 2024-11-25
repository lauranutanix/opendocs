Creating PDFs using with-pdf: https://github.com/orzih/mkdocs-with-pdf

- Installed requirements and plugin itself
- Running `mkdocs build` should automatically generate the PDF. 

Made the following updates to the doc files:

* Updated mkdocs.yml
  ```
  plugins:
  - search
  - with-pdf:
      output_path: /Users/laura.jordana/dev/opendocs/giab-opendocs.pdf
      cover_title: "GPT-in-a-Box 1.0"
      cover_subtitle: "Deprecated"
      author: "Nutanix"
    ```
* Created a `latest` folder for the GPT-in-a-Box files, otherwise that section wasn't rendering.
  * e.g. renamed `docs/gpt-in-a-box/overview.md` to `docs/gpt-in-a-box/latest/overview.md`
* CSS changes in extra.css to address these issues:
  * Admonition overlap with text
https://github.com/orzih/mkdocs-with-pdf/issues/161#issuecomment-2449745011
  * Code samples not showing up https://github.com/orzih/mkdocs-with-pdf/issues/117
  * Changing line color from red to purple: https://github.com/orzih/mkdocs-with-pdf/issues/153#issuecomment-2419403452 
