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
</style>

<h2 class="publications-page-title">Full Publications</h2>

<figure class="publication-cover">
  <img src="{{ '/assets/img/publication/como-lake.jpg' | relative_url }}" alt="Como Lake photographed by Wenrui">
  <figcaption>cover image: Como Lake 📷 Wenrui</figcaption>
</figure>

Full-text PDFs of all publications are available for download **[here]**.<br>
†Equal Contribution, *Corresponding Author

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
      <div class="title"><a href="{{ link.doi }}"><span style="color:var(--site-blue);">{{ link.title }}</span></a></div>
      <div class="author">{{ link.authors }}</div>
      <div class="periodical"><em>{{ link.journal }}</em>
      </div>
    <div class="links">
      {% if link.pdf %} 
      <a href="{{ link.pdf }}" class="btn btn-sm z-depth-0" role="button" target="_blank">PDF</a>
      {% endif %}
      {% if link.doi %} 
      <a href="{{ link.doi }}" class="btn btn-sm z-depth-0" role="button" target="_blank">DOI</a>
      {% endif %}
      {% if link.code %} 
      <a href="{{ link.code }}" class="btn btn-sm z-depth-0" role="button" target="_blank">Code</a>
      {% endif %}
      {% if link.data %} 
      <a href="{{ link.data }}" class="btn btn-sm z-depth-0" role="button" target="_blank">Data</a>
      {% endif %}
      {% if link.page %} 
      <a href="{{ link.page }}" class="btn btn-sm z-depth-0" role="button" target="_blank">Project Page</a>
      {% endif %}
      {% if link.bibtex %} 
      <a href="{{ link.bibtex }}" class="btn btn-sm z-depth-0" role="button" target="_blank">BibTex</a>
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
