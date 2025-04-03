---
layout: page
permalink: /meetings/
title: Meetings
description: past lab meetings

news: false
calendar: false
social: false
---

<script>
  document.addEventListener("DOMContentLoaded", function () {
    const headings = document.querySelectorAll("h3.year-toggle");

    headings.forEach((heading, index) => {
      const tableDiv = heading.nextElementSibling;

      if (index === 0) {
        heading.classList.add("open");
        tableDiv.classList.add("open");
      }
      heading.addEventListener("click", function () {
        heading.classList.toggle("open");
        tableDiv.classList.toggle("open");
      });
    });
  });
</script>

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
