# HTML Coding Standards

## Table of Contents
* [Files and Directory](#files-and-directory)
  * [HTML-01 One HTML per View or Component](#html-01-one-html-per-view-or-component)
  * [HTML-02 - HTML File Naming Convention](#html-02---html-file-naming-convention)
* [Style and Syntax](#style-and-syntax)
  * [HTML-03 – Element and Attribute Naming](#html-03--element-and-attribute-naming)
  * [HTML-04 – Attribute Quotes](#html-04--attribute-quotes)
  * [HTML-05 – Tag Closures](#html-05--tag-closures)
  * [HTML-06 – Custom Attributes](#html-06--custom-attributes)
  * [HTML-07 – Whitespace, Indentation, Line Length](#html-07--whitespace-indentation-line-length)
  * [HTML-08 – Comments](#html-08--comments)
  * [HTML-09 – ID Naming Conventions](#html-09--id-naming-conventions)
  * [HTML-10 – Do not use `type="text/javascript"` in `<script>` tags](#html-10--do-not-use-typetextjavascript-in-script-tags)
  * [HTML-11 – Do no use Inline Styles](#html-11--do-no-use-inline-styles)
  * [HTML-12 – Avoid JavaScript in Markup](#html-12--avoid-javascript-in-markup)
  * [HTML-13 – Use Custom Web Components (Modularize your code!)](#html-13--use-custom-web-components-modularize-your-code)
  * [HTML-14 – Block vs Inline Elements](#html-14--block-vs-inline-elements)
  * [HTML-15 – USE Semantic HTML Tags](#html-15--use-semantic-html-tags)
  * [HTML-16 – Markup Validation](#html-16--markup-validation)


## Files and Directory

### HTML-01 One HTML per View or Component
Create a dedicated HTML file for each application, view, or component.

> Do not create an empty HTML file if it is not needed

### HTML-02 - HTML File Naming Convention
File names should clearly describe what the file is and where it is used.
- All lowercase
- Words separated by hyphens (-)
- No abbreviations unless formally agreed upon

**Format**:
```text
[name-]*name.html
```

`[] = optional, * = zero or more`

**Examples**:
- home.html
- phone-catalog.html
- index.html

## Style and Syntax

### HTML-03 – Element and Attribute Naming
- All tag names and attribute names **must be lowercase**.
- Multi-word names **must use hyphens (-)**.

**Examples**:
```html
<div class="button-primary"></div>
<custom-component type="alpha" data-usage="beta"></custom-component>
<bar-chart series="[]" settings="{}"></bar-chart>
```
### HTML-04 – Attribute Quotes
- Attribute values **must use double quotes**.

**Examples**:
```html
<ul id="desertMenu" class="delicious-list">
  <li>Baklava</li>
  <li class="recommended">Cannoli</li>
  <li>Ice Cream</li>
</ul>
```

### HTML-05 – Tag Closures
- All elements **must be properly closed**.
- Elements with content require closing tags.
- Self-contained (“void”) elements must end with `/>`.

**Examples**:
```html
<p>Some content</p>
<custom-element></custom-element>
<input type="text" class="form-input" />
```

### HTML-06 – Custom Attributes
- Prefix all custom attributes with `data-` for native HTML tags.
- Custom components attributes do not need to use `data-` prefix.

**Examples**:
```html
<input type="range" min="0" max="100" value="97" data-alarm="3" data-notify="core-gl" />
<custom-card type="secondary" collapsible="true">
  <p slot="body">Hi There!</p>
</custom-card>
```

### HTML-07 – Whitespace, Indentation, Line Length
- Use 2-space indentation.
- Max 120 characters per line before wrapping.
- No space around `=` in attributes (`id="menu"`, **not** `id = "menu"`).
- Separate logical blocks with one blank line.

**Examples**:
```html
<header>
  <h1>Hello</h1>
</header>

<nav>
  <menu>
    <li>main</li>
    <li>production</li>
  </menu>
</nav>
```

### HTML-08 – Comments
- **Comment only exceptions and things you cannot explain with code.**
- **Do not comment unused code**, just remove it!
- If there is a **temporary or exception** case, add a TODO, the current date, and your name.
    - `<!-- TODO <Date> <Developer Name>: Explanation. -->`
- Start with a space, uppercase letter, end with a period. Just like a regular sentence.
- Explain exceptions or overrides clearly

**Examples**:
```html
<!-- This is an HTML comment. -->

<!--
This is a multiline
HTML comment.
-->
```

### HTML-09 – ID Naming Conventions
- ID names **must clearly describe** what it is and where it is used.
- Start with lowercase
- Words separated with camelcase
- No abbreviations unless formally agreed upon

**Format**:
```text
[name]*Name
```

**Examples**:
```html
<custom-card id="customerChart0867"></custom-card>
<section id="firstSeatSelection"></section>
```

### HTML-10 – Do not use `type="text/javascript"` in `<script>` tags
- This is deprecated do not use!

**Examples**: 
```html
<!-- Not OK -->
<script type="text/javascript" src="../src/common/util.js"></script>
```

### HTML-11 – Do no use Inline Styles
- Avoid using inline `style` attribute. Use CSS classes instead.

**Examples**:
```html
<!-- Not OK -->
<div style="margin-top:2rem;"></div>

<!-- OK -->
<div class="page-top-block"></div>
```

### HTML-12 – Avoid JavaScript in Markup
- Avoid embedding JavaScript code in HTML attributes (`onclick`, etc.). Unless you are using a framework that requires it.
- Configuration-only initialization is OK.

**Examples**:
```html
<! Avoid -->
<button onclick="avoidDoingThis();"></button>
```

### HTML-13 – Use Custom Web Components (Modularize your code!)
- This is the best thing happen to web since AJAX!
- Move complex markup into web components to **simplify** and **modularize** your code.
- Build **reusable components**.
- **Extend HTML elements** to do more things.

### HTML-14 – Block vs Inline Elements
- **Do not** place block elements inside inline elements.
- Wrap inline elements inside suitable block elements instead.

**Examples**:
```html
<!-- Not OK -->
<span>
  <section>My Section</section>
</span>

<!-- Not OK -->
<button>
  <div>Click Me</div>
</button>

<!-- Not OK, <p> cannot contain any block-level elements. -->
<p>
  <div>Notes</div>
</p>

<!-- OK -->
<p>
  <span>Hi</span>
</p>

<!-- OK -->
<div>
  <button>Click Me</button>
</div>
```

### HTML-15 – USE Semantic HTML Tags
- Do not use deprecated tags (e.g. `<font>`).
- Use semantic tags correctly:
- `<header>` for headers.
- `<main>` for the main content.
- `<foooter>` for footers.
- `<nav>` and `<menu>` for navigation
- `<strong>` for bold text.
- `<em>` emphasized italic text.
- `<dialog>` for dialogs.
- `<section>` for each section in the page.
- `<aside>` for side content.
- `<article>` for content that is independent.
- `<details> and <summary>` for expandable/collapsible content.
- `<div>` use for generic containers, not everything. 

### HTML-16 – Markup Validation
- Validate your markup regularly! [W3C VALIDATOR](https://validator.w3.org/#validate_by_input)