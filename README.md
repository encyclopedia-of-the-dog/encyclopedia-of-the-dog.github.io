# Encyclopedia of the Dog Development Site

## End of Summer 2022 Note

### Site Prototype

In developing the prototype for the Encyclopedia of the Dog website, we, the 2022 DSSFs, focused on designing an interface that was clean, intuitive, and accessible. We kept the project's intended audience, primarily students and Russian language learners, in mind throughout the design process, and we also wanted the design to reflect the aesthetics and themes of *Between Dog and Wolf*. We looked at existing annotated and/or multilingual digital editions of other texts to see how their websites are designed and to get a sense both of features that we liked and may consider implementing on the Dog site and of features that we do not like and want to improve upon or steer clear of. We aimed to create a site with all the necessary functionality for an annotated, bilingual digital edition of a text, without making it clunky, difficult, or irritating to use.

Moreover, we have designed the website with sustainability in mind, and we have been committed to reducing the website's carbon footprint. The website is built using [Ed.](https://minicomp.github.io/ed/), a Jekyll theme for minimal digital editions that is based on minimal computing principles. According to the [Website Carbon Calculator](https://www.websitecarbon.com), as of August 5, 2022, the Encyclopedia of the Dog prototype site runs cleaner than 95% of websites tested.

Also as of August 5, 2022, the Encyclopedia of the Dog prototype site is deployed at https://digbmc.github.io/dogopedia-dev/, though it may be taken down by the time the project is finished and the official project site is live.

### Still to Be Done / Next Steps

As the Encyclopedia of the Dog project team moves forward, here are some possible next steps and things to keep in mind:

- Annotations:
    - fully add / install Littlefoot 
    - edit / improve functionality of footnotes / annotations
    - ensure readability of annotations by screen readers
    - explore ways of including other media types such as images in annotations
    - automate the addition of annotation to the texts
    - add functionality for viewing different "layers" of annotations, allowing the user to select which kinds of annotations are visible by tags
- Proofreading:
    - after annotation is complete and all annotations have been added to the site, proofread the texts again
- Metadata:
    - include metadata for the images on the site, including the image on the homepage
- Search:
    - expand search functionality so that search works in Russian as well as in English by adding the [Lunr Languages](https://github.com/MihaiValentin/lunr-languages) plugin to the site
