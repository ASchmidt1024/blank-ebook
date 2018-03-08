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

Continue in the templateDetails.xml. The date in `<creationDate>` should be set to the current date. Just take a format you want. Your name is in `<author>` tag. The `<copyright>` follows. `<authorEmail>` and `<authorUrl>` are self explanatory. In `<version>` you can specify which version of the template this is. A description of the templates can be stored under `<description>`. You can use HTML here. The rest can remain as it is for the moment. Later on, when you set the module positions, you will need this file again. Save the file and you'll see that your changes in the backend (Extensions > Templates > Templates. Yes, you read it right: Double 'Templates'. Do you work as a freelancer? It is awesome to explain this path to your client on the phone). The template is now ready for development.

Optional, replace the template\_preview.png, template\_thumbnail.png and the favicon.ico with your own. You'll find all three files in the root of your template folder.


