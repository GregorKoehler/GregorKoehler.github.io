---
layout: post
title:  "'Initial Commit' Or How To Blog Using Github"
date:   2018-01-02 06:45:27 +0200
categories: tech
---
Welcome to my blog!  
This blog serves as a medium to share things that I find interesting and think others might be interested in as well. 
I plan to blog about topics ranging from machine learning to my experiences while traveling (and working remotely) and 
maybe even some thoughts&ideas about fun gadgets and the possible symbiosis of real-world objects and machine learning!

As for this first blog post I thought it would be best to give a small and concise tutorial on how to set up this very thing you're 
looking at right now. A blog hosted on GitHub - because chances are if you're reading this you also signed up with GitHub some time ago.

Eventually the plan is to have check marks at the top of the blog helping to filter the content through a selection of three or so topics. 
If you see something like this by the time you read this - great, future Gregor succeeded!

# Now for the tutorial:
First things first - how come anyone with a github account can simply host a blog directly from a GitHub repository?  
Well, this great feature is called [**GitHub** Pages](https://pages.github.com). This video nicely describes the possibilities GitHub Pages offer:  
[![IMAGE ALT TEXT HERE](http://img.youtube.com/vi/2MsN8gpT6jY/0.jpg)](http://www.youtube.com/watch?v=2MsN8gpT6jY)  
In the end of the video [**Jekyll**](https://jekyllrb.com) is mentioned. That's exactly what we're using here for this tutorial.  
Jekyll is a **static site generator** (SSG) built on [Ruby](https://www.ruby-lang.org/en/downloads/) which generates static HTML pages
from a template directory containing raw text files. This together with GitHub's Jekyll integration makes it easy to create and maintain
a blog by simply tweaking some configs and writing posts in Markdown.  
Let's see how we can set up a new website using Jekyll:

1. **Install Jekyll plus dependencies**
* refer to the [Jekyll Installation Docs](https://jekyllrb.com/docs/installation/)
* if you have [RubyGems](https://rubygems.org/pages/download) installed, the following command should suffice:  
  `gem install jekyll bundler`

2. **Create a new repository on Github and clone it to some directory of your choice**
* name it <*your Github username*>.github.io
* navigate to some place where you want to check out the Github repository and clone the repository.
* `git clone <your Github username>.github.io`
* in your local repo, run `jekyll new .`

3. **Take a look at the default layout and get acquainted**
* you can always see what your website looks like via `bundle exec jekyll serve`  
  and navigating to [http://localhost:4000](http://localhost:4000)
* try setting a **title, email and description** in *`_config.yml`* and see what changes when you build the site again,  
  repeat for other settings
* next maybe make some changes in *`about.md`*

4. **Create additional pages to accomodate your content**
* additional pages can be created by simply copying the about markdown file and changing title, permalink and the text body  
  (deleting the title line results in the page not showing up in the menu) 

5. **Customize the default theme or migrate to some other theme**
* to be continued..







[jekyll-docs]: http://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
