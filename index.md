---
layout: schedule
title: Welcome
---

Welcome to CS 386 -- {{ site.title }}! This course gives students the opportunity to engage with alumni mentors from industry and develop their identities as computing professionals.

Computer science is a broad, diverse field. No matter your background, your hobbies, or your working style, computer science has a place for you. Finding that place and navigating the field may seem daunting at times, but we aim to build a support structure through classmates, peers, teachers, and mentors to make the journey easier.

Classes will be held in HR 435 from **4:45&ndash;6:25pm**.

## Upcoming Schedule

{%- assign today_date = 'now' | date: '%Y-%m-%d' -%}
{%- assign today = today_date | date: '%s'| abs -%}
{%- assign beg_date = '2021-08-22' | date: '%s' | abs -%}
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
