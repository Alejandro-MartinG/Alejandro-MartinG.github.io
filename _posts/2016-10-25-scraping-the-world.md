---
layout: post
section-type: post
title:  "Scraping the World"
category: tech
tags: [ 'ruby' ]
---

Hi guys!

A big part of my professional experience is decated to scraping. In this
new post I'll explain how to do a simple ruby script for scraping a
website.

This post will be explain with ruby, You can select other language
better than ruby in the "scraping world" like python.

You'll need previus experience with HTML and HTTP flow.

The basic tools when you want to do scraping:
{% highlight ruby %}
require 'nokogiri'
require 'tweakphoeus'
{% endhighlight %}

`Nokogiri` is a HTML parser. We need it for manage the response. The
response always will be a string and we need convert it to the correct
format.
`Tweakphoeus` is a gem that help us to do HTTP conections.

I always do a principal method where I can see the "flow to scraping".
I think that it's a good practice to isolate errors.

In our case we go to implement a method called `extract_urls` which will
recive a string url. In the following lines can see the how initilize
the `Tweakphoeus client` and do a request to the url recived. Now the
response is saved and parse to HTML object because the real response is
a simple string.


{% highlight ruby %}
def extract_urls(url)

  @http = Tweakphoeus::Client.new()
  response = @http.get(url)
  page = Nokogiri::HTML(response.body)

  [...]

end
{% endhighlight %}



<!--Execution example:-->
<!--`ruby _site/scrap.rb-->
<!--"https://www.youtube.com/watch?v=-uYOlj51dgQ&list=PL75E6204957B76A65"`-->
