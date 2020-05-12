---
title: "Create a website using Jekyll"
header:
  image: images/main_doc1_1024.jpg
  teaser: images/main_doc1_1024.jpg
  caption: "Photo credit: [**pixabay**](https://pixabay.com)"
tag:
  - Website
categories:
  - Web & Mobile
---

{% include toc %}

This page describes how to make personal github site step by step using Jekyll on Windows 7.

# Installation (Contents)

1. Install Ruby. (For more Information, Click [Here](http://jekyll-windows.juthilo.com/1-ruby-and-devkit/)).

2. You will also need Jekyll, a part of Ruby Gem. <br>

        gem install jekyll


3. If you have a Gemfile, and add a following line if you do not see the line

	    gem 'wdm', '~> 0.1.0' if Gem.win_platform?

4. bundler is also a gem package which helps version dependency problems.

	    gem install bundler
	    bundle install

5. You will also need to install a package called "nokogiri" <br>
   (*Currently, this has an issue*. (i.e. *'nokogiri requires Ruby version < 2.3, >= 1.9.2.'*))<br>
   If you have the issue, run following will solve the problem:

		gem install nokogiri -v '1.6.6.4'
		gem install rails
		gem install nokogiri -v '1.6.8.rc3'

		In **gemfile**, include
		gem 'nokogiri', '>=1.6.8.rc3'

		gem update  
		bundle install or bundle update

6. run following on command prompt to run the site locally.

    	bundle exec jekyll serve --config _config.yml,_config.dev.yml


7. To test *step 6*, type following on your browser (including baseurl):

		http://127.0.0.1:4000/

# Installation (Layout)

To change layouts, fonts, colors, assets directory needs modifications and nodejs (npm) is necessary.

	nodejs

	npm install --save-dev node-sass -g

	npm install -g



# Structure (Abstract)

	Homepage
	├── _data                      # data files for customizing the theme
	|  ├── authors.yml             # name all the authors
	|  ├── navigations.yml         # main navigation links
	|  └── ui-text.yml             # text used throughout the theme's UI
	├── _includes
	|  └── ...
	├── _layouts
	|  └── ...
	├── assets
	|  ├── _scss                   # stylesheet source files
	|  |  ├── vendor               # vendor SCSS partials
	|  |  ├── main.scss            # imports all SCSS partials
	|  |  └── ...                  # theme SCSS partials
	|  ├── css
	|  |  └── main.css             # optimized stylesheet loaded in <head>
	|  ├── fonts
	|  |  └── fontawesome-webfont  # Font Awesome webfonts
	|  ├── js                      # Java Script Plugins
	|  └── ...before </body>
	├── images                     # image assets for posts/pages/collections/etc.
	├── _config.yml                # site configuration
	├── Gemfile                    # gem file dependencies
	├── Gemfile.lock               # gem file dependencies
	├── index.html                 # paginated home page showing recent posts
	└── package.json               # NPM build scripts

Too se more detailed structure, click [Here](https://mmistakes.github.io/minimal-mistakes/docs/structure/).


# Github Configuration

To open an own website using github, your target repository should be named under the certain rule.

	(USERNAME.github.io)  

To make a change of repository name on github,

	go Settings -> Option tab -> rename repository name

Test after the modification.


# Domain mapping

To link USERNAME.github.io with a domain, there are number of things to do.
Prior to map domain, USERNAME.github.io should be working.

1. There are both paid and free domains. Whichever it is chosen, it is fine.
Every domain would be configurable so that goto settings of your domain.


2. Add github DNS provider IP to your domain and save it.
   Here is the DNS IP of github:

		192.30.252.153
		192.30.252.154

3. In github repository, upload a new file named "CNAME"on base directory.
   CNAME should contain the domain name. For example, if the domain name is "domain.com", on your CNAME, following must be written down.

		domain.com

4. After above steps are done, type domain name (i.e. URL) on internet explorer.  
