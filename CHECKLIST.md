# Accessibility Checklist

Here are some general guidelines to follow.

- Screen readers only see the DOM. Use correct HTML5 semantic elements.
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

  ```html
  <button tabindex="0"></button>
  ```
- Apply focus state styles to make it clear element is focused.
- Don't use tables for visual layout. Use tables for data. Use CSS For layout. Use `role="presentation"` for layout if you must.
- Use anchors and buttons for links, not divs or spans. If element not focusable by default, then focus element, ie dialogs. When closed, focus back to element that opened dialog.
- Use `aria-expanded` and `aria-hidden` attributes for tree navigation.

  ```html
    <nav role="menu" aria-expanded="true">
       <div role="menuitem">Item one</div>
       <div role="menuitem">Item two</div>
    </nav>
  ```

  The `menu` role can have any of the following states

  ```
  aria-activedescendant aria-atomic aria-busy aria-controls aria-describedby aria-disabled aria-dropeffect aria-expanded aria-flowto aria-grabbed aria-haspopup aria-hidden aria-invalid aria-label aria-labelledby aria-live aria-owns aria-relevant
  ```
- Add `aria-activedescendant` attribute to an autocomplete widget handler to tell adaptive technologies that the child elements have focus.
- All form fields should have an associated `<label>` and `for` attribute, ie `for="my-textfield"`.
- Use landmark roles to identify seperate areas of your app.
  ```html
  <body role="application">
    <header role="banner">
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
  </body>
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
    <div role="checkbox" aria-checked="true">checkbox</div>
    ```
- `aria-live` for dynamic content. Use `assertative` value to interupt user, or `polite` to wait until user is done with current task.

    ```html
    <output class="result" aria-live="polite"></output>
    ```
- `aria-label` for describing objects with no text like icons.

    ```html
    <i class="nav-icon" aria-label="Navigation button"></i>
    ```

- `aria-labelledby` to reference a label.

  ```html
  <div id="mylabel" class="hidden">My Progressbar</div>
  <div role="progressbar" aria-labelledby="mylabel"></div>
  ```

- `role="progressbar"` for progress bars

  ```html
  <div role="progressbar" aria-valuenow="20" aria-valuemin="0" aria-valuetext="Step 2: Copying files... " aria-valuemax="100">
    Step 2: Copying files...
  </div>

- `aria-haspopup` for dialog modals.

  ```html
  <button aria-haspopup="true"></button>
  <div role="dialog" arial-label="Modal" tabindex="-1"></div>
  ```
