# General Guidelines

- Users only see the DOM. Use correct HTML5 semantic elements.
- Use correct heading hierachy.
- Text elements should have a reasonable contrast ratio.
- Controls and media elements should have labels.
- These elements are focusable but either invisible or obscured by another element.
- The purpose of each link should be clear from the link text. Use title attribute.
- Meaningful images should not be used in element backgrounds.
- The web page should have a title that describes topic or purpose.
- Audio elements should have controls.
- ARIA state and property values must be valid.
- Elements with ARIA roles must use a valid, non-abstract ARIA role.
- Always require alt attribute for images and provide meaningful alt text. If not meaningful leave alt attribute empty, otherwise screen readers will read image url.
- role=main should only appear on significant elements.
- aria-labelledby attributes should refer to an element which exists in the DOM.
- Elements with ARIA roles must have all required attributes for that role.
- Video elements should use <track> elements to provide captions.
- Touch target sizes for mobile should be at least 44px square.
fallback text for icons
http://www.filamentgroup.com/lab/bulletproof_icon_fonts.html
- Logical tab order
- Apply focus state styles
- Don't use tables for visual layout. Use tables for data. Use CSS For layout.
- Use anchors and buttons for links, not divs or spans. If element not focusable by default, then focus element, ie dialogs. When closed, focus back to element that opened dialog.
- aria-expanded and aria-hidden attributes for tree navigation
- aria-activedescendant attribute to an autocomplete widget handler to tell adaptive technologies that the child elements have focus.
- All form fields should have an associated label, ie for="my-textfield".

# ARIA examples
Use arial roles
http://www.paciellogroup.com/blog/2010/10/using-wai-aria-landmark-roles/
http://checklist.crip.io/

```html
<header role="header">
  Site wide specific content e.g. logo, global search, navigation

  <nav role="navigation">
    <ul>
      <li>Nav item 1</li>
      <li>Nav item 2</li>
    </ul>
  </nav>
</header>

<main role="main">
  Your main content

  <div role="button">button</div>
</main>

<aside role="complementary">
  Secondary content
</aside>

<footer role="contentinfo">
  Footnote, copyright statement
</footer>
```

- arial roles indicate composite controls that do not have a native HTML equivalent
```html
<div tabindex="0" role="menuitem">Paste</div>
```

- landmark roles can be used to identify seperate areas of your app

```html
<section role="search">Search this site</section>
```

- aria states

```html
<div role="checkbox" aria-checked="true"></div>
```

- aria live for dynamic content

- arial-label for describing objects with no text like icons

