---
layout: default
---

<header>
  <h1>
    <a href="{{ site.url  }}">
      {{ site.page_title }}
    </a>
  </h1>
  <p class="subtitle">
    {{ site.page_subtitle }}
  </p>
</header>
<main>
  {% for post in site.posts %}
    <article>
      <header>
        <h2>
          <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a>
        </h2>
        <p class="metadata">
          Posted on
          <time datetime="{{ post.date | date_to_xmlschema }}">
            {{ post.date | date: "%b %e, %Y" }}
          </time>
        </p>
      </header>
      <div>
        {% comment %}
          use post.excerpt as soon as all posts will have a proper introduction paragraph
        {% endcomment %}
        {{ post.content | strip_html | truncatewords: 100 }}
      </div>
    </article>
  {% endfor %}
</main>
