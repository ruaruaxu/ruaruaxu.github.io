<style>
  .news-list.is-collapsed li:nth-child(n+6) {
    display: none;
  }

  .news-date {
    color: var(--site-muted);
    font-weight: 500;
  }

  .news-show-more {
    background: transparent;
    border: 1px solid var(--site-border);
    border-radius: 6px;
    color: var(--site-link-blue);
    cursor: pointer;
    display: block;
    font-family: inherit;
    font-size: 14px;
    margin: -4px auto 18px;
    padding: 6px 18px;
  }

  .news-show-more:hover {
    border-color: var(--site-pink);
    color: var(--site-pink);
  }
</style>

<ul class="news-list is-collapsed" id="news-list">
    <li><span class="news-date">[2026.08]</span> 🎉 Our paper on 3D material albedo has been accepted for publication in <i><strong>Communications Earth &amp; Environment</strong></i>!</li>
    <li><span class="news-date">[2026.07]</span> 🎉 My first-authored paper has been accepted by <i><strong>Frontiers of Architectural Research</strong></i>!</li>
    <li><span class="news-date">[2026.04]</span> 🥳 I received the Autodesk Graduate Student Fellowship ($15,000).</li>
    <li><span class="news-date">[2026.03]</span> 😊 I presented my research on compound heat and air pollution hazards and organized the session "Exploring Spatial, Temporal, and Social Dimensions of Multiple Climatic Hazards" at <a href="https://www.aag.org/events/aag2026/">AAG 2026</a> in San Francisco.</li>
    <li><span class="news-date">[2025.07]</span> Our research on human perception disparity between urban and suburban areas has been accepted by <i><strong>Cities (SSCI, IF=6.6)</strong></i>!</li>
    <li><span class="news-date">[2025.05]</span> My first-authored paper <i>Defining and Evaluating Visual Language Models' Basic Spatial Abilities: A Perspective from Psychometrics</i> (<a href="https://arxiv.org/abs/2502.11859">DOI</a>) has been accepted by <i><strong>ACL Main (CCF-A)</strong></i>!</li>
    <li><span class="news-date">[2025.05]</span> My first-authored paper on the spatiotemporal impacts of purpose-specific human mobility on air pollution (<a href="https://doi.org/10.1016/j.scs.2025.106411">DOI</a>) has been published by <i><strong>Sustainable Cities and Society (SCI, IF=12.0)</strong></i>!</li>
    <li><span class="news-date">[2025.02]</span> I got a PhD offer from the University of Cambridge.</li>
    <li><span class="news-date">[2024.11]</span> I received the Comprehensive Excellence Award of Tsinghua.</li>
    <li><span class="news-date">[2024.09]</span> I joined the <a href="https://fi.ee.tsinghua.edu.cn/">FIB-LAB</a> at Tsinghua EE as a research assistant.</li>
    <li><span class="news-date">[2024.07]</span> I participated in cultural exchange events in Italy as an "Interdisciplinary Design Innovation Scholar" of Tsinghua <a href="https://www.cidih.tsinghua.edu.cn/en/">CIDIH</a>.</li>
    <li><span class="news-date">[2023.07]</span> I graduated from Tongji with the highest distinction (top 1%).</li>
</ul>

<button class="news-show-more" id="news-show-more" type="button" aria-expanded="false">Show more</button>

<script>
  (function() {
    const newsList = document.querySelector("#news-list");
    const showMoreButton = document.querySelector("#news-show-more");

    if (!newsList || !showMoreButton) return;

    const collapsedLimit = 5;
    const newsItems = newsList.querySelectorAll("li");

    if (newsItems.length <= collapsedLimit) {
      showMoreButton.hidden = true;
      newsList.classList.remove("is-collapsed");
      return;
    }

    showMoreButton.addEventListener("click", function() {
      const isCollapsed = newsList.classList.toggle("is-collapsed");
      showMoreButton.textContent = isCollapsed ? "Show more" : "Show less";
      showMoreButton.setAttribute("aria-expanded", String(!isCollapsed));
    });
  })();
</script>
