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
                    <i class="fas fa-user"></i>
                    <i class="far fa-user"></i>
                    <i class="fab fa-github-square"></i>
                </div>
            </div>
        </div>


        <jdoc:include type="modules" name="debug" />
        <script src="templates/frontend/build/app.js"></script>
    </body>

Well, the first line opens the body area with two specific class values: `$active->alias` and `$pageclass`. Maybe you still have recognized it, that every time you create a new menu item in the backend, Joomla!™ creates an alias of this item automatically. It will be created throught the item title in lowercase and empty spaces will be replaced with separators. This alias is predestined to be a class name. So we take it and give it to the body. And yes, at the menu item you are able to leave an extra page class. This page class is also taken for the body class.

The seven lines after `SHOW ME YOUR AWESOME CODE` are example code in the bootstrap way. Three divs contains one jdoc. You can read it in the [official Bootstrap documentation](http://getbootstrap.com/), that containers are required when using the grid system. It uses a series of containers, rows and columns to layout and align content. 'It’s built with [flexbox](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Using_CSS_flexible_boxes) and is fully responsive.' The above example creates one column in full width (the basic grid system has 12 columns) to display the content of each component of Joomla!™, e.g. articles. This will be done with `<jdoc:include type="component" />` and can only be once in every template. The following three i tags are for preview some icons of Font Awesome (a solid icon, a regular icon and a brand icon).

One module follows the component: `<jdoc:include type="modules" name="debug" />`. If you turn on the debug mode in your configuration of your awesome CMS, the output will shown in the frontend in exactly this place. You need to do the same with all your module positions; later more.

Finally, and as an very old developer (40 y, call me grandpa) long awaited, the one and only javascript of the website before the closing body tag: `<script src="templates/frontend/build/app.js"></script>`. This file will be created with Gulp. But before going into gulpfile.js, we just take a look at the logic.php. It takes only five minutes.

## logic.php

The logic.php file is being included in the index.php. While the index.php stands for the HTML output, the logic.php represents the programming logic. During template development, it is not unusual that the file is further programmed.

First to make sure that this file is called from Joomla!™ only, the following line is written at top.

    <?php defined( '_JEXEC' ) or die;

This code prevents that the file can not be accessed from the address bar of your browser.

### Declaring variables

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

### generator tag

The generator tag tells the world that we build this site with Joomla!™. Something nobody needs to know, least of all undesirables who want to hack your site. Do we want it? No, we most certainly do not!

    $this->setGenerator(null);

We are the web developers and we are the ones that need to know what the source code actually is. Nobody else should. Hackers need to know what CMS your using, in order to hack it. Why make it any easier than necessary?

Supposing your want to want to tell the world your website runs on Drupal or WordPress? No problem. Just fill in Drupal or WordPress between the single quotes. Or anything that you like:

    $this->setGenerator('Drupal');

This will generate `<meta name="generator" content="Drupal" />` in the outputted source code of your website.

### Unset JavaScript

As web developer you should have the full power over your website. In order to that you should unset some JavaScripts, because you want to put this JavaScripts in one single file, referenced before the closing body tag. And if you can take this JavaScripts, you can compressing and uglifiying them. This is the best case for performance. However, the following lines unset some scripts.

    unset($doc->_scripts[$this->baseurl .'/media/jui/js/jquery.min.js']);
    unset($doc->_scripts[$this->baseurl .'/media/jui/js/jquery-noconflict.js']);
    unset($doc->_scripts[$this->baseurl .'/media/jui/js/jquery-migrate.min.js']);
    unset($doc->_scripts[$this->baseurl .'/media/jui/js/bootstrap.min.js']);
    unset($doc->_scripts[$this->baseurl .'/media/system/js/caption.js']);
    unset($doc->_scripts[$this->baseurl .'/media/system/js/core.js']);
    unset($doc->_scripts[$this->baseurl .'/media/system/js/tabs-state.js']);
    unset($doc->_scripts[$this->baseurl .'/media/system/js/validate.js']);

Each line calls the unset function. This functions gets access to the document ($doc), especially to the scripts (\_scripts). Then, only the path to each script is needed to execute the function correctly. And yes, not only scripts will be loaded in the head. Some plain JavaScript code appears there too. Muah! Lets unset this.

    if (isset($doc->_script['text/javascript']))
    {
        $doc->_script['text/javascript'] = preg_replace('%jQuery\(window\)\.on\(\'load\'\,\s*function\(\)\s*\{\s*new\s*JCaption\(\'img.caption\'\);\s*}\s*\);\s*%', '', $doc->_script['text/javascript']);
        $doc->_script['text/javascript'] = preg_replace("%\s*jQuery\(document\)\.ready\(function\(\)\{\s*jQuery\('\.hasTooltip'\)\.tooltip\(\{\"html\":\s*true,\"container\":\s*\"body\"\}\);\s*\}\);\s*%", '', $doc->_script['text/javascript']);
        if (empty($doc->_script['text/javascript']))
        {
            unset($doc->_script['text/javascript']);
        }
    }

This JavaScript belongs to the image caption and the tooltip via jQuery. We don't need and and if we need it in the future, we will do it the Bootstrap way. Okay, here you need a little structure to control, if the unset is really needed. You do it with a simple if statement. So if some plain script (text/javascript) exists (isset), then there should be a replacement (preg_replace). One replacement function is looking for some jQuery, that activate the JCaption function, a function for image captions. Another replacement is looking for the hasTooltip function, a function - you guess it right - to activate tooltips.

Keep in mind that some scripts belong in the head, e.g. modernizr. If this is the case you shouldn't unset them. Well done.

You get it off. The head is cleaned from any script.

### Template CSS

To access the one and compressed CSS file of your template, you only need this line:

    $doc->addStyleSheet($tpath.'/build/main.css');

This will instruct the $doc variable to add main.css by the addStyleSheet function with the path to it. Continue reading to know how this file will be generated.

## gulpfile.js

> gulp is a toolkit for automating painful or time-consuming tasks in your development workflow, so you can stop messing around and build something. ~ [gulp.js](https://gulpjs.com/)

You are using Gulp to get the current version of [Bootstrap](http://getbootstrap.com/) and [Font Awesome](https://fontawesome.com/). Another task of Gulp will be to compile your SASS to CSS and compress it. All JavaScripts will be concatinated and compressed to one file. Last but not least you automate a browser reload after every change, so you havn't to do it manually. All this comes with Gulp plugins and will save your time. Well, lets take a look into the gulpfile.js in your template root folder.

### Declaring variables

To use a plugin in Gulp you have to create a variable for it. With a variable you can write a task to use the plugin for his work.

    var gulp        = require('gulp');
    var concat      = require('gulp-concat');
    var sass        = require('gulp-sass');
    var uglify      = require('gulp-uglify');
    var runSequence = require('run-sequence');
    var browserSync = require('browser-sync').create();

First gulp itself is declared. concat holds the [gulp-concat](https://github.com/gulp-community/gulp-concat) plugin, to put many files into one file. The plugin [gulp-sass](https://github.com/dlmanning/gulp-sass) will be used as sass compiler to generate and compress your CSS. uglify holds the [gulp-uglify](https://github.com/terinjokes/gulp-uglify) plugin, which is a JavaScript parser, minifier, compressor and beautifier toolkit with [UglifyJS3](https://github.com/mishoo/UglifyJS2). The plugin [run-sequence](https://github.com/OverZealous/run-sequence) runs a sequence of gulp tasks in the specified order. For time-saving synchronised browser testing you're using [browser-sync](https://browsersync.io/). All these plugins will be installed when you install the template through `npm install`.

### Current Bootstrap

It's time for the first Gulp task called 'bootstrap' to get the new versions of - you guess it right - Bootstrap.

    gulp.task('bootstrap', function() {
        return gulp.src('node_modules/bootstrap/scss/**/*')
            .pipe(gulp.dest('scss/bootstrap'));
    });

After installing the template via npm the Node.js® package manager gets the current versions of Bootstrap and copies the files in a specific folder. This folder will be used as source folder to get all files in there, your are using placeholders like \*\* and \*. The first placeholder \*\* is for any directory in the folder, the second \* for any file. The destination folder for the files is the scss and the font folder of the template.

### Compiling SASS

To compile your SASS to CSS the gulpfile.js contains another task called 'sass'.

    gulp.task('sass', function() {
        return gulp.src(['scss/main.scss'])
            .pipe(sass({outputStyle: 'compressed'}))
            .pipe(gulp.dest('build'))
            .pipe(browserSync.stream());
    });

First line is to declare the task 'sass' as a function. It will take the main.scss as source and compile and compress it with the sass plugin. The final destination is the build folder in your template directory. After that the browser should be reload automatically through browserSync.

### Uglifying JavaScript

The code to bring all JavaScripts together is written in the task 'js'.

    gulp.task('js', function() {
        return gulp.src([
            'node_modules/jquery/dist/jquery.slim.min.js',
            'node_modules/popper.js/dist/umd/popper.min.js',
            'node_modules/bootstrap/dist/js/bootstrap.min.js',
            'js/script.js'
            ])
            .pipe(concat('app.js'))
            .pipe(uglify())
            .pipe(gulp.dest('build'))
            .pipe(browserSync.stream());
    });

Four files should be the source. The first three belongs to Bootstrap and the last one called script.js is for your own scripting. With concat your will bring them together. After that only one file is left: 'app.js'. This file will be minified and compressed before put it into the build folder of your template. Finally the browserSyn reloads your browser automatically. Magic!

### Starting a server

Well, you don't want to call every task manually after a change. Gulp can do it for your by watching all necessary files and after a change, it runs the specific task.

    gulp.task('serve', ['sass'], function() {
        browserSync.init({
            // server: './'' // default server
            // proxy: 'http://localhost:8888/' // mamp
            proxy: 'http://localhost/blank5/' // usualy
        });
        gulp.watch(['js/**/*.js'], ['js']);
        gulp.watch(['scss/**/*.scss'], ['sass']);
        gulp.watch('*.php').on('change', browserSync.reload);
    });

This task 'serve' initializes the browserSync by watching all php, js and scss files of your template. To run it correctly change the proxy path with the path of your browser address (e.g. 'http://localhost/blank5/'). This is the address of your Joomla!™ frontend. So if you change your script.js the task 'js' will be done and if you change your \_custom.scss the task 'sass' will be done. Sexy.

### Default tasks

To start Gulp you only type `gulp` into your command line interface (cli). As default it should run all tasks in a specific order.

    gulp.task('default', runSequence('bootstrap','sass','js','serve'));

This task runs by runSequence and calls bootstrap, sass, js and serve in exactly this order.

## Navbar

Back to index.php. Its time to code. For the menu and the search you use the [Bootstrap Navbar](http://getbootstrap.com/docs/4.0/components/navbar/) and apply them to Joomla!™. Copy the following lines and paste them after the body tag.

    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <div class="container">
        <a class="navbar-brand"
          href="<?php echo $this->baseurl; ?>/">
           <?php echo $app->getCfg('sitename'); ?>
        </a>
        <button class="navbar-toggler"
          type="button"
          data-toggle="collapse"
          data-target="#nav-modules"
          aria-controls="nav-modules"
          aria-expanded="false"
          aria-label="Navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse"
          id="nav-modules"
        >
          <jdoc:include type="modules" name="navbar" />
        </div>
      </div>
    </nav>

The code looks harder than it is. Roughly speaking, it is here there to display the page name, the menu and the search on one line next to each other. On the left side the site name with the menu, and to the right a search box. Remark this in the code with comments, so later on you can find it back more easily.

First, you open a div with the class `navbar navbar-expand-lg navbar-light bg-light`. Bootstrap creates a (responsive) navigation menu. Its horizontal padding is removed at breakpoints lower than the specified `navbar-expand-lg` class. This ensures your are not doubling up on padding unnecessarily on lower viewports when your navbar is collapsed. Theming the navbar will be done by `navbar-light bg-light`. You can try `navbar-dark bg-dark` or `navbar-dark bg-primary` as well (take a look at [Color shemes](http://getbootstrap.com/docs/4.0/components/navbar/#color-schemes)). Although it’s not required, you can wrap a navbar in div with the class `container` to center it on a page.

What follows is the link to the site name. The class `navbar-brand` formats the presentation of the site name. The Joomla!™ API gives you a target (href) to the base URL. Important here is the slash (/) at the end. If you open a tag you have to close it, too. Normally you do it separat (e.g. `<div></div>`) but you can do it the short way (e.g. `<div />`), when no value between the opening and closing tag is needed. About the predefined variable $app you have to get the site name from the configuration and display it.

With the site name on the left the toggle button comes on the right. The toggler appears only on small devices. Its a `button` with the class `navbar-toggle`. The `data-toggle` attribute has the value `collapse`, so the navigation can toggle in and out. The target (attribute `data-target`) is the ID `#nav-modules`. Below you write in a div with the same ID (`#navbar-modules`) a module position called `navbar`.

Look at the result in the frontend. Apart from the site name nothing to see. Both the menu and the search should be created in the backend. But first we need to set the module positions.

## Module positions

In order to do it right you should define all module positions in the file templateDetails.xml. So the system has access to and the backend user can publish modules at this defined positions. Open the file in an editor of your choice and scoll to `<positions>`. There you'll find one predefined position called "debug". Add the following code:

    <position>navbar</position>
    <position>breadcrumbs</position>
    <position>largebar</position>
    <position>sidebar</position>

What? These are already listed? Well the template seems to be well written, hehe. Okay, the names are self-explanatory (always use a good naming convention!). The login should be published at the "sidebar" position. Maybe later you want to add another module there, so the name "sidebar" is better than "login" for this position. The "largebar" is intended for visitors with large displays. One you defined the module positions, save and close the file.

## Boilerplate text

Now it'is time to make some preparations in the backend. You create a blank article for building the menu. First create an item with some boiler plate text. Click in Content > Articles > New and set the title "HTML Ipsum Presents". You can copy the following text:

    <p><strong>Pellentesque habitant morbi tristique</strong> senectus et netus et malesuada fames ac turpis egestas. Vestibulum tortor quam, feugiat vitae, ultricies eget, tempor sit amet, ante. Donec eu libero sit amet quam egestas semper. <em>Aenean ultricies mi vitae est.</em> Mauris placerat eleifend leo. Quisque sit amet est et sapien ullamcorper pharetra. Vestibulum erat wisi, condimentum sed, <code>commodo vitae</code>, ornare sit amet, wisi. Aenean fermentum, elit eget tincidunt condimentum, eros ipsum rutrum orci, sagittis tempus lacus enim ac dui. <a href="#">Donec non enim</a> in turpis pulvinar facilisis. Ut felis.</p>

    <h2>Header Level 2</h2>

    <ol>
       <li>Lorem ipsum dolor sit amet, consectetuer adipiscing elit.</li>
       <li>Aliquam tincidunt mauris eu risus.</li>
    </ol>

    <blockquote><p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus magna. Cras in mi at felis aliquet congue. Ut a est eget ligula molestie gravida. Curabitur massa. Donec eleifend, libero at sagittis mollis, tellus est malesuada tellus, at luctus turpis elit sit amet quam. Vivamus pretium ornare est.</p></blockquote>

    <hr id="system-readmore" />

    <h3>Header Level 3</h3>

    <ul>
       <li>Lorem ipsum dolor sit amet, consectetuer adipiscing elit.</li>
       <li>Aliquam tincidunt mauris eu risus.</li>
    </ul>

    <pre><code>
    #header h1 a {
      display: block;
      width: 300px;
      height: 80px;
    }
    </code></pre>

This text was written by Chris Coyiers on his site [html-ipsum.com](http://html-ipsum.com/) and is called Kitchen Sink. It's a good boiler plate text with some elements, that might be appear on your website. Before the third title `<h3>` we place a "Read more" link. Well, make it a featured article (Featured > Yes) and Save & Close it. Now under Options > Articles hide the following entries near the bottom:

- Show Icons > Hide
- Show Print Icon > Hide
- Show Email Icon > Hide
- Show Hits > Hide

Open the frontend in another tab to preview the result. Ah, yeah! Looks good.

(to be continued)


