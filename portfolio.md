---
layout: homepage
permalink: /portfolio/
---

<script>
  document.body.classList.add('portfolio-body');
</script>

<style>
  .portfolio-body > .wrapper > section {
    max-width: 980px;
    padding-top: 4px;
    width: calc(100% - 300px);
  }

  .portfolio-page {
    display: flow-root;
    font-family: Georgia, "Times New Roman", "Noto Serif SC", serif;
    margin-bottom: 44px;
  }

  .portfolio-year {
    float: none;
    margin-top: 8px;
    max-width: none;
    width: 100%;
  }

  .portfolio-year:first-of-type {
    margin-top: 0;
  }

  .portfolio-year + .portfolio-year {
    padding-top: 12px;
  }

  .portfolio-year-heading {
    align-items: baseline;
    border-bottom: 1px solid var(--site-border, #d9dde5);
    display: flex;
    gap: 14px;
    margin: 0 0 8px;
    padding-bottom: 6px;
  }

  .portfolio-year-heading span {
    color: var(--site-muted, #6b7280);
    font-size: 14px;
    font-weight: 400;
  }

  .portfolio-grid {
    align-items: start;
    display: grid;
    gap: 12px;
    grid-template-columns: repeat(3, minmax(0, 1fr));
  }

  .portfolio-grid.is-masonry {
    display: block;
    position: relative;
  }

  .portfolio-grid.is-masonry .portfolio-card {
    position: absolute;
  }

  .portfolio-card {
    aspect-ratio: var(--portfolio-aspect, 4 / 3);
    background: transparent;
    border: 0;
    cursor: zoom-in;
    display: block;
    font-family: inherit;
    margin: 0;
    overflow: hidden;
    padding: 0;
    position: relative;
    text-align: left;
    width: 100%;
  }

  .portfolio-card.is-wide {
    aspect-ratio: 16 / 10;
  }

  .portfolio-card.is-tall {
    aspect-ratio: 3 / 4;
  }

  .portfolio-card.is-square {
    aspect-ratio: 1 / 1;
  }

  .portfolio-card.is-split-cover {
    aspect-ratio: var(--portfolio-cover-aspect, 13 / 6);
    border-radius: 2px;
    grid-column: span 2;
  }

  .portfolio-card.is-double-wide {
    grid-column: span 2;
  }

  .portfolio-card.is-placeholder {
    cursor: default;
  }

  .portfolio-card img {
    border-radius: 2px;
    display: block;
    height: 100%;
    object-fit: contain;
    width: 100%;
  }

  .portfolio-card-split {
    display: grid;
    gap: 2px;
    grid-template-columns: var(--portfolio-cover-columns, 4fr 9fr);
    height: 100%;
    width: 100%;
  }

  .portfolio-card-split img {
    border-radius: 0;
    min-width: 0;
  }

  .portfolio-placeholder {
    align-items: center;
    aspect-ratio: var(--portfolio-aspect, 4 / 3);
    background:
      linear-gradient(135deg, rgba(216, 27, 114, 0.10), rgba(43, 109, 168, 0.06)),
      #eef1f2;
    border-radius: 2px;
    display: flex;
    height: 100%;
    justify-content: center;
    min-height: 100%;
    width: 100%;
  }

  .portfolio-card::after {
    background: linear-gradient(to top, rgba(12, 22, 28, 0.66), rgba(12, 22, 28, 0));
    border-radius: 2px;
    bottom: 0;
    content: "";
    left: 0;
    opacity: 0;
    pointer-events: none;
    position: absolute;
    right: 0;
    top: 40%;
    transition: opacity 0.18s ease;
  }

  .portfolio-card:hover::after,
  .portfolio-card:focus-visible::after {
    opacity: 1;
  }

  .portfolio-card-meta {
    bottom: 16px;
    color: #fff;
    left: 18px;
    opacity: 0;
    position: absolute;
    right: 18px;
    text-shadow: 0 1px 8px rgba(0, 0, 0, 0.28);
    transition: opacity 0.18s ease;
    z-index: 1;
  }

  .portfolio-card:hover .portfolio-card-meta,
  .portfolio-card:focus-visible .portfolio-card-meta {
    opacity: 1;
  }

  .portfolio-card-title {
    display: block;
    font-size: 19px;
    font-weight: 600;
    line-height: 1.2;
  }

  .portfolio-card-subtitle {
    display: block;
    font-size: 14px;
    margin-top: 4px;
  }

  .portfolio-count {
    align-items: center;
    background: rgba(24, 34, 38, 0.72);
    border: 1px solid rgba(255, 255, 255, 0.44);
    border-radius: 999px;
    color: #fff;
    display: flex;
    font-size: 14px;
    font-family: inherit;
    height: 32px;
    justify-content: center;
    position: absolute;
    right: 12px;
    top: 12px;
    width: 32px;
    z-index: 2;
  }

  .portfolio-lightbox {
    --portfolio-lightbox-control-offset: 22px;
    --portfolio-lightbox-horizontal-space: 144px;
    align-items: center;
    background: rgba(13, 22, 20, 0.94);
    display: none;
    inset: 0;
    justify-content: center;
    padding: 36px 72px;
    position: fixed;
    font-family: Georgia, "Times New Roman", "Noto Serif SC", serif;
    z-index: 13000;
  }

  .portfolio-lightbox.is-open {
    display: flex;
  }

  .portfolio-lightbox-figure {
    margin: 0;
    max-height: 100%;
    position: relative;
    width: min(
      calc(100vw - var(--portfolio-lightbox-horizontal-space)),
      calc((100vh - 120px) * var(--portfolio-lightbox-aspect-ratio, 1.3333))
    );
  }

  .portfolio-lightbox-counter {
    background: rgba(13, 22, 20, 0.72);
    border: 1px solid rgba(255, 255, 255, 0.28);
    border-radius: 999px;
    color: #fff;
    font-size: 13px;
    left: 50%;
    line-height: 1;
    padding: 6px 10px;
    position: absolute;
    top: -31px;
    transform: translateX(-50%);
    white-space: nowrap;
    z-index: 2;
  }

  .portfolio-lightbox-media {
    align-items: center;
    display: flex;
    justify-content: center;
    max-height: calc(100vh - 120px);
    width: 100%;
  }

  .portfolio-lightbox img {
    display: block;
    max-height: calc(100vh - 120px);
    max-width: 100%;
    object-fit: contain;
  }

  .portfolio-lightbox-embed {
    aspect-ratio: var(--portfolio-lightbox-aspect, 4 / 3);
    border: 0;
    display: none;
    max-height: calc(100vh - 120px);
    width: 100%;
  }

  .portfolio-lightbox-embed.is-visible {
    display: block;
  }

  .portfolio-lightbox figcaption {
    align-items: flex-start;
    color: #fff;
    display: flex;
    gap: 18px;
    justify-content: space-between;
    line-height: 1.4;
    margin-top: 14px;
  }

  .portfolio-lightbox-copy {
    min-width: 0;
  }

  .portfolio-lightbox-title {
    font-weight: 600;
  }

  .portfolio-lightbox-subtitle {
    color: rgba(255, 255, 255, 0.72);
    font-size: 14px;
    margin-left: 8px;
  }

  .portfolio-lightbox-description {
    color: rgba(255, 255, 255, 0.82);
    display: none;
    font-size: 14px;
    margin-top: 6px;
    max-width: 680px;
  }

  .portfolio-lightbox-description.is-visible {
    display: block;
  }

  .portfolio-lightbox-actions {
    align-items: center;
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    justify-content: flex-end;
  }

  .portfolio-lightbox-link,
  .portfolio-lightbox-source {
    border: 1px solid rgba(255, 255, 255, 0.34);
    border-radius: 999px;
    color: #fff;
    display: none;
    font-size: 13px;
    padding: 5px 12px;
    white-space: nowrap;
  }

  .portfolio-lightbox-link.is-visible,
  .portfolio-lightbox-source.is-visible {
    display: inline-flex;
  }

  .portfolio-lightbox-button {
    align-items: center;
    background: rgba(255, 255, 255, 0.08);
    border: 1px solid rgba(255, 255, 255, 0.2);
    border-radius: 999px;
    color: #fff;
    cursor: pointer;
    display: flex;
    font-family: inherit;
    font-size: 28px;
    height: 44px;
    justify-content: center;
    position: fixed;
    width: 44px;
  }

  .portfolio-lightbox-button:hover {
    background: rgba(255, 255, 255, 0.16);
  }

  .portfolio-lightbox-button:disabled {
    cursor: default;
    opacity: 0.28;
    pointer-events: none;
  }

  .portfolio-lightbox-close {
    right: var(--portfolio-lightbox-control-offset);
    top: 22px;
  }

  .portfolio-lightbox-prev {
    left: var(--portfolio-lightbox-control-offset);
    position: fixed;
    top: 50%;
    transform: translateY(-50%);
  }

  .portfolio-lightbox-next {
    position: fixed;
    right: var(--portfolio-lightbox-control-offset);
    top: 50%;
    transform: translateY(-50%);
  }

  section > p:last-of-type {
    clear: both;
    display: block;
    width: 100%;
  }

  @media print, screen and (max-width: 960px) {
    .portfolio-body .wrapper,
    .portfolio-body section {
      width: auto;
    }

    .portfolio-body > .wrapper > section {
      padding-left: 0;
      padding-right: 0;
      width: 100%;
    }

    .portfolio-grid {
      grid-template-columns: repeat(2, minmax(0, 1fr));
    }

    .portfolio-lightbox {
      --portfolio-lightbox-control-offset: 10px;
      --portfolio-lightbox-horizontal-space: 36px;
      padding: 34px 18px;
    }
  }

  @media print, screen and (max-width: 560px) {
    .portfolio-grid {
      grid-template-columns: 1fr;
    }

    .portfolio-grid.is-masonry {
      display: grid;
      height: auto !important;
    }

    .portfolio-grid.is-masonry .portfolio-card {
      left: auto !important;
      position: relative;
      top: auto !important;
      width: 100% !important;
    }

    .portfolio-card.is-split-cover {
      grid-column: 1 / -1;
    }

    .portfolio-card.is-double-wide {
      grid-column: span 1;
    }

    .portfolio-lightbox figcaption {
      align-items: flex-start;
      flex-direction: column;
    }
  }
</style>

<div class="portfolio-page">
  {% assign items = site.data.portfolio | where_exp: "item", "item.image" %}
  {% assign items = items | where_exp: "item", "item.hidden != true" | sort: "year" | reverse %}
  {% assign years = items | map: "year" | uniq %}
  {% assign portfolio_index = 0 %}
  {% for year in years %}
    {% assign year_items = items | where: "year", year %}
    <section class="portfolio-year">
      <h2 id="portfolio-{{ year }}" class="portfolio-year-heading" data-outline-title="{{ year }}">{{ year }}</h2>
      <div class="portfolio-grid" data-year="{{ year }}">
        {% for item in year_items %}
          {% assign aspect = item.aspect | default: "4 / 3" %}
          {% assign card_aspect = item.cover_aspect | default: aspect %}
          {% assign image_url = item.image %}
          {% assign large_image_url = item.image_large | default: item.image %}
          {% if item.image and item.image contains "://" %}
            {% assign image_url = item.image %}
          {% elsif item.image %}
            {% assign image_url = item.image | relative_url %}
          {% endif %}
          {% if large_image_url and large_image_url contains "://" %}
            {% assign large_image_url = large_image_url %}
          {% elsif large_image_url %}
            {% assign large_image_url = large_image_url | relative_url %}
          {% endif %}
          {% assign shape_class = "" %}
          {% if card_aspect == "3 / 4" or card_aspect == "4 / 5" %}
            {% assign shape_class = " is-tall" %}
          {% elsif card_aspect == "1 / 1" %}
            {% assign shape_class = " is-square" %}
          {% elsif card_aspect == "16 / 10" or card_aspect == "16 / 9" %}
            {% assign shape_class = " is-wide" %}
          {% endif %}
          {% assign raw_card_title = item.card_title | default: item.title %}
          {% assign raw_card_title = raw_card_title | replace: "2026 ", "" | replace: "2025 ", "" | replace: "2024 ", "" | replace: "2023 ", "" | replace: "2022 ", "" | replace: "2021 ", "" %}
          {% assign card_title = raw_card_title | split: "," | first | strip %}
          {% assign card_subtitle = item.country | default: item.subtitle | default: item.place %}
          {% assign item_subtitle = item.subtitle | default: item.place %}
          {% assign use_split_cover = false %}
          {% if item.cover_layout == "split" and item.photos.size == 2 %}
            {% assign use_split_cover = true %}
          {% endif %}
          {% capture gallery_images %}{% if item.photos %}{% for photo in item.photos %}{% if photo.image contains "://" %}{{ photo.image }}{% elsif photo.image %}{{ photo.image | relative_url }}{% endif %}{% unless forloop.last %}||{% endunless %}{% endfor %}{% else %}{{ image_url }}{% endif %}{% endcapture %}
          {% capture gallery_large_images %}{% if item.photos %}{% for photo in item.photos %}{% assign photo_large = photo.image_large | default: photo.image %}{% if photo_large contains "://" %}{{ photo_large }}{% elsif photo_large %}{{ photo_large | relative_url }}{% endif %}{% unless forloop.last %}||{% endunless %}{% endfor %}{% else %}{{ large_image_url }}{% endif %}{% endcapture %}
          {% capture gallery_embeds %}{% if item.photos %}{% for photo in item.photos %}{{ photo.embed_url }}{% unless forloop.last %}||{% endunless %}{% endfor %}{% else %}{{ item.embed_url }}{% endif %}{% endcapture %}
          {% capture gallery_sources %}{% if item.photos %}{% for photo in item.photos %}{{ photo.source_url | default: item.source_url }}{% unless forloop.last %}||{% endunless %}{% endfor %}{% else %}{{ item.source_url }}{% endif %}{% endcapture %}
          {% capture gallery_photo_titles %}{% if item.photos %}{% for photo in item.photos %}{{ photo.title | default: item.title }}{% unless forloop.last %}||{% endunless %}{% endfor %}{% else %}{{ item.photo_title | default: item.title }}{% endif %}{% endcapture %}
          {% capture gallery_descriptions %}{% if item.photos %}{% for photo in item.photos %}{{ photo.description }}{% unless forloop.last %}||{% endunless %}{% endfor %}{% else %}{{ item.description }}{% endif %}{% endcapture %}
          {% capture gallery_aspects %}{% if item.photos %}{% for photo in item.photos %}{{ photo.aspect | default: aspect | replace: ' ', '' }}{% unless forloop.last %}||{% endunless %}{% endfor %}{% else %}{{ aspect | replace: ' ', '' }}{% endif %}{% endcapture %}
          {% assign display_count = item.count %}
          {% if item.photos %}
            {% assign display_count = item.photos.size %}
          {% endif %}
          <button class="portfolio-card{% if item.image %}{{ shape_class }}{% else %} is-placeholder{{ shape_class }}{% endif %}{% if use_split_cover %} is-split-cover{% endif %}{% if item.layout_span == 2 %} is-double-wide{% endif %}"
            type="button"
            data-index="{{ portfolio_index }}"
            data-image="{{ image_url }}"
            data-large-image="{{ large_image_url }}"
            data-gallery-images="{{ gallery_images | strip | escape }}"
            data-gallery-large-images="{{ gallery_large_images | strip | escape }}"
            data-gallery-embeds="{{ gallery_embeds | strip | escape }}"
            data-gallery-sources="{{ gallery_sources | strip | escape }}"
            data-gallery-photo-titles="{{ gallery_photo_titles | strip | escape }}"
            data-gallery-descriptions="{{ gallery_descriptions | strip | escape }}"
            data-gallery-aspects="{{ gallery_aspects | strip | escape }}"
            data-placeholder="{% if item.image %}false{% else %}true{% endif %}"
            data-title="{{ item.title | escape }}"
            data-card-title="{{ card_title | escape }}"
            data-place="{{ item.place | escape }}"
            data-subtitle="{{ card_subtitle | escape }}"
            data-year="{{ item.year }}"
            data-layout-column="{{ item.layout_column }}"
            data-kind="{{ item.kind | escape }}"
            data-description="{{ item.description | escape }}"
            data-blog-url="{{ item.blog_url }}"
            data-embed-url="{{ item.embed_url }}"
            data-source-url="{{ item.source_url }}"
            data-source-label="{{ item.source_label | default: 'View on 500px' | escape }}"
            data-aspect-ratio="{{ aspect | replace: ' ', '' }}"
            style="--portfolio-aspect: {{ card_aspect }};{% if use_split_cover %} --portfolio-cover-aspect: {{ item.cover_aspect | default: '13 / 6' }}; --portfolio-cover-columns: {{ item.cover_columns | default: '4fr 9fr' }};{% endif %}">
            {% if use_split_cover %}
              <span class="portfolio-card-split" aria-hidden="true">
                {% for photo in item.photos %}
                  {% assign cover_photo_url = photo.image %}
                  {% unless cover_photo_url contains "://" %}
                    {% assign cover_photo_url = cover_photo_url | relative_url %}
                  {% endunless %}
                  <img src="{{ cover_photo_url }}" alt="">
                {% endfor %}
              </span>
            {% elsif item.image %}
              <img src="{{ image_url }}" alt="{{ item.alt | default: item.title | escape }}">
            {% else %}
              <span class="portfolio-placeholder"></span>
            {% endif %}
            {% if item.image and display_count %}
              <span class="portfolio-count">{{ display_count }}</span>
            {% endif %}
            {% if item.image %}
            <span class="portfolio-card-meta">
              <span class="portfolio-card-title">{{ card_title }}</span>
              <span class="portfolio-card-subtitle">{{ card_subtitle }}, {{ item.year }}</span>
            </span>
            {% endif %}
          </button>
          {% assign portfolio_index = portfolio_index | plus: 1 %}
        {% endfor %}
      </div>
    </section>
  {% endfor %}
</div>

<div class="portfolio-lightbox" aria-hidden="true" role="dialog" aria-label="Portfolio image viewer">
  <button class="portfolio-lightbox-button portfolio-lightbox-close" type="button" aria-label="Close">×</button>
  <figure class="portfolio-lightbox-figure">
    <span class="portfolio-lightbox-counter" aria-live="polite"></span>
    <button class="portfolio-lightbox-button portfolio-lightbox-prev" type="button" aria-label="Previous">‹</button>
    <span class="portfolio-lightbox-media">
      <img src="" alt="">
      <iframe class="portfolio-lightbox-embed" src="" title="500px embedded photo" allowfullscreen loading="lazy"></iframe>
    </span>
    <figcaption>
      <span class="portfolio-lightbox-copy">
        <span class="portfolio-lightbox-title"></span>
        <span class="portfolio-lightbox-subtitle"></span>
        <span class="portfolio-lightbox-description"></span>
      </span>
      <span class="portfolio-lightbox-actions">
        <a class="portfolio-lightbox-source" href="#" target="_blank" rel="noopener">View on 500px</a>
        <a class="portfolio-lightbox-link" href="#" target="_blank" rel="noopener">Read blog</a>
      </span>
    </figcaption>
    <button class="portfolio-lightbox-button portfolio-lightbox-next" type="button" aria-label="Next">›</button>
  </figure>
</div>

<script>
  (function() {
    const allCards = Array.from(document.querySelectorAll('.portfolio-card'));
    const cards = allCards.filter(card => card.dataset.placeholder !== 'true');
    const portfolioGrids = Array.from(document.querySelectorAll('.portfolio-grid'));
    const lightbox = document.querySelector('.portfolio-lightbox');
    if (!cards.length || !lightbox) return;

    function layoutMasonryGrid(grid) {
      const gridCards = Array.from(grid.querySelectorAll('.portfolio-card'));
      const singleColumn = window.matchMedia('(max-width: 560px)').matches;

      if (singleColumn) {
        grid.classList.remove('is-masonry');
        grid.style.removeProperty('height');
        gridCards.forEach(card => {
          card.style.removeProperty('left');
          card.style.removeProperty('top');
          card.style.removeProperty('width');
        });
        return;
      }

      const columnCount = window.matchMedia('(max-width: 960px)').matches ? 2 : 3;
      const gap = 12;
      const columnWidth = (grid.clientWidth - gap * (columnCount - 1)) / columnCount;
      const columnHeights = Array(columnCount).fill(0);
      grid.classList.add('is-masonry');

      gridCards.forEach(card => {
        const requestedSpan = card.classList.contains('is-double-wide') ||
          card.classList.contains('is-split-cover')
          ? 2
          : 1;
        const columnSpan = Math.min(requestedSpan, columnCount);
        const preferredColumn = Number(card.dataset.layoutColumn) - 1;
        const candidateColumns = Array.from(
          { length: columnCount - columnSpan + 1 },
          (_, index) => index
        );
        const placementTop = columnIndex =>
          Math.max(...columnHeights.slice(columnIndex, columnIndex + columnSpan));
        const hasValidPreference = Number.isInteger(preferredColumn) &&
          preferredColumn >= 0 &&
          preferredColumn + columnSpan <= columnCount;
        const columnIndex = hasValidPreference
          ? preferredColumn
          : candidateColumns.reduce((best, candidate) =>
              placementTop(candidate) < placementTop(best) ? candidate : best
            );
        const cardTop = placementTop(columnIndex);
        card.style.width = `${columnWidth * columnSpan + gap * (columnSpan - 1)}px`;
        card.style.left = `${columnIndex * (columnWidth + gap)}px`;
        card.style.top = `${cardTop}px`;
        const nextHeight = cardTop + card.getBoundingClientRect().height + gap;
        for (let index = columnIndex; index < columnIndex + columnSpan; index += 1) {
          columnHeights[index] = nextHeight;
        }
      });

      grid.style.height = `${Math.max(...columnHeights) - gap}px`;
    }

    function layoutPortfolioGrids() {
      portfolioGrids.forEach(layoutMasonryGrid);
    }

    let layoutFrame;
    function schedulePortfolioLayout() {
      window.cancelAnimationFrame(layoutFrame);
      layoutFrame = window.requestAnimationFrame(layoutPortfolioGrids);
    }

    layoutPortfolioGrids();
    window.addEventListener('resize', schedulePortfolioLayout);

    const image = lightbox.querySelector('img');
    const embed = lightbox.querySelector('.portfolio-lightbox-embed');
    const title = lightbox.querySelector('.portfolio-lightbox-title');
    const subtitle = lightbox.querySelector('.portfolio-lightbox-subtitle');
    const description = lightbox.querySelector('.portfolio-lightbox-description');
    const counter = lightbox.querySelector('.portfolio-lightbox-counter');
    const blogLink = lightbox.querySelector('.portfolio-lightbox-link');
    const sourceLink = lightbox.querySelector('.portfolio-lightbox-source');
    const closeButton = lightbox.querySelector('.portfolio-lightbox-close');
    const prevButton = lightbox.querySelector('.portfolio-lightbox-prev');
    const nextButton = lightbox.querySelector('.portfolio-lightbox-next');
    let activeIndex = 0;
    let activePhotoIndex = 0;
    let activeGallery = [];

    function splitList(value) {
      if (!value) return [];
      return value.split('||');
    }

    function getGallery(card) {
      const images = splitList(card.dataset.galleryImages);
      const largeImages = splitList(card.dataset.galleryLargeImages);
      const embeds = splitList(card.dataset.galleryEmbeds);
      const sources = splitList(card.dataset.gallerySources);
      const photoTitles = splitList(card.dataset.galleryPhotoTitles);
      const photoDescriptions = splitList(card.dataset.galleryDescriptions);
      const aspects = splitList(card.dataset.galleryAspects);
      const fallbackImage = card.dataset.largeImage || card.dataset.image;
      const itemCount = Math.max(
        images.length,
        largeImages.length,
        embeds.length,
        sources.length,
        photoTitles.length,
        photoDescriptions.length,
        aspects.length,
        1
      );

      return Array.from({ length: itemCount }, (_, photoIndex) => {
        const photoImage = images[photoIndex] || "";
        return {
          image: photoImage || fallbackImage,
          largeImage: largeImages[photoIndex] || photoImage || fallbackImage,
          embedUrl: embeds[photoIndex] || "",
          sourceUrl: sources[photoIndex] || card.dataset.sourceUrl || "",
          photoTitle: photoTitles[photoIndex] || card.dataset.title,
          description: photoDescriptions[photoIndex] || card.dataset.description || "",
          aspect: aspects[photoIndex] || card.dataset.aspectRatio || "4/3"
        };
      }).filter(photo => photo.image || photo.embedUrl);
    }

    function splitCaption(description) {
      const lines = (description || "")
        .split(/\r?\n/)
        .map(line => line.trim())
        .filter(Boolean);
      return {
        location: lines[0] || "",
        body: lines.slice(1).join("\n")
      };
    }

    function trimTerminalPunctuation(value) {
      return (value || "").replace(/[.。]+$/u, "");
    }

    function normalizeImageUrl(value) {
      return (value || "")
        .replace(/&amp;/g, "&")
        .trim();
    }

    function getCoverPhotoIndex(card) {
      const coverImage = normalizeImageUrl(card.dataset.image);
      const coverLargeImage = normalizeImageUrl(card.dataset.largeImage);
      if (!coverImage && !coverLargeImage) return 0;

      const matchIndex = activeGallery.findIndex(photo => {
        const imageUrl = normalizeImageUrl(photo.image);
        const largeImageUrl = normalizeImageUrl(photo.largeImage);
        return imageUrl === coverImage ||
          imageUrl === coverLargeImage ||
          largeImageUrl === coverImage ||
          largeImageUrl === coverLargeImage;
      });

      return matchIndex >= 0 ? matchIndex : 0;
    }

    function render(index, photoIndex = 0) {
      activeIndex = (index + cards.length) % cards.length;
      const card = cards[activeIndex];
      activeGallery = getGallery(card);
      activePhotoIndex = (photoIndex + activeGallery.length) % activeGallery.length;
      const activePhoto = activeGallery[activePhotoIndex];
      counter.textContent = `${activePhotoIndex + 1} / ${activeGallery.length}`;
      const activeAspect = activePhoto.aspect || card.dataset.aspectRatio || "4/3";
      const aspectParts = activeAspect.split("/");
      const aspectRatio = Number(aspectParts[0]) / Number(aspectParts[1]);
      lightbox.style.setProperty("--portfolio-lightbox-aspect", activeAspect);
      lightbox.style.setProperty("--portfolio-lightbox-aspect-ratio", Number.isFinite(aspectRatio) ? aspectRatio : 1.3333);
      if (activePhoto.embedUrl) {
        image.removeAttribute('src');
        image.style.display = "none";
        embed.src = activePhoto.embedUrl;
        embed.classList.add('is-visible');
      } else {
        embed.removeAttribute('src');
        embed.classList.remove('is-visible');
        image.src = activePhoto.largeImage || activePhoto.image;
        image.style.display = "";
      }
      image.alt = card.querySelector('img')?.alt || card.dataset.title;
      const caption = splitCaption(activePhoto.description);
      const location = trimTerminalPunctuation(caption.location || card.dataset.place);
      title.textContent = (activePhoto.photoTitle || card.dataset.title).trim();
      subtitle.textContent = location ? `${location}, ${card.dataset.year}` : card.dataset.year;
      description.textContent = caption.body;
      description.classList.toggle('is-visible', Boolean(caption.body));
      const hasMultiplePhotos = activeGallery.length > 1;
      prevButton.disabled = !hasMultiplePhotos;
      nextButton.disabled = !hasMultiplePhotos;
      if (card.dataset.blogUrl) {
        blogLink.href = card.dataset.blogUrl;
        blogLink.classList.add('is-visible');
      } else {
        blogLink.removeAttribute('href');
        blogLink.classList.remove('is-visible');
      }
      if (activePhoto.sourceUrl) {
        sourceLink.href = activePhoto.sourceUrl;
        sourceLink.textContent = card.dataset.sourceLabel || "View on 500px";
        sourceLink.classList.add('is-visible');
      } else {
        sourceLink.removeAttribute('href');
        sourceLink.classList.remove('is-visible');
      }
    }

    function openLightbox(index) {
      activeIndex = (index + cards.length) % cards.length;
      activeGallery = getGallery(cards[activeIndex]);
      render(index, getCoverPhotoIndex(cards[activeIndex]));
      lightbox.classList.add('is-open');
      lightbox.setAttribute('aria-hidden', 'false');
      document.body.style.overflow = 'hidden';
    }

    function closeLightbox() {
      lightbox.classList.remove('is-open');
      lightbox.setAttribute('aria-hidden', 'true');
      document.body.style.overflow = '';
    }

    cards.forEach((card, index) => {
      card.addEventListener('click', () => openLightbox(index));
    });

    function moveLightbox(delta) {
      if (activeGallery.length <= 1) return;
      render(activeIndex, activePhotoIndex + delta);
    }

    closeButton.addEventListener('click', closeLightbox);
    prevButton.addEventListener('click', () => moveLightbox(-1));
    nextButton.addEventListener('click', () => moveLightbox(1));

    lightbox.addEventListener('click', (event) => {
      if (event.target === lightbox) closeLightbox();
    });

    document.addEventListener('keydown', (event) => {
      if (!lightbox.classList.contains('is-open')) return;
      if (event.key === 'Escape') closeLightbox();
      if (event.key === 'ArrowLeft') moveLightbox(-1);
      if (event.key === 'ArrowRight') moveLightbox(1);
    });
  })();
</script>
