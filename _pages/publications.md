---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

{% if site.author.googlescholar %}
  You can also find my articles on [my Google Scholar profile]({{site.author.googlescholar}})
{% endif %}

{% include base_path %}

<!-- New style rendering if publication categories are defined -->
{% if site.publication_category %}
{% for category in site.publication_category  %}
{% assign title_shown = false %}
{% for post in site.publications reversed %}
{% if post.category != category[0] %}
{% continue %}
{% endif %}
{% unless title_shown %}

## {{ category[1].title }}

{% assign title_shown = true %}
{% endunless %}

1. {% for author in post.authors %}{% if forloop.last == false %}{% if author.link %} [{{ author.name }}]({{ author.link }}),{% else %}{{ author.name }}, {% endif %}{% else %}{% if author.link %}&amp; [{{ author.name }}]({{ author.link }}){% else %}&amp; {{ author.name }} {% endif %}{% endif %}{% endfor %}  
 *{{post.title}}.* {% if post.venue_link %} [({{ post.venue_shortname }} {{ post.date | default: "1900-01-01" | date: "%Y" }})]({{post.venue_link}})  {% else %} (({{ post.venue_shortname }} {{ post.date | default: "1900-01-01" | date: "%Y" }})){% endif %}  
Read more [here]({{post.permalink}}).

{% endfor %}
{% endfor %}
{% else %}
{% for post in site.publications reversed %}
{% include archive-single.html %}
{% endfor %}
{% endif %}



