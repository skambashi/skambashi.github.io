---
layout: archive
title: "Latest Posts"
date:
modified:
excerpt:
image:
  feature:
  teaser:
  thumb:
ads: false
---

<div class="tiles">
{% for post in site.categories.blog %}
  {% include post-grid.html %}
{% endfor %}
</div><!-- /.tiles -->
<style>
	.project-image {
		width: 100%;
	    height: 200px;
	    overflow: hidden;
	    background-size: cover;
	    background-repeat: no-repeat;
	    background-position: 50% 50%;
	}
</style>
