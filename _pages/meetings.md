---
layout: page
permalink: /meetings/
title: Meetings
description: past lab meetings

news: false
calendar: false
social: false
---

{% assign news = site.news | where_exp: "post", "post.title contains 'Lab meeting - '" | sort: "date" | reverse %}
{% assign grouped_news = news | group_by_exp: "post", "post.date | date: '%Y'" %}

{% for group in grouped_news %}
  <h3 class="year-toggle" id="y{{ group.name }}">{{ group.name }}</h3>
  <div class="toggle-table">
    <table class="meetings">
      {% for post in group.items %}
        <tr>
          <td class="date">{{ post.date | date: "%b %-d, %Y" }}</td>
          <td class="announcement">
            <a class="news-title" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
            {% if post.inline %}
              : {{ post.content | markdownify | strip_html | emojify }}
            {% endif %}
          </td>
        </tr>
      {% endfor %}
    </table>
  </div>
{% endfor %}
