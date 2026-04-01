---
layout: post
title: "Βοηθός Δημιουργίας Διαγωνίσματος Φυσικής"
description: "Διαδραστικό εργαλείο για εκπαιδευτικούς - παρακολούθηση τύπων ανά κεφάλαιο"
category: Εφαρμογή
tags: [Διαγώνισμα, Φυσική, Εργαλείο]
---

Διαδραστική εφαρμογή για εκπαιδευτικούς Φυσικής Γ'  Λυκείου. Επιλέξτε τα κεφάλαια του διαγωνίσματος και σημειώνετε τους τύπους που έχετε ήδη εξετάσει.

---

<div id="diagwnisma-app">

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
      background: #f0f4ff;
      min-height: 100vh;
      padding: 24px 16px 48px;
      color: #1a1a2e;
    }

    .container { max-width: 960px; margin: 0 auto; }

    .app-header {
      background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%);
      color: white;
      padding: 28px 32px;
      border-radius: 12px;
      margin-bottom: 24px;
      box-shadow: 0 8px 32px rgba(15,52,96,0.3);
    }
    .app-header h1 { font-size: 1.4em; font-weight: 700; letter-spacing: 0.5px; margin-bottom: 6px; }
    .app-header p { opacity: 0.75; font-size: 0.9em; }

    .section-label {
      font-size: 0.78em; font-weight: 700; letter-spacing: 1.5px;
      text-transform: uppercase; color: #0f3460; margin-bottom: 10px;
    }

    .chapters-grid { display: flex; flex-wrap: wrap; gap: 10px; margin-bottom: 20px; }

    .chapter-btn {
      border: 2px solid #0f3460; background: white; color: #0f3460;
      padding: 8px 16px; border-radius: 8px; cursor: pointer;
      font-size: 0.85em; font-weight: 600; transition: all 0.2s; white-space: nowrap;
    }
    .chapter-btn:hover { background: #e8f0fe; }
    .chapter-btn.active { background: #0f3460; color: white; }
    .chapter-btn.all-btn { border-color: #e63946; color: #e63946; }
    .chapter-btn.all-btn:hover { background: #ffeef0; }
    .chapter-btn.all-btn.active { background: #e63946; color: white; }

    .progress-wrap {
      background: #f0f4ff; border-radius: 10px; padding: 14px 18px;
      margin-bottom: 16px; border-left: 4px solid #0f3460;
      display: flex; align-items: center; gap: 16px; flex-wrap: wrap;
    }
    .progress-text { font-size: 0.9em; color: #0f3460; font-weight: 600; min-width: 200px; }
    .progress-bar-outer { flex: 1; min-width: 120px; height: 10px; background: #d0d9f0; border-radius: 5px; overflow: hidden; }
    .progress-bar-inner { height: 100%; background: linear-gradient(90deg, #0f3460, #e63946); border-radius: 5px; transition: width 0.4s ease; width: 0%; }
    .progress-pct { font-size: 0.85em; font-weight: 700; color: #e63946; min-width: 40px; text-align: right; }

    .actions-bar {
      display: flex; gap: 10px; flex-wrap: wrap; margin-bottom: 24px;
      padding: 14px 18px; background: white; border-radius: 10px; border: 1px solid #d8e2f5;
    }
    .action-btn { padding: 8px 16px; border-radius: 7px; border: none; cursor: pointer; font-size: 0.85em; font-weight: 600; transition: all 0.2s; }
    .action-btn.cover-all { background: #f4a100; color: white; }
    .action-btn.cover-all:hover { background: #d08c00; }
    .action-btn.uncover { background: #0f3460; color: white; }
    .action-btn.uncover:hover { background: #0c2a50; }
    .action-btn.reset { background: #e63946; color: white; }
    .action-btn.reset:hover { background: #c0303b; }

    .legend { display: flex; gap: 20px; flex-wrap: wrap; font-size: 0.8em; color: #5a6a8a; margin-bottom: 16px; }
    .legend-item { display: flex; align-items: center; gap: 6px; }
    .legend-dot { width: 14px; height: 14px; border-radius: 3px; flex-shrink: 0; }

    .chapter-section {
      background: white; border: 1px solid #d8e2f5; border-radius: 12px;
      margin-bottom: 20px; overflow: hidden; box-shadow: 0 2px 12px rgba(15,52,96,0.07);
    }
    .chapter-section-header {
      background: linear-gradient(90deg, #0f3460, #1a4a8a);
      color: white; padding: 14px 20px;
      display: flex; justify-content: space-between; align-items: center;
    }
    .chapter-section-header h3 { font-size: 1em; font-weight: 700; color: white; }
    .ch-stats { font-size: 0.8em; opacity: 0.85; background: rgba(255,255,255,0.15); padding: 3px 10px; border-radius: 20px; white-space: nowrap; }

    .formula-row {
      display: flex; align-items: center; padding: 12px 20px;
      border-bottom: 1px solid #eef2fb; transition: background 0.2s;
      gap: 14px; cursor: pointer; user-select: none;
    }
    .formula-row:last-child { border-bottom: none; }
    .formula-row:hover { background: #f7f9ff; }
    .formula-row.covered { background: #fff3cd; }
    .formula-row.covered:hover { background: #ffe9a0; }

    .formula-check {
      width: 22px; height: 22px; border: 2px solid #b0b8d0; border-radius: 5px;
      flex-shrink: 0; display: flex; align-items: center; justify-content: center;
      background: white; transition: all 0.2s; font-size: 14px;
    }
    .formula-row.covered .formula-check { background: #f4a100; border-color: #f4a100; color: white; }

    .formula-name { flex: 1; font-size: 0.9em; color: #2c3e6b; font-weight: 500; }
    .formula-math { font-size: 0.95em; color: #0f3460; min-width: 260px; text-align: right; }
    .formula-row.covered .formula-name { text-decoration: line-through; color: #997000; }
    .formula-row.covered .formula-math { color: #c48c00; }

    .empty-state {
      text-align: center; padding: 48px 24px; color: #7a8cbf;
      background: white; border-radius: 12px; border: 1px solid #d8e2f5;
    }
    .empty-state .icon { font-size: 3em; margin-bottom: 16px; }

    @media (max-width: 600px) {
      .formula-row { flex-wrap: wrap; }
      .formula-math { min-width: unset; text-align: left; width: 100%; padding-left: 36px; }
      .app-header { padding: 20px; }
      .app-header h1 { font-size: 1.15em; }
    }
  </style>

<div class="container">

  <div class="app-header">
    <h1>📋 Βοηθός Δημιουργίας Διαγωνίσματος Φυσικής</h1>
    <p>Επιλέξτε κεφάλαια και σημειώστε τους τύπους που έχετε ήδη εξετάσει</p>
  </div>

  <div class="section-label">Επιλογή Κεφαλαίων</div>
  <div class="chapters-grid" id="chapterButtons"></div>

  <div class="legend">
    <div class="legend-item">
      <div class="legend-dot" style="background:#d8e2f5;border:2px solid #b0b8d0;"></div>
      <span>Δεν εξετάστηκε</span>
    </div>
    <div class="legend-item">
      <div class="legend-dot" style="background:#f4a100;"></div>
      <span>Εξετάστηκε ✓</span>
    </div>
  </div>

  <div id="progressArea" style="display:none">
    <div class="progress-wrap">
      <div class="progress-text">Κάλυψη ύλης: <span id="coveredCount">0</span> / <span id="totalCount">0</span> τύποι</div>
      <div class="progress-bar-outer"><div class="progress-bar-inner" id="progressBar"></div></div>
      <div class="progress-pct" id="progressPct">0%</div>
    </div>
    <div class="actions-bar">
      <button class="action-btn cover-all" onclick="coverAll()">☑ Σημείωση Όλων ως Εξετασμένων</button>
      <button class="action-btn uncover" onclick="uncoverAll()">↺ Αναίρεση Όλων</button>
      <button class="action-btn reset" onclick="resetSelection()">✕ Νέο Διαγώνισμα</button>
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
      { name: "Αρχή Διατήρησης Ορμής", latex: "p_{πριν} = p_{μετά}" },
      { name: "Κεντρική Ελαστική Κρούση (v₁')", latex: "v_1' = \\frac{m_1-m_2}{m_1+m_2}v_1 + \\frac{2m_2}{m_1+m_2}v_2" },
      { name: "Κεντρική Ελαστική Κρούση (v₂')", latex: "v_2' = \\frac{2m_1}{m_1+m_2}v_1 + \\frac{m_2-m_1}{m_1+m_2}v_2" },
      { name: "Ελαστική Κρούση – Ίσες Μάζες, Σ₂ ακίνητη (5.8)", latex: "v_1' = \\frac{m_1-m_2}{m_1+m_2}\\,v_1" },
      { name: "Ελαστική Κρούση – Ίσες Μάζες, Σ₂ ακίνητη (5.9)", latex: "v_2' = \\frac{2m_1}{m_1+m_2}\\,v_1" },
      { name: "Πλαστική Κρούση (Κοινή Ταχύτητα V)", latex: "m_1v_1 + m_2v_2 = (m_1+m_2)V" },
      { name: "Μεταβολή Κινητικής Ενέργειας", latex: "\\Delta K = K_{μετά} - K_{πριν}" },
      { name: "Γωνία Πρόσπτωσης = Γωνία Ανάκλασης", latex: "\\pi = \\alpha" }
    ]
  },
  {
    id: 2,
    title: "2. Μηχανική Στερεού Σώματος",
    shortTitle: "Στερεό",
    dw: 18,
    formulas: [
      { name: "Γραμμική και Γωνιακή Ταχύτητα", latex: "v = \\omega r" },
      { name: "Γωνιακή Επιτάχυνση", latex: "\\alpha_{γων} = \\frac{d\\omega}{dt}" },
      { name: "Επιτάχυνση Κέντρου Μάζας (Κύλιση)", latex: "a_{cm} = \\alpha_{γων} R" },
      { name: "Ροπή Δύναμης (ως προς άξονα)", latex: "\\tau = F \\cdot l" },
      { name: "Στροφορμή Υλικού Σημείου (κυκλική κίνηση)", latex: "L = m\\upsilon r" },
      { name: "Στροφορμή Στερεού Σώματος", latex: "L = I\\omega" },
      { name: "Θεμελιώδης Νόμος Στροφικής Κίνησης", latex: "\\Sigma\\tau = \\frac{dL}{dt}" },
      { name: "Διατήρηση Στροφορμής (αν ΣΤ=0)", latex: "L_{ολ} = \\text{σταθερή}" }
    ]
  },
  {
    id: 3,
    title: "3. Ηλεκτρικές – Μηχανικές Ταλαντώσεις",
    shortTitle: "Ταλαντώσεις",
    dw: 16,
    formulas: [
      { name: "Απομάκρυνση Απλής Αρμονικής Ταλάντωσης (1.1)", latex: "x = A\\,\\eta\\mu\\,\\omega t" },
      { name: "Ταχύτητα Απλής Αρμονικής Ταλάντωσης (1.2)", latex: "\\upsilon = \\upsilon_{max}\\,\\text{συν}\\,\\omega t" },
      { name: "Επιτάχυνση Απλής Αρμονικής Ταλάντωσης (1.3)", latex: "a = -a_{max}\\,\\eta\\mu\\,\\omega t" },
      { name: "Περίοδος και Συχνότητα", latex: "T = \\frac{t}{N} \\text{ και } f = \\frac{1}{T}" },
      { name: "Γωνιακή Συχνότητα", latex: "\\omega = \\frac{2\\pi}{T} = 2\\pi f" },
      { name: "Μέγιστη Ταχύτητα και Επιτάχυνση", latex: "v_{max} = \\omega A \\text{ και } a_{max} = \\omega^2 A" },
      { name: "Δύναμη Επαναφοράς", latex: "\\Sigma F = -m\\omega^2 x = -Dx" },
      { name: "Περίοδος Αρμονικής Ταλάντωσης", latex: "T = 2\\pi\\sqrt{\\frac{m}{D}}" },
      { name: "Ολική Ενέργεια Ταλάντωσης", latex: "E = K + U = \\frac{1}{2}DA^2" },
      { name: "Πλάτος Φθίνουσας Ταλάντωσης", latex: "A = A_0 e^{-\\Lambda t}" },
      { name: "Εξαναγκασμένη Ταλάντωση – Συχνότητα", latex: "f_{ταλάντωσης} = f_{διεγέρτη}" }
    ]
  },
  {
    id: 4,
    title: "4. Κύματα",
    shortTitle: "Κύματα",
    dw: 16,
    formulas: [
      { name: "Ταχύτητα Διάδοσης Κύματος", latex: "v = \\frac{x}{t}" },
      { name: "Θεμελιώδης Εξίσωση Κυματικής", latex: "v = \\lambda f = \\frac{\\lambda}{T}" },
      { name: "Εξίσωση Στιγμιότυπου Κύματος", latex: "y = A\\sin\\frac{2\\pi}{\\lambda}x" },
      { name: "Εξίσωση Αρμονικού Κύματος", latex: "y = A\\sin 2\\pi\\!\\left(\\frac{t}{T} \\mp \\frac{x}{\\lambda}\\right)" },
      { name: "Ενισχυτική Συμβολή (σε επιφάνεια υγρού)", latex: "r_1 - r_2 = N\\lambda" },
      { name: "Αποσβεστική Συμβολή (σε επιφάνεια υγρού)", latex: "r_1 - r_2 = (2N+1)\\frac{\\lambda}{2}" },
      { name: "Εξίσωση Στάσιμου Κύματος", latex: "y = 2A\\cos\\!\\left(2\\pi\\frac{x}{\\lambda}\\right)\\sin\\!\\left(2\\pi\\frac{t}{T}\\right)" },
      { name: "Ένταση Ηλεκτρικού και Μαγνητικού Πεδίου", latex: "\\frac{E}{B} = c" }
    ]
  },
  {
    id: 5,
    title: "5. Μαγνητικό Πεδίο",
    shortTitle: "Μαγνητικό Πεδίο",
    dw: 23,
    formulas: [
      { name: "Νόμος Biot-Savart", latex: "\\Delta B = \\frac{\\mu_0}{4\\pi}\\frac{I\\Delta l\\sin\\theta}{r^2}" },
      { name: "Ένταση Πεδίου Ευθύγραμμου Αγωγού", latex: "B = \\frac{\\mu_0}{4\\pi}\\frac{2I}{a}" },
      { name: "Ένταση Πεδίου Κυκλικού Αγωγού (κέντρο)", latex: "B = \\frac{\\mu_0}{4\\pi}\\frac{2\\pi I}{r}" },
      { name: "Ένταση Πεδίου Σωληνοειδούς", latex: "B = \\mu_0 I n" },
      { name: "Νόμος του Ampere", latex: "\\Sigma B\\Delta l\\cos\\theta = \\mu_0 I_{εγκ}" },
      { name: "Μαγνητική Ροή", latex: "\\Phi = BA\\cos\\theta" },
      { name: "Δύναμη Lorentz (σε φορτίο)", latex: "F = Bvq\\sin\\theta" },
      { name: "Ακτίνα Κυκλικής Τροχιάς Φορτίου", latex: "R = \\frac{mv}{B|q|}" },
      { name: "Περίοδος Περιστροφής σε Μαγνητικό Πεδίο (4.12)", latex: "T = \\frac{2\\pi m}{B|q|}" },
      { name: "Βήμα Έλικας", latex: "\\beta = \\upsilon_{\\parallel}\\cdot T = \\upsilon_{\\parallel}\\frac{2\\pi m}{B|q|}" },
      { name: "Δύναμη Laplace (σε αγωγό)", latex: "F = BIl\\sin\\phi" },
      { name: "Δύναμη μεταξύ Παράλληλων Αγωγών", latex: "\\frac{F}{l} = \\frac{\\mu_0}{4\\pi}\\frac{2I_1 I_2}{a}" }
    ]
  },
  {
    id: 6,
    title: "6. Επαγωγή",
    shortTitle: "Επαγωγή",
    dw: 22,
    formulas: [
      { name: "Νόμος της Επαγωγής (Faraday)", latex: "E_{ind} = -N\\frac{\\Delta\\Phi}{\\Delta t}" },
      { name: "Επαγωγικό Φορτίο", latex: "q = N\\frac{\\Delta\\Phi}{R}" },
      { name: "ΗΕΔ σε Κινούμενο Αγωγό", latex: "E = BLv" },
      { name: "ΗΕΔ σε Στρεφόμενο Αγωγό", latex: "E = \\frac{1}{2}BL^2\\omega" },
      { name: "Εναλλασσόμενη Τάση (Πλάτος)", latex: "V = NBA\\omega" },
      { name: "Ενεργές Τιμές Τάσης και Ρεύματος", latex: "V_{εν} = \\frac{V}{\\sqrt{2}} \\text{ και } I_{εν} = \\frac{I}{\\sqrt{2}}" },
      { name: "ΗΕΔ Αυτεπαγωγής", latex: "E_{αυτ} = -L\\frac{di}{dt}" },
      { name: "Ενέργεια Μαγνητικού Πεδίου Πηνίου", latex: "U = \\frac{1}{2}LI^2" }
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
      { name: "Ενέργεια Φωτονίου", latex: "E = hf = \\frac{hc}{\\lambda}" },
      { name: "Φωτοηλεκτρική Εξίσωση Einstein", latex: "K_{max} = hf - \\phi" },
      { name: "Ορμή Φωτονίου", latex: "p = \\frac{E}{c} = \\frac{h}{\\lambda}" },
      { name: "Φαινόμενο Compton", latex: "\\lambda' - \\lambda = \\frac{h}{mc}(1 - \\cos\\phi)" },
      { name: "Κύματα de Broglie", latex: "\\lambda = \\frac{h}{p}" },
      { name: "Αρχή Αβεβαιότητας", latex: "\\Delta x \\cdot \\Delta p_x \\geq \\frac{h}{4\\pi}" }
    ]
  }
];

let selectedChapters = new Set();
let coveredFormulas = new Set();

function init() {
  renderChapterButtons();
  renderFormulas();
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
  renderChapterButtons();
  renderFormulas();
  updateProgress();
}

function toggleAll() {
  if (selectedChapters.size === CHAPTERS.length) {
    selectedChapters.clear();
    coveredFormulas.clear();
  } else {
    CHAPTERS.forEach(ch => selectedChapters.add(ch.id));
  }
  renderChapterButtons();
  renderFormulas();
  updateProgress();
}

function toggleFormula(chId, fIdx) {
  const key = chId + '-' + fIdx;
  if (coveredFormulas.has(key)) coveredFormulas.delete(key);
  else coveredFormulas.add(key);
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

  CHAPTERS.forEach(ch => {
    if (!selectedChapters.has(ch.id)) return;
    const coveredInChapter = ch.formulas.filter((_, i) => coveredFormulas.has(ch.id + '-' + i)).length;

    const section = document.createElement('div');
    section.className = 'chapter-section';

    const header = document.createElement('div');
    header.className = 'chapter-section-header';
    header.innerHTML =
      '<h3>' + ch.title + ' <span style="opacity:0.6;font-weight:400;font-size:0.85em;">(' + ch.dw + ' ΔΩ)</span></h3>' +
      '<span class="ch-stats">' + coveredInChapter + '/' + ch.formulas.length + ' εξετάστηκαν</span>';
    section.appendChild(header);

    const body = document.createElement('div');
    ch.formulas.forEach((f, i) => {
      const key = ch.id + '-' + i;
      const isCovered = coveredFormulas.has(key);
      const row = document.createElement('div');
      row.className = 'formula-row' + (isCovered ? ' covered' : '');
      row.onclick = () => toggleFormula(ch.id, i);
      row.innerHTML =
        '<div class="formula-check">' + (isCovered ? '✓' : '') + '</div>' +
        '<div class="formula-name">' + f.name + '</div>' +
        '<div class="formula-math">\\(' + f.latex + '\\)</div>';
      body.appendChild(row);
    });
    section.appendChild(body);
    area.appendChild(section);
  });

  if (window.MathJax) {
    MathJax.typesetPromise([area]).catch(err => console.log(err));
  }
}

function coverAll() {
  selectedChapters.forEach(id => {
    const ch = CHAPTERS.find(c => c.id === id);
    ch.formulas.forEach((_, i) => coveredFormulas.add(id + '-' + i));
  });
  renderFormulas();
  updateProgress();
}

function uncoverAll() {
  coveredFormulas.clear();
  renderFormulas();
  updateProgress();
}

function resetSelection() {
  selectedChapters.clear();
  coveredFormulas.clear();
  renderChapterButtons();
  renderFormulas();
  updateProgress();
}

init();
</script>

</div>

---

*Κάντε κλικ σε κάθε τύπο για να τον σημειώσετε ως εξετασμένο.*
