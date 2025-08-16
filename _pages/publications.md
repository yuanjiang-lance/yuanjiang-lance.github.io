---
layout: page
permalink: /publications/
title: Publications
description: Categorized in reverse chronological order.
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

{% include bib_search.liquid %}



<!-- Filter checkboxes -->
<div id="pub-filter" style="margin-bottom: 1rem;">
  <label><input type="checkbox" name="type" value="journal" onchange="applyFilters()"> Journal</label>
  <label style="margin-left: 1rem;"><input type="checkbox" name="type" value="conference" onchange="applyFilters()"> Conference</label>
</div>


<!-- Publication entries start -->
<div class="publications">
{% bibliography %}
</div>


<script>
function applyFilters() {
  const checkboxes = document.querySelectorAll('#pub-filter input[type=checkbox]');
  const selected = Array.from(checkboxes).filter(cb => cb.checked).map(cb => 'type-' + cb.value.toLowerCase());
  const items = document.querySelectorAll('.publications .col-sm-10, .publications .col-sm-8');

  items.forEach(item => {
    const classes = item.className.split(' ');
    const match = selected.length === 0 || selected.some(sel => classes.includes(sel));
    item.parentElement.style.display = match ? 'flex' : 'none'; // hide the entire row
  });
}
</script>


