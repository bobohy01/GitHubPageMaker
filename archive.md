---
layout: page
current: archive
title: All Posts
navigation: true
logo:
class: page-template
subclass: 'post page'
---

<div id="post-index" class="well article">
<article>
{%for post in site.posts %}
    {% unless post.next %}
        <h2>{{ post.date | date: '%Y' }}</h2> 
        <ul>
    {% else %}
        {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
        {% capture nyear %}{{ post.next.date | date: '%Y' }}{% endcapture %}
        {% if year != nyear %}
            </ul>
            <h2>{{ post.date | date: '%Y' }}</h2> 
            <ul>
        {% endif %}
    {% endunless %}
    <li><span class="post-date">
        {% assign date_format = site.date_format.archive %}
        {{ post.date | date: '%Y-%m-%d' }} </span><a href=".{{ post.url }}" target="_blank">{{ post.title }}</a></li>
{% endfor %}
</ul>
</article>
</div>