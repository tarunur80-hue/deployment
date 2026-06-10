[nutri-scope.html](https://github.com/user-attachments/files/28787017/nutri-scope.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>NutriScope Pro — Advanced Nutrition Tracking</title>
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.min.js"></script>
<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=Space+Grotesk:wght@400;500;600;700&display=swap');
:root{
  --bg-base:#0a0b0f;--bg-surface:#111318;--bg-elevated:#181b22;--bg-card:#1e2230;--bg-input:#13161e;
  --border:rgba(255,255,255,.07);--border-hi:rgba(99,179,237,.35);
  --accent:#63b3ed;--accent-g:rgba(99,179,237,.15);--a2:#68d391;--aw:#f6ad55;--ad:#fc8181;--ap:#b794f4;
  --txt:#f0f4ff;--txt2:#8892a4;--txtm:#4a5568;
  --grad:linear-gradient(135deg,#1e2230 0%,#181b22 100%);
  --rsm:8px;--rmd:12px;--rlg:16px;--rxl:20px;
  --sh:0 4px 24px rgba(0,0,0,.4);
  --fd:'Space Grotesk',sans-serif;--fb:'Inter',sans-serif;
}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth}
body{font-family:var(--fb);background:var(--bg-base);color:var(--txt);min-height:100vh;line-height:1.6}
/* HEADER */
header{position:sticky;top:0;z-index:100;background:rgba(10,11,15,.94);backdrop-filter:blur(16px);
  border-bottom:1px solid var(--border);padding:0 22px;height:58px;display:flex;align-items:center;justify-content:space-between}
.logo{font-family:var(--fd);font-size:19px;font-weight:700;letter-spacing:-.5px;display:flex;align-items:center;gap:9px}
.logo-icon{width:30px;height:30px;background:linear-gradient(135deg,var(--accent),#4299e1);border-radius:7px;display:flex;align-items:center;justify-content:center;font-size:15px}
.logo span{color:var(--accent)}.logo em{font-size:11px;font-style:normal;color:var(--txt2);font-weight:400;margin-left:4px}
.hdr-r{display:flex;align-items:center;gap:10px}
.score-badge{font-family:var(--fd);font-size:13px;font-weight:700;padding:4px 13px;border-radius:20px;
  border:1px solid var(--border);background:var(--bg-elevated);display:flex;align-items:center;gap:6px}
.sdot{width:7px;height:7px;border-radius:50%;background:var(--txtm);flex-shrink:0;transition:background .4s}
.hbadge{font-size:11px;font-weight:500;color:var(--accent);background:var(--accent-g);border:1px solid var(--border-hi);padding:3px 9px;border-radius:20px}
/* LAYOUT */
.app{max-width:1340px;margin:0 auto;padding:26px 18px;display:grid;grid-template-columns:308px 1fr;gap:20px;align-items:start}
.sidebar{display:flex;flex-direction:column;gap:16px}
/* CARD */
.card{background:var(--grad);border:1px solid var(--border);border-radius:var(--rxl);padding:20px;box-shadow:var(--sh);transition:border-color .2s}
.card:hover{border-color:rgba(255,255,255,.11)}
.ct{font-family:var(--fd);font-size:11px;font-weight:600;letter-spacing:.8px;text-transform:uppercase;
  color:var(--txt2);margin-bottom:14px;display:flex;align-items:center;gap:7px}
.ct::before{content:'';width:3px;height:12px;background:var(--accent);border-radius:2px;display:inline-block;flex-shrink:0}
/* FORMS */
.fg{margin-bottom:11px}
label{display:block;font-size:12px;font-weight:500;color:var(--txt2);margin-bottom:4px}
input,select,textarea{width:100%;background:var(--bg-input);border:1px solid var(--border);border-radius:var(--rsm);
  color:var(--txt);font-family:var(--fb);font-size:13px;padding:8px 10px;outline:none;
  transition:border-color .2s,box-shadow .2s;-webkit-appearance:none;appearance:none}
select{background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='11' height='11' viewBox='0 0 24 24' fill='none' stroke='%238892a4' stroke-width='2'%3E%3Cpath d='M6 9l6 6 6-6'/%3E%3C/svg%3E");
  background-repeat:no-repeat;background-position:right 10px center;padding-right:30px}
input:focus,select:focus,textarea:focus{border-color:var(--border-hi);box-shadow:0 0 0 3px var(--accent-g)}
input::placeholder{color:var(--txtm)}
.fr{display:grid;grid-template-columns:1fr 1fr;gap:9px}
/* BUTTONS */
.btn{display:inline-flex;align-items:center;justify-content:center;gap:6px;font-family:var(--fb);font-size:13px;font-weight:500;
  border:none;border-radius:var(--rsm);cursor:pointer;transition:all .2s;padding:8px 15px;white-space:nowrap}
.btn-p{background:linear-gradient(135deg,var(--accent),#4299e1);color:#fff;box-shadow:0 2px 10px rgba(99,179,237,.25)}
.btn-p:hover{opacity:.87;transform:translateY(-1px);box-shadow:0 4px 18px rgba(99,179,237,.35)}
.btn-g{background:transparent;color:var(--txt2);border:1px solid var(--border)}
.btn-g:hover{background:var(--bg-elevated);color:var(--txt);border-color:rgba(255,255,255,.14)}
.btn-d{background:rgba(252,129,129,.1);color:var(--ad);border:1px solid rgba(252,129,129,.2);font-size:12px;padding:5px 10px}
.btn-d:hover{background:rgba(252,129,129,.2)}
.btn-w{background:rgba(246,173,85,.1);color:var(--aw);border:1px solid rgba(246,173,85,.2);font-size:12px;padding:5px 10px}
.btn-full{width:100%}
/* TABS */
.tab-row{display:flex;gap:3px;background:var(--bg-elevated);border-radius:var(--rsm);padding:3px;margin-bottom:16px;overflow-x:auto;flex-shrink:0}
.tb{flex:1;font-family:var(--fb);font-size:12px;font-weight:500;padding:7px 8px;border:none;border-radius:6px;
  cursor:pointer;color:var(--txt2);background:transparent;transition:all .2s;white-space:nowrap}
.tb.active{background:var(--bg-card);color:var(--txt);box-shadow:0 1px 5px rgba(0,0,0,.3)}
.tp{display:none}.tp.active{display:block}
/* GRIDS */
.mc{display:flex;flex-direction:column;gap:16px}
.g2{display:grid;grid-template-columns:1fr 1fr;gap:16px}
.g3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:13px}
.g4{display:grid;grid-template-columns:repeat(4,1fr);gap:11px}
/* STAT PILLS */
.sp{background:var(--bg-elevated);border:1px solid var(--border);border-radius:var(--rmd);padding:13px 14px;display:flex;flex-direction:column;gap:2px}
.spl{font-size:10px;color:var(--txt2);font-weight:500;letter-spacing:.3px}
.spv{font-family:var(--fd);font-size:20px;font-weight:700;color:var(--txt);line-height:1.1}
.sps{font-size:10px;color:var(--txtm)}
.sp.good{border-color:rgba(104,211,145,.25)}.sp.good .spv{color:var(--a2)}
.sp.warn{border-color:rgba(246,173,85,.25)}.sp.warn .spv{color:var(--aw)}
.sp.bad{border-color:rgba(252,129,129,.25)}.sp.bad .spv{color:var(--ad)}
/* ENERGY RING */
.rw{position:relative;width:130px;height:130px;flex-shrink:0}
.rw canvas{width:130px!important;height:130px!important}
.rc{position:absolute;inset:0;display:flex;flex-direction:column;align-items:center;justify-content:center;pointer-events:none}
.rk{font-family:var(--fd);font-size:24px;font-weight:700;line-height:1}
.rl{font-size:10px;color:var(--txt2);margin-top:2px}
.rt{font-size:10px;color:var(--txtm);margin-top:1px}
/* MACRO BARS */
.mb-wrap{display:flex;flex-direction:column;gap:10px;flex:1;min-width:130px}
.mbh{display:flex;justify-content:space-between;font-size:12px;margin-bottom:3px}
.mbn{color:var(--txt2);font-weight:500}.mbv{color:var(--txt);font-weight:600}.mbp{color:var(--txtm);font-size:11px}
.pt{height:5px;background:var(--bg-elevated);border-radius:99px;overflow:hidden}
.pf{height:100%;border-radius:99px;transition:width .7s cubic-bezier(.4,0,.2,1)}
/* LOG TABLE */
.ls{margin-bottom:18px}
.mgh{font-size:11px;font-weight:600;letter-spacing:.5px;text-transform:uppercase;color:var(--txt2);
  padding:7px 0 5px;border-bottom:1px solid var(--border);margin-bottom:2px;
  display:flex;align-items:center;justify-content:space-between}
.mkb{font-size:10px;color:var(--txtm);background:var(--bg-elevated);padding:2px 7px;border-radius:99px}
.ftw{overflow-x:auto;border-radius:var(--rmd);border:1px solid var(--border)}
table{width:100%;border-collapse:collapse}
thead th{background:var(--bg-elevated);font-size:10px;font-weight:600;letter-spacing:.5px;text-transform:uppercase;
  color:var(--txt2);padding:8px 11px;text-align:left;border-bottom:1px solid var(--border);white-space:nowrap}
tbody tr{border-bottom:1px solid var(--border);transition:background .15s}
tbody tr:last-child{border-bottom:none}
tbody tr:hover{background:rgba(255,255,255,.022)}
td{padding:8px 11px;font-size:13px;color:var(--txt);vertical-align:middle}
td.dim{color:var(--txt2);font-size:12px}
.eq{width:65px;background:var(--bg-input);border:1px solid var(--border);border-radius:5px;
  color:var(--txt);font-size:12px;padding:3px 7px;text-align:center}
.eq:focus{border-color:var(--border-hi);outline:none;box-shadow:0 0 0 2px var(--accent-g)}
.es{text-align:center;padding:32px 18px;color:var(--txtm);font-size:13px}
.ei{font-size:26px;display:block;margin-bottom:7px}
/* LOG ADD BAR */
.lab{display:grid;grid-template-columns:2fr 1fr 1fr 1fr auto;gap:8px;align-items:end;
  padding:13px 14px;background:var(--bg-elevated);border-radius:var(--rmd);border:1px solid var(--border);margin-bottom:12px}
/* NUTRIENT TABLE */
.nt{width:100%;border-collapse:collapse;font-size:13px}
.nt th{font-size:10px;font-weight:600;letter-spacing:.5px;text-transform:uppercase;color:var(--txt2);
  padding:7px 11px;text-align:left;border-bottom:1px solid var(--border)}
.nt td{padding:9px 11px;border-bottom:1px solid rgba(255,255,255,.035);vertical-align:middle}
.nt tr:last-child td{border-bottom:none}
.ntb{height:4px;border-radius:99px;background:var(--bg-elevated);overflow:hidden;width:80px;display:inline-block;vertical-align:middle}
.ntf{height:100%;border-radius:99px;min-width:2px}
.badge{display:inline-flex;align-items:center;font-size:9px;font-weight:700;letter-spacing:.3px;padding:2px 7px;border-radius:99px}
.bok{background:rgba(104,211,145,.12);color:var(--a2)}.blow{background:rgba(252,129,129,.12);color:var(--ad)}
.bwarn{background:rgba(246,173,85,.12);color:var(--aw)}.bhigh{background:rgba(246,173,85,.12);color:var(--aw)}
/* DEF/EXCESS */
.del{display:flex;flex-direction:column;gap:6px}
.di{display:flex;align-items:center;justify-content:space-between;padding:8px 12px;background:var(--bg-elevated);border-radius:var(--rsm)}
.dn{color:var(--txt);font-weight:500;font-size:12px}
.dr{display:flex;align-items:center;gap:9px}
.dp{font-size:11px;color:var(--txt2)}
.dbm{width:44px;height:3px;background:rgba(255,255,255,.06);border-radius:99px;overflow:hidden}
.dfm{height:100%;border-radius:99px}
/* RECO */
.rl2{display:flex;flex-direction:column;gap:8px}
.ri{background:var(--bg-elevated);border-radius:var(--rmd);border-left:3px solid var(--accent);
  padding:11px 13px;font-size:13px;color:var(--txt);line-height:1.55}
.ri.swap{border-color:var(--aw)}.ri.add{border-color:var(--a2)}.ri.port{border-color:var(--ap)}.ri.risk{border-color:var(--ad)}
.rt2{font-size:9px;font-weight:700;letter-spacing:.8px;text-transform:uppercase;margin-bottom:4px}
.rt2.add{color:var(--a2)}.rt2.swap{color:var(--aw)}.rt2.port{color:var(--ap)}.rt2.risk{color:var(--ad)}
.re{text-align:center;padding:28px;color:var(--txtm);font-size:13px}
/* SECTION */
.sh{font-family:var(--fd);font-size:14px;font-weight:600;color:var(--txt);margin-bottom:2px}
.ss{font-size:12px;color:var(--txt2);margin-bottom:12px}
hr{border:none;border-top:1px solid var(--border);margin:14px 0}
/* TARGETS */
.tg{display:grid;grid-template-columns:1fr 1fr;gap:7px}
.tc{background:var(--bg-elevated);border-radius:7px;padding:8px 10px}
.tcl{font-size:10px;color:var(--txtm);margin-bottom:1px}
.tcv{font-size:12px;font-weight:600;color:var(--txt)}
/* SCORE BARS */
.sbr{display:flex;align-items:center;gap:9px;margin-bottom:5px}
.sbl{font-size:11px;color:var(--txt2);width:82px;flex-shrink:0}
.sbt{flex:1;height:5px;background:var(--bg-elevated);border-radius:99px;overflow:hidden}
.sbf{height:100%;border-radius:99px;transition:width .7s cubic-bezier(.4,0,.2,1)}
.sbp{font-size:10px;color:var(--txt2);width:28px;text-align:right;flex-shrink:0}
/* RISK */
.risk-item{background:var(--bg-elevated);border-radius:var(--rmd);border:1px solid var(--border);padding:14px 16px;margin-bottom:10px}
.risk-head{display:flex;align-items:center;gap:10px;margin-bottom:8px}
.risk-icon{font-size:18px;flex-shrink:0}
.risk-title{font-weight:600;font-size:13px;color:var(--txt)}
.risk-level{font-size:10px;font-weight:700;letter-spacing:.5px;text-transform:uppercase;
  padding:2px 8px;border-radius:99px;margin-left:auto;flex-shrink:0}
.rl-low{background:rgba(104,211,145,.15);color:var(--a2)}
.rl-med{background:rgba(246,173,85,.15);color:var(--aw)}
.rl-high{background:rgba(252,129,129,.15);color:var(--ad)}
.risk-desc{font-size:12px;color:var(--txt2);line-height:1.55}
/* MEAL PLANNER */
.planner-grid{display:grid;grid-template-columns:1fr 1fr;gap:16px}
.day-col{background:var(--bg-elevated);border-radius:var(--rlg);padding:16px;border:1px solid var(--border)}
.day-head{font-family:var(--fd);font-size:13px;font-weight:600;color:var(--txt);margin-bottom:12px;
  display:flex;align-items:center;justify-content:space-between}
.day-kcal{font-size:11px;color:var(--txt2);font-weight:400}
.meal-slot{margin-bottom:10px}
.meal-slot-head{font-size:11px;font-weight:600;letter-spacing:.4px;text-transform:uppercase;
  color:var(--txt2);margin-bottom:6px;display:flex;align-items:center;gap:6px}
.plan-food-add{display:flex;gap:7px;margin-bottom:5px}
.plan-food-add select{flex:1;font-size:12px;padding:6px 8px}
.plan-food-add input{width:60px;font-size:12px;padding:6px 8px}
.plan-food-add button{font-size:12px;padding:6px 11px;white-space:nowrap}
.plan-items{display:flex;flex-direction:column;gap:4px}
.plan-item{display:flex;align-items:center;justify-content:space-between;
  padding:5px 8px;background:var(--bg-card);border-radius:6px;font-size:12px}
.plan-item-name{color:var(--txt);font-weight:500}
.plan-item-info{color:var(--txt2);font-size:11px}
.plan-item-del{background:none;border:none;color:var(--txtm);cursor:pointer;padding:0 3px;font-size:13px;line-height:1}
.plan-item-del:hover{color:var(--ad)}
.plan-totals{margin-top:10px;padding-top:10px;border-top:1px solid var(--border);
  display:flex;flex-wrap:wrap;gap:8px}
.plan-tot-item{font-size:11px;color:var(--txt2)}
.plan-tot-item strong{color:var(--txt);font-weight:600}
/* CSV */
.csv-zone{border:2px dashed var(--border);border-radius:var(--rmd);padding:28px;text-align:center;
  cursor:pointer;transition:all .2s;background:var(--bg-elevated)}
.csv-zone:hover,.csv-zone.drag{border-color:var(--border-hi);background:rgba(99,179,237,.05)}
.csv-icon{font-size:28px;margin-bottom:8px}
.csv-lbl{font-size:13px;color:var(--txt2)}
.csv-sub{font-size:11px;color:var(--txtm);margin-top:4px}
.csv-preview{margin-top:14px;overflow-x:auto}
.csv-preview table{font-size:12px}
/* SOURCES */
.src-list{display:flex;flex-direction:column;gap:8px}
.src-item{background:var(--bg-elevated);border-radius:var(--rsm);padding:10px 13px;font-size:12px}
.src-name{font-weight:600;color:var(--txt);margin-bottom:2px}
.src-desc{color:var(--txt2);line-height:1.5}
/* DISCLAIMER */
.disclaimer{background:rgba(252,129,129,.06);border:1px solid rgba(252,129,129,.2);
  border-radius:var(--rmd);padding:14px 16px;font-size:12px;color:var(--txt2);line-height:1.6}
.disclaimer strong{color:var(--ad)}
/* PRINT */
@media print{
  header,.sidebar,.tab-row{display:none!important}
  .app{grid-template-columns:1fr;padding:0}
  .mc{gap:10px}
  .card{break-inside:avoid;border:1px solid #ddd;box-shadow:none}
  body{background:#fff;color:#111}
  .tp{display:block!important}
}
/* TOAST */
.tw{position:fixed;bottom:20px;right:20px;display:flex;flex-direction:column;gap:6px;z-index:999;pointer-events:none}
.toast{background:var(--bg-card);border:1px solid var(--border);border-radius:var(--rmd);
  padding:10px 15px;font-size:13px;color:var(--txt);box-shadow:var(--sh);
  animation:tin .3s ease forwards;pointer-events:auto}
@keyframes tin{from{opacity:0;transform:translateX(14px)}to{opacity:1;transform:translateX(0)}}
/* MODAL */
.modal-overlay{position:fixed;inset:0;background:rgba(0,0,0,.7);backdrop-filter:blur(4px);z-index:200;display:none;align-items:center;justify-content:center}
.modal-overlay.open{display:flex}
.modal{background:var(--bg-card);border:1px solid var(--border);border-radius:var(--rxl);
  padding:28px;max-width:480px;width:90%;box-shadow:0 20px 60px rgba(0,0,0,.6)}
.modal-title{font-family:var(--fd);font-size:16px;font-weight:600;margin-bottom:8px}
.modal-body{font-size:13px;color:var(--txt2);line-height:1.65;margin-bottom:20px}
.modal-foot{display:flex;justify-content:flex-end}
/* RESPONSIVE */
@media(max-width:980px){
  .app{grid-template-columns:1fr}
  .g2,.planner-grid{grid-template-columns:1fr}
  .g4{grid-template-columns:1fr 1fr}
  .lab{grid-template-columns:1fr 1fr 1fr}
  .lab .btn{grid-column:span 3}
}
@media(max-width:580px){
  .app{padding:12px}
  .g3,.g4{grid-template-columns:1fr}
  .fr{grid-template-columns:1fr}
  header{padding:0 13px}
  .hbadge{display:none}
  .lab{grid-template-columns:1fr 1fr}
  .lab .btn{grid-column:span 2}
}
::-webkit-scrollbar{width:5px;height:5px}
::-webkit-scrollbar-track{background:transparent}
::-webkit-scrollbar-thumb{background:rgba(255,255,255,.08);border-radius:99px}
</style>
</head>
<body>
 
<!-- DISCLAIMER MODAL -->
<div class="modal-overlay open" id="disclaimer-modal">
  <div class="modal">
    <div class="modal-title">⚕️ Educational Use Only</div>
    <div class="modal-body">
      <strong style="color:var(--ad)">NutriScope is not a medical device.</strong>
      <br><br>
      All nutrient data, targets, risk analyses, and recommendations are for <strong>general educational purposes only</strong> and are based on general population reference values (ICMR/WHO/NIH RDAs). They do not constitute medical advice.
      <br><br>
      Individual needs vary based on health conditions, medications, genetics, and other factors. Always consult a <strong>registered dietitian or physician</strong> before making significant dietary changes, especially if you have a medical condition.
      <br><br>
      Data sources: IFCT 2017 (Indian Food Composition Tables), USDA FoodData Central, ICMR Dietary Reference Intakes.
    </div>
    <div class="modal-foot">
      <button class="btn btn-p" onclick="closeDisclaimer()">I Understand — Continue</button>
    </div>
  </div>
</div>
 
<header>
  <div class="logo">
    <div class="logo-icon">🥗</div>
    Nutri<span>Scope</span><em>Pro</em>
  </div>
  <div class="hdr-r">
    <div class="score-badge"><div class="sdot" id="hdr-dot"></div><span id="hdr-score">Score: —</span></div>
    <div class="hbadge">v2.0 Enhanced</div>
  </div>
</header>
 
<div class="app">
  <!-- SIDEBAR -->
  <aside class="sidebar">
    <div class="card">
      <div class="ct">Your Profile</div>
      <div class="fr">
        <div class="fg"><label>Age (yrs)</label><input type="number" id="age" placeholder="25" min="10" max="100"></div>
        <div class="fg"><label>Gender</label>
          <select id="gender"><option value="male">Male</option><option value="female">Female</option></select>
        </div>
      </div>
      <div class="fr">
        <div class="fg"><label>Height (cm)</label><input type="number" id="height" placeholder="170"></div>
        <div class="fg"><label>Weight (kg)</label><input type="number" id="weight" placeholder="65"></div>
      </div>
      <div class="fg"><label>Health Condition</label>
        <select id="health">
          <option value="none">None / Healthy</option>
          <option value="diabetes">Diabetes / Pre-diabetes</option>
          <option value="hypertension">Hypertension</option>
          <option value="anemia">Anaemia</option>
          <option value="osteoporosis">Osteoporosis</option>
          <option value="kidney">Kidney Disease</option>
          <option value="pregnancy">Pregnancy</option>
          <option value="lactation">Lactation</option>
        </select>
      </div>
      <div class="fg"><label>Activity Level</label>
        <select id="activity">
          <option value="1.2">Sedentary (desk job)</option>
          <option value="1.375">Lightly Active (1–3×/wk)</option>
          <option value="1.55" selected>Moderately Active (3–5×/wk)</option>
          <option value="1.725">Very Active (6–7×/wk)</option>
          <option value="1.9">Extremely Active (athlete)</option>
        </select>
      </div>
      <div class="fg"><label>Dietary Preference</label>
        <select id="diet">
          <option value="veg">Vegetarian</option>
          <option value="nonveg" selected>Non-Vegetarian</option>
          <option value="egg">Eggetarian</option>
          <option value="vegan">Vegan</option>
        </select>
      </div>
      <button class="btn btn-p btn-full" onclick="applyProfile()">Apply Profile</button>
    </div>
 
    <div class="card">
      <div class="ct">Quick Add Food</div>
      <div class="fg"><label>Meal</label>
        <select id="sb-meal">
          <option value="Breakfast">🌅 Breakfast</option>
          <option value="Lunch" selected>☀️ Lunch</option>
          <option value="Dinner">🌙 Dinner</option>
          <option value="Snack">🍎 Snack</option>
        </select>
      </div>
      <div class="fg"><label>Food Item</label><select id="food-select"><option value="">— Choose food —</option></select></div>
      <div class="fr">
        <div class="fg"><label>Quantity</label><input type="number" id="food-qty" placeholder="100" min="1" step="any"></div>
        <div class="fg"><label>Unit</label>
          <select id="food-unit">
            <option value="g">grams</option><option value="ml">ml</option>
            <option value="piece">piece (≈100g)</option><option value="cup">cup (240ml)</option>
            <option value="tbsp">tbsp (15g)</option><option value="katori">katori (150g)</option>
          </select>
        </div>
      </div>
      <button class="btn btn-p btn-full" onclick="addFood('sb')">+ Add to Log</button>
    </div>
 
    <div class="card">
      <div class="ct">Daily Targets</div>
      <div id="targets-display"><p style="font-size:12px;color:var(--txtm);text-align:center;padding:10px 0">Fill profile and click Apply.</p></div>
    </div>
 
    <div class="card" style="padding:14px">
      <div style="display:flex;flex-direction:column;gap:7px">
        <button class="btn btn-g btn-full" onclick="clearLog()">🗑 Clear Today's Log</button>
        <button class="btn btn-g btn-full" onclick="exportCSV()">⬇ Export Log as CSV</button>
        <button class="btn btn-g btn-full" onclick="window.print()">🖨 Print Summary</button>
      </div>
    </div>
  </aside>
 
  <!-- MAIN -->
  <main class="mc">
    <div class="tab-row">
      <button class="tb active" onclick="stab('dashboard',this)">Dashboard</button>
      <button class="tb" onclick="stab('log',this)">Food Log</button>
      <button class="tb" onclick="stab('nutrients',this)">Nutrients</button>
      <button class="tb" onclick="stab('reco',this)">Recommendations</button>
      <button class="tb" onclick="stab('risk',this)">Risk Analysis</button>
      <button class="tb" onclick="stab('planner',this)">Meal Planner</button>
      <button class="tb" onclick="stab('upload',this)">CSV Upload</button>
      <button class="tb" onclick="stab('sources',this)">Sources</button>
    </div>
 
    <!-- DASHBOARD -->
    <div class="tp active" id="tab-dashboard">
      <div class="g4" style="margin-bottom:14px">
        <div class="sp" id="pill-bmi"><div class="spl">BMI</div><div class="spv" id="bmi-val">—</div><div class="sps" id="bmi-cat">Set profile</div></div>
        <div class="sp"><div class="spl">BMR</div><div class="spv" id="bmr-val">—</div><div class="sps">kcal base/day</div></div>
        <div class="sp"><div class="spl">TDEE Target</div><div class="spv" id="tdee-val">—</div><div class="sps">kcal goal/day</div></div>
        <div class="sp" id="pill-score"><div class="spl">Nutri Score</div><div class="spv" id="score-val">—</div><div class="sps" id="score-cat">Log food first</div></div>
      </div>
      <div class="g2">
        <div class="card">
          <div class="ct">Energy Balance</div>
          <div style="display:flex;align-items:center;gap:16px;flex-wrap:wrap">
            <div class="rw"><canvas id="energyRing"></canvas>
              <div class="rc"><div class="rk" id="ring-kcal">0</div><div class="rl">kcal eaten</div><div class="rt" id="ring-tgt">of — kcal</div></div>
            </div>
            <div class="mb-wrap">
              <div><div class="mbh"><span class="mbn">Protein</span><span><span class="mbv" id="mb-prot">0g</span> <span class="mbp" id="mb-prot-p"></span></span></div><div class="pt"><div class="pf" id="pb-prot" style="background:#63b3ed;width:0%"></div></div></div>
              <div><div class="mbh"><span class="mbn">Carbs</span><span><span class="mbv" id="mb-carb">0g</span> <span class="mbp" id="mb-carb-p"></span></span></div><div class="pt"><div class="pf" id="pb-carb" style="background:#f6ad55;width:0%"></div></div></div>
              <div><div class="mbh"><span class="mbn">Fat</span><span><span class="mbv" id="mb-fat">0g</span> <span class="mbp" id="mb-fat-p"></span></span></div><div class="pt"><div class="pf" id="pb-fat" style="background:#68d391;width:0%"></div></div></div>
              <div><div class="mbh"><span class="mbn">Fiber</span><span><span class="mbv" id="mb-fiber">0g</span> <span class="mbp" id="mb-fiber-p"></span></span></div><div class="pt"><div class="pf" id="pb-fiber" style="background:#b794f4;width:0%"></div></div></div>
            </div>
          </div>
        </div>
        <div class="card">
          <div class="ct">Macros vs Target</div>
          <div style="position:relative;height:185px"><canvas id="macroChart"></canvas></div>
        </div>
      </div>
      <div class="g2" style="margin-top:16px">
        <div class="card">
          <div class="ct">Micronutrient Radar</div>
          <div style="position:relative;height:215px"><canvas id="radarChart"></canvas></div>
        </div>
        <div class="card">
          <div class="ct">Calorie Distribution</div>
          <div style="position:relative;height:215px"><canvas id="mealPieChart"></canvas></div>
        </div>
      </div>
      <div class="g2" style="margin-top:16px">
        <div class="card">
          <div class="ct">Score Breakdown</div>
          <div id="score-breakdown"><p style="font-size:12px;color:var(--txtm);text-align:center;padding:18px 0">Log food to see score breakdown</p></div>
        </div>
        <div class="card">
          <div class="ct">Top Deficiencies</div>
          <div class="del" id="deficiency-list"><div style="font-size:12px;color:var(--txtm);text-align:center;padding:18px 0">Log food to see insights</div></div>
        </div>
      </div>
      <div class="card" style="margin-top:16px">
        <div class="ct">Top Excesses</div>
        <div class="del" id="excess-list"><div style="font-size:12px;color:var(--txtm);text-align:center;padding:18px 0">Log food to see insights</div></div>
      </div>
    </div>
 
    <!-- FOOD LOG -->
    <div class="tp" id="tab-log">
      <div class="card">
        <div class="sh">Today's Food Log</div>
        <div class="ss">Edit quantity inline — changes recalculate instantly.</div>
        <div class="lab">
          <div class="fg" style="margin:0"><label style="margin-bottom:3px">Food</label><select id="log-fs"><option value="">— Choose —</option></select></div>
          <div class="fg" style="margin:0"><label style="margin-bottom:3px">Meal</label>
            <select id="log-meal"><option value="Breakfast">🌅 Breakfast</option><option value="Lunch" selected>☀️ Lunch</option><option value="Dinner">🌙 Dinner</option><option value="Snack">🍎 Snack</option></select>
          </div>
          <div class="fg" style="margin:0"><label style="margin-bottom:3px">Qty</label><input type="number" id="log-qty" placeholder="100" min="1" step="any"></div>
          <div class="fg" style="margin:0"><label style="margin-bottom:3px">Unit</label>
            <select id="log-unit"><option value="g">g</option><option value="ml">ml</option><option value="piece">piece</option><option value="cup">cup</option><option value="tbsp">tbsp</option><option value="katori">katori</option></select>
          </div>
          <button class="btn btn-p" style="align-self:flex-end" onclick="addFood('log')">+ Add</button>
        </div>
        <div id="log-body"></div>
      </div>
    </div>
 
    <!-- NUTRIENTS -->
    <div class="tp" id="tab-nutrients">
      <div class="card">
        <div class="sh">Full Nutrient Breakdown</div>
        <div class="ss">Macros, Micronutrients & Additional Micronutrients vs daily targets</div>
        <div style="overflow-x:auto">
          <table class="nt">
            <thead><tr><th>Nutrient</th><th>Category</th><th>Consumed</th><th>Target</th><th>Progress</th><th>% Goal</th><th>Status</th></tr></thead>
            <tbody id="nutrient-tbody"><tr><td colspan="7" style="text-align:center;padding:28px;color:var(--txtm);font-size:13px">Set profile and log food to see data</td></tr></tbody>
          </table>
        </div>
      </div>
    </div>
 
    <!-- RECOMMENDATIONS -->
    <div class="tp" id="tab-reco">
      <div class="card">
        <div class="sh">Personalised Recommendations</div>
        <div class="ss" id="reco-diet-lbl">Based on your dietary preference, health condition & nutrient gaps</div>
        <div class="rl2" id="reco-list"><div class="re">Log food and set your profile to get recommendations.</div></div>
      </div>
    </div>
 
    <!-- RISK ANALYSIS -->
    <div class="tp" id="tab-risk">
      <div class="card">
        <div class="sh">Nutritional Risk Analysis</div>
        <div class="ss">Identifies potential health risks based on your current intake and profile</div>
        <div class="disclaimer" style="margin-bottom:16px">
          <strong>⚕️ Medical Disclaimer:</strong> Risk analysis is for educational purposes only. These are general population risk indicators, not a clinical diagnosis. Consult a healthcare professional for personalised advice.
        </div>
        <div id="risk-body"><div style="font-size:12px;color:var(--txtm);text-align:center;padding:28px">Set your profile and log food to see risk analysis.</div></div>
      </div>
    </div>
 
    <!-- MEAL PLANNER -->
    <div class="tp" id="tab-planner">
      <div class="card">
        <div class="sh">2-Day Meal Planner</div>
        <div class="ss">Plan meals for 2 days. Totals calculated automatically.</div>
        <div class="planner-grid" id="planner-grid"></div>
      </div>
    </div>
 
    <!-- CSV UPLOAD -->
    <div class="tp" id="tab-upload">
      <div class="card">
        <div class="sh">CSV Upload</div>
        <div class="ss">Upload a CSV to bulk-import food entries. Download the template to get started.</div>
        <div style="margin-bottom:12px;display:flex;gap:9px;flex-wrap:wrap">
          <button class="btn btn-g" onclick="downloadTemplate()">⬇ Download CSV Template</button>
          <button class="btn btn-g" onclick="document.getElementById('csv-file').click()">📁 Choose File</button>
          <input type="file" id="csv-file" accept=".csv" style="display:none" onchange="handleCSV(this)">
        </div>
        <div class="csv-zone" id="csv-zone" ondragover="event.preventDefault();this.classList.add('drag')"
          ondragleave="this.classList.remove('drag')" ondrop="handleDrop(event)">
          <div class="csv-icon">📋</div>
          <div class="csv-lbl">Drag & drop your CSV here</div>
          <div class="csv-sub">or use the button above · Format: food, meal, quantity, unit</div>
        </div>
        <div id="csv-preview"></div>
        <div style="margin-top:14px;background:var(--bg-elevated);border-radius:var(--rmd);padding:12px 14px;font-size:12px;color:var(--txt2)">
          <strong style="color:var(--txt)">Expected CSV columns:</strong> food, meal, quantity, unit<br>
          <strong style="color:var(--txt)">Valid meals:</strong> Breakfast, Lunch, Dinner, Snack<br>
          <strong style="color:var(--txt)">Valid units:</strong> g, ml, piece, cup, tbsp, katori<br>
          <strong style="color:var(--txt)">Food names</strong> must match the database (case-insensitive).
        </div>
      </div>
    </div>
 
    <!-- SOURCES -->
    <div class="tp" id="tab-sources">
      <div class="card">
        <div class="sh">Data Sources & Methodology</div>
        <div class="ss">All nutrient values, RDAs and algorithms used in NutriScope Pro</div>
        <div class="disclaimer" style="margin-bottom:16px">
          <strong>⚕️ Educational Tool Disclaimer:</strong> NutriScope Pro is designed for nutrition awareness and education. It is not a substitute for professional medical or dietetic advice. Individual requirements vary significantly based on health status, medications, genetics, and lifestyle. All calculations use general population averages and reference values.
        </div>
        <div class="src-list">
          <div class="src-item"><div class="src-name">🇮🇳 IFCT 2017 — Indian Food Composition Tables</div><div class="src-desc">Primary source for Indian foods (Rice, Roti, Dal, Paneer, etc.). Published by the National Institute of Nutrition (NIN), Hyderabad, India. Contains nutrient data for 528 Indian food items across 23 nutrient parameters.</div></div>
          <div class="src-item"><div class="src-name">🇺🇸 USDA FoodData Central</div><div class="src-desc">Source for international foods and additional micronutrients (Omega-3, Selenium, Magnesium, Zinc). Available at fdc.nal.usda.gov. Regularly updated with laboratory-analysed values.</div></div>
          <div class="src-item"><div class="src-name">🏥 ICMR Dietary Reference Intakes (2020)</div><div class="src-desc">Recommended Dietary Allowances (RDAs) for the Indian population by the Indian Council of Medical Research. Used for all macro and micronutrient daily targets, adjusted by age, gender and physiological state (pregnancy, lactation).</div></div>
          <div class="src-item"><div class="src-name">🌍 WHO/FAO Joint Expert Consultation</div><div class="src-desc">Used for BMR calculation (Mifflin-St Jeor equation), TDEE multipliers, and international micronutrient upper limits. Reference: FAO/WHO/UNU (2004) — Human Energy Requirements.</div></div>
          <div class="src-item"><div class="src-name">📐 Calculations & Algorithms</div><div class="src-desc"><strong>BMR:</strong> Mifflin-St Jeor equation (±5% accuracy). <strong>TDEE:</strong> BMR × PAL (Physical Activity Level). <strong>Protein target:</strong> 1.2g/kg body weight (moderate activity). <strong>Fat target:</strong> 25% of TDEE. <strong>Carb target:</strong> Remainder of energy budget. <strong>Nutri Score:</strong> Weighted average of % RDA achievement across 14 nutrients (penalises both deficiency and excess).</div></div>
          <div class="src-item"><div class="src-name">⚠️ Limitations</div><div class="src-desc">Nutrient values are averages and actual content varies by cooking method, variety, region, and freshness. Bioavailability (how much the body absorbs) is not modelled — e.g. plant iron (non-haem) absorbs at ~5–12% vs meat iron (haem) at 15–35%. Vitamin D from sunlight is not tracked. Glycaemic Index and glycaemic load are not calculated.</div></div>
        </div>
      </div>
    </div>
 
  </main>
</div>
 
<div class="tw" id="tw"></div>
 
<script>
// ════════════════════════════════════════════════════════════════
// FOOD DATABASE — 60 foods, per 100g
// keys: kcal,prot,carb,fat,fiber,iron,calcium,vitC,vitD,vitB12,
//       magnesium,zinc,potassium,sodium,omega3,selenium,vitA,vitE,vitK,folate
// ════════════════════════════════════════════════════════════════
const DB = {
  // ─ ORIGINAL 20 ─
  "Rice":     {kcal:130,prot:2.7, carb:28.2,fat:0.3, fiber:0.4, iron:0.8, calcium:10,  vitC:0,    vitD:0,    vitB12:0,   mag:12,  zinc:0.5, pot:35,  sod:5,   om3:0,    sel:7.5,  vitA:0,  vitE:0.1, vitK:0,   fol:2   },
  "Roti":     {kcal:297,prot:9.0, carb:57.0,fat:3.7, fiber:4.0, iron:3.9, calcium:34,  vitC:0,    vitD:0,    vitB12:0,   mag:76,  zinc:2.1, pot:215, sod:2,   om3:0.1,  sel:35,   vitA:0,  vitE:1.4, vitK:1.9, fol:40  },
  "Dal":      {kcal:116,prot:8.0, carb:19.5,fat:0.4, fiber:7.9, iron:3.3, calcium:35,  vitC:2,    vitD:0,    vitB12:0,   mag:47,  zinc:1.4, pot:369, sod:6,   om3:0.1,  sel:8,    vitA:2,  vitE:0.1, vitK:5,   fol:181 },
  "Paneer":   {kcal:265,prot:18.3,carb:1.2, fat:20.8,fiber:0,   iron:0.5, calcium:480, vitC:0,    vitD:0.5,  vitB12:0.5, mag:18,  zinc:2.7, pot:84,  sod:400, om3:0.2,  sel:14.5, vitA:110,vitE:0.3, vitK:2.3, fol:7   },
  "Curd":     {kcal:98, prot:3.1, carb:3.4, fat:4.3, fiber:0,   iron:0.1, calcium:121, vitC:0,    vitD:0,    vitB12:0.4, mag:11,  zinc:0.5, pot:141, sod:46,  om3:0.1,  sel:9.7,  vitA:27, vitE:0.1, vitK:0.2, fol:7   },
  "Chana":    {kcal:164,prot:8.9, carb:27.4,fat:2.6, fiber:7.6, iron:2.9, calcium:49,  vitC:1.3,  vitD:0,    vitB12:0,   mag:48,  zinc:1.5, pot:291, sod:24,  om3:0.1,  sel:3.6,  vitA:2,  vitE:0.8, vitK:9,   fol:172 },
  "Rajma":    {kcal:127,prot:8.7, carb:22.8,fat:0.5, fiber:6.4, iron:2.2, calcium:43,  vitC:0,    vitD:0,    vitB12:0,   mag:45,  zinc:1.4, pot:403, sod:2,   om3:0.3,  sel:3.2,  vitA:0,  vitE:0.1, vitK:8.4, fol:130 },
  "Banana":   {kcal:89, prot:1.1, carb:22.8,fat:0.3, fiber:2.6, iron:0.3, calcium:5,   vitC:8.7,  vitD:0,    vitB12:0,   mag:27,  zinc:0.2, pot:358, sod:1,   om3:0.03, sel:1,    vitA:3,  vitE:0.1, vitK:0.5, fol:20  },
  "Apple":    {kcal:52, prot:0.3, carb:13.8,fat:0.2, fiber:2.4, iron:0.1, calcium:6,   vitC:4.6,  vitD:0,    vitB12:0,   mag:5,   zinc:0.04,pot:107, sod:1,   om3:0.01, sel:0,    vitA:3,  vitE:0.2, vitK:2.2, fol:3   },
  "Milk":     {kcal:61, prot:3.2, carb:4.8, fat:3.3, fiber:0,   iron:0.05,calcium:113, vitC:0,    vitD:1.2,  vitB12:0.4, mag:10,  zinc:0.4, pot:132, sod:43,  om3:0.1,  sel:3.7,  vitA:28, vitE:0.1, vitK:0.3, fol:5   },
  "Oats":     {kcal:389,prot:16.9,carb:66.3,fat:6.9, fiber:10.6,iron:4.7, calcium:54,  vitC:0,    vitD:0,    vitB12:0,   mag:177, zinc:3.9, pot:429, sod:2,   om3:0.1,  sel:28,   vitA:0,  vitE:1.4, vitK:2,   fol:56  },
  "Bread":    {kcal:265,prot:9.0, carb:49.0,fat:3.2, fiber:2.7, iron:3.5, calcium:260, vitC:0,    vitD:0,    vitB12:0,   mag:23,  zinc:0.7, pot:115, sod:681, om3:0.1,  sel:24,   vitA:0,  vitE:0.2, vitK:7.8, fol:86  },
  "Egg":      {kcal:155,prot:12.6,carb:1.1, fat:10.6,fiber:0,   iron:1.8, calcium:50,  vitC:0,    vitD:2.0,  vitB12:1.1, mag:10,  zinc:1.3, pot:126, sod:124, om3:0.1,  sel:30.7, vitA:149,vitE:1.0, vitK:0.3, fol:47  },
  "Chicken":  {kcal:165,prot:31.0,carb:0,   fat:3.6, fiber:0,   iron:1.0, calcium:15,  vitC:0,    vitD:0.1,  vitB12:0.3, mag:27,  zinc:1.0, pot:256, sod:74,  om3:0.07, sel:27.6, vitA:9,  vitE:0.3, vitK:0,   fol:4   },
  "Fish":     {kcal:136,prot:20.0,carb:0,   fat:6.0, fiber:0,   iron:0.9, calcium:12,  vitC:0,    vitD:11.0, vitB12:3.0, mag:26,  zinc:0.5, pot:397, sod:61,  om3:1.5,  sel:36.5, vitA:15, vitE:0.5, vitK:0.1, fol:7   },
  "Potato":   {kcal:77, prot:2.0, carb:17.0,fat:0.1, fiber:2.2, iron:0.8, calcium:12,  vitC:19.7, vitD:0,    vitB12:0,   mag:23,  zinc:0.3, pot:421, sod:6,   om3:0.01, sel:0.4,  vitA:2,  vitE:0.1, vitK:1.8, fol:15  },
  "Poha":     {kcal:376,prot:6.9, carb:82.0,fat:1.0, fiber:0.2, iron:20.0,calcium:14,  vitC:0,    vitD:0,    vitB12:0,   mag:76,  zinc:1.2, pot:180, sod:5,   om3:0,    sel:15,   vitA:0,  vitE:0.1, vitK:0,   fol:8   },
  "Idli":     {kcal:39, prot:2.0, carb:7.9, fat:0.2, fiber:0.5, iron:0.5, calcium:20,  vitC:0,    vitD:0,    vitB12:0,   mag:12,  zinc:0.3, pot:55,  sod:250, om3:0,    sel:5,    vitA:0,  vitE:0,   vitK:0.1, fol:18  },
  "Dosa":     {kcal:168,prot:3.9, carb:31.6,fat:3.7, fiber:1.0, iron:1.1, calcium:25,  vitC:0,    vitD:0,    vitB12:0,   mag:20,  zinc:0.5, pot:90,  sod:390, om3:0.1,  sel:10,   vitA:0,  vitE:0.2, vitK:1,   fol:22  },
  "Spinach":  {kcal:23, prot:2.9, carb:3.6, fat:0.4, fiber:2.2, iron:2.7, calcium:99,  vitC:28.1, vitD:0,    vitB12:0,   mag:79,  zinc:0.5, pot:558, sod:79,  om3:0.14, sel:1,    vitA:469,vitE:2.0, vitK:483, fol:194 },
  // ─ 40 NEW FOODS ─
  "Brown Rice":{kcal:216,prot:4.5, carb:45.0,fat:1.8, fiber:3.5, iron:1.0, calcium:10,  vitC:0,    vitD:0,    vitB12:0,   mag:84,  zinc:1.2, pot:154, sod:5,   om3:0.02, sel:9.8,  vitA:0,  vitE:0.3, vitK:1.9, fol:9   },
  "Quinoa":   {kcal:120,prot:4.4, carb:21.3,fat:1.9, fiber:2.8, iron:1.5, calcium:17,  vitC:0,    vitD:0,    vitB12:0,   mag:64,  zinc:1.1, pot:172, sod:7,   om3:0.1,  sel:2.8,  vitA:0,  vitE:0.6, vitK:0,   fol:42  },
  "Moong Dal":{kcal:105,prot:7.0, carb:19.1,fat:0.4, fiber:7.0, iron:1.8, calcium:27,  vitC:2.4,  vitD:0,    vitB12:0,   mag:48,  zinc:0.8, pot:326, sod:15,  om3:0.1,  sel:2.5,  vitA:2,  vitE:0.4, vitK:9,   fol:159 },
  "Urad Dal": {kcal:347,prot:25.2,carb:59.6,fat:1.6, fiber:18.3,iron:7.6, calcium:138, vitC:0,    vitD:0,    vitB12:0,   mag:267, zinc:3.3, pot:983, sod:38,  om3:0.2,  sel:5,    vitA:0,  vitE:0.2, vitK:5,   fol:216 },
  "Soya Chunks":{kcal:336,prot:52.4,carb:33.5,fat:0.5,fiber:13.0,iron:9.0,calcium:350, vitC:0,    vitD:0,    vitB12:0,   mag:280, zinc:3.9, pot:2080,sod:4,   om3:0.3,  sel:7.2,  vitA:0,  vitE:0.5, vitK:34,  fol:0   },
  "Tofu":     {kcal:76, prot:8.0, carb:1.9, fat:4.8, fiber:0.3, iron:1.6, calcium:350, vitC:0.1,  vitD:0,    vitB12:0,   mag:30,  zinc:0.8, pot:121, sod:7,   om3:0.4,  sel:8.9,  vitA:5,  vitE:0.1, vitK:2.4, fol:19  },
  "Peanuts":  {kcal:567,prot:25.8,carb:16.1,fat:49.2,fiber:8.5, iron:4.6, calcium:92,  vitC:0,    vitD:0,    vitB12:0,   mag:168, zinc:3.3, pot:705, sod:18,  om3:0.003,sel:7.2,  vitA:0,  vitE:8.3, vitK:0,   fol:246 },
  "Almonds":  {kcal:579,prot:21.2,carb:21.7,fat:49.9,fiber:12.5,iron:3.7, calcium:264, vitC:0,    vitD:0,    vitB12:0,   mag:270, zinc:3.1, pot:733, sod:1,   om3:0.004,sel:4.1,  vitA:0,  vitE:25.6,vitK:0,   fol:44  },
  "Walnuts":  {kcal:654,prot:15.2,carb:13.7,fat:65.2,fiber:6.7, iron:2.9, calcium:98,  vitC:1.3,  vitD:0,    vitB12:0,   mag:158, zinc:3.1, pot:441, sod:2,   om3:9.1,  sel:4.9,  vitA:1,  vitE:0.7, vitK:2.7, fol:98  },
  "Flaxseeds":{kcal:534,prot:18.3,carb:28.9,fat:42.2,fiber:27.3,iron:5.7, calcium:255, vitC:0.6,  vitD:0,    vitB12:0,   mag:392, zinc:4.3, pot:813, sod:30,  om3:22.8, sel:25.4, vitA:0,  vitE:0.3, vitK:4.3, fol:87  },
  "Chia Seeds":{kcal:486,prot:16.5,carb:42.1,fat:30.7,fiber:34.4,iron:7.7,calcium:631, vitC:1.6,  vitD:0,    vitB12:0,   mag:335, zinc:4.6, pot:407, sod:16,  om3:17.8, sel:55.2, vitA:2,  vitE:0.5, vitK:0,   fol:49  },
  "Sweet Potato":{kcal:86,prot:1.6,carb:20.1,fat:0.1,fiber:3.0, iron:0.6, calcium:30,  vitC:2.4,  vitD:0,    vitB12:0,   mag:25,  zinc:0.3, pot:337, sod:55,  om3:0.01, sel:0.6,  vitA:709,vitE:0.3, vitK:1.8, fol:11  },
  "Broccoli": {kcal:34, prot:2.8, carb:6.6, fat:0.4, fiber:2.6, iron:0.7, calcium:47,  vitC:89.2, vitD:0,    vitB12:0,   mag:21,  zinc:0.4, pot:316, sod:33,  om3:0.1,  sel:2.5,  vitA:31, vitE:0.8, vitK:101, fol:63  },
  "Carrot":   {kcal:41, prot:0.9, carb:9.6, fat:0.2, fiber:2.8, iron:0.3, calcium:33,  vitC:5.9,  vitD:0,    vitB12:0,   mag:12,  zinc:0.2, pot:320, sod:69,  om3:0.01, sel:0.1,  vitA:835,vitE:0.7, vitK:13.2,fol:19  },
  "Tomato":   {kcal:18, prot:0.9, carb:3.9, fat:0.2, fiber:1.2, iron:0.3, calcium:10,  vitC:13.7, vitD:0,    vitB12:0,   mag:11,  zinc:0.2, pot:237, sod:5,   om3:0,    sel:0,    vitA:42, vitE:0.5, vitK:7.9, fol:15  },
  "Onion":    {kcal:40, prot:1.1, carb:9.3, fat:0.1, fiber:1.7, iron:0.2, calcium:23,  vitC:7.4,  vitD:0,    vitB12:0,   mag:10,  zinc:0.2, pot:146, sod:4,   om3:0,    sel:0.5,  vitA:0,  vitE:0.02,vitK:0.4, fol:19  },
  "Garlic":   {kcal:149,prot:6.4, carb:33.1,fat:0.5, fiber:2.1, iron:1.7, calcium:181, vitC:31.2, vitD:0,    vitB12:0,   mag:25,  zinc:1.2, pot:401, sod:17,  om3:0.01, sel:14.2, vitA:0,  vitE:0.08,vitK:1.7, fol:3   },
  "Amla":     {kcal:44, prot:0.9, carb:10.2,fat:0.6, fiber:4.3, iron:0.7, calcium:50,  vitC:600,  vitD:0,    vitB12:0,   mag:10,  zinc:0.1, pot:198, sod:1,   om3:0.03, sel:0,    vitA:3,  vitE:0.4, vitK:0,   fol:6   },
  "Orange":   {kcal:47, prot:0.9, carb:11.8,fat:0.1, fiber:2.4, iron:0.1, calcium:40,  vitC:53.2, vitD:0,    vitB12:0,   mag:10,  zinc:0.1, pot:181, sod:0,   om3:0.01, sel:0.5,  vitA:11, vitE:0.2, vitK:0,   fol:30  },
  "Papaya":   {kcal:43, prot:0.5, carb:10.8,fat:0.3, fiber:1.7, iron:0.3, calcium:20,  vitC:60.9, vitD:0,    vitB12:0,   mag:21,  zinc:0.1, pot:182, sod:8,   om3:0.01, sel:0.6,  vitA:47, vitE:0.3, vitK:2.6, fol:37  },
  "Mango":    {kcal:60, prot:0.8, carb:15.0,fat:0.4, fiber:1.6, iron:0.2, calcium:11,  vitC:36.4, vitD:0,    vitB12:0,   mag:10,  zinc:0.1, pot:168, sod:1,   om3:0.02, sel:0.6,  vitA:54, vitE:0.9, vitK:4.2, fol:43  },
  "Guava":    {kcal:68, prot:2.6, carb:14.3,fat:1.0, fiber:5.4, iron:0.3, calcium:18,  vitC:228.3,vitD:0,    vitB12:0,   mag:22,  zinc:0.2, pot:417, sod:2,   om3:0.09, sel:0.6,  vitA:31, vitE:0.73,vitK:2.6, fol:49  },
  "Coconut Milk":{kcal:197,prot:2.3,carb:2.8,fat:21.3,fiber:2.2,iron:3.3,calcium:16, vitC:2.8,  vitD:0,    vitB12:0,   mag:37,  zinc:0.7, pot:263, sod:13,  om3:0.01, sel:8.3,  vitA:0,  vitE:0.2, vitK:0,   fol:16  },
  "Ghee":     {kcal:900,prot:0,   carb:0,   fat:99.8,fiber:0,   iron:0,   calcium:4,   vitC:0,    vitD:1.5,  vitB12:0,   mag:0,   zinc:0,   pot:5,   sod:2,   om3:0.5,  sel:0,    vitA:300,vitE:2.4, vitK:8.5, fol:0   },
  "Mustard Oil":{kcal:884,prot:0, carb:0,   fat:100, fiber:0,   iron:0,   calcium:0,   vitC:0,    vitD:0,    vitB12:0,   mag:0,   zinc:0,   pot:0,   sod:0,   om3:5.9,  sel:0,    vitA:0,  vitE:10.1,vitK:0,   fol:0   },
  "Salmon":   {kcal:208,prot:20.4,carb:0,   fat:13.4,fiber:0,   iron:0.3, calcium:9,   vitC:3.9,  vitD:11.1, vitB12:3.2, mag:27,  zinc:0.6, pot:363, sod:59,  om3:2.6,  sel:36.5, vitA:12, vitE:3.6, vitK:0.5, fol:25  },
  "Prawns":   {kcal:99, prot:20.1,carb:0.9, fat:1.7, fiber:0,   iron:1.8, calcium:64,  vitC:0,    vitD:0.4,  vitB12:1.1, mag:34,  zinc:1.1, pot:182, sod:111, om3:0.5,  sel:38,   vitA:54, vitE:1.3, vitK:0.1, fol:2   },
  "Mutton":   {kcal:294,prot:25.6,carb:0,   fat:21.0,fiber:0,   iron:2.7, calcium:17,  vitC:0,    vitD:0.5,  vitB12:2.4, mag:22,  zinc:4.8, pot:318, sod:72,  om3:0.3,  sel:14,   vitA:0,  vitE:0.4, vitK:0,   fol:8   },
  "Toor Dal": {kcal:340,prot:22.3,carb:57.6,fat:1.7, fiber:15.0,iron:7.6, calcium:73,  vitC:0,    vitD:0,    vitB12:0,   mag:103, zinc:3.0, pot:1076,sod:19,  om3:0.2,  sel:3,    vitA:5,  vitE:0.4, vitK:5,   fol:456 },
  "Peas":     {kcal:81, prot:5.4, carb:14.5,fat:0.4, fiber:5.1, iron:1.5, calcium:25,  vitC:40.0, vitD:0,    vitB12:0,   mag:33,  zinc:1.2, pot:244, sod:5,   om3:0.04, sel:1.8,  vitA:38, vitE:0.1, vitK:24.8,fol:65  },
  "Corn":     {kcal:86, prot:3.3, carb:19.0,fat:1.4, fiber:2.7, iron:0.5, calcium:2,   vitC:6.8,  vitD:0,    vitB12:0,   mag:37,  zinc:0.5, pot:270, sod:15,  om3:0.03, sel:0.6,  vitA:9,  vitE:0.1, vitK:0.3, fol:42  },
  "Beetroot": {kcal:43, prot:1.6, carb:9.6, fat:0.2, fiber:2.8, iron:0.8, calcium:16,  vitC:4.9,  vitD:0,    vitB12:0,   mag:23,  zinc:0.4, pot:325, sod:78,  om3:0.01, sel:0.7,  vitA:2,  vitE:0.04,vitK:0.2, fol:109 },
  "Mushroom": {kcal:22, prot:3.1, carb:3.3, fat:0.3, fiber:1.0, iron:0.5, calcium:3,   vitC:2.1,  vitD:7.0,  vitB12:0,   mag:9,   zinc:0.5, pot:318, sod:5,   om3:0.02, sel:9.3,  vitA:0,  vitE:0.01,vitK:0,   fol:17  },
  "Bottle Gourd":{kcal:14,prot:0.6,carb:3.4,fat:0.1, fiber:0.5, iron:0.2, calcium:26,  vitC:10.1, vitD:0,    vitB12:0,   mag:11,  zinc:0.1, pot:150, sod:2,   om3:0,    sel:0.2,  vitA:2,  vitE:0,   vitK:0,   fol:6   },
  "Bitter Gourd":{kcal:17,prot:1.0,carb:3.7,fat:0.2, fiber:2.8, iron:0.6, calcium:20,  vitC:84,   vitD:0,    vitB12:0,   mag:17,  zinc:0.8, pot:296, sod:5,   om3:0.05, sel:0.2,  vitA:24, vitE:0.1, vitK:4.8, fol:72  },
  "Drumstick":{kcal:37, prot:2.5, carb:8.3, fat:0.2, fiber:2.0, iron:0.4, calcium:185, vitC:141,  vitD:0,    vitB12:0,   mag:45,  zinc:0.4, pot:461, sod:42,  om3:0.04, sel:0.9,  vitA:135,vitE:0.9, vitK:0,   fol:44  },
  "Dates":    {kcal:282,prot:2.5, carb:75.0,fat:0.4, fiber:8.0, iron:1.0, calcium:39,  vitC:0,    vitD:0,    vitB12:0,   mag:43,  zinc:0.4, pot:656, sod:2,   om3:0.01, sel:3,    vitA:7,  vitE:0.05,vitK:2.7, fol:15  },
  "Coconut":  {kcal:354,prot:3.3, carb:15.2,fat:33.5,fiber:9.0, iron:2.4, calcium:14,  vitC:3.3,  vitD:0,    vitB12:0,   mag:32,  zinc:1.1, pot:356, sod:20,  om3:0,    sel:10.1, vitA:0,  vitE:0.2, vitK:0.2, fol:26  },
  "Groundnut Oil":{kcal:884,prot:0,carb:0,  fat:100, fiber:0,   iron:0,   calcium:0,   vitC:0,    vitD:0,    vitB12:0,   mag:0,   zinc:0,   pot:0,   sod:0,   om3:0.3,  sel:0,    vitA:0,  vitE:15.7,vitK:0.7, fol:0   },
  "Jaggery":  {kcal:383,prot:0.4, carb:98.0,fat:0.1, fiber:0,   iron:11.0,calcium:80,  vitC:7.4,  vitD:0,    vitB12:0,   mag:70,  zinc:0.3, pot:1056,sod:19,  om3:0,    sel:1.2,  vitA:0,  vitE:0,   vitK:0,   fol:0   },
  "Buttermilk":{kcal:40, prot:3.3, carb:4.8, fat:0.9, fiber:0,   iron:0.07,calcium:116, vitC:0,    vitD:0,    vitB12:0.2, mag:10,  zinc:0.4, pot:151, sod:105, om3:0.04, sel:4.1,  vitA:7,  vitE:0.02,vitK:0.1, fol:5   },
  "Sambar":   {kcal:45, prot:2.9, carb:7.3, fat:0.9, fiber:2.1, iron:1.2, calcium:32,  vitC:8.0,  vitD:0,    vitB12:0,   mag:22,  zinc:0.4, pot:220, sod:320, om3:0.1,  sel:3,    vitA:60, vitE:0.3, vitK:12,  fol:50  },
  "Upma":     {kcal:130,prot:3.6, carb:24.0,fat:3.2, fiber:1.8, iron:1.8, calcium:14,  vitC:1.0,  vitD:0,    vitB12:0,   mag:38,  zinc:0.6, pot:130, sod:380, om3:0.05, sel:12,   vitA:5,  vitE:0.3, vitK:3,   fol:30  },
  "Khichdi":  {kcal:110,prot:5.2, carb:19.8,fat:2.1, fiber:2.5, iron:1.6, calcium:28,  vitC:0,    vitD:0,    vitB12:0,   mag:40,  zinc:0.9, pot:200, sod:280, om3:0.05, sel:6,    vitA:3,  vitE:0.2, vitK:4,   fol:55  },
  "Pumpkin":  {kcal:26, prot:1.0, carb:6.5, fat:0.1, fiber:0.5, iron:0.8, calcium:21,  vitC:9.0,  vitD:0,    vitB12:0,   mag:12,  zinc:0.3, pot:340, sod:1,   om3:0.01, sel:0.3,  vitA:426,vitE:1.1, vitK:1.1, fol:16  },
  "Cauliflower":{kcal:25,prot:1.9, carb:5.0, fat:0.3, fiber:2.0, iron:0.4, calcium:22,  vitC:48.2, vitD:0,    vitB12:0,   mag:15,  zinc:0.3, pot:299, sod:30,  om3:0.03, sel:0.6,  vitA:0,  vitE:0.1, vitK:15.5,fol:57  },
};
 
const UNIT_G = {g:1,ml:1,piece:100,cup:240,tbsp:15,katori:150};
const MEALS = ['Breakfast','Lunch','Dinner','Snack'];
const MEAL_IC = {Breakfast:'🌅',Lunch:'☀️',Dinner:'🌙',Snack:'🍎'};
 
// Nutrient metadata
const NUTMETA = [
  // Macros
  {k:'kcal', n:'Calories',      cat:'Macronutrient', u:'kcal'},
  {k:'prot', n:'Protein',       cat:'Macronutrient', u:'g'},
  {k:'carb', n:'Carbohydrates', cat:'Macronutrient', u:'g'},
  {k:'fat',  n:'Fat',           cat:'Macronutrient', u:'g'},
  {k:'fiber',n:'Dietary Fiber', cat:'Macronutrient', u:'g'},
  // Core Micros
  {k:'iron',    n:'Iron',      cat:'Mineral', u:'mg'},
  {k:'calcium', n:'Calcium',   cat:'Mineral', u:'mg'},
  {k:'vitC',    n:'Vitamin C', cat:'Vitamin', u:'mg'},
  {k:'vitD',    n:'Vitamin D', cat:'Vitamin', u:'mcg'},
  {k:'vitB12',  n:'Vitamin B12',cat:'Vitamin',u:'mcg'},
  // Additional Micros
  {k:'mag',  n:'Magnesium',  cat:'Mineral', u:'mg'},
  {k:'zinc', n:'Zinc',       cat:'Mineral', u:'mg'},
  {k:'pot',  n:'Potassium',  cat:'Mineral', u:'mg'},
  {k:'sod',  n:'Sodium',     cat:'Mineral', u:'mg'},
  {k:'om3',  n:'Omega-3',    cat:'Fatty Acid',u:'g'},
  {k:'sel',  n:'Selenium',   cat:'Mineral', u:'mcg'},
  {k:'vitA', n:'Vitamin A',  cat:'Vitamin', u:'mcg RAE'},
  {k:'vitE', n:'Vitamin E',  cat:'Vitamin', u:'mg'},
  {k:'vitK', n:'Vitamin K',  cat:'Vitamin', u:'mcg'},
  {k:'fol',  n:'Folate',     cat:'Vitamin', u:'mcg'},
];
 
// ── STATE ─────────────────────────────────────────────────────
let profile={age:null,gender:'male',height:null,weight:null,activity:1.55,diet:'nonveg',health:'none'};
let targets=null;
let foodLog=[];
let planner={day1:{Breakfast:[],Lunch:[],Dinner:[],Snack:[]},day2:{Breakfast:[],Lunch:[],Dinner:[],Snack:[]}};
let charts={};
 
// ── INIT ──────────────────────────────────────────────────────
(function init(){
  const names = Object.keys(DB).sort();
  ['food-select','log-fs','plan-food-day1','plan-food-day2'].forEach(id=>{
    const el=document.getElementById(id);
    if(!el)return;
    names.forEach(n=>{const o=document.createElement('option');o.value=n;o.textContent=n;el.appendChild(o);});
  });
  initCharts();
  initPlanner();
  loadState();
  renderAll();
})();
 
function closeDisclaimer(){document.getElementById('disclaimer-modal').classList.remove('open');}
 
// ── PERSISTENCE ───────────────────────────────────────────────
function saveState(){
  try{
    sessionStorage.setItem('ns2_p',JSON.stringify(profile));
    sessionStorage.setItem('ns2_t',JSON.stringify(targets));
    sessionStorage.setItem('ns2_l',JSON.stringify(foodLog));
    sessionStorage.setItem('ns2_pl',JSON.stringify(planner));
  }catch(e){}
}
function loadState(){
  try{
    const p=sessionStorage.getItem('ns2_p');const t=sessionStorage.getItem('ns2_t');
    const l=sessionStorage.getItem('ns2_l');const pl=sessionStorage.getItem('ns2_pl');
    if(p)profile=JSON.parse(p);
    if(t)targets=JSON.parse(t);
    if(l)foodLog=JSON.parse(l);
    if(pl)planner=JSON.parse(pl);
    if(profile.age){
      ['age','gender','height','weight','activity','diet','health'].forEach(k=>{
        const el=document.getElementById(k);if(el&&profile[k])el.value=profile[k];
      });
    }
  }catch(e){}
}
 
// ── CHARTS ────────────────────────────────────────────────────
function initCharts(){
  const eCtx=document.getElementById('energyRing').getContext('2d');
  charts.energy=new Chart(eCtx,{type:'doughnut',
    data:{datasets:[{data:[0,100],backgroundColor:['rgba(99,179,237,.9)','rgba(255,255,255,.04)'],borderWidth:0,borderRadius:4}]},
    options:{cutout:'76%',responsive:true,maintainAspectRatio:false,plugins:{legend:{display:false},tooltip:{enabled:false}},animation:{duration:700}}
  });
 
  const mCtx=document.getElementById('macroChart').getContext('2d');
  charts.macro=new Chart(mCtx,{type:'bar',
    data:{labels:['Protein','Carbs','Fat','Fiber'],
      datasets:[
        {label:'Consumed',data:[0,0,0,0],backgroundColor:['rgba(99,179,237,.85)','rgba(246,173,85,.85)','rgba(104,211,145,.85)','rgba(183,148,244,.85)'],borderRadius:5,borderSkipped:false},
        {label:'Target',  data:[0,0,0,0],backgroundColor:['rgba(99,179,237,.12)','rgba(246,173,85,.12)','rgba(104,211,145,.12)','rgba(183,148,244,.12)'],borderRadius:5,borderSkipped:false}
      ]
    },
    options:{responsive:true,maintainAspectRatio:false,
      plugins:{legend:{display:true,labels:{color:'#8892a4',font:{size:11},boxWidth:12,padding:14}},
        tooltip:{callbacks:{label:c=>` ${c.dataset.label}: ${c.parsed.y}g`}}},
      scales:{x:{grid:{color:'rgba(255,255,255,.04)'},ticks:{color:'#8892a4',font:{size:11}}},
              y:{grid:{color:'rgba(255,255,255,.04)'},ticks:{color:'#8892a4',font:{size:11}}}},
      animation:{duration:600}}
  });
 
  const rCtx=document.getElementById('radarChart').getContext('2d');
  charts.radar=new Chart(rCtx,{type:'radar',
    data:{labels:['Iron','Calcium','Vit C','Vit D','Vit B12','Magnesium','Zinc','Folate'],
      datasets:[
        {label:'% of Target',data:[0,0,0,0,0,0,0,0],
          backgroundColor:'rgba(99,179,237,.1)',borderColor:'rgba(99,179,237,.8)',
          pointBackgroundColor:'rgba(99,179,237,1)',pointRadius:4,fill:true,tension:.3},
        {label:'100% Goal',data:[100,100,100,100,100,100,100,100],
          backgroundColor:'rgba(255,255,255,.02)',borderColor:'rgba(255,255,255,.1)',
          pointRadius:0,borderDash:[3,3],fill:true}
      ]
    },
    options:{responsive:true,maintainAspectRatio:false,
      plugins:{legend:{display:true,labels:{color:'#8892a4',font:{size:11},boxWidth:12}},
        tooltip:{callbacks:{label:c=>` ${c.dataset.label}: ${Math.round(c.parsed.r)}%`}}},
      scales:{r:{min:0,max:150,grid:{color:'rgba(255,255,255,.06)'},angleLines:{color:'rgba(255,255,255,.06)'},
        pointLabels:{color:'#8892a4',font:{size:11}},ticks:{display:false,stepSize:50}}},
      animation:{duration:700}}
  });
 
  const pCtx=document.getElementById('mealPieChart').getContext('2d');
  charts.meal=new Chart(pCtx,{type:'doughnut',
    data:{labels:['Breakfast','Lunch','Dinner','Snack'],
      datasets:[{data:[0,0,0,0],backgroundColor:['rgba(99,179,237,.85)','rgba(104,211,145,.85)','rgba(183,148,244,.85)','rgba(246,173,85,.85)'],borderWidth:0,borderRadius:3}]
    },
    options:{responsive:true,maintainAspectRatio:false,cutout:'60%',
      plugins:{legend:{display:true,position:'right',labels:{color:'#8892a4',font:{size:11},boxWidth:10,padding:12}},
        tooltip:{callbacks:{label:c=>` ${c.label}: ${c.parsed.toFixed(0)} kcal`}}},
      animation:{duration:700}}
  });
}
 
// ── PROFILE ───────────────────────────────────────────────────
function applyProfile(){
  const age=+document.getElementById('age').value;
  const gender=document.getElementById('gender').value;
  const ht=+document.getElementById('height').value;
  const wt=+document.getElementById('weight').value;
  const act=+document.getElementById('activity').value;
  const diet=document.getElementById('diet').value;
  const health=document.getElementById('health').value;
  if(!age||!ht||!wt){toast('Fill Age, Height and Weight first.');return;}
  profile={age,gender,height:ht,weight:wt,activity:act,diet,health};
 
  let bmr=gender==='male'?10*wt+6.25*ht-5*age+5:10*wt+6.25*ht-5*age-161;
  const tdee=Math.round(bmr*act);
  const bmi=+(wt/((ht/100)**2)).toFixed(1);
 
  let protT=Math.round(wt*1.2);
  const fatT=Math.round(tdee*.25/9);
  const carbT=Math.round((tdee-protT*4-fatT*9)/4);
  let fiberT=gender==='male'?38:25;
  let ironT=gender==='female'&&age<50?18:8;
  let calcT=age>50?1200:1000;
  let vitCT=gender==='male'?90:75;
  let vitDT=age>70?20:15;
 
  // Health condition adjustments
  if(health==='pregnancy'){protT=Math.round(wt*1.5);ironT=27;calcT=1300;vitCT=85;fiberT=28;}
  else if(health==='lactation'){protT=Math.round(wt*1.4);calcT=1300;vitCT=120;}
  else if(health==='osteoporosis'){calcT=1500;vitDT=20;}
  else if(health==='anemia'){ironT=gender==='female'?27:18;}
  else if(health==='diabetes'){fiberT=38;}
 
  targets={
    kcal:tdee,prot:protT,carb:carbT,fat:fatT,fiber:fiberT,
    iron:ironT,calcium:calcT,vitC:vitCT,vitD:vitDT,vitB12:2.4,
    mag:gender==='male'?420:320,zinc:gender==='male'?11:8,
    pot:3400,sod:2300,om3:1.6,sel:55,
    vitA:gender==='male'?900:700,vitE:15,vitK:gender==='male'?120:90,fol:400
  };
  if(health==='pregnancy')targets.fol=600;
 
  let bmiCat='',bmiCls='';
  if(bmi<18.5){bmiCat='Underweight';bmiCls='bad';}
  else if(bmi<25){bmiCat='Normal';bmiCls='good';}
  else if(bmi<30){bmiCat='Overweight';bmiCls='warn';}
  else{bmiCat='Obese';bmiCls='bad';}
  document.getElementById('pill-bmi').className='sp '+bmiCls;
  document.getElementById('bmi-val').textContent=bmi;
  document.getElementById('bmi-cat').textContent=bmiCat;
  document.getElementById('bmr-val').textContent=Math.round(bmr);
  document.getElementById('tdee-val').textContent=tdee;
  document.getElementById('reco-diet-lbl').textContent=`Recommendations for ${diet==='veg'?'Vegetarian':diet==='nonveg'?'Non-Vegetarian':diet==='egg'?'Eggetarian':'Vegan'} · ${health!=='none'?health:'Healthy'}`;
 
  const tRows=[['Calories',tdee+' kcal'],['Protein',protT+' g'],['Carbs',carbT+' g'],['Fat',fatT+' g'],
    ['Fiber',fiberT+' g'],['Iron',ironT+' mg'],['Calcium',calcT+' mg'],['Vit C',vitCT+' mg'],
    ['Vit D',vitDT+' mcg'],['B12','2.4 mcg'],['Magnesium',targets.mag+' mg'],['Zinc',targets.zinc+' mg'],
    ['Potassium',targets.pot+' mg'],['Sodium','<'+targets.sod+' mg'],['Omega-3',targets.om3+' g'],
    ['Folate','400 mcg']];
  document.getElementById('targets-display').innerHTML=`<div class="tg">${tRows.map(([l,v])=>`<div class="tc"><div class="tcl">${l}</div><div class="tcv">${v}</div></div>`).join('')}</div>`;
  saveState();renderAll();toast('Profile applied ✓');
}
 
// ── ADD FOOD ──────────────────────────────────────────────────
function addFood(src){
  const isLog=src==='log';
  const nameEl=isLog?'log-fs':'food-select';
  const mealEl=isLog?'log-meal':'sb-meal';
  const qtyEl=isLog?'log-qty':'food-qty';
  const unitEl=isLog?'log-unit':'food-unit';
  const name=document.getElementById(nameEl).value;
  const meal=document.getElementById(mealEl).value;
  const qty=+document.getElementById(qtyEl).value;
  const unit=document.getElementById(unitEl).value;
  if(!name){toast('Select a food item.');return;}
  if(!qty||qty<=0){toast('Enter a valid quantity.');return;}
  const grams=qty*UNIT_G[unit];
  const e=calcEntry(name,meal,qty,unit,grams);
  foodLog.push(e);
  document.getElementById(qtyEl).value='';
  saveState();renderAll();toast(`${name} (${qty} ${unit}) added ✓`);
}
 
function calcEntry(name,meal,qty,unit,grams){
  const f=DB[name];const s=grams/100;
  const nut={};
  NUTMETA.forEach(m=>{nut[m.k]=+(f[m.k]*s).toFixed(3);});
  return{id:Date.now()+Math.random(),name,meal,qty,unit,grams,nut};
}
 
function removeFood(id){foodLog=foodLog.filter(e=>e.id!==id);saveState();renderAll();}
function updateQty(id,v){
  const e=foodLog.find(x=>x.id===id);if(!e||!v||v<=0)return;
  e.qty=+v;e.grams=e.qty*UNIT_G[e.unit];
  const ent=calcEntry(e.name,e.meal,e.qty,e.unit,e.grams);
  e.nut=ent.nut;
  saveState();renderAll();
}
function clearLog(){if(!foodLog.length){toast('Log already empty.');return;}foodLog=[];saveState();renderAll();toast('Log cleared.');}
 
function getTotals(log){
  const base={};NUTMETA.forEach(m=>base[m.k]=0);
  return (log||foodLog).reduce((a,e)=>{NUTMETA.forEach(m=>a[m.k]=(a[m.k]||0)+e.nut[m.k]);return a;},base);
}
 
// ── NUTRI SCORE ───────────────────────────────────────────────
function calcScore(totals){
  if(!targets||!foodLog.length)return null;
  let tot=0;const details=[];
  NUTMETA.forEach(m=>{
    if(!targets[m.k])return;
    let pct=Math.min((totals[m.k]/targets[m.k])*100,200);
    let sc=pct<=100?Math.max(0,pct<=50?pct*1.5:75+(pct-50)*0.5):Math.max(0,100-(pct-100)*1.5);
    sc=Math.min(100,Math.max(0,sc));
    tot+=sc;details.push({key:m.k,name:m.n,pct:Math.round(pct),score:Math.round(sc)});
  });
  return{overall:Math.round(tot/details.length),details};
}
 
// ── RENDER ALL ────────────────────────────────────────────────
function renderAll(){
  const totals=getTotals();
  renderLog();renderDashboard(totals);renderNutrients(totals);renderReco(totals);renderRisk(totals);renderPlanner();
}
 
// ── LOG ───────────────────────────────────────────────────────
function renderLog(){
  const c=document.getElementById('log-body');
  if(!foodLog.length){c.innerHTML=`<div class="es"><span class="ei">🍽️</span>Nothing logged yet.</div>`;return;}
  const grouped={};MEALS.forEach(m=>grouped[m]=[]);
  foodLog.forEach(e=>{(grouped[e.meal]=grouped[e.meal]||[]).push(e);});
  let h='';
  MEALS.forEach(meal=>{
    const items=grouped[meal];if(!items.length)return;
    const mk=items.reduce((s,e)=>s+e.nut.kcal,0);
    h+=`<div class="ls"><div class="mgh">${MEAL_IC[meal]} ${meal}<span class="mkb">${mk.toFixed(0)} kcal</span></div>
    <div class="ftw"><table><thead><tr><th>Food</th><th>Qty</th><th>Unit</th><th>kcal</th><th>Prot</th><th>Carbs</th><th>Fat</th><th>Fiber</th><th>Iron</th><th></th></tr></thead><tbody>
    ${items.map(e=>`<tr>
      <td><strong>${e.name}</strong></td>
      <td><input class="eq" type="number" value="${e.qty}" min="1" step="any" onchange="updateQty(${e.id},this.value)"></td>
      <td class="dim">${e.unit}</td>
      <td>${e.nut.kcal.toFixed(1)}</td>
      <td class="dim">${e.nut.prot.toFixed(1)}g</td>
      <td class="dim">${e.nut.carb.toFixed(1)}g</td>
      <td class="dim">${e.nut.fat.toFixed(1)}g</td>
      <td class="dim">${e.nut.fiber.toFixed(1)}g</td>
      <td class="dim">${e.nut.iron.toFixed(2)}mg</td>
      <td><button class="btn btn-d" onclick="removeFood(${e.id})">✕</button></td>
    </tr>`).join('')}
    </tbody></table></div></div>`;
  });
  c.innerHTML=h;
}
 
// ── DASHBOARD ─────────────────────────────────────────────────
function renderDashboard(totals){
  const kcal=Math.round(totals.kcal);
  document.getElementById('ring-kcal').textContent=kcal;
  document.getElementById('ring-tgt').textContent=targets?`of ${targets.kcal} kcal`:'of — kcal';
  const ep=targets?Math.min(Math.round((kcal/targets.kcal)*100),100):0;
  const rc=ep>110?'rgba(252,129,129,.9)':ep>85?'rgba(104,211,145,.9)':'rgba(99,179,237,.9)';
  charts.energy.data.datasets[0].data=[ep,100-ep];
  charts.energy.data.datasets[0].backgroundColor[0]=rc;
  charts.energy.update('none');
 
  [{k:'prot',c:'#63b3ed'},{k:'carb',c:'#f6ad55'},{k:'fat',c:'#68d391'},{k:'fiber',c:'#b794f4'}].forEach(m=>{
    const v=+totals[m.k].toFixed(1);const t=targets?targets[m.k]:0;
    const p=t?Math.min(Math.round((v/t)*100),100):0;
    document.getElementById('mb-'+m.k).textContent=v+'g';
    document.getElementById('mb-'+m.k+'-p').textContent=t?p+'%':'';
    const pb=document.getElementById('pb-'+m.k);pb.style.width=p+'%';pb.style.background=m.c;
  });
 
  if(targets){
    charts.macro.data.datasets[0].data=[totals.prot.toFixed(1),totals.carb.toFixed(1),totals.fat.toFixed(1),totals.fiber.toFixed(1)];
    charts.macro.data.datasets[1].data=[targets.prot,targets.carb,targets.fat,targets.fiber];
    charts.macro.update();
    const rkeys=['iron','calcium','vitC','vitD','vitB12','mag','zinc','fol'];
    charts.radar.data.datasets[0].data=rkeys.map(k=>targets[k]?Math.min(+(totals[k]/targets[k]*100).toFixed(1),150):0);
    charts.radar.update();
  }
 
  // Meal pie
  const mkcal=MEALS.map(m=>foodLog.filter(e=>e.meal===m).reduce((s,e)=>s+e.nut.kcal,0));
  charts.meal.data.datasets[0].data=mkcal;charts.meal.update();
 
  // Score
  const so=calcScore(totals);
  if(so){
    const s=so.overall;
    const sc=s>=80?'good':s>=50?'warn':'bad';
    document.getElementById('score-val').textContent=s;
    document.getElementById('score-cat').textContent=s>=80?'Excellent':s>=65?'Good':s>=50?'Fair':'Needs Work';
    document.getElementById('pill-score').className='sp '+sc;
    document.getElementById('hdr-score').textContent=`Score: ${s}/100`;
    document.getElementById('hdr-dot').style.background=s>=80?'var(--a2)':s>=50?'var(--aw)':'var(--ad)';
    document.getElementById('score-breakdown').innerHTML=so.details.map(d=>{
      const fc=d.score>=80?'var(--a2)':d.score>=50?'var(--aw)':'var(--ad)';
      return`<div class="sbr"><div class="sbl">${d.name}</div><div class="sbt"><div class="sbf" style="width:${d.score}%;background:${fc}"></div></div><div class="sbp">${d.score}</div></div>`;
    }).join('');
  }
 
  // Deficiency / Excess
  if(!targets||!foodLog.length){
    ['deficiency-list','excess-list'].forEach(id=>document.getElementById(id).innerHTML='<div style="font-size:12px;color:var(--txtm);text-align:center;padding:16px 0">Log food to see insights</div>');
    return;
  }
  const nm=NUTMETA.map(m=>({n:m.n,k:m.k,u:m.u,pct:targets[m.k]?Math.round((totals[m.k]/targets[m.k])*100):0}));
  const defs=nm.filter(m=>m.pct<75&&targets[m.k]>0).sort((a,b)=>a.pct-b.pct).slice(0,6);
  const excs=nm.filter(m=>m.pct>115&&targets[m.k]>0).sort((a,b)=>b.pct-a.pct).slice(0,6);
  const defEl=m=>`<div class="di"><div><div class="dn">${m.n}</div></div><div class="dr"><div class="dp">${m.pct}%</div><div class="dbm"><div class="dfm" style="width:${Math.min(m.pct,100)}%;background:var(--ad)"></div></div></div></div>`;
  const excEl=m=>`<div class="di"><div><div class="dn">${m.n}</div></div><div class="dr"><div class="dp">${m.pct}%</div><div class="dbm"><div class="dfm" style="width:${Math.min(m.pct,100)}%;background:var(--aw)"></div></div></div></div>`;
  document.getElementById('deficiency-list').innerHTML=defs.length?defs.map(defEl).join(''):'<div style="font-size:12px;color:var(--a2);text-align:center;padding:16px 0">✓ No major deficiencies!</div>';
  document.getElementById('excess-list').innerHTML=excs.length?excs.map(excEl).join(''):'<div style="font-size:12px;color:var(--a2);text-align:center;padding:16px 0">✓ No major excesses!</div>';
}
 
// ── NUTRIENTS TABLE ───────────────────────────────────────────
function renderNutrients(totals){
  if(!targets)return;
  document.getElementById('nutrient-tbody').innerHTML=NUTMETA.map(r=>{
    if(!targets[r.k])return'';
    const pct=Math.round((totals[r.k]/targets[r.k])*100);
    const fill=Math.min(pct,100);
    let color='#63b3ed',bc='bok',bl='OK';
    if(pct<50){color='#fc8181';bc='blow';bl='Low';}
    else if(pct<75){color='#f6ad55';bc='bwarn';bl='Below';}
    else if(pct>150){color='#fc8181';bc='bhigh';bl='High';}
    else if(pct>110){color='#f6ad55';bc='bhigh';bl='Over';}
    return`<tr><td style="font-weight:500">${r.n}</td><td><span class="badge" style="background:rgba(255,255,255,.05);color:var(--txt2)">${r.cat}</span></td>
      <td>${+totals[r.k].toFixed(2)} ${r.u}</td><td style="color:var(--txt2)">${targets[r.k]} ${r.u}</td>
      <td><div class="ntb"><div class="ntf" style="width:${fill}%;background:${color}"></div></div></td>
      <td style="font-weight:600;color:${color}">${pct}%</td>
      <td><span class="badge ${bc}">${bl}</span></td></tr>`;
  }).join('');
}
 
// ── RECOMMENDATIONS ───────────────────────────────────────────
function renderReco(totals){
  if(!targets||!foodLog.length)return;
  const d=profile.diet;const h=profile.health;
  const p=k=>targets[k]?(totals[k]/targets[k])*100:100;
  const R=[];
 
  // Protein
  if(p('prot')<70){
    if(d==='nonveg')R.push({t:'add',txt:`<strong>Protein is low (${Math.round(p('prot'))}%).</strong> Add Chicken (31g/100g), Fish (20g/100g) or Eggs (12.6g/100g) to boost intake.`});
    else if(d==='egg')R.push({t:'add',txt:`<strong>Protein gap detected.</strong> Add 2–3 Eggs or 100g Tofu (8g protein). Both are complete protein sources.`});
    else if(d==='vegan')R.push({t:'add',txt:`<strong>Protein is at ${Math.round(p('prot'))}%.</strong> Add Soya Chunks (52g protein/100g), Quinoa (4.4g) or Peanuts (25.8g) as vegan sources.`});
    else R.push({t:'add',txt:`<strong>Protein gap.</strong> Add Paneer (18.3g/100g), Chana (8.9g) or Moong Dal (7g) to reach your target.`});
  }
 
  // Iron
  if(p('iron')<70){
    if(d==='veg'||d==='vegan')R.push({t:'add',txt:`<strong>Iron is low (${Math.round(p('iron'))}%).</strong> Add Spinach (2.7mg), Urad Dal (7.6mg), or Jaggery (11mg per 100g). Pair with Amla or Orange (Vitamin C) to improve absorption by up to 3×.`});
    else R.push({t:'add',txt:`<strong>Iron at ${Math.round(p('iron'))}%.</strong> Add Mutton (2.7mg/100g) or Chicken liver. Also consider Poha (20mg iron/100g) as an iron-rich grain option.`});
  }
 
  // Calcium
  if(p('calcium')<70)R.push({t:'add',txt:`<strong>Calcium is at ${Math.round(p('calcium'))}%.</strong> Add Milk (113mg/100ml), Paneer (480mg), Drumstick (185mg) or Ragi for vegetarian sources. Chia Seeds provide 631mg per 100g.`});
 
  // Vitamin C
  if(p('vitC')<60)R.push({t:'add',txt:`<strong>Vitamin C is low (${Math.round(p('vitC'))}%).</strong> Amla is the richest source (600mg/100g). Also try Guava (228mg), Drumstick (141mg), or Broccoli (89mg).`});
 
  // Vitamin D
  if(p('vitD')<60){
    if(d==='nonveg'||d==='egg')R.push({t:'add',txt:`<strong>Vitamin D at ${Math.round(p('vitD'))}%.</strong> Salmon provides 11.1mcg/100g. Mushrooms exposed to sunlight also generate Vitamin D (up to 7mcg/100g). Also: 15–20 min morning sunlight daily.`});
    else R.push({t:'add',txt:`<strong>Vitamin D is low.</strong> Sunlight-exposed Mushrooms (7mcg/100g) and fortified Milk (1.2mcg) are your best food sources. Consider 15–20 min morning sun exposure.`});
  }
 
  // B12
  if(p('vitB12')<60){
    if(d==='veg')R.push({t:'add',txt:`<strong>B12 deficiency risk.</strong> B12 is found almost exclusively in animal products. Curd (0.4mcg), Milk (0.4mcg) and Paneer (0.5mcg) are your best options. A supplement (1000mcg methylcobalamin) is strongly advised.`});
    else if(d==='vegan')R.push({t:'risk',txt:`<strong>⚠ Critical B12 Risk for Vegans.</strong> There are virtually no plant sources of B12. A Vitamin B12 supplement is medically essential. Consult a doctor or dietitian.`});
    else R.push({t:'add',txt:`<strong>B12 at ${Math.round(p('vitB12'))}%.</strong> Fish (3.2mcg), Mutton (2.4mcg) and Prawns (1.1mcg) are rich sources. Add 1–2 servings of these weekly.`});
  }
 
  // Omega-3
  if(p('om3')<50){
    if(d==='nonveg'||d==='egg')R.push({t:'add',txt:`<strong>Omega-3 is low.</strong> Salmon (2.6g/100g) and Fish (1.5g) are top sources. Aim for 2 servings of fatty fish per week.`});
    else R.push({t:'add',txt:`<strong>Omega-3 gap.</strong> Add Flaxseeds (22.8g/100g), Chia Seeds (17.8g) or Walnuts (9.1g) daily. Use Mustard Oil (5.9g Omega-3) for cooking.`});
  }
 
  // Magnesium
  if(p('mag')<60)R.push({t:'add',txt:`<strong>Magnesium is low (${Math.round(p('mag'))}%).</strong> Add Oats (177mg), Almonds (270mg), Chia Seeds (335mg) or Flaxseeds (392mg) as magnesium-rich snacks.`});
 
  // Folate
  if(p('fol')<60)R.push({t:'add',txt:`<strong>Folate at ${Math.round(p('fol'))}%.</strong> Add Toor Dal (456mcg/100g), Spinach (194mcg), Peas (65mcg) or Beetroot (109mcg) to boost folate intake.`});
 
  // Health condition specific
  if(h==='diabetes'){
    if(p('fiber')<80)R.push({t:'add',txt:`<strong>For Diabetes:</strong> Fiber slows glucose absorption. Target 38g/day. Add Rajma, Chana, or Flaxseeds and replace White Rice with Brown Rice or Quinoa.`});
    if(p('carb')>90)R.push({t:'swap',txt:`<strong>For Diabetes:</strong> Your carb intake is at ${Math.round(p('carb'))}%. Swap White Rice for Brown Rice (lower glycaemic index) or reduce portion size. Prefer complex carbs.`});
  }
  if(h==='hypertension'){
    if(totals.sod>2000)R.push({t:'risk',txt:`<strong>⚠ Sodium is high (${Math.round(totals.sod)}mg).</strong> For hypertension, keep sodium below 2300mg/day. Reduce processed foods, Bread, Idli and Dosa. Increase Potassium-rich foods (Banana, Sweet Potato, Rajma).`});
  }
  if(h==='anemia'){
    if(p('iron')<80)R.push({t:'risk',txt:`<strong>⚠ Iron Priority for Anaemia:</strong> Your iron is at ${Math.round(p('iron'))}% of the elevated target. Eat iron-rich foods (Poha, Spinach, Jaggery) WITH Vitamin C (Amla, Orange) at every meal for maximum absorption.`});
    if(p('vitB12')<80)R.push({t:'risk',txt:`<strong>B12 is low — critical for anaemia.</strong> B12 deficiency can cause megaloblastic anaemia. Include Egg, Milk, Curd or Fish daily.`});
  }
  if(h==='pregnancy'){
    if(p('fol')<90)R.push({t:'risk',txt:`<strong>⚠ Folate is critical in pregnancy.</strong> Target is 600mcg/day. Add Toor Dal, Spinach, and Peas daily. Medical supplementation is typically recommended — consult your doctor.`});
    if(p('iron')<85)R.push({t:'risk',txt:`<strong>⚠ Iron needs are higher in pregnancy (27mg/day).</strong> Current intake is at ${Math.round(p('iron'))}%. Include iron-rich foods at every meal and avoid tea/coffee with meals (reduces absorption).`});
  }
 
  // Swaps
  if(p('fat')>130&&p('prot')<80){
    if(d!=='veg'&&d!=='vegan')R.push({t:'swap',txt:`<strong>Swap fried for grilled:</strong> Replace fried Chicken or Mutton with grilled versions. Same protein, ~40% less fat. Your fat is at ${Math.round(p('fat'))}%.`});
    else R.push({t:'swap',txt:`<strong>Reduce oil in cooking:</strong> Fat is at ${Math.round(p('fat'))}%. Measure oil using a tablespoon (1 tbsp = 15g). Choose baking or steaming over frying.`});
  }
  if(p('carb')>130)R.push({t:'swap',txt:`<strong>Carbs at ${Math.round(p('carb'))}%.</strong> Swap one serving of Rice with Dal + Sabzi. You'll gain protein and fiber while cutting carbs. Try Brown Rice or Quinoa for lower glycaemic options.`});
  if(p('sodium')>110||(targets&&totals.sod>targets.sod))R.push({t:'port',txt:`<strong>Sodium approaching limit.</strong> Reduce Bread, Idli, Dosa and processed foods which tend to be high in sodium. Cook at home with minimal salt.`});
  if(p('kcal')>115)R.push({t:'port',txt:`<strong>Calories at ${Math.round(p('kcal'))}% of target.</strong> Consider smaller Rice/Roti portions. Replace a snack with Cucumber, Tomato or Buttermilk (very low calorie, high nutrition).`});
  if(p('kcal')<55&&foodLog.length>0)R.push({t:'add',txt:`<strong>Calorie intake is very low (${Math.round(p('kcal'))}%).</strong> Add energy-dense foods: Oats (389kcal), Roti (297kcal), Peanuts (567kcal) or Dates (282kcal).`});
 
  document.getElementById('reco-list').innerHTML=R.length
    ?R.map(r=>`<div class="ri ${r.t}"><div class="rt2 ${r.t}">${r.t==='add'?'+ Add':r.t==='swap'?'⇄ Swap':r.t==='port'?'⚖ Portion':r.t==='risk'?'⚠ Risk Alert':r.t}</div><div>${r.txt}</div></div>`).join('')
    :'<div class="re">🎉 Great balance! Keep logging to track progress.</div>';
}
 
// ── RISK ANALYSIS ─────────────────────────────────────────────
function renderRisk(totals){
  if(!targets||!foodLog.length){return;}
  const risks=[];
  const p=k=>targets[k]?(totals[k]/targets[k])*100:100;
  const h=profile.health;const diet=profile.diet;
 
  // Protein malnutrition
  if(p('prot')<50)risks.push({icon:'💪',title:'Protein Malnutrition Risk',level:'high',desc:`Protein intake is critically low (${Math.round(p('prot'))}% of target). Chronic low protein can lead to muscle wasting (sarcopenia), impaired immunity, slow wound healing, and hair loss. Aim to include a protein source at every meal.`});
  else if(p('prot')<70)risks.push({icon:'💪',title:'Sub-Optimal Protein Intake',level:'med',desc:`Protein is at ${Math.round(p('prot'))}% of target. Consider adding 1–2 protein-rich servings daily to meet your ${targets.prot}g target.`});
 
  // Iron deficiency anaemia
  if(p('iron')<50)risks.push({icon:'🩸',title:'Iron Deficiency Anaemia Risk',level:'high',desc:`Iron intake is at ${Math.round(p('iron'))}% of target (${Math.round(totals.iron)}/${targets.iron}mg). Iron deficiency is the most common nutritional deficiency in India, especially in women. Symptoms: fatigue, pallor, shortness of breath, poor concentration. ${diet==='veg'||diet==='vegan'?'Plant iron (non-haem) absorbs poorly — always combine with Vitamin C foods.':''}`});
  else if(p('iron')<75)risks.push({icon:'🩸',title:'Low Iron Intake',level:'med',desc:`Iron is at ${Math.round(p('iron'))}%. Sustained deficit over weeks can deplete iron stores leading to anaemia.`});
 
  // Vitamin D deficiency
  if(p('vitD')<40)risks.push({icon:'☀️',title:'Vitamin D Deficiency Risk',level:'high',desc:`Vitamin D is critically low (${Math.round(p('vitD'))}%). Deficiency leads to weakened bones (osteomalacia, rickets in children), impaired immune function, depression, and increased fracture risk. Over 70% of Indians are estimated to be Vitamin D deficient. Food alone rarely meets needs — sun exposure is essential.`});
  else if(p('vitD')<70)risks.push({icon:'☀️',title:'Vitamin D Insufficiency',level:'med',desc:`Vitamin D at ${Math.round(p('vitD'))}%. Long-term insufficiency can contribute to bone density loss.`});
 
  // Calcium — bone health
  if(p('calcium')<50)risks.push({icon:'🦴',title:'Bone Health Risk (Calcium)',level:h==='osteoporosis'?'high':'med',desc:`Calcium is at ${Math.round(p('calcium'))}%. Combined with low Vitamin D, this significantly increases risk of osteoporosis and bone fractures, especially in post-menopausal women and older adults. ${h==='osteoporosis'?'⚠ Critical given your declared health condition.':''}`});
 
  // B12 — neurological
  if(p('vitB12')<50)risks.push({icon:'🧠',title:'Vitamin B12 Deficiency Risk',level:diet==='vegan'?'high':'med',desc:`B12 at ${Math.round(p('vitB12'))}%. Deficiency causes megaloblastic anaemia, irreversible neurological damage, depression, memory issues, and tingling in extremities. ${diet==='vegan'?'⚠ Critical for vegans — supplementation is medically essential.':diet==='veg'?'Plant-based diets have very limited B12 sources. Supplementation is recommended.':''}`});
 
  // Sodium
  if(totals.sod>targets.sod)risks.push({icon:'🧂',title:'High Sodium Intake',level:h==='hypertension'?'high':'med',desc:`Sodium intake is ${Math.round(totals.sod)}mg vs the ${targets.sod}mg limit. High sodium raises blood pressure, increasing risk of stroke, heart disease and kidney damage. ${h==='hypertension'?'⚠ Especially critical given your hypertension history.':''} Main sources: Bread, processed foods, Idli, Dosa, pickles.`});
 
  // Calorie surplus
  if(p('kcal')>120)risks.push({icon:'⚖️',title:'Calorie Surplus',level:p('kcal')>140?'high':'med',desc:`Calorie intake is ${Math.round(p('kcal'))}% of target. Consistent surplus leads to weight gain and increases risk of obesity, type 2 diabetes, hypertension, and cardiovascular disease. ${h==='diabetes'?'⚠ Especially relevant given your diabetes risk.':''}`});
 
  // Calorie deficit
  if(p('kcal')<60&&foodLog.length>0)risks.push({icon:'🔋',title:'Calorie Deficit Risk',level:p('kcal')<40?'high':'med',desc:`Calorie intake is only ${Math.round(p('kcal'))}% of target. Severe restriction causes muscle breakdown, nutrient deficiencies, fatigue, hormonal disruption, and impaired metabolic rate.`});
 
  // Omega-3 very low
  if(p('om3')<30)risks.push({icon:'🐟',title:'Omega-3 Deficiency',level:'low',desc:`Omega-3 at ${Math.round(p('om3'))}%. Chronic low intake is associated with increased inflammation, cardiovascular disease risk, cognitive decline, and poor eye health.`});
 
  // Pregnancy specific
  if(h==='pregnancy'&&p('fol')<75)risks.push({icon:'🤰',title:'Neural Tube Defect Risk',level:'high',desc:`Folate is at ${Math.round(p('fol'))}% — critically important in pregnancy. Folate deficiency in the first trimester is strongly associated with neural tube defects (spina bifida, anencephaly). Medical supplementation of 400–600mcg folic acid is standard. Please consult your gynaecologist.`});
 
  if(!risks.length){risks.push({icon:'✅',title:'No Major Risks Detected',level:'low',desc:`Based on today's log, your nutritional intake does not show major risk indicators. Continue logging consistently for accurate ongoing assessment. Remember: risk analysis is based on a single day's log — patterns over time are more meaningful.`});}
 
  const lvl={high:'rl-high',med:'rl-med',low:'rl-low'};
  const lvlLabel={high:'High Risk',med:'Moderate',low:'Low'};
  document.getElementById('risk-body').innerHTML=risks.map(r=>`
    <div class="risk-item">
      <div class="risk-head">
        <div class="risk-icon">${r.icon}</div>
        <div class="risk-title">${r.title}</div>
        <div class="risk-level ${lvl[r.level]}">${lvlLabel[r.level]}</div>
      </div>
      <div class="risk-desc">${r.desc}</div>
    </div>`).join('');
}
 
// ── MEAL PLANNER ──────────────────────────────────────────────
function initPlanner(){
  const grid=document.getElementById('planner-grid');
  grid.innerHTML=['day1','day2'].map((day,di)=>`
    <div class="day-col">
      <div class="day-head">Day ${di+1}<span class="day-kcal" id="plan-kcal-${day}"></span></div>
      ${MEALS.map(meal=>`
        <div class="meal-slot">
          <div class="meal-slot-head">${MEAL_IC[meal]} ${meal}</div>
          <div class="plan-food-add">
            <select id="plan-food-${day}-${meal}" style="font-size:12px;padding:5px 8px"><option value="">— food —</option></select>
            <input id="plan-qty-${day}-${meal}" type="number" placeholder="g" min="1" style="width:55px;font-size:12px;padding:5px 7px">
            <button class="btn btn-p" style="font-size:12px;padding:5px 10px" onclick="addPlanItem('${day}','${meal}')">+</button>
          </div>
          <div class="plan-items" id="plan-items-${day}-${meal}"></div>
        </div>`).join('')}
      <div class="plan-totals" id="plan-totals-${day}"></div>
    </div>`).join('');
 
  // Populate plan food selects
  const names=Object.keys(DB).sort();
  ['day1','day2'].forEach(day=>{
    MEALS.forEach(meal=>{
      const sel=document.getElementById(`plan-food-${day}-${meal}`);
      names.forEach(n=>{const o=document.createElement('option');o.value=n;o.textContent=n;sel.appendChild(o);});
    });
  });
}
 
function addPlanItem(day,meal){
  const name=document.getElementById(`plan-food-${day}-${meal}`).value;
  const qty=+document.getElementById(`plan-qty-${day}-${meal}`).value;
  if(!name||!qty||qty<=0){toast('Select food and quantity.');return;}
  const grams=qty;
  const f=DB[name];const s=grams/100;
  const kcal=+(f.kcal*s).toFixed(1);
  planner[day][meal].push({id:Date.now()+Math.random(),name,qty,kcal});
  document.getElementById(`plan-qty-${day}-${meal}`).value='';
  saveState();renderPlanner();
}
 
function removePlanItem(day,meal,id){
  planner[day][meal]=planner[day][meal].filter(x=>x.id!==id);
  saveState();renderPlanner();
}
 
function renderPlanner(){
  if(!document.getElementById('planner-grid'))return;
  ['day1','day2'].forEach(day=>{
    MEALS.forEach(meal=>{
      const container=document.getElementById(`plan-items-${day}-${meal}`);
      if(!container)return;
      const items=planner[day][meal];
      container.innerHTML=items.length
        ?items.map(it=>`<div class="plan-item"><span class="plan-item-name">${it.name}</span><span class="plan-item-info">${it.qty}g · ${it.kcal}kcal</span><button class="plan-item-del" onclick="removePlanItem('${day}','${meal}',${it.id})">✕</button></div>`).join('')
        :'<div style="font-size:11px;color:var(--txtm);padding:3px 0">Nothing added yet</div>';
    });
    const allItems=MEALS.flatMap(m=>planner[day][m]);
    const totKcal=allItems.reduce((s,x)=>s+x.kcal,0);
    document.getElementById(`plan-kcal-${day}`).textContent=totKcal.toFixed(0)+' kcal planned';
    const tgtKcal=targets?targets.kcal:0;
    const macTotals={prot:0,carb:0,fat:0};
    allItems.forEach(it=>{
      const f=DB[it.name];const s=it.qty/100;
      macTotals.prot+=f.prot*s;macTotals.carb+=f.carb*s;macTotals.fat+=f.fat*s;
    });
    document.getElementById(`plan-totals-${day}`).innerHTML=allItems.length?`
      <div class="plan-tot-item">Protein: <strong>${macTotals.prot.toFixed(1)}g</strong></div>
      <div class="plan-tot-item">Carbs: <strong>${macTotals.carb.toFixed(1)}g</strong></div>
      <div class="plan-tot-item">Fat: <strong>${macTotals.fat.toFixed(1)}g</strong></div>
      ${tgtKcal?`<div class="plan-tot-item">vs Target: <strong style="color:${Math.abs(totKcal-tgtKcal)<200?'var(--a2)':'var(--aw)'}">${totKcal>tgtKcal?'+':''}${(totKcal-tgtKcal).toFixed(0)} kcal</strong></div>`:''}
    `:'';
  });
}
 
// ── CSV UPLOAD ────────────────────────────────────────────────
function handleCSV(input){
  const file=input.files[0];if(!file)return;
  const reader=new FileReader();
  reader.onload=e=>parseCSV(e.target.result);
  reader.readAsText(file);input.value='';
}
function handleDrop(e){
  e.preventDefault();document.getElementById('csv-zone').classList.remove('drag');
  const file=e.dataTransfer.files[0];
  if(!file||!file.name.endsWith('.csv')){toast('Please drop a .csv file.');return;}
  const reader=new FileReader();
  reader.onload=ev=>parseCSV(ev.target.result);
  reader.readAsText(file);
}
function parseCSV(text){
  const lines=text.trim().split('\n');
  if(!lines.length){toast('CSV is empty.');return;}
  const headers=lines[0].toLowerCase().split(',').map(h=>h.trim());
  const fi=headers.indexOf('food'),mi=headers.indexOf('meal'),qi=headers.indexOf('quantity'),ui=headers.indexOf('unit');
  if(fi<0||qi<0){toast('CSV must have "food" and "quantity" columns.');return;}
  let added=0,skipped=0,previewRows=[];
  for(let i=1;i<lines.length;i++){
    if(!lines[i].trim())continue;
    const cols=lines[i].split(',').map(c=>c.trim().replace(/^"|"$/g,''));
    const name=cols[fi];const meal=mi>=0?cols[mi]:'Lunch';const qty=+cols[qi];const unit=ui>=0?(cols[ui]||'g'):'g';
    const matchName=Object.keys(DB).find(k=>k.toLowerCase()===name.toLowerCase());
    if(!matchName||!qty||qty<=0){skipped++;previewRows.push({status:'⚠ Skip',name,meal,qty,unit,reason:!matchName?'Unknown food':'Invalid qty'});continue;}
    const validMeal=MEALS.includes(meal)?meal:'Lunch';
    const grams=qty*(UNIT_G[unit]||1);
    const entry=calcEntry(matchName,validMeal,qty,unit,grams);
    foodLog.push(entry);added++;
    previewRows.push({status:'✓ Added',name:matchName,meal:validMeal,qty,unit,reason:''});
  }
  saveState();renderAll();
  toast(`CSV: ${added} added, ${skipped} skipped.`);
  document.getElementById('csv-preview').innerHTML=previewRows.length?`
    <div style="margin-top:12px;font-size:12px;color:var(--txt2);margin-bottom:6px">${added} rows added · ${skipped} skipped</div>
    <div class="ftw"><table><thead><tr><th>Status</th><th>Food</th><th>Meal</th><th>Qty</th><th>Unit</th><th>Note</th></tr></thead><tbody>
    ${previewRows.map(r=>`<tr><td style="color:${r.status.includes('✓')?'var(--a2)':'var(--aw)'}">${r.status}</td><td>${r.name}</td><td>${r.meal}</td><td>${r.qty}</td><td>${r.unit}</td><td style="color:var(--txtm)">${r.reason}</td></tr>`).join('')}
    </tbody></table></div>`:'';
}
function downloadTemplate(){
  const csv='food,meal,quantity,unit\nRice,Lunch,150,g\nDal,Lunch,100,g\nChicken,Dinner,120,g\nBanana,Breakfast,1,piece\nMilk,Breakfast,200,ml\n';
  const blob=new Blob([csv],{type:'text/csv'});
  const a=document.createElement('a');a.href=URL.createObjectURL(blob);a.download='nutri-scope-template.csv';a.click();
}
 
// ── EXPORT CSV ────────────────────────────────────────────────
function exportCSV(){
  if(!foodLog.length){toast('Nothing to export.');return;}
  const headers=['food','meal','quantity','unit','kcal','protein_g','carbs_g','fat_g','fiber_g','iron_mg','calcium_mg','vitC_mg','vitD_mcg','vitB12_mcg'];
  const rows=foodLog.map(e=>[e.name,e.meal,e.qty,e.unit,e.nut.kcal.toFixed(1),e.nut.prot.toFixed(1),e.nut.carb.toFixed(1),e.nut.fat.toFixed(1),e.nut.fiber.toFixed(1),e.nut.iron.toFixed(2),e.nut.calcium.toFixed(1),e.nut.vitC.toFixed(1),e.nut.vitD.toFixed(2),e.nut.vitB12.toFixed(2)].join(','));
  const csv=[headers.join(','),...rows].join('\n');
  const blob=new Blob([csv],{type:'text/csv'});
  const a=document.createElement('a');a.href=URL.createObjectURL(blob);a.download='nutri-scope-log.csv';a.click();
  toast('CSV exported ✓');
}
 
// ── TABS ──────────────────────────────────────────────────────
function stab(id,btn){
  document.querySelectorAll('.tp').forEach(p=>p.classList.remove('active'));
  document.querySelectorAll('.tb').forEach(b=>b.classList.remove('active'));
  document.getElementById('tab-'+id).classList.add('active');btn.classList.add('active');
}
 
// ── TOAST ─────────────────────────────────────────────────────
function toast(msg){
  const w=document.getElementById('tw');const el=document.createElement('div');
  el.className='toast';el.textContent=msg;w.appendChild(el);setTimeout(()=>el.remove(),3200);
}
</script>
</body>
</html>
