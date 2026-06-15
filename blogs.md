---
layout: homepage
permalink: /blog/
---

<style>
  .blog-page {
    margin-bottom: 44px;
  }

  .blog-header {
    margin-bottom: 24px;
    max-width: 760px;
  }

  .blog-header h2 {
    margin: 0 0 8px;
  }

  .blog-header p {
    color: var(--site-muted, #6b7280);
    font-size: 16px;
    line-height: 1.6;
    margin: 0;
  }

  .blog-cover {
    margin: 0 0 24px;
  }

  .blog-cover img {
    aspect-ratio: 3 / 1;
    border-radius: 8px;
    display: block;
    object-fit: cover;
    object-position: center;
    width: 100%;
  }

  .blog-cover figcaption {
    color: var(--site-muted, #6b7280);
    font-size: 12px;
    margin-top: 6px;
  }

  .blog-directory {
    margin-top: 28px;
  }

  .blog-category {
    margin-top: 34px;
  }

  .blog-category:first-child {
    margin-top: 0;
  }

  .blog-category-title {
    border-bottom: 1px solid var(--site-border, #d9dde5);
    font-size: 22px;
    line-height: 1.25;
    margin: 0;
    padding-bottom: 8px;
  }

  .blog-entry {
    border-bottom: 1px solid var(--site-border, #d9dde5);
    display: grid;
    gap: 18px;
    grid-template-columns: 96px minmax(0, 1fr);
    padding: 18px 0;
  }

  .blog-entry-date {
    color: var(--site-muted, #6b7280);
    font-size: 14px;
    line-height: 1.35;
    padding-top: 2px;
  }

  .blog-entry-title {
    font-size: 19px;
    line-height: 1.3;
    margin: 0 0 5px;
  }

  .blog-entry-title a {
    color: var(--site-blue, #17315f);
  }

  .blog-entry-title a:hover {
    color: var(--site-pink, #d81b72);
  }

  .blog-entry-summary {
    color: #374151;
    font-size: 15px;
    line-height: 1.55;
    margin: 0;
  }

  .blog-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 5px;
    margin-top: 9px;
  }

  .blog-tag {
    border: 1px solid var(--site-border, #d9dde5);
    border-radius: 5px;
    color: var(--site-link-blue, #2b6da8);
    font-size: 11px;
    line-height: 1;
    padding: 3px 8px;
  }

  .blog-footer-note {
    border-top: 1px solid var(--site-border, #d9dde5);
    color: var(--site-muted, #6b7280);
    font-size: 13px;
    line-height: 1.55;
    margin-top: 24px;
    padding-top: 14px;
  }

  @media print, screen and (max-width: 720px) {
    .blog-entry {
      gap: 6px;
      grid-template-columns: 1fr;
      padding: 16px 0;
    }
  }
</style>

<div class="blog-page">
  <div class="blog-header">
    <h2 class="no-outline">Blog</h2>
    <p>Welcome to my blog “徐徐图之”, where I share my travels, photography, thoughts about music and movies, and of course also research projects.</p>
  </div>

  <figure class="blog-cover">
    <img src="{{ '/assets/img/blog/yosemite.jpg' | relative_url }}" alt="Yosemite landscape photographed by Wenrui">
    <figcaption>cover image: Yosemite 📷 Wenrui</figcaption>
  </figure>

  <div class="blog-directory">
    {% assign posts = site.data.blogs | sort: "date_sort" | reverse %}
    {% assign category_order = "Course Notes|Beautiful Things" | split: "|" %}
    {% for category in category_order %}
      {% assign category_posts = posts | where: "category", category %}
      {% if category_posts.size > 0 %}
        {% assign category_title = category %}
        {% assign category_posts = category_posts | sort: "order" %}
        <div class="blog-category">
          <h2 id="{{ category_title | slugify }}" class="blog-category-title">{{ category_title }}</h2>
          {% for post in category_posts %}
          <article class="blog-entry">
            <div class="blog-entry-date">{{ post.date }}</div>
            <div class="blog-entry-body">
              <h3 class="blog-entry-title">
                <a href="{{ post.url }}" target="_blank" rel="noopener">{{ post.title }}</a>
              </h3>
              <p class="blog-entry-summary">{{ post.summary }}</p>
            </div>
          </article>
          {% endfor %}
        </div>
        {% endif %}
    {% endfor %}
  </div>

  <div class="blog-footer-note">
    徐徐图之 © Wenrui's Blog. 徐: xú, Chinese surname; adv. slowly, gently, calmly; adj. composed, dignified. 图: tú, v. plan, strive for, picture and understand, draw; n. plan, picture, chart. 之: zhī, pron. it, the goal, the question, the world.
  </div>
</div>
