---
layout: schedule
title: Welcome
---

{% comment %}
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bulma-carousel@4.0.4/dist/css/bulma-carousel.min.css">

<style>
.slider-container {
  margin-bottom: 1rem;
  background-color: whitesmoke;
}

.slider-item {
  border: 3px solid white;
}

.carousel .card {
  box-shadow: unset;
  background-color: whitesmoke;
}

.carousel .card-content {
  font-size: 0.8rem;
  padding: 0.5rem 1.0rem;
  background-color: whitesmoke;
}
</style>

<div id="field-trips" class="carousel">
  <div class="item-1">
    <div class="card">
      <div class="card-image">
        <img class="image" src="images/autodesk2019.jpg"/>
      </div>
      <div class="card-content">
        Students at the <a href="https://www.autodesk.com/technology-centers/san-francisco">AutoDesk Technology Center</a> field trip as part of the <a href="https://scholars.cs.usfca.edu/cs186-fall2019/">Community Engaged CS</a> course in 2019.
      </div>
    </div>
  </div>

  <div class="item-2">
    <div class="card">
      <div class="card-image">
        <img class="image" src="images/lyft2019.jpg"/>
      </div>
      <div class="card-content">
        Students at the <a href="https://www.lyft.com/careers">Lyft</a> field trip as part of the <a href="https://scholars.cs.usfca.edu/cs186-fall2019/">Community Engaged CS</a> course in 2019.
      </div>
    </div>
  </div>

  <div class="item-3">
    <div class="card">
      <div class="card-image">
        <img class="image" src="images/github2019.jpg"/>
      </div>
      <div class="card-content">
        <a href="https://twitter.com/bdougieYO">Brian Douglas</a>, Developer Advocate at Github.com, speaking to students as part of the <a href="https://scholars.cs.usfca.edu/cs186-fall2019/">Community Engaged CS</a> course in 2019.
      </div>
    </div>
  </div>

  <div class="item-4">
    <div class="card">
      <div class="card-image">
        <img class="image" src="images/autodesk_inside2019.jpg"/>
      </div>
      <div class="card-content">
        Students at the <a href="https://www.autodesk.com/technology-centers/san-francisco">AutoDesk Technology Center</a> field trip as part of the <a href="https://scholars.cs.usfca.edu/cs186-fall2019/">Community Engaged CS</a> course in 2019.
      </div>
    </div>
  </div>  
</div>
{% endcomment %}

<div class="notification is-danger">
  <button class="delete"></button>
  <p>All instruction for Fall 2020 will be conducted remotely via Zoom. See the <a href="https://myusf.usfca.edu/covid">USF Remote</a> page for more resources related to the ongoing COVID-19 pandemic.</p>
</div>

{{ site.description }}

Classes are livestreamed on **Fridays** from **1:00pm&ndash;2:45pm** via [Zoom]({{ site.zoom }}).

[Getting Started Guide]({{ "/guides/getting-started.html" | relative_url }}){: .button .is-primary } &nbsp; [Join Livestream]({{ site.zoom }}){: .button .is-primary}

## Upcoming Schedule

{%- assign today_date = 'now' | date: '%Y-%m-%d' -%}
{%- assign today = today_date | date: '%s'| abs -%}
{%- assign beg_date = '2020-08-18' | date: '%s' | abs -%}
{%- assign beg_index = 0 -%}

{%- if today > beg_date -%}
  {%- assign end_index = site.data.schedule.weeks | size | minus: 1 -%}

  {%- for week in site.data.schedule.weeks limit:end_index -%}
    {%- if week.date -%}
      {%- assign as_seconds = week.date | date: '%s' | abs -%}
      {%- if as_seconds > today -%}
        {%- break -%}
      {%- endif -%}
    {%- endif -%}
    {%- assign beg_index = forloop.index0 -%}
  {%- endfor -%}

  {%- assign beg_index = beg_index | minus: 1 -%}
{%- endif -%}

{% for week in site.data.schedule.weeks offset:beg_index limit:3 %}
{% include week.html week = week %}
{% endfor %}


<script>
document.addEventListener('DOMContentLoaded', () => {
  (document.querySelectorAll('.notification .delete') || []).forEach(($delete) => {
    $notification = $delete.parentNode;
    $delete.addEventListener('click', () => {
      $notification.parentNode.removeChild($notification);
    });
  });
});
</script>

{% comment %}
<script src="https://cdn.jsdelivr.net/npm/bulma-carousel@4.0.4/dist/js/bulma-carousel.min.js"></script>
<script>
bulmaCarousel.attach('#field-trips', {
  slidesToScroll: 1,
  slidesToShow: 2,
  infinite: true,
  autoplay: true,
  duration: 2000,
  pauseOnHover: true
});
</script>
{% endcomment %}
