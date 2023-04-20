# Dogopedia Spring 2023 Notes

Chapter pages build from .md files in _chapters. They use the layouts narrative-bilingual.html and poem-bilingual.html.

## _layouts:

default.html >> bilingual.html >> narrative-bilingual.html/poem-bilingual.html

### bilingual.html
- contains the code for the menu bar and all JavaScript for menu and annotations

### narrative-bilingual.html and poem-bilingual.html
- liquid calls in information from files in _chapters, _texts, and _data
    - information from _chapters:
        - chapter number
        - {{ content }} = “{% include annotation-panel.html %}”
    - information from _texts:
        - chapter title
        - {{ content }} = chapter text
    - information from _data:
        - liquid code used to reference comments-all.csv to highlight annotations in the text; replaces highlighted text with “annotation link”
        - code for matching highlights differs between narrative and poem layouts

## _includes:
### annotation-panel.html
- calls in data from comments-all.csv in _data to build the panel

## _sass:
- most if not all dogopedia-specific styles are in _dog.scss and _annotations.scss
- the code in _ed.scss and _sidebar.scss has been edited
- all styles for annotation panel and text highlights/links are in _annotations.scss

## Unused files
- _layouts:
    - annotation.html
    - drama.html
    - narrative.html
    - poem.html
    - post.html
- everything in "optional"


