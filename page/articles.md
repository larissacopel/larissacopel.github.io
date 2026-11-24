---
layout: page
title: Articles
subtitle: Some articles I've written
permalink: /articles/
---

<div class="projects">

{%- if site.articles -%}
    {%- assign sorted_articles = site.articles | sort: "date" | reverse -%}

    {%- for article in sorted_articles -%}
        <div class="project-post">
            <div class="project-post-title">
                <a class="post-link" href="{{ article.url | relative_url }}">
                    {{ article.title | escape }}
                </a>
            </div>

            {%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}

            <span class="post-meta project-post-date">
                {{ article.date | date: date_format }}
            </span>

            {%- if site.show_excerpts -%}
                <p>{{ article.excerpt }}</p>
            {%- endif -%}

            <span class="project-post-learn-more">Learn more...</span>
        </div>
    {%- endfor -%}
{%- endif -%}

</div>