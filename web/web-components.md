# Web Components

In software engineering we solve big problems by diving them into smaller problems, smaller pieces. Functions, methods, 
classes and modules are core parts of JavaScript and many other languages. These are structures and paradigms that we use 
in programming to reduce, isolate the complexity of our code. Modular code also makes it easy for us to understand very 
complex systems, piece by piece, one at a time.

How about HTML? It is markup language, it has limited number of tags, it does not have any logic, and it is very monolithic.

You can easily see a web based application or page consists of thousands of lines of HTML code. As of 2023;
> Amazon landing page consists of more than **19K lines of HTML code**.
> 
> CVS Specialty consists of more than **3K lines of HTML code**.
> 
> Apple landing page consists of **just over 1K lines of HTML code**.

Large monolithic HTML pages, web based applications are definitely not easy to maintain, to understand, easy to isolate 
and fix issues. When we add styling, accessibility and functionality on top of it becomes a nightmare. It is just yucky, 
very yucky!

We do need more HTML tags, custom elements, controls to build our pages, our applications. Even HTML is way better now;
and we have quite a few new useful tags like; dialog, calendar (input date), expand/collapse (detail/summary) it is still
not enough and never will be. We do need custom tags!

With web components we can drastically reduce the main HTML code, modularize it, break into logical pieces. We can write
functional parts of HTML declaratively. _For example:_ navigation, shopping item, page header, page footer, etc. This   
makes the HTML code way easier to maintain as well consistent. We use the same page header component throughout our application,
so it looks the same. When it is time to update the page header we updated in one place and the entire application is updated.

Also from scalability perspective it is very effective. Image we build one card container, one set of form elements (extend native tags)
and the entire application looks and behaves the same.


Web components come into play when we really want to organize our HTML, build modular, functional small components, just 
like lego bricks we can build our applications and web pages in a modular way. Web components are custom HTML elements. 
This technology is also capable of extending the functionality of current HTML elements. So just with some imagination 
you can do magic.

## A bit of history

### Server side rendering

In old days when we used to render pages using HTML and JSP tags.

### Client side rendering

When we start use JS frameworks we started to assemble pages in browsers. We did use many frameworks, for example configuration based frameworks like SenihaJS to create pages. These were ugly not easy to maintain each control had huge config files.

Then Angular JS come into our lives in year 2010 created by Misko Hevery from Google, and I was in love!

Angular was a framework that manages dependencies like not other, a fully testable JavaScript framework, and have something  very special called **directives**!

Directives were the prelude to the web components. We were able to create custom tags and encapsulate all the HTML, CSS and JavaScript within the directives (There were behavioral directives too, which we can do by extending an HTML element).

So we can create a chart just with one directive. We can create dialog (We did not have dialog tag then) with one directive. The HTML was written declaratively too, you just add the HTML custom tag/directive provide the parameters, and you were done. One of the companies that I work I wrapped a complex tool into a directive exposed most used features as simple parameters, and reduced engineering development time form a week to under an hour. Multiply that by 100s of teams that made a huge difference.

There was one problem! The encapsulation was only in development time, in runtime all the internal HTML, CSS and JavaScript was exposed. So the CSS we use, the JavaScript we use and HTML we use has to fit the tech stack, to the software ecosystem perfectly. If you use a wrong style in the parent page, or within the component it would break the layout. The JavaScript framework you use must exactly match, and if you make a mistake you could have break the entire application.

In year 2012 W3C published the first spec of web components. Which will brought encapsulation, declarative coding not only in development time but in the runtime as well. You can build your web component in one framework and without any issue use it in a page that uses another. The CSS you write would not break your parent page or the CSS you wrote in your parent page will not break any style within your component.

It took sometime for all the browser support web components, but now they all do, and we use them to make our lives simpler, easier and more productive.

## Why does it matter?
- Modular encapsulated code.
- Reduce the main HTML code drastically.
- Declarative HTML. `<my-chart></my-chart>`
- Extendable HTML. `<ul is="my-tree">...</ul>`
- Encapsulated or open. (Shadow DOM)
- Can use different frameworks, libraries.
- Works very well with design systems.
- Easier to enhance and update.
- Easier to isolate and fix issues
- Make changes from one place, centrally.
- Make our applications load way faster.
- Easier to make it accessible.
- Easier to test.
- Simpler architecture.
- Pleasure to design and develop.

## Component based web architecture
Component based web architecture is an approach for building web pages and applications with components. Develop each 
component independently and reuse them.

You can make your components accessible, test them in isolation, and fixing issues and updating your code centrally.

This approach also supports custom design systems very well (Given some common CSS for core items). Design also have 
more freedom and flexibility because they can update the design of a component (and common CSS) that will trickle to 
the entire application(s). Updating the look and feel, changing design systems will be done easier, cheaper and much 
faster.

## Micro frontend web architecture (MFA)
This approach even takes component based web architecture a step further, and build mini apps, with all the services, UI 
in one peace. _For example:_ We can build a calendar micro frontend that any web application can use by just adding the 
markup and necessary libraries. Another example could be a chat client that we can add to any web application. 

## Parts of a web component

### 1 Custom elements

Browser native JavaScript API, that defines custom elements. Let the browser know how the element will behave, render.

### 2 Shadow DOM

An encapsulated DOM, separate from the page DOM that will enable you to keep your HTML, CSS and JavaScript within your 
component private and avoid collisions with the page. In other words, you can use different frameworks, CSS libraries, they
will not collide and override each other.

> This is similar to an iFrame from encapsulation perspective.

### 3 Templates and Slots

Templates enable you to create your custom private (or public) HTML and will define the structure of your custom component.

Slots are placeholder for child content belongs to the main page. _For example_: In a dialog component, you can put any 
HTML inside its body/content or the header or the footer. A slot is a bucket of custom element that you can put stuff in.

Slots come in 2 flavors named and generic.

- If you name a slot content will be treated according to the custom code in your component, it can have it own styles. 
- _For example_: for a dialog you might have header, body and footer slots.
- If you have a generic slot any content you put from the main page will be treated the same. _For example_: for a 
- tooltip component you will just have a generic slot since it can only have one type of content.
> Important note: When you define a slot in your template, the host page can insert multiple of them. _For example_: 
> multiple body slots in a dialog component, or multiple generic slots in a tooltip.

## Web component life cycle and events

As described in the previous section, we have to create a template, add the necessary JavaScript and style to create a 
web component. Below is the basic skeleton, which I will describe each part in detail.

```
class CustomComponent extends HTMLElement {

    #template = document.createElement('template');
    #templateMarkup = `
        <!-- Your custom markup, styles -->
        
        <!-- :host is the style of the root element of your web component. -->
        <style>
            :host {
                display: inline-block;
                contain: content;
            }
        </style>
        
        <div>Your own markup</div>
        
        <!-- Generic slot. --> 
        <slot></slot>
        
        <!-- Named slot. --> 
        <slot name="content-header"></slot>
    `;
    
    constructor() {
    
        super();
        
        this.#template.innerHTML = this.#templateMarkup;
        
        // this.shadowRoot is like your document object in your main HTML page.
        this.shadowRoot.appendChild(this.#template.content.cloneNode(true));
        
        /*
            If you do not add shadowRoot the page will have full access to your child template, CSS and JavaScript.
            This migth be necessary if you migrating from monolotic UI, and if you are building a design system.
         */   
    }
    
    connectedCallback() {
        // Executed when component is added to the page, DOM.
    }
    
    disconnectedCallback() {
        // Executed when component is removed to the page, DOM.
    }
    
    static get observedAttributes() {
        return ['param-one', 'param-two'];
    }

    attributeChangedCallback(name, oldValue, newValue) {

        switch (name) {
            case 'param-one': {
                // Handle changes.
                break;
            }
            case 'param-two': {
                 // Handle changes.
                break;
            }
            default:
                break;
        }
    }
    
    #customPrivateMethod() {
        // Custom handling.
    }
}

// Adding your component to the custom elements, and defining component.
customElements.define('custom-component', CustomComponent);
```
> Note: This is how write components, my coding style. You can have the templates outside the class if you want and prefer.

## References
- [Web Components](https://developer.mozilla.org/en-US/docs/Web/API/Web_components)
