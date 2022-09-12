---
layout: page
title: Documentation
lang: en
permalink: /en/docs/
lang-ref: docs
---

# Documentation

This documentation is an extended version of book "***The abc of ABCD: the Reference Manual - Version 2.0f***" by {{ site.author[page.lang] }}. It contains the CISIS manuals, SECS Web and other loose topics that have been grouped together on this site.


## Abstract

This site aims at providing all relevant background information and instructions on how to use the integrated library and documentation management system 'ABCD'. Both the basic operations and the advanced management of the software are discussed, as are useful and necessary topics concerning the ISIS-software on which ABCD is based. In this new edition the new features of version 2.0 are added : the use of different flavors of CISIS, of Unicode,and the digital library capabilities as well as some additional modules (ODDS, LDAP, DSpaceBridge) and utilities (UTF8-conversion, loanobjects creation...) .

## Table of Contents

<div class="section-index">
    <hr class="panel-line">
    {% assign posts=site.pages | where:"lang", page.lang %}
      {% if page.description != '' %}
        {% for post in posts %}    
    <div class="entry">
    <h5><a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a></h5>
    <p>{{ post.description }}</p>
    </div>
        {% endfor %}
    {% endif %}
</div>


For features, getting started with development, see the {% include doc.html name="Getting Started" path="getting-started" %} page. Would you like to request a feature or contribute?
[Open an issue]({{ site.repo }}/issues)
