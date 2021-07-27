---
layout: post
title:  "Absolute positioning and the importance of doctype"
date:   2010-04-04 10:39:29 +1000
categories: programming
---

When a CSS layout breaks in Internet Explorer (IE) 7 or 8, it may be due to the lack of an appropriate HTML/XHTML [doctype declaration](https://www.w3schools.com/tags/tag_doctype.asp).

My latest site design involves a footer positioned at the bottom of the viewport (browser window) or, if the content spills off-screen, below everything else on the page. My design relies on the following code in my stylesheet:

```
#footer {
  position:absolute;
  bottom:0;
  padding-bottom:10px;
}
```

Chrome, Safari, and Firefox rendered the footer perfectly on Mac and Windows Vista, but my design failed in IE7.

I learned that IE7 and IE8 require the `strict` HTML/XHTML doctype for absolute positioning to work. Updating my site's pages to the strict doctype required one copy-paste action, thanks to PHP, and fixed the problem entirely. The footer behaved as intended, and the change corrected some wonky alignments. Hooray!
