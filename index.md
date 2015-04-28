---
layout: page
title: S.T.E.M
tagline: Science Technology Engineering Mathematics
---
{% include JB/setup %}

Bio [Petridis](http://about.me/petridis)

“I hope that in this year to come, you make mistakes.
Because if you are making mistakes, then you are making new things, trying new things, learning, living, pushing yourself, changing yourself, changing your world. You're doing things you've never done before, and more importantly, you're Doing Something.
So that's my wish for you, and all of us, and my wish for myself. Make New Mistakes. Make glorious, amazing mistakes. Make mistakes nobody's ever made before. Don't freeze, don't stop, don't worry that it isn't good enough, or it isn't perfect, whatever it is: art, or love, or work or family or life.
Whatever it is you're scared of doing, Do it.
Make your mistakes, next year and forever.” 
`― Neil Gaiman`

Ακολουθεί μια απλή λίστα άρθρων.

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>






