---
layout: guide
title: Class Activities
---

You can find a list of all the activities associated with this class for Fall 2020. See the [Schedule](/schedule.html) for a chronological listing with lecture recordings.

{% for category in site.data.activities %}
<div markdown="1">

### {{ category.label }}

{% assign sorted = category.items | sort: "date" %}
{% for activity in sorted %}

  - **{% if activity.link %}[{{ activity.name }}]({{ activity.link }}){% else %}{{ activity.name }}{% endif %}:** {{ activity.info }}{% if activity.from %} by *{{ activity.from | join: ", and " }}*{% endif %}{% if activity.date %} on {{ activity.date | date: "%B %d, %Y"}}{% endif %}.

{% endfor %}

<br/>

</div>
{% endfor %}
