# INTEGRATION-NOTES.md

## 1) Placement
I placed the lightbox triggers in my existing photo gallery section because the gallery is already a natural place for interactive viewing. Clicking a photo to view it larger fits the purpose of the section.

## 2) Content
I used my own photos:
- Seahawks game at Lumen Field
- Family at Universal Studios (two photos)
- Oktoberfest photo
These represent my life outside of work with my family.

## 3) Class names reconciliation
I updated my existing images by adding the class `gallery__thumb` so the starter JavaScript could find them using the selector `.gallery__thumb`. I kept the starter lightbox overlay classes (`lightbox`, `lightbox__img`, `lightbox__caption`) as-is to match `lightbox.js`.

## 4) CSS conflicts
I kept my existing page styling and added `css/lightbox.css` as an additional stylesheet for the overlay. Any conflicts were avoided by keeping the lightbox styles scoped to `.lightbox` and its child elements.
