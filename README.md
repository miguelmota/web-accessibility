# Web Accessibility

This document presents general guidelines to follow for making the web a more accessible place based on W3C web accessibility standards and best practices.

## Table of Contents

1. [Semantics and Layout](#semantics-and-layout)
1. [Dynamic Data](#dynamic-data)
1. [Focus Control](#focus-control)
1. [Data Tables](#data-tables)
1. [Forms](#forms)
1. [Color and Contrast](#color-and-contrast)
1. [CSS](#css)
1. [Links](#links)
1. [Images](#images)
1. [Animations](#animations)
1. [Audio and Video](#audio-and-video)
1. [Dialogs](#dialogs)
1. [Frames](#frames)

## Semantics and Layout

- Screen readers only see the DOM. Use correct HTML5 semantic elements. <sup>[more](http://webaim.org/techniques/screenreader/)</sup>

- Use correct heading hierachy since this is usually the primary way users of screen readers quickly navigate page. <sup>[more](http://www.w3.org/WAI/tutorials/page-structure/headings/)</sup>

- The web page should have a title that describes topic or purpose. <sup>[more](http://www.w3.org/WAI/eval/preliminary.html#title)</sup>

- Always ensure elements that use Aria provide non-aria fallback accessible content because not all assistive technologies support ARIA or fully implement the spec. <sup>[more](https://www.webaccessibility.com/best_practices.php?technology_platform_id=255)</sup>

- Don't use tables for visual layout. Use tables for data. Use CSS For layout. Use `role="presentation"` for layout if you must. <sup>[more](http://www.w3.org/TR/aria-in-html/#presentation)</sup>

- Elements with ARIA roles must have all required attributes for that role.

- Use landmark roles to identify separate sections of your app.
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

- `role=main` should only appear on significant elements.

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

- `aria-label` for describing objects with no text like icons.

    ```html
    <i class="nav-icon" aria-label="Navigation button"></i>
    ```

- `aria-labelledby` to reference a label.

  ```html
  <div id="mylabel" class="hidden">My Progressbar</div>
  <div role="progressbar" aria-labelledby="mylabel"></div>
  ```
- `aria-labelledby` attributes should refer to an element which exists in the DOM.

- Use aria roles indicate composite controls that do not have a native HTML equivalent.

    ```html
    <div tabindex="0" role="menuitem">Paste</div>
    ```
- Use aria roles to indicate element types.

    ```html
    <div role="button">button</div>
    ```
- Handle artificial checkbox states with aria roles.

    ```html
    <div role="checkbox" aria-checked="true">checkbox</div>
    ```

- Handle artificial radio buttons.

  ```html
  <label id="radio_label">
  <ul role="radiogroup" aria-labelledby="radio_label">
    <li role="radio" aria-checked="true"></li>
    <li role="radio" aria-checked="false"></li>
  </ul>
  ```

- Handle artificial select list.

  ```html
  <ul role="selectable">
    <li aria-role="option" aria-selected="true"></li>
  </ul>
  ```

- `role="progressbar"` for progress bars. Provide accessible names for progress bars and meters.

  ```html
  <div role="progressbar" aria-valuenow="20" aria-valuemin="0" aria-valuetext="Step 2: Copying files... " aria-valuemax="100">
    Step 2: Copying files...
  </div>
  ```

## Dynamic Data

- Avoid forced focus changes that are not user-initated or user unaware of because users heavily rely on keyboard navigation and need to be aware of where focus is placed at all times in order to properly navigate.
- Ensure the user-initiated content updates (ie via AJAX) are programmatically focused in order for scren readers to read updated content.

- Ensure auto-updating content can be paused, stopped, or hidden (ie stock ticker) because it can be distracting to users on screen readers.

- Ensure user and screen reader is aware of content changes that occur without explicit user knowledge (ie select menu updating a div).

- Ensure screen reader is alerted when an element state is changed

- Use aria landmarks, atomic, and busy attributes for specifying accessible attributes and state.

- `aria-live` for dynamic content. Use `assertative` value to interrupt user, or `polite` to wait until user is done with current task.

    ```html
    <output class="result" aria-live="polite"></output>
    ```

- Explicitly label live region.

- Provide additional long descriptions where a label is not sufficient for describing a live region

- Determine if live regions need to be explicitly alerted. ex scrolling marquee no, chat user left yes

## Focus Control

- Avoid using event handlers that trigger focus change because it can produce significant challenges to users with disabilities.

- Ensure interactive elements can be visually distinguished from static elements.

- Ensure keyboard focus is visually indicated.

- Ensure new windows are opened only when user initiated because users with disabilities may become disoriented and not realiz focus has changed.

- Ensure elements that are focusable are visible and not obscured by another element.

- Ensure tabs have a logical order. Use `tabindex` to specify order.

  ```html
  <button tabindex="0"></button>
  ```

## Data tables

- Avoid nested tables because users with assistive technology will have a hard time navigating between cells and understanding what table they are viewing.

- Ensure no tables are used in table headers because screen readers might not be able to associate headers with table data.

- Ensure table `th` have an `id` or `scope` attribute that associate with table data `headers` attribute so screen readers can associate relationships.

- Ensure complex data table row header cells that act as header cells for a row or cell define the `scope` attribute.

- Ensure table header cells are not blank because screen readers will not be able to identify the table column.

- Ensure table captions are explicitly provided via `caption` element instead of `summary` attribute because captions should be visually on-screen.

## Forms

- Avoid improper nesting of form elements (ie checkbox within link) because users might have a hard time identifying which element is focused.

- Avoid using placeholder values as a replacement for input label because placeholders are meant to provide short hints to aid user with data entry and may not be available to screen readers.

- All form fields should have an associated `<label>` and `for` attribute, ie `for="my-textfield"`.

- Ensure accessible usage of time based session and timed responses because users with disabilities take longer to fill out forms.

- Ensure CAPTCHAs are accessibile both visually and audibly.

- Ensure each `fieldset` has a `legend` which provides contextual information about the form.

- Ensure field constraints are clearly indicated via `label` elements (ie Birthday YYYY/MM/DD).

- Ensure option elements in large lists are grouped with `optgroup`.

- Ensure related radio buttons are grouped by `name` attribute.

- Ensure WYSIWYG (What You See Is What You Get) rich text editors are directly accessibile or provide an alternative means of entering text.

- Ensure that instructive text is placed at the beginning of the form or before the input fields because users might not encounter the descriptive text before interacting with field.

- Provide clear indication of errors in form fields.

- Provide an indication of current location in search results such as displaying number search results on page and total search results count.

- Provide suggestions for error messages when known to aid impaired users in completing the form before giving up.

## Color and Contrast

- Ensure color is not the sole means of communicating information (error message, link, selection) because color blind or poor visioned users will find the page unusable (ie using only color to determine linked vs non-linked text. error messages normal font size vs bold).

- Ensure contrast between text foreground and background color because color deficient users might not be able to distinguish the text.

## CSS

- Avoid use of before, after pseudo selectors for non-decorative content because screen readers can't access that content.

- Ensure documents are readable without stylesheets is correct because vision deficient users might disable stylesheets and increase font size.

- Ensure reading order of content is correct when stylesheets are turned off.

- Ensure screen reader specific content is rendered off-screen (ie position absolute off-screen) rather than hidden or not displayed because screen readers ignore those elements.

- Ensure text can be resized up to 200% without assistive technology. On mobile websites do not disable ability to pinch and zoom to enlarge text because vision deficient users benefit from this.

- Ensure text equivalent for icon fonts are provided because screen readers do not know what symbol (ie a heart) the font represent.

- Fallback text for icons
  - [Filament group - Bulletproof Accessible Icon Fonts](http://www.filamentgroup.com/lab/bulletproof_icon_fonts.html)

- Ensure fonts use relative sizing because with absolute sizing the user might not be able to increase font size and relative sizing ensures fonts are relative to user's browser settings.

## Links

- Use anchors and buttons for links, not divs or spans because these elements are not focusable and clickable by default.

- The purpose of each link should be clear from the link text. Use `title` attribute if necessary. Always include `href` to make it clickable with keyboard.

## Images

- Always require `alt` attribute for images and provide meaningful alt text. If not meaningful leave alt attribute empty, otherwise screen readers will read image url.

- Ensure complex images provide sufficient description outside of `alt` text.

- Ensure CSS background images that convey meaning have text equivalents since these images can't have an alt attribute.

- Always use text instead of images of text because users have ability to adjust styling of font.

- Provide mathemataical formulas in appropriate markup, such as MathML, to describe math functions so screen readers can relay information properly.

## Animations

- Avoid blinking and flashing elments that flash three times a second or more since it may trigger epileptic seizures in individuals with photosensitive epilepsy.

- Ensure to add option to disable content "fade-in" transitions, provide non-animated method, provide a way to step through animations, or provide option to show content all at once, because screen readers might start rendering screen content before animation completes and text not visible will not be displayed.

## Audio and Video

- Ensure autoplay media can be controlled within containing page.

- Ensure controls and media elements have readable labels.

- Ensure embedded element provide a meaningful text equivalent (ie transcripts).

- Ensure embedded objects are fully accessible via all types of input such as keyboard.

- Video elements should use `<track>` elements to provide captions.

## Dialogs

- If element not focusable by default, then focus element (ie dialogs). When closed, focus back to element that opened dialog.

- `aria-haspopup` for dialog modals.

  ```html
  <button aria-haspopup="true"></button>
  <div role="dialog" arial-label="Modal" tabindex="-1"></div>
  ```

## Frames

- Ensure iframes have a width and height of `0` to hide properly from screen readers and add title attribute indicating the iframe is empty (ie title="Empty")

# Resources

- [Google Web Accessibility Course](https://webaccessibility.withgoogle.com/course)
- [The Accessibility Project](http://a11yproject.com/)
- [Web Accessibility Best Practices](https://www.webaccessibility.com/best_practices.php)
- [MDN ARIA](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA)
- [Accessible Web Components with Polymer](https://www.polymer-project.org/0.5/articles/accessible-web-components.html)
- [Smashing Magazine - The WAI Forward](http://www.smashingmagazine.com/2014/07/09/the-wai-forward/)
- [The Paciello Group - Using WAI ARIA Landmark Roles](http://www.paciellogroup.com/blog/2010/10/using-wai-aria-landmark-roles/)
- [The Paciello Group - Accessibility Testing Tools](http://www.paciellogroup.com/blog/2014/10/accessibility-testing-tools-updated/)
- [W3 Web Accessibility Initiative (WAI)](http://www.w3.org/WAI/)
  - [W3 Web Content Accessibility Guidelines (WCAG) Overview](http://www.w3.org/WAI/intro/wcag)
  - [W3 Introduction to Web Accessibility](http://www.w3.org/WAI/intro/accessibility.php)
  - [W3 WAI-ARIA Overview](http://www.w3.org/WAI/intro/aria.php)
  - [W3 WAI-ARIA The Roles Model](http://www.w3.org/TR/wai-aria/roles)
  - [W3 WAI-ARIA Taxonomy](http://www.w3.org/TR/wai-aria/rdf_model.html)
  - [W3 WAI-ARIA States and Properties](http://www.w3.org/TR/wai-aria/states_and_properties)
  - [W3 WAI-ARIA Authoring Practices](http://www.w3.org/TR/wai-aria-practices/)
  - [W3 Aria in HTML](http://w3c.github.io/aria-in-html/)
  - [W3 Web Design - Accessibility](http://www.w3.org/standards/webdesign/accessibility)

# Extensions
- [Accessibility Developer Tools](https://chrome.google.com/webstore/detail/accessibility-developer-t/fpkknkljclfencbdbgkenhalefipecmb)
- [ChromeVox - Screen Reader](https://chrome.google.com/webstore/detail/chromevox/kgejglhpjiefppelpmljglcjbhoiplfn)
 - [Video: Making Accessible Web Apps Using HTML5 and ChromeVox](https://www.youtube.com/watch?v=x18vEEfpK3g)
- [ChromeVis - Magnify and change the color of any selected text](https://chrome.google.com/webstore/detail/chromevis-by-google/halnfobaneppemjnonmmhngbfifnafgd)
- [Lois TTS US English - Lois is a female US English text-to-speech (TTS) voice extension](https://chrome.google.com/webstore/detail/lois-tts-us-english/jcabofbhfighebggomnamjankeaplmhn)

# Tools
- [A11y - Accessibility audit tooling for the web](https://github.com/addyosmani/a11y)

# License

MIT
