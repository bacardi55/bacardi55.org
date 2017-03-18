---
layout: post
title: "Alternate css classes easily in twig"
subtitle: ""
date: 2013-02-02 21:00:00 +0100
tag: twig
---

Today, I wanted to style a little bit my project.
The basic way in classic PHP project would be to use the iterator variable of your `for loop` with the use of `modulo`.

For example:

{% highlight php linenos %}
{% raw %}<div class="<?php echo ($i % 2 == 0) 'odd' : 'even' ; ?>"></div>{% endraw %}
{% endhighlight %}

In twig, when you use a loop, there are several variables that you can use like `loop.index`, `loop.first`, `loop.last`. I won't copy/paste the official documentation here, you can read it here [twig loop documentation](http://twig.sensiolabs.org/doc/tags/for.html).

To use the modulo function in twig, just use

{% highlight twig linenos %}
{% raw %} {{ 10 % 2 }} {% endraw %}
{% endhighlight %}

And there you go, as simple as in PHP.

Then, using twig, you can do this:

{% highlight twig linenos %}
{% raw %} {% if loop.index % 2 == 0 %} {% endraw %}
{% endhighlight %}

Or in my case I needed this :

{% highlight twig linenos %}
{% raw %} {% if loop.parent.loop.index % 2 == 0 %} {% endraw %}
{% endhighlight %}

To be able to use the index of my parent loop :)

On [this blog](http://nerdpress.org/2012/02/14/modulo-in-twig/), I found the following tips :

{% highlight twig linenos %}
{% raw %} {% if loop.index divisibleby(2) %} {% endraw %}
{% endhighlight %}

Isn't it beautiful ? But it gets even better!

{% highlight twig linenos %}
{% raw %} {{ cycle(['odd', 'even'], loop.index) }} {% endraw %}
{% endhighlight %}

And there you go, thank you [twig](http://twig.sensio.org "twig") !
