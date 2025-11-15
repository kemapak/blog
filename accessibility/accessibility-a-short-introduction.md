# Accessibility a short introduction

What is accessibility? why it is important? As an engineer you might have been asked to make sure you build your 
application accessible. How can you do that? This document will get you started and give you some tips, show you some 
examples.
> Note: This document only covers web accessibility.

First, I have to say accessibility is not a requirement it is a moral obligation. As a professional engineer, as a 
craftsman you have to build an application properly functioning, bug free and accessible.

Second, I hate politics being brought into accessibility. It is not inclusive design or engineering, it is accessible 
design and engineering. No one is intentionally is excluding anyone. We are building software for everyone! Because 
this is the right thing to do, because we are professionals.

# Rule 01 -Use semantic tags
I do see that most of the engineers do not know how to build proper markup. Even in some famous frameworks, design 
libraries are build incorrectly. `<div>` tags are used everywhere, anywhere without thinking.  


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