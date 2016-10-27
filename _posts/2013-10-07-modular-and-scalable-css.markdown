title: Modular and scalable CSS
tags:
  - CSS
id: 24
categories:
  - Development
date: 2013-10-07 21:49:11
---

I've been working as a front-end developer for almost a year now. I still wonder which approach should I take to write my CSS code when I start a new project. It is a bit frustrating when you think that you should know what is best, but you are not entirely sure that it is the best one for the project.

I've came across an article about [modular and scalable CSS techniques](http://www.creativebloq.com/css3/create-modular-and-scalable-css-9134351). The closest thing to OOCSS to me was when we were using our own similar technique to one project at [BWS](http://balticwebstudio.com/). Of course it was not perfect, we ended up having up to 7 classes for one container (one class for each: text alignment, text size, text color, background color, etc.), but it was quite maintainable and strangely enough (at this point I mean), it was working for the developers and the manager. Actually the last designs were converted to HTML so quickly due to those classes that the team could not believe I've managed to to that in such a short amount of time. Sadly, I was discouraged from using this technique in my current workplace. However, I've been using SASS lately for all our projects and it's a bliss. I could write a very similar CSS code that we did in BWS and SASS would save us from having too much classes for elements. And that would pretty much be OOCSS.

Actually up until now I thought that OOCSS means writing CSS modules with descendant selectors depending on one main object like ".header". Never have I been so wrong (probably). And it is a common practice in our workplace. So the major problem I see with my CSS code is that I'm using a lot of descendant selectors. It's time to fix this.