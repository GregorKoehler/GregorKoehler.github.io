---
layout: default
permalink: /crypto/
---

<div class="home">


<div class="btn-group">
<a href="/"> <button class="button">All</button> </a>
<a href="/ml"> <button class="button">ML</button> </a>
<a href="/crypto"> <button class="button" style="background:linear-gradient(to right, gray, white)">Crypto</button> </a>
<a href="/tech"> <button class="button">Other Tech</button> </a>
<a href="/nomadism"> <button class="button">Digital Nomadism</button> </a>
</div>


<ul class="post-list" style="clear:both">
	{% for post in site.categories.crypto %}
		<li>
			{% assign date_format = site.minima.date_format | default: "%b %-d, %Y" %}
			<span class="post-meta">{{ post.date | date: date_format }}</span>

			<h2>
				<a class="post-link" href="{{ post.url | relative_url }}">{{ post.title | escape }}</a>
			</h2>
		</li>
	{% endfor %}
</ul>

</div>
