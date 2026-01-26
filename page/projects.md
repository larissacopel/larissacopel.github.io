---
layout: page
title: Projects
subtitle: Some projects I've created and a few that are still ongoing!
permalink: /projects/
---

<div class="projects">

{%- if site.posts.size > 0 -%}
    {%- for post in site.posts -%}
        <div class="project-post">
            <div class="project-post-title">
                <a class="post-link" href="{{ post.url | relative_url }}">{{ post.title | escape }}</a>
            </div>
            {%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
            <span class="post-meta">{{ post.date | date: date_format }}</span>
            {%- if site.show_excerpts -%}
                {{ post.excerpt }}
            {%- endif -%}
        </div>
    {%- endfor -%}
{%- endif -%}
</div>
