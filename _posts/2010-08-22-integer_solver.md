---
layout: post
title: "Επίλυση Ακεραίου"
description: "Εργαλείο εύρεσης συνδυασμών δεδομένων που μετατρέπουν τα ζητούμενα σε ακέραιους αριθμούς."
category: Εφαρμογή
tags: []
---

Διαδραστική εφαρμογή που βρίσκει συνδυασμούς δεδομένων για τους οποίους οι τιμές των ζητούμενων μεγεθών είναι ακέραιοι αριθμοί.

---

<!-- MathJax -->
<script>
window.MathJax = {
  tex: { inlineMath: [['\\(','\\)']] },
  startup: { ready() { MathJax.startup.defaultReady(); } }
};
</script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/3.2.2/es5/tex-chtml.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/mathjs/12.4.1/math.min.js"></script>

{% raw %}
<style>
/* ── Reset & Base ── */
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

:root {
  --bg:        #f8f8f6;
  --surface:   #ffffff;
  --surface2:  #f1f0ec;
  --border:    #e0deda;
  --border2:   #c8c6c0;
  --text:      #1a1a18;
  --text2:     #6b6a66;
  --text3:     #9e9d99;
  --blue:      #1a5fd4;
  --blue-bg:   #e8f0fc;
  --blue-bdr:  #a8c0f0;
  --amber:     #a06010;
  --amber-bg:  #fef3e0;
  --amber-bdr: #f0c870;
  --green:     #1a7a40;
  --green-bg:  #e6f5ec;
  --green-bdr: #80c8a0;
  --red:       #c0281e;
  --red-bg:    #fdecea;
  --red-bdr:   #f0a8a4;
  --info-bg:   #e8f0fc;
  --info-text: #1a5fd4;
  --radius:    8px;
  --radius-lg: 12px;
}

body {
  font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
  background: var(--bg);
  color: var(--text);
  font-size: 15px;
  line-height: 1.6;
  min-height: 100vh;
}

.container {
  max-width: 860px;
  margin: 0 auto;
  padding: 2rem 1.5rem;
}

h1 {
  font-size: 22px;
  font-weight: 600;
  margin-bottom: 4px;
  color: var(--text);
}
.subtitle {
  font-size: 14px;
  color: var(--text2);
  margin-bottom: 2rem;
}

/* ── Step bar ── */
.step-bar {
  display: flex;
  border-radius: var(--radius);
  overflow: hidden;
  border: 1px solid var(--border);
  margin-bottom: 2rem;
}
.stp {
  flex: 1;
  padding: 10px 8px;
  text-align: center;
  font-size: 13px;
  color: var(--text2);
  background: var(--surface2);
  cursor: pointer;
  border-right: 1px solid var(--border);
  transition: background .15s;
  user-select: none;
}
.stp:last-child { border-right: none; }
.stp:hover { background: #e8e7e3; }
.stp.active { background: var(--text); color: #fff; font-weight: 600; }
.stp.done { background: var(--green-bg); color: var(--green); }

/* ── Sections ── */
.section {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: var(--radius-lg);
  padding: 1.5rem;
  margin-bottom: 1rem;
}
.sec-title {
  font-size: 11px;
  font-weight: 600;
  color: var(--text2);
  text-transform: uppercase;
  letter-spacing: .07em;
  margin-bottom: 1rem;
}

/* ── Inputs ── */
label { font-size: 14px; color: var(--text2); }

input[type=text], input[type=number], select {
  font-size: 14px;
  padding: 8px 11px;
  border-radius: var(--radius);
  border: 1px solid var(--border2);
  background: var(--surface2);
  color: var(--text);
  outline: none;
  transition: border-color .15s, box-shadow .15s;
}
input[type=text]:focus, input[type=number]:focus, select:focus {
  border-color: var(--blue);
  box-shadow: 0 0 0 3px rgba(26,95,212,.12);
}
input[type=text] { width: 100%; }
input[type=number] { width: 78px; }
input.unit-inp { width: 90px; font-size: 13px; padding: 5px 8px; }
input.wide { width: 100%; }

/* ── Buttons ── */
.btn {
  font-size: 13px;
  font-weight: 500;
  padding: 8px 18px;
  border-radius: var(--radius);
  border: 1px solid var(--border2);
  background: transparent;
  color: var(--text);
  cursor: pointer;
  transition: background .12s;
}
.btn:hover { background: var(--surface2); }
.btn-p {
  background: var(--text);
  color: #fff;
  border-color: transparent;
}
.btn-p:hover { background: #2d2d2b; }
.btn-d { color: var(--red); border-color: var(--red-bdr); }
.btn-d:hover { background: var(--red-bg); }
.btn-sel {
  font-size: 12px;
  padding: 4px 12px;
  border-radius: var(--radius);
  border: 1px solid var(--blue-bdr);
  background: transparent;
  color: var(--blue);
  cursor: pointer;
}
.btn-sel:hover { background: var(--blue-bg); }

/* ── Tags ── */
.tag {
  display: inline-block;
  font-size: 12px;
  padding: 2px 10px;
  border-radius: 99px;
  background: var(--blue-bg);
  color: var(--blue);
  border: 1px solid var(--blue-bdr);
}
.tag.unk { background: var(--amber-bg); color: var(--amber); border-color: var(--amber-bdr); }
.tag.angle { background: var(--green-bg); color: var(--green); border-color: var(--green-bdr); }

/* ── Equation blocks ── */
.eq-block {
  background: var(--surface2);
  border-radius: var(--radius);
  padding: 14px;
  margin-bottom: 10px;
  border: 1px solid var(--border);
}
.eq-row { display: flex; gap: 8px; align-items: center; margin-bottom: 8px; }
.eq-row label { min-width: 60px; font-size: 13px; }
.eq-row input[type=text] { font-family: 'Courier New', monospace; font-size: 13px; }

.preview {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  padding: 8px 14px;
  min-height: 40px;
  font-size: 16px;
  margin-top: 6px;
}
.mjs-preview {
  font-family: 'Courier New', monospace;
  font-size: 12px;
  color: var(--text2);
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  padding: 6px 10px;
  margin-top: 4px;
  word-break: break-all;
}
.mjs-preview.ok { color: var(--green); }
.mjs-preview.err { color: var(--red); }

/* ── Status messages ── */
.status {
  font-size: 13px;
  padding: 8px 14px;
  border-radius: var(--radius);
  background: var(--info-bg);
  color: var(--info-text);
  border: 1px solid var(--blue-bdr);
  margin-top: 8px;
}
.status.err { background: var(--red-bg); color: var(--red); border-color: var(--red-bdr); }
.truncated-note {
  font-size: 12px;
  color: var(--amber);
  background: var(--amber-bg);
  border-radius: var(--radius);
  padding: 7px 12px;
  margin-top: 8px;
  border: 1px solid var(--amber-bdr);
}

/* ── Range table ── */
.rt { width: 100%; border-collapse: collapse; }
.rt th {
  font-size: 12px;
  font-weight: 600;
  color: var(--text2);
  text-align: left;
  padding: 6px 8px;
  border-bottom: 1px solid var(--border);
}
.rt td { padding: 7px 8px; border-bottom: 1px solid var(--border); vertical-align: middle; }
.rt tr:last-child td { border-bottom: none; }

/* ── Type toggle ── */
.type-toggle {
  display: flex;
  border-radius: var(--radius);
  overflow: hidden;
  border: 1px solid var(--border2);
}
.type-toggle button {
  flex: 1;
  padding: 5px 10px;
  font-size: 12px;
  border: none;
  background: transparent;
  color: var(--text2);
  cursor: pointer;
  transition: background .12s;
}
.type-toggle button:hover { background: var(--surface2); }
.type-toggle button.on { background: var(--text); color: #fff; font-weight: 500; }

/* ── Total box ── */
.total-box {
  font-size: 13px;
  color: var(--text2);
  background: var(--surface2);
  border-radius: var(--radius);
  padding: 8px 14px;
  margin-top: 12px;
  border: 1px solid var(--border);
}
.total-box strong { color: var(--text); }

/* ── Limit row ── */
.limit-row {
  display: flex;
  align-items: center;
  gap: 10px;
  background: var(--surface2);
  border-radius: var(--radius);
  padding: 10px 14px;
  margin-bottom: 1rem;
  border: 1px solid var(--border);
  flex-wrap: wrap;
}
.limit-row label { font-size: 13px; color: var(--text2); }
.limit-note { font-size: 12px; color: var(--text3); }

/* ── Results table ── */
table.res { width: 100%; font-size: 13px; border-collapse: collapse; margin-top: 10px; }
table.res th {
  text-align: left;
  font-weight: 600;
  font-size: 12px;
  color: var(--text2);
  border-bottom: 1px solid var(--border);
  padding: 6px 10px;
  background: var(--surface2);
}
table.res td { padding: 7px 10px; border-bottom: 1px solid var(--border); font-family: 'Courier New', monospace; }
table.res tr.res-row { cursor: pointer; transition: background .1s; }
table.res tr.res-row:hover td { background: var(--blue-bg); }
table.res tr.res-row.selected td { background: var(--blue-bg); color: var(--blue); font-weight: 600; }

/* ── Progress ── */
progress {
  width: 100%;
  height: 6px;
  border-radius: 3px;
  margin-top: 8px;
  appearance: none;
  -webkit-appearance: none;
  border: none;
  background: var(--border);
  overflow: hidden;
}
progress::-webkit-progress-bar { background: var(--border); }
progress::-webkit-progress-value { background: var(--text); border-radius: 3px; }
progress::-moz-progress-bar { background: var(--text); border-radius: 3px; }

/* ── Solution card ── */
.solution-card {
  margin-top: 1.5rem;
  background: var(--surface);
  border-radius: var(--radius-lg);
  border: 1px solid var(--border);
  overflow: hidden;
}
.sol-header {
  font-size: 12px;
  font-weight: 600;
  color: var(--text2);
  text-transform: uppercase;
  letter-spacing: .07em;
  padding: 10px 18px;
  border-bottom: 1px solid var(--border);
  background: var(--surface2);
}
.sol-table { width: 100%; border-collapse: collapse; }
.sol-table td { padding: 10px 18px; border-bottom: 1px solid var(--border); font-size: 16px; }
.sol-table tr:last-child td { border-bottom: none; }
.sol-table .sol-var { font-family: 'Courier New', monospace; font-weight: 600; color: var(--text2); width: 90px; }
.sol-table .sol-eq { color: var(--text3); width: 28px; text-align: center; }
.sol-table .sol-val { font-family: 'Courier New', monospace; font-weight: 700; font-size: 20px; }
.sol-table .sol-unit { font-size: 14px; color: var(--text2); padding-left: 8px; }
.sol-table tr.sol-divider td {
  background: var(--surface2);
  padding: 5px 18px;
  border-bottom: 1px solid var(--border);
}
.sol-table tr.sol-divider td span {
  font-size: 11px;
  font-weight: 600;
  color: var(--text3);
  text-transform: uppercase;
  letter-spacing: .07em;
}
.sol-table tr.sol-known .sol-val { color: var(--blue); }
.sol-table tr.sol-unknown .sol-val { color: var(--green); }

.hidden { display: none; }

/* ── Hint ── */
.hint { font-size: 13px; color: var(--text2); line-height: 1.7; }
.hint code {
  font-family: 'Courier New', monospace;
  font-size: 12px;
  background: var(--surface2);
  padding: 1px 6px;
  border-radius: 4px;
  border: 1px solid var(--border);
}

/* ── Row helpers ── */
.flex-row { display: flex; gap: 10px; align-items: center; }
.flex-row label { min-width: 170px; }

/* ── Units section ── */
#unitsSection { margin-top: 20px; padding-top: 20px; border-top: 1px solid var(--border); }

/* ── Nav row ── */
.nav-row { display: flex; justify-content: space-between; align-items: center; margin-top: 1.25rem; }

@media (max-width: 600px) {
  .step-bar { flex-wrap: wrap; }
  .stp { min-width: 50%; border-right: none; border-bottom: 1px solid var(--border); }
  .limit-row { flex-direction: column; align-items: flex-start; }
}
</style>


<div class="container">
  <h1>Επίλυση Ακεραίου</h1>
  <p class="subtitle">Βρες συνδυασμούς δεδομένων που κάνουν τα ζητούμενα ακέραιους αριθμούς.</p>

  <!-- Step bar -->
  <div class="step-bar">
    <div class="stp active" id="stp1" onclick="goStep(1)">1. Μεταβλητές</div>
    <div class="stp" id="stp2" onclick="goStep(2)">2. Εξισώσεις</div>
    <div class="stp" id="stp3" onclick="goStep(3)">3. Εύρη &amp; Αναζήτηση</div>
    <div class="stp" id="stp4" onclick="goStep(4)">4. Αποτελέσματα</div>
  </div>

  <!-- ════════════════════ STEP 1 ════════════════════ -->
  <div id="step1">
    <div class="section">
      <div class="sec-title">Ορισμός μεταβλητών</div>

      <div style="margin-bottom:14px">
        <label>Δεδομένα (γνωστά) — χωρισμένα με κόμμα</label>
        <input type="text" id="knownVars" placeholder="π.χ.  m, θ, c" oninput="parseVars()" style="margin-top:6px"/>
        <div id="knownTags" style="display:flex;gap:6px;flex-wrap:wrap;margin-top:8px"></div>
      </div>

      <div style="margin-bottom:14px">
        <label>Ζητούμενα (άγνωστα) — χωρισμένα με κόμμα</label>
        <input type="text" id="unknownVars" placeholder="π.χ.  x, y" oninput="parseVars()" style="margin-top:6px"/>
        <div id="unknownTags" style="display:flex;gap:6px;flex-wrap:wrap;margin-top:8px"></div>
      </div>

      <div id="unitsSection" style="display:none">
        <div class="sec-title">Μονάδες μέτρησης (προαιρετικά)</div>
        <table class="rt" id="unitsTable">
          <thead><tr>
            <th>Μεταβλητή</th>
            <th>Μονάδα</th>
            <th style="font-size:11px;color:var(--text3)">π.χ. m, kg, °, rad, N/m² …</th>
          </tr></thead>
          <tbody id="unitsBody"></tbody>
        </table>
      </div>

      <div class="nav-row">
        <span></span>
        <button class="btn btn-p" onclick="goStep(2)">Επόμενο →</button>
      </div>
    </div>
  </div>

  <!-- ════════════════════ STEP 2 ════════════════════ -->
  <div id="step2" class="hidden">
    <div class="section">
      <div class="sec-title">Εξισώσεις σε LaTeX</div>
      <div class="hint" style="margin-bottom:14px">
        Γράψε κάθε εξίσωση σε LaTeX της μορφής <code>ζητούμενο = έκφραση</code>.
        Το δεξί μέλος μετατρέπεται αυτόματα σε υπολογισμό.<br>
        Παραδείγματα: <code>\frac{2m}{\sin(\theta)}</code> &nbsp;·&nbsp;
        <code>\sqrt{a^2+b^2}</code> &nbsp;·&nbsp; <code>a \cdot b + c</code>
      </div>
      <div id="eqList"></div>
      <button class="btn" onclick="addEq()" style="width:100%;margin-top:6px">+ Προσθήκη εξίσωσης</button>
      <div class="nav-row">
        <button class="btn" onclick="goStep(1)">← Πίσω</button>
        <button class="btn btn-p" onclick="goStep(3)">Επόμενο →</button>
      </div>
    </div>
  </div>

  <!-- ════════════════════ STEP 3 ════════════════════ -->
  <div id="step3" class="hidden">
    <div id="refineNotice" style="display:none;background:var(--amber-bg);border:1px solid var(--amber-bdr);border-radius:var(--radius);padding:10px 16px;margin-bottom:1rem;font-size:13px;color:var(--amber)">
      Οι μεταβλητές, ζητούμενα και εξισώσεις παραμένουν αναλλοίωτα — μπορείς να αλλάξεις μόνο τα εύρη και τα βήματα.
    </div>
    <div class="section">
      <div class="sec-title">Εύρος αναζήτησης ανά μεταβλητή</div>
      <div class="hint" style="margin-bottom:14px">
        Για γωνίες επίλεξε <strong>Γωνία (rad)</strong> — εύρος και βήμα ως πολλαπλάσια του π.
      </div>
      <table class="rt">
        <thead><tr>
          <th style="min-width:90px">Μεταβλητή</th>
          <th>Τύπος</th>
          <th>Από</th>
          <th>Έως</th>
          <th>Βήμα</th>
          <th style="min-width:70px">Τιμές</th>
        </tr></thead>
        <tbody id="rangeBody"></tbody>
      </table>
      <div class="total-box" id="totalBox" style="display:none">
        Σύνολο συνδυασμών προς έλεγχο: <strong id="totalCount">—</strong>
      </div>
    </div>

    <div class="section">
      <div class="sec-title">Εμφάνιση αποτελεσμάτων</div>
      <div class="limit-row">
        <label>Εμφάνισε τους πρώτους
          <input type="number" id="maxRes" value="20" min="1" max="10000" style="width:68px;margin:0 6px"/>
          συνδυασμούς που θα βρεθούν
        </label>
        <span class="limit-note">— η αναζήτηση ελέγχει <em>όλους</em> τους συνδυασμούς πάντα</span>
      </div>
      <div class="nav-row">
        <button class="btn" onclick="goStep(2)">← Πίσω</button>
        <button class="btn btn-p" id="searchBtn" onclick="runSearch()">▶ Εκκίνηση αναζήτησης</button>
      </div>
      <div id="sStatus" style="display:none"></div>
      <progress id="prog" value="0" max="100" style="display:none"/>
    </div>
  </div>

  <!-- ════════════════════ STEP 4 ════════════════════ -->
  <div id="step4" class="hidden">
    <div class="section">
      <div class="sec-title">
        Αποτελέσματα
        <span id="foundBadge"></span>
      </div>
      <div id="resultsArea"></div>
      <div id="solutionArea"></div>
      <div class="nav-row">
        <button class="btn btn-p" onclick="resetAll()">+ Νέα αναζήτηση</button>
        <button class="btn" onclick="goStep(3, true)" style="display:flex;align-items:center;gap:6px">
          <svg width="14" height="14" viewBox="0 0 14 14" fill="none" style="flex-shrink:0">
            <path d="M2 7a5 5 0 1 1 1.5 3.6" stroke="currentColor" stroke-width="1.4" stroke-linecap="round"/>
            <path d="M2 10.5V7h3.5" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
          Τροποποίηση εύρους / βήματος
        </button>
      </div>
    </div>
  </div>

</div><!-- /container -->

<script>
/* ════════════════════════════════════════════════
   STATE
════════════════════════════════════════════════ */
let knownList = [], unknownList = [], eqCount = 0;
let equations = [], allResults = [];
const units = {};

/* ════════════════════════════════════════════════
   ANGLE PRESETS
════════════════════════════════════════════════ */
const ANGLE_PRESETS = [
  {label:'0',        v:0},
  {label:'π/12',     v:Math.PI/12},
  {label:'π/8',      v:Math.PI/8},
  {label:'π/6',      v:Math.PI/6},
  {label:'π/4',      v:Math.PI/4},
  {label:'π/3',      v:Math.PI/3},
  {label:'5π/12',    v:5*Math.PI/12},
  {label:'π/2',      v:Math.PI/2},
  {label:'7π/12',    v:7*Math.PI/12},
  {label:'2π/3',     v:2*Math.PI/3},
  {label:'3π/4',     v:3*Math.PI/4},
  {label:'5π/6',     v:5*Math.PI/6},
  {label:'11π/12',   v:11*Math.PI/12},
  {label:'π',        v:Math.PI},
];

function angleSelect(cls, defIdx) {
  return `<select class="${cls}" style="width:90px" onchange="updateTotals()">
    ${ANGLE_PRESETS.map((p,i) => `<option value="${i}"${i==defIdx?' selected':''}>${p.label}</option>`).join('')}
  </select>`;
}

/* ════════════════════════════════════════════════
   STEP NAVIGATION
════════════════════════════════════════════════ */
function goStep(n, fromResults) {
  for (let i = 1; i <= 4; i++) {
    document.getElementById('step'+i).classList.toggle('hidden', i !== n);
    const s = document.getElementById('stp'+i);
    s.classList.remove('active','done');
    if (i < n) s.classList.add('done');
    else if (i === n) s.classList.add('active');
  }
  if (n === 2 && document.getElementById('eqList').children.length === 0) addEq();
  if (n === 3) {
    buildRangeTable();
    const notice = document.getElementById('refineNotice');
    notice.style.display = fromResults ? 'block' : 'none';
  }
}

/* ════════════════════════════════════════════════
   STEP 1 — VARIABLES & UNITS
════════════════════════════════════════════════ */
function parseVars() {
  knownList   = document.getElementById('knownVars').value.split(',').map(s=>s.trim()).filter(Boolean);
  unknownList = document.getElementById('unknownVars').value.split(',').map(s=>s.trim()).filter(Boolean);
  document.getElementById('knownTags').innerHTML   = knownList.map(v=>`<span class="tag">${v}</span>`).join('');
  document.getElementById('unknownTags').innerHTML = unknownList.map(v=>`<span class="tag unk">${v}</span>`).join('');
  buildUnitsTable();
}

function buildUnitsTable() {
  const allVars = [...knownList, ...unknownList];
  const sec = document.getElementById('unitsSection');
  sec.style.display = allVars.length ? 'block' : 'none';
  const tbody = document.getElementById('unitsBody');
  tbody.innerHTML = '';
  allVars.forEach(v => {
    const existing = units[v] || '';
    const tr = document.createElement('tr');
    tr.innerHTML = `
      <td><span class="tag ${unknownList.includes(v)?'unk':''}">${v}</span></td>
      <td><input class="unit-inp" type="text" placeholder="π.χ. kg" value="${existing}"
          oninput="units['${v}']=this.value.trim()"/></td>
      <td style="font-size:12px;color:var(--text3)">αφήστε κενό αν δεν υπάρχει μονάδα</td>
    `;
    tbody.appendChild(tr);
  });
}

/* ════════════════════════════════════════════════
   STEP 2 — EQUATIONS
════════════════════════════════════════════════ */
function addEq() {
  eqCount++;
  const id = 'eq' + eqCount;
  const unk = unknownList[eqCount-1] || '?';
  const div = document.createElement('div');
  div.className = 'eq-block'; div.id = id;
  div.innerHTML = `
    <div class="eq-row">
      <label style="font-size:12px;min-width:60px;color:var(--text2)">Εξίσωση ${eqCount}</label>
      <span class="tag unk" style="font-size:12px">${unk}</span>
      <span style="font-size:13px;color:var(--text2);margin-left:6px">= f(δεδομένων)</span>
      <button class="btn btn-d" onclick="removeEq('${id}')"
        style="margin-left:auto;padding:3px 10px;font-size:12px">✕</button>
    </div>
    <div class="eq-row">
      <label style="min-width:60px">LaTeX</label>
      <input type="text" class="wide" id="${id}_l"
        placeholder="π.χ.  \\frac{2m}{\\sin(\\theta)}" oninput="updateEq('${id}')"/>
    </div>
    <div class="preview" id="${id}_p" style="min-height:36px;color:var(--text3);font-size:13px">preview LaTeX…</div>
    <div class="mjs-preview" id="${id}_j">— γράψε LaTeX παραπάνω —</div>
  `;
  document.getElementById('eqList').appendChild(div);
}

function removeEq(id) { document.getElementById(id)?.remove(); }

function updateEq(id) {
  const latex  = document.getElementById(id+'_l').value;
  const prev   = document.getElementById(id+'_p');
  const jprev  = document.getElementById(id+'_j');
  if (!latex) {
    prev.innerHTML = 'preview LaTeX…'; prev.style.color='var(--text3)';
    jprev.textContent = '—'; jprev.className = 'mjs-preview'; return;
  }
  prev.style.color = '';
  prev.innerHTML = `\\(${latex}\\)`;
  if (window.MathJax && MathJax.typesetPromise) MathJax.typesetPromise([prev]);
  let rhs = latex;
  const ei = latex.indexOf('=');
  if (ei >= 0) rhs = latex.slice(ei+1).trim();
  const mjs = latexToMathjs(rhs);
  const t = tryEval(mjs);
  jprev.textContent = `Έκφραση: ${mjs}` + (t.ok ? '' : `  ← σφάλμα: ${t.err}`);
  jprev.className = 'mjs-preview ' + (t.ok ? 'ok' : 'err');
}

function collectEquations() {
  equations = [];
  document.querySelectorAll('.eq-block').forEach((b, i) => {
    const latex = document.getElementById(b.id+'_l').value;
    let rhs = latex;
    const ei = latex.indexOf('=');
    if (ei >= 0) rhs = latex.slice(ei+1).trim();
    equations.push({ latex, mjs: latexToMathjs(rhs), unknown: unknownList[i] || ('u'+(i+1)) });
  });
}

/* ════════════════════════════════════════════════
   LaTeX → mathjs converter
════════════════════════════════════════════════ */
function latexToMathjs(raw) {
  let s = raw.trim();
  s = s.replace(/\\left|\\right|\\[Bb]ig[lr]?/g, '');
  s = s.replace(/\\[,;!]|\\quad|\\qquad/g, ' ');

  function repFrac(str) {
    let r = str, ch = true;
    while (ch) {
      ch = false;
      r = r.replace(
        /\\frac\s*\{((?:[^{}]|\{[^{}]*\})*)\}\s*\{((?:[^{}]|\{[^{}]*\})*)\}/g,
        (_, n, d) => { ch = true; return `(${latexToMathjs(n)})/(${latexToMathjs(d)})`; }
      );
    }
    return r;
  }
  s = repFrac(s);

  s = s.replace(/\\sqrt\s*\[([^\]]+)\]\s*\{((?:[^{}]|\{[^{}]*\})*)\}/g,
    (_, n, x) => `(${latexToMathjs(x)})^(1/(${latexToMathjs(n)}))`);
  s = s.replace(/\\sqrt\s*\{((?:[^{}]|\{[^{}]*\})*)\}/g,
    (_, x) => `sqrt(${latexToMathjs(x)})`);

  ['sin','cos','tan','cot','sec','csc','ln','log','exp',
   'arcsin','arccos','arctan','sinh','cosh','tanh'].forEach(f => {
    s = s.replace(new RegExp('\\\\'+f+'\\s*\\{((?:[^{}]|\\{[^{}]*\\})*)\\}','g'),
      (_, x) => `${f}(${latexToMathjs(x)})`);
    s = s.replace(new RegExp('\\\\'+f+'\\b','g'), f);
  });

  s = s.replace(/\\pi\b/g, 'pi');
  s = s.replace(/\\e\b/g,  'e');
  s = s.replace(/\\cdot|\\times/g, '*');
  s = s.replace(/\^\s*\{((?:[^{}]|\{[^{}]*\})*)\}/g, (_, e) => `^(${latexToMathjs(e)})`);
  s = s.replace(/\\text\s*\{[^{}]*\}/g, '');
  s = s.replace(/\{/g,'(').replace(/\}/g,')');
  s = s.replace(/([0-9])\s*([a-zA-Zα-ωΑ-Ω_])/g, '$1*$2');
  s = s.replace(/([0-9])\s*\(/g, '$1*(');
  s = s.replace(/\)\s*([a-zA-Zα-ωΑ-Ω_0-9])/g, ')*$1');
  s = s.replace(/\)\s*\(/g, ')*(');
  return s.replace(/\s+/g,' ').trim();
}

function tryEval(e) {
  try {
    const sc = {};
    [...knownList, ...unknownList].forEach(v => sc[v] = 0.5);
    const r = math.evaluate(e, sc);
    return (typeof r === 'number' && isFinite(r)) ? {ok:true} : {ok:false, err:'μη αριθμητικό'};
  } catch(ex) { return {ok:false, err:ex.message}; }
}

/* ════════════════════════════════════════════════
   STEP 3 — RANGES
════════════════════════════════════════════════ */
function buildRangeTable() {
  parseVars();
  const tbody = document.getElementById('rangeBody');
  const existing = {};
  tbody.querySelectorAll('tr[data-var]').forEach(tr => {
    const v = tr.dataset.var;
    const isAngle = tr.dataset.isAngle === '1';
    existing[v] = { isAngle };
    if (isAngle) {
      existing[v].amin  = tr.querySelector('.amin')?.value  ?? '0';
      existing[v].amax  = tr.querySelector('.amax')?.value  ?? '7';
      existing[v].astep = tr.querySelector('.astep')?.value ?? '3';
    } else {
      existing[v].rmin  = tr.querySelector('.rmin')?.value  ?? '1';
      existing[v].rmax  = tr.querySelector('.rmax')?.value  ?? '20';
      existing[v].rstep = tr.querySelector('.rstep')?.value ?? '1';
    }
  });
  tbody.innerHTML = '';
  knownList.forEach(v => {
    const prev = existing[v] || { isAngle: false };
    const tr = document.createElement('tr');
    tr.dataset.var = v;
    tr.dataset.isAngle = prev.isAngle ? '1' : '0';
    const minCell  = prev.isAngle
      ? angleSelect('amin',  parseInt(prev.amin  ?? 0))
      : `<input type="number" class="rmin"  value="${prev.rmin  ?? 1}"  step="any" oninput="updateTotals()"/>`;
    const maxCell  = prev.isAngle
      ? angleSelect('amax',  parseInt(prev.amax  ?? 7))
      : `<input type="number" class="rmax"  value="${prev.rmax  ?? 20}" step="any" oninput="updateTotals()"/>`;
    const stepCell = prev.isAngle
      ? angleSelect('astep', parseInt(prev.astep ?? 3))
      : `<input type="number" class="rstep" value="${prev.rstep ?? 1}"  min="0.001" step="any" oninput="updateTotals()"/>`;
    tr.innerHTML = `
      <td><span class="tag ${prev.isAngle?'angle':''}" id="vtag_${v}">${v}</span></td>
      <td><div class="type-toggle">
        <button class="${prev.isAngle?'':'on'}" onclick="setType('${v}',false,this)">Αριθμός</button>
        <button class="${prev.isAngle?'on':''}" onclick="setType('${v}',true,this)">Γωνία (rad)</button>
      </div></td>
      <td id="cm_${v}">${minCell}</td>
      <td id="cx_${v}">${maxCell}</td>
      <td id="cs_${v}">${stepCell}</td>
      <td id="cc_${v}" style="font-size:12px;color:var(--text2)">—</td>
    `;
    tbody.appendChild(tr);
    updateCount(v);
  });
  updateTotals();
}

function setType(v, isAngle, btn) {
  const tr = document.querySelector(`tr[data-var="${v}"]`);
  tr.dataset.isAngle = isAngle ? '1' : '0';
  btn.parentElement.querySelectorAll('button').forEach(b => b.classList.remove('on'));
  btn.classList.add('on');
  document.getElementById('vtag_'+v).className = 'tag ' + (isAngle ? 'angle' : '');
  document.getElementById('cm_'+v).innerHTML = isAngle ? angleSelect('amin',0)  : `<input type="number" class="rmin" value="1" step="any" oninput="updateTotals()"/>`;
  document.getElementById('cx_'+v).innerHTML = isAngle ? angleSelect('amax',7)  : `<input type="number" class="rmax" value="20" step="any" oninput="updateTotals()"/>`;
  document.getElementById('cs_'+v).innerHTML = isAngle ? angleSelect('astep',3) : `<input type="number" class="rstep" value="1" min="0.001" step="any" oninput="updateTotals()"/>`;
  updateCount(v); updateTotals();
}

function getValsForVar(v) {
  const tr = document.querySelector(`tr[data-var="${v}"]`);
  if (!tr) return [1];
  if (tr.dataset.isAngle === '1') {
    const mi   = parseInt(tr.querySelector('.amin')?.value  || 0);
    const mx   = parseInt(tr.querySelector('.amax')?.value  || 7);
    const si   = parseInt(tr.querySelector('.astep')?.value || 3);
    const step = ANGLE_PRESETS[si].v || (Math.PI/12);
    const minR = ANGLE_PRESETS[mi].v, maxR = ANGLE_PRESETS[mx].v;
    const vals = [];
    for (let x = minR; x <= maxR + 1e-9; x += step) vals.push(Math.round(x * 1e10) / 1e10);
    return vals.length ? vals : [minR];
  }
  const mn = parseFloat(tr.querySelector('.rmin')?.value)  || 1;
  const mx = parseFloat(tr.querySelector('.rmax')?.value)  || 20;
  const st = parseFloat(tr.querySelector('.rstep')?.value) || 1;
  const vals = [];
  for (let x = mn; x <= mx + 1e-9; x += st) vals.push(Math.round(x * 1e5) / 1e5);
  return vals.length ? vals : [mn];
}

function updateCount(v) {
  const el = document.getElementById('cc_'+v);
  if (el) el.textContent = getValsForVar(v).length + ' τιμές';
}

function updateTotals() {
  knownList.forEach(v => updateCount(v));
  if (!knownList.length) { document.getElementById('totalBox').style.display='none'; return; }
  const total = knownList.reduce((a,v) => a * getValsForVar(v).length, 1);
  document.getElementById('totalBox').style.display = 'block';
  document.getElementById('totalCount').textContent = total.toLocaleString('el-GR');
}

function formatVal(val, varName) {
  const tr = document.querySelector(`tr[data-var="${varName}"]`);
  if (tr && tr.dataset.isAngle === '1') {
    let best = null, bestD = Infinity;
    ANGLE_PRESETS.forEach(p => { const d = Math.abs(p.v - val); if (d < bestD) { bestD = d; best = p; } });
    return (best && bestD < 1e-9) ? best.label : val.toFixed(4);
  }
  return val;
}

/* ════════════════════════════════════════════════
   SEARCH
════════════════════════════════════════════════ */
function showSt(msg, type) {
  const el = document.getElementById('sStatus');
  el.className = 'status' + (type ? ' '+type : '');
  el.textContent = msg;
  el.style.display = msg ? 'block' : 'none';
}

function runSearch() {
  parseVars(); collectEquations();
  if (!knownList.length)   { showSt('Ορίστε δεδομένα μεταβλητές.','err'); return; }
  if (!unknownList.length) { showSt('Ορίστε ζητούμενες μεταβλητές.','err'); return; }
  if (equations.length !== unknownList.length) {
    showSt(`Χρειάζεστε ${unknownList.length} εξίσωση(ς) — μία για κάθε ζητούμενο.`,'err'); return;
  }
  for (const eq of equations) {
    const t = tryEval(eq.mjs);
    if (!t.ok) { showSt(`Σφάλμα στην εξίσωση για "${eq.unknown}": ${t.err}`,'err'); return; }
  }

  const valArrays  = knownList.map(v => getValsForVar(v));
  const total      = valArrays.reduce((a,b) => a * b.length, 1);
  const maxDisplay = parseInt(document.getElementById('maxRes').value) || 20;

  document.getElementById('searchBtn').disabled = true;
  showSt(`Έλεγχος ${total.toLocaleString('el-GR')} συνδυασμών…`,'');
  const prog = document.getElementById('prog');
  prog.style.display = 'block'; prog.value = 0;
  allResults = [];
  let done = 0;
  const n = knownList.length;

  function chunk() {
    const dl = Date.now() + 30;
    while (Date.now() < dl && done < total) {
      const combo = []; let idx = done;
      for (let k = 0; k < n; k++) {
        const arr = valArrays[k];
        combo.push(arr[idx % arr.length]);
        idx = Math.floor(idx / arr.length);
      }
      done++;
      const scope = {};
      knownList.forEach((v,i) => scope[v] = combo[i]);
      let ok = true; const computed = {};
      for (const eq of equations) {
        try {
          const r = math.evaluate(eq.mjs, scope);
          if (typeof r !== 'number' || !isFinite(r)) { ok = false; break; }
          if (Math.abs(r - Math.round(r)) > 1e-9)    { ok = false; break; }
          computed[eq.unknown] = Math.round(r);
        } catch(e) { ok = false; break; }
      }
      if (ok) allResults.push({ combo: [...combo], computed });
    }
    prog.value = Math.min(100, Math.round(done / total * 100));
    if (done < total) { setTimeout(chunk, 0); }
    else {
      prog.style.display = 'none';
      document.getElementById('searchBtn').disabled = false;
      showSt('');
      showResults(total, maxDisplay);
    }
  }
  setTimeout(chunk, 0);
}

/* ════════════════════════════════════════════════
   STEP 4 — RESULTS & SOLUTION
════════════════════════════════════════════════ */
function showResults(total, maxDisplay) {
  goStep(4);
  const area    = document.getElementById('resultsArea');
  const solArea = document.getElementById('solutionArea');
  const badge   = document.getElementById('foundBadge');
  solArea.innerHTML = '';

  const totalFound = allResults.length;
  const displayed  = allResults.slice(0, maxDisplay);

  const summary = `<div style="font-size:13px;color:var(--text2);margin-bottom:10px">
    Ελέγχθηκαν <strong style="color:var(--text)">${total.toLocaleString('el-GR')}</strong> συνδυασμοί —
    βρέθηκαν <strong style="color:var(--text)">${totalFound}</strong> με ακέραια αποτελέσματα.
    ${totalFound ? 'Κάνε κλικ σε έναν για να δεις τη λύση.' : ''}
  </div>`;

  if (!totalFound) {
    badge.innerHTML = '';
    area.innerHTML = summary + '<div class="status err">Κανένας συνδυασμός δεν δίνει ακέραια αποτελέσματα.<br>Δοκίμασε μεγαλύτερο εύρος ή διαφορετικό βήμα.</div>';
    return;
  }

  badge.innerHTML = `<span style="display:inline-block;font-size:11px;padding:2px 10px;border-radius:99px;background:var(--green-bg);color:var(--green);border:1px solid var(--green-bdr);margin-left:8px">${totalFound} συνδυασμοί</span>`;

  const hdrs = [...knownList, ...unknownList];
  let html = summary + `<table class="res"><thead><tr>
    ${hdrs.map(h => `<th>${h}${units[h] ? ` <span style="font-weight:400;font-size:11px">(${units[h]})</span>` : ''}</th>`).join('')}
    <th></th>
  </tr></thead><tbody>`;

  displayed.forEach((r, i) => {
    html += `<tr class="res-row" onclick="selectResult(${i})" id="rrow_${i}">`;
    knownList.forEach((v, ki) => html += `<td>${formatVal(r.combo[ki], v)}</td>`);
    unknownList.forEach(u => html += `<td>${r.computed[u]}</td>`);
    html += `<td><button class="btn-sel" onclick="event.stopPropagation();selectResult(${i})">Επιλογή</button></td>`;
    html += '</tr>';
  });
  html += '</tbody></table>';

  if (totalFound > maxDisplay) {
    html += `<div class="truncated-note">Εμφανίζονται οι πρώτοι <strong>${maxDisplay}</strong> από τους <strong>${totalFound}</strong> συνδυασμούς. Αύξησε τον αριθμό εμφάνισης στο βήμα 3 για να δεις περισσότερους.</div>`;
  }

  area.innerHTML = html;
}

function selectResult(i) {
  document.querySelectorAll('.res-row').forEach(r => r.classList.remove('selected'));
  document.getElementById('rrow_'+i)?.classList.add('selected');
  const r = allResults[i];
  if (!r) return;

  let rows = '';

  // Δεδομένα
  rows += `<tr class="sol-divider"><td colspan="4"><span>Δεδομένα</span></td></tr>`;
  knownList.forEach((v, ki) => {
    const dispVal = formatVal(r.combo[ki], v);
    const u = units[v] || '';
    rows += `<tr class="sol-known">
      <td class="sol-var">\\(${v}\\)</td>
      <td class="sol-eq">=</td>
      <td class="sol-val">${dispVal}</td>
      <td class="sol-unit">${u ? `<span style="font-size:15px;color:var(--text2)">${u}</span>` : ''}</td>
    </tr>`;
  });

  // Ζητούμενα
  rows += `<tr class="sol-divider"><td colspan="4"><span>Ζητούμενα</span></td></tr>`;
  unknownList.forEach(u => {
    const val  = r.computed[u];
    const unit = units[u] || '';
    rows += `<tr class="sol-unknown">
      <td class="sol-var">\\(${u}\\)</td>
      <td class="sol-eq">=</td>
      <td class="sol-val">${val}</td>
      <td class="sol-unit">${unit ? `<span style="font-size:15px;color:var(--text2)">${unit}</span>` : ''}</td>
    </tr>`;
  });

  const card = `<div class="solution-card">
    <div class="sol-header">Λύση</div>
    <table class="sol-table">${rows}</table>
  </div>`;

  document.getElementById('solutionArea').innerHTML = card;
  if (window.MathJax && MathJax.typesetPromise) MathJax.typesetPromise([document.getElementById('solutionArea')]);
  document.getElementById('solutionArea').scrollIntoView({ behavior:'smooth', block:'nearest' });
}

function resetAll() {
  eqCount = 0; equations = []; allResults = [];
  ['knownVars','unknownVars'].forEach(id => document.getElementById(id).value = '');
  ['knownTags','unknownTags','eqList','rangeBody','unitsBody','solutionArea','resultsArea'].forEach(id => {
    document.getElementById(id).innerHTML = '';
  });
  document.getElementById('totalBox').style.display = 'none';
  document.getElementById('unitsSection').style.display = 'none';
  document.getElementById('foundBadge').innerHTML = '';
  knownList = []; unknownList = [];
  goStep(1);
}
</script>

{% endraw %}
