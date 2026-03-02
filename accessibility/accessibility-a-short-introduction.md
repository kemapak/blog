# Accessibility (a11y) a short introduction

What is accessibility? Why is it important? As an engineer, you might have been asked to make sure you build your
application accessible. How can you do that? This document will get you started and give you some tips, show you some
examples. Also, I will share some great resources, both books and websites.

> Note: This document only covers web accessibility.

First, I have to say accessibility is not a requirement, it is a moral obligation. As a professional engineer, as a
craftsman, you have to build an application that is properly functioning, bug free, and accessible.

Second, I hate politics being brought into accessibility. It is **not inclusive design** or **inclusive engineering**,
it is **accessible design** and **accessible engineering**. No one is intentionally excluding anyone. We are
building software for everyone! Because this is the right thing to do, because we are professionals.

## Table of Contents
- [Terms](#terms)
- [What areas of accessibility we code for?](#what-areas-of-accessibility-we-code-for)
- [Tools](#tools)
- [Semantic tags](#semantic-tags)
- [Custom Tags (Web Components)](#custom-tags-web-components)
- [ARIA or ROLE](#aria-or-role)
- [Page structure and organization](#page-structure-and-organization)
  - [Headings](#headings)
  - [Landmarks](#landmarks)
- [Components and tags](#components-and-tags)
  - [Lists](#lists)
  - [Links](#links)
  - [Page Title](#page-title)
  - [Table](#table)
  - [iframe](#iframe)
  - [Images](#images)
    - [Types](#types)
    - [Tags](#tags)
- [Color Contrast & Use of Color](#color-contrast--use-of-color)
- [Name, Role, Value](#name-role-value)
- [Tabindex](#tabindex)
  - [Tabindex Values](#tabindex-values)
  - [Best Practices](#best-practices)
- [Notifications `aria-live`](#notifications-aria-live)
  - [ARIA Live Region Politeness Levels](#aria-live-region-politeness-levels)
  - [Common Use Cases](#common-use-cases)
  - [Important Attributes](#important-attributes)
  - [Best Practices](#best-practices-1)
  - [Example: Complete Notification System](#example-complete-notification-system)
- [Skipping to Main Content](#skipping-to-main-content)
  - [How It Works](#how-it-works)
  - [Best Practices](#best-practices-2)
  - [Alternative: Multiple Skip Links](#alternative-multiple-skip-links)
  - [Common Mistakes to Avoid](#common-mistakes-to-avoid)
- [Testing](#testing)
  - [Text Spacing](#text-spacing)
  - [General markup, color and structural issues](#general-markup-color-and-structural-issues)
  - [Keyboard](#keyboard)
  - [Screen reader](#screen-reader)
- [References](#references)

## Terms

- **a11y**: Accessibility, there are eleven (11) characters between a and y, therefore a11y.
- **ARIA**: Accessible rich internet applications.
- **AT**: Assistive Technologies (Screen readers).
- **WAI**: Web Accessibility initiative.
- **WCAG**: Web Content Accessibility Guidelines.

## What areas of accessibility we code for?

1. Keyboard only navigation (Users that cannot use a mouse or a trackpad, because of motor disabilities)
2. Screen readers (For blind users)
3. Color contrast (Issues with color blindness, and low vision)
4. Blinking or flickering (Causes severe distractions and can trigger seizures in people with photosensitive epilepsy)
5. Complex markup (Cognitive overload because of complex user interface or content)
6. Proper markup and page structure (Visually pleasing pages does not translate to usable pages without proper markup and structure)

## Tools

There are quite a few tools we can use to test a11y of our web pages. 
- Keyboard navigation, using tabs, arrow, enter, space, arrow via our keyboard.
- [AXE tool](tools/axe.md), to test general structure, tags, properties and color contrast.
- [Text spacing bookmarklet](tools/text-spacing-bookmarklet.md), to test text spacing.
- Screen readers (AT), [VoiceOver](https://www.apple.com/accessibility/vision/voiceover/) for macOS (built-in), [JAWS](https://www.freedomscientific.com/products/software/jaws/) (Commercial) and [NVDA](https://www.nvaccess.org/) (Open source) for Windows OS.

## Semantic tags

Do learn and use semantic tags when building your applications and site HTML. Just doing this avoids most of the 
accessibility defects and make your code more robust. I do see that most of the engineers do not know how to build 
markup properly. Even in some famous frameworks, design libraries are build incorrectly. `<div>` tags are used 
everywhere, anywhere without thinking or checking if there is a semantic tag.  

Proper markup helps:
* Heading tags allow screen reader users to skip to page headings for efficient navigation.
* Images with concise and relevant alt text enhances user experience and supports content.
* Lists allow users to jump to blocks of information and to individual list items.
* Links that are clearly defined help users understand their purpose.
* Landmarks make the page easier to navigate.
* Title conveys the browser tab that has focus and brief information about the page.

Learn what are the semantic tags and how to use them.
- `<header>` for headers.
- `<main>` for the main content.
- `<footer>` for footers.
- `<nav>` and `<menu>` for navigation
- `<strong>` for bold text.
- `<em>` emphasized italic text.
- `<dialog>` for dialogs.
- `<section>` for each section in the page.
- `<aside>` for side content.
- `<article>` for content that is independent.
- `<details> and <summary>` for expandable/collapsible content.
- `<div>` use for generic containers, not everything.


- **Reference**: [W3C Semantics - WCAG 1.3.1 - Info and Relationships](https://www.w3.org/WAI/WCAG21/Understanding/info-and-relationships.html)

## Custom Tags (Web Components)

Web components are an extremely powerful tool that will help to modularize our pages and create custom tags. That said,
it brings a lot of responsibility to make sure they are fully accessible. I highly recommend checking the W3C reference 
and following their established patterns.

**Key considerations for accessible web components:**
- Ensure proper keyboard navigation support (tab, enter, space, arrow keys).
- Provide appropriate ARIA roles, labels, and states when semantic HTML isn't sufficient.
- Announce dynamic content changes to screen readers using `aria-live` regions.
- Maintain focus management when components open, close, or change state.
- Test with screen readers and keyboard-only navigation.
- Follow W3C design patterns for common interactive components (carousel, tabs, notifications, etc.).

- **Patterns**: [W3C ARIA Authoring Practices Guide (APG) Patterns](https://www.w3.org/WAI/ARIA/apg/patterns/)
- **Reference**: [W3C Web Components and Accessibility](https://www.w3.org/WAI/ARIA/apg/practices/read-me-first/)

## ARIA or ROLE

If you use semantic tags you can mostly avoid using aria or role attributes. Even more important is not use them 
incorrectly.

- Use `<button>` tag instead of `<div role="button">`.

**Example**:
```html
<!-- Incorrect -->
<div role="button">Show settings</div>


<!-- Correct -->
<button>Show settings</button>
```

- Use `<h1 through 6>` tags instead of `role="heading"` with `aria-level`.

**Example**:
```html
<!-- Incorrect -->
<div role="heading" aria-level="3"></div>

<!-- Correct -->
<h3></h3>
```

- Use `<nav>` tag instead of `<div role="navigation">`.

**Examples**:
```html
<!-- Incorrect -->
<div role="navigation">
  <a href="main.html">Home</a>
  <a href="catalog.html">Catalog</a>
  <a href="settings.html">Settings</a>
</div>
  
<!-- Correct -->
<nav>
  <a href="main.html">Home</a>
  <a href="catalog.html">Catalog</a>
  <a href="settings.html">Settings</a>
</nav>  
```

- Use `<menu>` tag instead of `<ul role="menu">`.

**Example**:
```html
<!-- Incorrect -->
<ul role="menu">
  <li>Home page</li>
  <li>Dominican cigars</li>
  <li>Nicaraguan cigars</li>
  <li>Honduran cigars</li>
  <li>Cuban cigars</li>
</ul>

<!-- Correct -->
<menu>
  <li>Home page</li>
  <li>Dominican cigars</li>
  <li>Nicaraguan cigars</li>
  <li>Honduran cigars</li>
  <li>Cuban cigars</li>
</menu>
```

- Use Anchor `<a>` tag with `href` attribute should be used instead of custom links with `role="link"`.

**Example**:
```html
<!-- Incorrect -->
<button role="link" onclick="window.location.href=https://softwarenotes.net">Software Notes</button>

<!-- Correct -->
<a href="https://softwarenotes.net">Software Notes</a>
```

- Sometimes using the `role` attribute is completely unnecessary. Just by using semantic tag will be enough.

**Example**:
```html
<!-- Incorrect -->
<a href="https://www.softwarenotes.net" role="link">SoftwareNotes</a>

<!-- Correct -->
<a href="https://softwarenotes.net">Software Notes</a>
```

- Do not use ARIA roles to change a semantic HTML control..

**Example**:
```html
<!-- Incorrect -->
<div role="footer">....<div>

<!-- Correct -->
<footer>...</footer>

<!-- Incorrect -->
<button onclick="window.location.href=https://softwarenotes.net" role="link">SoftwareNotes</button>
  
<!-- Correct -->
<a href="https://softwarenotes.net">Software Notes</a>
```

- Do not use `aria-label` attribute if the `label` and `aria-label` values are the same.

```html
<!-- Incorrect -->
<label for="firstName" aria-label="First Name">First Name:</label><input type="text" id="firstName" />

<!-- Correct -->
<label for="firstName" >First Name:</label><input type="text" id="firstName" />
```

- **Reference**: [W3C ARIA in HTML](https://www.w3.org/TR/html-aria/)

## Page structure and organization

### Headings

Each page should have one level-one heading. A level-one heading signals the start of the heading structure of the 
page and the beginning of the main content.
- Heading structure should follow a hierarchical order.
- Nest headings sequentially.
- Avoid skipping heading levels *unless starting a new section*.
- Use HTML rather than role="heading" and aria-level.
- Create heading text that is concise and summarizes the general purpose of the page.
- Heading tags should not be used to style text.

> Please note there could only one `<h1>` per page.

```html
<h1>Start of the page heading structure</h1>

<h2>Don't skip heading levels</h2>
<h3>Heading levels are sequential</h3>
<h4>Use heading levels 1-6</h4>

<h2>Heading levels can skip when starting a new section</h2>
```

- **Reference**: [W3C Headings](https://www.w3.org/WAI/tutorials/page-structure/headings/)

### Landmarks

The main landmark identifies the primary page content and simplifies screen reader navigation.
- **Banner** `<header>`: typically, at the beginning of the page. Contains navigation elements such as menus.
- **Main landmark** `<main>`: wraps the main content area between the header and footer. Each page should have one main landmark.
- **Navigation landmarks** `<nav>`: used to create regions for groups of links or blocks of content. Name nav regions use aria-label or aria-labelledby. 
- **Complementary landmark** `<aside>`: can be used for content that supports the page, but if separated, can stand alone and still maintain its purpose.
- **Content Info landmark** `<footer>`: contains info about the business or site, such as links to a contact page, social media and so forth
- **Region landmark**: Can be used to indicate a custom landmark. Usually we need to use the `<section>` tag with role="region" and with aria-label or aria-labelledby property set.

```html
<!DOCTYPE html>

<html lang="en">
 <head>
   <title>Page | Site</title>
 </head>
 <body>
  <header>Banner Menu</header>
  
  <nav>Left nav</nav>
  
  <main>
   <aside class="complementary">Sidebar</aside>
  </main>
  
  <footer>Bottom Navigation</footer>
 </body>
</html>

```

- **Reference**: [W3C ARIA Landmarks Example](https://www.w3.org/WAI/ARIA/apg/patterns/landmarks/examples/general-principles.html)
- **Reference**: [W3C Semantics - WCAG 1.3.1 - Info and Relationships](https://www.w3.org/WAI/WCAG21/Understanding/info-and-relationships.html)

## Components and tags

### Lists
Items that indicate a relationship should be semantically grouped.
- Lines or blocks of text, related links or objects such as images that are visually grouped should be marked-up using HTML list elements.
- Use ordered, unordered or definition list structure.

> Very important note: There is a Safari/VoiceOver defect that skips styled lists. To overcome this, instead of setting the `list-style: none;` you can set `list-style-type: "";`.

```html
<!-- Ordered list markup -->
<ol>
  <li>Item 1</li>
  <li>Item 2</li>
</ol>

<!-- Unordered list markup -->
<ul>
  <li>Item 1</li>
  <li>Item 2</li>
</ul>
```

### Links

Links that indicate a relationship to each other should be grouped.
For users of assistive technologies like screen readers, grouping related links can make it easier to locate and use them.
- Use ‹nav> to group related links.
- Add list markup.
- Use aria-label or aria-labelledby to name the nav so the purpose can be easily understood.

> Group related links using the nav element.

```html
<nav aria-label="Explore NASA">
  <a href="https://www.nasa.gov ">NASA Home Page</a>
  <a href="https://www.nasa.gov/images/ ">NASA Image of the Day</a>
  <a href="https://www.nasa.gov/mars-rovers/">Mars Rovers</a>
</nav>

<style>
  /* This is for demo purposes, make sure all your CSS rules are declared in external CSS files. */
  ul li {list-style-type: none;}
</style>
<nav aria-label="Help with sign in.">
  <ul>
    <li><a href="[URL]">Forgot your username</a></li>
    <li><a href="[URL]">Forgot your password</a></li>
  </ul>
</nav>
```

- **Reference**: [W3C Grouping related links using the nav element](https://www.w3.org/WAI/WCAG21/Techniques/html/H97)

### Page Title
Web pages should have clear, descriptive titles.
Page titles help users understand content and get oriented within the browser.
1. Indicate the purpose of the page.
2. Add location information.

```html
<head>
  <title>Identify the page subject | Identify the site</title>
</head>
```

**Example**:
```html
<!-- Correct -->
<title>Sign In Page | CoffeeDrinks.com</title>

<!-- Incorrect -->
<title>Page 3</title>
```

- **Reference**: [W3C Page Titled - Level A](https://www.w3.org/WAI/WCAG21/Understanding/page-titled.html)
- **Reference**: [W3C Providing descriptive titles for web pages](https://www.w3.org/WAI/WCAG21/Techniques/general/G88)

### Table
```html
<!-- Simple table. Note that complex tables should have id + headers -->

<table>
  <thead>
    <tr>
      <th scope="col">Purchase Date</th>
      <th scope="col">Name</th>
      <th scope="col" >Measure</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">12/31/2021</th>
      <td>Name 1</td>
      <td>1 Kilo</td>
    </tr>
    <tr>
      <th scope="row">02/12/2022</th>
      <td>Name 2</td>
      <td>2 Kilos</td>
    </tr>
  </tbody>
</table>
```

- **Reference**: [W3C F91: Failure of Success Criterion 1.3.1 for not correctly marking up table headers](https://www.w3.org/TR/WCAG20-TECHS/F91.html)

### iframe
- Always name the iframe using the title attribute.
- The title should concisely describe the purpose.

```html
<iframe title="Visit our registration info page." src="https://softwarenotes.net"></iframe>
```

- **Reference**: [W3C H64: Using the title attribute of the frame and iframe elements](https://www.w3.org/TR/WCAG20-TECHS/H64.html)

### Images
Image tags must be accessible!

#### Types

**Informative**
- Represents concepts or information.
- Supplements or supports textual content.
- Use alt text to make it accessible to assistive technologies.
  
**Decorative**
- Adds decoration to the page.
- Does not convey info that is essential to understanding the purpose of the content.
- Use null alt text `alt=""` so assistive technologies will ignore
  
**Images of text - antipattern**
- Text that is part of an image and cannot be changed or edited.
- The alt text should contain the same words as the image.
  
**Complex**
- Graphs, diagrams, inaccessible flowcharts.
- Convey using alt text as well as a full text equivalent adjacent to the image.

#### Tags
  
**`<img>`**
- Every `<img>` element must have an `alt` attribute.
- Axe reports when `<img>` elements are missing `alt` attributes. **It does not evaluate alt text.**
- Screen readers convey alt text to users.
- Images with null alt text `alt=""` are ignored by screen readers. These are **decorative images**. 

```html
<!-- Informative image. -->
<img src="[Image file]" alt="Family picture at Tampa, Florida" />

<!-- Decorative image. -->
<img src="[Image file]" alt="" />
```

**`<svg>`**
- `<svg>` images are named using `<title>` tag + `role="image"` or `aria-labelledby` attributes.
- Screen readers ignore `<svg>` tags with `aria-hidden="true"` and keyboard keystrokes are ignored when adding `focusable="false"` attributes.

```html
<!-- Informative image. -->
<svg role="img" id="IdRef">
  <title>Read this!</title>
  <path […]</path>
</svg>

<!-- Decorative image. -->
<svg role="img" aria-hidden="true" focusable="false">
  <path […]</path>
</svg>
```

- **Reference**: [W3C Image Tutorial](https://www.w3.org/WAI/tutorials/images/)
- **Reference**: [deque Creating Accessible SVGs](https://www.deque.com/blog/creating-accessible-svgs/)

## Color Contrast & Use of Color

W3C Understanding Success Criterion 1.4.3: Contrast (Minimum) | WAI | W3C

Increase the contrast between background and foreground.
- **Text**: **minimum contrast ratio** against the background of at least **4.5 to 1**.
- **Large text**: (at least **18 point or 14 point bold and larger**) **minimum contrast ratio** of **3 to 1**.
- **Color is not sufficient to convey information** (for example red color for indication errors) Use alternate aria 
attributes like aria-described by or additional helper text.

> Note: check with your accessibility designer for guidance in using the correct color contrast values.

- **Reference**: [W3C Contrast Minimum - Level AA](https://www.w3.org/WAI/WCAG21/Understanding/contrast-minimum.html)
- **Reference**: [W3C Failure of Success Criterion 1.4.3, 1.4.6 and 1.4.8 due to specifying foreground colors without specifying background colors or vice versa](https://www.w3.org/WAI/WCAG21/Techniques/failures/F24)
- **Reference**: [W3C Content Structure](https://www.w3.org/WAI/tutorials/page-structure/content/)

## Name, Role, Value

Name, role and value convey important information about forms to users of assistive technologies (AT).
- **Name**: identifies the purpose of a form control. For example, a form `<label>`.
- **Role**: the type of object. For example, `<input type="checkbox" />`, `<input type="text" />`, `<input type="radio" />`, etc.
- **Value**: information about states, properties and values. For example, the value of a slider control, or the state of something such as checked, selected, or expanded.

**Examples**:

**Accordion** (`detail/summary`): screen readers announce the accordion state when first setting focus on it, then communicate the value when it changes.
- Expanded: the control is open.
- Collapsed: the control is closed.
- When toggled: the change is announced.

**Disabled button**: Screen readers announce the disabled state when navigating to the object using arrow keys.

**Checkboxes** or **radio buttons**: the checked / not checked states are announced.

> Tip: Native HTML controls automatically meet the WCAG 4.1.2 success criteria when used as designed.

- **Reference**: [W3C Name, Role, Value - Level A](https://www.w3.org/WAI/WCAG21/Understanding/name-role-value.html)
- **Reference**: [W3C Accordion example](https://www.w3.org/WAI/ARIA/apg/patterns/accordion/examples/accordion/)
- **Patterns**: [W3C Patterns](https://www.w3.org/WAI/ARIA/apg/patterns/)

## Tabindex

The `tabindex` attribute controls the keyboard navigation order of elements on a page. While powerful, it should be 
used sparingly as it can easily break the natural tab order and create a confusing experience for keyboard users.

### Tabindex Values

**`tabindex="0"`** - Makes an element focusable in the natural tab order
- The element becomes keyboard accessible.
- Follows the DOM order (like native interactive elements).
- Use for custom interactive elements that aren't naturally focusable.

**`tabindex="-1"`** - Makes an element programmatically focusable only
- The element can receive focus via JavaScript (`element.focus()`).
- Cannot be reached by pressing Tab.
- Use for skip links, modals, or elements that need focus management.

**`tabindex="1"` or higher** - Creates a specific tab order (**AVOID!**)
- Values greater than 0 jump to the front of the tab order.
- Makes maintenance difficult and breaks natural flow.
- Confuses users and makes pages harder to navigate.
- **Almost never use positive tabindex values**.

### Best Practices

**Do:**
- Let the browser handle tab order naturally (no tabindex needed for buttons, links, form elements)
- Use `tabindex="0"` to make custom widgets focusable.
- Use `tabindex="-1"` for programmatic focus (modals, error messages, skip link targets).
- Structure your HTML in logical order - tab order follows DOM order.

**Don't:**
- Use positive tabindex values (`tabindex="1"`, `tabindex="2"`, etc.)
- Add tabindex to elements that are already naturally focusable.
- Change tabindex to fix poor HTML structure - restructure the HTML instead.
- Use tabindex to make non-interactive elements clickable - use `<button>` instead.

> **Remember**: **The best tabindex is no tabindex**. Proper HTML structure and semantic elements provide natural, 
> accessible keyboard navigation without any `tabindex` attributes.


- **Reference**: [W3C Using tabindex](https://www.w3.org/WAI/WCAG21/Techniques/html/H4)
- **Reference**: [MDN tabindex](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/tabindex)
- **Reference**: [W3C Focus Management](https://www.w3.org/WAI/ARIA/apg/practices/keyboard-interface/)

## Notifications `aria-live`

The `aria-live` attribute is used to announce dynamic content changes to screen reader users. This is crucial for 
notifications, alerts, status updates, and any content that changes without a page reload.

### ARIA Live Region Politeness Levels

- **`aria-live="polite"`**: Announces changes when the screen reader finishes its current task. Used for non-critical updates.
- **`aria-live="assertive"`**: Interrupts the screen reader immediately to announce the change. Used for important or time-sensitive information.
- **`aria-live="off"`**: Changes are not announced (default behavior).

### Common Use Cases

**Status Messages** - Use `aria-live="polite"` for general status updates:
```html
<div aria-live="polite" aria-atomic="true" class="status-message">
    <p>Your changes have been saved.</p>
</div>
```

**Error Messages** - Use `aria-live="assertive"` for critical errors:
```html
<div aria-live="assertive" aria-atomic="true" class="error-message">
    <p>Error: Payment failed. Please check your card details.</p>
</div>
```

**Loading Indicators** - Announce loading states:
```html
<div aria-live="polite" aria-busy="true" id="loadingRegion">
    <p>Loading content, please wait...</p>
</div>
```

**Form Validation** - Real-time validation feedback:
```html
<label for="email">Email:</label>
<input type="email" id="email" aria-describedby="emailError" />
<div id="emailError" aria-live="polite" role="alert">
    <!-- Error message inserted here dynamically. -->
</div>
```

**Toast Notifications** - Temporary notifications:
```html
<div aria-live="polite" aria-atomic="true" role="status" class="toast">
    <p>Item added to cart</p>
</div>
```

**Timer/Countdown** - Use `aria-atomic="false"` to announce only changed parts:
```html
<div aria-live="polite" aria-atomic="false">
    Time remaining: <span id="minutes">5</span> minutes <span id="seconds">30</span> seconds.
</div>
```

**Search Results Count** - Dynamic result updates:
```html
<div aria-live="polite" aria-atomic="true" role="status">
    <p>Found <span id="resultCount">42</span> results</p>
</div>
```

### Important Attributes

- **`aria-atomic="true"`**: Announces the entire region content, even if only part changed.
- **`aria-atomic="false"`**: Announces only the changed portion (default).
- **`aria-relevant`**: Specifies what types of changes should be announced:
  - `additions` - Added nodes
  - `removals` - Removed nodes
  - `text` - Text changes
  - `all` - All changes (default is `additions text`)

### Best Practices

1. **Create the live region on page load** - Don't dynamically add `aria-live` to existing content, as it may not work reliably.
2. **Keep messages concise** - Screen readers read the entire content.
3. **Don't overuse assertive** - Only use for critical/urgent messages.
4. **Use semantic roles** - Combine with `role="status"` or `role="alert"` for better support.
5. **Avoid rapid updates** - Multiple quick changes can overwhelm users.
6. **Test with screen readers** - Behavior varies across different screen readers.
7. **Clear messages after they're read** - Remove or clear old notification content.

### Example: Complete Notification System

```html
<!-- Status messages (polite) -->
<div id="statusRegion"
     aria-live="polite"
     aria-atomic="true"
     role="status"
     class="visually-hidden">
    <!-- Status messages injected here via JavaScript. -->
</div>

<!-- Error/Warning messages (assertive) -->
<div id="alertRegion"
     aria-live="assertive"
     aria-atomic="true"
     role="alert"
     class="visually-hidden">
    <!-- Critical messages injected here via JavaScript -->
</div>

<style>
/* This is for demo purposes, make sure all your CSS rules are declared in external CSS files. */  
/* Visually hidden but accessible to screen readers. */
.visually-hidden {
    position: absolute;
    left: -10000px;
    width: 1px;
    height: 1px;
    overflow: hidden;
}
</style>

<script>
// Usage example.
function showStatus(message) {
    const statusRegion = document.getElementById('statusRegion');
    statusRegion.textContent = message;

    // Clear after 5 seconds.
    setTimeout(() => {
        statusRegion.textContent = '';
    }, 5000);
}

function showAlert(message) {
    const alertRegion = document.getElementById('alertRegion');
    alertRegion.textContent = message;

    // Clear after user acknowledges (or after timeout).
    setTimeout(() => {
        alertRegion.textContent = '';
    }, 10000);
}

// Example usage.
showStatus('Your profile has been updated');
showAlert('Session expiring in 2 minutes');
</script>
```

- **Reference**: [W3C ARIA Live Regions](https://www.w3.org/WAI/WCAG21/Understanding/status-messages.html)
- **Reference**: [W3C Using aria-live](https://www.w3.org/WAI/WCAG21/Techniques/aria/ARIA22)
- **Reference**: [MDN aria-live](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Live_Regions)

## Skipping to Main Content

Sometimes web pages are full of links and buttons, making it very hard and time-consuming for users with visual
disabilities or keyboard-only users to navigate to the main content. Users must tab through dozens of navigation links
before reaching the actual content on every page visit.

The solution is a "skip to main content" link - an invisible link that appears only when focused, allowing users to
jump directly to the main content area. This is one of the first WCAG success criteria (2.4.1 Bypass Blocks) and can
be implemented without JavaScript using the `tabindex="-1"` attribute and basic CSS.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Skip to Main Content Example</title>
  <style>
    /* This is for demo purposes, make sure all your CSS rules are declared in external CSS files. */
    /* Visually hide the skip link until focused. */
    .skip-link {
      position: absolute;
      top: -40px;
      left: 0;
      padding: 0.75rem 1rem;
      z-index: 100;
      color: #000000;
      background-color: #FFFFFF;
      outline: thin solid gray;
    }

    /* Show the link when it receives keyboard focus. */
    .skip-link:focus {
      top: 0;
    }
  </style>
</head>
<body>

  <!-- Skip link MUST be the FIRST focusable element on the page -->
  <a href="#main-content" class="skip-link">
    Skip to main content
  </a>

  <header>
    <nav aria-label="Main navigation">
      <a href="#">Home</a>
      <a href="#">Products</a>
      <a href="#">About</a>
      <a href="#">Services</a>
      <a href="#">Blog</a>
      <a href="#">Contact</a>
      <!-- Imagine 20+ more links here. -->
    </nav>
  </header>

  <!-- The target element with an ID and tabindex="-1". -->
  <main id="main-content" tabindex="-1">
    <h1>Main Content Heading</h1>
    <p>This is where the important content starts. Users can skip all the navigation links above.</p>
  </main>

  <footer>
    <cite>&copy; 2024 Example Site</cite>
  </footer>

</body>
</html>
```

### How It Works

1. **The Skip Link (`<a href="#main-content">`)**:
   - Must be the **first focusable element** on the page.
   - Links to the main content area using a fragment identifier (`#main-content`).
   - Hidden off-screen by default (`top: -40px`).
   - Becomes visible when focused via keyboard (`top: 0`).

2. **The Target (`<main id="main-content" tabindex="-1">`)**:
   - The `id` attribute matches the skip link's `href`.
   - `tabindex="-1"` allows programmatic focus (otherwise `<main>` isn't focusable by default).
   - When clicked, browser jumps to this element and sets focus on it.

3. **CSS Strategy**:
   - Link is positioned absolutely and moved off-screen.
   - High `z-index` ensures it appears above other content when visible.
   - `:focus` pseudo-class brings it into view when keyboard user tabs to it.

### Best Practices

- **Always place the skip link first** - It should be the very first element users encounter when tabbing.
- **Use descriptive text** - "Skip to main content" is clear and standard.
- **Make it visible on focus** - Never use `display: none` or `visibility: hidden` which would hide it from screen readers.
- **Ensure sufficient contrast** - The visible link must meet WCAG color contrast requirements (4.5:1 minimum).
- **Test with keyboard** - Press Tab when the page loads to verify it appears.
- **Consider multiple skip links** - Large sites might benefit from "Skip to navigation", "Skip to search", etc.

### Alternative: Multiple Skip Links

For complex pages, you can provide multiple skip links:

```html
<div class="skip-links">
  <a href="#main-content" class="skip-link">Skip to main content</a>
  <a href="#navigation" class="skip-link">Skip to navigation</a>
  <a href="#search" class="skip-link">Skip to search</a>
</div>
```

### Common Mistakes to Avoid

- **Don't use `display: none`** - Screen readers won't announce it.
- **Don't place it after header elements** - Defeats the purpose.
- **Don't forget `tabindex="-1"`** - Focus won't work in some browsers.
- **Don't use only `opacity: 0`** - Link remains visible to screen readers but confusing to keyboard users.


- **Reference**: [W3C Bypass Blocks - Level A](https://www.w3.org/WAI/WCAG21/Understanding/bypass-blocks.html)
- **Reference**: [WebAIM Skip Navigation Links](https://webaim.org/techniques/skipnav/)
- **Reference**: [W3C Technique G1: Adding a link at the top of each page](https://www.w3.org/WAI/WCAG21/Techniques/general/G1)

## Testing

### Text Spacing
Text spacing accessibility testing is necessary because many users rely on customized spacing to read and understand 
content comfortably. Supports users with low vision, dyslexia, and cognitive disabilities. For organizations following 
ADA, Section 508, or international accessibility laws, supporting text spacing is a mandatory part of WCAG compliance.

You can use the [text spacing bookmarklet](tools/text-spacing-bookmarklet.md) to test your web pages and applications. 

Text spacing adjustments apply to all content on the page except in cases where the user agent or platform does not 
permit overriding the default text spacing. Common exceptions include embedded `video` captions, images of text, **custom 
elements** with styles encapsulated in the **Shadow DOM**, the `<option>` list of a `<select>` element, and the 
**date picker** interface of an `<input type="date">` element.

### General markup, color and structural issues
[AXE](tools/axe.md) is a great Chrome browser plugin that can help you identify the problems you have and recommend a 
solution and links the related documentation. You find color contrast issues, structural issues, for example skipping 
headers, missing page titles. 

Said that it will not teach you how to use the right semantic tag and always understand how you use role and aria 
properties correctly.

With a good page structure user with disabilities can find the necessary information easier, can jump into areas of 
their interest, and able to complete the tasks with their screen readers, keyboards only. Will be able to see clearly, 
because of good color contrast as well understand what UI wants to depict even they are color-blind. Understand the 
pictures and images on a website what they mean even they cannot see it. They should be able to watch a video without 
hearing a word, or seeing a single shot, by reading close captions or transcripts. Able to jump any section without 
going through the entire page.

(Some of the source code of very famous websites are thousands and thousands of lines of code that is crap and unnecessary).

### Keyboard
Keyboard is crucial to be able to use a web application or site without a mouse. A user should be able to navigate through
the page, complete forms, and use the links.

### Screen reader
For users that cannot see or have visual disabilities, we need to make sure they can use screen readers to understand
and are able to perform any action they need without difficulty. Unfortunately, there are still some browser and screen
reader specific issues we need to be aware of and implement workarounds for.

Learn how to use the screen reader supported by your operating system. Test your code before you push to production.
There are some nasty defects with some browser and screen reader combinations. For example, in macOS you can test
your pages with a screen reader even without listening. There is a message box that shows the read text to you in
VoiceOver.

With good structure, screen reader users can:
- Skim the page.
- Jump to areas of interest.
- Find important information more easily.

Keyboard commands provide single-key access to objects like:
- Links
- Form controls
- Headings
- Lists
- Landmarks
- Graphics
- And more

## References
- [Accessibility Handbook, Katie Cunningham](https://www.ebooks.com/en-us/book/1013438/accessibility-handbook/katie-cunningham/)
- [Web Accessibility Cookbook, Manuel Matuzovic](https://www.ebooks.com/en-us/book/211381474/web-accessibility-cookbook/manuel-matuzovic/)
- [MDN Accessibility](https://developer.mozilla.org/en-US/docs/Web/Accessibility)
- [W3C Accessibility Standards Overview](https://www.w3.org/WAI/standards-guidelines/)
- [W3C Accessibility Patterns](https://www.w3.org/WAI/ARIA/apg/patterns/))
