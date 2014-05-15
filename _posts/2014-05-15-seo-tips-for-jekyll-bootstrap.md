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

* Then set `production_url` to the domain name of the Jekyll-Bootstrap site. [www.jasred.com](http://www.jasred.com)in my case which is a customized domain.

* Replace the default `sitemap.txt` with a `sitemap.xml` which would be more search engine friendly. 

* Create a `robots.txt` file in the root directory of the repository.

* Last but not least, keep producing content. 
