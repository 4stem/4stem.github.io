---
layout: post
title: "Επίλυση Ακεραίου"
description: "Διαδραστική εφαρμογή που βρίσκει συνδυασμούς δεδομένων για τους οποίους οι τιμές των ζητούμενων μεγεθών είναι ακέραιοι ή δεκαδικοί αριθμοί."
category: Εφαρμογή
tags: [Εργαστήριο]
---

# Εφαρμογή εύρεσης ακέραιων ή δεκαδικών

Διαδραστική εφαρμογή που βρίσκει συνδυασμούς δεδομένων για τους οποίους οι τιμές των ζητούμενων μεγεθών είναι ακέραιοι ή δεκαδικοί αριθμοί.

## Χαρακτηριστικά

- ✅ Ορισμός δεδομένων (γνωστών) και ζητούμενων μεταβλητών
- ✅ Εισαγωγή εξισώσεων σε LaTeX με άμεση προεπισκόπηση
- ✅ Αυτόματη μετατροπή LaTeX σε υπολογίσιμη έκφραση (mathjs)
- ✅ Ορισμός εύρους και βήματος αναζήτησης ανά μεταβλητή
- ✅ Υποστήριξη γωνιών σε rad ως πολλαπλάσια του π
- ✅ Κριτήριο αποδοχής: ακέραιος ή δεκαδικός με N ψηφία, ανά ζητούμενο
- ✅ Προαιρετικό εύρος αποδοχής τιμών ανά ζητούμενο (πριν την αναζήτηση)
- ✅ Φίλτρο αποτελεσμάτων μετά την αναζήτηση
- ✅ Δυνατότητα τροποποίησης εύρους/βήματος χωρίς επανεισαγωγή εξισώσεων

---

<script>
window.MathJax = {
  tex: { inlineMath: [['\\(','\\)']] },
  startup: { ready() { MathJax.startup.defaultReady(); } }
};
</script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/3.2.2/es5/tex-chtml.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/mathjs/12.4.1/math.min.js"></script>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

{% raw %}
<style>
#isw{background:linear-gradient(135deg,#667eea 0%,#764ba2 100%);padding:28px 20px 36px;margin:0 -20px;border-radius:12px;position:relative;}
#isw .apc{max-width:860px;margin:0 auto;background:#fff;border-radius:20px;box-shadow:0 20px 60px rgba(0,0,0,.25);padding:32px 28px;overflow-x:hidden;}
#isw *,#isw *::before,#isw *::after{box-sizing:border-box;margin:0;padding:0;}
#isw{--bg:#f8f8f6;--surface:#fff;--surface2:#f1f0ec;--border:#e0deda;--border2:#c8c6c0;--text:#1a1a18;--text2:#6b6a66;--text3:#9e9d99;--blue:#667eea;--blue-bg:#eef0fc;--blue-bdr:#b0b8f0;--amber:#a06010;--amber-bg:#fef3e0;--amber-bdr:#f0c870;--green:#1a7a40;--green-bg:#e6f5ec;--green-bdr:#80c8a0;--red:#c0281e;--red-bg:#fdecea;--red-bdr:#f0a8a4;--radius:8px;--radius-lg:12px;}
#isw .social-buttons{position:fixed;bottom:30px;right:30px;display:flex;flex-direction:column;gap:12px;z-index:1000;}
#isw .social-btn{width:46px;height:46px;border-radius:50%;display:flex;align-items:center;justify-content:center;color:#fff;text-decoration:none;font-size:20px;box-shadow:0 4px 15px rgba(0,0,0,.3);transition:all .3s;}
#isw .social-btn:hover{transform:translateY(-4px) scale(1.1);box-shadow:0 8px 25px rgba(0,0,0,.4);}
#isw .social-btn.github{background:#333;}#isw .social-btn.facebook{background:#3b5998;}
#isw .social-btn.twitter{background:#1DA1F2;}#isw .social-btn.linkedin{background:#0077B5;}
#isw .social-btn.youtube{background:#FF0000;}#isw .social-btn.wordpress{background:#21759B;}
#isw .social-btn.tumblr{background:#35465C;}
#isw .ct{font-family:'Segoe UI',system-ui,-apple-system,sans-serif;color:var(--text);font-size:15px;line-height:1.6;}
#isw h1{font-size:20px;font-weight:600;margin-bottom:4px;color:#667eea;text-align:center;}
#isw .subtitle{font-size:13px;color:var(--text2);margin-bottom:1.5rem;text-align:center;}
#isw .step-bar{display:flex;border-radius:var(--radius);overflow:hidden;border:1px solid var(--border);margin-bottom:1.5rem;}
#isw .stp{flex:1;padding:10px 8px;text-align:center;font-size:13px;color:var(--text2);background:var(--surface2);cursor:pointer;border-right:1px solid var(--border);transition:background .15s;user-select:none;}
#isw .stp:last-child{border-right:none;}
#isw .stp:hover{background:#e8e7e3;}
#isw .stp.active{background:#667eea;color:#fff;font-weight:600;}
#isw .stp.done{background:var(--green-bg);color:var(--green);}
#isw .section{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius-lg);padding:1.25rem;margin-bottom:1rem;}
#isw .sec-title{font-size:11px;font-weight:600;color:var(--text2);text-transform:uppercase;letter-spacing:.07em;margin-bottom:1rem;}
#isw label{font-size:14px;color:var(--text2);}
#isw input[type=text],#isw input[type=number],#isw select{font-size:14px;padding:8px 11px;border-radius:var(--radius);border:1px solid var(--border2);background:var(--surface2);color:var(--text);outline:none;transition:border-color .15s,box-shadow .15s;}
#isw input[type=text]:focus,#isw input[type=number]:focus,#isw select:focus{border-color:#667eea;box-shadow:0 0 0 3px rgba(102,126,234,.15);}
#isw input[type=text]{width:100%;}#isw input[type=number]{width:78px;}
#isw input.unit-inp{width:90px;font-size:13px;padding:5px 8px;}#isw input.wide{width:100%;}
#isw .btn{font-size:13px;font-weight:500;padding:8px 18px;border-radius:var(--radius);border:1px solid var(--border2);background:transparent;color:var(--text);cursor:pointer;transition:background .12s;}
#isw .btn:hover{background:var(--surface2);}
#isw .btn-p{background:#667eea;color:#fff;border-color:transparent;}#isw .btn-p:hover{background:#5568d3;}
#isw .btn-d{color:var(--red);border-color:var(--red-bdr);}#isw .btn-d:hover{background:var(--red-bg);}
#isw .btn-sel{font-size:12px;padding:4px 12px;border-radius:var(--radius);border:1px solid var(--blue-bdr);background:transparent;color:var(--blue);cursor:pointer;}
#isw .btn-sel:hover{background:var(--blue-bg);}
#isw .tag{display:inline-block;font-size:12px;padding:2px 10px;border-radius:99px;background:var(--blue-bg);color:var(--blue);border:1px solid var(--blue-bdr);}
#isw .tag.unk{background:var(--amber-bg);color:var(--amber);border-color:var(--amber-bdr);}
#isw .tag.angle{background:var(--green-bg);color:var(--green);border-color:var(--green-bdr);}
#isw .eq-block{background:var(--surface2);border-radius:var(--radius);padding:14px;margin-bottom:10px;border:1px solid var(--border);}
#isw .eq-row{display:flex;gap:8px;align-items:center;margin-bottom:8px;}
#isw .eq-row label{min-width:60px;font-size:13px;}
#isw .eq-row input[type=text]{font-family:'Courier New',monospace;font-size:13px;}
#isw .preview{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius);padding:8px 14px;min-height:40px;font-size:16px;margin-top:6px;}
#isw .mjs-preview{font-family:'Courier New',monospace;font-size:12px;color:var(--text2);background:var(--surface);border:1px solid var(--border);border-radius:var(--radius);padding:6px 10px;margin-top:4px;word-break:break-all;}
#isw .mjs-preview.ok{color:var(--green);}#isw .mjs-preview.err{color:var(--red);}
#isw .status{font-size:13px;padding:8px 14px;border-radius:var(--radius);background:var(--blue-bg);color:#667eea;border:1px solid var(--blue-bdr);margin-top:8px;}
#isw .status.err{background:var(--red-bg);color:var(--red);border-color:var(--red-bdr);}
#isw .truncated-note{font-size:12px;color:var(--amber);background:var(--amber-bg);border-radius:var(--radius);padding:7px 12px;margin-top:8px;border:1px solid var(--amber-bdr);}
#isw .rt{width:100%;border-collapse:collapse;}
#isw .rt th{font-size:12px;font-weight:600;color:var(--text2);text-align:left;padding:6px 8px;border-bottom:1px solid var(--border);}
#isw .rt td{padding:7px 8px;border-bottom:1px solid var(--border);vertical-align:middle;}
#isw .rt tr:last-child td{border-bottom:none;}
#isw .type-toggle{display:flex;border-radius:var(--radius);overflow:hidden;border:1px solid var(--border2);}
#isw .type-toggle button{flex:1;padding:5px 10px;font-size:12px;border:none;background:transparent;color:var(--text2);cursor:pointer;transition:background .12s;}
#isw .type-toggle button:hover{background:var(--surface2);}
#isw .type-toggle button.on{background:#667eea;color:#fff;font-weight:500;}
#isw .total-box{font-size:13px;color:var(--text2);background:var(--surface2);border-radius:var(--radius);padding:8px 14px;margin-top:12px;border:1px solid var(--border);}
#isw .total-box strong{color:var(--text);}
#isw .limit-row{display:flex;align-items:center;gap:10px;background:var(--surface2);border-radius:var(--radius);padding:10px 14px;margin-bottom:1rem;border:1px solid var(--border);flex-wrap:wrap;}
#isw .limit-row label{font-size:13px;color:var(--text2);}
#isw .limit-note{font-size:12px;color:var(--text3);}
#isw table.res{width:100%;font-size:13px;border-collapse:collapse;margin-top:10px;}
#isw table.res th{text-align:left;font-weight:600;font-size:12px;color:var(--text2);border-bottom:1px solid var(--border);padding:6px 10px;background:var(--surface2);}
#isw table.res td{padding:7px 10px;border-bottom:1px solid var(--border);font-family:'Courier New',monospace;}
#isw table.res tr.res-row{cursor:pointer;transition:background .1s;}
#isw table.res tr.res-row:hover td{background:var(--blue-bg);}
#isw table.res tr.res-row.selected td{background:var(--blue-bg);color:#667eea;font-weight:600;}
#isw progress{width:100%;height:6px;border-radius:3px;margin-top:8px;appearance:none;-webkit-appearance:none;border:none;background:var(--border);overflow:hidden;}
#isw progress::-webkit-progress-bar{background:var(--border);}
#isw progress::-webkit-progress-value{background:#667eea;border-radius:3px;}
#isw progress::-moz-progress-bar{background:#667eea;border-radius:3px;}
#isw .solution-card{margin-top:1.5rem;background:var(--surface);border-radius:var(--radius-lg);border:1px solid var(--border);overflow:hidden;}
#isw .sol-header{font-size:12px;font-weight:600;color:var(--text2);text-transform:uppercase;letter-spacing:.07em;padding:10px 18px;border-bottom:1px solid var(--border);background:var(--surface2);}
#isw .sol-table{width:100%;border-collapse:collapse;}
#isw .sol-table td{padding:10px 18px;border-bottom:1px solid var(--border);font-size:16px;}
#isw .sol-table tr:last-child td{border-bottom:none;}
#isw .sol-table .sol-var{font-family:'Courier New',monospace;font-weight:600;color:var(--text2);width:90px;}
#isw .sol-table .sol-eq{color:var(--text3);width:28px;text-align:center;}
#isw .sol-table .sol-val{font-family:'Courier New',monospace;font-weight:700;font-size:20px;}
#isw .sol-table .sol-unit{font-size:14px;color:var(--text2);padding-left:8px;}
#isw .sol-table tr.sol-divider td{background:var(--surface2);padding:5px 18px;border-bottom:1px solid var(--border);}
#isw .sol-table tr.sol-divider td span{font-size:11px;font-weight:600;color:var(--text3);text-transform:uppercase;letter-spacing:.07em;}
#isw .sol-table tr.sol-known .sol-val{color:#667eea;}
#isw .sol-table tr.sol-unknown .sol-val{color:var(--green);}
#isw .hidden{display:none;}
#isw .hint{font-size:13px;color:var(--text2);line-height:1.7;}
#isw .hint code{font-family:'Courier New',monospace;font-size:12px;background:var(--surface2);padding:1px 6px;border-radius:4px;border:1px solid var(--border);}
#isw .nav-row{display:flex;justify-content:space-between;align-items:center;margin-top:1.25rem;}
#isw #unitsSection{margin-top:20px;padding-top:20px;border-top:1px solid var(--border);}
@media(max-width:600px){
  #isw .step-bar{flex-wrap:wrap;}
  #isw .stp{min-width:50%;border-right:none;border-bottom:1px solid var(--border);}
  #isw .limit-row{flex-direction:column;align-items:flex-start;}
  #isw .social-buttons{bottom:15px;right:15px;gap:8px;}
  #isw .social-btn{width:40px;height:40px;font-size:17px;}
}
</style>

<div id="isw">

  <div class="social-buttons">
    <a href="https://github.com/4stem" target="_blank" class="social-btn github" title="GitHub"><i class="fab fa-github"></i></a>
    <a href="https://www.facebook.com/papetridis" target="_blank" class="social-btn facebook" title="Facebook"><i class="fab fa-facebook-f"></i></a>
    <a href="https://www.twitter.com/Petridis_P" target="_blank" class="social-btn twitter" title="Twitter"><i class="fab fa-twitter"></i></a>
    <a href="http://www.linkedin.com/pub/panagiotis-petridis/42/840/516" target="_blank" class="social-btn linkedin" title="LinkedIn"><i class="fab fa-linkedin-in"></i></a>
    <a href="https://www.youtube.com/channel/UC0nvnxsK6_cBOFiM19tG0TA" target="_blank" class="social-btn youtube" title="YouTube"><i class="fab fa-youtube"></i></a>
    <a href="http://petridis.wordpress.com/" target="_blank" class="social-btn wordpress" title="WordPress"><i class="fab fa-wordpress"></i></a>
    <a href="http://28lykeio.tumblr.com/" target="_blank" class="social-btn tumblr" title="Tumblr"><i class="fab fa-tumblr"></i></a>
  </div>

  <div class="apc">
    <div class="ct">

      <h1>Επίλυση Ακεραίου</h1>
      <p class="subtitle">Βρες συνδυασμούς δεδομένων που κάνουν τα ζητούμενα ακέραιους ή δεκαδικούς αριθμούς.</p>

      <div class="step-bar">
        <div class="stp active" id="stp1" onclick="goStep(1)">1. Μεταβλητές</div>
        <div class="stp" id="stp2" onclick="goStep(2)">2. Εξισώσεις</div>
        <div class="stp" id="stp3" onclick="goStep(3)">3. Εύρη &amp; Αναζήτηση</div>
        <div class="stp" id="stp4" onclick="goStep(4)">4. Αποτελέσματα</div>
      </div>

      <!-- STEP 1 -->
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
            <table class="rt"><thead><tr>
              <th>Μεταβλητή</th><th>Μονάδα</th>
              <th style="font-size:11px;color:var(--text3)">π.χ. m, kg, °, rad, N/m² …</th>
            </tr></thead><tbody id="unitsBody"></tbody></table>
          </div>
          <div class="nav-row"><span></span>
            <button class="btn btn-p" onclick="goStep(2)">Επόμενο →</button>
          </div>
        </div>
      </div>

      <!-- STEP 2 -->
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

      <!-- STEP 3 -->
      <div id="step3" class="hidden">
        <div id="refineNotice" style="display:none;background:var(--amber-bg);border:1px solid var(--amber-bdr);border-radius:var(--radius);padding:10px 16px;margin-bottom:1rem;font-size:13px;color:var(--amber)">
          Οι μεταβλητές, ζητούμενα και εξισώσεις παραμένουν αναλλοίωτα — μπορείς να αλλάξεις μόνο τα εύρη και τα βήματα.
        </div>
        <div class="section">
          <div class="sec-title">Εύρος αναζήτησης ανά μεταβλητή</div>
          <div class="hint" style="margin-bottom:14px">
            Για γωνίες επίλεξε <strong>Γωνία (rad)</strong> — εύρος και βήμα ως πολλαπλάσια του π.
          </div>
          <div style="overflow-x:auto">
            <table class="rt"><thead><tr>
              <th style="min-width:80px">Μεταβλητή</th><th>Τύπος</th>
              <th>Από</th><th>Έως</th><th>Βήμα</th>
              <th style="min-width:70px">Τιμές</th>
            </tr></thead><tbody id="rangeBody"></tbody></table>
          </div>
          <div class="total-box" id="totalBox" style="display:none">
            Σύνολο συνδυασμών προς έλεγχο: <strong id="totalCount">—</strong>
          </div>
        </div>
        <div class="section">
          <div class="sec-title">Κριτήριο αποδοχής ανά ζητούμενο</div>
          <div class="hint" style="margin-bottom:14px">
            Επίλεξε αν το αποτέλεσμα πρέπει να είναι <strong>ακέραιος</strong> ή να έχει συγκεκριμένο αριθμό <strong>δεκαδικών ψηφίων</strong>. Προαιρετικά όρισε και <strong>εύρος τιμών</strong> για κάθε ζητούμενο.
          </div>
          <div style="overflow-x:auto">
            <table class="rt"><thead><tr>
              <th style="min-width:80px">Ζητούμενο</th><th>Τύπος</th>
              <th style="min-width:100px">Δεκαδικά ψηφία</th>
              <th style="min-width:100px">Ελάχιστο</th>
              <th style="min-width:100px">Μέγιστο</th>
            </tr></thead><tbody id="precBody"></tbody></table>
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

      <!-- STEP 4 -->
      <div id="step4" class="hidden">
        <div class="section">
          <div class="sec-title">Αποτελέσματα <span id="foundBadge"></span></div>
          <div id="filterPanel" style="display:none;margin-bottom:14px">
            <div style="font-size:11px;font-weight:600;color:var(--text2);text-transform:uppercase;letter-spacing:.07em;margin-bottom:8px">Φίλτρο αποτελεσμάτων</div>
            <table class="rt"><thead><tr>
              <th style="min-width:80px">Ζητούμενο</th>
              <th>Από</th><th>Έως</th><th style="min-width:80px"></th>
            </tr></thead><tbody id="filterBody"></tbody></table>
          </div>
          <div id="resultsArea"></div>
          <div id="solutionArea"></div>
          <div class="nav-row">
            <button class="btn btn-p" onclick="resetAll()">+ Νέα αναζήτηση</button>
            <button class="btn" onclick="goStep(3,true)" style="display:flex;align-items:center;gap:6px">
              <svg width="14" height="14" viewBox="0 0 14 14" fill="none" style="flex-shrink:0">
                <path d="M2 7a5 5 0 1 1 1.5 3.6" stroke="currentColor" stroke-width="1.4" stroke-linecap="round"/>
                <path d="M2 10.5V7h3.5" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"/>
              </svg>
              Τροποποίηση εύρους / βήματος
            </button>
          </div>
        </div>
      </div>

    </div>
  </div>
</div>

<script>
let knownList=[],unknownList=[],eqCount=0,equations=[],allResults=[];
const units={};
const ANGLE_PRESETS=[
  {label:'0',v:0},{label:'π/12',v:Math.PI/12},{label:'π/8',v:Math.PI/8},
  {label:'π/6',v:Math.PI/6},{label:'π/4',v:Math.PI/4},{label:'π/3',v:Math.PI/3},
  {label:'5π/12',v:5*Math.PI/12},{label:'π/2',v:Math.PI/2},{label:'7π/12',v:7*Math.PI/12},
  {label:'2π/3',v:2*Math.PI/3},{label:'3π/4',v:3*Math.PI/4},{label:'5π/6',v:5*Math.PI/6},
  {label:'11π/12',v:11*Math.PI/12},{label:'π',v:Math.PI},
];
function angleSelect(cls,defIdx){
  return`<select class="${cls}" style="width:90px" onchange="updateTotals()">
    ${ANGLE_PRESETS.map((p,i)=>`<option value="${i}"${i==defIdx?' selected':''}>${p.label}</option>`).join('')}
  </select>`;
}
function goStep(n,fromResults){
  for(let i=1;i<=4;i++){
    document.getElementById('step'+i).classList.toggle('hidden',i!==n);
    const s=document.getElementById('stp'+i);s.classList.remove('active','done');
    if(i<n)s.classList.add('done');else if(i===n)s.classList.add('active');
  }
  if(n===2&&document.getElementById('eqList').children.length===0)addEq();
  if(n===3){buildRangeTable();buildPrecTable();document.getElementById('refineNotice').style.display=fromResults?'block':'none';}
}
function parseVars(){
  knownList=document.getElementById('knownVars').value.split(',').map(s=>s.trim()).filter(Boolean);
  unknownList=document.getElementById('unknownVars').value.split(',').map(s=>s.trim()).filter(Boolean);
  document.getElementById('knownTags').innerHTML=knownList.map(v=>`<span class="tag">${v}</span>`).join('');
  document.getElementById('unknownTags').innerHTML=unknownList.map(v=>`<span class="tag unk">${v}</span>`).join('');
  buildUnitsTable();
}
function buildUnitsTable(){
  const allVars=[...knownList,...unknownList];
  document.getElementById('unitsSection').style.display=allVars.length?'block':'none';
  const tbody=document.getElementById('unitsBody');tbody.innerHTML='';
  allVars.forEach(v=>{
    const tr=document.createElement('tr');
    tr.innerHTML=`<td><span class="tag ${unknownList.includes(v)?'unk':''}">${v}</span></td>
      <td><input class="unit-inp" type="text" placeholder="π.χ. kg" value="${units[v]||''}" oninput="units['${v}']=this.value.trim()"/></td>
      <td style="font-size:12px;color:var(--text3)">αφήστε κενό αν δεν υπάρχει μονάδα</td>`;
    tbody.appendChild(tr);
  });
}
function addEq(){
  eqCount++;const id='eq'+eqCount;const unk=unknownList[eqCount-1]||'?';
  const div=document.createElement('div');div.className='eq-block';div.id=id;
  div.innerHTML=`
    <div class="eq-row">
      <label style="font-size:12px;min-width:60px;color:var(--text2)">Εξίσωση ${eqCount}</label>
      <span class="tag unk" style="font-size:12px">${unk}</span>
      <span style="font-size:13px;color:var(--text2);margin-left:6px">= f(δεδομένων)</span>
      <button class="btn btn-d" onclick="removeEq('${id}')" style="margin-left:auto;padding:3px 10px;font-size:12px">✕</button>
    </div>
    <div class="eq-row">
      <label style="min-width:60px">LaTeX</label>
      <input type="text" class="wide" id="${id}_l" placeholder="π.χ.  \\frac{2m}{\\sin(\\theta)}" oninput="updateEq('${id}')"/>
    </div>
    <div class="preview" id="${id}_p" style="min-height:36px;color:var(--text3);font-size:13px">preview LaTeX…</div>
    <div class="mjs-preview" id="${id}_j">— γράψε LaTeX παραπάνω —</div>`;
  document.getElementById('eqList').appendChild(div);
}
function removeEq(id){document.getElementById(id)?.remove();}
function updateEq(id){
  const latex=document.getElementById(id+'_l').value;
  const prev=document.getElementById(id+'_p');const jprev=document.getElementById(id+'_j');
  if(!latex){prev.innerHTML='preview LaTeX…';prev.style.color='var(--text3)';jprev.textContent='—';jprev.className='mjs-preview';return;}
  prev.style.color='';prev.innerHTML=`\\(${latex}\\)`;
  if(window.MathJax&&MathJax.typesetPromise)MathJax.typesetPromise([prev]);
  let rhs=latex;const ei=latex.indexOf('=');if(ei>=0)rhs=latex.slice(ei+1).trim();
  const mjs=latexToMathjs(rhs);const t=tryEval(mjs);
  jprev.textContent=`Έκφραση: ${mjs}`+(t.ok?'':` ← σφάλμα: ${t.err}`);
  jprev.className='mjs-preview '+(t.ok?'ok':'err');
}
function collectEquations(){
  equations=[];
  document.querySelectorAll('.eq-block').forEach((b,i)=>{
    const latex=document.getElementById(b.id+'_l').value;
    let rhs=latex;const ei=latex.indexOf('=');if(ei>=0)rhs=latex.slice(ei+1).trim();
    equations.push({latex,mjs:latexToMathjs(rhs),unknown:unknownList[i]||('u'+(i+1))});
  });
}
function latexToMathjs(raw){
  let s=raw.trim();
  s=s.replace(/\\left|\\right|\\[Bb]ig[lr]?/g,'');s=s.replace(/\\[,;!]|\\quad|\\qquad/g,' ');
  function repFrac(str){let r=str,ch=true;while(ch){ch=false;r=r.replace(/\\frac\s*\{((?:[^{}]|\{[^{}]*\})*)\}\s*\{((?:[^{}]|\{[^{}]*\})*)\}/g,(_,n,d)=>{ch=true;return`(${latexToMathjs(n)})/(${latexToMathjs(d)})`;})}return r;}
  s=repFrac(s);
  s=s.replace(/\\sqrt\s*\[([^\]]+)\]\s*\{((?:[^{}]|\{[^{}]*\})*)\}/g,(_,n,x)=>`(${latexToMathjs(x)})^(1/(${latexToMathjs(n)}))`);
  s=s.replace(/\\sqrt\s*\{((?:[^{}]|\{[^{}]*\})*)\}/g,(_,x)=>`sqrt(${latexToMathjs(x)})`);
  ['sin','cos','tan','cot','sec','csc','ln','log','exp','arcsin','arccos','arctan','sinh','cosh','tanh'].forEach(f=>{
    s=s.replace(new RegExp('\\\\'+f+'\\s*\\{((?:[^{}]|\\{[^{}]*\\})*)\\}','g'),(_,x)=>`${f}(${latexToMathjs(x)})`);
    s=s.replace(new RegExp('\\\\'+f+'\\b','g'),f);
  });
  s=s.replace(/\\pi\b/g,'pi').replace(/\\e\b/g,'e').replace(/\\cdot|\\times/g,'*');
  s=s.replace(/\^\s*\{((?:[^{}]|\{[^{}]*\})*)\}/g,(_,e)=>`^(${latexToMathjs(e)})`);
  s=s.replace(/\\text\s*\{[^{}]*\}/g,'');
  s=s.replace(/\{/g,'(').replace(/\}/g,')');
  s=s.replace(/([0-9])\s*([a-zA-Zα-ωΑ-Ω_])/g,'$1*$2');s=s.replace(/([0-9])\s*\(/g,'$1*(');
  s=s.replace(/\)\s*([a-zA-Zα-ωΑ-Ω_0-9])/g,')*$1');s=s.replace(/\)\s*\(/g,')*(');
  return s.replace(/\s+/g,' ').trim();
}
function tryEval(e){
  try{const sc={};[...knownList,...unknownList].forEach(v=>sc[v]=0.5);const r=math.evaluate(e,sc);return(typeof r==='number'&&isFinite(r))?{ok:true}:{ok:false,err:'μη αριθμητικό'};}
  catch(ex){return{ok:false,err:ex.message};}
}
function buildRangeTable(){
  parseVars();const tbody=document.getElementById('rangeBody');const existing={};
  tbody.querySelectorAll('tr[data-var]').forEach(tr=>{
    const v=tr.dataset.var,isAngle=tr.dataset.isAngle==='1';existing[v]={isAngle};
    if(isAngle){existing[v].amin=tr.querySelector('.amin')?.value??'0';existing[v].amax=tr.querySelector('.amax')?.value??'7';existing[v].astep=tr.querySelector('.astep')?.value??'3';}
    else{existing[v].rmin=tr.querySelector('.rmin')?.value??'1';existing[v].rmax=tr.querySelector('.rmax')?.value??'20';existing[v].rstep=tr.querySelector('.rstep')?.value??'1';}
  });
  tbody.innerHTML='';
  knownList.forEach(v=>{
    const prev=existing[v]||{isAngle:false};const tr=document.createElement('tr');
    tr.dataset.var=v;tr.dataset.isAngle=prev.isAngle?'1':'0';
    const minCell=prev.isAngle?angleSelect('amin',parseInt(prev.amin??0)):`<input type="number" class="rmin" value="${prev.rmin??1}" step="any" oninput="updateTotals()"/>`;
    const maxCell=prev.isAngle?angleSelect('amax',parseInt(prev.amax??7)):`<input type="number" class="rmax" value="${prev.rmax??20}" step="any" oninput="updateTotals()"/>`;
    const stepCell=prev.isAngle?angleSelect('astep',parseInt(prev.astep??3)):`<input type="number" class="rstep" value="${prev.rstep??1}" min="0.001" step="any" oninput="updateTotals()"/>`;
    tr.innerHTML=`
      <td><span class="tag ${prev.isAngle?'angle':''}" id="vtag_${v}">${v}</span></td>
      <td><div class="type-toggle">
        <button class="${prev.isAngle?'':'on'}" onclick="setType('${v}',false,this)">Αριθμός</button>
        <button class="${prev.isAngle?'on':''}" onclick="setType('${v}',true,this)">Γωνία (rad)</button>
      </div></td>
      <td id="cm_${v}">${minCell}</td><td id="cx_${v}">${maxCell}</td><td id="cs_${v}">${stepCell}</td>
      <td id="cc_${v}" style="font-size:12px;color:var(--text2)">—</td>`;
    tbody.appendChild(tr);updateCount(v);
  });
  updateTotals();
}
function buildPrecTable(){
  const tbody=document.getElementById('precBody');if(!tbody)return;
  const prev={};
  tbody.querySelectorAll('tr[data-unk]').forEach(tr=>{
    prev[tr.dataset.unk]={isInt:tr.dataset.isInt==='1',dec:tr.querySelector('.prec-dec')?.value??'1',
      vmin:tr.querySelector('.prec-vmin')?.value??'',vmax:tr.querySelector('.prec-vmax')?.value??''};
  });
  tbody.innerHTML='';
  unknownList.forEach(u=>{
    const p=prev[u]||{isInt:true,dec:'1',vmin:'',vmax:''};
    const tr=document.createElement('tr');tr.dataset.unk=u;tr.dataset.isInt=p.isInt?'1':'0';
    tr.innerHTML=`
      <td><span class="tag unk">${u}</span></td>
      <td><div class="type-toggle">
        <button class="${p.isInt?'on':''}" onclick="setPrecType('${u}',true,this)">Ακέραιος</button>
        <button class="${p.isInt?'':'on'}" onclick="setPrecType('${u}',false,this)">Δεκαδικός</button>
      </div></td>
      <td id="prec_dec_${u}">${p.isInt?'<span style="font-size:13px;color:var(--text3)">—</span>'
        :`<input type="number" class="prec-dec" value="${p.dec}" min="1" max="6" step="1" style="width:65px"/> ψηφία`}</td>
      <td><input type="number" class="prec-vmin" value="${p.vmin}" step="any" placeholder="χωρίς όριο" style="width:100px;font-size:12px"/></td>
      <td><input type="number" class="prec-vmax" value="${p.vmax}" step="any" placeholder="χωρίς όριο" style="width:100px;font-size:12px"/></td>`;
    tbody.appendChild(tr);
  });
}
function setPrecType(u,isInt,btn){
  const tr=document.querySelector(`#precBody tr[data-unk="${u}"]`);
  tr.dataset.isInt=isInt?'1':'0';
  btn.parentElement.querySelectorAll('button').forEach(b=>b.classList.remove('on'));btn.classList.add('on');
  document.getElementById('prec_dec_'+u).innerHTML=isInt?'<span style="font-size:13px;color:var(--text3)">—</span>'
    :`<input type="number" class="prec-dec" value="1" min="1" max="6" step="1" style="width:65px"/> ψηφία`;
}
function getPrecFor(u){
  const tr=document.querySelector(`#precBody tr[data-unk="${u}"]`);
  if(!tr)return{isInt:true,dec:0,vmin:null,vmax:null};
  const isInt=tr.dataset.isInt==='1';const dec=isInt?0:(parseInt(tr.querySelector('.prec-dec')?.value)||1);
  const vminS=tr.querySelector('.prec-vmin')?.value.trim();const vmaxS=tr.querySelector('.prec-vmax')?.value.trim();
  return{isInt,dec,vmin:vminS!==''?parseFloat(vminS):null,vmax:vmaxS!==''?parseFloat(vmaxS):null};
}
function setType(v,isAngle,btn){
  const tr=document.querySelector(`tr[data-var="${v}"]`);tr.dataset.isAngle=isAngle?'1':'0';
  btn.parentElement.querySelectorAll('button').forEach(b=>b.classList.remove('on'));btn.classList.add('on');
  document.getElementById('vtag_'+v).className='tag '+(isAngle?'angle':'');
  document.getElementById('cm_'+v).innerHTML=isAngle?angleSelect('amin',0):`<input type="number" class="rmin" value="1" step="any" oninput="updateTotals()"/>`;
  document.getElementById('cx_'+v).innerHTML=isAngle?angleSelect('amax',7):`<input type="number" class="rmax" value="20" step="any" oninput="updateTotals()"/>`;
  document.getElementById('cs_'+v).innerHTML=isAngle?angleSelect('astep',3):`<input type="number" class="rstep" value="1" min="0.001" step="any" oninput="updateTotals()"/>`;
  updateCount(v);updateTotals();
}
function getValsForVar(v){
  const tr=document.querySelector(`tr[data-var="${v}"]`);if(!tr)return[1];
  if(tr.dataset.isAngle==='1'){
    const mi=parseInt(tr.querySelector('.amin')?.value||0),mx=parseInt(tr.querySelector('.amax')?.value||7),si=parseInt(tr.querySelector('.astep')?.value||3);
    const step=ANGLE_PRESETS[si].v||(Math.PI/12),minR=ANGLE_PRESETS[mi].v,maxR=ANGLE_PRESETS[mx].v;
    const vals=[];for(let x=minR;x<=maxR+1e-9;x+=step)vals.push(Math.round(x*1e10)/1e10);return vals.length?vals:[minR];
  }
  const mn=parseFloat(tr.querySelector('.rmin')?.value)||1,mx=parseFloat(tr.querySelector('.rmax')?.value)||20,st=parseFloat(tr.querySelector('.rstep')?.value)||1;
  const vals=[];for(let x=mn;x<=mx+1e-9;x+=st)vals.push(Math.round(x*1e5)/1e5);return vals.length?vals:[mn];
}
function updateCount(v){const el=document.getElementById('cc_'+v);if(el)el.textContent=getValsForVar(v).length+' τιμές';}
function updateTotals(){
  knownList.forEach(v=>updateCount(v));
  if(!knownList.length){document.getElementById('totalBox').style.display='none';return;}
  const total=knownList.reduce((a,v)=>a*getValsForVar(v).length,1);
  document.getElementById('totalBox').style.display='block';
  document.getElementById('totalCount').textContent=total.toLocaleString('el-GR');
}
function formatVal(val,varName){
  const tr=document.querySelector(`tr[data-var="${varName}"]`);
  if(tr&&tr.dataset.isAngle==='1'){
    let best=null,bestD=Infinity;ANGLE_PRESETS.forEach(p=>{const d=Math.abs(p.v-val);if(d<bestD){bestD=d;best=p;}});
    return(best&&bestD<1e-9)?best.label:val.toFixed(4);
  }return val;
}
function showSt(msg,type){
  const el=document.getElementById('sStatus');el.className='status'+(type?' '+type:'');el.textContent=msg;el.style.display=msg?'block':'none';
}
function runSearch(){
  parseVars();collectEquations();
  if(!knownList.length){showSt('Ορίστε δεδομένα μεταβλητές.','err');return;}
  if(!unknownList.length){showSt('Ορίστε ζητούμενες μεταβλητές.','err');return;}
  if(equations.length!==unknownList.length){showSt(`Χρειάζεστε ${unknownList.length} εξίσωση(ς) — μία για κάθε ζητούμενο.`,'err');return;}
  for(const eq of equations){const t=tryEval(eq.mjs);if(!t.ok){showSt(`Σφάλμα στην εξίσωση για "${eq.unknown}": ${t.err}`,'err');return;}}
  const valArrays=knownList.map(v=>getValsForVar(v));const total=valArrays.reduce((a,b)=>a*b.length,1);
  const maxDisplay=parseInt(document.getElementById('maxRes').value)||20;
  document.getElementById('searchBtn').disabled=true;
  showSt(`Έλεγχος ${total.toLocaleString('el-GR')} συνδυασμών…`,'');
  const prog=document.getElementById('prog');prog.style.display='block';prog.value=0;
  allResults=[];let done=0;const n=knownList.length;
  function chunk(){
    const dl=Date.now()+30;
    while(Date.now()<dl&&done<total){
      const combo=[];let idx=done;
      for(let k=0;k<n;k++){const arr=valArrays[k];combo.push(arr[idx%arr.length]);idx=Math.floor(idx/arr.length);}
      done++;const scope={};knownList.forEach((v,i)=>scope[v]=combo[i]);
      let ok=true;const computed={};
      for(const eq of equations){
        try{
          const r=math.evaluate(eq.mjs,scope);
          if(typeof r!=='number'||!isFinite(r)){ok=false;break;}
          const prec=getPrecFor(eq.unknown);
          if(prec.isInt){
            if(Math.abs(r-Math.round(r))>1e-7){ok=false;break;}
            const val=Math.round(r);
            if(prec.vmin!==null&&val<prec.vmin){ok=false;break;}
            if(prec.vmax!==null&&val>prec.vmax){ok=false;break;}
            computed[eq.unknown]={val,dec:0,isInt:true};
          }else{
            const factor=Math.pow(10,prec.dec);const rounded=Math.round(r*factor)/factor;
            if(Math.abs(r-rounded)>5e-7){ok=false;break;}
            if(prec.vmin!==null&&rounded<prec.vmin){ok=false;break;}
            if(prec.vmax!==null&&rounded>prec.vmax){ok=false;break;}
            computed[eq.unknown]={val:rounded,dec:prec.dec,isInt:false};
          }
        }catch(e){ok=false;break;}
      }
      if(ok)allResults.push({combo:[...combo],computed});
    }
    prog.value=Math.min(100,Math.round(done/total*100));
    if(done<total){setTimeout(chunk,0);}
    else{prog.style.display='none';document.getElementById('searchBtn').disabled=false;showSt('');showResults(total,maxDisplay);}
  }
  setTimeout(chunk,0);
}
function fmtComputed(obj){if(!obj)return'—';if(obj.isInt)return obj.val;return obj.val.toFixed(obj.dec);}
function buildFilterPanel(){
  const panel=document.getElementById('filterPanel');const tbody=document.getElementById('filterBody');
  if(!unknownList.length){panel.style.display='none';return;}
  tbody.innerHTML='';
  unknownList.forEach(u=>{
    const vals=allResults.map(r=>r.computed[u]?.val??0);const mn=Math.min(...vals),mx=Math.max(...vals);
    const tr=document.createElement('tr');tr.dataset.unk=u;
    tr.innerHTML=`<td><span class="tag unk">${u}</span></td>
      <td><input type="number" class="flt-min" value="${mn}" step="any" style="width:90px" oninput="applyFilter()"/></td>
      <td><input type="number" class="flt-max" value="${mx}" step="any" style="width:90px" oninput="applyFilter()"/></td>
      <td><button class="btn" style="font-size:12px;padding:4px 10px" onclick="resetFilter('${u}',${mn},${mx})">Επαναφορά</button></td>`;
    tbody.appendChild(tr);
  });
  panel.style.display='block';
}
function resetFilter(u,mn,mx){
  const tr=document.querySelector(`#filterBody tr[data-unk="${u}"]`);if(!tr)return;
  tr.querySelector('.flt-min').value=mn;tr.querySelector('.flt-max').value=mx;applyFilter();
}
function getFilteredResults(){
  return allResults.filter(r=>unknownList.every(u=>{
    const tr=document.querySelector(`#filterBody tr[data-unk="${u}"]`);if(!tr)return true;
    const mn=parseFloat(tr.querySelector('.flt-min').value),mx=parseFloat(tr.querySelector('.flt-max').value);
    const v=r.computed[u]?.val??0;return(isNaN(mn)||v>=mn)&&(isNaN(mx)||v<=mx);
  }));
}
function applyFilter(){
  const maxDisplay=parseInt(document.getElementById('maxRes').value)||20;
  document.getElementById('solutionArea').innerHTML='';renderResultsTable(getFilteredResults(),maxDisplay);
}
let _lastTotal=0;
function criteriaStr(){
  return unknownList.map(u=>{
    const prec=getPrecFor(u);
    let s=prec.isInt?`<strong>${u}</strong>: ακέραιος`:`<strong>${u}</strong>: ${prec.dec} δεκαδικ${prec.dec===1?'ό':'ά'}`;
    if(prec.vmin!==null||prec.vmax!==null){const lo=prec.vmin!==null?prec.vmin:'−∞',hi=prec.vmax!==null?prec.vmax:'+∞';s+=` [${lo}, ${hi}]`;}
    return s;
  }).join(' &nbsp;·&nbsp; ');
}
function renderResultsTable(results,maxDisplay){
  const area=document.getElementById('resultsArea');
  const totalFound=allResults.length,filteredLen=results.length,displayed=results.slice(0,maxDisplay);
  const filterNote=filteredLen<totalFound?` — εμφανίζονται <strong style="color:var(--text)">${filteredLen}</strong> μετά το φίλτρο`:'';
  const summary=`<div style="font-size:13px;color:var(--text2);margin-bottom:10px">
    Ελέγχθηκαν <strong style="color:var(--text)">${_lastTotal.toLocaleString('el-GR')}</strong> συνδυασμοί —
    βρέθηκαν <strong style="color:var(--text)">${totalFound}</strong> που πληρούν τα κριτήρια (${criteriaStr()})${filterNote}.
    ${filteredLen?'Κάνε κλικ σε έναν για να δεις τη λύση.':''}
  </div>`;
  if(!filteredLen){area.innerHTML=summary+'<div class="status err">Κανένα αποτέλεσμα εντός του φίλτρου. Άλλαξε τα όρια.</div>';return;}
  const hdrs=[...knownList,...unknownList];
  let html=summary+`<div style="overflow-x:auto"><table class="res"><thead><tr>
    ${hdrs.map(h=>`<th>${h}${units[h]?` <span style="font-weight:400;font-size:11px">(${units[h]})</span>`:''}</th>`).join('')}<th></th>
  </tr></thead><tbody>`;
  displayed.forEach(r=>{
    const origIdx=allResults.indexOf(r);
    html+=`<tr class="res-row" onclick="selectResult(${origIdx})" id="rrow_${origIdx}">`;
    knownList.forEach((v,ki)=>html+=`<td>${formatVal(r.combo[ki],v)}</td>`);
    unknownList.forEach(u=>html+=`<td>${fmtComputed(r.computed[u])}</td>`);
    html+=`<td><button class="btn-sel" onclick="event.stopPropagation();selectResult(${origIdx})">Επιλογή</button></td></tr>`;
  });
  html+='</tbody></table></div>';
  if(filteredLen>maxDisplay)html+=`<div class="truncated-note">Εμφανίζονται οι πρώτοι <strong>${maxDisplay}</strong> από τους <strong>${filteredLen}</strong> συνδυασμούς.</div>`;
  area.innerHTML=html;
}
function showResults(total,maxDisplay){
  _lastTotal=total;goStep(4);
  const badge=document.getElementById('foundBadge');document.getElementById('solutionArea').innerHTML='';
  const totalFound=allResults.length;
  if(!totalFound){
    document.getElementById('filterPanel').style.display='none';badge.innerHTML='';
    document.getElementById('resultsArea').innerHTML=
      `<div style="font-size:13px;color:var(--text2);margin-bottom:10px">Ελέγχθηκαν <strong style="color:var(--text)">${total.toLocaleString('el-GR')}</strong> συνδυασμοί — βρέθηκαν <strong style="color:var(--text)">0</strong> που πληρούν τα κριτήρια (${criteriaStr()}).</div>
      <div class="status err">Κανένας συνδυασμός δεν πληροί τα κριτήρια.<br>Δοκίμασε μεγαλύτερο εύρος, διαφορετικό βήμα ή περισσότερα δεκαδικά ψηφία.</div>`;
    return;
  }
  badge.innerHTML=`<span style="display:inline-block;font-size:11px;padding:2px 10px;border-radius:99px;background:var(--green-bg);color:var(--green);border:1px solid var(--green-bdr);margin-left:8px">${totalFound} συνδυασμοί</span>`;
  buildFilterPanel();renderResultsTable(allResults,maxDisplay);
}
function selectResult(i){
  document.querySelectorAll('.res-row').forEach(r=>r.classList.remove('selected'));
  document.getElementById('rrow_'+i)?.classList.add('selected');
  const r=allResults[i];if(!r)return;
  let rows=`<tr class="sol-divider"><td colspan="4"><span>Δεδομένα</span></td></tr>`;
  knownList.forEach((v,ki)=>{
    const dispVal=formatVal(r.combo[ki],v);const u=units[v]||'';
    rows+=`<tr class="sol-known"><td class="sol-var">\\(${v}\\)</td><td class="sol-eq">=</td><td class="sol-val">${dispVal}</td><td class="sol-unit">${u?`<span style="font-size:15px;color:var(--text2)">${u}</span>`:''}</td></tr>`;
  });
  rows+=`<tr class="sol-divider"><td colspan="4"><span>Ζητούμενα</span></td></tr>`;
  unknownList.forEach(u=>{
    const val=fmtComputed(r.computed[u]);const unit=units[u]||'';
    rows+=`<tr class="sol-unknown"><td class="sol-var">\\(${u}\\)</td><td class="sol-eq">=</td><td class="sol-val">${val}</td><td class="sol-unit">${unit?`<span style="font-size:15px;color:var(--text2)">${unit}</span>`:''}</td></tr>`;
  });
  document.getElementById('solutionArea').innerHTML=`<div class="solution-card"><div class="sol-header">Λύση</div><table class="sol-table">${rows}</table></div>`;
  if(window.MathJax&&MathJax.typesetPromise)MathJax.typesetPromise([document.getElementById('solutionArea')]);
  document.getElementById('solutionArea').scrollIntoView({behavior:'smooth',block:'nearest'});
}
function resetAll(){
  eqCount=0;equations=[];allResults=[];
  ['knownVars','unknownVars'].forEach(id=>document.getElementById(id).value='');
  ['knownTags','unknownTags','eqList','rangeBody','precBody','filterBody','unitsBody','solutionArea','resultsArea'].forEach(id=>document.getElementById(id).innerHTML='');
  document.getElementById('totalBox').style.display='none';document.getElementById('unitsSection').style.display='none';
  document.getElementById('foundBadge').innerHTML='';document.getElementById('filterPanel').style.display='none';
  goStep(1);
}
</script>
{% endraw %}

---

## 📖 Οδηγίες χρήσης

### Τρόπος 1: Χρήση Online (Απλούστερο)

Απλά χρησιμοποιήστε την εφαρμογή πάνω σε αυτή τη σελίδα! Δεν χρειάζεται να κατεβάσετε τίποτα.

### Τρόπος 2: Κατέβασμα και Χρήση Offline

#### Βήμα 1: Κατέβασμα

## 💾 Λήψη από Google Drive

[📥 Κατέβασμα Εφαρμογής](https://drive.google.com/uc?export=download&id=14CJOFetc9shrtdv8hSzItQzr5ispobu7)

**Σημαντικό για Windows:**
- Αν ο browser σας ρωτήσει "Keep" ή "Discard", πατήστε **Keep**
- Αν εμφανιστεί προειδοποίηση ασφαλείας, πατήστε **Keep anyway** (το αρχείο είναι αρχείο html 100% ασφαλές)

#### Βήμα 2: Αποθήκευση

Το αρχείο θα αποθηκευτεί στον φάκελο **Downloads** (Λήψεις) του υπολογιστή σας.

#### Βήμα 3: Άνοιγμα

**Για Windows/Mac/Linux:**
- Βρείτε το αρχείο στον φάκελο Λήψεις
- Κάντε **διπλό κλικ** πάνω του
- Θα ανοίξει αυτόματα στον browser σας (Chrome, Firefox, Safari, Edge)

**Εναλλακτικά:**
- Δεξί κλικ στο αρχείο → **Open with** → Επιλέξτε τον browser σας

#### Βήμα 4: Χρήση

Τώρα μπορείτε να χρησιμοποιήσετε την εφαρμογή όποτε θέλετε, ακόμα και χωρίς Internet!

**💡 Συμβουλή:** Αντιγράψτε το αρχείο στην Επιφάνεια Εργασίας για πιο εύκολη πρόσβαση.

---

### Αντιμετώπιση Προβλημάτων

#### ❓ Τα μαθηματικά σύμβολα δεν φαίνονται σωστά

Χρειάζεται Internet την πρώτη φορά για να φορτώσει το MathJax. Μετά από αυτό, θα δουλεύει και offline.

#### ❓ Δεν βρίσκει αποτελέσματα ενώ γνωρίζω ότι υπάρχουν

- Έλεγξε το **βήμα** αναζήτησης — π.χ. αν κάποια μεταβλητή παίρνει τιμή 0.6, το βήμα πρέπει να είναι 0.1 ή 0.2.
- Έλεγξε το **κριτήριο αποδοχής** — αν το αποτέλεσμα είναι 0.4, επίλεξε "Δεκαδικός, 1 ψηφίο" αντί για "Ακέραιος".
- Διεύρυνε το **εύρος αναζήτησης** των δεδομένων.

---

### 📱 Χρήση σε Κινητό/Tablet

Η εφαρμογή λειτουργεί και σε κινητές συσκευές!

**Android:** Ανοίξτε τη σελίδα με Chrome ή Firefox.

**iOS (iPhone/iPad):** Ανοίξτε τη σελίδα με Safari.

---

### 🎯 Tips για Καλύτερη Εμπειρία

1. **Αποθήκευση Δεδομένων**: Προς το παρόν η εφαρμογή δεν αποθηκεύει δεδομένα. Σημειώστε τα αποτελέσματά σας!
2. **Πολλά αποτελέσματα**: Χρησιμοποιήστε το φίλτρο αποτελεσμάτων ή ορίστε εύρος τιμών στα κριτήρια αποδοχής.

---

### 🆘 Χρειάζεστε Βοήθεια;

Αν έχετε πρόβλημα, επικοινωνήστε μαζί μου μέσω:
- Email: [sch(at)sch.gr]

ή στα social media buttons!
