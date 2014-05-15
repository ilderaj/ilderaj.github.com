---
layout: post
title: "SEO Tips For Jekyll Bootstrap"
description: "introducing some of the seo tips for jb"
category: Coding
tags: [Jekyll, SEO]
---
{% include JB/setup %}
There are many SEO tricks for JB. Some of them which I think are easy to manipulate are as below.

-Dead URL should be firstly avoided. Open `_config.yml` and remove `/:categories` from `permalink` part.
-Then set `production_url` to the domain name of the Jekyll-Bootstrap site. [www.jasred.com](http://www.jasred.com)in my case.
-Replace the default `sitemap.txt` with a `sitemap.xml` which would be more Google-friendly. Write the following content in the new `.xml` file:
```
---
# Remember to set production_url in your _config.yml file!
layout: nil
title : Sitemap
---
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
{% for post in site.posts %}
    <url>
        <loc>{{site.production_url}}{{ post.url }}</loc>
    </url>
{% endfor %}
{% for page in site.pages %}
    <url>
        <loc>{{site.production_url}}{{ page.url }}</loc>
    </url>
{% endfor %}
</urlset>
```
-Create a file named `robots.txt` in the root directory of your repository:
```
---
title: robots
---
User-agent: *
Sitemap: <{{site.production_url}}/sitemap.xml>
```
-Last but not least, keep producing content. 
