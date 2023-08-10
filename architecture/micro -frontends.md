# Micro Frontends

## Introduction
Our web based applications customer facing web sites are getting  more and more complex. Even with the advancement of JavaScript frameworks, tools, technologies we are having huge monolithic UI applications.

_Micro Frontend_ is an architectural pattern to address the monolithic UI applications and modularizing them into smaller, logical, and independent pieces.

Like anything in software development, micro frontend is not a silver bullet and a solution for every use case or problem. Said that it can be used effectively to reduce complexity for the code, and business logic. The caveat is the complexity it brings for the building, testing, integration and security.

Micro frontend is inspired by micro services.

## Current UI architectural patterns

### Single page applications, thin client
This is currently the most popular way of doing UI development. All the content, HTML, JavaScript, CSS are loaded into browser and then rendered. Routing, is the responsibility of the code in the browser, also JavaScript is used to get and submit data, content. This works very well but loading all the content initially, and rendering is slow. Angular, React, Backbone are some of the frameworks that are used for this type approach. All the static assets (JavaScript, CSS, images, config, templates, etc.) are served by a content delivery network (CDN)

### Server side rendered applications, thin client
This is old way of preparing and rendering all the pages at the server side and sending to the browser. This requires a lot server processing. Routing is at the server side. This requires a lot of server processing and is not the best of way writing applications. The JavaScript at the page is used to do minimal work like getting content, data. All the static assets (JavaScript, CSS, images, config, templates, etc.) are served by a content delivery network (CDN)

## Server Side Rendered Single Page Applications, thin client
This approach mixes server side rendering for strategic pages (login, home page, etc), and use single page application for rest. This is way faster and currently an excellent way to achieve performance, security and low server processing. All the static assets (JavaScript, CSS, images, config, templates, etc.) are served by a content delivery network (CDN)

### Desktop applications, mobile applications, thick client
Browser based application can be converted to desktop application, and installed on user machines. This code lives in the user machine. JavaScript again is used to get data, content. This fast but the problem is updating the application code, and need of an install. Electron, Cordova are some of the tools that are used to do this. This approach is used for both desktop and mobile devices. All the static assets (JavaScript, CSS, images, config, templates, etc.) are bundled within the app as well as the dynamic assets (HTML).

A new approach _Progressive Web Apps_ (PWA) which you can install a web app into a mobile device without the need of tools .


## Micro Frontend architecture pattern
