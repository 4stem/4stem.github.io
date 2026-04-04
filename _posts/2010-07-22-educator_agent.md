---
layout: post
title: "Βοηθός Δημιουργίας Διαγωνίσματος Φυσικής"
description: "Διαδραστικό εργαλείο για εκπαιδευτικούς - παρακολούθηση τύπων ανά κεφάλαιο"
category: Εφαρμογή
tags: [Διαγώνισμα, Φυσική, Εργαλείο]
---

Διαδραστική εφαρμογή για εκπαιδευτικούς Φυσικής Γ' Λυκείου. Επιλέξτε κεφάλαια, σημειώστε εξετασμένους τύπους και αποθηκεύστε/μοιραστείτε την εργασία σας.

---

<script>
  window.MathJax = {
    tex: { inlineMath: [['\\(', '\\)']], displayMath: [['$$', '$$']] }
  };
  </script>
<script src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-chtml.js" async></script>

<style>

    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: #f5f9fc;
      min-height: 100vh;
      padding: 24px 16px 48px;
      color: #2c3e50;
    }
    .container { max-width: 980px; margin: 0 auto; }
    .app-header {
      background: linear-gradient(135deg, #2c3e50 0%, #2c3e50 50%, #2c6496 100%);
      color: white; padding: 24px 28px; border-radius: 12px;
      margin-bottom: 20px; box-shadow: 0 8px 32px rgba(15,52,96,0.3);
    }
    .app-header h1 { font-size: 1.35em; font-weight: 700; margin-bottom: 4px; }
    .app-header p { opacity: 0.72; font-size: 0.88em; }
    .section-label {
      font-size: 0.76em; font-weight: 700; letter-spacing: 1.4px;
      text-transform: uppercase; color: #2c6496; margin-bottom: 9px;
    }
    .chapters-grid { display: flex; flex-wrap: wrap; gap: 9px; margin-bottom: 18px; }
    .chapter-btn {
      border: 2px solid #2c6496; background: white; color: #2c6496;
      padding: 7px 14px; border-radius: 8px; cursor: pointer;
      font-size: 0.84em; font-weight: 600; transition: all 0.18s; white-space: nowrap;
    }
    .chapter-btn:hover { background: #e8f0f8; }
    .chapter-btn.active { background: #2c6496; color: white; }
    .chapter-btn.all-btn { border-color: #e63946; color: #e63946; }
    .chapter-btn.all-btn:hover { background: #ffeef0; }
    .chapter-btn.all-btn.active { background: #e63946; color: white; }

    /* ── TOOLBAR ── */
    .toolbar {
      display: flex; flex-wrap: wrap; gap: 8px; align-items: center;
      background: white; border: 1px solid #d0dde8; border-radius: 10px;
      padding: 11px 16px; margin-bottom: 14px;
    }
    .toolbar-label { font-size: 0.78em; color: #666; font-weight: 600;
      text-transform: uppercase; letter-spacing: 1px; margin-right: 4px; }
    .tb-btn {
      padding: 6px 13px; border-radius: 7px; border: none; cursor: pointer;
      font-size: 0.82em; font-weight: 600; transition: all 0.18s;
    }
    .tb-btn.save   { background: #2c6496; color: white; }
    .tb-btn.save:hover   { background: #235280; }
    .tb-btn.load   { background: #5a8a5a; color: white; }
    .tb-btn.load:hover   { background: #477047; }
    .tb-btn.share  { background: #7c5cbf; color: white; }
    .tb-btn.share:hover  { background: #6448a8; }
    .tb-btn.filter { background: #2c6496; color: white; }
    .tb-btn.filter:hover { background: #235280; }
    .tb-sep { width: 1px; background: #dde4f0; height: 26px; margin: 0 4px; }
    .ts-label { font-size: 0.76em; color: #888; margin-left: auto; white-space: nowrap; }

    /* ── PROGRESS ── */
    .progress-wrap {
      background: #f5f9fc; border-radius: 10px; padding: 13px 16px;
      margin-bottom: 14px; border-left: 4px solid #2c6496;
      display: flex; align-items: center; gap: 14px; flex-wrap: wrap;
    }
    .progress-text { font-size: 0.88em; color: #2c6496; font-weight: 600; min-width: 180px; }
    .progress-remaining { font-size: 0.8em; color: #e63946; font-weight: 600; }
    .progress-bar-outer { flex: 1; min-width: 100px; height: 10px; background: #dce8f0; border-radius: 5px; overflow: hidden; }
    .progress-bar-inner { height: 100%; background: linear-gradient(90deg, #2c6496, #e63946); border-radius: 5px; transition: width 0.4s ease; width: 0%; }
    .progress-pct { font-size: 0.84em; font-weight: 700; color: #e63946; min-width: 38px; text-align: right; }
    .actions-bar {
      display: flex; gap: 9px; flex-wrap: wrap; margin-bottom: 20px;
      padding: 12px 16px; background: white; border-radius: 10px; border: 1px solid #d0dde8;
    }
    .action-btn { padding: 7px 14px; border-radius: 7px; border: none; cursor: pointer; font-size: 0.83em; font-weight: 600; transition: all 0.18s; }
    .action-btn.cover-all { background: #f4a100; color: white; }
    .action-btn.cover-all:hover { background: #d08c00; }
    .action-btn.uncover { background: #2c6496; color: white; }
    .action-btn.uncover:hover { background: #245480; }
    .action-btn.reset { background: #e63946; color: white; }
    .action-btn.reset:hover { background: #c0303b; }

    .legend { display: flex; gap: 18px; flex-wrap: wrap; font-size: 0.79em; color: #666; margin-bottom: 14px; }
    .legend-item { display: flex; align-items: center; gap: 6px; }
    .legend-dot { width: 13px; height: 13px; border-radius: 3px; flex-shrink: 0; }

    /* ── CHAPTER SECTIONS ── */
    .chapter-section {
      background: white; border: 1px solid #d0dde8; border-radius: 12px;
      margin-bottom: 18px; overflow: hidden; box-shadow: 0 2px 10px rgba(15,52,96,0.07);
      transition: opacity 0.2s;
    }
    .chapter-section.chapter-done { border-color: #a8d5a8; }
    .chapter-section-header {
      background: linear-gradient(90deg, #2c6496, #3d6494);
      color: white; padding: 13px 18px;
      display: flex; justify-content: space-between; align-items: center;
    }
    .chapter-section.chapter-done .chapter-section-header {
      background: linear-gradient(90deg, #2d7a2d, #3d9a3d);
    }
    .chapter-section-header h3 { font-size: 0.97em; font-weight: 700; color: white; }
    .ch-stats { font-size: 0.79em; opacity: 0.88; background: rgba(255,255,255,0.15);
      padding: 3px 10px; border-radius: 20px; white-space: nowrap; }
    .formula-row {
      display: flex; align-items: flex-start; padding: 11px 18px;
      border-bottom: 1px solid #edf2f7; transition: background 0.15s;
      gap: 13px; cursor: pointer; user-select: none;
    }
    .formula-row:last-child { border-bottom: none; }
    .formula-row:hover { background: #f8fafc; }
    .formula-row.covered { background: #fff8e6; }
    .formula-row.covered:hover { background: #fff0c8; }
    .formula-check {
      width: 22px; height: 22px; border: 2px solid #b0b8d0; border-radius: 5px;
      flex-shrink: 0; display: flex; align-items: center; justify-content: center;
      background: white; transition: all 0.18s; font-size: 13px; margin-top: 2px;
    }
    .formula-row.covered .formula-check { background: #f4a100; border-color: #f4a100; color: white; }
    .formula-name { flex: 1; font-size: 0.89em; color: #2c6496; font-weight: 500; padding-top: 3px; }
    .formula-math { font-size: 0.89em; color: #2c6496; min-width: 250px; text-align: right; }
    .formula-math.multi { line-height: 1.9; }
    .formula-row.covered .formula-name { text-decoration: line-through; color: #997000; }
    .formula-row.covered .formula-math { color: #c48c00; }
    .proof-block {
      font-size: 0.79em; color: #666; background: #f8fafc;
      border-left: 3px solid #8aaac8; padding: 5px 9px;
      margin-top: 5px; border-radius: 0 4px 4px 0; line-height: 1.65;
    }
    .empty-state {
      text-align: center; padding: 44px 24px; color: #999;
      background: white; border-radius: 12px; border: 1px solid #d0dde8;
    }
    .empty-state .icon { font-size: 2.8em; margin-bottom: 14px; }
    @media (max-width: 640px) {
      .formula-row { flex-wrap: wrap; }
      .formula-math { min-width: unset; text-align: left; width: 100%; padding-left: 35px; }
      .app-header { padding: 18px; }
      .app-header h1 { font-size: 1.12em; }
      .ts-label { display: none; }
    }
  </style>

<div class="container">

  <div class="app-header">
    <h1>📋 Βοηθός Δημιουργίας Διαγωνίσματος Φυσικής</h1>
    <p>Επιλέξτε κεφάλαια και σημειώστε τους τύπους που έχετε ήδη εξετάσει</p>
  </div>

  <div class="section-label">Επιλογή Κεφαλαίων</div>
  <div class="chapters-grid" id="chapterButtons"></div>

  <!-- TOOLBAR -->
  <div class="toolbar">
    <span class="toolbar-label">💾 Εργασία:</span>
    <button class="tb-btn save"  onclick="exportState()">Εξαγωγή / Κοινοποίηση</button>
    <button class="tb-btn load"  onclick="importFromFile()">Φόρτωση από αρχείο</button>
    <div class="tb-sep"></div>
    <span class="toolbar-label">👁 Προβολή:</span>
    <button class="tb-btn filter" id="filterBtn" onclick="toggleFilter()">🔍 Μόνο Αδιάβαστα</button>
    <span class="ts-label" id="lastSaved"></span>
  </div>

  <div class="legend">
    <div class="legend-item">
      <div class="legend-dot" style="background:#d8e2f5;border:2px solid #b0b8d0;"></div>
      <span>Δεν εξετάστηκε</span>
    </div>
    <div class="legend-item">
      <div class="legend-dot" style="background:#f4a100;"></div>
      <span>Εξετάστηκε ✓</span>
    </div>
    <div class="legend-item">
      <div class="legend-dot" style="background:#2d7a2d;"></div>
      <span>Κεφάλαιο ολοκληρωμένο ✅</span>
    </div>
  </div>

  <div id="progressArea" style="display:none">
    <div class="progress-wrap">
      <div class="progress-text">
        Κάλυψη: <span id="coveredCount">0</span> / <span id="totalCount">0</span> τύποι
        <span class="progress-remaining" id="remainingCount"></span>
      </div>
      <div class="progress-bar-outer"><div class="progress-bar-inner" id="progressBar"></div></div>
      <div class="progress-pct" id="progressPct">0%</div>
    </div>
    <div class="actions-bar">
      <button class="action-btn cover-all" onclick="coverAll()">☑ Σημείωση Όλων ως Εξετασμένων</button>
      <button class="action-btn uncover"   onclick="uncoverAll()">↺ Αναίρεση Όλων</button>
      <button class="action-btn reset"     onclick="resetSelection()">✕ Νέο Διαγώνισμα</button>
    </div>
  </div>

  <div id="formulaArea"></div>

</div>

<script>
const CHAPTERS = [
  {
    id: 1,
    title: "1. Κρούσεις & Σχετικές Κινήσεις",
    shortTitle: "Κρούσεις",
    dw: 12,
    formulas: [
      {
        name: "Αρχή Διατήρησης Ορμής",
        latex: "p_{\\pi\\rho\\iota\\nu} = p_{\\mu\\varepsilon\\tau\\acute{\\alpha}}"
      },
      {
        name: "Κεντρική Ελαστική Κρούση",
        latex: "v_1' = \\dfrac{m_1-m_2}{m_1+m_2}v_1 + \\dfrac{2m_2}{m_1+m_2}v_2 \\\\[6pt] v_2' = \\dfrac{2m_1}{m_1+m_2}v_1 + \\dfrac{m_2-m_1}{m_1+m_2}v_2",
        multiline: true
      },
      {
        name: "Ελαστική Κρούση – Ίσες Μάζες (Σ₂ ακίνητη)",
        latex: "v_1' = \\dfrac{m_1-m_2}{m_1+m_2}\\,v_1 \\\\[6pt] v_2' = \\dfrac{2m_1}{m_1+m_2}\\,v_1",
        multiline: true
      },
      {
        name: "Πλαστική Κρούση (Κοινή Ταχύτητα V)",
        latex: "m_1v_1 + m_2v_2 = (m_1+m_2)V"
      },
      {
        name: "Μεταβολή Κινητικής Ενέργειας",
        latex: "\\Delta K = K_{\\mu\\varepsilon\\tau\\acute{\\alpha}} - K_{\\pi\\rho\\iota\\nu}"
      },
      {
        name: "Πλάγια Κρούση (γωνία πρόσπτωσης = γωνία ανάκλασης)",
        latex: "\\pi = \\alpha",
        proof: "Διάσπαση ταχύτητας: \\(v_x' = -v_x\\), \\(v_y' = v_y\\) &rarr; \\(v' = \\sqrt{v_x'^2+v_y'^2} = v\\).<br>Επίσης \\(\\eta\\mu\\pi = v_y/v = v_y'/v' = \\eta\\mu\\alpha\\), οπότε \\(\\pi = \\alpha\\)."
      }
    ]
  },
  {
    id: 2,
    title: "2. Μηχανική Στερεού Σώματος",
    shortTitle: "Στερεό",
    dw: 18,
    formulas: [
      { name: "Ορισμός Γωνιακής Ταχύτητας", latex: "\\omega = \\dfrac{d\\theta}{dt}" },
      { name: "Γραμμική και Γωνιακή Ταχύτητα", latex: "v = \\omega r" },
      { name: "Γωνιακή Επιτάχυνση", latex: "\\alpha_{\\gamma\\omega\\nu} = \\dfrac{d\\omega}{dt}" },
      { name: "Επιτάχυνση Κέντρου Μάζας (Κύλιση)", latex: "a_{cm} = \\alpha_{\\gamma\\omega\\nu} R" },
      { name: "Ροπή Δύναμης (ως προς άξονα)", latex: "\\tau = F \\cdot d" },
      { name: "Στροφορμή Υλικού Σημείου (κυκλική κίνηση)", latex: "L = m\\upsilon r = pr" },
      {
        name: "Θεμελιώδης Νόμος Στροφικής Κίνησης",
        latex: "\\Sigma\\tau = \\dfrac{dL}{dt} \\qquad (\\Sigma\\tau = F \\cdot d)"
      },
      { name: "Διατήρηση Στροφορμής (αν Στ=0)", latex: "L_{\\text{ολ}} = \\text{σταθερή}" },
      {
        name: "Ισορροπία Στερεού Σώματος",
        latex: "\\Sigma F = 0 \\;\\Leftrightarrow\\; \\begin{cases} \\Sigma F_x = 0 \\\\ \\Sigma F_y = 0 \\end{cases} \\qquad \\Sigma\\tau = 0",
        multiline: false
      }
    ]
  },
  {
    id: 3,
    title: "3. Μηχανικές Ταλαντώσεις",
    shortTitle: "Ταλαντώσεις",
    dw: 16,
    formulas: [
      {
        name: "Κινηματική προσέγγιση (θέση, ταχύτητα, επιτάχυνση)",
        latex: "x = A\\,\\eta\\mu(\\omega t) \\\\[4pt] \\upsilon = \\upsilon_{max}\\,\\text{συν}(\\omega t) \\\\[4pt] a = -a_{max}\\,\\eta\\mu(\\omega t)",
        multiline: true
      },
      {
        name: "Περίοδος & Συχνότητα",
        latex: "T = \\dfrac{t}{N},\\quad f = \\dfrac{1}{T} \\\\[6pt] T = 2\\pi\\sqrt{\\dfrac{m}{D}}",
        multiline: true
      },
      {
        name: "Γωνιακή Συχνότητα",
        latex: "\\omega = \\dfrac{2\\pi}{T} = 2\\pi f"
      },
      {
        name: "Μέγιστη Ταχύτητα & Επιτάχυνση",
        latex: "v_{max} = \\omega A, \\quad a_{max} = \\omega^2 A"
      },
      { name: "Δύναμη Επαναφοράς", latex: "\\Sigma F = -m\\omega^2 x = -Dx" },
      { name: "Ολική Ενέργεια Ταλάντωσης", latex: "E = K + U = \\tfrac{1}{2}DA^2" },
      { name: "Πλάτος Φθίνουσας Ταλάντωσης", latex: "A = A_0 e^{-\\Lambda t}" },
      { name: "Εξαναγκασμένη Ταλάντωση – Συχνότητα", latex: "f_{\\text{ταλάντωσης}} = f_{\\text{διεγέρτη}}" }
    ]
  },
  {
    id: 4,
    title: "4. Κύματα",
    shortTitle: "Κύματα",
    dw: 16,
    formulas: [
      { name: "Ταχύτητα Διάδοσης Κύματος", latex: "v = \\dfrac{x}{t}" },
      { name: "Θεμελιώδης Εξίσωση Κυματικής", latex: "v = \\lambda f = \\dfrac{\\lambda}{T}" },
      {
        name: "Εξίσωση Αρμονικού Κύματος",
        latex: "y = A\\sin 2\\pi\\!\\left(\\dfrac{t}{T} - \\dfrac{x}{\\lambda}\\right)"
      },
      {
        name: "Στιγμιότυπο Κύματος (για \\(t = t_1\\))",
        latex: "y = A\\sin\\!\\left(\\sigma\\tau\\alpha\\theta. - \\dfrac{2\\pi}{\\lambda}x\\right) \\\\[4pt] \\sigma\\tau\\alpha\\theta. = \\dfrac{2\\pi t_1}{T}",
        multiline: true
      },
      { name: "Ενισχυτική Συμβολή", latex: "r_1 - r_2 = N\\lambda" },
      { name: "Αποσβεστική Συμβολή", latex: "r_1 - r_2 = (2N+1)\\dfrac{\\lambda}{2}" },
      { name: "Εξίσωση Στάσιμου Κύματος", latex: "y = 2A\\cos\\!\\left(\\dfrac{2\\pi x}{\\lambda}\\right)\\sin\\!\\left(\\dfrac{2\\pi t}{T}\\right)" },
      { name: "Ένταση Ηλ. & Μαγν. Πεδίου (ΗΜΚ)", latex: "\\dfrac{E}{B} = c" }
    ]
  },
  {
    id: 5,
    title: "5. Μαγνητικό Πεδίο",
    shortTitle: "Μαγνητικό Πεδίο",
    dw: 23,
    formulas: [
      { name: "Νόμος Biot-Savart", latex: "\\Delta B = \\dfrac{\\mu_0}{4\\pi}\\dfrac{I\\Delta l\\sin\\theta}{r^2}" },
      { name: "Ένταση Πεδίου Ευθύγραμμου Αγωγού", latex: "B = \\dfrac{\\mu_0}{4\\pi}\\dfrac{2I}{a}" },
      { name: "Ένταση Πεδίου Κυκλικού Αγωγού (κέντρο)", latex: "B = \\dfrac{\\mu_0}{4\\pi}\\dfrac{2\\pi I}{r}" },
      { name: "Ένταση Πεδίου Σωληνοειδούς", latex: "B = \\mu_0 I n" },
      { name: "Νόμος του Ampere", latex: "\\Sigma B\\Delta l\\cos\\theta = \\mu_0 I_{\\varepsilon\\gamma\\kappa}" },
      { name: "Μαγνητική Ροή", latex: "\\Phi = BA\\cos\\theta" },
      { name: "Δύναμη Lorentz (σε φορτίο)", latex: "F = Bvq\\sin\\theta" },
      { name: "Ακτίνα Κυκλικής Τροχιάς Φορτίου", latex: "R = \\dfrac{mv}{B|q|}" },
      { name: "Περίοδος Περιστροφής σε Μαγνητικό Πεδίο (4.12)", latex: "T = \\dfrac{2\\pi m}{B|q|}" },
      { name: "Βήμα Έλικας", latex: "\\beta = \\upsilon_{\\parallel}\\cdot T = \\dfrac{2\\pi m\\,\\upsilon_{\\parallel}}{B|q|}" },
      { name: "Δύναμη Laplace (σε αγωγό)", latex: "F = BIl\\sin\\phi" },
      { name: "Δύναμη μεταξύ Παράλληλων Αγωγών", latex: "\\dfrac{F}{l} = \\dfrac{\\mu_0}{4\\pi}\\dfrac{2I_1 I_2}{a}" }
    ]
  },
  {
    id: 6,
    title: "6. Επαγωγή",
    shortTitle: "Επαγωγή",
    dw: 22,
    formulas: [
      { name: "Νόμος της Επαγωγής (Faraday)", latex: "E_{ind} = -N\\dfrac{\\Delta\\Phi}{\\Delta t}" },
      {
        name: "Επαγωγικό Φορτίο",
        latex: "\\Delta q = N\\dfrac{|\\Delta\\Phi|}{R}"
      },
      { name: "Νόμος Ohm (επαγόμενο ρεύμα)", latex: "I = \\dfrac{E_{\\varepsilon\\pi}}{R}" },
      { name: "Στρεφόμενος Δίσκος", latex: "E_{\\varepsilon\\pi} = \\tfrac{1}{2}B\\omega r^2" },
      { name: "ΗΕΔ σε Κινούμενο Αγωγό", latex: "E = BLv" },
      { name: "ΗΕΔ σε Στρεφόμενο Αγωγό", latex: "E = \\tfrac{1}{2}BL^2\\omega" },
      { name: "Εναλλασσόμενη Τάση (Πλάτος)", latex: "V = NBA\\omega" },
      {
        name: "Ενεργές Τιμές Τάσης & Ρεύματος",
        latex: "V_{\\varepsilon\\nu} = \\dfrac{V}{\\sqrt{2}},\\quad I_{\\varepsilon\\nu} = \\dfrac{I}{\\sqrt{2}}"
      },
      { name: "ΗΕΔ Αυτεπαγωγής", latex: "E_{\\alpha\\upsilon\\tau} = -L\\dfrac{di}{dt}" },
      { name: "Ενέργεια Μαγνητικού Πεδίου Πηνίου", latex: "U = \\tfrac{1}{2}LI^2" },
      {
        name: "Αρχή Διατήρησης Ενέργειας στην Επαγωγή",
        latex: "W_F = Q \\;\\Rightarrow\\; F\\cdot\\upsilon\\Delta t = I^2 R\\Delta t",
        proof: "Κινούμενος αγωγός ΚΛ σε πεδίο \\(B\\): &nbsp;\\(E_{\\varepsilon\\pi}=B\\upsilon L\\), &nbsp;\\(I=\\frac{E_{\\varepsilon\\pi}}{R}=\\frac{B\\upsilon L}{R}\\).<br>Θερμότητα: \\(Q = I^2R\\Delta t = \\frac{B^2\\upsilon^2L^2}{R}\\Delta t\\).<br>Εξωτερική δύναμη: \\(F = BIL = \\frac{B^2\\upsilon L^2}{R}\\), &nbsp; \\(W_F = F\\cdot\\upsilon\\Delta t = \\frac{B^2\\upsilon^2L^2}{R}\\Delta t = Q\\). ✓"
      }
    ]
  },
  {
    id: 7,
    title: "7. Στοιχεία Κβαντομηχανικής",
    shortTitle: "Κβαντομηχανική",
    dw: 23,
    formulas: [
      { name: "Κβάντωση Ενέργειας Ταλαντωτή", latex: "E = nhf" },
      { name: "Νόμος Μετατόπισης Wien", latex: "\\lambda_{max}T = \\text{σταθερό}" },
      { name: "Ενέργεια Φωτονίου", latex: "E = hf = \\dfrac{hc}{\\lambda}" },
      { name: "Φωτοηλεκτρική Εξίσωση Einstein", latex: "K_{max} = hf - \\phi" },
      { name: "Συχνότητα Κατωφλίου", latex: "f_0 = \\dfrac{\\phi}{h}" },
      { name: "Ορμή Φωτονίου", latex: "p = \\dfrac{E}{c} = \\dfrac{h}{\\lambda}" },
      {
        name: "Φαινόμενο Compton",
        latex: "\\lambda' - \\lambda = \\dfrac{h}{mc}(1 - \\cos\\phi)"
      },
      {
        name: "Κινητική Ενέργεια Ανακρουόμενου Ηλεκτρονίου (Compton)",
        latex: "K_e = \\dfrac{hc}{\\lambda} - \\dfrac{hc}{\\lambda'}"
      },
      { name: "Κινητική Ενέργεια", latex: "K = \\dfrac{p^2}{2m}" },
      { name: "Κύματα de Broglie", latex: "\\lambda = \\dfrac{h}{p}" },
      { name: "Αρχή Αβεβαιότητας Heisenberg (θέση–ορμή)", latex: "\\Delta x \\cdot \\Delta p_x \\geq \\dfrac{h}{4\\pi}" },
      { name: "Αρχή Αβεβαιότητας Heisenberg (ενέργεια–χρόνος)", latex: "\\Delta E \\cdot \\Delta t \\geq \\dfrac{h}{2\\pi}" }
    ]
  }
];

// ── STATE ────────────────────────────────────────────────────────────────────
let selectedChapters = new Set();
let coveredFormulas  = new Set();   // keys like "1-3"
let showOnlyUncovered = false;
const STORAGE_KEY = 'diagwnisma_state_v1';

// ── PERSIST: localStorage (auto-save on every change) ────────────────────────
function saveState() {
  const state = {
    chapters: [...selectedChapters],
    covered:  [...coveredFormulas],
    ts: Date.now()
  };
  try {
    localStorage.setItem(STORAGE_KEY, JSON.stringify(state));
  } catch(e) {}
  updateTimestamp(state.ts);
}

function loadState() {
  try {
    const raw = localStorage.getItem(STORAGE_KEY);
    if (!raw) return false;
    const state = JSON.parse(raw);
    selectedChapters = new Set(state.chapters || []);
    coveredFormulas  = new Set(state.covered  || []);
    updateTimestamp(state.ts);
    return true;
  } catch(e) { return false; }
}

function updateTimestamp(ts) {
  if (!ts) return;
  const el = document.getElementById('lastSaved');
  if (el) el.textContent = 'Αποθηκεύτηκε: ' + new Date(ts).toLocaleString('el-GR');
}

// ── SHARE: export/import JSON + URL hash ─────────────────────────────────────
function exportState() {
  const state = {
    chapters: [...selectedChapters],
    covered:  [...coveredFormulas],
    ts: Date.now()
  };
  const json = JSON.stringify(state);
  // Put into URL hash (base64) for easy sharing
  const hash = '#state=' + btoa(unescape(encodeURIComponent(json)));
  const shareUrl = window.location.href.split('#')[0] + hash;

  // Also offer JSON download
  const blob = new Blob([json], {type:'application/json'});
  const url  = URL.createObjectURL(blob);
  const a    = document.createElement('a');
  a.href = url;
  a.download = 'diagwnisma_' + new Date().toISOString().slice(0,10) + '.json';
  a.click();
  URL.revokeObjectURL(url);

  // Copy share URL to clipboard
  navigator.clipboard.writeText(shareUrl).then(() => {
    showToast('📋 Το link αντιγράφηκε! Στείλτε το σε συνεργάτες.');
  }).catch(() => {
    showToast('🔗 ' + shareUrl, 8000);
  });
}

function importFromFile() {
  const input = document.createElement('input');
  input.type = 'file';
  input.accept = '.json';
  input.onchange = e => {
    const file = e.target.files[0];
    if (!file) return;
    const reader = new FileReader();
    reader.onload = ev => {
      try {
        const state = JSON.parse(ev.target.result);
        selectedChapters = new Set(state.chapters || []);
        coveredFormulas  = new Set(state.covered  || []);
        saveState();
        renderAll();
        showToast('✅ Η κατάσταση φορτώθηκε επιτυχώς!');
      } catch(err) {
        showToast('❌ Σφάλμα ανάγνωσης αρχείου.');
      }
    };
    reader.readAsText(file);
  };
  input.click();
}

function loadFromHash() {
  try {
    const hash = window.location.hash;
    if (!hash.startsWith('#state=')) return false;
    const json = decodeURIComponent(escape(atob(hash.slice(7))));
    const state = JSON.parse(json);
    selectedChapters = new Set(state.chapters || []);
    coveredFormulas  = new Set(state.covered  || []);
    saveState();
    return true;
  } catch(e) { return false; }
}

// ── TOAST NOTIFICATION ────────────────────────────────────────────────────────
function showToast(msg, dur=3000) {
  let t = document.getElementById('toast');
  if (!t) {
    t = document.createElement('div');
    t.id = 'toast';
    t.style.cssText = 'position:fixed;bottom:24px;left:50%;transform:translateX(-50%);' +
      'background:#2c3e50;color:white;padding:12px 22px;border-radius:8px;font-size:0.88em;' +
      'z-index:9999;box-shadow:0 4px 20px rgba(0,0,0,0.25);max-width:90vw;text-align:center;' +
      'transition:opacity 0.4s;opacity:0;word-break:break-all;';
    document.body.appendChild(t);
  }
  t.textContent = msg;
  t.style.opacity = '1';
  clearTimeout(t._timer);
  t._timer = setTimeout(() => { t.style.opacity = '0'; }, dur);
}

// ── FILTER ───────────────────────────────────────────────────────────────────
function toggleFilter() {
  showOnlyUncovered = !showOnlyUncovered;
  const btn = document.getElementById('filterBtn');
  if (btn) {
    btn.textContent = showOnlyUncovered ? '👁 Εμφάνιση Όλων' : '🔍 Μόνο Αδιάβαστα';
    btn.style.background = showOnlyUncovered ? '#e63946' : '#2c6496';
  }
  renderFormulas();
}

// ── RENDER ────────────────────────────────────────────────────────────────────
function init() {
  // Priority: URL hash > localStorage > empty
  if (!loadFromHash()) loadState();
  // Clear hash from URL to keep it clean (but keep share URL intact for user)
  renderAll();
}

function renderAll() {
  renderChapterButtons();
  renderFormulas();
  updateProgress();
}

function renderChapterButtons() {
  const container = document.getElementById('chapterButtons');
  container.innerHTML = '';
  CHAPTERS.forEach(ch => {
    const btn = document.createElement('button');
    btn.className = 'chapter-btn' + (selectedChapters.has(ch.id) ? ' active' : '');
    btn.textContent = ch.shortTitle + ' (' + ch.dw + ' ΔΩ)';
    btn.onclick = () => toggleChapter(ch.id);
    container.appendChild(btn);
  });
  const allBtn = document.createElement('button');
  const allSelected = selectedChapters.size === CHAPTERS.length;
  allBtn.className = 'chapter-btn all-btn' + (allSelected ? ' active' : '');
  allBtn.textContent = "★ Εφ' Όλης της Ύλης";
  allBtn.onclick = toggleAll;
  container.appendChild(allBtn);
}

function toggleChapter(id) {
  if (selectedChapters.has(id)) {
    selectedChapters.delete(id);
    const ch = CHAPTERS.find(c => c.id === id);
    ch.formulas.forEach((_, i) => coveredFormulas.delete(id + '-' + i));
  } else {
    selectedChapters.add(id);
  }
  saveState();
  renderAll();
}

function toggleAll() {
  if (selectedChapters.size === CHAPTERS.length) {
    selectedChapters.clear();
    coveredFormulas.clear();
  } else {
    CHAPTERS.forEach(ch => selectedChapters.add(ch.id));
  }
  saveState();
  renderAll();
}

function toggleFormula(chId, fIdx) {
  const key = chId + '-' + fIdx;
  if (coveredFormulas.has(key)) coveredFormulas.delete(key);
  else coveredFormulas.add(key);
  saveState();
  renderFormulas();
  updateProgress();
}

function updateProgress() {
  let total = 0, covered = 0;
  selectedChapters.forEach(id => {
    const ch = CHAPTERS.find(c => c.id === id);
    total += ch.formulas.length;
    ch.formulas.forEach((_, i) => { if (coveredFormulas.has(id + '-' + i)) covered++; });
  });
  document.getElementById('coveredCount').textContent = covered;
  document.getElementById('totalCount').textContent = total;
  const remaining = total - covered;
  const remEl = document.getElementById('remainingCount');
  if (remEl) remEl.textContent = '(' + remaining + ' αδιάβαστα)';
  const pct = total > 0 ? Math.round(covered / total * 100) : 0;
  document.getElementById('progressBar').style.width = pct + '%';
  document.getElementById('progressPct').textContent = pct + '%';
  document.getElementById('progressArea').style.display = selectedChapters.size > 0 ? 'block' : 'none';
}

function renderFormulas() {
  const area = document.getElementById('formulaArea');
  area.innerHTML = '';

  if (selectedChapters.size === 0) {
    area.innerHTML = '<div class="empty-state"><div class="icon">📚</div><p>Επιλέξτε ένα ή περισσότερα κεφάλαια παραπάνω για να εμφανιστούν οι τύποι</p></div>';
    return;
  }

  let anyVisible = false;
  CHAPTERS.forEach(ch => {
    if (!selectedChapters.has(ch.id)) return;

    const visibleFormulas = ch.formulas.filter((f, i) =>
      !showOnlyUncovered || !coveredFormulas.has(ch.id + '-' + i)
    );
    if (visibleFormulas.length === 0) return;
    anyVisible = true;

    const coveredInChapter = ch.formulas.filter((_, i) => coveredFormulas.has(ch.id + '-' + i)).length;
    const allDone = coveredInChapter === ch.formulas.length;

    const section = document.createElement('div');
    section.className = 'chapter-section' + (allDone ? ' chapter-done' : '');

    const header = document.createElement('div');
    header.className = 'chapter-section-header';
    header.innerHTML =
      '<h3>' + ch.title + ' <span style="opacity:0.6;font-weight:400;font-size:0.85em;">(' + ch.dw + ' ΔΩ)</span></h3>' +
      '<span class="ch-stats">' + coveredInChapter + '/' + ch.formulas.length +
      (allDone ? ' ✅' : ' εξετάστηκαν') + '</span>';
    section.appendChild(header);

    const body = document.createElement('div');
    // Show all formulas but hide covered ones if filter active
    ch.formulas.forEach((f, i) => {
      const key = ch.id + '-' + i;
      const isCovered = coveredFormulas.has(key);
      if (showOnlyUncovered && isCovered) return;

      const row = document.createElement('div');
      row.className = 'formula-row' + (isCovered ? ' covered' : '');
      row.onclick = () => toggleFormula(ch.id, i);

      const mathClass = 'formula-math' + (f.multiline ? ' multi' : '');
      const mathContent = f.multiline
        ? f.latex.split('\\\\').map(l => '\\(' + l.replace(/\[.*?\]/g,'').trim() + '\\)').join('<br>')
        : '\\(' + f.latex + '\\)';

      let nameContent = '<div class="formula-name">' + f.name;
      if (f.proof) nameContent += '<div class="proof-block">📐 ' + f.proof + '</div>';
      nameContent += '</div>';

      row.innerHTML =
        '<div class="formula-check">' + (isCovered ? '✓' : '') + '</div>' +
        nameContent +
        '<div class="' + mathClass + '">' + mathContent + '</div>';
      body.appendChild(row);
    });
    section.appendChild(body);
    area.appendChild(section);
  });

  if (showOnlyUncovered && !anyVisible) {
    area.innerHTML = '<div class="empty-state"><div class="icon">🎉</div><p>Όλοι οι τύποι έχουν εξεταστεί!</p></div>';
  }

  if (window.MathJax) MathJax.typesetPromise([area]).catch(err => console.log(err));
}

function coverAll() {
  selectedChapters.forEach(id => {
    const ch = CHAPTERS.find(c => c.id === id);
    ch.formulas.forEach((_, i) => coveredFormulas.add(id + '-' + i));
  });
  saveState(); renderFormulas(); updateProgress();
}

function uncoverAll() {
  coveredFormulas.clear();
  saveState(); renderFormulas(); updateProgress();
}

function resetSelection() {
  if (!confirm('Να διαγραφεί η τρέχουσα εργασία;')) return;
  selectedChapters.clear();
  coveredFormulas.clear();
  try { localStorage.removeItem(STORAGE_KEY); } catch(e) {}
  renderAll();
}

init();

</script>

---

*Κάντε κλικ σε κάθε τύπο για να τον σημειώσετε ως εξετασμένο. Η εργασία αποθηκεύεται αυτόματα στον browser σας.*
