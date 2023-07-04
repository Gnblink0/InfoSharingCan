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


{% assign sorted_notes = site.notes | sort: 'lastmod' | reverse %}
<ul class="archive">
  {% for note in sorted_notes %}
    <li>
      <a href="{{ note.url }}{%- if site.use_html_extension -%}.html{%- endif -%}" class="internal-link">
        {{ note.title }}</a>
      {% if note.category != null %} in {{ note.category }}{% endif %}
      <time datetime="{{ note.lastmod | date_to_xmlschema }}">
        {{ note.lastmod | date: "%Y-%m-%d" }}
      </time>
    </li>
  {% endfor %}
</ul>

<section>
  {%- if site.show_notes_graph -%}<p>Here are all the notes in this garden, along with their links, visualized as a graph.</p>{% include notes-graph.html %}{%- endif -%}</section>