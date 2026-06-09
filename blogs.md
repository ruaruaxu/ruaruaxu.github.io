---
layout: homepage
---

<style>
  .blog-page {
    margin-bottom: 44px;
  }

  .blog-intro {
    max-width: 760px;
    margin-bottom: 26px;
  }

  .blog-intro h2 {
    margin-top: 0;
  }

  .blog-intro p {
    color: #4b5563;
    font-size: 17px;
    line-height: 1.65;
    margin-bottom: 0;
  }

  .blog-filters {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    margin: 0 0 20px;
  }

  .blog-filter {
    background: #fff;
    border: 1px solid var(--site-border);
    border-radius: 6px;
    color: var(--site-blue);
    cursor: pointer;
    font-family: inherit;
    font-size: 14px;
    line-height: 1;
    padding: 8px 12px;
  }

  .blog-filter:hover,
  .blog-filter.active {
    border-color: var(--site-pink);
    color: var(--site-pink);
  }

  .blog-grid {
    display: grid;
    gap: 14px;
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }

  .blog-card {
    border: 1px solid var(--site-border);
    border-radius: 8px;
    display: flex;
    flex-direction: column;
    min-height: 188px;
    padding: 18px;
    transition: border-color 0.18s ease, box-shadow 0.18s ease, transform 0.18s ease;
  }

  .blog-card:hover {
    border-color: rgba(216, 27, 114, 0.42);
    box-shadow: 0 10px 24px rgba(23, 49, 95, 0.08);
    transform: translateY(-2px);
  }

  .blog-card-meta {
    color: var(--site-muted);
    display: flex;
    font-size: 12px;
    gap: 8px;
    letter-spacing: 0;
    margin-bottom: 10px;
  }

  .blog-card h3 {
    color: var(--site-blue);
    font-size: 21px;
    line-height: 1.25;
    margin: 0 0 10px;
  }

  .blog-card p {
    color: #4b5563;
    flex: 1;
    font-size: 15px;
    line-height: 1.55;
    margin-bottom: 18px;
  }

  .blog-card-link {
    align-self: flex-start;
    border-bottom: 1px solid rgba(43, 109, 168, 0.35);
    color: var(--site-link-blue);
    font-size: 14px;
    line-height: 1.2;
  }

  .blog-card-link:hover {
    border-color: var(--site-pink);
    color: var(--site-pink);
  }

  .blog-empty {
    border: 1px solid var(--site-border);
    border-radius: 8px;
    color: var(--site-muted);
    display: none;
    padding: 18px;
  }

  @media print, screen and (max-width: 720px) {
    .blog-grid {
      grid-template-columns: 1fr;
    }

    .blog-intro p {
      font-size: 16px;
    }
  }
</style>

<div class="blog-page">
  <div class="blog-intro">
    <h2>Blogs</h2>
    <p>Notes on cities, design, photography, music, films, and everyday wandering.</p>
  </div>

  <div class="blog-filters" aria-label="Blog categories">
    <button class="blog-filter active" type="button" data-filter="All">All</button>
    {% assign categories = site.data.blogs | map: "category" | uniq | sort %}
    {% for category in categories %}
    <button class="blog-filter" type="button" data-filter="{{ category }}">{{ category }}</button>
    {% endfor %}
  </div>

  <div class="blog-grid" id="blog-grid">
    {% for post in site.data.blogs %}
    <article class="blog-card" data-category="{{ post.category }}">
      <div class="blog-card-meta">
        <span>{{ post.date }}</span>
        <span>{{ post.category }}</span>
        <span>{{ post.source }}</span>
      </div>
      <h3>{{ post.title }}</h3>
      <p>{{ post.summary }}</p>
      <a class="blog-card-link" href="{{ post.url }}" target="_blank" rel="noopener">Open {{ post.source }}</a>
    </article>
    {% endfor %}
  </div>

  <div class="blog-empty" id="blog-empty">No entries in this category yet.</div>
</div>

<script>
  (function() {
    const filters = Array.from(document.querySelectorAll(".blog-filter"));
    const cards = Array.from(document.querySelectorAll(".blog-card"));
    const emptyState = document.querySelector("#blog-empty");

    filters.forEach((filter) => {
      filter.addEventListener("click", () => {
        const category = filter.dataset.filter;
        let visibleCount = 0;

        filters.forEach((item) => item.classList.toggle("active", item === filter));
        cards.forEach((card) => {
          const shouldShow = category === "All" || card.dataset.category === category;
          card.hidden = !shouldShow;
          if (shouldShow) visibleCount += 1;
        });

        if (emptyState) {
          emptyState.style.display = visibleCount ? "none" : "block";
        }
      });
    });
  })();
</script>
