---
layout: post
category : Άρθρο
title: Φυσικές Επιστήμες στην εκπαίδευση, τεύχος 2ο.
tagline: "Στάσιμα κύματα: μία ολιστική αντιμετώπιση"
tags : [Φυσική, Python]
---
{% include JB/setup %}


Στο δεύτερο τεύχος του ηλεκτρονικού περιοδικού [Φυσικές Επιστήμες στην εκπαίδευση](https://physcool.web.auth.gr/index.php?start=12) μπορεί να βρεθεί η εργασία με τίτλο ***Στάσιμα κύματα: μία ολιστική αντιμετώπιση***. Η συγκεκριμένη πρόταση διδασκαλίας απευθύνεται σε εκπαιδευτικούς της δευτεροβάθμιας εκπαίδευσης, ενώ συνοδεύεται από Φύλλο εργασίας και ενδεικτικά στιγμιότυπα. Μπορείτε να την κατεβάσετε από [εδώ](https://drive.google.com/open?id=0B2PMgebiPbrIck44aXNtOWZqZWM)


Ακολουθεί ο κώδικας σε python που χρησιμοποιήθηκε από την ομάδα "Allan Matheson Turing".


{% highlight python %}

        import numpy as np
        import matplotlib.pyplot as plt
        def f(x):
            return 0.3*np.sin(2*np.pi*(t/T-x/lamda))
        def g(x):
            return 0.6*np.sin(2*np.pi*(L-x)/lamda)*np.cos(2*np.pi*(t/T-L/lamda))
        font = {'family' : 'serif',
                'color'  : 'darkred',
                'weight' : 'normal',
                'size'   : 16,        }
        x1 = np.arange(0.0, 1.0, 0.01)
        x2 = np.arange(1.0, 1.5, 0.01)
        x3 = np.arange(0.0, 0.5, 0.01)
        x4 = np.arange(0.0, 1.5, 0.01)
        x5 = np.arange(0.5, 1.5, 0.01)
        T = 1       #T is for wave period
        lamda = 1   #lamda is for wavelength
        L = 1.5     #L is for thread length
        t = input('choose a time moment that you prefer as multiple of 0.5 only  ')
        plt.xlim(0.0, 1.5)
        plt.ylim(-0.6, 0.6)
        plt.xlabel('x (m)', fontdict=font)
        plt.ylabel('y (m)', fontdict=font)
        plt.grid(True)
        plt.title('Snapshot when the time is % s second' % t, fontdict=font)
        if t%0.5 == 0:

            if t == 0:
                plt.plot(x4, (0*x4), 'ko')
            elif t==0.5:
                plt.plot(x3, f(x3), 'bo', x5, (0*x5), 'ko')
            elif t==1:
                plt.plot(x1, f(x1), 'bo', x2, (0*x2), 'ko')
            elif t==1.5:
                plt.plot(x4, f(x4), 'bo')
            elif t==2:
                plt.plot(x1, f(x1), 'bo', x2, g(x2), 'ro')
            elif t==2.5:
                plt.plot(x3, f(x3), 'bo', x5, g(x5), 'ro')
            else:
                plt.plot(x4, g(x4), 'ro')
            plt.show()
        else: print ('choose only a time moment as multiple of 0.5 ')

{% endhighlight %}

και $$\href{https://youtu.be/JElXnImGCZU}{εδώ}$$ το βίντεο της ομάδας "CERN"



<script type='text/javascript' src='https://demonstrations.wolfram.com/javascript/embed.js' ></script><script type='text/javascript'>var demoObj = new DEMOEMBED(); demoObj.run('StandingWavesAndChords', '', '357', '545');</script><div id='DEMO_StandingWavesAndChords'><a class='demonstrationHyperlink' href='https://demonstrations.wolfram.com/StandingWavesAndChords/' target='_blank'>Standing Waves and Chords</a> from the <a class='demonstrationHyperlink' href='https://demonstrations.wolfram.com/' target='_blank'>Wolfram Demonstrations Project</a> by Hans-Joachim Domke</div><br />





