---
layout: page
title: people
permalink: /people/
description: current and past projects, and other resources
---

### faculty

{% for person in site.people %}
{% if person.position == 'faculty' %}
<div class="project">
    <div class="thumbnail">
        <a href="{{ person.url | prepend: site.baseurl | prepend: site.url }}">
        {% if person.img %}
        <img class="thumbnail" src="{{ person.img | prepend: site.baseurl | prepend: site.url }}"/>
        {% else %}
        <div class="thumbnail blankbox"></div>
        {% endif %}    
        <span>
            <h1>{{ person.title }}</h1>
            <br/>
            <p>{{ person.description }}</p>
        </span>
        </a>
    </div>
</div>
{% endif %}
{% endfor %}


### post-doctoral fellows

### graduate students

### undergradutate students

{% for person in site.people %}
{% if person.position == 'undergrad' %}
<div class="project">
    <div class="thumbnail">
        <a href="{{ person.url | prepend: site.baseurl | prepend: site.url }}">
        {% if person.img %}
        <img class="thumbnail" src="{{ person.img | prepend: site.baseurl | prepend: site.url }}"/>
        {% else %}
        <div class="thumbnail blankbox"></div>
        {% endif %}    
        <span>
            <h1>{{ person.title }}</h1>
            <br/>
            <p>{{ person.description }}</p>
        </span>
        </a>
    </div>
</div>
{% endif %}
{% endfor %}

### external collaborators

*   [Adam Albright](http://web.mit.edu/albright/www/)
*   [Leon Bergen](http://profiles.ucsd.edu/leon.bergen)
*   [Matthew Carlson](http://cls.psu.edu/people/mtc173)
*   [Meghan Clayards](https://www.mcgill.ca/linguistics/people/faculty/clayards)
*   [Joshua Hartshorne](http://l3atbc.org/JKHartshorne.About.html)
*   [Yoonjung Kang](https://www.yoonjungkang.com)
*   [Roni Katzir](https://english.tau.ac.il/profile/rkatzir)
*   [Joseph Keshet](http://u.cs.biu.ac.il/~jkeshet/)
*   [James Kirby](http://www.lel.ed.ac.uk/~jkirby/)
*   [Roger Levy](http://www.mit.edu/~rplevy/)
*   [Tal Linzen](http://tallinzen.net)
*   [Martina Martinović](http://inamartinovic.com)
*   [Emily Morgan](https://sites.tufts.edu/emilymorgan/)
*   [Tamara Rathcke](https://www.kent.ac.uk/secl/ell/staff/rathcke.html)
*   [Jason Riggle](http://hum.uchicago.edu/~jriggle/)
*   [Derek Ruths](http://www.derekruths.com)
*   [Kenny Smith](https://www.ed.ac.uk/profile/kenny-smith)
*   [Jane Stuart-Smith](https://www.gla.ac.uk/schools/critical/staff/janestuart-smith/)
*   [Michael Wagner](http://www.mcgill.ca/linguistics/people/faculty/wagner)
*   [Tae-Jin Yoon]()
*   [Alan Yu](https://lucian.uchicago.edu/blogs/aclyu/)
