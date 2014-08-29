#**Snuggie - A Sass-based CSS architecture**  

530medialab's Organizational Template. Inspired by MVCSS, CSS Burrito, the GroupBuddies template, and hints of SMACSS and OOCSS. This template follows the BEM syntax and uses SASS. To understand why you would want to use this template, it is a great idea to familiarize yourself with the following css architectures:  

####[BEM](http://bem.info/method/) - Block, Element, Modifier

* BEM stands for Block, Element, Modifier. The meaning of these terms will be described further in the article.
* One of the most common examples of a methodology in programming is Object-Oriented Programming. It's a programming paradigm embodied by many languages. In some ways, BEM is similar to OOP. It's a way of describing reality in code, a range of patterns, and a way of thinking about program entities regardless of programming languages being used. 

####[OOCSS](http://oocss.org/) - Object Oriented CSS

* **Separate structure and skin** - Structure properties like padding and margin should be separated from skin properties like background and border.
* **Separate content from container** - Content modules like buttons and lists should not be dependent on their parent containers.  

####[SMACSS] (http://smacss.com/) - Scalable and Modular Architecture for CSS

* Increase the semantic value of HTML and content.
* Decrease the expectation of a specific HTML structure. 
* Organize your css files into sections like **base rules**, **layout rules**, and **modules** so that the styling will be flexible and easily maintainable.

##**What's in this project?**
```
stylesheets/ 
|
|– bits/ 
|   |- _base.scss           # Base styles for lonely tags that don't have their own partial
|   |– _buttons.scss        # Base styles for buttons
|   |– _forms.scss          # Base styles for all Form elements (inputs, checkboxes, etc.)
|   |– _lists.scss          # Base styles for OL's, UL's, LI's, and list classes
|   |– _pagination.scss     # Base styles pagination arrows, numbers, etc.
|   |– _tables.scss         # Base styles tables, tbody, thead, tr, td, and table classes
|   |– _typography.scss     # Base styles for headings, paragraphs, or any global type classes
| 
|– modules/ 
|   |– _carousel.scss       # Carousel 
|   |– _media.scss          # Media 
|   |– _nav.scss            # Navigation 
|   |– _search-form.scss    # Forms 
|   |– _modals.scss         # Modals
|   |– _post.scss           # Post
|   |– _product.scss        # Product
|   |– _touts.scss          # Touts
|   |- _flags.scss          # Flags 
|   |– _tabs.scss           # Tabs
|   |– _tooltips.scss       # Tooltips
|
|– sections/ 
|   |– _header.scss         # Header 
|   |– _footer.scss         # Footer 
|   |– _sidebar.scss        # Sidebar 
|   |– _body.scss           # Body 
|   ...                     # Etc… 
|
|– templates/ 
|   |– _custom-temp.scss    # Custom Template -- If needed
|   ...                     # Etc… 
|
|- utilities/
|   |– _animations/animate  # Animations
|   |– _functions/functions # Functions 
|   |– _grid/index.scss     # Grid system
|   |– _mixins/mixins       # Mixins
|   |– _helpers             # Helper Classes
|   |– _settings.scss       # Font Declarations, Colors, Type Variables
| 
|- vendors/
|   |– normalize            # Normalize
|   ...                     # Vendor css
|
`– main.scss     # primary Sass file 
`– ie.scss       # ie Sass file for ie 8 and down
```

###This template has seven main pieces.  

####**0.  main.scss & ie.scss**
- This section serves two purposes.  
* It imports all files from each folder.  
* It has a **Shame** section for quick fixes, hacks, and other questionable techniques.  Be sure to fix them later. Included at the top of each of these files are variables that allow for ie specific compiling. 

####**1.  Bits**
* ** Bits are the basic, smaller building blocks of matter. Applied to web interfaces, Bits are our HTML tags, such as a form label, an input or a button.
Bits can also include more abstract elements like color palettes, typography and more.

####**2.  Modules**
* ** Modules are groups of Bits combined together and are the smallest fundamental units of a compound, built for **reuse.** These Modules take on their own properties and serve as the backbone of our design system. For example, a search form.

####**3.  Sections**
* ** Sections are groups of modules and/or bits joined together to form a relatively complex, distinct section of an interface, such as a header or a footer. This is where we declare our main body, footer, header, and sidebar wrappers & containers. Sections are used to ensure wrappers and containers are consistent throughtout the whole site. These should be the first pieces that are built on a project. 

####**4.  Templates**
* ** Templates consist mostly of groups of Modules stitched together to form pages. Templates are very concrete and piece together our Bits and Modules. Templates can also consist of unique page styling. 

####**5.  Utilities**
* ** Utilities hold the Grid, Animations functions, Settings (Font Declarations, Color, Type, and Media Query Variables), Helpers (Helper classes, mixins, functions, utilities), and Normalize, or a custom reset. 

####**7.  Vendors**
* ** All Vendor CSS and/or SASS goes here. Along with normalize.css.

###Lets talk about States.

* States are styles that override all other styles.  Usually via javascript.  
* States are generally applied to the same element as a layout rule, or to the same element as a base module.
* An example would be a navigation drop down, or a message that displays a success or error state. 
* State class names should be written as a boolean.  For example, ```.is-collapsed``` or ```.is-error```.
* When state rules are added to specific modules, the module name should be included in the classname.  For example, an active tab state could be written as ```.is-tab-active```.

###Wrapping it all together.
This template should feel intuitive and easy to use.  The goal is to keep everything organized so that large projects will scale nicely without duplicating code, or having unnecessary increases in specificity.

##Styleguide

####General Styling  
* Avoid using ID's.  Use classes instead
* All CSS class names should use BEM syntax with double underscore and double dash
* Read more about BEM below in Naming Conventions
* DO NOT over-qualify selectors.  Keep specificity number as low as possible
* Use one discrete, comma separated selector per line in multi-selector rulesets
* Order of CSS properties: Positioning, Display & Box Model, Color, Text, Other
* List @extend(s) first
* List "regular" styles next
* List @include(s) next
* Nest all pseduo-classes directly beneath base properties and values
* Media queries belong right after pseudo-classes
* Nest tags beaneath if absolutely necessary, but try to refrain from that 
* Keep it OOCSS and use un-nested class names
* List any class modifiers after all module children
* Use auto prefixer 
* Break into as many small files as makes sense
* Modules are named _module.scss
* Be generous with comments & use same comment block style => "// -- Comment Text"
* Variablize all colors, numbers, etc.
* Use included grid. It's super rad => [http://jeet.gs/](http://jeet.gs/)
* Include all Hacky and Gross CSS in main.scss at the Bottom in 'Shame' Section

**Info on style guides => [http://css-tricks.com/sass-style-guide/](http://css-tricks.com/sass-style-guide/)**

####Styleguide Example
```css
    .module {
        @extend %clearfix;
        width: 100%;
        color: red;
        @include mixin;

        /* -- Min Width @ $tablet */
        @include min-breakpoint($tablet) {
            width: 25%;
        }

    .module__item {
        display: inline-block;
    }

    .module--alt {
        @extend .module;
        color: green;
    }
```

####Naming Conventions
* **Content-layer semantics are already served by HTML** elements and other attributes.
* **Class names impart little or no useful semantic information to** machines or human visitors unless it is part of a small set of agreed upon (and machine readable) names – Microformats.
* **The primary purpose of a class name is to be a hook for CSS (Use ID's for JS on unique selectors. Prefix all JS hooks with 'js-').** If you don’t need to add presentation and behaviour to your web documents, then you probably don’t need classes in your HTML.
* **Class names should communicate _useful_ information to _developers_.** It’s helpful to understand what a specific class name is going to do when you read a DOM snippet, especially in multi-developer teams where front-enders won’t be the only people working with HTML components.
* Class names are named using adjectives and nouns.  

**Info on naming => [http://nicolasgallagher.com/about-html-semantics-front-end-architecture/](http://nicolasgallagher.com/about-html-semantics-front-end-architecture/)**

####Naming Example
```css
    /* -- Block Noun */
    .person {}

    /* -- Element Noun__Noun */
    .person__hand{}

    /* -- Modifier Noun_Noun--Adjective */
    .person__hand--left{}
```
**Info on BEM Syntax => [http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)**

####Commenting/Snippets
Throw this snippet in your Emmet Sublime User Settings to enable some quick keyboard shortcuts
```json
{
  "snippets": { 
    "css": {
      "snippets": {
        "mq-": "// -- Min Width @ ${1:width}\n@media #{${1:width}} {\n|\n}",
        "com": "// -------------------------------------\n//   ${1:Comment Name} \n// -------------------------------------",
        "scom": "// -- ${1:Small Comment}"
      } 
    }
  }
} 
```
**Custom snippets definitions => [https://github.com/emmetio/emmet/blob/master/snippets.json](https://github.com/emmetio/emmet/blob/master/snippets.json)**

####Preprocessors 
* Do not NEST! (with the exception of pseudo/hover states and module modifier and child classes).
* Declare ```@extend``` followed by styles then ```@include``` statements at the end of the declaration block whenever possible.
* If a ```:hover``` pseudo class is styled, ```:focus``` should also be styled for accessibility. Focus styles should never be removed
