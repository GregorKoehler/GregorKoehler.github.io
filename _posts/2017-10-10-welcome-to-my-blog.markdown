---
layout: post
title:  "'Initial Commit' Or How To Blog Using Github"
date:   2017-10-10 13:45:27 +0200
categories: jekyll update
---
Welcome to my blog! This blog serves as a medium to share things that I find interesting and think others might be interested in as well. I plan to blog about many things ranging from topics in machine learning to my experiences while traveling (and working remotely) and maybe even some thoughts/ideas about fun gadgets and the possible symbiosis of real-world objects and machine learning! Because like my brother, I've always had a thing for new gadgets.

As for this first blog post I thought it would be best to give a small and concise tutorial on how to set up this very thing you're looking at right now. A blog hosted on github - because chances are if you're reading this that you also got a github account.

Eventually the plan is to have check marks at the top of the blog helping to filter the content through a selection of three or so topics. If you see something like this by the time you read this - great, future Gregor succeeded!

# Now for the tutorial:
1. Create a new repository on Github and clone it to some directory of your choice.
* Name it <*your Github username*>.github.io
* Navigate to some place where you want to check out the Github repository and clone the repository.
* `git clone <your Github username>.github.io`
* Install Jekyll (refer to the [Jekyll Docs][jekyll-docs]) plus dependencies.

Jekyll also offers powerful support for code snippets:




## Addendum - Markdown Basics
Just to help you write nice-looking markdown posts here is sort of a cheat-sheet for markdown:
### Basics
# H1
## H2
### H3
#### H4
##### H5
###### H6
{% highlight markdown %}
# H1
## H2
### H3
#### H4
##### H5
###### H6
{% endhighlight %}


They should be displayed ranging from big to small (for me the **H1** header is displayed smaller than the **H2** weirdly - but it should work as expected if you keep the basic top-down structure).

*Italic*, **bold** and ~~scratch this~~.
{% highlight markdown %}
*Italic*, **bold** and ~~scratch this~~.
{% endhighlight %}


`Inline Code`
{% highlight markdown %}
`Inline Code`
{% endhighlight %}


### Links

[Inline-style links](https://www.google.com)
{% highlight markdown %}
[Inline-style links](https://www.google.com)
{% endhighlight %}


### Quotes
> What I cannot create I do not understand. - Richard P. Feynman
{% highlight markdown %}
> What I cannot create I do not understand. - Richard P. Feynman
{% endhighlight %}


### Lists

1. First ordered list item
2. Another item
	* Unordered sub-list. 
1. Actual numbers don't matter, just that it's a number
	1. Ordered sub-list
4. And another item.

{% highlight markdown %}
1. First ordered list item
2. Another item
  * Unordered sub-list. 
1. Actual numbers don't matter, just that it's a number
  1. Ordered sub-list
4. And another item.
{% endhighlight %}


### Tables

| Markdown      | supports      | tables|
| ------------- |:-------------:| -----:|
| col 1 is      | standard    (btw: lines can be out of place)   | $1600 |
| col 2 is      | centered      |   $12 |
| col 3 is      | right-aligned | $1    |
{% highlight markdown %}
| Markdown      | supports      | tables|
| ------------- |:-------------:| -----:|
| col 1 is      | standard    (btw: separators can be out of place)   | $1600 |
| col 2 is      | centered      |   $12 |
| col 3 is      | right-aligned | $1    |
{% endhighlight %}




[jekyll-docs]: http://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
