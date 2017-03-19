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


### See Kalliopé in action

Coming soon
