---
layout: grid
title: People
permalink: /people
description: faculty, postdocs, and students in the lab, and collaborators
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


### Postdocs
{% assign number_printed = 0 %}
{% for person in site.people %}
{% if person.position == "postdoc" %}

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

### Former members

<ul class="personlist">
    {% for person in site.people %}
    {%- if person.position == "alum" -%}
    {%- if person.profile.website -%}
    <li><a href="{{ person.profile.website }}">{{ person.name }}</a></li>
    {%- else -%}
    <li>{{ person.name }}</li>
    {%- endif -%}
    {%- endif -%}
    {% endfor %}
</ul>


## External

<!-- ### Associate Collaborators -->

{% assign number_printed = 0 %}
{% for person in site.people %}
{% if person.position == "assoc" %}

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


### Other Collaborators

<ul class="personlist">
<li><a href="http://web.mit.edu/albright/www/">Adam Albright</a></li>
<li><a href="http://profiles.ucsd.edu/leon.bergen">Leon Bergen</a></li>
<li><a href="http://cls.psu.edu/people/mtc173">Matthew Carlson</a></li>
<li><a href="https://www.mcgill.ca/linguistics/people/faculty/clayards">Meghan Clayards</a></li>
<li><a href="http://socsci.uci.edu/~rfutrell/">Richard Futrell</a></li>
<li><a href="http://l3atbc.org/JKHartshorne.About.html">Joshua Hartshorne</a></li>
<li><a href="https://www.yoonjungkang.com">Yoonjung Kang</a></li>
<li><a href="https://english.tau.ac.il/profile/rkatzir">Roni Katzir</a></li>
<li><a href="http://u.cs.biu.ac.il/~jkeshet/">Joseph Keshet</a></li>
<li><a href="http://www.lel.ed.ac.uk/~jkirby/">James Kirby</a></li>
<li><a href="http://www.mit.edu/~rplevy/">Roger Levy</a></li>
<li><a href="http://tallinzen.net">Tal Linzen</a></li>
<li><a href="http://inamartinovic.com">Martina Martinovi&#263;</a></li>
<li><a href="https://mehr.cz/">Samuel Mehr</a></li>
<li><a href="https://sites.tufts.edu/emilymorgan/">Emily Morgan</a></li>
<li><a href="https://www.kent.ac.uk/secl/ell/staff/rathcke.html">Tamara Rathcke</a></li>
<li><a href="http://hum.uchicago.edu/~jriggle/">Jason Riggle</a></li>
<li><a href="http://www.derekruths.com">Derek Ruths</a></li>
<li><a href="https://www.ed.ac.uk/profile/kenny-smith">Kenny Smith</a></li>
<li><a href="https://www.microsoft.com/en-us/research/people/alsordon/">Alessandro Sordoni</a></li>
<li><a href="https://www.gla.ac.uk/schools/critical/staff/janestuart-smith/">Jane Stuart-Smith</a></li>
<li><a href="http://www.mcgill.ca/linguistics/people/faculty/wagner">Michael Wagner</a></li>
<li>Tae-Jin Yoon</li>
<li><a href="https://lucian.uchicago.edu/blogs/aclyu/">Alan Yu</a></li>
</ul>

