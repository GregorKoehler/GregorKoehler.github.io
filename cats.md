---
layout: page
permalink: /categories/
---

Find blog posts roughly sorted by categories. Not all categories are populated, yet.  
Expect blog posts in those areas soon!

<h3> Machine Learning </h3>
<ul>
{% for post in site.categories.ml %}
 <li><span>{{ post.date | date_to_string }}</span> &nbsp; <a href="{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}  
 <li> no posts yet, stay tuned! </li>
</ul>

<h3> Cryptocurrency </h3>
<ul>
{% for post in site.categories.crypto %}
<li><span>{{ post.date | date_to_string }}</span> &nbsp; <a href="{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}  
<li> no posts yet, stay tuned! </li>
</ul>

<h3> Other Tech </h3>
<ul>
{% for post in site.categories.tech %}
<li><span>{{ post.date | date_to_string }}</span> &nbsp; <a href="{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}  
</ul>

<h3> Physics </h3>
<ul>
{% for post in site.categories.physics %}
<li><span>{{ post.date | date_to_string }}</span> &nbsp; <a href="{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}  
<li> no posts yet, stay tuned! </li>
</ul>

<h3> Misc </h3>
<ul>
{% for post in site.categories.misc %}
<li><span>{{ post.date | date_to_string }}</span> &nbsp; <a href="{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}  
</ul>
