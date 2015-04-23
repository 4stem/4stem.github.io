---
layout: page
title: Περί Φυσικής κυρίως!
tagline: S.T.E.M
---
{% include JB/setup %}

Bio [Petridis](http://about.me/petridis)

## Science 

Στην κατηγορία `Φυσική` μπορείτε να βρείτε ασκήσεις που αφορούν μαθητές Λυκείου και πρωτοετείς φοιτητές.
    
## Technology, Engineering

Στην κατηγορία `Τεχνολογία` μπορείτε να βρείτε πληροφορίες σχετικά με τον μικροελεγκτή **[Arduino](http://arduino.org)**, το miniPC **[Raspberry Pi](https://www.raspberrypi.org/)** και το τηλεκατευθυνόμενο όχημα **[Hydrobot](http://hydrobots.gr/index/)**


## Mathematics

Στην κατηγορία `Μαθηματικά` μπορείτε να βρείτε πληροφορίες σχετικά με την γλώσσα προγραμματισμού **Wolfram Alpha**, και παραδείγματα χρήσης του λογισμικού **Geogebra**

Ακολουθεί μια απλή λίστα άρθρων.

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>






