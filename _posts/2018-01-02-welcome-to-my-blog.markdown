---
layout: post
title:  "'Initial Commit' Or How To Blog Using Github"
date:   2018-01-02 06:45:27 +0200
categories: tech
---
Welcome to my blog!  

I created it to serve as a medium to share things that I find interesting and think others might be interested in as well. 
My plan is to blog about topics ranging from machine learning to my experiences while traveling (and working remotely) and 
maybe even some thoughts&ideas about fun gadgets and the possible symbiosis of real-world objects and machine learning!

As for this first blog post I thought it would be best to give a small and concise tutorial on how to set up this very thing you're 
looking at right now. A blog hosted on GitHub - because chances are if you're reading this you also signed up with GitHub some time ago.

Eventually the plan is to have buttons on the blog page helping to filter the content through a selection of topics.
If you saw something like this by the time you visited my blog - great, future Gregor succeeded in writing some basic HTML and CSS!

# Now for the tutorial:
First things first - how come anyone with a github account can simply host a blog directly from a GitHub repository?  
Well, this great feature is called [**GitHub** Pages](https://pages.github.com). This video nicely describes the possibilities GitHub Pages offer:  
[![IMAGE ALT TEXT HERE](http://img.youtube.com/vi/2MsN8gpT6jY/0.jpg)](http://www.youtube.com/watch?v=2MsN8gpT6jY)  
In the end of the video [**Jekyll**](https://jekyllrb.com) is mentioned. That's exactly what we're using here for this tutorial.  
Jekyll is a **static site generator** (SSG) built on [Ruby](https://www.ruby-lang.org/en/downloads/) which generates static HTML pages
from a template directory containing raw text files. This together with GitHub's Jekyll integration makes it easy to create and maintain
a blog by simply tweaking some configs and writing posts in Markdown.  
Let's see how we can set up a new blog using Jekyll:

1. **Install Jekyll plus dependencies**  
For an installation guide please refer to the [Jekyll Installation Docs](https://jekyllrb.com/docs/installation/). 
If you have [RubyGems](https://rubygems.org/pages/download) installed, the following command should suffice:  
  `gem install jekyll bundler`  

2. **Create a new repository on Github and name it accordingly**  
Use your github username to create a new repository, naming it:  
*YOUR_GITHUB_USERNAME*.github.io  
Now navigate to some place where you want to check out the Github repository and clone the repository via 
`git clone YOUR_GITHUB_USERNAME.github.io`.  
Then in your local repo run: `jekyll new .`

3. **Take a look at the default layout and get acquainted**  
Time to get started actually making changes to the website.
You can always see what your website looks like via `bundle exec jekyll serve` 
and navigating to [http://localhost:4000](http://localhost:4000).  
Try setting a **title, email and description** in *`_config.yml`* and see what changes when you reload the page - repeat for other settings.
Next maybe go ahead and make some changes in *`about.md`*.

4. **Create additional pages to accomodate your content**  
Additional pages can be created by simply copying the about markdown file and changing title, permalink and the text body 
(deleting the title line results in the page not showing up in the menu).

5. **Customize the default theme or migrate to some other theme**  
Theme defaults can be overwritten by creating copies of theme files in your directory and modifying them.
Locating a theme's files can be achieved by:   
`bundle show THEME_NAME` (Jekyll's default theme is called *minima*).  
For example the buttons you might have seen on the blog homepage were created by copying *`_layouts/home.html`* and *`_sass/minima.scss`*
and modifying them to include some buttons which help filtering the blog posts.  
Jekyll first looks for the following folders in your base directory before using the theme's defaults:  
*`/assets`*  
*`/_layouts`*  
*`/_includes`*  
*`/_sass`*  
  

6. **Write your first blogpost in Markdown**  
Now for the fun part: With Jekyll blogposts can simply be written in Markdown.
Jekyll blogposts are sitting in *`/_posts`* and follow the naming convention:  
	*`YEAR-MONTH-DAY-title.md`*  
This [Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) may come in handy when writing a post.  

7. **Push your changes and let Github Pages handle the rest**  
Once you're happy with your page and blogposts, simply commit the changes and push them. The changes should be live within seconds.  


That's all there is to it! Enjoy running your personal blog using little more than the usual *git* workflow.






[jekyll-docs]: http://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
