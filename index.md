---
layout: page
title: S.T.E.M
tagline: Science Technology Engineering Mathematics
---
{% include JB/setup %}

For a better look at the mathematical formulas, right clik as shown

![σχήμα]({{ site.url }}/assets/intro.png) 


**Introduction**

“I hope that in this year to come, you make mistakes.
Because if you are making mistakes, then you are making new things, trying new things, learning, living, pushing yourself, changing yourself, changing your world. You're doing things you've never done before, and more importantly, you're Doing Something.
So that's my wish for you, and all of us, and my wish for myself. Make New Mistakes. Make glorious, amazing mistakes. Make mistakes nobody's ever made before. Don't freeze, don't stop, don't worry that it isn't good enough, or it isn't perfect, whatever it is: art, or love, or work or family or life.
Whatever it is you're scared of doing, Do it.
Make your mistakes, next year and forever.” 
`― Neil Gaiman`

<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1">
<style>
body {
  font-family: Arial, Helvetica, sans-serif;
}

.flip-card {
  background-color: transparent;
  width: 300px;
  height: 300px;
  perspective: 1000px;
}

.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.6s;
  transform-style: preserve-3d;
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
}

.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
}

.flip-card-front, .flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
}

.flip-card-front {
  background-color: #bbb;
  color: black;
}

.flip-card-back {
  background-color: #2980b9;
  color: white;
  transform: rotateY(180deg);
}
</style>
</head>
<body>

<h1>Splendide mendax</h1>

<div class="flip-card">
  <div class="flip-card-inner">
    <div class="flip-card-front">
      <h2>a physics teacher said</h2> 
      <p>there are no mistakes only lessons <br> growth is a process of trial and error</p> 
      <h2>Eduardo Galeano said </h2>
      <p>After all, we are what we do <br> to change what we are.</p>
    </div>
    <div class="flip-card-back">
     <img src="me.png" alt="Avatar" style="width:300px;height:300px;">
    </div>
  </div>
</div>

</body>
</html>

 <h3> here is a list of posts <br> chronologically sorted  </h3>
 
 <p></p>

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>






