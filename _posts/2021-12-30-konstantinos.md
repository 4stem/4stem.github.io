---
layout: post
title: "Ταλαντώσεις και γραφικές παραστάσεις"
description: "Mathematica"
category: Άσκηση
tags: [Mathematica]
---
{% include JB/setup %}


Προσομοιώσεις στο παρακάτω [λινκ](https://www.wolframcloud.com/)


Απλή Αρμονική Ταλάντωση

$$ Σ \vec F = m \cdot \vec a \Rightarrow -D \cdot x = m \cdot \frac{d^2x}{dt^2} $$

$$ \frac{d^2x}{dt^2} + ω_ο^2 \cdot x = 0$$


		DSolve[{x''[t] + ωο^2*x[t] == 0, x'[0] == 0, x[0]==A},x[t], t];
		Manipulate[Plot[x[t] /. %, {t, 0, 2π}, PlotLabel -> "απλή αρμονική ταλάντωση", Background -> LightBlue, GridLines -> Automatic, AxesLabel -> {"t(s)", "x(m)"}, Filling -> Automatic], {ωο, 1, 10}, {A, 1, 10}]



Φθίνουσα Ταλάντωση

$$Σ \vec F = m \cdot \vec α \Rightarrow -D \cdot x - b \cdot υ = m \cdot \frac{d^2x}{dt^2} $$


$$\frac{d^2x}{dt^2} + \frac{b}{m} \cdot \frac{dx}{dt} + \frac{D}{m} \cdot x = 0$$


$$\frac{d^2x}{dt^2} + 2 \cdot Λ \cdot \frac{dx}{dt} + ω_ο^2 \cdot x = 0$$


		DSolve[{x''[t] + 2*Λ* x'[t] + ωο^2*x[t] == 0, x[0] == 5, x'[0] == 0}, x[t], t];
		Manipulate[Plot[x[t] /. %, {t, 0, 2π}, PlotLabel -> "φθίνουσα ταλάντωση", Background -> LightBlue, GridLines -> Automatic, AxesLabel -> {"t(s)", "x(m)"}, Filling -> Automatic, PlotRange -> All], {ωο, 0.1, 100}, {Λ, 1, 10}]


Εξαναγκασμένη Ταλάντωση


$$A = \frac{\frac{F_o}{m}}{\sqrt{(ω_ο^2-ω_δ^2)^2+(b \cdot ω_δ)^2}}$$


		Manipulate[Plot[0.5/Sqrt[((25 -  ωδ^2)^2 +b^2* ωδ^2)], {ωδ, 0, 20}, PlotLabel -> "εξαναγκασμένη ταλάντωση", Background -> LightBlue, GridLines -> Automatic, AxesLabel -> {"ωδ(r/s)", "A(m)"}, Filling -> Automatic, PlotRange -> All ], {b, 0, 5}]



		Rasterize@Graphics[{Riffle[Table[Text[Style[Pi,FontFamily->"Source Serif Pro",20s]],{s,34,3,-1}],{White,Black}]}]


		Sound[SoundNote[2#,1,"Cello"]&/@First[RealDigits[Pi,10,50]],15]


		pi = Characters[ToString@N[Pi, 3000000]];
		tel = Characters[ToString@123456];
		pos = SequencePosition[pi, tel]


		a=0; digits=First[RealDigits[Pi,10,100]]; 
		Graphics@Table[r=.1+.03 a;\[IndentingNewLine]a=a+(80000/ r)^.32;\[IndentingNewLine]g=Rotate[Style[Text[Reverse[digits][[n]],{0,r^1.5},{0,0}],(353 (.1+r)^1.25)/100^1.5], a Degree,{0,0}],{n,0,Length[digits]}]


Ερωτήσεις και απαντήσεις στο παρακάτω [λινκ](https://www.wolframalpha.com/)

= Hello

= What is your name?

= Where are you?

= How old are you?

= What do you not like?

= Where am I?

= edge detect image of pythagoras

= Dude, where's my car?
