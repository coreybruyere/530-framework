#**530 Framework**  
##**An organizational template based off of CSS Burrito**

### Style Guide Rules

-List @extend(s) First

-List "Regular" Styles Next

-List @include(s) Next

-Nested Selectors Last

-All Vendor Prefixes Use @mixins

-Maximum Nesting: Three Levels Deep

-Maximum Nesting: 50 Lines

-Global and Section-Specific Sass Files Are just Table of Contents

-List Vendor/Global Dependancies First, Then Author Dependancies, Then Patterns, Then Parts

-Break Into As Many Small Files As Makes Sense

-Partials are named _partial.scss

-In Deployment, Compile Compressed

-Be Generous With Comments

-Variablize All Common Numbers, and Numbers with Meaning

-Variablize All Colors

-Nest and Name Your Media Queries. Nest at bottom of declaration

-Include all hacky and gross CSS in a _shame.scss file

###Helpful Links about Style guides, best practices, SMACSS, OOCSS, BEM, etc.

####[More info on style guide above](http://css-tricks.com/sass-style-guide/)

http://www.sitepoint.com/architecture-sass-project/

http://scaffy.railsware.com/

https://github.com/csswizardry/CSS-Guidelines

http://csswizardry.com/2012/11/code-smells-in-css/

http://thesassway.com/beginner/how-to-structure-a-sass-project/

http://ianstormtaylor.com/oocss-plus-sass-is-the-best-way-to-css/

http://geoffgraham.me/sassifying-wordpress/


To understand why you would want to use this template, it is a great idea to familiarize yourself with the following css architectures:  

####[OOCSS](http://oocss.org/) - Object Oriented CSS

* **Separate structure and skin** - Structure properties like padding and margin should be separated from skin properties like background and border.
* **Separate content from container** - Content modules like buttons and lists should not be dependent on their parent containers.  

####[SMACSS] (http://smacss.com/) - Scalable and Modular Architecture for CSS

* Increase the semantic value of HTML and content.
* Decrease the expectation of a specific HTML structure. 
* Organize your css files into sections like **base rules**, **layout rules**, and **modules** so that the styling will be flexible and easily maintainable.

####[MVCSS] (http://mvcss.github.io/) - A Sass based CSS architecture and style guide.  

###What's in this project?
```
stylesheets/ 
|
|– libs/ 
|   |- _libs-override    # Library Variable Overrides
|   ...                  # Etc… 
|
|– helpers/ 
|   |– _settings.scss    # Font Declarations, Color, Type Variables
|   |– _helpers.scss     # Helper Classes, Mixins, Functions, Utilities
|   ...                  # Etc… 
| 
|– core/ 
|   |– _normalize.scss   # Reset/normalize 
|   |- _base.scss        # Base-level tags 
|   |– _typography.scss  # Typography rules 
|   ...                  # Etc… 
|
|– layout/ 
|   |– _grid.scss        # Grid system 
|   |– _header.scss      # Header 
|   |– _footer.scss      # Footer 
|   |– _sidebar.scss     # Sidebar 
|   ...                  # Etc… 
|
|– components/ 
|   |- _components.scss  # Import of all used components
|   |– _buttons.scss     # Buttons 
|   |– _carousel.scss    # Carousel 
|   |– _cover.scss       # Cover 
|   |– _dropdown.scss    # Dropdown 
|   |– _navigation.scss  # Navigation 
|   |– _forms.scss       # Forms 
|   ...                  # Etc… 
| 
|– pages/ 
|   |– _home.scss        # Home specific styles 
|   |– _contact.scss     # Contact specific styles 
|   ...                  # Etc… 
| 
`– application.css.scss  # primary Sass file 
```

###This template has six main ingredients.  
####**1.  Application.css.scss**
- This section serves two purposes.  
* It imports all files from each folder.  
* It has a **Shame** section for quick fixes, hacks, and other questionable techniques.  Be sure to fix them later.

#### **2.  Libs**
* **libs-override**  Any overrides to Bootstrap or other library or vendor variables should be made in this file to prevent unnecessary overwriting.  

#### **3.  Helpers**
* **Settings** - @font-face and global variables
* **Helpers** - Extends, Functions, Mixins
  
#### **3.  Core** -  There are three core files.
* **Normalize** - Normalize reset file
* **Base** - Base-level tags (body, p, nav ul li, etc.)
* **Typography** - Base-level typography (colors, fonts). 

####**4.  Layout** - Major structural pieces. **Use components if possible.**
* **Grid** - Use grid of choice here
* **Header** - Header structure
* **Footer** - Footer structure
* **Sidebar** - Sidebar structure

####**5. Pages** - **This should RARELY be used**
* **Home** - Home page specific style overrides 

####**6. Components** - **Most of your styles should be found here.**
Any unit of style that can be found across multiple pages (Buttons, Navigations, Carousels, Modals).  
Components are stand alone pieces that can be reused anywhere without having to rewrite any code.


###Lets talk about States.

Inside the **components** file and in the **example-module** file, there is a section for styling states.

* States are styles that override all other styles.  Usually via javascript.  
* States are generally applied to the same element as a layout rule, or to the same element as a base module.
* An example would be a navigation drop down, or a message that displays a success or error state. 
* State class names should be written as a boolean.  For example, ```.is-collapsed``` or ```.is-error```.
* When state rules are added to specific modules, the module name should be included in the classname.  For example, an active tab state could be written as ```.is-tab-active```.

###Wrapping it all together.
This template should feel intuitive and easy to use.  The goal is to keep everything organized so that large projects will scale nicely without duplicating code, or having unnecessary increases in specificity.

<!-- ##Setup
To make adding new modules easy, css-burrito has a shell script that will add new modules for you.

**To use this feature:**  

Open up the command line, and navigate to the project root.  

``` cd ~/Desktop/css-burrito-master```

Then run the following command   

``` ./setup.sh```  

This will only need to be done once.  

After that,  navigate to the modules folder in any project that has a ```burrito.sh``` file.  

```cd path/to/project/stylesheets/modules```

From here, in the command line, you can type  

```burrito example-module ```

This will create a file with some default comments, in this case named ```_example-module.scss``` and import it into the main ```_modules.scss``` file for you.  
 -->
##Suggested Styleguide

####General Styling  
* Avoid using ID's.  Use classes instead.
* All CSS class names should use dashes instead of underscores or camel case.
* Do not over-qualify selectors.  Keep specificity number as low as possible.
* Use one discrete, comma separated selector per line in multi-selector rulesets.

####Preprocessors 
* Do not nest deeper than 3 levels (with the exception of pseudo/hover states).
* Declare ```@extend``` followed by styles then ```@include``` statements at the end of the declaration block whenever possible.
* If a ```:hover``` pseudo class is styled, ```:focus``` should also be styled for accessibility. Focus styles should never be removed
