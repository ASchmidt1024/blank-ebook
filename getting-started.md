# Getting Started

This template is for local developing under [Node.js®](http://nodejs.org/) and [Gulp](https://gulpjs.com/). A good workflow is to code your template on localhost and if it is ready to deploy it on the live server \(e.g. copy via sftp\). And for shure, you should have a [Joomla!™](https://www.joomla.org/) installation ready for this.

## Requirements

* [XAMPP](https://www.apachefriends.org/) or [MAMP](https://www.mamp.info) \(or any local web server\)
* [Joomla!™](https://www.joomla.org/) \(should be installed\)
* [Node.js®](http://nodejs.org/) \(should be installed\)
* [Gulp](https://gulpjs.com/)

If Node.js® is installed, install Gulp via command prompt \(e.g. console or terminal\).

```text
npm install -g gulp-cli
```

* [BL4NK](https://github.com/Bloggerschmidt/Blank/releases/latest) \(download latest version\)

## Customization

You can customize your template with your information doing the following steps.

* Unzip BL4NK
* Edit the `templateDetails.xml`

  Fill out all information

* Replace the following images \(optional\)

  `template_preview.png`

  `template_thumbnail.png`

  `favicon.ico`

* Zip the template folder again

## Installation

Install BL4NK like a normal template in Joomla!™. Open your command prompt and go to the template directory. Install all dependencies.

```text
npm install
```

Run Gulp to compile, compress and build.

```text
gulp
```

See the magic happen on your command line if you edit some files.

## Working files

Let's start the work by coding in the following files.

* index.php \(html\)
* js/script.js \(javascript\)
* css/template.scss or .less \(css\)

The building files are stored in folder `/build` in your template directory.

## Snippets

There exits a [gist with usefull template snippets](https://gist.github.com/Bloggerschmidt/2360208).

{% embed data="{\"url\":\"https://gist.github.com/Bloggerschmidt/2360208\",\"type\":\"rich\",\"title\":\"Template Snippets for Joomla!\",\"description\":\"Template Snippets for Joomla! · GitHub\",\"icon\":{\"type\":\"icon\",\"url\":\"https://gist.github.com/fluidicon.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://avatars1.githubusercontent.com/u/1226135?s=400&v=4\",\"width\":400,\"height\":400,\"aspectRatio\":1},\"embed\":{\"type\":\"reader\",\"html\":\"<script type=\\\"text/javascript\\\" src=\\\"https://gist.github.com/2360208.js\\\"></script>\",\"aspectRatio\":0}}" %}



