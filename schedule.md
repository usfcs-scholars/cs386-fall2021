---
layout: schedule
title: Schedule
---

The following is the current weekly schedule. This schedule is subject to change and will be frequently updated throughout the semester. The latest deadlines may also be found on [Canvas]({{ site.canvas }}).

<!-- quick navigation -->
<div class="buttons has-addons is-centered">
  <a class="button is-small is-link is-outlined" disabled>
    Weeks:
  </a>

  {% for week in site.data.schedule.weeks %}

  <a class="button is-small is-link is-outlined" href="#week-{{ week.week }}{{ week.text | slugify }}">
    {{ week.week }}{{ week.text }}
  </a>
  {%- endfor %}
</div>

<!-- schedule -->
{% for week in site.data.schedule.weeks %}
{% include week.html week = week %}

{% comment %}
<div class="columns">
  <div class="column is-narrow">
    <div class="heading" id="week-{{ week.week }}{{ week.text | slugify }}">
      <span class="week">
        {%- if week.week %}
        Week {% if week.week < 10 %}0{% endif %}{{ week.week }}
        {%- else %}
        {{ week.text }}
        {%- endif %}
      </span>
    </div>
  </div>

  <div class="column">
    <div class="columns">
    {% for column in week.columns %}
      <div class="column is-one-third {{ column.class }}">
        <div class="heading">
          <span class="week">
            {{ column.label }}
          </span>
        </div>
        <ul class="icons">
          {%- for item in column.items %}
          <li class="{{ item.type }} {% if item.bump %}bump{% endif %}">
            {%- if item.icon %}
              <i class="{{ item.icon.class }}"></i>
            {%- else %}
              <i class="far fa-question-square"></i>
            {%- endif %}
            {%- if item.date %}
            <strong>{{ item.date | date: "%m/%d" }}:</strong>
            {%- endif %}
            {%- if item.link %}
            <a href="{{ item.link }}">
              {{ item.text }}
            </a>
            {%- else %}
            {{ item.text }}
            {% endif -%}
          </li>
          {% endfor -%}
        </ul>
      </div>
    {% endfor %}
    </div>
  </div>

</div>
{% unless forloop.last %}<hr>{% endunless %}
{% endcomment %}
<!-- end week row -->

{% endfor %}

<!-- icon legend -->
<div class="buttons">
  {%- for icon in site.data.schedule.icons %}
  <span class="button is-small is-static">
    <i class="{{ icon[1].class }}"></i>&nbsp;{{ icon[1].label }}
  </span>
  {%- endfor %}
</div>

<div class="notification is-usf-gold">
  <button class="delete"></button>
  Interested in being a <a href="guides/speaking.html">guest speaker</a> for this course? Please email Sophie at <a href="mailto:sjengle@cs.usfca.edu">sjengle@cs.usfca.edu</a> for details!
</div>

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
