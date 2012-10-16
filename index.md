---
layout: page
title: Hello World!
tagline: Supporting tagline
---
{% include JB/setup %}

Read [Jekyll Quick Start](http://jekyllbootstrap.com/usage/jekyll-quick-start.html)

Complete usage and documentation available at: [Jekyll Bootstrap](http://jekyllbootstrap.com)

## Update Author Attributes

In `_config.yml` remember to specify your own data:
    
    title : My Blog =)
    
    author :
      name : Name Lastname
      email : blah@email.test
      github : username
      twitter : username

The theme should reference these variables whenever needed.
    
## Sample Posts

This blog contains sample posts which help stage pages and blog data.
When you don't need the samples anymore just delete the `_posts/core-samples` folder.

    $ rm -rf _posts/core-samples

Here's a sample "posts list".

<ul class="posts">
  {% for post in site.posts %}
    <li><h3><a class="tit" href="{{ BASE_PATH }}{{ post.url }}" title="{{ post.title }}">{{ post.title }}</a></h3> -- <span class="post-sub">{{ post.date | date_to_string }}</span>
        <!--<a class="comment" href="http://44ux.com{{ BASE_PATH }}{{ post.url }}#disqus_thread" data-disqus-identifier="article_1_identifier">link</a>-->
        <p class="abstract">{{ post.content | strip_html | truncatewords:50 }}</p>
        <p class="more"><a href="{{ BASE_PATH }}{{ post.url }}"  target="_blank" title="Read more...">Continue Reading ...</a></p>
    </li>
  {% endfor %}
</ul>

## To-Do

This theme is still unfinished. If you'd like to be added as a contributor, [please fork](http://github.com/plusjade/jekyll-bootstrap)!
We need to clean up the themes, make theme usage guides with theme-specific markup examples.


