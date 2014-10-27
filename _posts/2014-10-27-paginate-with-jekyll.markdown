---
title: "Paginate with jekyll"
layout: default
category: jekyll
date: 2014-10-27 22:04:20 CET
tags:
- jekyll
---

# Paginate with jekyll

From the [jekyll documentation](http://jekyllrb.com/docs/pagination/)

To enable pagination for your blog, add a line to the `_config.yml` file that specifies how many items should be displayed per page:

    paginate: 10

You may also specify where the destination of the pagination pages:

    paginate_path: "blog/page:num"

And then render the paginated posts.
Modify the `index.html` and add or correct to:

{% highlight html %}
{% raw %}
<ul class="post-list">
  {% for post in paginator.posts %}
    <li>
      <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>

      <h2>
        <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
      </h2>
    </li>
  {% endfor %}
</ul>
{% endraw %}
{% endhighlight %}

And generate the pagination links:

{% highlight html %}
{% raw %}
<!-- Pagination links -->
<div class="pagination">
  {% if paginator.previous_page %}
    {% if paginator.previous_page == 1 %}
    <a href="/" class="previous">Previous</a>
    {% else %}
    <a href="/blog/page{{ paginator.previous_page }}" class="previous">Previous</a>
    {% endif %}
  {% else %}
    <span class="previous">Previous</span>
  {% endif %}
  <span class="page_number ">Page: {{ paginator.page }} of {{ paginator.total_pages }}</span>
  {% if paginator.next_page %}
    <a href="/blog/page{{ paginator.next_page }}" class="next">Next</a>
  {% else %}
    <span class="next ">Next</span>
  {% endif %}
</div>
{% endraw %}
{% endhighlight %}

Jekyll does not generate page 1 folder thats why I added `{% if paginator.previous_page == 1 %}` condition to point the previous link to the root `index.html`.
