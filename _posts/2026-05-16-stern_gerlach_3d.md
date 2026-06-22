---
layout: post
title: "Πείραμα Stern–Gerlach 3D"
description: "Διαδραστική τρισδιάστατη προσομοίωση του πειράματος Stern–Gerlach για τη διδασκαλία της κβάντωσης της στροφορμής"
category: Προσομοίωση
tags: [Κβαντική Φυσική]
---

# Διαδραστική Προσομοίωση Πειράματος Stern–Gerlach

Τρισδιάστατη προσομοίωση του ιστορικού πειράματος Stern–Gerlach (1922) για τη διδασκαλία της **κβάντωσης της στροφορμής** στη Φυσική Γ΄ Λυκείου.

## Χαρακτηριστικά

- ✅ Τρισδιάστατη απεικόνιση μαγνήτη με λεπίδα (knife-edge) και κοίλη επιφάνεια (αυλάκι)
- ✅ Ακτινική εξάπλωση ατόμων Ag από τον κλίβανο — ρεαλιστική κολλιμάτωση από σχισμές
- ✅ Στιγμιαία ίχνη πρόσκρουσης στις επιφάνειες των σχισμών
- ✅ Σταδιακή συσσώρευση κηλίδων στη φωτογραφική πλάκα (2D + 3D)
- ✅ Περιστροφή μαγνήτη (0° / 90°) — αλλάζει ο προσανατολισμός των γραμμών στην πλάκα
- ✅ Τέσσερα σενάρια: Ag (s=½), ²H (s=1), Na (s=½), spin-3/2
- ✅ Orbit camera (drag ποντίκι / zoom scroll)
- ✅ Δυναμικές γραμμές μαγνητικού πεδίου με βέλη φοράς (κλιμακώνονται με ∂B/∂z)
- ✅ Φύλλα εργασίας (Ανοιχτή & Καθοδηγούμενη Διερεύνηση) — άμεση λήψη

---

<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

<style>
#sg3d-wrap * { box-sizing: border-box; margin: 0; padding: 0; }
#sg3d-wrap {
  width: 100%;
  margin: -20px -20px 20px -20px;
  padding: 0;
}
#sg3d-wrap :root{--bg:#070b14;--panel:#0f1525;--brd:#1a2840;--acc:#00c8ff;--gold:#ffd166;--grn:#06d6a0;--mag:#d55aff;--org:#ff6b35;--txt:#c8d8f0;--dim:#6a80a0}
*{box-sizing:border-box;margin:0;padding:0}
#sg3d-wrap {height:100%;overflow:hidden}
body{background:var(--bg);color:var(--txt);font-family:Arial,sans-serif;display:flex;flex-direction:column}
header{background:#0a1020;border-bottom:1px solid var(--brd);padding:7px 16px;display:flex;align-items:center;gap:10px;flex-shrink:0}
header h1{font-size:15px;font-weight:700;color:var(--acc);letter-spacing:1px}
header h1 span{color:var(--dim);font-weight:400;font-size:10px;display:block}
.main{display:grid;grid-template-columns:260px 1fr 280px;flex:1;min-height:0;overflow:hidden}
.panel{background:var(--panel);padding:9px 11px;overflow-y:auto;display:flex;flex-direction:column;gap:7px;font-size:12px}
.L{border-right:1px solid var(--brd)} .R{border-left:1px solid var(--brd)}
.st{font-size:10px;font-weight:700;letter-spacing:2px;color:var(--dim);text-transform:uppercase;padding-bottom:3px;border-bottom:1px solid var(--brd)}
.scg{display:grid;grid-template-columns:repeat(4,1fr);gap:3px}
.sb{background:var(--bg);border:1px solid var(--brd);color:var(--dim);padding:5px 2px;border-radius:4px;cursor:pointer;text-align:center;font-size:10px;font-weight:700;display:flex;flex-direction:column;align-items:center;gap:1px}
.sb:hover,.sb.on{border-color:var(--mag);color:var(--mag);background:rgba(213,90,255,0.1)}
.sb .sy{font-size:14px} .sb .su{font-size:8px} .sb .sb2{font-size:7px}
.ctrl{display:flex;flex-direction:column;gap:3px}
.cl{display:flex;justify-content:space-between;align-items:center;font-size:11px}
.cl .v{font-family:monospace;font-size:10px;color:var(--acc);background:rgba(0,200,255,0.1);padding:1px 4px;border-radius:3px}
input[type=range]{-webkit-appearance:none;width:100%;height:4px;background:var(--brd);border-radius:2px;cursor:pointer}
input[type=range]::-webkit-slider-thumb{-webkit-appearance:none;width:12px;height:12px;border-radius:50%;background:var(--acc)}
.btn{padding:7px;border:none;border-radius:4px;cursor:pointer;font-weight:700;font-size:12px;letter-spacing:1px;display:flex;align-items:center;justify-content:center;gap:4px}
.bgo{background:var(--acc);color:#000} .bgo:disabled{background:var(--brd);color:var(--dim);cursor:not-allowed}
.bst{background:transparent;border:1px solid var(--brd);color:var(--dim)}
.bclr{background:transparent;border:1px solid #f44;color:#f44;font-size:11px;padding:5px}
.bws{background:rgba(255,209,102,0.08);border:1px solid rgba(255,209,102,0.3);color:var(--gold);font-size:11px;padding:6px;text-align:left;justify-content:flex-start;gap:5px}
.ic{background:var(--bg);border:1px solid var(--brd);border-radius:4px;padding:6px 8px;display:flex;flex-direction:column;gap:3px}
.ir{display:flex;justify-content:space-between;align-items:center;font-size:11px}
.ir .k{color:var(--dim)} .ir .vv{font-family:monospace;font-size:10px}
.g{color:var(--grn)} .m{color:var(--mag)} .o{color:var(--org)}
.ins{background:rgba(213,90,255,0.05);border:1px solid rgba(213,90,255,0.18);border-radius:4px;padding:7px 8px}
.ins-t{font-size:9px;letter-spacing:2px;color:var(--mag);text-transform:uppercase;margin-bottom:2px}
.ins-r{font-size:11px;color:var(--dim);line-height:1.55;margin-bottom:2px} .ins-r .ih{color:var(--txt);font-weight:700}
.vb{background:rgba(6,214,160,0.04);border:1px solid rgba(6,214,160,0.2);border-radius:4px;padding:7px 8px}
.vb-t{font-size:9px;letter-spacing:2px;color:var(--grn);text-transform:uppercase;margin-bottom:3px}
.veq{font-family:monospace;font-size:10px;color:var(--dim);margin-bottom:2px;line-height:1.5} .veq .ev{color:var(--txt)}
.vm{margin-top:3px;font-size:10px;font-weight:700;text-align:center;padding:3px;border-radius:3px;background:rgba(6,214,160,0.1);color:var(--grn)}
.bl{display:flex;flex-direction:column;gap:2px}
.bi{background:var(--bg);border:1px solid var(--brd);border-radius:3px;padding:3px 5px;font-size:10px;display:flex;align-items:center;gap:3px}
.bi .dot{width:6px;height:6px;border-radius:50%;flex-shrink:0} .bi .mj{color:var(--mag);font-family:monospace;min-width:48px} .bi .dir{color:var(--dim);flex:1} .bi .dz{color:var(--gold);font-family:monospace}
.abt{font-size:10px;color:var(--dim);line-height:1.6;padding:5px 7px;background:var(--bg);border:1px solid var(--brd);border-radius:4px} .abt .ih{color:var(--txt);font-weight:700}
.ccb{font-size:9px;color:var(--dim);line-height:1.6;padding:6px;background:rgba(0,200,255,0.02);border:1px solid var(--brd);border-radius:3px} .ccb a{color:var(--acc)}
.ctr{position:relative;display:flex;flex-direction:column;overflow:hidden}
#cv3d{display:block;cursor:grab} #cv3d:active{cursor:grabbing}
.rind{position:absolute;top:8px;left:50%;transform:translateX(-50%);background:rgba(0,200,255,0.12);border:1px solid rgba(0,200,255,0.34);color:var(--acc);font-size:10px;letter-spacing:2px;padding:3px 10px;border-radius:15px;display:none;align-items:center;gap:4px;z-index:10}
.rind.on{display:flex} .pd{width:5px;height:5px;border-radius:50%;background:var(--acc);animation:pu 1s infinite}
@keyframes pu{0%,100%{opacity:1}50%{opacity:.3}}
.rot-wrap{position:absolute;bottom:8px;right:8px;display:flex;flex-direction:column;align-items:flex-end;gap:3px;z-index:5}
.rot-lbl{font-size:9px;letter-spacing:1px;color:var(--dim)}
.rot-btns{display:flex;gap:4px}
.rb{background:rgba(0,200,255,0.08);border:1px solid rgba(0,200,255,0.28);color:var(--dim);font-size:10px;font-weight:700;padding:4px 8px;border-radius:4px;cursor:pointer}
.rb.on{border-color:var(--gold);color:var(--gold);background:rgba(255,209,102,0.12)}
.rot-info{font-family:monospace;font-size:9px;color:var(--gold)}
.hint{position:absolute;bottom:8px;left:8px;font-size:8px;color:rgba(200,216,240,0.25);pointer-events:none}
#plateCv{display:block;border-radius:4px;border:1px solid var(--brd);background:#06080f}
hr.d{border:none;border-top:1px solid var(--brd);margin:0}
.mov{display:none;position:fixed;inset:0;background:rgba(0,0,0,.75);z-index:100;align-items:center;justify-content:center}
.mov.open{display:flex} .mbx{background:var(--panel);border:1px solid var(--brd);border-radius:8px;max-width:380px;width:90%;padding:16px;display:flex;flex-direction:column;gap:9px}
.mt{font-size:14px;font-weight:700;color:var(--acc)}
::-webkit-scrollbar{width:3px} ::-webkit-scrollbar-thumb{background:var(--brd);border-radius:2px}
</style>

<div id="sg3d-wrap">
<header><span style="font-size:20px">&#x26DB;</span>
<h1>Πείραμα Stern–Gerlach<span>ΚΒΑΝΤΩΣΗ ΣΤΡΟΦΟΡΜΗΣ · ΦΥΣΙΚΗ Γ΄ ΛΥΚΕΙΟΥ</span></h1></header>
<div class="main">
<div class="panel L">
<div class="st">Σενάριο</div>
<div class="scg" id="scGrid"></div>
<hr class="d">
<div class="st">Παράμετροι</div>
<div class="ctrl"><div class="cl">&part;B/&part;z <span class="v" id="gV">5.0 T/m</span></div><input type="range" id="gS" min="1" max="20" value="5" step="0.5"></div>
<div class="ctrl"><div class="cl">Μήκος L <span class="v" id="lV">0.10 m</span></div><input type="range" id="lS" min="0.02" max="0.30" value="0.10" step="0.01"></div>
<div class="ctrl"><div class="cl">Ταχύτητα v <span class="v" id="vV">500 m/s</span></div><input type="range" id="vS" min="100" max="2000" value="500" step="10"></div>
<div class="ctrl"><div class="cl">Ρυθμός <span class="v" id="rV">Μέσαιος</span></div><input type="range" id="rS" min="1" max="3" value="2" step="1"></div>
<div class="ic">
<div class="ir"><span class="k">Δέσμες (2s+1)</span><span class="vv m" id="nbV">-</span></div>
<div class="ir"><span class="k">Μέγ. εκτροπή</span><span class="vv o" id="mdV">-</span></div>
<div class="ir"><span class="k">Δύναμη max</span><span class="vv g" id="fmV">-</span></div>
</div><hr class="d">
<div class="st">Έλεγχος</div>
<button class="btn bgo" id="startBtn">&#x25B6; ΕΝΑΡΞΗ</button>
<button class="btn bst" id="stopBtn" disabled>&#x23F9; ΔΙΑΚΟΠΗ</button>
<button class="btn bclr" id="clearBtn">&#x2715; Εκκαθάριση</button>
<hr class="d">
<div class="st">Φύλλα Εργασίας</div>
<button class="btn bws" onclick="document.getElementById('wsModal').classList.add('open')">&#x1F4C4; Επιλογή Φύλλου</button>
</div>
<div class="ctr">
<div class="rind" id="rind"><div class="pd"></div>ΠΡΟΣΟΜΟΊΩΣΗ</div>
<canvas id="cv3d"></canvas>
<div class="rot-wrap">
<div class="rot-lbl">ΠΡΟΣΑΝΑΤΟΛΙΣΜΟΣ ΜΑΓΝΗΤΗ</div>
<div class="rot-btns">
<button class="rb on" id="rb0" onclick="setRot(0)">&#x2195; 0&deg;</button>
<button class="rb" id="rb90" onclick="setRot(90)">&#x2194; 90&deg;</button>
</div>
<div class="rot-info" id="rotInfo">Γραμμές οριζόντιες</div>
</div>
<div class="hint">&#x1F5B1; Drag: περιστροφή | Scroll: zoom</div>
</div>
<div class="panel R">
<div class="st">Αποτελέσματα</div>
<div class="ins"><div class="ins-t">&#x2666; Παρατηρήσεις</div>
<div class="ins-r" id="ins1">-</div><div class="ins-r" id="ins2">-</div></div>
<div class="vb"><div class="vb-t">&#x2666; Εκτροπή</div>
<div class="veq">F = m&#x2C7C;&middot;g&#x2C7C;&middot;&mu;<sub>B</sub>&middot;(&part;B/&part;z) = <span class="ev" id="vF">-</span></div>
<div class="veq">|&Delta;z|<sub>max</sub> = <span class="ev" id="vDz">-</span></div>
<div class="vm" id="vM">Ρυθμίστε παραμέτρους</div></div>
<hr class="d">
<div class="st">Δέσμες &amp; m&#x2C7C;</div>
<div class="bl" id="bList"></div>
<hr class="d">
<div class="st">Φωτογραφική Πλάκα</div>
<canvas id="plateCv" width="258" height="88"></canvas>
<div style="font-size:9px;color:var(--dim);margin-top:2px;">Σταδιακή συσσώρευση κηλίδων</div>
<hr class="d">
<div class="st">Σχετικά</div>
<div class="abt" id="abtDiv">-</div>
<div class="ccb">Δημιουργία – Ανάπτυξη: <strong style="color:var(--txt)">Παναγιώτης Πετρίδης</strong><br>
<a href="https://creativecommons.org/licenses/by-nc-sa/4.0/deed.el" target="_blank">CC BY-NC-SA 4.0</a> | sch(at)sch.gr</div>
</div></div>
<div class="mov" id="wsModal"><div class="mbx">
<div class="mt">&#x1F4C4; Επιλογή Φύλλου Εργασίας</div>
<button class="btn bws" style="font-size:11px;padding:8px;" onclick="dlWS(0)">&#x1F52C; Ανοιχτή Διερεύνηση</button>
<button class="btn bws" style="font-size:11px;padding:8px;" onclick="dlWS(1)">&#x1F4CB; Καθοδηγούμενη Διερεύνηση</button>
<button class="btn bst" style="align-self:flex-end;font-size:11px;" onclick="document.getElementById('wsModal').classList.remove('open')">&#x2715; Κλείσιμο</button>
</div></div>
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
<script>
var SC=[
  {lbl:"Ag",sub:"s=\u00bd",bt:"2 \u03b4\u03ad\u03c3\u03bc\u03b5\u03c2",name:"\u0391\u03c1\u03b3\u03c5\u03c1\u03bf\u03c2",mass:1.791e-25,spin:0.5,
   fact:"\u0399\u03c3\u03c4\u03bf\u03c1\u03b9\u03ba\u03cc \u03c0\u03b5\u03af\u03c1\u03b1\u03bc\u03b1 (1922): <ih>2 \u03b4\u03ad\u03c3\u03bc\u03b5\u03c2</ih>. \u039c\u03bf\u03bd\u03ae\u03c1\u03b5\u03c2 e\u207b 5s\u00b9 \u03bc\u03ad\u03c3\u03b1 \u03c3\u03c4\u03bf \u03bf\u03c5\u03b4\u03ad\u03c4\u03b5\u03c1\u03bf \u03ac\u03c4\u03bf\u03bc\u03bf.",
   abt:"\u0394\u03cd\u03bd\u03b1\u03bc\u03b7: <ih>F=\u2207(\u03bc\u00b7B)</ih>. \u039c\u03bf\u03bd\u03ae\u03c1\u03b5\u03c2 e\u207b 5s\u00b9, q=0, \u03ba\u03b1\u03bc\u03af\u03b1 Lorentz."},
  {lbl:"\u00b2H",sub:"s=1",bt:"3 \u03b4\u03ad\u03c3\u03bc\u03b5\u03c2",name:"\u0394\u03b5\u03c5\u03c4\u03ad\u03c1\u03b9\u03bf",mass:3.344e-27,spin:1.0,
   fact:"\u03a0\u03c5\u03c1\u03ae\u03bd\u03b1\u03c2 \u00b2H spin <ih>s=1</ih>: <ih>3 \u03b4\u03ad\u03c3\u03bc\u03b5\u03c2</ih>. m\u2c7c=0 \u03b4\u03b5\u03bd \u03b5\u03ba\u03c4\u03c1\u03ad\u03c0\u03b5\u03c4\u03b1\u03b9.",
   abt:"\u0394\u03cd\u03bd\u03b1\u03bc\u03b7: F=\u2207(\u03bc\u00b7B). q=0."},
  {lbl:"Na",sub:"s=\u00bd",bt:"2 \u03b4\u03ad\u03c3\u03bc\u03b5\u03c2",name:"\u039d\u03ac\u03c4\u03c1\u03b9\u03bf",mass:3.818e-26,spin:0.5,
   fact:"Na spin <ih>s=\u00bd</ih>, 2 \u03b4\u03ad\u03c3\u03bc\u03b5\u03c2. \u039c\u03b5\u03b3\u03b1\u03bb\u03cd\u03c4\u03b5\u03c1\u03b7 \u03bc\u03ac\u03b6\u03b1 \u2192 \u03bc\u03b9\u03ba\u03c1\u03cc\u03c4\u03b5\u03c1\u03b7 \u03b5\u03ba\u03c4\u03c1\u03bf\u03c0\u03ae.",
   abt:"\u0394\u03cd\u03bd\u03b1\u03bc\u03b7: F=\u2207(\u03bc\u00b7B). q=0."},
  {lbl:"s=\u00be",sub:"s=3/2",bt:"4 \u03b4\u03ad\u03c3\u03bc\u03b5\u03c2",name:"spin-3/2",mass:1.791e-25,spin:1.5,
   fact:"Spin <ih>s=3/2</ih>: <ih>4 \u03b4\u03ad\u03c3\u03bc\u03b5\u03c2</ih>. \u0393\u03b5\u03bd. \u03ba\u03b1\u03bd\u03cc\u03bd\u03b1\u03c2: 2s+1.",
   abt:"\u0394\u03cd\u03bd\u03b1\u03bc\u03b7: F=\u2207(\u03bc\u00b7B). q=0."},
];

var muB=9.2741e-24, gjF=2.0023;
var BCOL=['#ff6b35','#ffd166','#e8eeff','#00c8ff','#06d6a0','#d55aff'];
var curSc=0, running=false, magRotDeg=0;
var deflections=[], particles=[], flashes=[], spawnT=0;
var plateMarks=[];
// Slits moved closer to magnet
var SLIT_X1=-2.2, SLIT_X2=-1.95, SLIT_GAP=0.16;

var cv=document.getElementById('cv3d');
var renderer=new THREE.WebGLRenderer({canvas:cv,antialias:true});
renderer.setPixelRatio(window.devicePixelRatio);
renderer.shadowMap.enabled=true;
var scene=new THREE.Scene(); scene.background=new THREE.Color(0x070b14);
var camera=new THREE.PerspectiveCamera(45,2,0.1,100);
var sph={th:0.3,phi:1.1,r:9};
function camUpd(){
  camera.position.set(sph.r*Math.sin(sph.phi)*Math.sin(sph.th),sph.r*Math.cos(sph.phi),sph.r*Math.sin(sph.phi)*Math.cos(sph.th));
  camera.lookAt(0,0,0);
}
camUpd();
scene.add(new THREE.AmbientLight(0x223355,1.4));
var dl=new THREE.DirectionalLight(0xffffff,1.5); dl.position.set(3,5,4); dl.castShadow=true; scene.add(dl);
var pl=new THREE.PointLight(0xaa44ff,1.0,12); pl.position.set(-2,1,2); scene.add(pl);

var drag=false,pm={x:0,y:0};
cv.addEventListener('mousedown',function(e){drag=true;pm={x:e.clientX,y:e.clientY};});
window.addEventListener('mouseup',function(){drag=false;});
window.addEventListener('mousemove',function(e){
  if(!drag)return;
  sph.th-=(e.clientX-pm.x)*0.008;
  sph.phi=Math.max(0.2,Math.min(Math.PI-0.2,sph.phi+(e.clientY-pm.y)*0.008));
  pm={x:e.clientX,y:e.clientY}; camUpd();
});
cv.addEventListener('wheel',function(e){sph.r=Math.max(3,Math.min(20,sph.r+e.deltaY*0.01));camUpd();e.preventDefault();},{passive:false});
cv.addEventListener('touchstart',function(e){pm={x:e.touches[0].clientX,y:e.touches[0].clientY};},{passive:true});
cv.addEventListener('touchmove',function(e){
  sph.th-=(e.touches[0].clientX-pm.x)*0.01;
  sph.phi=Math.max(0.2,Math.min(Math.PI-0.2,sph.phi+(e.touches[0].clientY-pm.y)*0.01));
  pm={x:e.touches[0].clientX,y:e.touches[0].clientY}; camUpd(); e.preventDefault();
},{passive:false});

var matN=new THREE.MeshPhongMaterial({color:0x2a1060,specular:0xaa44ff,shininess:60});
var matNk=new THREE.MeshPhongMaterial({color:0x4020a0,specular:0xdd88ff,shininess:120});
var matS=new THREE.MeshPhongMaterial({color:0x0d2040,specular:0x4488ff,shininess:50,side:THREE.DoubleSide});
var matOv=new THREE.MeshPhongMaterial({color:0x5a2810,specular:0xff8833,shininess:40});
var matSl=new THREE.MeshPhongMaterial({color:0x1a2545,specular:0x8899cc,shininess:30});
var matPl=new THREE.MeshPhongMaterial({color:0x1a0840,specular:0xaa66ff,shininess:80,transparent:true,opacity:0.88});

var expG=new THREE.Group(); scene.add(expG);
var magG=new THREE.Group(); expG.add(magG);
var partG=new THREE.Group(); expG.add(partG);
var markG=new THREE.Group(); expG.add(markG);

function mkLbl(txt,pos,sz,col,grp){
  var cv2=document.createElement('canvas'); cv2.width=256; cv2.height=56;
  var c=cv2.getContext('2d');
  c.font='bold '+Math.round(sz*140)+'px Arial';
  c.fillStyle=col||'#fff'; c.textAlign='center'; c.textBaseline='middle';
  c.fillText(txt,128,28);
  var tex=new THREE.CanvasTexture(cv2);
  var sp=new THREE.Sprite(new THREE.SpriteMaterial({map:tex,transparent:true,depthWrite:false}));
  sp.position.copy(pos); sp.scale.set(sz*2.6,sz*0.56,1);
  (grp||expG).add(sp);
}

// Oven
(function(){
  var g=new THREE.BoxGeometry(0.72,0.72,0.72);
  var m=new THREE.Mesh(g,matOv); m.position.set(-4.5,0,0); m.castShadow=true; expG.add(m);
  var og=new THREE.CircleGeometry(0.07,16);
  var om=new THREE.Mesh(og,new THREE.MeshBasicMaterial({color:0xffee88}));
  om.position.set(-4.149,0,0); om.rotation.y=Math.PI/2; expG.add(om);
  mkLbl("\u039a\u03bb\u03af\u03b2\u03b1\u03bd\u03bf\u03c2",new THREE.Vector3(-4.5,0.72,0),0.26,"#ffcc44");
})();

// Slits - closer to magnet, narrower gap
(function(){
  var blockH=0.85;
  [SLIT_X1,SLIT_X2].forEach(function(sx){
    [1,-1].forEach(function(sign){
      var g=new THREE.BoxGeometry(0.06,blockH,0.55);
      var m=new THREE.Mesh(g,matSl);
      m.position.set(sx,sign*(SLIT_GAP/2+blockH/2),0);
      expG.add(m);
    });
  });
  mkLbl("\u03a3\u03c7\u03b9\u03c3\u03bc\u03ad\u03c2",new THREE.Vector3((SLIT_X1+SLIT_X2)/2,0.95,0),0.32,"#aaccee");
})();

// Magnet
var flG=new THREE.Group();
function buildMagnet(){
  var savedRot=magG.rotation.x;
  while(magG.children.length>0){var c=magG.children[0];if(c.geometry)c.geometry.dispose();if(c.material)c.material.dispose();magG.remove(c);}
  var Lm=parseFloat(document.getElementById('lS').value);
  var mX=1.0+(Lm-0.02)/(0.30-0.02)*2.8;
  var mZ=2.0,mH=0.8,hg=0.44;
  var gN=new THREE.BoxGeometry(mX,mH,mZ);
  var mN=new THREE.Mesh(gN,matN); mN.position.set(0,hg+mH/2,0); mN.castShadow=true; magG.add(mN);
  var edgN=new THREE.LineSegments(new THREE.EdgesGeometry(gN),new THREE.LineBasicMaterial({color:0xaa55ff,transparent:true,opacity:0.5}));
  edgN.position.copy(mN.position); magG.add(edgN);
  var kw=0.28,kh=0.24;
  var ks=new THREE.Shape(); ks.moveTo(-kw,0); ks.lineTo(kw,0); ks.lineTo(0,-kh); ks.closePath();
  var kg=new THREE.ExtrudeGeometry(ks,{depth:mX,bevelEnabled:false});
  var km=new THREE.Mesh(kg,matNk); km.rotation.y=Math.PI/2; km.position.set(-mX/2,hg,0); km.castShadow=true; magG.add(km);
  var gS=new THREE.BoxGeometry(mX,mH,mZ);
  var mS=new THREE.Mesh(gS,matS); mS.position.set(0,-(hg+mH/2),0); mS.castShadow=true; magG.add(mS);
  var edgS=new THREE.LineSegments(new THREE.EdgesGeometry(gS),new THREE.LineBasicMaterial({color:0x5588ff,transparent:true,opacity:0.4}));
  edgS.position.copy(mS.position); magG.add(edgS);
  var gr=0.42,gs=18;
  var gsh=new THREE.Shape();
  for(var i=0;i<=gs;i++){var a=Math.PI+(i/gs)*Math.PI;if(i===0)gsh.moveTo(gr*Math.cos(a),gr*Math.sin(a));else gsh.lineTo(gr*Math.cos(a),gr*Math.sin(a));}
  gsh.lineTo(gr,0); gsh.lineTo(-gr,0); gsh.closePath();
  var gg=new THREE.ExtrudeGeometry(gsh,{depth:mX,bevelEnabled:false});
  var gm=new THREE.Mesh(gg,new THREE.MeshPhongMaterial({color:0x0a1830,specular:0x2255aa,shininess:90,side:THREE.FrontSide}));
  gm.rotation.y=Math.PI/2; gm.position.set(-mX/2,-hg,0); magG.add(gm);
  mkLbl("N",new THREE.Vector3(0,hg+mH+0.18,0),0.30,"#cc66ff",magG);
  mkLbl("S",new THREE.Vector3(0,-(hg+mH+0.18),0),0.30,"#5588ff",magG);
  mkLbl("\u039c\u03b1\u03b3\u03bd\u03ae\u03c4\u03b7\u03c2",new THREE.Vector3(0,hg+mH+0.52,0),0.24,"#cc88ff",magG);

  buildFieldLines(mX,mZ,hg,kh);
  magG.rotation.x=savedRot;
}

function buildFieldLines(mX,mZ,hg,kh){
  magG.remove(flG); flG=new THREE.Group();
  var dBdz=parseFloat(document.getElementById('gS').value);
  var nX=Math.round(5+(dBdz-1)/19*13), nL=7;
  var tipY=hg-kh, sY=-hg+0.06;
  for(var xi=0;xi<nX;xi++){
    var x=-mX/2*0.82+(xi/(nX-1))*mX*0.82;
    for(var li=0;li<nL;li++){
      var t=li/(nL-1), zEnd=(t-0.5)*mZ*0.72, gSY=sY-0.08*zEnd*zEnd;
      var curve=new THREE.QuadraticBezierCurve3(new THREE.Vector3(x,tipY,0),new THREE.Vector3(x,(tipY+gSY)*0.5,zEnd*0.3),new THREE.Vector3(x,gSY,zEnd));
      var pts=curve.getPoints(16);
      var alpha=0.10+0.35*(1-Math.abs(t-0.5)*2.2);
      flG.add(new THREE.Line(new THREE.BufferGeometry().setFromPoints(pts),new THREE.LineBasicMaterial({color:0xaa66ff,transparent:true,opacity:Math.max(0.07,alpha)})));
      var ap=curve.getPoint(0.55),ad=curve.getTangent(0.55).normalize();
      var ah=new THREE.ArrowHelper(ad,ap,0.13,0xaa66ff,0.08,0.05);
      ah.line.material.transparent=true; ah.line.material.opacity=Math.max(0.09,alpha);
      ah.cone.material.transparent=true; ah.cone.material.opacity=Math.max(0.09,alpha);
      flG.add(ah);
    }
  }
  magG.add(flG);
}

// Plate
(function(){
  var g=new THREE.BoxGeometry(0.07,2.4,2.0);
  var m=new THREE.Mesh(g,matPl); m.position.set(3.5,0,0); expG.add(m);
  var edgPl=new THREE.LineSegments(new THREE.EdgesGeometry(g),new THREE.LineBasicMaterial({color:0xcc88ff,transparent:true,opacity:0.5}));
  edgPl.position.copy(m.position); expG.add(edgPl);
  mkLbl("\u03a6\u03c9\u03c4\u03bf\u03b3\u03c1. \u03a0\u03bb\u03ac\u03ba\u03b1",new THREE.Vector3(3.5,1.55,0),0.24,"#cc88ff");
})();

var pCv=document.getElementById('plateCv'), pCtx=pCv.getContext('2d');
function drawPlate2D(){
  var W=pCv.width,H=pCv.height;
  pCtx.clearRect(0,0,W,H);
  pCtx.fillStyle='#06080f'; pCtx.fillRect(0,0,W,H);
  pCtx.strokeStyle='rgba(213,90,255,0.35)'; pCtx.lineWidth=1; pCtx.strokeRect(1,1,W-2,H-2);
  if(!plateMarks.length) return;
  var maxDz=0;
  for(var i=0;i<deflections.length;i++) if(Math.abs(deflections[i].dz_mm)>maxDz) maxDz=Math.abs(deflections[i].dz_mm);
  if(!maxDz) maxDz=1;
  var rotX=magRotDeg*Math.PI/180, cx=W/2, cy=H/2;
  var sclD=Math.min(H,W)*0.28/maxDz;
  var sclZ=Math.min(H,W)*0.28/(SLIT_GAP/2*0.9);
  for(var i=0;i<plateMarks.length;i++){
    var mk=plateMarks[i];
    var defPx=mk.dz*Math.cos(rotX)*sclD, defPz=mk.dz*Math.sin(rotX)*sclD;
    var ribPx=mk.rib*Math.cos(rotX+Math.PI/2)*sclZ, ribPz=mk.rib*Math.sin(rotX+Math.PI/2)*sclZ;
    pCtx.fillStyle=mk.c; pCtx.globalAlpha=0.72;
    pCtx.beginPath(); pCtx.arc(cx+defPz+ribPz,cy-defPx-ribPx,1.8,0,Math.PI*2); pCtx.fill();
  }
  pCtx.globalAlpha=1;
}

function calcDefl(){
  var sc=SC[curSc];
  var v=parseFloat(document.getElementById('vS').value);
  var dBdz=parseFloat(document.getElementById('gS').value);
  var Lm=parseFloat(document.getElementById('lS').value);
  var m=sc.mass,s=sc.spin,D=Lm,tm=Lm/v;
  var nMj=Math.round(2*s+1), cOff=Math.max(0,Math.floor((BCOL.length-nMj)/2));
  deflections=[];
  for(var k=0;k<nMj;k++){
    var mj=-s+k, F=mj*gjF*muB*dBdz, a=F/m;
    var dz=(0.5*a*tm*tm+a*tm*(D/v))*1000;
    deflections.push({mj:Number.isInteger(mj)?mj.toFixed(0):mj.toFixed(1),dz_mm:dz,F:F,color:BCOL[cOff+k]||'#fff'});
  }
}

function updateUI(){
  calcDefl();
  var sc=SC[curSc];
  var dBdz=parseFloat(document.getElementById('gS').value);
  var maxF=sc.spin*gjF*muB*dBdz;
  var maxDz=deflections.length?Math.abs(deflections[deflections.length-1].dz_mm):0;
  var rates=["\u03a7\u03b1\u03bc\u03b7\u03bb\u03cc\u03c2","\u039c\u03ad\u03c3\u03b1\u03b9\u03bf\u03c2","\u03a5\u03c8\u03b7\u03bb\u03cc\u03c2"];

  document.getElementById('gV').textContent=parseFloat(document.getElementById('gS').value).toFixed(1)+' T/m';
  document.getElementById('lV').textContent=parseFloat(document.getElementById('lS').value).toFixed(2)+' m';
  document.getElementById('vV').textContent=parseFloat(document.getElementById('vS').value).toFixed(0)+' m/s';
  document.getElementById('rV').textContent=rates[parseInt(document.getElementById('rS').value)-1];
  var nMj=deflections.length;
  document.getElementById("nbV").textContent=nMj;
  document.getElementById("mdV").textContent=maxDz.toFixed(2)+" mm";
  document.getElementById("fmV").textContent=(maxF*1e24).toFixed(2)+" ×10⁻²⁴ N";
  document.getElementById("vF").textContent=(maxF*1e24).toFixed(3)+" ×10⁻²⁴ N";
  document.getElementById("vDz").textContent=maxDz.toFixed(3)+" mm";
  document.getElementById("vM").textContent=nMj+" \u03b4\u03ad\u03c3\u03bc\u03b5\u03c2 | mⱼ: "+deflections.map(function(d){return d.mj;}).join(", ");

  document.getElementById('ins1').innerHTML=sc.fact.replace(/<ih>/g,'<span class="ih">').replace(/<\/ih>/g,'</span>');
  document.getElementById('ins2').innerHTML=nMj+' '+"\u03b4\u03ad\u03c3\u03bc\u03b5\u03c2"+' | '+sc.name;
  document.getElementById('abtDiv').innerHTML=sc.abt.replace(/<ih>/g,'<span class="ih">').replace(/<\/ih>/g,'</span>');
  var bl=document.getElementById('bList'); bl.innerHTML='';
  for(var i=0;i<deflections.length;i++){
    var d=deflections[i];
    var dir=d.dz_mm>0.005?"\u2191 (\u03c0\u03c1\u03bf\u03c2 N)":d.dz_mm<-0.005?"\u2193 (\u03b1\u03c0\u03cc N)":"\u2192 (0)";

    var el=document.createElement('div'); el.className='bi';
    el.innerHTML='<span class="dot" style="background:'+d.color+'"></span><span class="mj">m\u2C7C='+d.mj+'</span><span class="dir">'+dir+'</span><span class="dz">'+(d.dz_mm>=0?'+':'')+d.dz_mm.toFixed(2)+' mm</span>';
    bl.appendChild(el);
  }
  buildMagnet(); drawPlate2D();
}

function buildScGrid(){
  var g=document.getElementById('scGrid'); g.innerHTML='';
  SC.forEach(function(sc,i){
    var b=document.createElement('button'); b.className='sb'+(i===curSc?' on':'');
    b.innerHTML='<span class="sy">'+sc.lbl+'</span><span class="su">'+sc.sub+'</span><span class="sb2">'+sc.bt+'</span>';
    b.onclick=function(){curSc=i;document.querySelectorAll('.sb').forEach(function(x){x.classList.remove('on');});b.classList.add('on');clearAll();updateUI();};
    g.appendChild(b);
  });
}

function setRot(deg){
  magRotDeg=deg;
  magG.rotation.x=deg*Math.PI/180;
  document.querySelectorAll('.rb').forEach(function(b){b.classList.remove('on');});
  document.getElementById('rb'+(deg===0?'0':'90')).classList.add('on');
  document.getElementById("rotInfo").textContent=deg===0?"\u0393\u03c1\u03b1\u03bc\u03bc\u03ad\u03c2 \u03bf\u03c1\u03b9\u03b6\u03cc\u03bd\u03c4\u03b9\u03b5\u03c2":"\u0393\u03c1\u03b1\u03bc\u03bc\u03ad\u03c2 \u03ba\u03b1\u03c4\u03b1\u03ba\u03cc\u03c1\u03c5\u03c6\u03b5\u03c2";

  clearAll(); drawPlate2D();
}

function spawnParticle(){
  if(!deflections.length) return;
  // Spawn multiple atoms at once — radial spread in all directions
  var nSpawn = 4 + Math.floor(Math.random()*3); // 4-6 per call
  for(var s=0;s<nSpawn;s++){
    var k=Math.floor(Math.random()*deflections.length);
    var d=deflections[k];
    var maxDz=0;
    for(var i=0;i<deflections.length;i++) if(Math.abs(deflections[i].dz_mm)>maxDz) maxDz=Math.abs(deflections[i].dz_mm);
    if(!maxDz) maxDz=0.001;
    var scale=0.75/maxDz;
    var dzU=d.dz_mm*scale;
    var rotX=magRotDeg*Math.PI/180;
    var dY=dzU*Math.cos(rotX), dZ=dzU*Math.sin(rotX);
    // Full radial spread: angle from -PI to +PI (all directions in YZ plane)
    var ang=(Math.random()-0.5)*Math.PI*2.0;
    // Spread rate determines how fast atom moves away from beam axis
    // Most atoms spread far and hit slit 1; few pass through
    var sRate=0.025+Math.random()*0.055;
    var ribHalf=SLIT_GAP/2*0.9;
    var tf=(Math.random()-0.5)*2;
    var pY=tf*ribHalf*(-Math.sin(rotX));
    var pZ=tf*ribHalf*Math.cos(rotX);
    var geo=new THREE.SphereGeometry(0.035,5,5);
    var mat=new THREE.MeshBasicMaterial({color:new THREE.Color(d.color),transparent:true,opacity:0.85});
    var mesh=new THREE.Mesh(geo,mat);
    mesh.position.set(-4.5,0,0);
    partG.add(mesh);
    particles.push({mesh:mesh,dY:dY,dZ:dZ,pY:pY,pZ:pZ,tf:tf,col:d.color,dz:d.dz_mm,
      phase:'spread',x:-4.5,vx:0.055+Math.random()*0.015,
      ang:ang,sRate:sRate,hitSlit:0,alpha:1});
  }
}

function flashHit(x,y,z,col){
  // Bright impact flash on slit wall
  var geo=new THREE.CircleGeometry(0.07,8);
  var mat=new THREE.MeshBasicMaterial({color:0xffffff,transparent:true,opacity:1.0,depthWrite:false,side:THREE.DoubleSide});
  var m=new THREE.Mesh(geo,mat);
  m.position.set(x+0.031,y,z); m.rotation.y=Math.PI/2;
  partG.add(m);
  // Colored glow behind
  var ggeo=new THREE.CircleGeometry(0.12,8);
  var gmat=new THREE.MeshBasicMaterial({color:new THREE.Color(col),transparent:true,opacity:0.7,depthWrite:false,side:THREE.DoubleSide});
  var gm=new THREE.Mesh(ggeo,gmat);
  gm.position.set(x+0.025,y,z); gm.rotation.y=Math.PI/2;
  partG.add(gm);
  flashes.push({mesh:m,glow:gm,alpha:1.0});
}

function updateParticles(){
  var plateX=3.52;
  particles=particles.filter(function(p){
    if(p.alpha<=0.03){partG.remove(p.mesh);if(p.mesh.geometry)p.mesh.geometry.dispose();if(p.mesh.material)p.mesh.material.dispose();return false;}
    return true;
  });
  for(var i=0;i<particles.length;i++){
    var p=particles[i];
    p.x+=p.vx; p.mesh.position.x=p.x;
    if(p.phase==='spread'){
      var trav=p.x-(-4.5);
      var r=trav*p.sRate;
      p.mesh.position.y=Math.sin(p.ang)*r;
      p.mesh.position.z=Math.cos(p.ang)*r*0.35;
      // Check SLIT 1
      if(p.hitSlit===0 && p.x>=SLIT_X1){
        var yp=p.mesh.position.y;
        if(Math.abs(yp)>SLIT_GAP/2){flashHit(SLIT_X1,yp,p.mesh.position.z,p.col);p.phase='abs';}
        else{p.hitSlit=1;}
      }
      // Check SLIT 2
      if(p.phase==='spread' && p.hitSlit===1 && p.x>=SLIT_X2){
        var yp=p.mesh.position.y;
        if(Math.abs(yp)>SLIT_GAP/2){flashHit(SLIT_X2,yp,p.mesh.position.z,p.col);p.phase='abs';}
        else{p.phase='col';p.mesh.position.y=p.pY;p.mesh.position.z=p.pZ;}
      }
    } else if(p.phase==='abs'){
      p.alpha-=0.10; p.mesh.material.opacity=p.alpha;
    } else if(p.phase==='col'){
      p.mesh.position.y=p.pY; p.mesh.position.z=p.pZ;
      if(p.x>=-0.85) p.phase='mag';
    } else if(p.phase==='mag'){
      var pr=Math.min(1,(p.x+0.85)/(0.65+0.85));
      p.mesh.position.y=p.dY*(pr*pr)*0.5+p.pY;
      p.mesh.position.z=p.dZ*(pr*pr)*0.5+p.pZ;
      if(p.x>=0.65) p.phase='post';
    } else if(p.phase==='post'){
      var pr=Math.min(1,(p.x-0.65)/(plateX-0.65));
      var eY=p.dY*0.5+p.pY, eZ=p.dZ*0.5+p.pZ;
      p.mesh.position.y=eY+(p.dY+p.pY-eY)*pr;
      p.mesh.position.z=eZ+(p.dZ+p.pZ-eZ)*pr;
      if(p.x>=plateX){
        p.vx=0; p.x=plateX; p.mesh.position.x=plateX;
        var fy=p.mesh.position.y, fz=p.mesh.position.z;
        plateMarks.push({dz:p.dz,c:p.col,rib:p.tf||0,y:fy,z:fz});
        if(plateMarks.length>800) plateMarks.shift();
        addMark3D(fy,fz,p.col); drawPlate2D(); p.phase='fade';
      }
    } else {
      p.alpha-=0.06; p.mesh.material.opacity=p.alpha;
    }
  }
  flashes=flashes.filter(function(f){
    f.alpha-=0.06;
    if(f.alpha<=0.02){
      partG.remove(f.mesh);if(f.mesh.geometry)f.mesh.geometry.dispose();if(f.mesh.material)f.mesh.material.dispose();
      if(f.glow){partG.remove(f.glow);if(f.glow.geometry)f.glow.geometry.dispose();if(f.glow.material)f.glow.material.dispose();}
      return false;
    }
    f.mesh.material.opacity=f.alpha;
    if(f.glow) f.glow.material.opacity=f.alpha*0.7;
    return true;
  });
}

function addMark3D(y,z,col){
  var geo=new THREE.CircleGeometry(0.045,10);
  var mat=new THREE.MeshBasicMaterial({color:new THREE.Color(col),transparent:true,opacity:0.85,depthWrite:false,side:THREE.DoubleSide});
  var m=new THREE.Mesh(geo,mat); m.position.set(3.56,y,z); m.rotation.y=Math.PI/2; markG.add(m);
  var gg=new THREE.CircleGeometry(0.09,10);
  var gm=new THREE.MeshBasicMaterial({color:new THREE.Color(col),transparent:true,opacity:0.18,depthWrite:false,side:THREE.DoubleSide});
  var gd=new THREE.Mesh(gg,gm); gd.position.set(3.54,y,z); gd.rotation.y=Math.PI/2; markG.add(gd);
}

function clearAll(){
  for(var i=0;i<particles.length;i++){partG.remove(particles[i].mesh);}
  particles=[];
  for(var i=0;i<flashes.length;i++){partG.remove(flashes[i].mesh);}
  flashes=[];
  plateMarks=[];
  while(markG.children.length>0){var c=markG.children[0];if(c.geometry)c.geometry.dispose();if(c.material)c.material.dispose();markG.remove(c);}
  drawPlate2D();
}

function resize(){
  var p=cv.parentElement;
  var w=p.clientWidth||800, h=p.clientHeight;
  if(!h||h<50) h=window.innerHeight-90;
  renderer.setSize(w,h,false);
  camera.aspect=w/h; camera.updateProjectionMatrix();
}

function dlWS(t){
  var b64=['PCFET0NUWVBFIGh0bWw+PGh0bWwgbGFuZz0iZWwiPjxoZWFkPjxtZXRhIGNoYXJzZXQ9IlVURi04Ij4KPHRpdGxlPs6Rzr3Ov865z4fPhM6uIM6UzrnOtc+BzrXPjc69zrfPg863IFN0ZXJuLUdlcmxhY2g8L3RpdGxlPgo8c3R5bGU+Ym9keXtmb250LWZhbWlseTpBcmlhbCxzYW5zLXNlcmlmO21hcmdpbjozMHB4O2NvbG9yOiMyMjI7bGluZS1oZWlnaHQ6MS43O30KaDF7Y29sb3I6IzFhNTI3Njtib3JkZXItYm90dG9tOjJweCBzb2xpZCAjMWE1Mjc2O3BhZGRpbmctYm90dG9tOjZweDt9Cmgye2NvbG9yOiMxZjYxOGQ7bWFyZ2luLXRvcDoyMHB4O30gLmxpbmV7Ym9yZGVyLWJvdHRvbToxcHggc29saWQgI2NjYztoZWlnaHQ6MjZweDttYXJnaW46NHB4IDA7fQp0YWJsZXt3aWR0aDoxMDAlO2JvcmRlci1jb2xsYXBzZTpjb2xsYXBzZTttYXJnaW46MTBweCAwO30KdGh7YmFja2dyb3VuZDojMWE1Mjc2O2NvbG9yOiNmZmY7cGFkZGluZzo3cHg7fSB0ZHtib3JkZXI6MXB4IHNvbGlkICNiYmI7cGFkZGluZzo2cHg7fSB0ZC5le2hlaWdodDoyOHB4O30KLmJveHtib3JkZXI6MXB4IHNvbGlkICNhYWE7Ym9yZGVyLXJhZGl1czo1cHg7cGFkZGluZzoxMnB4O2JhY2tncm91bmQ6I2Y5ZjlmOTttYXJnaW46OHB4IDA7fQouY2N7Zm9udC1zaXplOjEwcHg7Y29sb3I6Izg4ODttYXJnaW4tdG9wOjI4cHg7Ym9yZGVyLXRvcDoxcHggc29saWQgI2RkZDtwYWRkaW5nLXRvcDo4cHg7fTwvc3R5bGU+CjwvaGVhZD48Ym9keT4KPGgxPiYjeDI2REI7IM6Rzr3Ov865z4fPhM6uIM6UzrnOtc+BzrXPjc69zrfPg863OiDOms6yzqzOvc+Ez4nPg863IM+Dz4DOuc69IM63zrvOtc66z4TPgc6/zr3Or86/z4U8L2gxPgo8cD48ZW0+zqfPgc6uz4POtyDPiM63z4bOuc6xzrrOrs+CIM+Az4HOv8+Dzr/OvM6/zq/Pic+DzrfPgiDOoM61zrnPgc6szrzOsc+Ezr/PgiBTdGVybuKAk0dlcmxhY2ggfCDOps+Fz4POuc66zq4gzpPOhCDOm8+FzrrOtc6vzr/PhTwvZW0+PC9wPgo8ZGl2IGNsYXNzPSJib3giPjxzdHJvbmc+8J+TjCDOo866zr/PgM+Mz4I6PC9zdHJvbmc+IM6UzrnOtc+BzrXPjc69zrfPg861IM61zrvOtc+NzrjOtc+BzrEgz4DPjs+CIM6tzr3OsSDOsc69zr/OvM6/zrnOv86zzrXOvc6tz4IgzrzOsc6zzr3Ot8+EzrnOus+MIM+AzrXOtM6vzr8gzrXPgM63z4HOtc6szrbOtc65IM68zrnOsSDOtM6tz4POvM63IM6xz4TPjM68z4nOvS4gzpHPgM6/z4bOrM+DzrnPg861IM61z4PPjSDPhM65IM64zrEgzrzOtc67zrXPhM6uz4POtc65z4IgzrrOsc65IM+Az47Pgi48L2Rpdj4KPGgyPvCflI0gzpXPgc+Oz4TOt8+DzrcgzpTOuc61z4HOtc+Nzr3Ot8+DzrfPgjwvaDI+CjxkaXYgY2xhc3M9ImxpbmUiPjwvZGl2PjxkaXYgY2xhc3M9ImxpbmUiPjwvZGl2PjxkaXYgY2xhc3M9ImxpbmUiPjwvZGl2Pgo8aDI+4pqZ77iPIM6jz4fOtc60zrnOsc+DzrzPjM+CPC9oMj4KPHA+zpzOtc+EzrHOss67zrfPhM6tz4Igz4DOsc+BzqzOvM61z4TPgc6/zrk6PC9wPjxkaXYgY2xhc3M9ImxpbmUiPjwvZGl2PjxkaXYgY2xhc3M9ImxpbmUiPjwvZGl2Pgo8cD7Oo8+EzrHOuM61z4HOrc+CIM+AzrHPgc6szrzOtc+Ez4HOv865OjwvcD48ZGl2IGNsYXNzPSJsaW5lIj48L2Rpdj48ZGl2IGNsYXNzPSJsaW5lIj48L2Rpdj4KPHA+zqTOuSDOvM61z4TPgc6sz4I6PC9wPjxkaXYgY2xhc3M9ImxpbmUiPjwvZGl2PjxkaXYgY2xhc3M9ImxpbmUiPjwvZGl2Pgo8aDI+8J+TiiDOms6xz4TOsc6zz4HOsc+Gzq4gzpTOtc60zr/OvM6tzr3Pic69PC9oMj4KPHRhYmxlPjx0cj48dGg+Jm5ic3A7PC90aD48dGg+Jm5ic3A7PC90aD48dGg+Jm5ic3A7PC90aD48dGg+Jm5ic3A7PC90aD48dGg+Jm5ic3A7PC90aD48L3RyPgo8dHI+PHRkIGNsYXNzPSJlIj48L3RkPjx0ZCBjbGFzcz0iZSI+PC90ZD48dGQgY2xhc3M9ImUiPjwvdGQ+PHRkIGNsYXNzPSJlIj48L3RkPjx0ZCBjbGFzcz0iZSI+PC90ZD48L3RyPgo8dHI+PHRkIGNsYXNzPSJlIj48L3RkPjx0ZCBjbGFzcz0iZSI+PC90ZD48dGQgY2xhc3M9ImUiPjwvdGQ+PHRkIGNsYXNzPSJlIj48L3RkPjx0ZCBjbGFzcz0iZSI+PC90ZD48L3RyPgo8dHI+PHRkIGNsYXNzPSJlIj48L3RkPjx0ZCBjbGFzcz0iZSI+PC90ZD48dGQgY2xhc3M9ImUiPjwvdGQ+PHRkIGNsYXNzPSJlIj48L3RkPjx0ZCBjbGFzcz0iZSI+PC90ZD48L3RyPgo8dHI+PHRkIGNsYXNzPSJlIj48L3RkPjx0ZCBjbGFzcz0iZSI+PC90ZD48dGQgY2xhc3M9ImUiPjwvdGQ+PHRkIGNsYXNzPSJlIj48L3RkPjx0ZCBjbGFzcz0iZSI+PC90ZD48L3RyPgo8L3RhYmxlPgo8aDI+8J+SoSDOo8+FzrzPgM61z4HOrM+DzrzOsc+EzrE8L2gyPgo8ZGl2IGNsYXNzPSJsaW5lIj48L2Rpdj48ZGl2IGNsYXNzPSJsaW5lIj48L2Rpdj48ZGl2IGNsYXNzPSJsaW5lIj48L2Rpdj48ZGl2IGNsYXNzPSJsaW5lIj48L2Rpdj4KPGgyPuKdkyDOnc6tzrEgzpXPgc+Jz4TOrs68zrHPhM6xPC9oMj4KPGRpdiBjbGFzcz0ibGluZSI+PC9kaXY+PGRpdiBjbGFzcz0ibGluZSI+PC9kaXY+PGRpdiBjbGFzcz0ibGluZSI+PC9kaXY+CjxkaXYgY2xhc3M9ImNjIj7OoM61zq/Pgc6xzrzOsSBTdGVybuKAk0dlcmxhY2ggfCDOps+Fz4POuc66zq4gzpPOhCDOm8+FzrrOtc6vzr/PhTxicj4KzpTOt868zrnOv8+Fz4HOs86vzrEg4oCTIM6Rzr3OrM+Az4TPhc6+zrc6IM6gzrHOvc6xzrPOuc+Oz4TOt8+CIM6gzrXPhM+Bzq/OtM63z4IgfCBDQyBCWS1OQy1TQSA0LjAgfCBzY2goYXQpc2NoLmdyPC9kaXY+CjwvYm9keT48L2h0bWw+','PCFET0NUWVBFIGh0bWw+CjxodG1sIGxhbmc9ImVsIj4KPGhlYWQ+CjxtZXRhIGNoYXJzZXQ9IlVURi04Ij4KPHRpdGxlPs6azrHOuM6/zrTOt86zzr/Pjc68zrXOvc63IM6UzrnOtc+BzrXPjc69zrfPg863IOKAlCBTdGVybuKAk0dlcmxhY2g8L3RpdGxlPgo8c2NyaXB0PgpNYXRoSmF4PXt0ZXg6e2lubGluZU1hdGg6W1snXFwoJywnXFwpJ11dLGRpc3BsYXlNYXRoOltbJ1xcWycsJ1xcXSddXX0sc3ZnOntmb250Q2FjaGU6J2dsb2JhbCd9fTsKPC9zY3JpcHQ+CjxzY3JpcHQgc3JjPSJodHRwczovL2Nkbi5qc2RlbGl2ci5uZXQvbnBtL21hdGhqYXhAMy9lczUvdGV4LXN2Zy5qcyI+PC9zY3JpcHQ+CjxzdHlsZT4KQGltcG9ydCB1cmwoJ2h0dHBzOi8vZm9udHMuZ29vZ2xlYXBpcy5jb20vY3NzMj9mYW1pbHk9Tm90bytTYW5zK0dyZWVrOndnaHRAMzAwOzQwMDs2MDAmZGlzcGxheT1zd2FwJyk7CmJvZHl7Zm9udC1mYW1pbHk6J05vdG8gU2FucyBHcmVlaycsQXJpYWwsc2Fucy1zZXJpZjttYXJnaW46MzBweCA0MHB4O2NvbG9yOiMyMjI7bGluZS1oZWlnaHQ6MS42NTtmb250LXNpemU6MTRweDt9Cmgxe2NvbG9yOiMxYTUyNzY7Ym9yZGVyLWJvdHRvbToycHggc29saWQgIzFhNTI3NjtwYWRkaW5nLWJvdHRvbTo2cHg7Zm9udC1zaXplOjIwcHg7fQpoMntjb2xvcjojMWY2MThkO2ZvbnQtc2l6ZToxNXB4O21hcmdpbi10b3A6MjJweDttYXJnaW4tYm90dG9tOjZweDt9Ci5ib3h7Ym9yZGVyOjFweCBzb2xpZCAjYWFhO2JvcmRlci1yYWRpdXM6NnB4O3BhZGRpbmc6MTJweCAxNnB4O21hcmdpbjoxMHB4IDA7YmFja2dyb3VuZDojZjlmOWY5O30KLmxpbmVze21hcmdpbjo4cHggMDt9IC5saW5le2JvcmRlci1ib3R0b206MXB4IHNvbGlkICNjY2M7aGVpZ2h0OjI4cHg7bWFyZ2luOjZweCAwO30KdGFibGV7d2lkdGg6MTAwJTtib3JkZXItY29sbGFwc2U6Y29sbGFwc2U7bWFyZ2luOjEwcHggMDt9CnRoe2JhY2tncm91bmQ6IzFhNTI3Njtjb2xvcjojZmZmO3BhZGRpbmc6OHB4O2ZvbnQtc2l6ZToxM3B4O3RleHQtYWxpZ246Y2VudGVyO30KdGR7Ym9yZGVyOjFweCBzb2xpZCAjYmJiO3BhZGRpbmc6N3B4IDhweDtmb250LXNpemU6MTNweDt0ZXh0LWFsaWduOmNlbnRlcjt9IHRkLmV7aGVpZ2h0OjMwcHg7fQoubm90ZXtmb250LXNpemU6MTFweDtjb2xvcjojNjY2O2ZvbnQtc3R5bGU6aXRhbGljO30KLmZie2JhY2tncm91bmQ6I2VhZjRmYjtib3JkZXItbGVmdDo0cHggc29saWQgIzFhNTI3NjtwYWRkaW5nOjhweCAxNHB4O21hcmdpbjo4cHggMDtib3JkZXItcmFkaXVzOjAgNHB4IDRweCAwO30KLmhse2JhY2tncm91bmQ6I2ZmZjNjZDtwYWRkaW5nOjJweCA2cHg7Ym9yZGVyLXJhZGl1czozcHg7fQouc3RlcHtiYWNrZ3JvdW5kOiNmMGY4ZmY7Ym9yZGVyOjFweCBzb2xpZCAjOTBiOGUwO2JvcmRlci1yYWRpdXM6NXB4O3BhZGRpbmc6OHB4IDEycHg7bWFyZ2luOjVweCAwO2ZvbnQtc2l6ZToxM3B4O30KLndhcm57YmFja2dyb3VuZDojZmZmOGUxO2JvcmRlcjoxcHggc29saWQgI2YwYzA0MDtib3JkZXItcmFkaXVzOjVweDtwYWRkaW5nOjhweCAxMnB4O21hcmdpbjo4cHggMDtmb250LXNpemU6MTNweDt9Ci5jY3tmb250LXNpemU6MTBweDtjb2xvcjojODg4O21hcmdpbi10b3A6MzBweDtib3JkZXItdG9wOjFweCBzb2xpZCAjZGRkO3BhZGRpbmctdG9wOjhweDt0ZXh0LWFsaWduOmNlbnRlcjt9Cm1qeC1jb250YWluZXJ7Zm9udC1zaXplOjFlbSFpbXBvcnRhbnQ7fQpAbWVkaWEgcHJpbnR7Lm5vLXByaW50e2Rpc3BsYXk6bm9uZTt9fQo8L3N0eWxlPgo8L2hlYWQ+Cjxib2R5Pgo8aDE+JiN4MjZkYjsgzprOsc64zr/OtM63zrPOv8+NzrzOtc69zrcgzpTOuc61z4HOtc+Nzr3Ot8+Dzrc6IM6azrLOrM69z4TPic+Dzrcgz4PPgM65zr0gzrfOu861zrrPhM+Bzr/Ovc6vzr/PhTwvaDE+CjxwIGNsYXNzPSJub3RlIj7Op8+Bzq7Pg863IM+IzrfPhs65zrHOus6uz4Igz4DPgc6/z4POv868zr/Or8+Jz4POt8+CIM6gzrXOuc+BzqzOvM6xz4TOv8+CIFN0ZXJuJm5kYXNoO0dlcmxhY2ggJm5ic3A7fCZuYnNwOyDOps+Fz4POuc66zq4gzpMmcHJpbWU7IM6bz4XOus61zq/Ov8+FPC9wPgoKPGgyPiYjeDFGM0FGOyDOo866zr/PgM+Mz4I8L2gyPgo8ZGl2IGNsYXNzPSJib3giPs6dzrEgzrTOuc61z4HOtc+Fzr3Ors+DzrXOuc+CIM+AzrXOuc+BzrHOvM6xz4TOuc66zqwgz4TOt869IDxzdHJvbmc+zrrOss6szr3PhM+Jz4POtyDPhM63z4Igz4PPhM+Bzr/Phs6/z4HOvM6uz4I8L3N0cm9uZz4gz4TOv8+FIM63zrvOtc66z4TPgc6/zr3Or86/z4UKzrzOrc+DzrEgzrHPgM+MIM+Ezr8gzrnPg8+Ezr/Pgc65zrrPjCDPgM61zq/Pgc6xzrzOsSBTdGVybiZuZGFzaDtHZXJsYWNoICgxOTIyKSwgzr3OsSDOtc+AzrHOu863zrjOtc+Nz4POtc65z4Igz4TOtyDPg8+Hzq3Pg863ClwoXHRleHR7zrHPgc65zrjOvM+Mz4IgzrTOtc+DzrzPjs69fSA9IDJzKzFcKSDOus6xzrkgzr3OsSDOus6xz4TOsc69zr/Ors+DzrXOuc+CIM6zzrnOsc+Ezq8gz4fPgc63z4POuc68zr/PgM6/zrnOrs64zrfOus6xzr0KPGVtPs6/z4XOtM6tz4TOtc+BzrEgzqzPhM6/zrzOsTwvZW0+IM6xzr3PhM6vIM6zzrnOsSDOtc67zrXPjc64zrXPgc6xIM63zrvOtc66z4TPgc+Mzr3Ouc6xLjwvZGl2PgoKPGgyPiYjeDFGNERBOyDOmM61z4nPgc63z4TOuc66z4wgzqXPgM+MzrLOsc64z4HOvzwvaDI+CjxkaXYgY2xhc3M9ImZiIj4KPHN0cm9uZz7Oo8+EzrHOuM61z4HOrc+COjwvc3Ryb25nPiAmbmJzcDsKXChcbXVfQiA9IDl7LH0yNzRcdGltZXMxMF57LTI0fVwpIEovVCAmbmJzcDsgKM68zrHOs869zrfPhM+Mzr3Ouc6/IEJvaHIpICZuYnNwO3wmbmJzcDsKXChnX2ogXGFwcHJveCAyXCkgJm5ic3A7ICjPgM6xz4HOrM6zzr/Ovc+EzrHPgiBMYW5kw6kgzrPOuc6xIHNwaW4pICZuYnNwO3wmbmJzcDsKXChtX3tBZ30gPSAxeyx9NzkxXHRpbWVzMTBeey0yNX1cKSBrZwo8L2Rpdj4KPGRpdiBjbGFzcz0iZmIiPgo8c3Ryb25nPs6azrLOsc69z4TOuc66z4zPgiDOsc+BzrnOuM68z4zPgiBcKG1falwpOjwvc3Ryb25nPjxicj4KzpPOuc6xIHNwaW4gXChzXCk6ICZuYnNwOyBcKG1faiA9IC1zLFw7IC1zKzEsXDsgXGxkb3RzLFw7ICtzXCkgJm5ic3A7Jm5ic3A7CijPg8+Nzr3Ov867zr8gXCgycysxXCkgz4TOuc68zq3Pgik8YnI+PGJyPgo8c3Ryb25nPs6Uz43Ovc6xzrzOtyDPg861IM6xzr3Ov868zr/Ouc6/zrPOtc69zq3PgiDOvM6xzrPOvc63z4TOuc66z4wgz4DOtc60zq/Ovzo8L3N0cm9uZz48YnI+ClxbRl96ID0gbV9qIFxjZG90IGdfaiBcY2RvdCBcbXVfQiBcY2RvdCBcZnJhY3tccGFydGlhbCBCfXtccGFydGlhbCB6fVxdCjxzdHJvbmc+zpXOus+Ez4HOv8+Azq4gzrTOrc+DzrzOt8+COjwvc3Ryb25nPjxicj4KXFtcRGVsdGEgeiA9IFxmcmFje0Zfen17bX1cY2RvdFxsZWZ0KFxmcmFje0x9e3Z9XHJpZ2h0KV4yXGNkb3RcbGVmdChcZnJhY3sxfXsyfStcZnJhY3tEfXtMfVxyaWdodClcXQrPjM+Azr/PhSBcKExcKSA9IM68zq7Ous6/z4IgzrzOsc6zzr3Ors+EzrcsIFwodlwpID0gz4TOsc+Hz43PhM63z4TOsSDOsc+Ez4zOvM+Jzr0sIFwoRFwpID0gzrHPgM+Mz4PPhM6xz4POtyDOvM6xzrPOvc6uz4TOt+KAk8+AzrvOrM66zrHPgiBcKChcYXBwcm94IEwpXCkKPC9kaXY+CjxkaXYgY2xhc3M9ImJveCI+CjxzdHJvbmc+zqDPjs+CIM+Hz4HOt8+DzrnOvM6/z4DOv865zrXOr8+CIM+EzrfOvSDPgM+Bzr/Pg86/zrzOv86vz4nPg863Ojwvc3Ryb25nPjxicj4KJmJ1bGw7IM6fIM60z4HOv868zq3Osc+CIDxzdHJvbmc+4oiCQi/iiIJ6PC9zdHJvbmc+IM6xzrvOu86szrbOtc65IM+EzrfOvSDOus67zq/Pg863IM+Ezr/PhSDOvM6xzrPOvc63z4TOuc66zr/PjSDPgM61zrTOr86/z4Ug4oCUIM+AzrHPgc6xz4TOrs+BzrfPg861IM+Ezr/OvSDOsc+BzrnOuM68z4wgzrPPgc6xzrzOvM+Ozr0gz4DOtc60zq/Ov8+FLjxicj4KJmJ1bGw7IM6fIM60z4HOv868zq3Osc+CIDxzdHJvbmc+TDwvc3Ryb25nPiDOsc67zrvOrM62zrXOuSDPhM6/IM68zq7Ous6/z4Igz4TOv8+FIM68zrHOs869zq7PhM63IOKAlCDPgM6xz4HOsc+Ezq7Pgc63z4POtSDPgM+Oz4IgzrHOu867zqzOts61zrkgz4TOvyDPg8+Hzq7OvM6xIM+Ezr/PhSDOvM6xzrPOvc6uz4TOty48YnI+CiZidWxsOyDOpM6xIM66zr/Phc68z4DOuc6sIDxzdHJvbmc+zqPOtc69zrHPgc6vzr/PhTwvc3Ryb25nPiDOtc+AzrnOu86tzrPOv8+Fzr0gzrTOuc6xz4bOv8+BzrXPhM65zrrOrCDOrM+Ezr/OvM6xIC8gc3Bpbi48YnI+CiZidWxsOyDOlyDOus6xz4HPhM6tzrvOsSA8c3Ryb25nPs6Uzq/PgM6/zrvOvyDPg861IM6czrHOs869LiDOoM61zrTOr86/PC9zdHJvbmc+IM60zrXOr8+Hzr3Otc65IM6zzrnOsc+Ezq8gz4fPgc61zrnOrM62zrXPhM6xzrkgzrHOvc6/zrzOv865zr/Os861zr3Orc+CIM+AzrXOtM6vzr8uCjwvZGl2PgoKPGgyPiYjeDFGNTJDOyDOnM6tz4HOv8+CIM6RICZuZGFzaDsgzp/OvM6/zrPOtc69zq3PgiB2cyDOkc69zr/OvM6/zrnOv86zzrXOvc6tz4IgzqDOtc60zq/OvzwvaDI+CjxwPs6Gzr3Ov865zr7OtSDPhM63zr0gzrrOsc+Bz4TOrc67zrEgPHNwYW4gY2xhc3M9ImhsIj7OlM6vz4DOv867zr8gz4POtSDOnM6xzrPOvS4gzqDOtc60zq/Ovzwvc3Bhbj4gzrrOsc65IM66zr/Phc69zqwgzrHPgc6zzqwgz4TOv869IM60z4HOv868zq3OsSDOsc+Az4wgzrHPgc65z4PPhM61z4HOrCAozr/OvM6/zrPOtc69zq3Pgikgz4DPgc6/z4Igz4TOsSDOtM61zr7Ouc6sICjOsc69zr/OvM6/zrnOv86zzrXOvc6tz4IpLjwvcD4KPHA+PHN0cm9uZz7OkTEuPC9zdHJvbmc+IM6jzrUgzr/OvM6/zrPOtc69zq3PgiDPgM61zrTOr86/LCDPhM65IM+AzrHPgc6xz4TOt8+BzrXOr8+CIM6zzrnOsSDPhM65z4IgzrTPhc69zqzOvM61zrnPgiBGJiN4MjA4QTsgzrrOsc65IEYmI3gyMDhCOyDPg8+Ezr/Phc+CIM60z43OvyDPgM+MzrvOv8+Fz4Igz4TOv8+FIM68zrHOs869zrfPhM65zrrOv8+NIM60zrnPgM+MzrvOv8+FOzwvcD4KPGRpdiBjbGFzcz0ibGluZXMiPjxkaXYgY2xhc3M9ImxpbmUiPjwvZGl2PjxkaXYgY2xhc3M9ImxpbmUiPjwvZGl2PjwvZGl2Pgo8cD48c3Ryb25nPs6RMi48L3N0cm9uZz4gzqDOv865zrEgzrXOr869zrHOuSDOtyDPg8+Fzr3Ouc+Dz4TOsc68zq3Ovc63IM60z43Ovc6xzrzOtyDOo0Ygz4POtSDOv868zr/Os861zr3Orc+CIM+AzrXOtM6vzr87IM6kzrkgzrrOr869zrfPg863IM66zqzOvc61zrkgz4TOvyDOtM6vz4DOv867zr87PC9wPgo8ZGl2IGNsYXNzPSJsaW5lcyI+PGRpdiBjbGFzcz0ibGluZSI+PC9kaXY+PGRpdiBjbGFzcz0ibGluZSI+PC9kaXY+PC9kaXY+CjxwPjxzdHJvbmc+zpEzLjwvc3Ryb25nPiDOnM+MzrvOuc+CIM6/IM60z4HOv868zq3Osc+CIM+AzqzOtc65IM+Dz4TOvyDOsc69zr/OvM6/zrnOv86zzrXOvc6tz4IgzqzOus+Bzr8sIM+EzrkgzrHOu867zqzOts61zrk7IM6TzrnOsc+Ezq8gz4TPjs+BzrEgzqNGIOKJoCAwOzwvcD4KPGRpdiBjbGFzcz0ibGluZXMiPjxkaXYgY2xhc3M9ImxpbmUiPjwvZGl2PjxkaXYgY2xhc3M9ImxpbmUiPjwvZGl2PjwvZGl2Pgo8cD48c3Ryb25nPs6RNC48L3N0cm9uZz4gzqDOsc+BzrHPhM6uz4HOt8+DzrUgzrrOsc65IM+Ezr/OvSDPgc61z4XOvM6xz4TOv8+Gz4zPgc6/IM6yz4HPjM+Hzr8gKM60zrXOvs65z4wgz4TOvM6uzrzOsSkuIM6TzrnOsc+Ezq8gz4TOvyDOvM6/zr3PhM6tzrvOvyDPhM6/z4UgzrLPgc+Mz4fOv8+FIM+BzrXPjc68zrHPhM6/z4Igz4DOtc+BzrnOs8+BzqzPhs61zrkgzrrOsc67z43PhM61z4HOsSDPhM6/IM63zrvOtc66z4TPgc+Mzr3Ouc6/IM6xz4DPjCDOrc69zrEgzrHPgM67z4wgz4HOrM6yzrTOvyDOvM6xzrPOvc6uz4TOtzs8L3A+CjxkaXYgY2xhc3M9ImxpbmVzIj48ZGl2IGNsYXNzPSJsaW5lIj48L2Rpdj48ZGl2IGNsYXNzPSJsaW5lIj48L2Rpdj48L2Rpdj4KCjxoMj4mI3gxRjUyQzsgzpzOrc+Bzr/PgiDOkiAmbmRhc2g7IM6azrLOrM69z4TPic+Dzrc6IM6Rz4HOuc64zrzPjM+CIM6UzrXPg868z47OvSB2cyBTcGluPC9oMj4KPHA+zpXPgM6tzrvOtc6+zrUgPHNwYW4gY2xhc3M9ImhsIj5BZzwvc3Bhbj4sIFwoXHBhcnRpYWwgQi9ccGFydGlhbCB6ID0gNVwpIFQvbSwgXChMID0gMHssfTEwXCkgbSwgXCh2ID0gNTAwXCkgbS9zLiDOoM6sz4TOsSA8c3Ryb25nPs6Vzp3Okc6hzp7Olzwvc3Ryb25nPi48L3A+CjxwPjxzdHJvbmc+zpIxLjwvc3Ryb25nPiDOoM+Mz4POtc+CIM66zrfOu86vzrTOtc+CIM61zrzPhs6xzr3Or862zr/Ovc+EzrHOuSDPg8+Ezrcgz4bPic+Ezr/Os8+BzrHPhs65zrrOriDPgM67zqzOus6xOyDOoM6/zrnOtc+CIM+EzrnOvM6tz4IgXChtX2pcKSDOsc69z4TOuc+Dz4TOv865z4fOv8+Nzr0gz4POtSDOus6xzrjOtc68zq/OsTs8L3A+CjxkaXYgY2xhc3M9ImxpbmVzIj48ZGl2IGNsYXNzPSJsaW5lIj48L2Rpdj48ZGl2IGNsYXNzPSJsaW5lIj48L2Rpdj48L2Rpdj4KPHA+PHN0cm9uZz7OkjIuPC9zdHJvbmc+IM6jz4XOvM+AzrvOrs+Bz4nPg861IM+Ezr/OvSDPgM6vzr3Osc66zrEgzrHOu867zqzOts6/zr3PhM6xz4Igz4POtc69zqzPgc65zr86PC9wPgo8dGFibGU+Cjx0cj48dGg+zqPOtc69zqzPgc65zr88L3RoPjx0aD5TcGluIFwoc1wpPC90aD48dGg+zqTOuc68zq3PgiBcKG1falwpPC90aD48dGg+zpHPgc65zrjOvM+Mz4IgzrTOtc+DzrzPjs69PC90aD48dGg+XCgycysxXCk8L3RoPjx0aD7Oo8+FzrzPhs+Jzr3Or86xOzwvdGg+PC90cj4KPHRyPjx0ZD5BZzwvdGQ+PHRkPjEvMjwvdGQ+PHRkIGNsYXNzPSJlIj48L3RkPjx0ZCBjbGFzcz0iZSI+PC90ZD48dGQgY2xhc3M9ImUiPjwvdGQ+PHRkIGNsYXNzPSJlIj48L3RkPjwvdHI+Cjx0cj48dGQ+wrJIPC90ZD48dGQ+MTwvdGQ+PHRkIGNsYXNzPSJlIj48L3RkPjx0ZCBjbGFzcz0iZSI+PC90ZD48dGQgY2xhc3M9ImUiPjwvdGQ+PHRkIGNsYXNzPSJlIj48L3RkPjwvdHI+Cjx0cj48dGQ+TmE8L3RkPjx0ZD4xLzI8L3RkPjx0ZCBjbGFzcz0iZSI+PC90ZD48dGQgY2xhc3M9ImUiPjwvdGQ+PHRkIGNsYXNzPSJlIj48L3RkPjx0ZCBjbGFzcz0iZSI+PC90ZD48L3RyPgo8dHI+PHRkPnM9My8yPC90ZD48dGQ+My8yPC90ZD48dGQgY2xhc3M9ImUiPjwvdGQ+PHRkIGNsYXNzPSJlIj48L3RkPjx0ZCBjbGFzcz0iZSI+PC90ZD48dGQgY2xhc3M9ImUiPjwvdGQ+PC90cj4KPC90YWJsZT4KPHA+PHN0cm9uZz7OkjMuPC9zdHJvbmc+IM6UzrnOsc+Ez43PgM+Jz4POtSDPhM6/zr0gzrPOtc69zrnOus+MIM66zrHOvc+Mzr3OsSDOvM61IM60zrnOus6sIM+Dzr/PhSDOu8+MzrPOuc6xOjwvcD4KPGRpdiBjbGFzcz0ibGluZXMiPjxkaXYgY2xhc3M9ImxpbmUiPjwvZGl2PjxkaXYgY2xhc3M9ImxpbmUiPjwvZGl2PjwvZGl2Pgo8cD48c3Ryb25nPs6SNC48L3N0cm9uZz4gzqPPhM6/IM+DzrXOvc6sz4HOuc6/IMKySCAoc3Bpbi0xKTogzrcgzrzOtc+DzrHOr86xIM60zq3Pg868zrcgKFwobV9qID0gMFwpKSDOtc66z4TPgc6tz4DOtc+EzrHOuSDOriDPjM+Hzrk7IM6TzrnOsc+Ezq8gzqzPgc6xzrPOtTs8L3A+CjxkaXYgY2xhc3M9ImxpbmVzIj48ZGl2IGNsYXNzPSJsaW5lIj48L2Rpdj48ZGl2IGNsYXNzPSJsaW5lIj48L2Rpdj48L2Rpdj4KCjxoMj4mI3gxRjlFRTsgzpzOrc+Bzr/PgiDOkyAmbmRhc2g7IM6lz4DOv867zr/Os865z4POvM+Mz4IgzpXOus+Ez4HOv8+Azq7PgjwvaDI+CjxwPs6TzrnOsSA8c3BhbiBjbGFzcz0iaGwiPkFnPC9zcGFuPiwgXChccGFydGlhbCBCL1xwYXJ0aWFsIHogPSA1XCkgVC9tLCBcKEwgPSAweyx9MTBcKSBtLCBcKHYgPSA1MDBcKSBtL3M6PC9wPgo8cD48c3Ryb25nPs6TMS48L3N0cm9uZz4gzp/Pgc65z4POvM6/zq86IFwobV9qXCkgPSDOus6yzrHOvc+EzrnOus+Mz4IgzrHPgc65zrjOvM+Mz4Igz4PPhM+Bzr/Phs6/z4HOvM6uz4IsIFwoZ19qIFxhcHByb3ggMlwpID0gz4DOsc+BzqzOs86/zr3PhM6xz4IgTGFuZMOpLApcKFxtdV9CID0gOXssfTI3NFx0aW1lczEwXnstMjR9XCkgSi9UID0gzrzOsc6zzr3Ot8+Ez4zOvc65zr8gQm9ociwgXChccGFydGlhbCBCL1xwYXJ0aWFsIHogPSA1XCkgVC9tID0gzrrOu86vz4POtyDPgM61zrTOr86/z4UuPGJyPgrOpc+Azr/Ou8+MzrPOuc+DzrUgz4TOtyDOtM+Nzr3Osc68zrcgzrPOuc6xIFwobV9qID0gK1x0ZnJhY3sxfXsyfVwpOjwvcD4KPGRpdiBjbGFzcz0iZmIiPlxbIEZfeiA9IG1faiBcY2RvdCBnX2ogXGNkb3QgXG11X0IgXGNkb3QgXGZyYWN7XHBhcnRpYWwgQn17XHBhcnRpYWwgen0KPSBcZnJhY3sxfXsyfSBcdGltZXMgMiBcdGltZXMgOXssfTI3NFx0aW1lczEwXnstMjR9IFx0aW1lcyA1Cj0gXHJ1bGV7M2NtfXswLjVwdH0gXHRleHR7IE59IFxdPC9kaXY+CjxwPjxzdHJvbmc+zpMyLjwvc3Ryb25nPiDOo8+NzrPOus+BzrnOvc61IM68zrUgz4TOtyDPhM65zrzOriDPhM63z4Igz4DPgc6/z4POv868zr/Or8+Jz4POt8+COiBcKEZfe3NpbX0gPSBcKSBfX19fX19fIMOXMTDigbvCsuKBtCBOPC9wPgo8cD48c3Ryb25nPs6TMy48L3N0cm9uZz4gzqXPgM6/zrvPjM6zzrnPg861IM64zrXPic+BzrfPhM65zrrOrCDPhM63zr0gzrXOus+Ez4HOv8+Azq4gXChcRGVsdGEgelwpICjOvM61IFwoRCA9IEwgPSAweyx9MTBcKSBtKTo8L3A+CjxkaXYgY2xhc3M9ImZiIj5cWyBcRGVsdGEgeiA9IFxmcmFje0Zfen17bV97QWd9fVxjZG90XGxlZnQoXGZyYWN7TH17dn1ccmlnaHQpXjJcY2RvdFxmcmFjezN9ezJ9Cj0gXGZyYWN7XHJ1bGV7MmNtfXswLjVwdH19ezF7LH03OTFcdGltZXMxMF57LTI1fX1cY2RvdFxsZWZ0KFxmcmFjezB7LH0xMH17NTAwfVxyaWdodCleMlxjZG90IDF7LH01Cj0gXHJ1bGV7Mi41Y219ezAuNXB0fSBcdGV4dHsgbW19IFxdPC9kaXY+CjxwPjxzdHJvbmc+zpM0Ljwvc3Ryb25nPiDOpM65zrzOriDOsc+Az4wgz4TOt869IM+Az4HOv8+Dzr/OvM6/zq/Pic+Dzrc6IFwoXERlbHRhIHpfe3NpbX0gPSBcKSBfX19fX19fIG1tICZuYnNwOyZuYnNwOyDOo8+FzrzPhs+Jzr3Or86xOyBfX188L3A+Cgo8aDI+JiN4MUY0Q0E7IM6czq3Pgc6/z4IgzpQgJm5kYXNoOyDOlc+Azq/OtM+BzrHPg863IM6gzrHPgc6xzrzOrc+Ez4HPic69PC9oMj4KPHA+zpTOuc6xz4TOrs+BzrfPg861IDxzcGFuIGNsYXNzPSJobCI+QWc8L3NwYW4+IM66zrHOuSDOrM67zrvOsc6+zrUgzrrOrM64zrUgz4bOv8+BzqwgPHN0cm9uZz7OvM+Mzr3OvyDOvM6vzrE8L3N0cm9uZz4gz4DOsc+BzqzOvM61z4TPgc6/OjwvcD4KPHRhYmxlPgo8dHI+PHRoPlwoXHBhcnRpYWwgQi9ccGFydGlhbCB6XCkgKFQvbSk8L3RoPjx0aD5cKExcKSAobSk8L3RoPjx0aD5cKHZcKSAobS9zKTwvdGg+PHRoPlwofFxEZWx0YSB6fF97bWF4fVwpIChtbSk8L3RoPjwvdHI+Cjx0cj48dGQ+NTwvdGQ+PHRkPjAsMTA8L3RkPjx0ZD41MDA8L3RkPjx0ZCBjbGFzcz0iZSI+PC90ZD48L3RyPgo8dHI+PHRkPjEwPC90ZD48dGQ+MCwxMDwvdGQ+PHRkPjUwMDwvdGQ+PHRkIGNsYXNzPSJlIj48L3RkPjwvdHI+Cjx0cj48dGQ+MjA8L3RkPjx0ZD4wLDEwPC90ZD48dGQ+NTAwPC90ZD48dGQgY2xhc3M9ImUiPjwvdGQ+PC90cj4KPHRyPjx0ZD41PC90ZD48dGQ+MCwyMDwvdGQ+PHRkPjUwMDwvdGQ+PHRkIGNsYXNzPSJlIj48L3RkPjwvdHI+Cjx0cj48dGQ+NTwvdGQ+PHRkPjAsMTA8L3RkPjx0ZD4xMDAwPC90ZD48dGQgY2xhc3M9ImUiPjwvdGQ+PC90cj4KPC90YWJsZT4KPHA+PHN0cm9uZz7OlDEuPC9zdHJvbmc+IM6UzrnPgM67zrHPg865zqzOts6/zr3PhM6xz4IgXChccGFydGlhbCBCL1xwYXJ0aWFsIHpcKSwgzrcgzrXOus+Ez4HOv8+Azq4gX19fX1/PgM67zrHPg865zqzOts61z4TOsc65LiDOk8+BzrHOvM68zrnOus6uIM+Dz4fOrc+Dzrc7IF9fXzwvcD4KPHA+PHN0cm9uZz7OlDIuPC9zdHJvbmc+IM6UzrnPgM67zrHPg865zqzOts6/zr3PhM6xz4IgXChMXCksIM63IM61zrrPhM+Bzr/PgM6uIF9fX19fz4DOu86xz4POuc6szrbOtc+EzrHOuS4gKM6lz4DPjM60zrXOuc6+zrc6IFwoXERlbHRhIHogXHByb3B0byBMXjJcKSkgzpPOuc6xz4TOrzs8L3A+CjxkaXYgY2xhc3M9ImxpbmVzIj48ZGl2IGNsYXNzPSJsaW5lIj48L2Rpdj48ZGl2IGNsYXNzPSJsaW5lIj48L2Rpdj48L2Rpdj4KPHA+PHN0cm9uZz7OlDMuPC9zdHJvbmc+IM6UzrnPgM67zrHPg865zqzOts6/zr3PhM6xz4IgXCh2XCksIM63IM61zrrPhM+Bzr/PgM6uIF9fX19fLiAozqXPgM+MzrTOtc65zr7OtzogXChcRGVsdGEgeiBccHJvcHRvIHZeey0yfVwpKSDOk865zrHPhM6vOzwvcD4KPGRpdiBjbGFzcz0ibGluZXMiPjxkaXYgY2xhc3M9ImxpbmUiPjwvZGl2PjxkaXYgY2xhc3M9ImxpbmUiPjwvZGl2PjwvZGl2PgoKPGgyPiYjeDFGOTE0OyDOnM6tz4HOv8+CIM6VICZuZGFzaDsgzpPOuc6xz4TOryDOrM+Ezr/OvM6xIEFnIM66zrHOuSDPjM+HzrkgzrXOu861z43OuM61z4HOsSDOt867zrXOus+Ez4HPjM69zrnOsTs8L2gyPgo8ZGl2IGNsYXNzPSJ3YXJuIj4mI3gyNkEwOyYjeEZFMEY7IDxzdHJvbmc+zpXPgc+Oz4TOt8+DzrcgzrPOuc6xIM+DzrrOrc+Izrc6PC9zdHJvbmc+IM6fzrkgU3Rlcm4gJmFtcDsgR2VybGFjaCDOrs64zrXOu86xzr0gzr3OsSDOvM61z4TPgc6uz4POv8+Fzr0gz4TOtyDOvM6xzrPOvc63z4TOuc66zq4gz4HOv8+Azq4gz4TOv8+FIM63zrvOtc66z4TPgc6/zr3Or86/z4UuCs6TzrnOsc+Ezq8gzrXPgM6tzrvOtc6+zrHOvSDOv8+FzrTOrc+EzrXPgc6xIM6sz4TOv868zrEgQWcgzrHOvc+Ezq8gzrPOuc6xIM61zrvOtc+NzrjOtc+BzrEgzrfOu861zrrPhM+Bz4zOvc65zrEgz4DOv8+FIM+AzrHPgc6szrPOv869z4TOsc65IM61z43Ous6/zrvOsSDOvM61IM64zrXPgc68zrnOv869zrnOus6uIM61zrrPgM6/zrzPgM6uOzwvZGl2Pgo8cD48c3Ryb25nPs6VMS48L3N0cm9uZz4gzojOvc6xIM66zrnOvc6/z43OvM61zr3OvyDPhs6/z4HPhM65z4POvM6tzr3OvyDPg8+JzrzOsc+Ezq/OtM65zr8gz4POtSDOvM6xzrPOvc63z4TOuc66z4wgz4DOtc60zq/OvyDOtM6tz4fOtc+EzrHOuSDOtM+Nzr3Osc68zrcgTG9yZW50ejoKXChGX3tMb3J9ID0gcXZCXCkuIM6TzrnOsSBcKHEgPSAxeyx9Nlx0aW1lczEwXnstMTl9XCkgQywgXCh2ID0gNTAwXCkgbS9zLCBcKEIgPSAweyx9MVwpIFQ6PC9wPgo8ZGl2IGNsYXNzPSJmYiI+XFsgRl97TG9yfSA9IFxydWxlezRjbX17MC41cHR9IFx0ZXh0eyBOfSBcXTwvZGl2Pgo8cD48c3Ryb25nPs6VMi48L3N0cm9uZz4gzpcgzrTPjc69zrHOvM63IM67z4zOs8+JIM68zrHOs869zrfPhM65zrrOrs+CIM+Bzr/PgM6uz4IgzrXOr869zrHOuSBcKEZfe3NwaW59IFxhcHByb3ggXG11X0IgXGNkb3QgKFxwYXJ0aWFsIEIvXHBhcnRpYWwgeikgPSA0eyx9Nlx0aW1lczEwXnstMjN9XCkgTi4gzqXPgM6/zrvPjM6zzrnPg861OjwvcD4KPGRpdiBjbGFzcz0iZmIiPlxbIFxmcmFje0Zfe0xvcn19e0Zfe3NwaW59fSA9IFxmcmFje1xydWxlezIuNWNtfXswLjVwdH19ezR7LH02XHRpbWVzMTBeey0yM319ID0gXHJ1bGV7MmNtfXswLjVwdH0gXHRleHR7IM+Gzr/Pgc6tz4J9IFxdPC9kaXY+CjxwPjxzdHJvbmc+zpUzLjwvc3Ryb25nPiDOk865zrHPhM6vIM61zq/Ovc6xzrkgzrHOtM+Nzr3Osc+Ezr8gzr3OsSDPgM6xz4HOsc+EzrfPgc63zrjOtc6vIM61zrrPhM+Bzr/PgM6uIM67z4zOs8+JIHNwaW4gz4POtSDOtM6tz4POvM63IM61zrvOtc+NzrjOtc+Bz4nOvSDOt867zrXOus+Ez4HOv869zq/Pic69OzwvcD4KPGRpdiBjbGFzcz0ic3RlcCI+zpHOvc6xzrvOv86zzq/OsTogzpHOvSDOuM6tzrvOtc65z4Igzr3OsSDOsc66zr/Pjc+DzrXOuc+CIM6tzr3Osc69IM+Izq/OuM+Fz4HOvywgz4TOuSDPgM+Bzq3PgM61zrkgzr3OsSDOus6szr3Otc65z4IgzrzOtSDPhM6/zr0gzrjPjM+Bz4XOss6/IM+AzrXPgc65zrLOrM67zrvOv869z4TOv8+COzwvZGl2Pgo8ZGl2IGNsYXNzPSJsaW5lcyI+PGRpdiBjbGFzcz0ibGluZSI+PC9kaXY+PGRpdiBjbGFzcz0ibGluZSI+PC9kaXY+PC9kaXY+CjxwPjxzdHJvbmc+zpU0Ljwvc3Ryb25nPiDOl867zrXOus+Ez4HOv869zrnOus6uIM60zr/OvM6uIEFnOiBcKFtcbWF0aHJte0tyfV1cLCA0ZF57MTB9XCwgNXNeMVwpLiDOoM+Mz4POsSDOvM6/zr3Ors+BzrcgzrfOu861zrrPhM+Bz4zOvc65zrE7IF9fXzxicj4KzpfOu861zrrPhM+BzrnOus6sIM+Ezr8gQWcgzrXOr869zrHOuSAozrrPjc66zrvPic+DzrUpOiAmbmJzcDsgPHN0cm9uZz7On86lzpTOlc6kzpXOoc6fPC9zdHJvbmc+IC8gzqbOn86hzqTOmc6jzpzOlc6dzp8gJm5ic3A7JnJhcnI7Jm5ic3A7IFwoRl97TG9yfSA9XCkgX19fPC9wPgo8cD48c3Ryb25nPs6VNS48L3N0cm9uZz4gzqTOuSDOtc6vzrTOv8+Fz4IgzrTPjc69zrHOvM63IM60zq3Ph861z4TOsc65IM+EzrXOu865zrrOrCDPhM6/IM6sz4TOv868zr8gQWc7ICjOlM61zr0gzrXOr869zrHOuSBMb3JlbnR6ISk8L3A+CjxkaXYgY2xhc3M9ImZiIj5cWyBGID0gXG5hYmxhKFxib2xkc3ltYm9se1xtdX0gXGNkb3QgXG1hdGhiZntCfSkgPSBtX2ogXGNkb3QgZ19qIFxjZG90IFxtdV9CIFxjZG90IFxmcmFje1xwYXJ0aWFsIEJ9e1xwYXJ0aWFsIHp9IFxdPC9kaXY+CjxkaXYgY2xhc3M9ImxpbmVzIj48ZGl2IGNsYXNzPSJsaW5lIj48L2Rpdj48L2Rpdj4KCjxoMj4mI3gyNzA1OyDOnM6tz4HOv8+CIM6jzqQgJm5kYXNoOyDOlc+AzrHOu86uzrjOtc+Fz4POtyAmIM6jz4XOvM+AzrXPgc6sz4POvM6xz4TOsTwvaDI+Cjx0YWJsZT4KPHRyPjx0aD7OnM6tzrPOtc64zr/PgjwvdGg+PHRoPs6YzrXPic+BzrfPhM65zrrOriDPhM65zrzOrjwvdGg+PHRoPs6kzrnOvM6uIM+Az4HOv8+Dzr/OvM6/zq/Pic+DzrfPgjwvdGg+PHRoPs6jz4XOvM+Gz4nOvc6vzrE7PC90aD48L3RyPgo8dHI+PHRkPs6Uz43Ovc6xzrzOtyBGIChtX2o9KzEvMik8L3RkPjx0ZCBjbGFzcz0iZSI+PC90ZD48dGQgY2xhc3M9ImUiPjwvdGQ+PHRkIGNsYXNzPSJlIj48L3RkPjwvdHI+Cjx0cj48dGQ+zpXOus+Ez4HOv8+Azq4gzpR6IChtbSk8L3RkPjx0ZCBjbGFzcz0iZSI+PC90ZD48dGQgY2xhc3M9ImUiPjwvdGQ+PHRkIGNsYXNzPSJlIj48L3RkPjwvdHI+Cjx0cj48dGQ+zpHPgc65zrjOvM+Mz4IgzrTOtc+DzrzPjs69IEFnPC90ZD48dGQ+MiAoPTJzKzEpPC90ZD48dGQgY2xhc3M9ImUiPjwvdGQ+PHRkIGNsYXNzPSJlIj48L3RkPjwvdHI+CjwvdGFibGU+CjxwPjxzdHJvbmc+zqPOpDEuPC9zdHJvbmc+IM6Rz4DOv860zrXOuc66zr3Pjc61zrkgz4TOvyDPgM61zq/Pgc6xzrzOsSDPjM+Ezrkgzrcgz4PPhM+Bzr/Phs6/z4HOvM6uIM61zq/Ovc6xzrkgzrrOss6xzr3PhM65z4POvM6tzr3OtzsgzpTOuc66zrHOuc6/zrvPjM6zzrfPg861OjwvcD4KPGRpdiBjbGFzcz0ibGluZXMiPjxkaXYgY2xhc3M9ImxpbmUiPjwvZGl2PjxkaXYgY2xhc3M9ImxpbmUiPjwvZGl2PjxkaXYgY2xhc3M9ImxpbmUiPjwvZGl2PjwvZGl2Pgo8cD48c3Ryb25nPs6jzqQyLjwvc3Ryb25nPiDOkc69IM63IM+Dz4TPgc6/z4bOv8+BzrzOriDOtM61zr0gzq7PhM6xzr0gzrrOss6xzr3PhM65z4POvM6tzr3OtyAozrrOu86xz4POuc66zq4gz4bPhc+DzrnOus6uKSwgz4TOuSDOuM6xIM6tzrLOu861z4DOtc+CIM+Dz4TOtyDPhs+Jz4TOv86zz4HOsc+GzrnOus6uIM+AzrvOrM66zrE7PC9wPgo8ZGl2IGNsYXNzPSJsaW5lcyI+PGRpdiBjbGFzcz0ibGluZSI+PC9kaXY+PGRpdiBjbGFzcz0ibGluZSI+PC9kaXY+PC9kaXY+CjxwPjxzdHJvbmc+zqPOpDMuPC9zdHJvbmc+IM6Zz4PPhM6/z4HOuc66zq4gz4POt868zrXOr8+Jz4POtzogzr/OuSBTdGVybuKAk0dlcmxhY2ggzrHOvc6tzrzOtc69zrHOvSDOsc+Azr/PhM6tzrvOtc+DzrzOsSDOs865zrEgz4TPgc6/z4fOuc6xzrrOriDPg8+Ez4HOv8+Gzr/Pgc68zq4gXChMPTFcKSAoMyDOtM6tz4POvM61z4IpLgrOks+Bzq7Ous6xzr0gz4zOvM+Jz4IgMiDOtM6tz4POvM61z4IuIM6kzrkgwqvOrc+Dz4nPg861wrsgz4TOvyDPgM61zq/Pgc6xzrzOsSDigJQgzrrOsc65IM+EzrkgzrHPgM6/zrrOrM67z4XPiM61Owo8L3A+CjxkaXYgY2xhc3M9ImxpbmVzIj48ZGl2IGNsYXNzPSJsaW5lIj48L2Rpdj48ZGl2IGNsYXNzPSJsaW5lIj48L2Rpdj48ZGl2IGNsYXNzPSJsaW5lIj48L2Rpdj48L2Rpdj4KPGRpdiBjbGFzcz0iY2MiPgrOqM63z4bOuc6xzrrPjCDOsc69z4TOuc66zrXOr868zrXOvc6/OiDOoM61zq/Pgc6xzrzOsSBTdGVybiZuZGFzaDtHZXJsYWNoIHwgzqbPhc+DzrnOus6uIM6TJnByaW1lOyDOm8+FzrrOtc6vzr/PhTxicj4KzpTOt868zrnOv8+Fz4HOs86vzrEgJm5kYXNoOyDOkc69zqzPgM+Ez4XOvs63OiDOoM6xzr3Osc6zzrnPjs+EzrfPgiDOoM61z4TPgc6vzrTOt8+CICZuYnNwO3wmbmJzcDsKPGEgaHJlZj0iaHR0cHM6Ly9jcmVhdGl2ZWNvbW1vbnMub3JnL2xpY2Vuc2VzL2J5LW5jLXNhLzQuMC9kZWVkLmVsIj5DQyBCWS1OQy1TQSA0LjA8L2E+ICZuYnNwO3wmbmJzcDsKzpHOvc6xz4bOv8+Bzqwgz4PPhs6xzrvOvM6sz4TPic69OiBzY2goYXQpc2NoLmdyCjwvZGl2Pgo8L2JvZHk+CjwvaHRtbD4='];
  var fn=['Anoixth_Diereunhsh_Stern_Gerlach.html','Kathodoghmenh_Diereunhsh_Stern_Gerlach.html'];
  var bin=atob(b64[t]), bytes=new Uint8Array(bin.length);
  for(var i=0;i<bin.length;i++) bytes[i]=bin.charCodeAt(i);
  var blob=new Blob([bytes],{type:'text/html;charset=utf-8'});
  var a=document.createElement('a'); a.href=URL.createObjectURL(blob); a.download=fn[t];
  document.body.appendChild(a); a.click(); document.body.removeChild(a);
  setTimeout(function(){URL.revokeObjectURL(a.href);},2000);
}

function loop(){
  resize();
  if(running){
    spawnT++;
    var rate=parseInt(document.getElementById('rS').value), intv=[55,30,14][rate-1];
    if(spawnT>intv && particles.length<500){spawnT=0; spawnParticle();}
    updateParticles();
  }
  renderer.render(scene,camera);
  requestAnimationFrame(loop);
}

document.getElementById('gS').addEventListener('input',updateUI);
document.getElementById('lS').addEventListener('input',updateUI);
document.getElementById('vS').addEventListener('input',updateUI);
document.getElementById('rS').addEventListener('input',function(){
  var rates=["\u03a7\u03b1\u03bc\u03b7\u03bb\u03cc\u03c2","\u039c\u03ad\u03c3\u03b1\u03b9\u03bf\u03c2","\u03a5\u03c8\u03b7\u03bb\u03cc\u03c2"];

  document.getElementById('rV').textContent=rates[parseInt(this.value)-1];
});
document.getElementById('startBtn').addEventListener('click',function(){
  running=true; spawnT=0;
  document.getElementById('startBtn').disabled=true;
  document.getElementById('stopBtn').disabled=false;
  document.getElementById('rind').classList.add('on');
});
document.getElementById('stopBtn').addEventListener('click',function(){
  running=false;
  document.getElementById('startBtn').disabled=false;
  document.getElementById('stopBtn').disabled=true;
  document.getElementById('rind').classList.remove('on');
});
document.getElementById('clearBtn').addEventListener('click',clearAll);
document.getElementById('wsModal').addEventListener('click',function(e){if(e.target===this)this.classList.remove('open');});
window.addEventListener('resize',resize);

buildScGrid(); updateUI(); loop();

</script>
</div>

---

## 📖 Οδηγίες Χρήσης

### Βασικές λειτουργίες

| Ενέργεια | Περιγραφή |
|----------|-----------|
| **Drag** ποντίκι | Περιστροφή της τρισδιάστατης σκηνής |
| **Scroll** | Zoom in/out |
| **▶ ΕΝΑΡΞΗ** | Εκτόξευση ατόμων από τον κλίβανο |
| **⏹ ΔΙΑΚΟΠΗ** | Παύση προσομοίωσης |
| **✕ Εκκαθάριση** | Διαγραφή σωματιδίων και ιχνών |
| **↕ 0° / ↔ 90°** | Περιστροφή μαγνήτη γύρω από τον άξονα δέσμης |

### Παράμετροι

- **∂B/∂z**: Κλίση του μαγνητικού πεδίου — αυξάνει τον αριθμό δυναμικών γραμμών και την εκτροπή
- **L**: Μήκος μαγνήτη — αλλάζει οπτικά το μέγεθός του, επηρεάζει την εκτροπή (Δz ∝ L²)
- **v**: Ταχύτητα ατόμων — μικρότερη ταχύτητα → μεγαλύτερη εκτροπή (Δz ∝ v⁻²)

### Τι παρατηρώ στη φωτογραφική πλάκα

- **0°** (κατακόρυφη λεπίδα): δύο **οριζόντιες** παράλληλες γραμμές
- **90°** (οριζόντια λεπίδα): δύο **κατακόρυφες** παράλληλες γραμμές
- Σενάριο **²H** (s=1): τρεις γραμμές — η μεσαία (m_j=0) δεν εκτρέπεται

---

## 💾 Λήψη Αρχείου για Offline Χρήση

[📥 Κατέβασμα Προσομοίωσης (HTML)](https://drive.google.com/uc?export=download&id=PLACEHOLDER_ID)

Αποθηκεύστε το αρχείο και ανοίξτε το με οποιονδήποτε browser (Chrome, Firefox, Edge).

---

## 📄 Φύλλα Εργασίας

Πατήστε το κουμπί **📄 Επιλογή Φύλλου** μέσα στην προσομοίωση για να κατεβάσετε:

- **🔍 Ανοιχτή Διερεύνηση** — Ο μαθητής σχεδιάζει ο ίδιος τη διερεύνηση
- **📋 Καθοδηγούμενη Διερεύνηση** — Δομημένα βήματα, πίνακες, υπολογισμοί, ερωτήσεις

---

### 🆘 Επικοινωνία

Αν έχετε πρόβλημα ή πρόταση βελτίωσης:
- Email: sch(at)sch.gr
- Ή μέσω των social media buttons!
