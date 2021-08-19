---
layout: schedule
title: Welcome
---

Welcome to CS 386 -- {{ site.title }}! {{ site.description }}

{{ site.coordinates }}

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
