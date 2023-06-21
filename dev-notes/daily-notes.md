# Daily Notes

## 02/14/23
add bibliography
- bdaw
- sokolov in general
remove documentation page
experiment with liquid in poetry chapters
lunr languages

bibliography
- the spreadsheet is a little weird to work with
    - transferring into markdown means i must italicize by hand
- if we want a more robust bibliography feature, we can add jekyll-scholar, but it will change the way the site will need to be deployed
    - GitHub pages will not build the site with the jekyll-scholar plugin, so the site will have to be built locally and then pushed to the repo (perhaps on a new gh-pages branch)
- jekyll-scholar takes BibTex format

lunr-languages
- not sure if lunr-languages will work with elasticlunr
- have not tried it yet

## 02/23/23

When annotations in both languages are visible, images that appear in both languages are duplicated. Can probably fix this with CSS by making, for example, images in the english divs always displayed, while images in russian divs always have display: none.

Also, I had to make some edits to comments-03_ru to make one of the annotations work properly (The line that ends with “Bin ich?”). It seemed to be somewhat of an odd case, but the issue might crop up again in poetry chapters with longer lines. The problem seemed to be that the first two words and last two words of the relatively long line were annotated, but the suffix for the first two words excluded the last few characters of the line and the prefix for the last two words excluded the first two characters of the line. I added these characters to the the suffix and prefix in the csv and it fixed the line.


## 02/28/23

Issue with stripping whitespace at the end of suffixes for liquid annotations on narrative chapters:
Last annotation of chapter 2 is linked just to a period “.” and the suffix string is empty “” because it’s at the end of the chapter and trailing whitespace is stripped.

Issues with annotations within annotations:
The annotation in ch 2 “север в пятнадцати минутах спокойной ходьбы на закат. Ходьбы по аллее, восставленной перпендикуляром к насыпи — на восход. На юго” breaks at “закат” because “закат” is annotated and its suffix ends before the end of the long annotated section that contains it. The links for “насыпи” and “восход” (which also fall within the long annotation) are also broken (don’t show up).

This is because anchor elements cannot be nested, but the liquid code that adds the annotations in causes this. I have been testing in Chrome, which adjusts for this and changes the html so that there aren’t nested anchor elements, creating the effect described above. This adjustment that Chrome makes is also possibly the reason why the poetry chapters currently work.

## 03/02/23

Long annotation in ch 2 ru that begins with “Метель, о ком многие” is still broken because of italics. If note of this is kept, the csv or json containing the annotation data can be edited to fix this.


## 04/06/23

Repeated lines of poetry are causing problems. In chapter 11, “Ламп своих фитиль.”

## 04/25/23

Ch 3 ru:
- “потатуй” = part of a word, highlighted; full word “потатуйка” is also annotated, but back link does not work bc full word is not highlighted/linked.
- Similar issue with “Падеспанец хорошенький танец”, “Падеспанец” is highlighted, which breaks the longer highlight (or rather, causes the liquid to not find a match for the longer annotation)
- Interestingly, between “потатуй” and “потатуйка”, the shorter annotation is marked as having a “full” overlap, while the longer has “none” (this could be very helpful). On the other hand, with “Падеспанец” and “Падеспанец хорошенький танец”, it is the longer annotation that is marked as having a “full” overlap, while the shorter one has “none.” Why is this the case? Is it something that can be adjusted so that the smaller annotation inside a longer one is always the one that is marked as “full” overlap? If liquid is used to skip over annotations marked with "full" overlap when adding highlights, then it may cause issues.
    - For example, with the “потатуй” issue above, if the liquid skips “потатуй” for highlighting, and instead highlights the longer selection, the highlighted text will link to the annotation for the longer selection, and users would have to scroll UP to see the shorter one. This feels less than ideal. On the other hand, if there is a way to subtract from/truncate the longer selection, it could be split into several links. Liquid's "split" filter could be useful for this and may even work for overlaps in the middle of long selections. It may be tricky though, depending on the order of annotations in the data.

- annotation of “грифом” and “грифом срочно, То ли с грифоном” appears to be broken because of the italicized word “срочно”; it will probably also be broken because of the overlap

## 05/22/23

- Should adjust annotation panel so that there is always a break between english and russian annotations and russian annotations always start on a new line, regardless of the size of the window
- Fix the site for smaller screens. The annotation panel resize button is invisible on Safari on my iPhone.
- For chapter 15 (ru) there is an annotation in comments-all.csv that has nothing in the "highlighted" column. Here is its ID: zc5mkpv4Ee26cXfA4TDVxg. The text of the annotation still appears in the annotation panel, but it has no highlighted text. The highlighted text should be "перемет". The annotation is also not visible on the annotation site. Perhaps it was deleted?
- Also in chapter 15, the accented letter и́ in "отчаи́ньи" is marked as an error, but it appears this way in the Azbooka PDF. (Full sentence: "Кто же взвоет в отчаи́ньи?") It may be a misspelling (spelled correctly the word is "отча́яние", meaning despair), but perhaps it is intentional. Is this alternative spelling used in other editions of the text, or is it a mistake in the PDF? Annotation ID: y1TK9JyyEe25zGOqeqyNNA.

## 05/25/22

Dogopedia, Ch 6, ru
- “с белого моего плеча” at the end of the first paragraph should be highlighted, but it is not. probably for the same reason that highlights at the ends of chapters used to be broken
- ешь-пей-ночуй (annotation id: yZBzbIeQEe2bwRvMVA9bhA) misspelling in comment. should be “enumeration”

## 05/26/22

If using find and replace to add highlights, the best approach to make sure maximum amount are added (and overlapping/darkening highlights are preserved) is to add the highlights that encompass/contain other ones first, then add the ones inside (but only match the words in the highlight, not the prefix or suffix). However, highlights that overlap only partially present their own issue. They could be combined into one link, but it would get rid of the overlapped look of the highlights. This aesthetic issue (although I would argue it's probably rather important since the darkening highlights help indicate the existence of multiple annotations tied to the same word(s)) could potentially be remedied by creating three spans (rather than two): the first section (annotated once, so lighter), the overlapping section (annotated twice, so darker), and the final section (annotated once, so lighter). (Picture a venn diagram.)

Or all overlapping highlights could be combined into one link, preserving individual hypothesis IDs for reference but linking to one annotation, meaning that users will have to scroll down to see all annotations (which they already have to do in the case of overlapping annotations that do work if they're using mouse/click navigation) and overlaps will not display as darkened/overlapped highlights.

Idea for dealing with overlaps:
- extract comment data separately from each chapter in each language
- determine overlap based on position_start and position_end values, find a way to compare the ranges of each annotation to determine overlap (how?)

Weird things I've noticed:
- annotations with the same start position aren't ordered in any specific way, might be nice to order them from longest to shortest
    - Update: Actually, annotations with the same start position are listed in order of end position, so short annotations come first. It would be great if for annotations with the same start position the longest one is listed first in the annotation panel. I wonder if I can do something with liquid to sort that out.

Other notes/ideas:
- What if i used liquid to add longer annotations first, then shorter annotations? Might it then be able to capture all nested annotations?
    - Update: I tried it and it looks promising, but needs some adjustments.