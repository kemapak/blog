# CSS Coding Standards

# Table of Contents
* [Files & Directory:](#files--directory)
  * [CSS-01 - One CSS per View or Component:](#css-01---one-css-per-view-or-component)
  * [CSS-02 - File Naming Convention:](#css-02---file-naming-convention)
* [Style and Syntax](#style-and-syntax)
  * [CSS-03 - Class/Selector Names](#css-03---classselector-names)
  * [CSS-04 - Quotes](#css-04---quotes)
  * [CSS-05 - Semicolon](#css-05---semicolon)
  * [CSS-06 – Whitespace, Indentation & Line Length](#css-06--whitespace-indentation--line-length)
  * [CSS-07 - Curly Braces](#css-07---curly-braces-)
  * [CSS-08 - Comments](#css-08---comments)
  * [CSS-09 - Never Use !important:](#css-09---never-use-important)
  * [CSS-10 - Color Codes:](#css-10---color-codes)
  * [CSS-11 - Grouping Properties:](#css11---grouping-properties)
  * [CSS-12 - Box Model:](#css-12---box-model)
  * [CSS-13 - Promotion and Demotion:](#css-13---promotion-and-demotion)
  * [CSS-14 - Absolute Positioning and Floating:](#css-14---absolute-positioning-and-floating)
  * [CSS-15 - Overriding Core Classes:](#css-15---overriding-core-classes)
  * [CSS-16 – Do Not Write CSS](#css-16--do-not-write-css)

## Files & Directory:

### CSS-01 - One CSS per View or Component:
Create a dedicated CSS file for each application, view, or component.

> Do not create an empty CSS file if it is not needed

> Note: All CSS files will be bundled for runtime.

### CSS-02 - File Naming Convention:
File names should clearly describe what the file is and where it is used.
- All lowercase
- Words separated by hyphens (-)
- No abbreviations unless formally agreed upon

**Format**:
\[_name_\]*-_name_.css
([] = optional, * = zero or more)

**Examples**:
- helper.css
- override.css
- messages.css
- login.css
- user-profile.css
- button.css

## Style and Syntax

### CSS-03 - Class/Selector Names
All class/selector names should clearly describe what the file is and where it is used.
- All lowercase
- Words separated by hyphens (-)
- No abbreviations unless formally agreed upon

**Format**:
.\[common prefix\]*[-module name][-view name]*[-name]

**Example**:
- .xyz-settings
- .xyz-settings-container
- .xyz-settings-authentication-details
- .xyz-settings-authentication-confirm-button

### CSS-04 - Quotes
- Use **double quotes** for values requiring quotes.

**Example**:
```css
.xyz-banner {
    background-image: url("banner.jpeg");
}
```

### CSS-05 - Semicolon
- Always end property declarations with a semicolon.

**Example**:
```css
.xyz-container {
    color: #789ABC;
    margin-left: 5rem;
}
```

### CSS-06 – Whitespace, Indentation & Line Length
- Use 2-character tabs for indentation.
- 140-character maximum line length.
- Single space between property operator and value.
- Closing brace on its own line.
- Separate logical groups with blank lines.
- Never combine multiple declarations on one line.

**Example**:

**OK**
```css
.xyz-my-class {
    color: #789ABC; 
    margin-left: 0.5rem; 
    border-radius: 3px;
}
```

**Not OK**
```css
.xyz-my-class {color: #789ABC; margin-left: 0.5rem; border-radius: 3px;}
```

### CSS-07 - Curly Braces  
- Opening brace on same line as selector
- Closing brace on its own line
- Blank line between class definitions unless grouped with commas

**Example**:
```css
.xyz-my-class {
    color: #4EAA24;
}

.xyz-my-class-primary,
.xyz-my-class-secondary {
    text-align: center;
}
```

### CSS-08 - Comments
- **Comment only exceptions and things you cannot explain with code.**
- **Instead of adding a comment try to have better selector name.**
- **Do not comment unused code**, just remove it!
- If there is a **temporary or exception** case, add a TODO, the current date, and your name.
  - `/* TODO <Date> <Developer Name>: Explanation. */`
- Start with a space, uppercase letter, end with a period. Just like a regular sentence.
- Explain exceptions or overrides clearly

Example:

**OK**
```css

.xyz-list {
    /* TODO 11-11-2025 Kem: Disabled this code until the x functionality is ready. */
    /* background-color: blue;*/
    
    /* Workaround for Safari/Voiceover issue, that ignores the list markup. */
    list-style: "";
}

```

**Not OK**
```css

/* Page header styles. */
.xyz-container {
    background-color: azure;
    /* color: #234213; */
    /* padding: 1rem; */
}
```

### CSS-09 - Never Use !important:
- Never use `!important` unless approved by your lead developer
- Rely on CSS specificity and cascading.

> Note: Platform developers can rarely use `!important` when it is absolutely necessary.

### CSS-10 - Color Codes:
- Hex colors must use 6 digits, uppercase:

**Example**:

```css
.xyz-card {
    background-color: #CC33AA;
}
```

> Note: Always use CSS variables/tokens when available.

### CSS-11 - Grouping Properties:
- Avoid single-property utility classes unless widely reused.

**Example**: 

**OK**
```css
.pull-right {
    float: right;
}
```

**Not OK**
```css
.table-column-width-medium {
    width: 50%;
}
```

> Note: Common helper classes should be handled by the layout framework or your Platform team. You should never need to
> write them.

### CSS-12 - Box Model:
- Use border-box as much as possible, especially when using percentage-based widths/heights.

### CSS-13 - Promotion and Demotion:
- Do not convert inline elements into block elements or block elements into inline.
- Block → inline-block is allowed when needed for layout.
- Inline-block → block is allowed when needed for layout. (Usually for custom components)

### CSS-14 - Absolute Positioning and Floating:
Avoid absolute positioning and floats. If used, document justification with block comments.

### CSS-15 - Overriding Core Classes:
- Never override core classes directly.
- Use view-level wrappers for safe scoping

**Example**:
```html
<div class="example-wrapper">
     <button class="button">Click Me!</button>
</div>
```

```css
.example-wrapper .button {
    border-radius: 12px;
}
```

### CSS-16 – Do Not Write CSS
- Re-use common classes whenever possible.
- Study your layout framework or design system to avoid writing unnecessary CSS.

