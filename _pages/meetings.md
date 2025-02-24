---
layout: page
permalink: /meetings/
title: Meetings
description: past lab meetings

news: false
calendar: false
social: false
---
<table class="meetings">
{% assign news = site.news | reverse |where_exp: "post", "post.title contains 'Lab meeting - '"%}
{% for item in news%}
  <tr>
    <td class="date">{{ item.date | date: "%b %-d, %Y" }}</td>
    <td class="announcement">
      {% if item.inline %}
          <a class="news-title" href="{{ item.url | prepend: site.baseurl }}">{{ item.title }}</a>:
        {{ item.content | remove: '<p>' | remove: '</p>' | emojify }}
      {% else %}
        <a class="news-title" href="{{ item.url | prepend: site.baseurl }}">{{ item.title }}</a>
      {% endif %}
    </td>
  </tr>
{% endfor %}
</table>
