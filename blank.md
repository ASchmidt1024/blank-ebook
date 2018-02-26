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
- template.sass

The files template.less and template.sass are not css files. For what are these files?

### template.less

LESS is a preprocessor of CSS. Or to say it with the official words: [It's CSS, with just a little more.](http://lesscss.org/). So, you can write simple CSS in every LESS-file. Maybe for someone is CSS enough, but to build more complex templates imports, variables, functions, advanced selectors, mixins and a lot more could be usefull. 

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

### template.sass




