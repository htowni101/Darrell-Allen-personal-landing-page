# LIGHTBOX-NOTES.md

## 1) The DOM

**Lines that locate DOM elements:**
- Line 6: `const lb       = document.querySelector('.lightbox');`
- Line 7: `const lbImg    = lb.querySelector('.lightbox__img');`
- Line 8: `const lbCap    = lb.querySelector('.lightbox__caption');`
- Line 9: `const thumbs   = document.querySelectorAll('.gallery__thumb');`

**Single vs collection:**
- `querySelector(...)` (lines 6–8) returns a **single DOM element**
- `querySelectorAll(...)` (line 9) returns a **collection (NodeList)**

**Why `lb.querySelector(...)` instead of `document.querySelector(...)` for nested elements?**  
Because `.lightbox__img` and `.lightbox__caption` are guaranteed to live *inside* the `.lightbox` element. Querying from `lb` scopes the search, avoids accidental matches elsewhere in the document, and is more efficient than searching the entire DOM.

---

## 2) Event Listeners

**All `addEventListener` calls:**

1. **Thumbnail click**
   - Element: each `.gallery__thumb`
   - Event: `click`
   - Handler does: opens the lightbox at the clicked image index
   - Lines: 47–49  
     `thumb.addEventListener('click', () => openLightbox(i));`

2. **Lightbox overlay click**
   - Element: `.lightbox`
   - Event: `click`
   - Handler does: closes the lightbox when clicking the backdrop
   - Lines: 51–53  
     `if (e.target === lb) closeLightbox();`

3. **Escape key**
   - Element: `document`
   - Event: `keydown`
   - Handler does: closes the lightbox when Esc is pressed
   - Lines: 55–57  
     `if (e.key === 'Escape' && state.isOpen) closeLightbox();`

**Event delegation?**  
Yes (lightbox click listener).  
The listener on `.lightbox` handles clicks for all child elements by checking `e.target === lb` (line 52) to determine whether the backdrop itself was clicked.

---

## 3) State and the render pattern

**State object and fields:**
- Lines 12–20:  
  ```js
  const state = {
    isOpen: false,
    index: 0,
    images: [
      { src: 'images/sample-1.svg', caption: 'Sample image one — replace with your own' },
      { src: 'images/sample-2.svg', caption: 'Sample image two — a second photo' },
      { src: 'images/sample-3.svg', caption: 'Sample image three — a third' },
    ],
  };
  