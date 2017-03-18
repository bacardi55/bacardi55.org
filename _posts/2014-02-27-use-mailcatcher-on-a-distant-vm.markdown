---
layout: post
title: Use mailcatcher on a distant VM
subtitle: ""
date: 2014-02-27 +0100
tag: dev mailcatcher email
---

## Simplify your email workflow development

Today, to revive this blog, a quick post about [mailcatcher](http://mailcatcher.me) that I needed to install at work as the port 25 to fire mails is blocked. I was used to work with email in a "regular" way, meaning having sendmail installed and configured and actually sending emails.

When you can't do that due to a firewall, [mailcatcher](http://mailcatcher.me) is here to help :)

Mailcatcher is a very nice tool that, as the doc says, «Catches mail and serves it through a dream». In other worlds, it simply displays emails that your server try to send in a very nice UI.

## Installation

The installation as it's written on the website didn't work on my laptop, so I had to install more stuff that what was asked. Thanks to [samsam](https://github.com/samyranavela), I made it work by running :

{% highlight bash linenos %}
sudo apt-get install ruby rubygems ruby-dev sqlite3 libsqlite3-dev
sudo gem install mailcatcher
{% endhighlight %}

## Configuration

After that, I put as the documentation said in my php.ini

{% highlight bash linenos %}
sendmail_path = /usr/bin/env catchmail
{% endhighlight %}

But it didn't work. At the end, I found that

{% highlight bash linenos %}
sendmail_path = "/usr/bin/env /usr/local/bin/catchmail"
{% endhighlight %}

solved the problem :)

Then, a simple ```mailcatcher``` make it works… but localy only. If you use like me a VM to dev in order to not mess up your local OS, this won't work as the web interface only accept connection from 127.0.0.1 as default. The website doesn't help (at least I didn't find anything usefull for that), but a simple ```mailcatcher --help``` display the solution:

{% highlight bash linenos %}
mailcatcher --help
Usage: mailcatcher [options]
        --ip IP                      Set the ip address of both servers
        --smtp-ip IP                 Set the ip address of the smtp server
        --smtp-port PORT             Set the port of the smtp server
        --http-ip IP                 Set the ip address of the http server
        --http-port PORT             Set the port address of the http server
    -f, --foreground                 Run in the foreground
    -v, --verbose                    Be more verbose
    -h, --help                       Display this help information
{% endhighlight %}

After reading this, a simple:

{% highlight bash linenos %}
mailcatcher --http-ip <YourIpAddress>
{% endhighlight %}

will fix your issue :). Don't do --ip as the server still needs to listen the localhost for sent emails.

Again, thanks to the Mailcatcher team as it's a great product! And hope that it will help some of you :).
