---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---
<sup>*</sup> Equal authorship

{% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

<h2>1. Preprint</h2>
{% for post in site.publications reversed %}
  {% if post.pubtype == 'preprint' %}
      {% include archive-single.html %}
  {% endif %}
{% endfor %}

<h2>2. Journal Articles</h2>
{% for post in site.publications reversed %}
  {% if post.pubtype == 'journal' %}
      {% include archive-single.html %}
  {% endif %}
{% endfor %}


<h2>3. PhD Thesis</h2>
{% for post in site.publications reversed %}
  {% if post.pubtype == 'thesis' %}
      {% include archive-single.html %}
  {% endif %}
{% endfor %}
