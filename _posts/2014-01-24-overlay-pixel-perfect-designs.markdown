title: Pixel perfect designs using overlay images
tags:
  - CSS
  - HTML
id: 55
categories:
  - Development
date: 2014-01-24 11:29:58
---

A while ago I've posted an [article about fast cross-browser HTML/CSS testing](http://studio36.lt/blog/fast-cross-browser-htmlcss-testing/ "Fast cross-browser HTML/CSS testing"). The "from scratch" version was using inline styles for image overlay, so it would be only HTML that has additional dev artifacts which have to be removed before shipping the code. But it wasn't really a time saver after all. Also I've had the image overlaying the page all the time, which was a bit of a problem when you wanted to inspect html and see what is causing the "unexpected".

I've improved the design overlay snippet to show image only if you hover a small rectangle fixed to the top of the page, [see the jsfiddle on this](http://jsfiddle.net/mbardauskas/3q9bf/). It's great because after hovering and right-clicking it, you can focus your editor to do the changes. Sadly this applies only to Chrome and the changes could only be seen instantly using CSS injection tool like [browser-sync](https://github.com/shakyShane/browser-sync) (might also work with other tools, I've just not tried any other yet). Though probably every front-end developer is using a tool like this already, if not - they really should.

These things made me rethink my front-end development process, there are lots of great tools to automate your tasks during development, so I've started a [framework ](https://github.com/mbardauskas/builder-framework)(or a boilerplate, not sure which one it is. I guess a mold of both) to have tasks automated for me and to deal with repeatable blocks in HTML, so I wouldn't need to go through all HTML files and remove parts of code if they changed.