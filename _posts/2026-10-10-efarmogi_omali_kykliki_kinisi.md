---
layout: post
category : Εφαρμογή
title: "Ομαλή κυκλική κίνηση"
tagline: "Οπτικοποίηση της ομαλής κυκλικής κίνησης ενός υλικού σημείου"
tags : [Φυσική]
---
{% include JB/setup %}

Μια εφαρμογή για τη διερεύνηση της ομαλής κυκλικής κίνησης ενός υλικού σημείου. Ο μαθητής χωρίζει την κίνηση σε **τέσσερα διαδοχικά χρονικά διαστήματα** αλλάζοντας το διάγραμμα φ–t και, στη συνέχεια, παρακολουθεί την κίνηση του υλικού σημείου πάνω στον κύκλο, βλέποντας συγχρόνως να σχηματίζεται και το διάγραμμα ω–t.

---

## Οδηγίες χρήσης

1. **Σχεδίασε την κίνηση.** Σύρε τα πέντε μπλε σημεία του διαγράμματος φ–t. Το πρώτο, πάνω στον άξονα φ, ορίζει την αρχική γωνία φ₀. Καθένα από τα άλλα τέσσερα ορίζει πού τελειώνει ένα τμήμα της κίνησης (χρόνος και γωνία). Η γωνία φ παίρνει τιμές από −2π έως 2π, με βήμα π/12, και ο χρόνος ακέραια δευτερόλεπτα. Κάθε τμήμα έχει δικό του χρώμα και αριθμό.
2. **Τοποθέτησε το υλικό σημείο.** Μπορείς να σύρεις και το ίδιο το υλικό σημείο πάνω στον κύκλο. Ορίζεις έτσι την αρχική γωνία φ₀ και το πρώτο μπλε σημείο ακολουθεί.
3. **Δες την κίνηση.** Πάτησε ▶ για να κινηθεί το υλικό σημείο, ⏸ για παύση ή σύρε το ρυθμιστικό του χρόνου. Η ταχύτητα της προσομοίωσης αλλάζει από το αντίστοιχο μενού και με το τετραγωνάκι «Επανάληψη» η κίνηση ξαναρχίζει αυτόματα.
4. **Βήμα βήμα.** Με τα κουμπιά **1 s ▶** και **◀ 1 s** ο χρόνος προχωράει ή γυρίζει πίσω ανά ένα δευτερόλεπτο, ώστε να εξηγείς την κίνηση σταδιακά.
5. **Διάγραμμα ω–t.** Τσέκαρε το «Εμφάνιση διαγράμματος ω–t» και το διάγραμμα εμφανίζεται ακριβώς κάτω από το πρώτο, με τον ίδιο άξονα χρόνου, και και σχηματίζεται καθώς περνά ο χρόνος.
6. **Επαναφορά.** Το κουμπί ⏮ γυρίζει τον χρόνο στο t = 0 και κρατά το διάγραμμα που έφτιαξες. Το κουμπί ↻ (επανεκκίνηση) επαναφέρει ολόκληρη την εφαρμογή στην αρχική της κατάσταση.
7. **Πλήρης οθόνη.** Το κουμπί **⛶ Πλήρης οθόνη** (πάνω δεξιά στη γραμμή κουμπιών) μεγεθύνει την εφαρμογή σε όλη την οθόνη, ιδανικά για διαδραστικό πίνακα. Τα κουμπιά και τα γράμματα μεγαλώνουν, ενώ η έξοδος γίνεται με το ίδιο κουμπί ή με το πλήκτρο Esc.

## Τι να παρατηρήσεις

- Η **κλίση** κάθε τμήματος στο διάγραμμα φ–t είναι η γωνιακή ταχύτητα: ω = Δφ/Δt.
- Οριζόντιο τμήμα στο φ–t σημαίνει ω = 0: το υλικό σημείο μένει ακίνητο πάνω στον κύκλο.
- Για **ω > 0** το υλικό σημείο κινείται αντίθετα από τους δείκτες του ρολογιού και στο κέντρο του κύκλου φαίνεται το διάνυσμα της ω ως κύκλος με τελεία. Για **ω < 0** κινείται όπως οι δείκτες του ρολογιού και το διάνυσμα φαίνεται ως κύκλος με ×.
- Το διάγραμμα ω–t είναι σταθερό σε κάθε τμήμα, γιατί η κίνηση σε κάθε διάστημα είναι ομαλή κυκλική. Το εμβαδόν κάτω από αυτό ισούται με τη μεταβολή της γωνίας Δφ.

## Χαρακτηριστικά

- ✅ Διάγραμμα φ–t με πέντε μπλε σημεία που σύρονται, δηλαδή τέσσερα τμήματα με δικό τους χρώμα
- ✅ Γωνία από −2π έως 2π με βήμα π/12 (π/6, π/4, π/3, π/2, π, 3π/2, 2π και οι αρνητικές τους)
- ✅ Σύρσιμο του υλικού σημείου πάνω στον κύκλο
- ✅ Διάνυσμα της γωνιακής ταχύτητας στο κέντρο του κύκλου (κύκλος με τελεία ή με ×)
- ✅ Βήμα μπροστά/πίσω ανά 1 s, παύση, ρυθμιζόμενη ταχύτητα και επανάληψη
- ✅ Προαιρετικό διάγραμμα ω–t που σχηματίζεται σταδιακά
- ✅ Επανεκκίνηση στην αρχική κατάσταση
- ✅ Πλήρης οθόνη για διαδραστικό πίνακα, με μεγαλύτερα κουμπιά και γράμματα, και υψηλή ανάλυση καμβά

---

<style>
#kyk-app *{box-sizing:border-box;margin:0;padding:0}
#kyk-app{
  width:min(96vw,1400px);margin:-20px 0 -20px calc(50% - min(96vw,1400px) / 2);display:flex;flex-direction:column;font-family:Arial,sans-serif;line-height:1.3;
  --bg:#070b14;--panel:#0f1525;--brd:#1a2840;--acc:#00c8ff;--gold:#ffd166;--grn:#06d6a0;--mag:#d55aff;--org:#ff6b35;--txt:#c8d8f0;--dim:#6a80a0;
  background:var(--bg);color:var(--txt);
}
#kyk-app header{background:#0a1020;border-bottom:1px solid var(--brd);padding:9px 16px;display:flex;align-items:center;gap:10px}
#kyk-app header h1{font-size:15px;font-weight:700;color:var(--acc);letter-spacing:1px;line-height:1.3;border:0}
#kyk-app header h1 span{color:var(--dim);font-weight:400;font-size:10px;display:block;letter-spacing:1px}
#kyk-app .k-bar{background:var(--panel);border-bottom:1px solid var(--brd);padding:9px 13px;display:flex;flex-wrap:wrap;align-items:center;gap:8px;font-size:12px}
#kyk-app .k-grp{display:inline-flex;align-items:center;gap:6px}
#kyk-app .k-sep{width:1px;height:24px;background:var(--brd);margin:0 2px}
#kyk-app .k-btn{min-width:34px;height:34px;border:1px solid var(--brd);border-radius:4px;background:var(--bg);color:var(--txt);display:inline-flex;align-items:center;justify-content:center;cursor:pointer;font:bold 16px Arial,sans-serif;line-height:1;box-shadow:none;text-shadow:none;background-image:none;padding:0}
#kyk-app .k-btn.k-wide{padding:0 10px;font-size:12px;letter-spacing:.3px;gap:5px}
#kyk-app .k-btn:hover{border-color:var(--acc)}
#kyk-app .k-btn:focus{outline:1px solid var(--acc);outline-offset:1px}
#kyk-app .k-btn.k-on{background:rgba(0,200,255,0.18);border-color:var(--acc);color:var(--acc)}
#kyk-app .k-btn svg{width:16px;height:16px;fill:currentColor;display:block}
#kyk-app .k-t{display:flex;align-items:center;gap:8px;margin-left:6px;font-family:monospace;font-size:12px;color:var(--acc)}
#kyk-app .k-tl{min-width:68px}
#kyk-app input[type=range]{width:210px;height:auto;accent-color:#00c8ff;background:transparent;border:0;box-shadow:none;padding:0;margin:0}
#kyk-app .k-opt{display:inline-flex;align-items:center;gap:6px;font-size:11px;color:var(--txt);cursor:pointer;margin:0 0 0 8px;font-weight:400;max-width:none}
#kyk-app .k-opt input[type=checkbox]{width:16px;height:16px;margin:0;accent-color:#00c8ff;cursor:pointer}
#kyk-app select{width:auto;height:auto;display:inline-block;background:var(--bg);border:1px solid var(--brd);color:var(--txt);border-radius:4px;padding:4px 6px;font-size:11px;font-family:inherit;line-height:1.2;box-shadow:none}
#kyk-app .k-help{display:none;background:rgba(0,200,255,0.05);border:1px solid rgba(0,200,255,0.18);border-width:0 0 1px 0;padding:9px 14px;font-size:11.5px;line-height:1.7;color:var(--txt)}
#kyk-app .k-help.k-open{display:block}
#kyk-app .k-help b{color:#fff}
#kyk-app .k-cvw{background:var(--panel);padding:0}
#kyk-app canvas{display:block;width:100%;max-width:none;height:auto;aspect-ratio:1280 / 712;touch-action:none;background:var(--panel)}
#kyk-app .k-ccb{font-size:9px;color:var(--dim);line-height:1.7;padding:8px 13px;text-align:center;border-top:1px solid var(--brd)}
#kyk-app .k-ccb a{color:var(--acc)}
#kyk-app .k-ccb strong{color:var(--txt)}
#kyk-app .k-fsb{margin-left:auto}
#kyk-app .k-btn.k-wide svg{flex:none}
#kyk-app.k-fs{position:fixed;left:0;top:0;right:0;bottom:0;width:100vw;height:100vh;max-width:none;margin:0;z-index:2147483000}
#kyk-app.k-fs header,#kyk-app.k-fs .k-ccb{display:none}
#kyk-app.k-fs .k-bar{position:absolute;left:0;right:0;bottom:0;z-index:6;background:rgba(10,16,32,.94);border:0;border-top:1px solid var(--brd);padding:6px 12px;gap:6px;font-size:14px;transition:opacity .25s,transform .25s}
#kyk-app.k-fs.k-idle .k-bar{opacity:0;transform:translateY(100%);pointer-events:none}
#kyk-app.k-fs .k-sep{display:none}
#kyk-app.k-fs .k-grp{gap:5px}
#kyk-app.k-fs .k-btn{min-width:44px;height:44px;border-radius:7px}
#kyk-app.k-fs .k-btn.k-wide{font-size:15px;padding:0 9px;gap:5px}
#kyk-app.k-fs .k-btn svg{width:21px;height:21px}
#kyk-app.k-fs .k-fsb{margin:0 8px 0 0;order:-1}
#kyk-app.k-fs .k-t{flex:1 1 160px;min-width:0;font-size:15px;gap:8px;margin-left:2px}
#kyk-app.k-fs .k-tl{min-width:86px}
#kyk-app.k-fs input[type=range]{flex:1 1 auto;width:auto;min-width:80px;height:32px}
#kyk-app.k-fs .k-opt{margin-left:0;white-space:nowrap;font-size:14px;gap:6px}
#kyk-app.k-fs .k-opt input[type=checkbox]{width:22px;height:22px}
#kyk-app.k-fs select{font-size:14px;padding:5px 6px}
#kyk-app.k-fs .k-help{position:absolute;left:0;right:0;bottom:64px;z-index:6;background:rgba(10,16,32,.96);font-size:16px;padding:12px 18px}
#kyk-app.k-fs.k-dock .k-bar{position:relative;order:5;transform:none!important;opacity:1!important;pointer-events:auto!important}
#kyk-app.k-fs .k-cvw{flex:1 1 0;min-width:0;min-height:0;display:flex;align-items:center;justify-content:center;overflow:hidden}
</style>

<div id="kyk-app">
<header><span style="font-size:20px">🔄</span>
<h1>Ομαλή κυκλική κίνηση<span>ΟΠΤΙΚΟΠΟΙΗΣΗ · ΔΙΑΓΡΑΜΜΑΤΑ φ–t ΚΑΙ ω–t</span></h1></header>
<div class="k-bar">
<div class="k-grp">
<button class="k-btn" id="kyk-play" title="Εκκίνηση" aria-label="Εκκίνηση"><svg viewBox="0 0 16 16"><path d="M3 1.5v13l11-6.5z"/></svg></button>
<button class="k-btn" id="kyk-pause" title="Παύση" aria-label="Παύση"><svg viewBox="0 0 16 16"><path d="M3 2h4v12H3zM9 2h4v12H9z"/></svg></button>
</div>
<div class="k-sep"></div>
<div class="k-grp">
<button class="k-btn k-wide" id="kyk-sback" title="Βήμα πίσω: ο χρόνος πηγαίνει 1 s πίσω" aria-label="Βήμα πίσω 1 δευτερόλεπτο"><svg viewBox="0 0 16 16"><path d="M13 1.5v13L3.5 8z"/></svg>1 s</button>
<button class="k-btn k-wide" id="kyk-sfwd" title="Βήμα μπροστά: ο χρόνος προχωράει 1 s" aria-label="Βήμα μπροστά 1 δευτερόλεπτο">1 s<svg viewBox="0 0 16 16"><path d="M3 1.5v13L12.5 8z"/></svg></button>
</div>
<div class="k-sep"></div>
<div class="k-grp">
<button class="k-btn" id="kyk-rew" title="Στην αρχή: ο χρόνος γίνεται t = 0" aria-label="Στην αρχή"><svg viewBox="0 0 16 16"><path d="M2 2h2.2v12H2zM14 1.5v13L5.5 8z"/></svg></button>
<button class="k-btn" id="kyk-reset" title="Επανεκκίνηση: επαναφορά της εφαρμογής στην αρχική κατάσταση" aria-label="Επανεκκίνηση"><svg viewBox="0 0 16 16"><path d="M8 2.5a5.5 5.5 0 1 0 5.2 7.3l-1.9-.6A3.5 3.5 0 1 1 8 4.5c.9 0 1.7.3 2.3.9L8.5 7.2H14V1.7l-1.9 1.9A5.5 5.5 0 0 0 8 2.5z"/></svg></button>
<button class="k-btn" id="kyk-helpb" title="Οδηγίες" aria-label="Οδηγίες">?</button>
</div>
<div class="k-t"><span class="k-tl" id="kyk-tl">t = 0 s</span><input id="kyk-tsl" type="range" min="0" max="1000" value="0" step="1" aria-label="Χρόνος t"></div>
<label class="k-opt">Ταχύτητα <select id="kyk-spd"><option value="0.5">0,5×</option><option value="1" selected>1×</option><option value="2">2×</option></select></label>
<label class="k-opt"><input type="checkbox" id="kyk-rep"> Επανάληψη</label>
<label class="k-opt"><input type="checkbox" id="kyk-showom"> Εμφάνιση διαγράμματος ω–t</label>
<button class="k-btn k-wide k-fsb" id="kyk-fs" title="Πλήρης οθόνη (Esc για έξοδο)" aria-label="Πλήρης οθόνη"><svg viewBox="0 0 16 16"><path id="kyk-fsi" d="M1 1h5v2H3v3H1zM10 1h5v5h-2V3h-3zM1 10h2v3h3v2H1zM13 10h2v5h-5v-2h3z"/></svg><span id="kyk-fst">Πλήρης οθόνη</span></button>
</div>
<div class="k-help" id="kyk-help">
<b>Σύρε τα πέντε μπλε σημεία</b> του διαγράμματος φ–t για να χωρίσεις την κίνηση σε τέσσερα τμήματα:<br>
• το σημείο πάνω στον άξονα φ ορίζει την αρχική γωνία φ₀ ·<br>
• καθένα από τα άλλα τέσσερα ορίζει πού τελειώνει ένα τμήμα (χρόνος και γωνία) · κάθε τμήμα έχει δικό του χρώμα και αριθμό.<br>
Μπορείς να σύρεις και το υλικό σημείο πάνω στον κύκλο: ορίζεις έτσι την αρχική γωνία φ₀.<br>
Η γωνία φ παίρνει τιμές από −2π έως 2π (με βήμα π/12) και ο χρόνος ακέραια δευτερόλεπτα. Στο κέντρο του κύκλου το διάνυσμα της γωνιακής ταχύτητας φαίνεται ως κύκλος με τελεία (ω &gt; 0) ή κύκλος με × (ω &lt; 0).<br>
<b>▶</b> εκκίνηση · <b>⏸</b> παύση · <b>1 s ▶</b> / <b>◀ 1 s</b> βήμα μπροστά / πίσω ανά δευτερόλεπτο · <b>⏮</b> στην αρχή (t = 0) · <b>↻</b> επανεκκίνηση: επαναφέρει την εφαρμογή στην αρχική κατάσταση.<br><b>⛶</b> πλήρης οθόνη για τον διαδραστικό πίνακα (έξοδος με το ίδιο κουμπί ή με Esc).
</div>
<div class="k-cvw"><canvas id="kyk-cv" width="1280" height="712" aria-label="Διάγραμμα φ–t, κίνηση του υλικού σημείου σε κύκλο και προαιρετικά διάγραμμα ω–t"></canvas></div>
<div class="k-ccb">Δημιουργία – Ανάπτυξη: <strong>Παναγιώτης Πετρίδης</strong><br>Η προσομοίωση αναπτύχθηκε με τη βοήθεια του Claude (Anthropic)</div>
</div>

<script>
(function () {
  'use strict';
  // ---------- Σταθερές και κατάσταση ----------
  var PI = Math.PI;
  var W = 1280;
  var H_TOP = 712, H_FULL = 830;       // ύψος χωρίς / με το διάγραμμα ω–t
  var H = H_TOP;
  var TMAX = 12;                       // μέγιστος χρόνος του άξονα t (s)
  var KMAX = 24;                       // φ από −2π έως 2π, σε μονάδες π/12
  var NSEG = 4;                        // πλήθος τμημάτων (άρα 5 σημεία)
  // Τέσσερα εύκολα διακρινόμενα χρώματα (κόκκινο, κίτρινο, πράσινο, μωβ)
  var COL = ['#ff5a5f', '#ffd166', '#2fd69a', '#d55aff'];
  var SUB = ['₁', '₂', '₃', '₄'];
  var P = {   // παλέτα (σκούρο θέμα)
    bg: '#0f1525', halo: 'rgba(15,21,37,.92)', txt: '#c8d8f0', dim: '#9fb3d1', strong: '#eaf2ff',
    axis: '#c8d8f0', gridV: '#1a2840', gridH0: '#2c4166', gridH1: '#1f3050', gridH2: '#172640',
    shade: 'rgba(255,255,255,0.045)', guide: '#6a80a0', cursor: '#8fa5c7', sep: '#1a2840',
    blue: '#2f80ff', blueLab: '#9cc2ff', blueTxt: '#6aa7ff', blueFill: 'rgba(47,128,255,.20)',
    ring: '#c8d8f0', ringFaint: '#1f3050', radius: '#e6efff', jump: '#7d93b5'
  };
  // Η αρχική κατάσταση. t[i] = χρόνος και k[i] = γωνία (σε μονάδες π/12) του σημείου i.
  // Το σημείο 0 βρίσκεται πάντα στον άξονα φ (t = 0).
  function defaults() { return { t: [0, 3, 6, 9, 12], k: [0, 12, 12, 6, -6] }; }
  var S = defaults();
  var tcur = 0, playing = false, repeat = false, speed = 1, showOm = false;
  var dragging = -1, hover = -1, dirty = true, lastTs = 0;
  var PHI = { x: 100, y: 62, w: 520, h: 480 };    // διάγραμμα φ–t
  var OM  = { x: 100, y: 640, w: 520, h: 150 };  // διάγραμμα ω–t (κάτω, προαιρετικό)
  var CC  = { x: 960, y: 350, R: 200 };           // κύκλος
  function T() { return S.t[NSEG]; }
  // ---------- Βοηθητικά ----------
  function clamp(v, a, b) { return Math.max(a, Math.min(b, v)); }
  function gcd(a, b) { a = Math.abs(a); b = Math.abs(b); while (b) { var r = a % b; a = b; b = r; } return a; }
  // (n/d)·π ως κείμενο, π.χ. 3π/2, π/6, −π/4
  function fracPi(n, d) {
    if (n === 0) return '0';
    var g = gcd(n, d); n /= g; d /= g;
    var a = Math.abs(n);
    return (n < 0 ? '−' : '') + (a === 1 ? 'π' : a + 'π') + (d === 1 ? '' : '/' + d);
  }
  function num(x, dec) {
    dec = dec === undefined ? 2 : dec;
    var s = (Math.round(x * Math.pow(10, dec)) / Math.pow(10, dec)).toFixed(dec);
    if (parseFloat(s) === 0) s = (0).toFixed(dec);
    return s.replace('.', ',').replace('-', '−');
  }
  function segments() {
    var a = [];
    for (var i = 0; i < NSEG; i++) {
      var s = { ta: S.t[i], tb: S.t[i + 1], ka: S.k[i], kb: S.k[i + 1] };
      s.num = s.kb - s.ka;            // ω = num/den · π
      s.den = 12 * (s.tb - s.ta);
      s.w = s.num / s.den * PI;
      a.push(s);
    }
    return a;
  }
  function segIndex(sg, t) {
    for (var i = 0; i < NSEG - 1; i++) if (t < sg[i].tb) return i;
    return NSEG - 1;
  }
  function kAt(sg, t) {
    var s = sg[segIndex(sg, t)];
    return s.ka + (s.kb - s.ka) * (clamp(t, s.ta, s.tb) - s.ta) / (s.tb - s.ta);
  }
  // ---------- Συντεταγμένες ----------
  function tx(t)  { return PHI.x + PHI.w * t / TMAX; }
  function txO(t) { return OM.x + OM.w * t / TMAX; }
  function ky(k)  { return PHI.y + PHI.h * (KMAX - k) / (2 * KMAX); }
  // Λαβές: 0..4 τα μπλε σημεία του φ–t, 5 το υλικό σημείο στον κύκλο
  function handles() {
    var hs = [], i, sg = segments();
    for (i = 0; i <= NSEG; i++) hs.push({ x: tx(S.t[i]), y: ky(S.k[i]), r: 26 });
    var a = kAt(sg, tcur) * PI / 12;
    hs.push({ x: CC.x + CC.R * Math.cos(a), y: CC.y - CC.R * Math.sin(a), r: 30 });
    return hs;
  }
  function applyDrag(i, p) {
    var j;
    if (i === NSEG + 1) {
      // Υλικό σημείο στον κύκλο: ορίζει την αρχική γωνία φ₀ (ίδια θέση, ισοδύναμο φ ± 2π)
      var ang = Math.atan2(-(p.y - CC.y), p.x - CC.x);
      var kr = Math.round(ang / (PI / 12)), best = null, ref = S.k[0];
      [kr - 24, kr, kr + 24].forEach(function (c) {
        if (c >= -KMAX && c <= KMAX && (best === null || Math.abs(c - ref) < Math.abs(best - ref))) best = c;
      });
      if (best !== null) S.k[0] = best;
    } else {
      var t = Math.round((p.x - PHI.x) / PHI.w * TMAX);
      var k = clamp(Math.round(KMAX - (p.y - PHI.y) / PHI.h * 2 * KMAX), -KMAX, KMAX);
      S.k[i] = k;
      if (i > 0) {
        S.t[i] = clamp(t, i, TMAX - (NSEG - i));
        for (j = i + 1; j <= NSEG; j++) S.t[j] = Math.max(S.t[j], S.t[j - 1] + 1);
        for (j = i - 1; j >= 1; j--) S.t[j] = Math.min(S.t[j], S.t[j + 1] - 1);
      }
    }
    dirty = true;
  }
  // ---------- Καμβάς ----------
  var cv = document.getElementById('kyk-cv');
  var ctx = cv.getContext('2d');
  var wrapEl = cv.parentNode, fsOn = false;
  var FS = 1.25;                        // κλίμακα γραμματοσειρών (πίνακας / μακρινή θέαση)
  function sf(f) { return f.replace(/(\d+(?:\.\d+)?)px/, function (m, n) { return (n * FS).toFixed(1) + 'px'; }); }
  var W0 = 1280, INFX = 700;
  function layout(w) {                  // προσαρμογή της διάταξης στο πλάτος W (πλήρης οθόνη: πλάτος ανάλογο της οθόνης)
    var dx = w - W0, h = Math.round(dx / 2);
    W = w; PHI.w = 520 + h; CC.x = 960 + h; OM.w = PHI.w; INFX = 700 + h;
  }
  function fit() {
    var aw = wrapEl.clientWidth, ah = wrapEl.clientHeight;
    if (fsOn && aw > 0 && ah > 0) {
      layout(clamp(Math.round(H * aw / ah), W0, 2560));
      var w = Math.min(aw, ah * W / H);
      cv.style.width = Math.floor(w) + 'px'; cv.style.height = Math.floor(w * H / W) + 'px';
    } else { layout(W0); cv.style.width = ''; cv.style.height = ''; }
    cv.style.aspectRatio = W + ' / ' + H;
  }
  function resize() {
    fit();
    var r = cv.getBoundingClientRect();
    var sc = Math.max(window.devicePixelRatio || 1, 2);          // υπερδειγματοληψία: τουλάχιστον 2×
    var bw = Math.min(4096, Math.max(Math.round(r.width * sc), 1920));
    var bh = Math.round(bw * H / W);
    if (cv.width !== bw || cv.height !== bh) { cv.width = bw; cv.height = bh; }
    ctx.setTransform(bw / W, 0, 0, bh / H, 0, 0);
    dirty = true;
  }
  function setHeight(h) {
    H = h;
    cv.style.aspectRatio = W + ' / ' + H;
    resize();
  }
  if (window.ResizeObserver) { var ro = new ResizeObserver(resize); ro.observe(cv); ro.observe(wrapEl); }
  window.addEventListener('resize', resize);
  function line(x1, y1, x2, y2, color, lw, dash) {
    ctx.beginPath(); ctx.moveTo(x1, y1); ctx.lineTo(x2, y2);
    ctx.strokeStyle = color; ctx.lineWidth = lw || 1;
    ctx.setLineDash(dash || []); ctx.stroke(); ctx.setLineDash([]);
  }
  function text(s, x, y, font, color, align, base, halo) {
    ctx.font = sf(font); ctx.textAlign = align || 'left'; ctx.textBaseline = base || 'alphabetic';
    if (halo) { ctx.lineWidth = 3.5; ctx.strokeStyle = P.halo; ctx.lineJoin = 'round'; ctx.strokeText(s, x, y); }
    ctx.fillStyle = color; ctx.fillText(s, x, y);
  }
  function arrowHead(x, y, ang, size, color) {
    ctx.beginPath();
    ctx.moveTo(x, y);
    ctx.lineTo(x - size * Math.cos(ang - 0.4), y - size * Math.sin(ang - 0.4));
    ctx.lineTo(x - size * Math.cos(ang + 0.4), y - size * Math.sin(ang + 0.4));
    ctx.closePath(); ctx.fillStyle = color; ctx.fill();
  }
  function dot(x, y, r, fill, stroke, lw) {
    ctx.beginPath(); ctx.arc(x, y, r, 0, 2 * PI);
    ctx.fillStyle = fill; ctx.fill();
    if (stroke) { ctx.lineWidth = lw || 2; ctx.strokeStyle = stroke; ctx.stroke(); }
  }
  // ---------- Διάγραμμα φ–t ----------
  function drawPhi(sg, idx) {
    var x = PHI.x, y = PHI.y, w = PHI.w, h = PHI.h, i, k, t;
    var y0 = ky(0), Tend = T();
    ctx.fillStyle = P.shade;
    ctx.fillRect(tx(Tend), y, x + w - tx(Tend), h);
    for (t = 0; t <= TMAX; t++) line(tx(t), y, tx(t), y + h, P.gridV);
    for (k = -KMAX; k <= KMAX; k++) line(x, ky(k), x + w, ky(k), k % 6 === 0 ? P.gridH0 : (k % 2 === 0 ? P.gridH1 : P.gridH2));
    // άξονες (ο άξονας t περνά από το φ = 0)
    line(x, y - 12, x, y + h, P.axis, 1.6);
    line(x, y0, x + w + 12, y0, P.axis, 1.6);
    arrowHead(x, y - 14, -PI / 2, 8, P.axis);
    arrowHead(x + w + 14, y0, 0, 8, P.axis);
    text('φ (rad)', x - 8, y - 22, 'bold 13px Arial', P.strong, 'left', 'alphabetic');
    text('t (s)', x + w + 20, y0 + 4, 'bold 13px Arial', P.strong, 'left', 'alphabetic');
    for (k = -KMAX; k <= KMAX; k += 2) text(fracPi(k, 12), x - 8, ky(k), (k % 6 === 0 ? 'bold 12px' : '11px') + ' Arial', k % 6 === 0 ? P.strong : P.dim, 'right', 'middle');
    for (t = 1; t <= TMAX; t++) text(String(t), tx(t), y0 + 6, '12px Arial', P.txt, 'center', 'top', true);
    // βοηθητικές γραμμές από τα σημεία
    var hs = handles();
    for (i = 0; i <= NSEG; i++) {
      line(x, hs[i].y, hs[i].x, hs[i].y, P.guide, 1, [3, 4]);
      if (i > 0) line(hs[i].x, hs[i].y, hs[i].x, y0, P.guide, 1, [3, 4]);
    }
    // τμήματα
    for (i = 0; i < NSEG; i++) {
      var s = sg[i];
      line(tx(s.ta), ky(s.ka), tx(s.tb), ky(s.kb), COL[i], 4.5);
    }
    // αριθμοί τμημάτων
    for (i = 0; i < NSEG; i++) {
      var q = sg[i], mx = tx((q.ta + q.tb) / 2), my = ky((q.ka + q.kb) / 2);
      dot(mx, my, 9, P.bg, COL[i], 2);
      text(String(i + 1), mx, my + 0.5, 'bold 12px Arial', COL[i], 'center', 'middle');
    }
    // δρομέας χρόνου
    if (tcur > 0) {
      line(tx(tcur), y, tx(tcur), y + h, P.cursor, 1.2, [5, 4]);
      dot(tx(tcur), ky(kAt(sg, tcur)), 6.5, COL[idx], '#fff', 2);
    }
    // μπλε σημεία και ετικέτες
    for (i = 0; i <= NSEG; i++) {
      var hx = hs[i].x, hy = hs[i].y;
      var big = (dragging === i || hover === i);
      dot(hx, hy, big ? 9 : 7.5, P.blue, '#fff', 2);
      var lab = i === 0 ? 'φ₀ = ' + fracPi(S.k[0], 12) : 't = ' + S.t[i] + ' s, φ = ' + fracPi(S.k[i], 12);
      var lx, ly, al;
      if (i === 0) { lx = hx + 13; ly = hy - 11; al = 'left'; }
      else { al = hx > x + w - 170 ? 'right' : 'left'; lx = hx + (al === 'right' ? -12 : 12); ly = hy - 12; }
      if (ly < y + 12) ly = hy + 20;
      text(lab, lx, ly, 'bold 12px Arial', P.blueLab, al, 'alphabetic', true);
    }
  }
  // ---------- Διάγραμμα ω–t ----------
  var STEPS = [[1, 12], [1, 6], [1, 4], [1, 3], [1, 2], [1, 1], [2, 1]];
  function drawOmega(sg, idx) {
    var x = OM.x, y = OM.y, w = OM.w, h = OM.h, i, m, Tend = T();
    var us = sg.map(function (s) { return s.num / s.den; });      // ω σε μονάδες π
    var uMax = Math.max.apply(null, us.concat([0])), uMin = Math.min.apply(null, us.concat([0]));
    var st = STEPS[STEPS.length - 1];
    for (i = 0; i < STEPS.length; i++) if ((uMax - uMin) / (STEPS[i][0] / STEPS[i][1]) <= 6) { st = STEPS[i]; break; }
    var step = st[0] / st[1];
    var top = Math.max(Math.ceil(uMax / step - 1e-9), 1) * step;
    var bot = Math.min(Math.floor(uMin / step + 1e-9), 0) * step;
    if (top - bot < 2 * step - 1e-9) bot -= step;
    function oy(u) { return y + h * (top - u) / (top - bot); }
    ctx.fillStyle = P.shade;
    ctx.fillRect(txO(Tend), y, x + w - txO(Tend), h);
    for (i = 0; i <= TMAX; i++) line(txO(i), y, txO(i), y + h, P.gridV);
    var m0 = Math.ceil(bot / step - 1e-9), m1 = Math.floor(top / step + 1e-9);
    for (m = m0; m <= m1; m++) {
      var u = m * step;
      line(x, oy(u), x + w, oy(u), P.gridH1);
      text(fracPi(m * st[0], st[1]), x - 8, oy(u), '12px Arial', P.txt, 'right', 'middle');
    }
    var y0 = oy(0);
    line(x, y - 12, x, y + h, P.axis, 1.6);
    line(x, y0, x + w + 12, y0, P.axis, 1.6);
    arrowHead(x, y - 14, -PI / 2, 8, P.axis);
    arrowHead(x + w + 14, y0, 0, 8, P.axis);
    text('ω (rad/s)', x - 8, y - 22, 'bold 13px Arial', P.strong, 'left', 'alphabetic');
    text('t (s)', x + w + 20, y0 + 4, 'bold 13px Arial', P.strong, 'left', 'alphabetic');
    var tickY = (uMin < 0) ? y + h + 6 : y0 + 6;
    for (i = 0; i <= TMAX; i++) text(String(i), txO(i), tickY, '12px Arial', P.txt, 'center', 'top');
    // σταδιακή σχεδίαση, όσο εξελίσσεται η κίνηση
    for (i = 0; i < NSEG; i++) {
      var s = sg[i];
      if (tcur <= s.ta) continue;
      var te = Math.min(tcur, s.tb);
      line(txO(s.ta), oy(us[i]), txO(te), oy(us[i]), COL[i], 4.5);
      if (i > 0) line(txO(s.ta), oy(us[i - 1]), txO(s.ta), oy(us[i]), P.jump, 1.3, [4, 4]);
      if (te - s.ta >= 0.6 || tcur >= s.tb) {
        text(fracPi(s.num, s.den), txO((s.ta + te) / 2), oy(us[i]) + (us[i] >= 0 ? -9 : 17), 'bold 12px Arial', COL[i], 'center', 'alphabetic', true);
      }
    }
    if (tcur > 0) {
      line(txO(tcur), y, txO(tcur), y + h, P.cursor, 1.2, [5, 4]);
      dot(txO(tcur), oy(us[idx]), 6.5, COL[idx], '#fff', 2);
    }
  }
  // ---------- Κύκλος ----------
  function drawCircle(sg, idx) {
    var cx = CC.x, cy = CC.y, R = CC.R, i;
    var kc = kAt(sg, tcur), phi = kc * PI / 12;
    line(cx - R - 26, cy, cx + R + 26, cy, P.ringFaint, 1);
    line(cx, cy - R - 26, cx, cy + R + 26, P.ringFaint, 1);
    // διανυθέντα τόξα ανά τμήμα
    ctx.lineCap = 'butt';
    for (i = 0; i < NSEG; i++) {
      var s = sg[i];
      if (tcur <= s.ta || s.kb === s.ka) continue;
      var te = Math.min(tcur, s.tb);
      var ke = s.ka + (s.kb - s.ka) * (te - s.ta) / (s.tb - s.ta);
      var a0 = s.ka * PI / 12, a1 = ke * PI / 12;
      ctx.beginPath(); ctx.arc(cx, cy, R, -a0, -a1, a1 > a0);
      ctx.strokeStyle = COL[i]; ctx.globalAlpha = 0.5; ctx.lineWidth = 12; ctx.stroke(); ctx.globalAlpha = 1;
    }
    // κύκλος και υποδιαιρέσεις ανά π/12
    ctx.beginPath(); ctx.arc(cx, cy, R, 0, 2 * PI); ctx.strokeStyle = P.ring; ctx.lineWidth = 2; ctx.stroke();
    for (i = 0; i < 24; i++) {
      var a = i * PI / 12, len = (i % 6 === 0) ? 11 : (i % 2 === 0 ? 8 : 5);
      line(cx + (R - len) * Math.cos(a), cy - (R - len) * Math.sin(a), cx + (R + len) * Math.cos(a), cy - (R + len) * Math.sin(a), P.ring, i % 6 === 0 ? 1.8 : 1);
    }
    text('0 , ±2π', cx + R + 18, cy - 4, '12px Arial', P.txt, 'left', 'bottom');
    text('π/2 , −3π/2', cx, cy - R - 16, '12px Arial', P.txt, 'center', 'bottom');
    text('±π', cx - R - 18, cy - 4, '12px Arial', P.txt, 'right', 'bottom');
    text('3π/2 , −π/2', cx, cy + R + 18, '12px Arial', P.txt, 'center', 'top');
    // θέσεις αλλαγής τμήματος
    for (i = 0; i <= NSEG; i++) {
      var ab = S.k[i] * PI / 12;
      dot(cx + R * Math.cos(ab), cy - R * Math.sin(ab), 5, P.bg, i === 0 ? '#fff' : P.cursor, 1.8);
    }
    // γωνία φ (θετική: αντίθετα από τους δείκτες του ρολογιού, αρνητική: όπως οι δείκτες)
    var px = cx + R * Math.cos(phi), py = cy - R * Math.sin(phi);
    var mid = phi / 2;
    if (Math.abs(kc) > 0.001) {
      ctx.beginPath(); ctx.moveTo(cx, cy); ctx.arc(cx, cy, 52, 0, -phi, phi > 0); ctx.closePath();
      ctx.fillStyle = P.blueFill; ctx.fill();
      ctx.beginPath(); ctx.arc(cx, cy, 52, 0, -phi, phi > 0); ctx.strokeStyle = P.blueTxt; ctx.lineWidth = 2; ctx.stroke();
      text('φ', cx + 72 * Math.cos(mid), cy - 72 * Math.sin(mid), 'italic bold 15px Arial', P.blueTxt, 'center', 'middle');
    }
    line(cx, cy, px, py, P.radius, 2.2);
    // διάνυσμα γωνιακής ταχύτητας στο κέντρο: ⊙ (ω > 0) ή ⊗ (ω < 0)
    var wn = sg[idx].num, wc = COL[idx];
    if (wn !== 0) {
      dot(cx, cy, 14, P.bg, wc, 2.8);
      if (wn > 0) {
        dot(cx, cy, 4.8, wc);
      } else {
        line(cx - 6.5, cy - 6.5, cx + 6.5, cy + 6.5, wc, 2.8);
        line(cx - 6.5, cy + 6.5, cx + 6.5, cy - 6.5, wc, 2.8);
      }
      text('ω', cx + 30 * Math.cos(mid + PI), cy - 30 * Math.sin(mid + PI), 'italic bold 16px Arial', wc, 'center', 'middle', true);
    } else {
      dot(cx, cy, 4, P.radius);
    }
    // διάνυσμα ταχύτητας (φορά κίνησης)
    var sgn = Math.sign(wn);
    if (sgn !== 0) {
      var dx = -Math.sin(phi) * sgn, dy = -Math.cos(phi) * sgn;
      line(px, py, px + dx * 62, py + dy * 62, wc, 3);
      arrowHead(px + dx * 66, py + dy * 66, Math.atan2(dy, dx), 11, wc);
    }
    // υλικό σημείο (σύρεται για να οριστεί η αρχική γωνία)
    var grab = (dragging === NSEG + 1 || hover === NSEG + 1);
    if (grab) { ctx.beginPath(); ctx.arc(px, py, 19, 0, 2 * PI); ctx.strokeStyle = 'rgba(255,255,255,.55)'; ctx.lineWidth = 2; ctx.stroke(); }
    dot(px, py, 11, wc, '#fff', 2.5);
  }
  // ---------- Πληροφορίες ----------
  function drawInfo(sg, idx) {
    var phi = kAt(sg, tcur) * PI / 12;
    var s = sg[idx];
    text('t = ' + num(tcur, 2) + ' s', INFX, 34, 'bold 17px Arial', P.strong, 'left', 'alphabetic');
    text('φ = ' + num(phi, 2) + ' rad', INFX + 120, 34, 'bold 17px Arial', P.blueTxt, 'left', 'alphabetic');
    text('ω = ' + fracPi(s.num, s.den) + ' rad/s  ≈ ' + num(s.w, 2) + ' rad/s', INFX, 59, 'bold 17px Arial', COL[idx], 'left', 'alphabetic');
    var dir = s.num > 0 ? 'αντίθετη φορά από τους δείκτες του ρολογιού' : (s.num < 0 ? 'ίδια φορά με τους δείκτες του ρολογιού' : 'το υλικό σημείο παραμένει ακίνητο');
    text('Τμήμα ' + (idx + 1) + ' · ' + dir, INFX, 82, '13px Arial', P.dim, 'left', 'alphabetic');
    var vec = s.num > 0 ? 'διάνυσμα ω: κύκλος με τελεία (προς τον παρατηρητή)' : (s.num < 0 ? 'διάνυσμα ω: κύκλος με × (μακριά από τον παρατηρητή)' : 'ω = 0: δεν υπάρχει διάνυσμα ω');
    text(vec, INFX, 102, '13px Arial', P.dim, 'left', 'alphabetic');
    var y0 = 614;
    for (var i = 0; i < NSEG; i++) {
      var q = sg[i], act = (i === idx);
      var yy = y0 + i * 26;
      ctx.fillStyle = COL[i]; ctx.fillRect(INFX, yy - 11, 16, 16);
      var lbl = 'Τμήμα ' + (i + 1) + ':  ' + q.ta + ' – ' + q.tb + ' s   ·   Δφ = ' + fracPi(q.num, 12) + '   ·   ω' + SUB[i] + ' = ' + fracPi(q.num, q.den) + ' rad/s';
      text(lbl, INFX + 26, yy + 1, (act ? 'bold ' : '') + '14px Arial', act ? P.strong : P.dim, 'left', 'alphabetic');
    }
  }
  // ---------- Σχεδίαση ----------
  function draw() {
    ctx.clearRect(0, 0, W, H);
    ctx.fillStyle = P.bg; ctx.fillRect(0, 0, W, H);
    var sg = segments();
    var idx = segIndex(sg, tcur);
    drawPhi(sg, idx);
    drawCircle(sg, idx);
    drawInfo(sg, idx);
    if (showOm) {
      for (var gi = 1; gi <= NSEG; gi++) line(tx(S.t[gi]), PHI.y + PHI.h + 4, tx(S.t[gi]), OM.y - 2, 'rgba(143,165,199,.55)', 1.2, [4, 5]);
      drawOmega(sg, idx);
    }
  }
  // ---------- Χειριστήρια ----------
  function $(id) { return document.getElementById(id); }
  var bPlay = $('kyk-play'), bPause = $('kyk-pause'), bHelp = $('kyk-helpb'), sl = $('kyk-tsl'), tl = $('kyk-tl');
  function syncUI() {
    sl.max = String(Math.round(T() * 100));
    sl.value = String(Math.round(tcur * 100));
    tl.textContent = 't = ' + num(tcur, 1) + ' s';
    bPlay.classList.toggle('k-on', playing);
    bPause.classList.toggle('k-on', !playing && tcur > 0 && tcur < T());
  }
  function play() { if (tcur >= T()) tcur = 0; playing = true; dirty = true; syncUI(); }
  function pause() { playing = false; dirty = true; syncUI(); }
  function toStart() { playing = false; tcur = 0; dirty = true; syncUI(); }
  // Βήμα προς τα εμπρός / πίσω κατά ένα δευτερόλεπτο (στο επόμενο / προηγούμενο ακέραιο)
  function stepFwd() { playing = false; tcur = Math.min(T(), Math.floor(tcur + 1e-6) + 1); dirty = true; syncUI(); }
  function stepBack() { playing = false; tcur = Math.max(0, Math.ceil(tcur - 1e-6) - 1); dirty = true; syncUI(); }
  // Επανεκκίνηση: πλήρης επαναφορά στην αρχική κατάσταση (διάγραμμα, χρόνος, εμφάνιση)
  function resetAll() {
    S = defaults(); playing = false; tcur = 0; dragging = -1; hover = -1; dirty = true;
    syncUI();
  }
  bPlay.addEventListener('click', play);
  bPause.addEventListener('click', pause);
  $('kyk-rew').addEventListener('click', toStart);
  $('kyk-sfwd').addEventListener('click', stepFwd);
  $('kyk-sback').addEventListener('click', stepBack);
  $('kyk-reset').addEventListener('click', resetAll);
  bHelp.addEventListener('click', function () {
    var h = $('kyk-help'); h.classList.toggle('k-open'); bHelp.classList.toggle('k-on', h.classList.contains('k-open'));
  });
  sl.addEventListener('input', function () { playing = false; tcur = clamp(parseInt(sl.value, 10) / 100, 0, T()); dirty = true; syncUI(); });
  $('kyk-spd').addEventListener('change', function (e) { speed = parseFloat(e.target.value); });
  $('kyk-rep').addEventListener('change', function (e) { repeat = e.target.checked; });
  $('kyk-showom').addEventListener('change', function (e) {
    showOm = e.target.checked;
    setHeight(showOm ? H_FULL : H_TOP); document.getElementById('kyk-app').classList.toggle('k-dock', showOm);
  });
  function frame(ts) {
    var dt = Math.min(0.1, (ts - lastTs) / 1000);
    lastTs = ts;
    if (playing) {
      tcur += dt * speed;
      if (tcur >= T()) {
        if (repeat) tcur = 0; else { tcur = T(); playing = false; }
      }
      dirty = true; syncUI();
    }
    if (dirty) { draw(); dirty = false; }
    requestAnimationFrame(frame);
  }
  // ---------- Ποντίκι / αφή ----------
  function pt(e) {
    var r = cv.getBoundingClientRect();
    return { x: (e.clientX - r.left) * W / r.width, y: (e.clientY - r.top) * H / r.height };
  }
  function hit(p) {
    var hs = handles(), best = -1, bd = Infinity;
    for (var i = 0; i < hs.length; i++) {
      var d = (hs[i].x - p.x) * (hs[i].x - p.x) + (hs[i].y - p.y) * (hs[i].y - p.y);
      if (d <= hs[i].r * hs[i].r && d < bd) { bd = d; best = i; }
    }
    return best;
  }
  cv.addEventListener('pointerdown', function (e) {
    var p = pt(e), i = hit(p);
    if (i < 0) return;
    dragging = i; cv.setPointerCapture(e.pointerId);
    playing = false; tcur = 0;
    applyDrag(i, p); syncUI(); cv.style.cursor = 'grabbing'; e.preventDefault();
  });
  cv.addEventListener('pointermove', function (e) {
    var p = pt(e);
    if (dragging >= 0) { applyDrag(dragging, p); syncUI(); return; }
    var h = hit(p);
    if (h !== hover) { hover = h; dirty = true; }
    cv.style.cursor = h >= 0 ? 'grab' : 'default';
  });
  function endDrag(e) {
    if (dragging < 0) return;
    dragging = -1; dirty = true;
    try { cv.releasePointerCapture(e.pointerId); } catch (err) {}
    cv.style.cursor = hover >= 0 ? 'grab' : 'default';
  }
  cv.addEventListener('pointerup', endDrag);
  cv.addEventListener('pointercancel', endDrag);
  cv.addEventListener('pointerleave', function () { if (dragging < 0 && hover !== -1) { hover = -1; dirty = true; } });
  // ---------- Πλήρης οθόνη ----------
  var appEl = document.getElementById('kyk-app');
  function setFS(on) {
    fsOn = on; appEl.classList.toggle('k-fs', on);
    $('kyk-fst').textContent = on ? 'Έξοδος' : 'Πλήρης οθόνη';
    $('kyk-fsi').setAttribute('d', on ? 'M5 1h2v6H1V5h4zM9 1h2v4h4v2H9zM1 9h6v6H5v-4H1zM9 9h6v2h-4v4H9z' : 'M1 1h5v2H3v3H1zM10 1h5v5h-2V3h-3zM1 10h2v3h3v2H1zM13 10h2v5h-5v-2h3z');
    if (on) wake(); else { clearTimeout(idleT); appEl.classList.remove('k-idle'); }
    resize(); setTimeout(resize, 120); setTimeout(resize, 400);
  }
  var idleT = 0;
  function wake() {                      // στην πλήρη οθόνη η γραμμή κουμπιών κρύβεται μετά από λίγο και επανεμφανίζεται με κάθε κίνηση ή άγγιγμα
    appEl.classList.remove('k-idle'); clearTimeout(idleT);
    idleT = setTimeout(function () {
      var bar = appEl.querySelector('.k-bar');
      if (!fsOn || dragging >= 0 || playing === 'x' || (bar && bar.matches(':hover')) || appEl.querySelector('.k-help.k-open') || (bar && bar.contains(document.activeElement) && document.activeElement.tagName === 'SELECT')) { if (fsOn) wake(); return; }
      appEl.classList.add('k-idle');
    }, 3500);
  }
  ['pointermove', 'pointerdown', 'touchstart', 'keydown'].forEach(function (ev) {
    appEl.addEventListener(ev, function () { if (fsOn) wake(); }, true);
  });
  function fsElem() { return document.fullscreenElement || document.webkitFullscreenElement || null; }
  $('kyk-fs').addEventListener('click', function () {
    if (fsOn) {
      if (fsElem()) { (document.exitFullscreen || document.webkitExitFullscreen).call(document); } else setFS(false);
      return;
    }
    var rq = appEl.requestFullscreen || appEl.webkitRequestFullscreen;
    if (!rq) { setFS(true); return; }
    try {
      var pr = rq.call(appEl);
      if (pr && pr.then) pr.then(function () { setFS(true); }, function () { setFS(true); });
      else setFS(true);
    } catch (err) { setFS(true); }
  });
  function onFsChange() { if (fsElem() === appEl) { if (!fsOn) setFS(true); } else if (fsOn) setFS(false); }
  document.addEventListener('fullscreenchange', onFsChange);
  document.addEventListener('webkitfullscreenchange', onFsChange);
  document.addEventListener('keydown', function (e) { if (e.key === 'Escape' && fsOn && !fsElem()) setFS(false); });
    resize(); syncUI();
  requestAnimationFrame(frame);
})();
</script>
