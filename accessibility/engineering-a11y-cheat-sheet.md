# Engineering accessibility (a11y) cheat sheet

Making our applications accessible is not just a functional requirement — it is a moral obligation. Like any defect, 
accessibility issues become significantly more expensive to fix after code is released to production. This document 
outlines how we can proactively reduce the number of accessibility defects: the tools to use, the people to involve, 
and when to escalate to product, design, or engineering leadership to adjust our approach.

Engineering plays a critical role in preventing defects, identifying design gaps, and calling out missing accessibility 
annotations. As engineers, we must do our part to prevent as many accessibility issues as possible.

## Before Development Begins
### Pre-Development Checklist
| Category                         | Questions                                                                                                        |
|:---------------------------------|:-----------------------------------------------------------------------------------------------------------------|
| Custom Component                 | Do we truly need to build a custom component?                                                                    |
| Design system                    | Are we using our Design System components exclusively?                                                           |
| Page Hierarchy                   | Does the page follow a proper heading hierarchy? Does it include an `h1` and a `title` tag?                      |
| A11y Design Annotations          | Are accessibility annotations provided? Do you see any gaps or have questions? (Required for custom components.) |
| 360px Responsive Wireframes      | Are wireframes provided at a minimum width of 320px per accessibility requirements?                              |
| Zoom Behavior                    | Has design defined how the layout behaves when text is zoomed 200%?                                              |
| Image & Icon Alt Text            | Are images decorative, or have proper alternative text/title been provided?                                      |
| Correct Design System Components | Are the correct component types used? (e.g., external links look different from internal links.)                 |
| Color Contrast                   | Has design validated color contrast in questionable areas?                                                       |
| A11y Engineer Preview            | Has your accessibility engineer or experts reviewed the designs and provided feedback?                           |

### Key Questions to Validate
1. **Did design use design system components to build the page?**
   - If not, discuss alternatives with engineering leads, design, and product.
   - If a custom component is required:
     - Full accessibility annotations must be provided before work begins.
     - Do **not** start the story until they are delivered.
     - Inform product and engineering leadership that:
       - Cost may increase tenfold (responsiveness, accessibility, mobile views, testing).
       - Historically, custom components have produced the highest number of accessibility defects.
     - Always obtain approval from engineering leads.
2. **Does the page follow the correct heading hierarchy?**
   - Exactly one `h1`
   - No heading level skipping (e.g., `h2` → `h4`)
   - Proper `title` tag
   - Use semantic heading elements, not styled divs.
3. **Do all form elements have labels?**
4. **Do elements that visually resemble lists use proper list semantics?**
5. **Are image alt/title attributes defined in the wireframes (or marked decorative)?**
6. **Are link types correct and consistent (internal vs. external)?**
7. **Is custom CSS minimized or avoided?**
8. **Does the design include wireframes for:**
   - Error states
   - Width at 360px
   - Loading spinners and screen reader announcements
   - Dynamic content (show/hide based on input)
   - Do we need aria-live regions?
   - Color contrast validation
   - 200% text zoom without layout breakage
9. **Is an a11y engineer or expert included in design reviews?**
   - You are responsible for ensuring their presence
   - Do not commit to work until concerns are addressed

## After Development: Verification & Testing
### Testing Checklist
| Category                     | What to Verify                                           |
|:-----------------------------|:---------------------------------------------------------|
| Run AXE                      | Detects page hierarchy and missing ARIA properties       |
| Word-Spacing Bookmark        | Detects spacing-based readability issues                 |
| 360px Width Validation       | Ensures required responsive behavior                     |
| Keyboard Navigation          | Validates keyboard-only accessibility                    |
| Assistive Technology         | Verify with macOS VoiceOver, NVDA, or JAWS for Window OS |
| A11y Engineer, Expert Review | Confirm review in lower environment                      | 

### Required Verification Steps
1. **Run AXE**
   - Fix all defects within your component
   - If defects belong to someone else:
     - Report to your engineering lead and accessibility engineer
     - We are all responsible for accessibility defects
   - Watch for false positives (AXE is not always correct)
2. **Run the Word-Spacing Tool**
   - Confirms support for custom spacing requirements
3. **Verify Layout at 360px Width**
   - We must support this minimum
4. **Verify Keyboard Navigation**
   - No keyboard traps
   - Logical movement order
   - Custom components require keyboard interaction specs from design/UX
5. **Test with Screen Readers**
   - macOS: VoiceOver
   - Windows: NVDA or JAWS
   - Validate:
     - Reading order
     - Labels
     - Focus states
     - Error feedback
6. **Ask for Help Early**
   - Do not stay blocked for more than **1 hour**
   - Others may resolve issues faster
7. **A11y Engineer, Expert Sign-off**
   - Required before moving stories forward

## Custom Components (Critical Reminder)
If you are building a custom component, schedule a review with:
- A11y engineering, expert
- A11y design
- Engineering leads
- Design
- Content
- Product

- Custom components:
  - Are responsible for most accessibility defects
  - Are difficult (and very expensive) to correct later
  - Require rigorous planning upfront

## Summary
Following these guidelines will:
- Prevent costly defect remediation
- Improve user experience for everyone
- Reduce risk of legal exposure
- Improve engineering quality and consistency

**Accessibility is everyone’s responsibility — and you play a key role in getting it right the first time.**
