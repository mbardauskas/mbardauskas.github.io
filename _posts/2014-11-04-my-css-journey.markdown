title: My CSS journey
tags:
  - CSS
  - HTML
id: 95
categories:
  - Development
date: 2014-11-04 22:25:40
---

I've started writing my first lines of CSS more than 10 years ago. It's been quite a learning process. I remember the times when having one class for one element was a norm. I even remember the times when IE7 was considered new and kind of great.

### The early days

CSS was the easiest way to go for me back in the day, since it was the simplest one. No loops, no variables, just describing how your HTML elements look. <!--more-->Redundant, yes, but that didn't seem like a problem. First attempts were mostly trial and error. And that went on for quite some time. In the beginning I had some styling inline, but that changed over time. Anyway, I got skilled at it pretty quickly.

Good knowledge in CSS made me a little lazy in other areas. I usually avoided extending my knowledge with internal workings of CMSes I've had been using. Why? Because I could do most of what I've wanted with only HTML and CSS. And do it quick. Custom data and other custom functionality was another question.

I don't remember having any trouble maintaining CSS back then. But then again, as a freelancer I usually didn't do any facelifts. Launched websites didn't require much support either, since the projects were quite simple.

### Don't repeat yourself and multiple classes for HTML elements

(Not to mix with [DRY CSS by Jeremy Clarke](http://vimeo.com/38063798).)

Around three years ago a start-up hired me to write CSS for their projects. They were making a mobile app for a major retailer in Lithuania and a part of their project was mobile web application. I've started with what I know and what I can. During the process we've decided to refactor the CSS and go for re-usability. Meaning we would simply reuse existing CSS classes to build blocks in different variations without any new CSS code.

At the beginning it seemed as a dreadful task. There were countless classes, up to around 7 classes for HTML elements. But after implementing the first pages, it started to pay off. Creating new pages had been really fast since we've had a lot of styles already and the designer was quite good at reusing his designs. Basically new pages required to write HTML with appropriate utility classes and add new classes (which identified new modules) to apply additional design features.

The technique required us to develop a naming convention. For example, all text related classes had a "t" prefix before (_tsize11, tsize12, tsize13, tgrey, tred, tblue, tblue2, tbold, tcenter,_ etc.).

Such technique might give you a headache if not used properly. One of the most important things here is not to mix utility classes to your modular CSS selectors (just create a new one instead). For example:
<pre>.catalog .tsize.tcenter .title {} /* hardly maintainable */
.catalog .catalog-head .title {} /* is fine */</pre>
When I've started working with my current company two years ago, they've had a freelancer who used to write selectors similar to a bad example above, thus when I've started coding using this principle in one of the projects I was quickly ordered not to use it.

Overall, this was a great technique for websites and apps with a clear design guideline. One thing to look out for is not to overdo with the utility classes. Identify and reuse in small chunks, otherwise it will lose it's purpose.

### Mix of SMACSS and DRY principle

<span style="line-height: 1.5;">I've tried a mix of SMACSS and DRY at one time. It was a bad idea, maintaining it is real hell. Basically I've taken naming conventions from SMACSS and tried to apply DRY principle (again, not the [DRY CSS](http://vimeo.com/38063798) methodology). I guess I took it too far. The worst part of it is that I understood my mistakes only when I had to go back and do some changes. </span>

The idea was to create a few generalised content blocks and have lots of utility classes (w250, w300, relative, etc.). I ended up extending main block for every new piece of different content. There were shared styles (mostly common ones such as position, background, font size, etc.) across those blocks, but it's not worth doing. Separate it to a different block instead for better maintainability.

When I look back, I think I could have avoided a great deal of issues simply by avoiding to extend current blocks with modifier classes. Here's an example of what I mean:
<pre>/* maintaining hell */
.b-container.blogpost { }

/* a better approach */
.b-container { }
.blogpost { }</pre>
Overall, I guess it was a matter of poorly implemented techniques. And the fact that they were mixed up. Lesson learned.

### BEM

The latest CSS technique that I've tried is called BEM. I'm really impressed with the results. I've got super fast at writing CSS and maintaining it seems to be a bliss.  You can check the whole [guideline](https://bem.info/method/) if you are interested.

Read more about my experience using BEM technique in upcoming posts.