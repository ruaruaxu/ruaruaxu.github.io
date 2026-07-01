---
layout: homepage
---

<style>
  .publication-cover {
    margin: 0 0 24px;
  }

  .publications-page-title {
    margin-top: 0;
  }

  .publication-cover img {
    aspect-ratio: 3 / 1;
    border-radius: 8px;
    display: block;
    object-fit: cover;
    object-position: center 76%;
    width: 100%;
  }

  .publication-cover figcaption {
    color: var(--site-muted, #6b7280);
    font-size: 12px;
    margin-top: 6px;
  }

  .working-papers {
    margin: 18px 0 28px;
    padding-left: 1.35rem;
  }

  .working-papers li {
    margin-bottom: 0.85rem;
  }

  .working-paper-title {
    color: var(--site-blue);
    font-weight: 700;
  }
</style>

<h2 class="publications-page-title no-outline">Full Publications</h2>

<figure class="publication-cover">
  <img src="{{ '/assets/img/publication/como-lake.jpg' | relative_url }}" alt="Como Lake photographed by Wenrui">
  <figcaption>cover image: Como Lake 📷 Wenrui</figcaption>
</figure>

Full-text PDFs of all publications are available for download **here**.<br>
†Equal Contribution, *Corresponding Author

## Publications

<div class="publications">
<ol class="bibliography">

{% for link in site.data.publications.all %}

<li>
<div class="pub-row">
  <div class="col-sm-3 abbr" style="position: relative;padding-right: 15px;padding-left: 15px;">
    {% if link.image %} 
    <img src="{{ link.image }}" class="teaser img-fluid z-depth-1">
    {% if link.journal_short %} 
    <abbr class="badge">{{ link.journal_short }}</abbr>
    {% endif %}
    {% endif %}
  </div>
  <div class="col-sm-9" style="position: relative;padding-right: 15px;padding-left: 20px;">
      <div class="title">
        {% if link.doi %}
        <a href="{{ link.doi }}"><span style="color:var(--site-blue);">{{ link.title }}</span></a>
        {% else %}
        <span style="color:var(--site-blue);">{{ link.title }}</span>
        {% endif %}
      </div>
      <div class="author">{{ link.authors }}</div>
      <div class="periodical"><em>{{ link.journal }}</em>
      </div>
    <div class="links">
      {% if link.pdf %} 
      <a href="{{ link.pdf }}" class="btn btn-sm z-depth-0" role="button" target="_blank">PDF</a>
      {% endif %}
      {% if link.page %}
      <a href="{{ link.page }}" class="btn btn-sm z-depth-0" role="button" target="_blank">Website</a>
      {% endif %}
      {% if link.code %} 
      <a href="{{ link.code }}" class="btn btn-sm z-depth-0 pub-link-code" role="button" target="_blank"><i class="fab fa-github" aria-hidden="true"></i> Code</a>
      {% endif %}
      {% if link.data %} 
      <a href="{{ link.data }}" class="btn btn-sm z-depth-0 pub-link-data" role="button" target="_blank"><span aria-hidden="true">🤗</span> Data</a>
      {% endif %}
      {% if link.bibtex %} 
      <a href="{{ link.bibtex }}" class="btn btn-sm z-depth-0" role="button" target="_blank">BibTex</a>
      {% endif %}
      {% if link.doi %}
      <a href="{{ link.doi }}" class="btn btn-sm z-depth-0" role="button" target="_blank">DOI</a>
      {% endif %}
      {% if link.notes %} 
      <strong> <i style="color:#e74d3c">{{ link.notes }}</i></strong>
      {% endif %}
      {% if link.others %} 
      {{ link.others }}
      {% endif %}
    </div>
  </div>
</div>
</li>

{% endfor %}

</ol>
</div>

## Working Papers

<ol class="working-papers">
  <li>Gu, X., Liu, Y*., <strong>Xu, W.</strong>, Qiu, W., Li, X., Chen, X., Lu, S., Qiu, W.* (2025-). <span class="working-paper-title">Scalable Quantification of 3D Material Albedo Reveals Consistent Cooling Mechanisms and Unequal Mitigation Potential.</span> <em>Communications Earth &amp; Environment</em> (1st Revision).</li>
  <li><strong>Xu, W.</strong>, Liang, L.* (2025-). <span class="working-paper-title">Compound Heatwave-Air Pollution Hazards Across the United States.</span> Manuscript in Preparation.</li>
  <li><strong>Xu, W.</strong>, Zhang, X., Sun, J., Liang, L.* (2026-). <span class="working-paper-title">Scaling Property-Level Wildfire Risk Assessment in California with Fine-Tuned Vision-Language Models and Prediction-Powered Inference.</span> Manuscript in Preparation.</li>
  <li><strong>Xu, W.</strong>, Agostini, G., Pierson, E.*, Blumenstock, J., Liang, L. (2026-). <span class="working-paper-title">SAEarth: Can Sparse AutoEncoders Expose Interpretable Features in Geospatial Foundation Models?</span> Manuscript in Preparation.</li>
  <li>Lyu, D.†, <strong>Xu, W.†</strong>, Wang, W., Gao, C., Zhuang, W.*, Li, Y.* (2025-). <span class="working-paper-title">Aesthetic Perception of Large Language Models.</span> Manuscript in Preparation.</li>
  <li>Lyu, D., Li, J., <strong>Xu, W.</strong>, Li, T.* (2025-). <span class="working-paper-title">Spatial Inequities in Emergency Rescue Networks in China.</span> Manuscript in Preparation.</li>
</ol>
