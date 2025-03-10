---
layout: post
title: "Ρευστά Μαθηματικά Γ' Λυκείου"
description: "Φυσική Κατεύθυνσης Θέμα Γ"
category: Άσκηση
tags: [Ρευστά]
---
{% include JB/setup %}

Έστω $$y = y(t)$$ το ύψος και $$V = V(t)$$ ο όγκος του νερού μιας δεξαμενής τη χρονική στιγμή $$t$$. Η δεξαμενή αδειάζει από μια κυκλική οπή εμβαδού $$α$$ που βρίσκεται στον πυθμένα της. Σύμφωνα με το νόμο του Torricelli ο ρυθμός μεταβολής του όγκου του νερού είναι

$$\frac{dV}{dt} = - α\cdot \sqrt{2 \cdot g \cdot y}$$

όπου $$g = 10 \frac{m}{s^2}$$ και $$α$$ το εμβαδόν διατομής της οπής.


**i)** Αν η δεξαμενή είναι κυλινδρική με ύψος $$36m$$, ακτίνα $$1m$$ και η ακτίνα της οπής είναι $$0.1m$$, να αποδείξετε ότι το $$y$$ ικανοποιεί την εξίσωση

$$y' = - \frac{\sqrt{5}}{50} \cdot y$$

**ii)** Να βρείτε το ύψος $$y(t)$$, αν είναι γνωστό ότι τη χρονική στιγμή $$t = 0$$ η δεξαμενή ήταν γεμάτη.


**iii)** Πόσος χρόνος θα χρειαστεί για να αδειάσει τελείως η δεξαμενή; 
Δίνεται ότι ο όγκος του κυλίνδρου είναι $$V = π\cdot R^2\cdot h$$, όπου $$h$$ το ύψος του κυλίνδρου.

![σχήμα]({{ site.url }}/assets/math.jpg) 


`Απάντηση:`

**i)** Ο όγκος του νερού της δεξαμενής τη χρονική στιγμή $$t$$ είναι

$$V(t) = π \cdot R^2 \cdot y(t) = π \cdot y(t)$$

όπου $$R = 1m$$ η ακτίνα του κυλίνδρου, οπότε

$$V′(t) = π \cdot y′(t)$$

O νόμος του Torricelli γράφεται

$$π \cdot y′ = − 0.02 \cdot π \cdot 5 \cdot y ,$$

όπου υπολογίσαμε πρώτα το εμβαδόν διατομής της οπής

$$α = π \cdot r^2 \Rightarrow α = 0.01 \cdot π$$

Άρα από τον νόμο του Torricelli έχουμε:

$$y' = -\frac{\sqrt5}{50}\cdot \sqrt{y}$$


**ii)** Προφανώς το $$y = 0$$ αποτελεί λύση της παραπάνω εξίσωσης. Για $$y > 0$$ η εξίσωση γράφεται

$$\frac{dy}{\sqrt{y}} = -\frac{\sqrt5}{50}\cdot dt$$

και λύνοντας την διαφορική εξίσωση έχουμε 

$$ \int y^{-\frac{1}{2}} dy = \frac{-\sqrt{5}}{50} \cdot t +c$$

και τελικά μετά τις πράξεις

$$y = (-\frac{\sqrt{5}}{100} \cdot t+\frac{c}{2})^2$$

Όμως ισχύει $$y_o = 36m$$ άρα $$c=12$$. Άρα τη τελική συνάρτηση έχει την μορφή

$$y = (-\frac{\sqrt{5}}{100} \cdot t+6)^2$$


**iii)** H δεξαμενή αδειάζει τελείως, όταν $$y(t) = 0$$. Έτσι έχουμε:

$$y(t) = 0 \Rightarrow -\frac{\sqrt{5}}{100} \cdot t+6 = 0 \Rightarrow t = 120 \cdot \sqrt5s$$

<script type='text/javascript' src='https://demonstrations.wolfram.com/javascript/embed.js' ></script><script type='text/javascript'>var demoObj = new DEMOEMBED(); demoObj.run('FlowOfFluidThroughAHoleInATank', '', '545', '445');</script><div id='DEMO_FlowOfFluidThroughAHoleInATank'><a class='demonstrationHyperlink' href='https://demonstrations.wolfram.com/FlowOfFluidThroughAHoleInATank/' target='_blank'>Flow of Fluid through a Hole in a Tank</a> from the <a class='demonstrationHyperlink' href='https://demonstrations.wolfram.com/' target='_blank'>Wolfram Demonstrations Project</a> by Rana Gordji</div><br />