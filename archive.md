---
title: Blog Archive
permalink: "/archive/"
layout: page
banner_image: sample-banner-image-3.jpg
---

<div>
  {% for post in site.posts %}
    {% capture currentyear %}{{post.date | date: "%Y"}}{% endcapture %}
    {% if currentyear != year %}
      {% unless forloop.first %}
      {% endunless %}
      <h5>{{ currentyear }}</h5>
      <ul>
      {% capture year %}{{currentyear}}{% endcapture %}
      </ul> 
    {% endif %}
    <ul>
    <li><a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a></li>
    </ul>
{% endfor %}
</div>