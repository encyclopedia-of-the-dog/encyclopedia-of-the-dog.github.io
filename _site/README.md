# *Encyclopedia of the Dog* Dev Site

## Site Structure (updated 2023-08-04)

### _layouts and _includes:
- page.html is nested inside default.html
- poetry-chapter.html and prose-chapter.html are nested in bilingual.html
- home.html is standalone

#### page.html 
- used for About, ToC, Bibliography, Credits, Search, and Feedback pages

#### home.html
- home.html is its own layout (not nested in default.html) because the hero header had to be outside of the <main> section

#### poetry-chapter.html and prose-chapter.html
- Liquid is used to get information from files in _chapters, _texts, and _data
    - Information from _chapters:
        - chapter number
    - Information from _texts:
        - chapter title and text (used in includes)
    - Information from _data:
        - liquid used to reference comments-all.csv to highlight annotations in the text; replaces highlighted text with “annotation link”, a copy of the text wrapped in <span> tags
        - code for matching highlights differs between narrative and poem layouts
- The annotated-poetry.html, annotated-prose.html, and annotated-title.html includes are called
    - These includes call information from _texts and _data to replace each piece of annotated text with a copy that is wrapped in <span> tags. The spans, which are styled to appear highlighted, are clickable and act link links to the corresponding comments in the annotation panel.
    - annotated-poetry.html and annotated-prose.html use data from comments-all.csv, while annotated-title.html uses comments-chap-notes.csv
- The annotation-panel.html include is called
    - This include builds the annotation panel for each chapter, using data from comments-chap-notes.csv and comments-all.csv, and it includes backlinks to the corresponding "highlights" in the main text.

## _sass:
- Most, if not all, *Dog*-specific styles are in _dog.scss and _annotations.scss.
- _dog.scss contains the styles for the bilingual layouts, while _annotations.scss contains the styles for the annotation functionality.
- Some of the base Ed code in _ed.scss has been edited.
- All styles for the annotation panel and text highlights are in _annotations.scss.

## Still to Be Done / Next Steps

As the Encyclopedia of the Dog project team moves forward, here are some possible next steps and things to keep in mind:

- Content:
    - update About page
    - update Bibliography
    - update comments data from Hypothesis as more work is done
- Annotations:
    - add functionality for viewing different "layers" of annotations, allowing the user to select which kinds of annotations are visible by tags
    - remove comments with editorial tags from the data used on the site
- Proofreading:
    - after annotation is complete and all annotations have been added to the site, proofread the texts again
- Metadata:
    - include metadata for the images on the site, including the image on the homepage
- Search:
    - expand search functionality so that search works in Russian as well as in English by adding the [Lunr Languages](https://github.com/MihaiValentin/lunr-languages) plugin to the site


## End of Summer 2022 Note

### Site Prototype

In developing the prototype for the Encyclopedia of the Dog website, we, the 2022 DSSFs, focused on designing an interface that was clean, intuitive, and accessible. We kept the project's intended audience, primarily students and Russian language learners, in mind throughout the design process, and we also wanted the design to reflect the aesthetics and themes of *Between Dog and Wolf*. We looked at existing annotated and/or multilingual digital editions of other texts to see how their websites are designed and to get a sense both of features that we liked and may consider implementing on the Dog site and of features that we do not like and want to improve upon or steer clear of. We aimed to create a site with all the necessary functionality for an annotated, bilingual digital edition of a text, without making it clunky, difficult, or irritating to use.

Moreover, we have designed the website with sustainability in mind, and we have been committed to reducing the website's carbon footprint. The website is built using [Ed.](https://minicomp.github.io/ed/), a Jekyll theme for minimal digital editions that is based on minimal computing principles. According to the [Website Carbon Calculator](https://www.websitecarbon.com), as of August 5, 2022, the Encyclopedia of the Dog prototype site runs cleaner than 95% of websites tested.

Also as of August 5, 2022, the Encyclopedia of the Dog prototype site is deployed at https://digbmc.github.io/dogopedia-dev/, though it may be taken down by the time the project is finished and the official project site is live.