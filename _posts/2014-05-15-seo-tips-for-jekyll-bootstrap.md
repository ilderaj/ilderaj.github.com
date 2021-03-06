---
layout: post
title: "SEO Tips for Jekyll Bootstrap"
description: "introducing some of the seo tips for jb"
category: Coding
tags: [Jekyll, SEO]
---
{% include JB/setup %}
There are many SEO tricks for JB. Some of them which I think are easy to manipulate are as below.

* Dead URL should be firstly avoided. Open `_config.yml` and remove `/:categories` from `permalink` part.

* Then set `production_url` to the domain name of the Jekyll-Bootstrap site. [www.jasred.com](http://www.jasred.com) in my case which is a [custom domain](https://help.github.com/articles/setting-up-a-custom-domain-with-github-pages).

* Replace the default `sitemap.txt` with a `sitemap.xml` which would be more search engine friendly:

<script src="https://gist.github.com/ilderaj/a139741e6b70b463bec2.js"></script>

* Create a `robots.txt` file in the root directory of the repository:

<script src="https://gist.github.com/ilderaj/8f1942efbb32856a7561.js"></script>

* Last but not least, keep producing content. 
