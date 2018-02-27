# BL4NK

BL4NK is a great starting point for a new Joomla!™ template project. It's a fully functional template (can be installed directly) and has responsive support. Internet Explorer is obsolete,  HTML5 and CSS3 are the present. And that is how I build BL4NK. HTML5 tags can be used that all browsers correctly interpret. The CSS file [Normalize.css](http://necolas.github.io/normalize.css/) is to all values neutral and independently to render by the browser. It is a advanced HTML5 alternative to the last CSS resets. All style sheets will be combined in one file and load compressed, which are compiled by [Gulp](https://gulpjs.com/) before. The browser loads only a single CSS file with just one line. You can't get it any faster than that.

To write your CSS you can choose between [LESS](http://lesscss.org/) and [SASS](https://sass-lang.com/). Wait a moment, you don't know both? LESS and Sass are preprocessors of CSS. Similar to PHP and HTML you can write code with them that will put out clear CSS. You will use LESS or SASS to write CSS more effective. You can use variables, e.g. to use the same hexadecimal color values on different points. There are a lot of functions, also, and much more. We will get it later.

Then there is a [BL4NK Bootstrap Edition](https://github.com/Bloggerschmidt/Blank-Bootstrap-Edition) (short BBE). For those of you who don't know [Bootstrap](http://getbootstrap.com/): you should! Bootstrap allows you to design a template responsive with mobile-first strategy. If you are using the grid system your template will be responsive for desktops, tabletts and smartphones. Frameworks and APIs (Applications Programming Interfaces) make your life easier. If you are use them, your coding will be much faster as stand alone coding.

## Features

- Loading brutally fast 
- Start browsing through constant normalize.css 
- CSS compressor
- Integrated LESS and SASS compiler
- Support for desktops, tablets and smartphones
- Own error, offline and print pages 
- [BL4NK Bootstrap Edition](https://github.com/Bloggerschmidt/Blank-Bootstrap-Edition)
- Great icons in Bootstrap with Font Awesome 

## PSD 

Download [psd.zip](http://itr.im/psd) (10.8 MB) to create icons and preview images faster. The ZIP package contains the following files: 

- App Icon Template [2.0] .psd 
- template_preview.psd 
- template_thumbnail.psd

All files in Blank, starting with the most important file named index.php until favicon.ico will be explained in the following. However, as said by Sherlock Holmes: "To a great mind, nothing is little". And so it is. Every detail is important! 

Following the Unix principle, each file is a text file and can be opened and edited with your editor. Okay, okay - for image files you'd rather use an image editing program. 

# Overview

Have you downloaded the Blank Template and unpacked, find you the following folders and files:

- build
- css
- js
- .gitignore
- component.php
- error.php
- favicon.ico
- gulpfile.js
- index.php
- logic.php
- offline.php
- package.json
- README.md
- template_preview.png
- template_thumbnail.png
- templateDetails.xml

Strictly speaking, you only need two files to create a working template: 

- index.php 
- templateDetails.xml 

Combining these two files gives you [Mini](https://github.com/Bloggerschmidt/Mini), the template with the smallest possible number of files. Follow the idea of minimalism further and look for the smallest index.php in the world. 

## index.php (Mini)

The index.php file is the core of the template.  This makes all the files work together. It is crucial for the source code responsible and ultimately it's all about the source to create and influence. 

The minimal structure of the index.php looks like this: 

    <?php defined('_JEXEC') or die; ?>
    <!doctype html>
    <html>
      <head>
        <jdoc:include type="head" />
      </head>
      <body>
        <jdoc:include type="message" />
        <jdoc:include type="component" />
      </body>
    </html>

The first line is written in PHP. The good thing about PHP and HTML is that it can be written together. You can add PHP statements in an HMTL file, and vice versa. `<?php`  opens  a PHP statement - no matter where - and `?>`  closes it again. In the first line we forbid direct access to this file. This is done via the Joomla!™ API with the `_JEXEC` command. This statement checks if the file is being called from within a Joomla!™ session and it protects your site by making it more difficult for a hacker to damage your site.

On line two we declare with `<!doctype html>` the document type. This line is one of the many little improvements in HTML5. Before HTML5 cryptic document types had to be declared for each different version and every application. Long arcane lines of code, impossible to jot down from memory. This was necessary to ensure browsers correctly interpret the source code. With HTML5 that's over, because it is backward compatible.

What follows in line three, is the smallest possible construction of a HTML page. This page is opened with `<html>` and ends with `</html>`. The header section begins with `<head>` and ends with `</head>`. The body starts with `<body>` and ends with `</body>`. Within the header area while we load the header information with `<jdoc: include type="head" />` from the Joomla!™ (API) in line five. This `jdoc:include` command will include the normal header information a website needs. It is a Joomla!™ statement that picks up the necessary bits from your Joomla!™ configuration. For example, the global metadata of the system load, the css stylesheets, JavaScripts and the RSS feeds.

The `jdoc:include` command you'll find twice more in the index.php: once as message type and then as a component type (on lines 8 and 9). In line eight we see `<jdoc:include type="message" />`, this makes the system messages work.  Whenever Joomla!™ needs to talk to you, this line will show it on your screen. For example, if you send an email on a contact form, you'll see the message “your message has been successfully send” after you hit the send button. 

Last item to discuss is `<jdoc:include type="component" />` in line nine. This element should only appear once in the `<body>` element of the template to render the main content of the page with respect to the current page being viewed. So, enough explained. This is how the generated source looks like:

    <!doctype html>
    <html>
     
    <head>
      <base href="http://localhost/joomla/" />
      <meta http-equiv="content-type" 
            content="text/html; charset=utf-8" />
      <meta name="generator" content="Joomla! ..." />
      <title>Home</title>
      <link href="http://localhost/joomla/?view=featured" 
            rel="canonical" />
      <link href="/joomla/index.php?format=feed&amp;type=rss" 
            rel="alternate" type="application/rss+xml" 
            title="RSS 2.0" />
      <link href="/joomla/index.php?format=feed&amp;type=atom" 
            rel="alternate" type="application/atom+xml" 
            title="Atom 1.0" />
      <link href="/joomla/templates/frontend/favicon.ico" 
            rel="shortcut icon" 
            type="image/vnd.microsoft.icon" />
      <script src="/joomla/media/system/js/mootools-core.js" 
            type="text/javascript"></script>
      <script src="/joomla/media/system/js/core.js" 
            type="text/javascript"></script>
      <script src="/joomla/media/system/js/caption.js" 
            type="text/javascript"></script>
      <script type="text/javascript">
        window.addEvent('load', function() {
          new JCaption('img.caption');
        });
      </script>
    </head>
     
    <body>
      <div id="system-message-container">
        <div id="system-message"></div>
      </div>
      <div class="blog-featured">
        <div class="page-header">
          <h1>Home</h1>
        </div>
      </div>
    </body>
     
    </html>

The code begins with the document type `<!doctype html>` on line one. Followed by the `<html>` tag on line two. The next line, line three, begins the header information with `<head>`. Here the header information loaded (base, meta, title, link and script). In the body `<body>` to display a div an `id="system-message-container"` for system messages and the div `class="blog featured"` for the actual content. In the last div (line 25) the article title as the title as a first degree heading (h1) is generated.

This source-code comes from the default settings of a content-less Joomla!™ installation. The global meta-data (keywords and description) are not defined and are therefore not displayed. In the previous main-menu the entry "Home" is responsible for the title and heading. This entry is specified as a blog layout hence the class "blog-featured" with activated feed display. Therefore the links in the head-section are titled "RSS 2.0" and "Atom 1.0". On the remaining source-code - for now - you don't have an impact on the backend. At a later stage you will get a chance to take influence on the meta tag called "generator" with code snippets and to take out unneeded JavaScripts. Besides JavaScripts belong to the end of the HTML page before the closing body tag `</body>`. To increase performance, all JavaScripts should be loaded combined and compresses into a single file. There are exceptions, such as the JavaScript modernizr.js, which expressly is to be included in the head-section `<head>`. So much for the generated source code of the minimal index.php.

## templateDetails.xml (Mini)

The file templateDetails.xml (note the capital D) is the second most important file after index.php within the template. The templateDetails.xml includes general template information (name, author, etc.) and defines the installation routine. The installation routine is nothing else than a listing of all folders and files that belong to the template, in order to have them unpacked and stored with the installation. Additionally the module positions are stored here in order to be integrated via the `jdoc:include` command in the index.php. Optionally, you can create parameters to make the template adjustable within the backend. Perhaps you want your template to shine in different colours, then you adjust those parameters. How about a pretty pink as in the BEEZ template (Joomla!™ 1.5), for example?

Now please, check out the minimum version of templateDetails.xml:

    <?xml version="1.0" encoding="utf-8"?>
    <!DOCTYPE install Public "-//Joomla! 2.5//DTD template 1.0//EN" 
      "http://www.joomla.org/xml/dtd/1.6/template-install.dtd">
     
    <extension version="3.8" type="template" method="upgrade">
       <name>mini</name>
       <creationDate>14.01.14</creationDate>
       <author>Alexander Schmidt</author>
       <copyright>Copyright © 2018 Alexander Schmidt</copyright>
       <authorEmail>alexander.schmidt@edvas.de</authorEmail>
       <authorUrl>https://alexanderschmidt.info</authorUrl>
       <version>1.0.0</version>
       <description>The smallest template ever.</description>
       <files>
          <filename>index.php</filename>
          <filename>templateDetails.xml</filename>
       </files>
       <positions>
          <position>debug<position>
       </positions>
    </extension>

What do you see here? The first line creates (similar to PHP) an XML section determining version and character set (utf-8). Then comes, what a horror, the document type declaration. Here you will probably want to see the same concept, which was responsible for simplifying the document type in HTML5. But what do you find instead? A declaration, which you and I and the creators of XML simply could not write down from memory. Oh no! But luckily we have the BL4NK where everything is already pre-coded. Phew! Further explanations on this can be avoided as under the given joomla.org address there is no file to be found. And you're right if you ask yourself: Why bother?

Fine! Lets get to the fun part of templateDetails.xml. It begins with the install-section that includes the Joomla!™ version for which the template is determined. The type is called "template". The `method="upgrade"` allows the template to install over an existing version at a later stage (do you smell the danger?). Thereby newer versions of the files will be installed. However old files that are no longer needed will remain, thus will not be deleted. Next are the template's general information (template name, creation date, author, copyright, e-mail address, website, version and description) being displayed within the template manager in the Joomla!™ backend. After this the installation routine is listed. Folders `<folder>` and files `<filename>` are embedded belonging to the template. The module `<positions>` find their place hereafter. Each position is written on a separate line and is now ready to be integrated into the index.php. This file is also selectable via the module manager in the Joomla!™ backend.

If you would copy the two test files index.php and templateDetails.xml in a folder called mini and zip it into a file (.zip) you could successfully install this mini template in Joomla!™.

The mini template is not all suited as the starting point of your template development and is therefore going to be extended. Essential components of the extensions are:

- LESS and SASS compiler
- CSS files
- error, offline and print pages

## Cascading Style Sheets

The Cascading Style Sheets of Blank are located in folder css. If you open this folder, you find other files beside the css files:

- custom.css
- editor.css
- error.css
- normalize.css
- offline.css
- print.css
- template.css
- template.less
- template.scss

The files template.less and template.scss are not css files. For what are these files?

### template.less

LESS is a preprocessor of CSS. Or to say it with the official words: [It's CSS, with just a little more.](http://lesscss.org/). So, you can write simple CSS in every LESS-file. Maybe for someone is CSS enough, but to build more complex templates imports, variables, functions, advanced selectors, mixins and a lot more could be usefull. You will get a very short overview of what LESS offers. For a deep dive read the official documentation.

[LESS Documentation](http://lesscss.org/features/)

By installing BL4NK you install the LESS compiler and the compiling process comes with Gulp. With Gulp you compile your less files into css. More on this later.

Let's take a look into template.less.

    // FRONTEND LESS
    // ==========================================================================

    // This file will be used to generate the template.css

    html {

    }

    body {

    }



    @media (min-width: 768px) {}

    @media (min-width: 992px) {}

    @media (min-width: 1200px) {}

Well, "This file will be used to generate the template.css". There are only the comment at the first lines, two selectors `html` and `body` with no attributes and three media queries. This structure should give you the idea of the mobile first strategy. First you write your rules for mobile. If you do it well, there is no need to write other rules. This is called mobile only strategy. But maybe, there should display something in a different way, than you go with your definitions from mobile to tablett to desktop.

#### Imports

It is a good idea to put the styles of an object into a separate file and then import it to you main file. For example, if you want to design the navigation of a website, create a file called navigation.less. If it is created, you can import it to your template.less. The following statements can be used.

    @import "navigation";
    @import "navigation.less";

There are also [more options for @import At-Rules](http://lesscss.org/features/#import-atrules-feature), which you can read in the official manual of LESS.

#### Variables

Often you need the same value some times in your CSS. Variables make it easier to controll those values from a single location.

    @link-color: #B22222;
    
    a {
      color: @link-color;
    }

If you handle a lot of variables, it makes sense to put them in a separate file called variables.less.


#### Functions

You find a [list of all built-in functions supported by LESS](http://lesscss.org/functions/) on the main manual. Here is a short example of the function to darken a color.

    @link-color: #B22222;
    @link-color-hover: darken(@link-color, 10%);
    
    a {
      color: @link-color;
    }
    
    a:hover {
      color: @link-color-hover;
    }

#### Advanced selectors

With the ampersand `&` you can reference parent selectors the following way.

    a {
      color: @link-color;
      &:hover {
        color: @link-color-hover;
      }
    }

Compiling this LESS results in

    a {
      color: #B22222;
    }
    
    a:hover {
      color: #B22222;
    }

You can [take use of multiple `&` and change selector order](http://lesscss.org/features/#parent-selectors-feature) (follow the link).

#### Mixins

You can mix-in class and id selectors.

    .class, #id {
      color: red;
    }
    .mixin-class {
      .class();
    }
    .mixin-id {
      #id();
    }

Results in

    .class, #id {
      color: red;
    }
    .mixin-class {
      color: red;
    }
    .mixin-id {
      color: red;
    }

There is [a lot more what you can do with mixins](http://lesscss.org/features/#mixins-feature).

### template.scss

SASS is also a preprocessor of CSS. "Sass is the most mature, stable, and powerful professional grade CSS extension language in the world." SASS-files normally ends with .scss (in the past it was .sass, but with an upgrade it changes the ending). You can use imports, variables, functions, advanced selectors, mixins and a lot more. I will give you a short overview of what is possible. Take a look in the official documentation for deep diving.

[SASS Documentation](https://sass-lang.com/documentation/)

By installing BL4NK you install the SASS compiler and the compiling process comes with Gulp. With Gulp you compile your less files into css. More on this later.

Let's take a look into template.scss.

    // FRONTEND SASS
    // ==========================================================================

    // This file will be used to generate the template.css

    html {

    }

    body {

    }



    @media (min-width: 768px) {}

    @media (min-width: 992px) {}

    @media (min-width: 1200px) {}

Same like LESS above, "This file will be used to generate the template.css". There are only the comment at the first lines, two selectors `html` and `body` with no attributes and three media queries. This structure should give you the idea of the mobile first strategy. First you write your rules for mobile. If you do it well, there is no need to write other rules. This is called mobile only strategy. But maybe, there should display something in a different way, than you go with your definitions from mobile to tablett to desktop.

#### Imports

It is a good idea to put the styles of an object into a separate file and then import it to you main file. For example, if you want to design the navigation of a website, create a file called navigation.scss. If it is created, you can import it to your template.scss. The following statements can be used.

    @import "navigation";
    @import "navigation.scss";

There are also [@-Rules and Directives](https://sass-lang.com/documentation/file.SASS_REFERENCE.html#import), which you can read in the official manual of SASS.

#### Variables

Often you need the same value some times in your CSS. Variables make it easier to control those values from a single location.

    $link-color: #B22222;
    
    a {
      color: $link-color;
    }

If you handle a lot of variables, it makes sense to put them in a separate file called variables.scss.


#### Functions

You find a [list of all built-in functions supported by SASS](http://sass-lang.com/documentation/Sass/Script/Functions.html) on the main manual. Here is a short example of the function to darken a color.

    $link-color: #B22222;
    $link-color-hover: darken($link-color, 10%);
    
    a {
      color: $link-color;
    }
    
    a:hover {
      color: $link-color-hover;
    }

#### Advanced selectors

With the ampersand `&` you can reference parent selectors the following way.

    a {
      color: $link-color;
      &:hover {
        color: $link-color-hover;
      }
    }

Compiling this SASS results in

    a {
      color: #B22222;
    }
    
    a:hover {
      color: #B22222;
    }

[Referencing Parent Selectors: &](https://sass-lang.com/documentation/file.SASS_REFERENCE.html#parent-selector) (follow the link)

#### Mixins

You can mix-in class and id selectors.

    .class, #id {
      color: red;
    }
    .mixin-class {
      .class();
    }
    .mixin-id {
      #id();
    }

Results in

    .class, #id {
      color: red;
    }
    .mixin-class {
      color: red;
    }
    .mixin-id {
      color: red;
    }

There is [a lot more what you can do with mixins](https://sass-lang.com/documentation/file.SASS_REFERENCE.html#mixins).

### custom.css

This is a file for fixing styles in a fast way in the browser (Joomla!™ backend). It's bad to use it but sometimes you have to. So it is empty a ready for your fixes.

    /* CUSTOM
       ========================================================================== */

    /**
     * In best case you don't use this file.
     * It's for fast fixes in browser only.
     */

Only the comment shows you which file you just opened.

### editor.css

The editor.css file is used to display your own definitions in your Joomla WYSIWYG editor in the backend, if you use one. For example, the JCE editor. This is most popular editor, but there are many more. In the configuration of this editor it is possible to include your own stylesheets. And that's what we  do.

    /* EDITOR
       ========================================================================== */

    /**
    * This file is for backend editors like JCE.
    * It will be used for print style, too.
    */

    body {
        background-color: #fff;
        color: #000;
        font: normal normal normal 75%/125% arial,sans-serif;
    }

By default, the text appears black on a white background. It is highly advisable to use the same definitions as in template.css. You may ask yourself: "why not assign the same template.css to the editor?” Well, that usually leads to an ugly editor screen. Also, only some sections of the template.css are responsible for the content. You don't need the remainder. That's why we define what you need in a separate file, without the initial IDs and container classes.

### error.css

The file error.css is linked via the file error.php. Both files are used for the error output that appears when the user visits a non existent page (error 404). The standard Joomla!™ error 404 page is so ugly that it's necessary to code something better. Customized error pages are part of every good template and are therefore not something optional.

The default "error.css" definitions are as follows:

    /* ERROR
       ========================================================================== */

    html,
    body {
      height: 100vh;
    }

    body {
      color: #111;
      font-family: Arial,Sans Serif;
      font-size: 1rem;
      margin: 0;
      padding: 0;
      text-align: center;
    }

    #error {
      margin: 0 auto;
      padding: 20px;
      max-width: 100%;
    }

    @media (min-width: 768px) {
      #error {
        padding-top: 32vh;
        max-width: 400px;
      }
    }

    h1 {
      margin:0 0 20px 0;
    }

    .search label {
      display:none
    }

The body are the background and typography defined. The padding is set to zero and output the contents are centered (text-align). The container with the ID #error then defines padding and width. The heading (h1) gets a smaller margin. The label of the search box is set not to be displayed (`display:none`).

### normalize.css

The normalize.css file is a small CSS file written by [Nicolas Gallaghers](https://github.com/necolas/normalize.css). It provides better cross-browser consistency of our HTML tags. It is a modern HTML5 compliant alternative to the traditional CSS reset. In more then 400 lines of code the HTML tags are defined. Look it over in your editor, when you have some free time. Don't mess around with it! 

### offline.css

Just like the error page, the file offline.css is linked within offline.php. The offline page will appear when Joomla is set offline in the global configuration. The visitor will then see the information as defined in this configuration. The appearance (our CSS definitions), is stored in this file.

    /* OFFLINE
       ========================================================================== */

    html,
    body {
      height: 100vh;
    }

    body {
      color: #111;
      font-family: Arial,Sans Serif;
      font-size: 1rem;
      margin: 0;
      padding: 0;
      text-align: center;
    }

    img {
      border: 0 none;
    }

    #frame {
      margin: 0 auto;
      padding: 20px;
      max-width: 100%;
    }

    @media (min-width: 768px) {
      #frame {
        padding-top: 32vh;
        max-width: 400px;
      }
    }

    .inputbox {
      width: 130px;
    }

    form {
      margin: auto;
    }

    form p {
      margin: 0;
      padding: 0;
    }

    form fieldset {
      border: 0 none;
      margin: 0;
      padding: 0.2em;
    }

    input {
      padding: 5px;
      font-size: 1rem;
    }

    input.button {
      cursor: pointer;
      width: auto;
    }

    form p {
      padding: 0.3em 0;
    }

    label[for="remember"] {
      font-size: .85rem;
    }

    .alert {
      padding: 15px;
      margin-bottom: 20px;
      border: 1px solid transparent;
      background-color: #fcf8e3;
      border-color: #faebcc;
      color: #8a6d3b;
    }

    .alert h4 {
        margin-top: 0;
        margin-bottom: 10px;
        color: inherit;
        font-family: inherit;
        font-size: 18px;
        font-weight: 500;
        line-height: 1.1;
    }

    .close {
        float: right;
        font-size: 21px;
        font-weight: 700;
        line-height: 1;
        color: #000;
        text-shadow: 0 1px 0 #fff;
        filter: alpha(opacity=20);
        opacity: .2;
    }

    .close:focus,
    .close:hover {
        color: #000;
        text-decoration: none;
        cursor: pointer;
        filter: alpha(opacity=50);
        opacity: .5;
    }

### print.css

The print.css file is linked within the file component.php. Joomla offers to display the content as a print preview. This is done by clicking on the print icon. The icon's view can be set within the article options. Using this file enables you to define a printer-friendly output. You can, for example, increase the contrast of the text color to it's background to improve the readability. The background is best to be defined in white, to save printer ink.

In Blank the reset style sheet normalize.css is imported into the print.css file, also the file editor.css to create a printer-friendly version.

    /* PRINT
       ========================================================================== */

    @import url('normalize.css');
    @import url('editor.css');

### template.css

In this file, CSS is written which is created by the LESS or SASS compiler generated with the help of your style sheet file template.less or template.scss. You don't need to edit the template.css file.
