---
layout: page
title: Archive
permalink: /archive
---

<style>
  .wrapper {
    max-width: 46em;
  }

  time {
    display: inline-block;
}
</style>

<!-- <div id="search-searchbar"></div>

<div class="post-list" id="search-hits">
</div>
{% include algolia.html %}

-->
<h1>{{ page.title }}</h1>


<ul class="archive">
  {% for note in site.notes %}
    {% assign modified_date = note.last_modified_at | date: "%Y-%m-%d" | date: "%s" %}
    {% if modified_date >= one_month_ago %}
      <li>
        <a href="{{ note.url }}{%- if site.use_html_extension -%}.html{%- endif -%}" class="internal-link">
          {{ note.title }}</a>
        {% if note.category != null %} in {{ note.category }}{% endif %}
        <time datetime="{{ note.last_modified_at | date_to_xmlschema }}">
          <!-- 🕙更新  --> {{ note.last_modified_at | date: "%Y-%m-%d" }}
        </time>
      </li>
    {% endif %}
  {% endfor %}
</ul>

<ul class="archive">
  {% for note in site.notes | sort: 'last_modified_at' | reverse %} 
  <li>
    <a href="{{ note.url }}{%- if site.use_html_extension -%}.html{%- endif -%}" class="internal-link">
    {{note.title}}</a>{% if note.category != null %} in {{note.category}}{% endif %} 
     <time datetime="{{ page.last_modified_at | date_to_xmlschema }}">{% if page.type != 'pages' %}
      <!-- 🕙更新  --> {{ note.last_modified_at | date: "%Y-%m-%d" }}
      {% endif %}
    </time>
    <!-- <span>{{ note.last_modified_at | date: "%B %-d, %Y" }}</span> -->
    <!-- <p>
        {% if note.summary %}
          {{ note.summary | strip_html | truncate: 50, "..." }}
        {% else %}
          {{ note.excerpt | strip_html | truncate: 50, "..." }}
        {% endif %}
    </P> -->
  </li>
{% endfor %}


<section>
  {%- if site.show_notes_graph -%}<p>Here are all the notes in this garden, along with their links, visualized as a graph.</p>{% include notes-graph.html %}{%- endif -%}</section>