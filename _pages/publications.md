---
layout: page
permalink: /publications/
title: publications
description: 
# years: [2024, 2023, 2021, 2020, 2018]
nav: true
nav_order: 1
---
<!-- _pages/publications.md -->



<div class="Publications">
<h1>Preprints</h1>

{% bibliography -f {{ site.scholar.bibliography }} -q @misc* %}
<!-- {%- for y in page.years %}
  <h2 class="year">{{y}}</h2>


{% endfor %} -->
<h1>Publications</h1>
{% bibliography -f {{ site.scholar.bibliography }} -q @article* %}
</div>


<!-- {%- for y in page.years %}
  <h2 class="year">{{y}}</h2>
  {% bibliography -f {{ site.scholar.bibliography }} -q @*[year={{y}}]* %}
{% endfor %}

</div> -->
