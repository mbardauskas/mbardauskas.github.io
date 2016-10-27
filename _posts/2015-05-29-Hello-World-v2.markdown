title: Hello World v2
date: 2015-05-29 11:42:41
tags:
  - hexo
categories:
  - Development
---

It's been a while since my last post.

Lately I've been really interested in static website generators. I believe it is the future for most of the promo websites, since they they are all basically static websites, but using CMSes for easier content management. Also, static content is secure (because there is nothing to hack) and faster - everything is already processed so you just need to download it and view it.

The biggest drawback for static website generators is ease of use - now you have to be a bit technical person to edit content. However, in time, I believe, the content editing process for static website generators will be as simple as with any popular CMS. Well, it almost is. If you are able to setup a wordpress website by yourself, you will be able to use a static website generator with command line interface.

I was pleasently surprised by how easy it is to migrate from wordpress to, for example, <a href="http://hexo.io">Hexo</a>. All you need is <a href="http://hexo.io">Hexo</a>, <a href="https://github.com/hexojs/hexo-migrator-wordpress">Hexo plugin for migration</a> and <a href="https://codex.wordpress.org/Tools_Export_Screen">wordpress export file</a>. With few command lines you are done. It took me roughly 15mins to go through the docs, play around with it and migrate the content.

I didn't stop there though. After migrating the blog, I've decided that I need a CI for the blog, so I've created a <a href="https://github.com/mbardauskas/blog-hexo">git repo for the blog source</a> and build process with <a href="https://jenkins-ci.org/">Jenkins</a> on my <a href="http://en.wikipedia.org/wiki/Raspberry_Pi">raspberry pi</a> (a real use at last!). The latter took me a lot longer than the migration, but that was due to the fact, that I haven't used Jenkins before. And raspberry pi is quite slow, the build process takes a lot longer than on my local machine. Anyway, now it's automated!

