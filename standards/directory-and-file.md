# Directory and File Standards

## Table of Contents
* [Table of Contents](#table-of-contents)
* [Directory & File Names](#directory--file-names)
    * [DF-01 – Directory Naming Convention](#df-01--directory-naming-convention)
    * [DF-02 - Image, Video, Font, Markdown File Naming Convention](#df-02---image-video-font-markdown-file-naming-convention)
    * [DF-03 - HTML File Naming Convention](#df-03---html-file-naming-convention)
    * [DF-04 - CSS File Naming Convention](#df-04---css-file-naming-convention)
    * [DF-05 - JavaScript File Naming Convention](#df-05---javascript-file-naming-convention)
* [File Grouping and Organization](#file-grouping-and-organization)
    * [DF-06 - Keep Related Files Together](#df-06---keep-related-files-together)

## Directory & File Names

### DF-01 – Directory Naming Convention
Directory names must clearly reflect their purpose.
- Start with lowercase
- Words separated by hyphens (-)
- No abbreviations unless formally agreed upon

**Format**:
```text
[name-]*name
```

**Examples**:
- /src/component/card
- /src/style
- /documentation/code-review

### DF-02 - Image, Video, Font, Markdown File Naming Convention
File names should clearly describe what the file is and where it is used.
- All lowercase
- Words separated by hyphens (-)
- No abbreviations unless formally agreed upon

**Format**:
```text
[name-]*name.[type]
```

**Examples**:
- flowers.png
- sale-banner.jpeg
- welcome.mov
- password-settings.svg
- directory-and-file.md

> For the main/index level documentation you can use `README.md` file name for markdown file.

### DF-03 - HTML File Naming Convention
File names should clearly describe what the file is and where it is used.
- All lowercase
- Words separated by hyphens (-)
- No abbreviations unless formally agreed upon

**Format**:
```text
[name-]*name.html
```

**Examples**:
- home.html
- phone-catalog.html
- index.html

### DF-04 - CSS File Naming Convention
File names should clearly describe what the file is and where it is used.
- All lowercase
- Words separated by hyphens (-)
- No abbreviations unless formally agreed upon

**Format**:
```text
[name-]*name.css
```

**Examples**:
- home.css
- phone-catalog.css
- normalize.css
- index.css

### DF-05 - JavaScript File Naming Convention
File names should clearly describe what the file is and where it is used.
- Classes start with uppercase
- Utilities start with lowercase
- Words separated with camelcase
- No abbreviations unless formally agreed upon

**Format**:
```text
class
[Name]*Name.js

or

util
[name]*Name.js
```

**Examples**:
- Card.js
- AdminUser.js
- PhoneCatalog.js
- utility.js
- dataVisualizationUtility.js
- index.js

## File Grouping and Organization

### DF-06 - Keep Related Files Together
- Group related files inside the same folder.
- Place common assets used by multiple applications inside a `common` folder.

**Examples**
```text
/src
    /component
        /card
            Card.js
            Card.test.js        # Unit tests always live with the code.
            card.css
            README.md           # Documentation always lives with the code.
        /button
            Button.js
            Button.test.js
            button.css
            README.md
        util.js                 # Common utility for web components.
    /user-profile
        UserProfile.js        
        UserProfile.test.js
        user-profile.css
        AdminUser.js
        AdminUser.test.js       
        /assets
            avatar.png          # Custom assets always live with the code.
            sign-in.svg
            sign-out.svg
            update-profile.mov
    /style
        normalize.css
        helper.css
        tokens.css
        /font                   # Custom fonts.
            abc.woff
            abc.css
        /icon                   # Common icons.
            icons.woff
            icons.css      
    /common                     # Common assets used by all applications and components.
        /util
            polyfill.js         
            commonUtil.js             
        /video
            welcome.mov         
        /image
             logo-large.png              
             logo-small.png
             anonymous-user.jpeg             
```
