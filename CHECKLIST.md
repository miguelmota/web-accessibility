# Accessibility Checklist

Here are some general guidelines you can follow.

- Users only see the DOM. Use correct HTML5 semantic elements.
- Use correct heading hierachy.
- Text elements should have a reasonable contrast ratio.
- Controls and media elements should have labels.
- If elements are focusable make them visible and not obscured by another element.
- The purpose of each link should be clear from the link text. Use `title` attribute if necessary.
- Meaningful images should not be used in element backgrounds.
- The web page should have a title that describes topic or purpose.
- Audio elements should have controls.
- ARIA state and property values must be valid.
- Elements with ARIA roles must use a valid, non-abstract ARIA role.
- Always require `alt` attribute for images and provide meaningful alt text. If not meaningful leave alt attribute empty, otherwise screen readers will read image url.
- `role=main` should only appear on significant elements.
- `aria-labelledby` attributes should refer to an element which exists in the DOM.
- Elements with ARIA roles must have all required attributes for that role.
- Video elements should use `<track>` elements to provide captions.
- Have fallback text for icons
  - [Filament group - Bulletproof Accessible Icon Fonts](http://www.filamentgroup.com/lab/bulletproof_icon_fonts.html)
- Have a logical tab order.
- Apply focus state styles to make it clear element is focused.
- Don't use tables for visual layout. Use tables for data. Use CSS For layout.
- Use anchors and buttons for links, not divs or spans. If element not focusable by default, then focus element, ie dialogs. When closed, focus back to element that opened dialog.
- Use `aria-expanded` and `aria-hidden` attributes for tree navigation.
- Add `aria-activedescendant` attribute to an autocomplete widget handler to tell adaptive technologies that the child elements have focus.
- All form fields should have an associated `<label>` and `for` attribute, ie `for="my-textfield"`.
- Use landmark roles to identify seperate areas of your app.
  ```html
  <header role="header">
    Site wide specific content e.g. logo, global search, navigation
    <nav role="navigation">
    </nav>
  </header>

  <main role="main">
    Your main content
  </main>

  <aside role="complementary">
    Secondary content
  </aside>

  <footer role="contentinfo">
  </footer>
  ```
  ```html
  <section role="search">Search this site</section>
  ```
- Use aria roles indicate composite controls that do not have a native HTML equivalent.
  ```html
  <div tabindex="0" role="menuitem">Paste</div>
  ```
- Use aria roles to indicate element types.
  ```html
  <div role="button">button</div>
  ```
- Use aria states attributes.
  ```html
  <div role="checkbox" aria-checked="true"></div>
  ```
- aria live for dynamic content
- `aria-label` for describing objects with no text like icons.
  ```html
  <i class="nav-icon" aria-label="Navigation button"></i>
  ```
