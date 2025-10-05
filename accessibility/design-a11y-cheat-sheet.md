# Design accessibility (a11y) cheat sheet

Designing with accessibility in mind ensures that everyone — including people with disabilities — can effectively use 
and enjoy our web and native applications. Accessible design improves usability, builds trust, and ultimately enhances 
the overall user experience.

It may take a bit of extra effort at first, but once accessibility becomes part of your design habits, it will feel as 
natural as any other design consideration.

## Design cheat sheet
| Item                                            | Description                                                                                                                                                                                   | ToDo                      |
|:------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------------|
| **Use standard components**                     | Use semantic HTML tags and components provided by your design system. Platform teams should ensure these components are accessible before use.                                                | <input type="checkbox" /> |
| **Avoid custom components**                     | Custom components are expensive to build and maintain. Use them only if necessary, and base them on verified accessible components. Include full accessibility annotations in the design.     | <input type="checkbox" /> |
| **Maintain a valid page hierarchy**             | Each page should have **one `<h1>` heading**. Subsequent headings should follow proper nesting (e.g., `<h2>` → `<h3>`). Never skip heading levels or style text to mimic headers.             | <input type="checkbox" /> |
| **Ensure a logical page structure**             | Identify and properly mark sections and lists. If it visually looks like a list, it should use list markup (`<ul>`, `<ol>` or `<dl>`).                                                        | <input type="checkbox" /> |  
| **Provide a clear page title**                  | Every page must have a descriptive title that matches the main header `<h1>'. _Example_: `[App or Company Name] – [Page Title]`.                                                              | <input type="checkbox" /> |
| **Annotate all images**                         | If an image is decorative, mark it as such. If it conveys information, provide meaningful alternative text.                                                                                   | <input type="checkbox" /> |                          
| **Label behaviors and errors clearly**          | Provide descriptive labels for all form fields. Add helper text where needed and write clear, actionable error messages explaining how to fix the issue.                                      | <input type="checkbox" /> |
| **Provide feedback during data loading**        | Show appropriate messages for all data states: loading (`Your data is loading...`), success (`Your data is ready!`), and error (`There was a problem loading your data. Please try again.`).  | <input type="checkbox" /> |
| **Support 360px viewport width**                | Ensure your responsive layouts work on narrow screens — many users still have small smartphones.                                                                                              | <input type="checkbox" /> |
| **Support page zoom**                           | Verify that the layout remains usable when zoomed up to **200%**.                                                                                                                             | <input type="checkbox" /> |
| **Check color contrast**                        | Ensure sufficient color contrast between text and background, especially for images and dark backgrounds.                                                                                     | <input type="checkbox" /> |
| **Avoid using text as images**                  | Text embedded in images cannot be resized or read by assistive technologies. If unavoidable, provide alternative text.                                                                        | <input type="checkbox" /> |
| **Avoid flashing text or images**               | Flashing or rapidly animated content can trigger seizures or discomfort. Avoid using it.                                                                                                      | <input type="checkbox" /> |
