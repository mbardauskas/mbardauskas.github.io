title: Web workers
tags:
  - JavaScript
id: 12
categories:
  - Development
date: 2013-09-01 20:32:55
---

Have you ever used Web Workers? If you haven't, remember that there's a limit for how many web workers you can use and each worker should be closed after it finished its code.

Me and my colleague came across a strange bug in IE10 using [BlackAndWhite ](https://github.com/GianlucaGuarini/jQuery.BlackAndWhite)jQuery plugin - images would stop showing up if there are more than 25 on the page. Turns out, the script is using a Web Worker to convert images to grayscale and IE10 has a limit of 25 workers. Browsers do not close Web Workers automatically, plus IE10 has its own method for closing  the worker thread.

See[ W3C standard](http://www.w3.org/TR/workers/#dedicated-workers-and-the-worker-interface) and [IE10 specification](http://msdn.microsoft.com/en-us/library/ie/hh673568(v=vs.85).aspx) for more details. Or just the see the [commit we've proposed](https://github.com/mbardauskas/jQuery.BlackAndWhite/commit/50df583176fc01e0ecbb0478c33318c14b4b30b4) for [BlackAndWhite ](https://github.com/GianlucaGuarini/jQuery.BlackAndWhite)plugin, it should contain all the information you need regarding this issue.