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
<div class="Preprints">
{% bibliography -f {{ site.scholar.bibliography }} -q @misc* %}
</div>


<div class="Publications">

<!-- {%- for y in page.years %}
  <h2 class="year">{{y}}</h2>
  
{% endfor %} -->
{% bibliography -f {{ site.scholar.bibliography }} -q @article* %}
</div>


<!-- {%- for y in page.years %}
  <h2 class="year">{{y}}</h2>
  {% bibliography -f {{ site.scholar.bibliography }} -q @*[year={{y}}]* %}
{% endfor %}

</div> -->
