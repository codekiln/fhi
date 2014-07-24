[![Stories in Ready](https://badge.waffle.io/hbshci/fhi.png?label=ready&title=Ready)](https://waffle.io/hbshci/fhi)

# Forum on Health Care Innovation Website
This repository contains the source code for the Forum on Health Care Innovation website. To see the work in progress, please see the todos at [Waffle.io](https://waffle.io/hbshci/fhi).

## Building the website
To build the website: 

0. Install [Node.js](http://nodejs.org/), which is available on all plaforms. Node is server software that you run from the command line. 
0. Install [Git](http://git-scm.com/), which is available on all platforms. Git is software for managing versions of software that is in the process of being written. Github uses git to help programmers manage versions of the software they are writing.
0. Open a command prompt or terminal. If on Windows, use [Git BASH](http://msysgit.github.io/). If on Mac, use [terminal](http://www.maclife.com/article/feature/25_terminal_tips_every_mac_user_should_know).
0. Enter `cd ~` and then `git clone git@github.com:codekiln/fhi.git`. 
0. Enter `cd fhi` and then `npm i` to install the dependencies for the project. 
0. Enter `grunt design`. This should open up a web browser that contains the web page. You may now edit the text files, save them, and watch the page reload with the new changes reflected. At this point, you can copy the contents of the _gh_pages directory onto any server.

## Deploying the website
If you have access to a conventional server, you can copy the _gh_pages directory onto any server after generating the files with `grunt design` or `grunt`. The site is currently served on Github. To specifically deploy the website on github, you need to:

0. Type in `cd _gh_pages`. 
0. Make a new revision and push it to the "gh-pages" branch. `git add -A`, `git commit -m "my commit message"`, `git push origin gh-pages`. 

## Technology stack
While a complete list of all the technologies this website relies on is outside the scope of this Readme document, the main dependencies are as follows: 

### Libraries

+ [Node.js](http://nodejs.org/) server software is used to build the site. Node comes with and uses [NPM](https://www.npmjs.org/) to manage packages of software dependencies, and is used to resolve all of the dependencies below when you type `npm i` or `npm install`. 
+ [Grunt](http://gruntjs.com/) task runner for Node.js is used to coordinate the tasks it takes to build the site. To see the tasks, take a look at [Gruntfile.js](Gruntfile.js). 
+ [Assemble](http://assemble.io/) static site generator library for Node.js. Technically, Assemble is a plugin for Grunt that provides a structure for laying out a static site.
+ [Handlebars](http://handlebarsjs.com/), a templating language used to pass data in to a template and render HTML.
+ [Less](http://lesscss.org/), a javascript library that enables preprocessing CSS files to give them extra capabilities, such as the ability to define colors in variables in one place. The Forum on Health Care Innovation website is based on Less CSS's website, which itself is based on Bootstrap's website.
+ [Bootstrap](http://getbootstrap.com/), a CSS and Javascript library that provides a set of mobile-responsive user interface templates to build upon. Bootstrap also includes [Glyphicons](http://getbootstrap.com/components/), a set of icons.  

### Other technologies

+ [Markdown](http://en.wikipedia.org/wiki/Markdown#Example), a markup language that enables readable plain text documents to be converted to HTML. [To try Markdown, click here](http://markdown-here.com/livedemo.html).
+ [Sublime Text](http://www.sublimetext.com/), a text editor with plugins that support Handlebars, Less, JavaScript, and other languages used in this project.
+ [Yet Another Markup Language (YAML)](http://en.wikipedia.org/wiki/YAML#Examples), a data format that is designed to be very readable by humans.

In addition to the core technologies listed above, there are many plugins for Handlebars and Assemble that this project depends on in turn. To examine them, one can look at the [package.json](package.json) file in the root directory of this repository. 

## Directory Structure
The following is an explanation of the directory structure used in this repository.

* [assets](assets/) 	- static files used in the site, such as images, fonts, and library javascript files.
* [content](content/) 	- folders of markdown files. Most of the content of the site should be edited in this folder.
* [data](data/) 		- data files that are used throughout site. For example, challenge.yml contains the due date of the challenge, defined once.
* [node_modules](node_modules/) - this folder is generated by node's package manager by examining this project's [package.json](package.json) file. It contains the dependencies for this project. Do not touch its contents.  
* [source_graphics](source_graphics) - this is just a folder to put photoshop templates and other graphic assets that are necessary for the site but should not be copied to the server where the site is deployed.
* [styles](styles/) - this folder contains the CSS and LESS files that style the site. Start with [index.less](styles/index.less) and follow the `@import` directives out to the other files.
* [templates](templates/) - this folder contains the templates for the site. These follow a pattern that is used in Assemble.
  * [_helpers](templates/_helpers/) - contains javascript helpers for Handlebars. These extend Handlebars and make it so it can render things with more complex logic. Many of these are from Assemble.
  * [_plugins](templates/_plugins/) - these are javascript scripts that plug in and modify the website. 
  * [includes](templates/includes/) - these are Handlebars templates (.hbs) that usually represent a smaller rectangular area on a page. 
  * [layouts](templates/layouts/) - these are Handlebars templates (.hbs) that lay out the high-level structure of a HTML page. Most pages have the default layout.
  * [snippets](templates/snippets/) - these are templates that are used to generate a feed. This is currently not used. 
  * *.hbs - these are the Handlebars templates for each of the top-level navigation elements. For each of these files, first the layout is called, and then the Handlebars page template is called where the body tag is in the layout file. 
* [.assemblerc.yml](.assemblerc.yml) - this is a YAML data file that has many of the configuration variables for the site that is used by Assemble. Whenever you see a variable that looks like "site.version" or "site.url," it is coming from this file.
* .bowerrc, .gitattributes, .gitignore, .jshintrc, .travis.yml, bower.json - you can ignore these if you don't know what they do.
* [Gruntfile.js](Gruntfile.js) - this contains the tasks for the grunt task runner. 
* README.md - this document. 
