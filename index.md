---
# You don't need to edit this file, it's empty on purpose.
# Edit theme's home layout instead if you wanna make some changes
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
layout: darkly
title: changsanjiang blog
---
<div class="home">
	<h1>Posts</h1>
	<ul>
		<li>
			<h2>
				{% for post in site.posts %}
				<li>{{ post.date | date_to_string }} <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></li>
				{% endfor %}
  		</h2>
		</li>
	</ul>
</div>
