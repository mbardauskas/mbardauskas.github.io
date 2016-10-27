---
layout: post
title: Fast cross-browser HTML/CSS testing
tags: CSS HTML QA
id: 7
categories: Development
date: 2013-08-28 17:11:07
---

Both techniques require PSDs of a quite skilled designer who is consistent with his/her work and manages spacing and other details to be the  same throughout all the files. Of course, the designer should be familiar with [Photoshop etiquette](http://photoshopetiquette.com/). Otherwise I would probably decide on details just by looking at the browser and Photoshop and would not use any overlay tools, because it would be just a waste of time.

## Starting from scratch

This technique is quite easy and you can test cross-browser.

<span style="line-height: 1.5;">I've tried using CSS and images as CSS backgrounds - that did not work out too well. Once you're done, you'll have to remove both the divs and the CSS (both files and tags inside HTML). I think probably the best way to do this is to create only one absolute overlay div with inline styles and image inside, because you would have to comment it out before delivering HTML.</span>
{% highlight html %}
<div style="position: absolute; z-index: 999; opacity: 0.3; -ms-filter: "progid:DXImageTransform.Microsoft.Alpha(Opacity=30)"; top: 0; left: 50%; margin-left: -750px;">
  <img src="image.jpg" style="max-width: none;" width="1500">
</div>
{% endhighlight %}
_Note: opacity is set to tell which is which, margin-left depends on image width, and max-width is used if you're using twitter bootstrap, which is quite common these days._

Such technique helps you achieve pixel perfect designs faster. Plus the development process is faster and easier as well, especially with Live preview in [Brackets](http://www.brackets.io).

## Editing existing projects

Usually I end up changing designs when the project has a demo website with running CMS. However, I use this only on Chrome and just check other browsers for big inconsistencies.

You could, of course, play with template files like in technique above, but that's not very efficient. I prefer using Chrome and it's tools. One of such tools is [PerfectPixel](https://chrome.google.com/webstore/detail/perfectpixel-by-welldonec/dkaagdgjmgdmbnecmcefdhjekcoceebi). I bet there are more, but unfortunately each one of them has its own quirks.
