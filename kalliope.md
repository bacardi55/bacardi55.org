---
layout: page
title: Kalliopé
permalink: /kalliope.html
---

This page regroups information about [kalliope project](http://github.com/kalliope-project/kalliope).

### General information

- [Kalliope website](https://kalliope-project.github.io/)
- [Kalliope github](http://github.com/kalliope-project/kalliope)
- [Kalliope gitter chat](https://gitter.im/kalliope-project/Lobby)


### See Kalliopé in action

*Videos are in French but I'll add subtitles to them shortly, maybe I'll do an English version later on…*

- [Uber neuron](https://www.youtube.com/watch?v=pnb1knix004) (*with english subtile*)
- [Gmaps neuron](https://www.youtube.com/watch?v=l8pi3Puzliw) (*with english subtile*)
- [TodoTxt neuron](https://www.youtube.com/watch?v=DLmaspBVd2A) (*with english subtile*)
- [MPD / Mopidy neuron](https://www.youtube.com/watch?v=Zdn7CUQlV1E) (*with english subtile*)
- [repeat](https://www.youtube.com/watch?v=lNfpX0MYfFI&list=PLDc8cUmeFkpKdErR5iYTkGJ1-4A05zHIi&index=4) (*with english subtile*)
- [google calendar](https://www.youtube.com/watch?v=4Xp2cJH2p2s&list=PLDc8cUmeFkpKdErR5iYTkGJ1-4A05zHIi&index=1) (*with english subtile*)
- [web scraper](https://www.youtube.com/watch?v=PxjtLvpvEFY&list=PLDc8cUmeFkpKdErR5iYTkGJ1-4A05zHIi&index=3) (*with english subtile*)

TODO video
- reminder
- wwtime
- domoticz integration
- …


### My neurons for Kalliopé

<ul>
{% for neuron in site.data.my_kalliope.neurons %}
    <li>
        <span><a href="{{ neuron.url }}">{{ neuron.name }}</a>: {{ neuron.description }}</span><br />
        <span> status: {{neuron.status}}</span>
    </li>
{% endfor %}
</ul>

### My scripts for Kalliopé
<ul>
{% for script in site.data.my_kalliope.scripts %}
    <li>
        <span><a href="{{ script.url }}">{{ script.name }}</a>: {{ script.description }}</span>
    </li>
{% endfor %}
</ul>

### Blog posts about Kalliopé

<!-- This loops through the paginated posts -->
<ul>
{% for post in site.posts %}
  <li>
    {{ post.date | date: "%b %-d, %Y" }} 
    <a href="{{ post.url | relative_url }}">{{ post.title | escape }}</a>
  </li>
{% endfor %}
</ul>


