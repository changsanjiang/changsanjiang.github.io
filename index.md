---
# You don't need to edit this file, it's empty on purpose.
# Edit theme's home layout instead if you wanna make some changes
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
layout: darkly
title: changsanjiang blog
---
<div class="home">
	<h1 style="text-align: center;">Posts</h1>
	<ul style="padding: 0">
		<li>
			<h2>
				{% for tag in site.tags %}
				<h3>{{ tag[0] }}</h3>
				<ul>
					{% for post in tag[1] %}
						<li>
							<a href="{{ post.url }}">{{ post.title }}</a>
						</li>
					{% endfor %}
				</ul>
				{% endfor %}
  		</h2>
		</li>
	</ul>
</div>
