---
layout: post
title: "Changing Default Zooming Percentage of Safari"
description: "by setting a customized style sheet of safari"
category: tweaking
tags: [safari, osx]
---
{% include JB/setup %}
I used to be a Chrome user, because it might be the best platform crosssing browser ever. But after swiching from Windows to OS X, I found Safari is more powerful in the Mac world, because of:
* the perfect syncing with iOS devices;
* the reader friendly features like `reading list` and `reader mode`;
* the faster download speed (maybe it is just me );
* the excellent extention `click to plugin for China` which disables all the plugins (including flash) on the web page until you click on it;
* the power efficiency, compared to which Chrome should be ashamed on Mac...

The one thing about Safari that bothers me a lot is the small default font size. Of course it can be adjusted manually, and I put the font size button on the toolbar in order to make it more reachable. But Safari does not remember the last time zooming gesture, it has to be adjusted everytime...

Well it turns out that there is a easy way to solve the problem. First create a file `name.css` and write in the following content:

~~~
body {
zoom: 110%;
}
~~~

Had several tries and 110% is perfect for me (I'm using MBA 13'). Save the file and go to `Safari -- Peferences -- Advanced --Style Sheet`, and choose the `.css` file which is just created:

![zoom]({{ site.url }}/image/zoom.jpg)