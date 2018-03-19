# Bootstrap Tutorial

In this guide you will learn how to use BL4NK with Bootstrap in order to create responsive web design. It will be locally developed. A prerequisite is an installed local web server, Node.js® and - of course - the latest version of Joomla!™ without content. The instructions are written so as you code it in practice, it is often switched back and forth. Only this way the individual steps are easy to understand and the learning effect remains high. The aim is to develop a finished device independent template under the use of Joomla!™, Node.js®, Bootstrap and SASS. Have fun!

## Requirement

* [XAMPP](https://www.apachefriends.org/) or [MAMP](https://www.mamp.info) (or any local web server)
* [Joomla!™](https://www.joomla.org/) (without content)
* [Node.js®](http://nodejs.org/) (should be installed)
* [Gulp](https://gulpjs.com/) (will be installed)

What you further need

- [Blank Bootstrap Edition](https://github.com/Bloggerschmidt/Blank-Bootstrap-Edition/releases/latest)
- [Journal](https://bootswatch.com/journal/) Bootstrap Theme

Good to know

- [Bootstrap Documentation](http://getbootstrap.com/)
- [Template Snippets](https://gist.github.com/Bloggerschmidt/2360208)

## Installation

First download the latest version of [Blank Bootstrap Edition](https://github.com/Bloggerschmidt/Blank-Bootstrap-Edition/releases/latest). Install it in the backend of Joomla!™ under Extensions > Manage > Install > Upload Package File. After successful installation choose the template called _frontend_ as default template under Extensions > Templates > Styles. Now it is active and can be viewed in the front end. Just click on the preview link at the top right. It is recommended to use two tabs in your browser (back end and front end) to work with.

Unfortunatly, you have to install the template twice, to automate and enhance your workflow. First keep shure you have installed [Node.js®](http://nodejs.org/). If Node.js® is installed, install Gulp via command prompt. Just open a console or a terminal.

    npm install -g gulp

Now change your path to the template directory. Install all dependencies.

    npm install

Run Gulp to compile, compress and build.

    gulp

Magic!

## Preparation

Before we get into details, you should give your (!) template a personal touch. Open the file templateDetails.xml in your template folder under JOOMLA-ROOT/templates/frontend/. This file is an XML file and must be filled in with your data. You can keep the `<name>` frontend. If you want to change your template name into something else, you should do that before (!) you install the template. The steps are the same, only that you unzip Blank Bootstrap Edition, change the name frontend in templateDetails.xml, rename the folder, zip the template (the renamed folder) and install it in the backend. If you want to do it right now, you should deinstall the current template. Keep shure you take another template as default before.

Continue in the templateDetails.xml. The date in `<creationDate>` should be set to the current date. Just take a format you want. Your name is in `<author>` tag. The `<copyright>` follows. `<authorEmail>` and `<authorUrl>` are self explanatory. In `<version>` you can specify which version of the template this is. A description of the templates can be stored under `<description>`. You can use HTML here. The rest can remain as it is for the moment. Later on, when you set the module positions, you will need this file again. Save the file and you'll see that your changes in the backend (Extensions > Templates > Templates. Yes, you read it right: Double 'Templates'. Do you work as a freelancer? It is awesome to explain this path to your client on the phone).

BL4NK comes with a little feature called 'browserSync'. Everytime you save your changes in PHP, CSS or JavaScript, the browser will be reloaded automatically. So that can happen you should change the path in gulpfile.js in your template folder. Open the file and search for the `serve` function. Change the line

    proxy: 'http://localhost/blank/'

to your local developing path, the address of your front end in the browser. E.g.

    proxy: 'http://localhost/my-awesome-website/'

We will get into the other functions later. The template is now ready for development.

Optional, replace the template\_preview.png, template\_thumbnail.png and the favicon.ico with your own. You'll find all three files in the root of your template folder. You can use [this PSD files](http://itr.im/psd) to create your own images.

## index.php

The file index.php is at the heart of each template. This is where all files converge. It is largely responsible for the source code and in the end it's all about creating and influencing the source code. Open it! We go through step by step, before you start coding.

The first line is written in PHP `<?php defined( '_JEXEC' ) or die;`. With `<?php` you open the PHP area (which should be closed with `?>` again) and with `defined( '_JEXEC' ) or die` you forbid direct access to this file. This is done via the Joomla!™ API with the \_JEXEC command. This statement checks to see if the file is being called from within Joomla!™ and it protects your site by making it more difficult for a cracker/hacker to damage your site.

With the next line you include the logic.php file.

    include_once JPATH_THEMES.'/'.$this->template.'/logic.php';

This file holds the variables and program logic of the template. It will be explained after index.php. JPATH_THEMES is a [constant of Joomla!™](https://docs.joomla.org/Constants) and with `$this->template` we get the current template.

### head

> Zombie, zombie, zombie  
> Hey, hey  
> What's in your head, in your head  
> Zombie, zombie, zombie  
> Hey, hey, hey  
> Oh, do, do, dou, do, do, dou, do, do  
> Dou, do, do, dou, dou, do, do, dou  
>  
> (Part of the songtext: The Cranberries - Zombie)

What follows is an HTML document. The declaration of `<!doctype html>`, `<html>` and `<head>`.

    <!doctype html>
    <html lang="<?php echo $this->language; ?>">
    <head>
        <jdoc:include type="head" />
    </head>

Yo, the first line is the document declaration, second line opens the html area with the attribute `lang` with the site specific language shortcut (e.g. `en`). This will be done with php `echo $this->language;`. The head area follows and contains a Joomla!™ specific code to include all the head stuff. With this line the CMS is able to load scripts, links, metas, title and all the invisible but necessary things of your website. If the template is already installed, take a look at the source code of the frontend and you will see all the stuff.

### body

The body contains all the visible stuff of your site.

    <body class="<?php echo $active->alias . ' ' . $pageclass; ?>">

        <!--
            SHOW ME YOUR AWESOME CODE
        -->
        <div class="container">
            <div class="row">
                <div class="col-12">
                    <jdoc:include type="component" />
                </div>
            </div>
        </div>


        <jdoc:include type="modules" name="debug" />
        <script src="templates/frontend/build/app.js"></script>
    </body>

Well, the first line opens the body area with two specific class values: `$active->alias` and `$pageclass`. Maybe you still have recognized it, that every time you create a new menu item in the backend, Joomla!™ creates an alias of this item automatically. It will be created throught the item title in lowercase and empty spaces will be replaced with separators. This alias is predestined to be a class name. So we take it and give it to the body. And yes, at the menu item you are able to leave an extra page class. This page class is also taken for the body class.

The seven lines after `SHOW ME YOUR AWESOME CODE` are example code in the bootstrap way. Three divs contains one jdoc. You can read it in the [official Bootstrap documentation](http://getbootstrap.com/), that containers are required when using the grid system. It uses a series of containers, rows and columns to layout and align content. 'It’s built with [flexbox](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Using_CSS_flexible_boxes) and is fully responsive.' The above example creates one column in full width (the basic grid system has 12 columns) to display the content of each component of Joomla!™, e.g. articles. This will be done with `<jdoc:include type="component" />` and can only be once in every template.

One module follows the component: `<jdoc:include type="modules" name="debug" />`. If you turn on the debug mode in your configuration of your awesome CMS, the output will shown in the frontend in exactly this place. You need to do the same with all your module positions; later more.

Finally, and as an very old developer (40 y, call me grandpa) long awaited, the one and only javascript of the website before the closing body tag: `<script src="templates/frontend/build/app.js"></script>`. This file will be created with Gulp. But before going into gulpfile.js, we just take a look at the logic.php. It takes only five minutes.

## logic.php

The logic.php file is being included in the index.php. While the index.php stands for the HTML output, the logic.php represents the programming logic. During template development, it is not unusual that the file is further programmed.

First to make sure that this file is called from Joomla!™ only, the following line is written at top.

    <?php defined( '_JEXEC' ) or die;

This code prevents that the file can not be accessed from the address bar of your browser.

Some variables for the proper use of the template are required. [The basics of PHP variables](http://de2.php.net/manual/en/language.variables.basics.php) can be found in PHP manual (for beginners: [A simple tutorial in PHP](http://php.net/manual/en/tutorial.php)).

In a nutshell:

- The first character of each PHP variables is the dollar sign $. This is followed by the variable name. 
- Distinction is made between uppercase and lowercase. 
- $My\_variable is not the same as $my\_variable or $My\_Variable. 
- The dollar sign must be followed by a letter or an underscore (_). 
- Spaces are not allowed. $\_my\_variable is okay, $ my\_variable is not. 

    // variables 
    $app = JFactory::getApplication(); 
    $doc = JFactory::getDocument(); 
    $menu = $app->getMenu(); 
    $active = $app->getMenu()->getActive(); 
    $params = $app->getParams(); 
    $pageclass = $params->get('pageclass_sfx'); 
    $tpath = $this->baseurl.'/templates/'.$this->template; 

Most of the variable names are quite self-explanatory. Not so for the contents of the variables, a little explanation is in order. Let's go line by line:

    $app = JFactory::getApplication();

The variable $app is created, the content in the Joomla!™ framework is called for by the JFactory. The application to which it refers to is Joomla!™ itself, the CMS. The variable $app we will also need for the parameters.

    $doc = JFactory::getDocument();

Similarly, here comes the variable $doc. Again, we put the Joomla!™ framework to work with the JFactory class. This variable will take care of the RSS feeds within the page, site information, such as the title and description, references to the JavaScript and CSS files being loaded and will do a lot more. However, that is beyond the scope of this book.

    $menu = $app->getMenu();

This variable points to the menu within the $app variable.

    $active = $app->getMenu()->getActive();

This variable goes a step further: It looks for the active menu item within the $menu. It also checks if this is the home page or not.

    $params = $app->getParams();

Using the variable $app we'll query Joomla!™ for the parameters and store that in the variable $params. We will then use to query the page class:

    $pageclass = $params->get('pageclass_sfx');

A rather aptly named variable, $pageclass. The page class suffix is a parameter in Joomla!™ menu items. It can be set in each menu item: [Edit] screen under the "Parameters (Advanced)" section. This will order Joomla!™ to either add a new CSS class or modify the existing CSS class for elements in this specific menu item layout.

    $tpath = $this->baseurl.'/templates/'.$this->template;

That's easy: Variable $tpath contains the relative path to the template directory from the base URL. The $tpath variable is told to look for the active template folder from the base url.

These are all the variables used in BL4NK.



(to be continued)


