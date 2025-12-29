---
layout: page
permalink: /publications/
title: Publications
description: >
  Categorized in reverse chronological order.<br>
  <sup>#</sup> indicates equal contribution.
nav: true
nav_order: 2
---

<!-- _pages/publications.md -->

<!-- Bibsearch Feature -->

<p>
  <a href="https://scholar.google.com/citations?user=CK8UMPkAAAAJ" target="_blank" rel="noopener noreferrer">
    Google Scholar
  </a>
</p>

<!-- Filter by text -->
{% include bib_search.liquid %}

<!-- Filter checkboxes -->
<div id="pub-filters" style="margin-bottom: 1em;">
  <label style="margin-right: 1em;">
    <input type="checkbox" id="filter-journal">
    Journal 
  </label>
  <label>
    <input type="checkbox" id="filter-conference">
    Conference 
  </label>
</div>


<!-- Paper list -->
<div class="publications">
  {% bibliography %}
</div>


<!-- Filter logic -->
<script>
  document.addEventListener("DOMContentLoaded", function () {
    function filterPublications() {
      const showJournal = document.getElementById('filter-journal').checked;
      const showConference = document.getElementById('filter-conference').checked;

      const pubItems = document.querySelectorAll('.publications .publication-entry');

      pubItems.forEach(item => {
        const type = item.dataset.type;

        if (!showJournal && !showConference) {
          item.style.display = '';
          return;
        }
        if (type === 'article') {
          item.style.display = showJournal ? '' : 'none';
        } else if (type === 'inproceedings') {
          item.style.display = showConference ? '' : 'none';
        } else {
          item.style.display = '';
        }
      });
    }

    document.getElementById('filter-journal').addEventListener('change', filterPublications);
    document.getElementById('filter-conference').addEventListener('change', filterPublications);

    filterPublications();  // Initial run
  });
</script>