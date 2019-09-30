---
layout: grid
title: People
permalink: /people
description: faculty, post-docs, and students in the lab, and collaborators
---


### Faculty
{% assign number_printed = 0 %}
{% for person in site.people %}
{% if person.position == "faculty" %}
{% if person.description == "Principal Investigator" %}

{% assign mod3 = number_printed | modulo: 3 %}

{% if mod3 == 0 %}
<div class="row">
{% endif %}

<div class="person">
    <div class="thumbnail">
        <a href="{{ person.url | prepend: site.baseurl | prepend: site.url }}">
        {% if person.img %}
        <img class="thumbnail" src="{{ person.img | prepend: '/assets/img/' | prepend: site.baseurl | prepend: site.url }}"/>
        {% else %}
        <div class="thumbnail blankbox"></div>
        {% endif %}    
        <span> <!-- mouse over material --> </span>
        </a>
    </div>
    <a href="{{ person.url | prepend: site.baseurl | prepend: site.url }}">
        <h4>{{ person.name }}</h4>
    </a>
    {% if person.description %}
    <i><p>{{ person.description }}</p></i>
    {% endif %}
</div>

{% assign number_printed = number_printed | plus: 1 %}

{% if mod3 == 2 %}
</div>
{% endif %}
{% endif %}
{% endif %}
{% endfor %}

{% for person in site.people %}
{% if person.position == "faculty" %}
{% if person.description != "Principal Investigator" %}

{% assign mod3 = number_printed | modulo: 3 %}

{% if mod3 == 0 %}
<div class="row">
{% endif %}

<div class="person">
    <div class="thumbnail">
        <a href="{{ person.url | prepend: site.baseurl | prepend: site.url }}">
        {% if person.img %}
        <img class="thumbnail" src="{{ person.img | prepend: '/assets/img/' | prepend: site.baseurl | prepend: site.url }}"/>
        {% else %}
        <div class="thumbnail blankbox"></div>
        {% endif %}    
        <span> <!-- mouse over material --> </span>
        </a>
    </div>
    <a href="{{ person.url | prepend: site.baseurl | prepend: site.url }}">
        <h4>{{ person.name }}</h4>
    </a>
    {% if person.description %}
    <i><p>{{ person.description }}</p></i>
    {% endif %}
</div>

{% assign number_printed = number_printed | plus: 1 %}

{% if mod3 == 2 %}
</div>
{% endif %}
{% endif %}
{% endif %}
{% endfor %}

{% assign mod3 = number_printed | modulo: 3 %}
{% if mod3 != 0 %}
</div>
{% endif %}

### Graduate Students
{% assign number_printed = 0 %}
{% for person in site.people %}
{% if person.position == "grad" %}

{% assign mod3 = number_printed | modulo: 3 %}

{% if mod3 == 0 %}
<div class="row">
{% endif %}

<div class="person">
    <div class="thumbnail">
        <a href="{{ person.url | prepend: site.baseurl | prepend: site.url }}">
        {% if person.img %}
        <img class="thumbnail" src="{{ person.img | prepend: '/assets/img/' | prepend: site.baseurl | prepend: site.url }}"/>
        {% else %}
        <div class="thumbnail blankbox"></div>
        {% endif %}    
        <span> <!-- mouse over material --> </span>
        </a>
    </div>
    <a href="{{ person.url | prepend: site.baseurl | prepend: site.url }}">
        <h4>{{ person.name }}</h4>
    </a>
    {% if person.description %}
    <i><p>{{ person.description }}</p></i>
    {% endif %}
</div>

{% assign number_printed = number_printed | plus: 1 %}

{% if mod3 == 2 %}
</div>
{% endif %}
{% endif %}
{% endfor %}

{% assign mod3 = number_printed | modulo: 3 %}
{% if mod3 != 0 %}
</div>
{% endif %}

### Undergraduate Students
{% assign number_printed = 0 %}
{% for person in site.people %}
{% if person.position == "undergrad" %}

{% assign mod3 = number_printed | modulo: 3 %}

{% if mod3 == 0 %}
<div class="row">
{% endif %}

<div class="person">
    <div class="thumbnail">
        <a href="{{ person.url | prepend: site.baseurl | prepend: site.url }}">
        {% if person.img %}
        <img class="thumbnail" src="{{ person.img | prepend: '/assets/img/' | prepend: site.baseurl | prepend: site.url }}"/>
        {% else %}
        <div class="thumbnail blankbox"></div>
        {% endif %}    
        <span> <!-- mouse over material --> </span>
        </a>
    </div>
    <a href="{{ person.url | prepend: site.baseurl | prepend: site.url }}">
        <h4>{{ person.name }}</h4>
    </a>
    {% if person.description %}
    <i><p>{{ person.description }}</p></i>
    {% endif %}
</div>

{% assign number_printed = number_printed | plus: 1 %}

{% if mod3 == 2 %}
</div>
{% endif %}
{% endif %}
{% endfor %}

{% assign mod3 = number_printed | modulo: 3 %}
{% if mod3 != 0 %}
</div>
{% endif %}

### Former Students

{% for person in site.people %}
{% if person.position == "alum" %}

<div class="link">
    <a href="{{ person.url | prepend: site.baseurl | prepend: site.url }}">
        <h4>{{ person.name }}</h4>
    </a>
    {% if person.description %}
    <i><p>{{ person.description }}</p></i>
    {% endif %}
</div>

{% endif %}
{% endfor %}


## External Collaborators

- [Adam Albright](http://web.mit.edu/albright/www/)
- [Leon Bergen](http://profiles.ucsd.edu/leon.bergen)
- [Matthew Carlson](http://cls.psu.edu/people/mtc173)
- [Meghan Clayards](https://www.mcgill.ca/linguistics/people/faculty/clayards)
- [Joshua Hartshorne](http://l3atbc.org/JKHartshorne.About.html)
- [Yoonjung Kang](https://www.yoonjungkang.com)
- [Roni Katzir](https://english.tau.ac.il/profile/rkatzir)
- [Joseph Keshet](http://u.cs.biu.ac.il/~jkeshet/)
- [James Kirby](http://www.lel.ed.ac.uk/~jkirby/)
- [Roger Levy](http://www.mit.edu/~rplevy/)
- [Tal Linzen](http://tallinzen.net)
- [Martina Martinovi&#263;](http://inamartinovic.com)
- [Emily Morgan](https://sites.tufts.edu/emilymorgan/)
- [Tamara Rathcke](https://www.kent.ac.uk/secl/ell/staff/rathcke.html)
- [Jason Riggle](http://hum.uchicago.edu/~jriggle/)
- [Derek Ruths](http://www.derekruths.com)
- [Kenny Smith](https://www.ed.ac.uk/profile/kenny-smith)
- [Jane Stuart-Smith](https://www.gla.ac.uk/schools/critical/staff/janestuart-smith/)
- [Michael Wagner](http://www.mcgill.ca/linguistics/people/faculty/wagner)
- Tae-Jin Yoon
- [Alan Yu](https://lucian.uchicago.edu/blogs/aclyu/)
