---
# You don't need to edit this file, it's empty on purpose.
# Edit theme's home layout instead if you wanna make some changes
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
layout: default
title: changsanjiang blog
---
<div class="home">

	<h1 class="page-heading">Posts</h1>
	<ul class="post-list">
		<li>
			<span class="post-meta">Mar 3, 2018</span>
			<h2>
				{% for post in site.posts %}
					<li>{{ post.date | date_to_string }} <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></li>
				{% endfor %}
			</h2>
		</li>
	</ul>
	<p class="rss-subscribe">subscribe <a href="/feed.xml">via RSS</a></p>
</div>
