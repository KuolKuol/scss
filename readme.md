# SASS Overview
**Written By [Kuol Kuol](https://kuol.ca)**

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/96/Sass_Logo_Color.svg/2000px-Sass_Logo_Color.svg.png" data-canonical-src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/96/Sass_Logo_Color.svg/2000px-Sass_Logo_Color.svg.png" width="200"/>

## Table Of Contents:

  - [1. Folder Structure](#1-folder-structure)
    - [The 7–1 Pattern](#the-7%e2%80%931-pattern)
    - [1.1 Helpers](#11-helpers)
    - [1.2 Base](#12-base)
    - [1.3 Components](#13-components)
    - [1.4 Layout](#14-layout)
    - [1.5 Pages](#15-pages)
    - [1.6 Themes](#16-themes)
    - [1.7 Vendors](#17-vendors)
  - [2. File Structure](#2-file-structure)
    - [1. Main.scss](#1-mainscss)
    - [2. All.scss](#2-allscss)
  - [Documentation Specifications](#documentation-specifications)
    - [Knyle Style Sheets (KSS)](#knyle-style-sheets-kss)
  - [4. Style Guide Format](#4-style-guide-format)
    - [Indentation and Spacing](#indentation-and-spacing)
    - [Ordering Pseudo-Selectors](#ordering-pseudo-selectors)
    - [Ordering Short Hand Rules](#ordering-short-hand-rules)
    - [Sorting Properties](#sorting-properties)
    - [Z-index](#z-index)
    - [Responsiveness](#responsiveness)
  - [5. Useful Links](#5-useful-links)



## **1. Folder Structure**
___
### **The 7–1 Pattern**
This project uses the architecture known as the 7–1 pattern (7 folders, 1 file), is a widely-adopted structure that serves as a basis for large projects. All the partials are organised into 7 different folders, and a single file sits at the root level (named `main.scss`) to handle the imports — which is the file you compile into CSS.

Here’s a sample 7–1 directory structure, I’ve included some examples of files that would sit inside of each folder:

```
sass/
|
|– helpers
|   |– _variables.scss    // Sass Variables
|   |– _functions.scss    // Sass Functions
|   |– _mixins.scss       // Sass Mixins
|   |– _all.scss          // Import File
|
|– base/
|   |– _reset.scss        // Resets CSS
|   |– _typography.scss   // Typography rules
|   |– _all.scss          // Import File
|     
|– components
|   |– _static/           
|   |   |– _header.scss   // Header
|   |   |– _footer.scss   // Footer
|   |   |– _all.scss      // Import File
|
|   |– _variable.scss/    
|   |   |– _buttons.scss  // Buttons 
|   |   |– _slider.scss   // Sliders
|   |   |– _all.scss      // Import File
|
|– layout/
|   |– _navigation.scss   // Navigation
|   |– _grid.scss         // Grid system
|   |– _header.scss       // Header
|   |– _footer.scss       // Footer
|   |– _sidebar.scss      // Sidebar
|   |– _forms.scss        // Forms
|   |– _all.scss          // Import File
|
|– pages/
|   |– _home.scss         // Home specific styles
|   |– _about.scss        // About specific styles
|   |– _contact.scss      // Contact specific styles
|   |– _all.scss          // Import File
|
|– themes/
|   |– _theme.scss        // Default theme
|   |– _admin.scss        // Admin theme
|   |– _all.scss          // Import File
|
|– vendors/
|   |– _bootstrap.scss    // Bootstrap
|   |– _jquery-ui.scss    // jQuery UI
|   |– _all.scss          // Import File
|
`– main.scss              // Main Sass file (Imports every all.scss files)
```

#### **1.1 Helpers**
These files don’t output any CSS when compiled, they are to be used by the other files to create custom styles. This folder holds Sass tools, helper files, variables, and config files.

### **1.2 Base**
This folder contains the boilerplate code which is used throughout the project such as css resets and typographic rules.

 ### **1.3 Components**
Holds all of the styles for buttons, carousels, sliders, and similar page components (think widgets). Your project will typically contain a lot of component files — as the whole site/app should be mostly composed of small modules. 

1. ### **Variable Components**
   Holds all the styles for modules that have multiple varients. Example: big and small buttons with different colors.

1. ### **Static Components**
   Holds all the styles for modules that never change and have only one version. Example: Navigation bars, Sidebars, and Footers.

### **1.4 Layout**
Contains all styles involved with the macro layout of the project which includes the grid system.

### **1.5 Pages**
Contains any styles specific to individual pages. For example it’s not uncommon for the home page of your site to require page specific styles that no other page receives.

### **1.6 Themes**
Hold files that create project specific themes. For example, if sections of the site contain alternate color schemes for night and day mode settings for website readers.

### **1.7 Vendors**
Contains all third party css and sass code from external libraries and frameworks. Example: Normalize.css.

## **2. File Structure**

### **1. Main.scss**
Located in the root directory, this file handles the imports of all the partials. This is done by importing every `all.scss` file in every folder.

### **2. All.scss**
Handles the imports for partials in specific folders. These files are to be imported into te `main.scss` file. 

## **Documentation Specifications**
___

### **Knyle Style Sheets (KSS)**
KSS is a documentation specification and style guide format. It attempts to provide a methodology for writing maintainable, documented CSS within a team. Most developers use it due to its popularity, expressiveness, and simplicity.

The KSS format is human-readable and machine-parsable. Therefore, it is intended to help automate the creation of a living style guide.

#### **Format**
Each KSS documentation block consists of three parts: a description of what the element does or looks like, a list of modifier classes or pseudo-classes and how they modify the element, and a reference to the element’s position in the styleguide.

The basic format for KSS documentation can be best explained in an example:

```
// A button suitable for giving stars to someone.
//
// :hover             - Subtle hover highlight.
// .stars-given       - A highlight indicating you’ve already given a star.
// .stars-given:hover - Subtle hover highlight on top of stars-given styling.
// .disabled          - Dims the button to indicate it cannot be used.
//
// Styleguide 2.1.3.
a.button.star{
  …
  &.star-given{
    …
  }
  &.disabled{
    …
  }
}
```

### **KSS Initial Setup**
1. Install kss-node and michelangelo theme project dependency:
```
npm install --save-dev kss michelangelo
```
2. Verify that it was installed by running
```
./node_modules/.bin/kss --version
```
3. Create a file named kss-config.json to configure our KSS settings.
```
{
  "title": "Title of the Style Guide",

  // Source tells KSS where the CSS, Sass, or SCSS is that it should parse for documentation comments. 
  // Here we are assuming your sass is in a directory at the root level of your project.
  "source": "sass/",

  // Destination tells KSS where to compile your style guide to.
  "destination": "styleguide/",

  // Builder tells KSS where to look for a theme. 
  // If you aren't using michelangelo, you don't need this.
  "builder": "node_modules/michelangelo/kss_styleguide/custom-template/",

  // CSS gives KSS the path to your CSS, so it can pull your styles into the style guide. 
  // The path needs to be relative to your style guide destination.
  // Here, our style guide is in /styleguide and our compiled css is at our project root.
  "css": [
    "../main.css"
  ],

  // If you want to include any javascript files, add this block, with the path to your javascript file. 
  // Also relative to your style guide destination.
 // Optional.
  "js" : [
    "../bundle.js"
  ]
}
```
4. Compile style guide by running:
```
./node_modules/.bin/kss --config kss-config.json
```
5. Or add a script to the scripts block in your `package.json` and npm run kss:
```
"scripts": {
  "kss": "kss --config kss-config.json"
},
```
6. We'll use the onchange package. First install it:

```
install onchange --save-dev
```
7. Then add a new script in our scripts object:
```
"scripts": {
  "watch": "onchange 'sass/**/*.sass' -- npm run kss",
  "kss": "kss --config kss-config.json"
},
```

#### **Helpers**
All documentation for helper functions should have a description section, parameters section, and compatibility section. The description section follows the same guidelines as style documentation.
 
Example of mixin documentation:

```
// Creates a linear gradient background, from top to bottom.
//
// $start - The color hex at the top.
// $end   - The color hex at the bottom.
//
// Compatible in IE6+, Firefox 2+, Safari 4+.
@mixin gradient($start, $end){
  …
}
```

## **4. Style Formatting Rules**
___

#### **Indentation and Spacing**
All SASS files should include indentation and spacing to make code more readable.
```
#nav {
    li {
        color:black;
    }
}
```

#### **Ordering Pseudo-Selectors**
All Pseudo-Selectors should follow the <strong>L</strong>o<strong>V</strong>e<strong>HA</strong>te ordering model:

```
a:link {
    color:black;
}

a:visited {
    color:blue;
}

a:hover {
    color:red;
}

a:active {
    color:purple;
}
```
#### **Ordering Short Hand Rules**
All Short Hand Rules should follow the <strong>TR</strong>ou<strong>BL</strong>ed ordering model:

```
margin-top:10px;
margin-right:20px;
margin-bottom:30px;
margin-left:40px;
```

#### **Sorting Properties**
All properties should be sorted in alphabetical order

```
#alphabetical-order {
    background:#000;
    color:black;
    z-index:9;
}
```

#### **Z-index**
All z-index rules should be grouped together in one SASS file.


#### **Responsiveness**
SASS files should include styles for mobile, tablet and desktop screens.


## **5. Useful Links**
___

1. [Knyle Style Sheets Documentation](http://warpspire.com/kss/syntax/)
2. [Structuring Your SASS Projects](https://itnext.io/structuring-your-sass-projects-c8d41fa55ed4)
3. [Options For Programmatically Documenting CSS](https://css-tricks.com/options-programmatically-documenting-css/#article-header-id-0)
4. [KSS Node Example](https://kss-node.github.io/kss-node/)
5. [Build Style Guide Straight SASS](https://css-tricks.com/build-style-guide-straight-sass/)
6. [Structuring and Organising SCSS Files](https://www.youtube.com/watch?v=VVsQts4pgF0)
7. [Best CSS reset libraries](https://cssauthor.com/css-reset-stylesheets/)