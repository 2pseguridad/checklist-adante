[index (4).html](https://github.com/user-attachments/files/27860557/index.4.html)
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
<title>Checklist de Adante</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@700;800&family=DM+Sans:wght@400;500&display=swap" rel="stylesheet">
<style>
:root {
  --bg:#0f0f13; --sur:#1a1a22; --sur2:#22222e; --bor:#2e2e3e;
  --acc:#7c6af7; --acc2:#f76a8f; --grn:#4ade80; --txt:#e8e8f0;
  --mut:#7070a0; --red:#f76a6a;
}
*{box-sizing:border-box;margin:0;padding:0}
body{background:var(--bg);color:var(--txt);font-family:'DM Sans',sans-serif;min-height:100vh;padding:20px 14px 70px}

/* HEADER */
h1{font-family:'Syne',sans-serif;font-weight:800;font-size:1.9rem;text-align:center;
   background:linear-gradient(135deg,var(--acc),var(--acc2));-webkit-background-clip:text;
   -webkit-text-fill-color:transparent;background-clip:text}
.sub{text-align:center;color:var(--mut);font-size:.83rem;margin-top:4px}
.bwrap{background:var(--sur2);border-radius:99px;height:8px;max-width:340px;margin:14px auto;overflow:hidden}
.bfill{height:100%;background:linear-gradient(90deg,var(--acc),var(--acc2));border-radius:99px;transition:width .5s ease;width:0}
.blbl{text-align:center;font-size:.77rem;color:var(--mut);margin-bottom:20px}

/* ADMIN BTN */
.admin-bar{max-width:480px;margin:0 auto 14px}
.abtn{background:var(--sur2);border:1px solid var(--bor);color:var(--mut);border-radius:10px;
      padding:8px 16px;font-size:.8rem;cursor:pointer;font-family:'DM Sans',sans-serif;transition:all .2s}
.abtn.on{border-color:var(--acc);color:var(--acc);background:rgba(124,106,247,.1)}

/* ADD PANEL */
.add-panel{max-width:480px;margin:0 auto 14px;background:var(--sur);border:1px dashed var(--acc);
           border-radius:14px;padding:16px;display:none}
.add-panel.show{display:block}
.add-panel label{font-size:.77rem;color:var(--mut);display:block;margin-bottom:6px}
.add-inp{width:100%;background:var(--sur2);border:1px solid var(--bor);border-radius:8px;
         color:var(--txt);font-size:.9rem;padding:10px 12px;outline:none;margin-bottom:10px;
         font-family:'DM Sans',sans-serif}
.add-inp:focus{border-color:var(--acc)}

/* TASK LIST */
.tlist{display:flex;flex-direction:column;gap:10px;max-width:480px;margin:0 auto}

.tcard{background:var(--sur);border:1px solid var(--bor);border-radius:14px;overflow:hidden;transition:border-color .2s,box-shadow .2s}
.tcard.done{border-color:var(--grn);box-shadow:0 0 0 1px rgba(74,222,128,.12)}

.thead{display:flex;align-items:center;gap:10px;padding:13px 14px;cursor:pointer;
       user-select:none;-webkit-tap-highlight-color:transparent}
.chk{width:26px;height:26px;border-radius:8px;border:2px solid var(--bor);flex-shrink:0;
     display:flex;align-items:center;justify-content:center;transition:all .2s;font-size:15px}
.tcard.done .chk{background:var(--grn);border-color:var(--grn)}
.tcard.done .chk::after{content:'✓';color:#0f0f13;font-weight:700}
.tinfo{flex:1;min-width:0}
.tname{font-family:'Syne',sans-serif;font-weight:700;font-size:.88rem;line-height:1.3}
.tcard.done .tname{color:var(--mut);text-decoration:line-through;text-decoration-color:var(--grn)}
.tmeta{font-size:.71rem;color:var(--grn);margin-top:3px}
.chev{font-size:.65rem;color:var(--mut);transition:transform .2s;flex-shrink:0}
.tcard.open .chev{transform:rotate(180deg)}

/* admin card buttons */
.be,.bd{background:none;border:none;cursor:pointer;font-size:.9rem;padding:2px 4px;
        flex-shrink:0;display:none;line-height:1}
body.admin .be,body.admin .bd{display:inline}
.bd{color:var(--red)}
.edit-inp{font-family:'Syne',sans-serif;font-weight:700;font-size:.88rem;background:var(--sur2);
          border:1px solid var(--acc);border-radius:6px;color:var(--txt);padding:4px 8px;outline:none;width:100%}

/* EVAL PANEL */
.epanel{display:none;background:var(--sur2);border-top:1px solid var(--bor);padding:16px}
.tcard.open .epanel{display:block;animation:drop .2s ease}
@keyframes drop{from{opacity:0;transform:translateY(-6px)}to{opacity:1;transform:translateY(0)}}

.epanel label{font-size:.77rem;color:var(--mut);display:block;margin-bottom:5px;font-weight:500}
.epanel textarea{width:100%;background:var(--sur);border:1px solid var(--bor);border-radius:8px;
                 color:var(--txt);font-family:'DM Sans',sans-serif;font-size:.84rem;
                 padding:9px 11px;resize:none;outline:none;margin-bottom:12px;min-height:60px;
                 transition:border-color .2s}
.epanel textarea:focus{border-color:var(--acc)}

/* score */
.srow{display:flex;align-items:center;gap:10px;margin-bottom:3px}
.srow label{margin:0;white-space:nowrap;font-size:.77rem}
.sinp{width:70px;background:var(--sur);border:1px solid var(--bor);border-radius:8px;
      color:var(--txt);font-family:'Syne',sans-serif;font-weight:700;font-size:1rem;
      padding:6px 10px;outline:none;text-align:center;transition:border-color .2s}
.sinp:focus{border-color:var(--acc)}
.shint{font-size:.71rem;color:var(--mut);flex:1}
.shint.ok{color:var(--grn)} .shint.bad{color:var(--red)}
.srange{font-size:.7rem;color:var(--mut);margin-bottom:12px}
.errmsg{font-size:.74rem;color:var(--red);margin-bottom:9px;display:none}

/* photo upload */
.photo-section{margin-bottom:14px}
.photo-label-btn{display:inline-flex;align-items:center;gap:6px;background:var(--sur);
                 border:1px solid var(--bor);border-radius:8px;padding:8px 12px;
                 font-size:.8rem;color:var(--mut);cursor:pointer;transition:border-color .2s}
.photo-label-btn:hover{border-color:var(--acc);color:var(--acc)}
.photo-label-btn input{display:none}
.photo-preview{margin-top:10px;border-radius:12px;overflow:hidden;display:none;
               border:1px solid var(--bor);background:var(--sur)}
.photo-preview img{width:100%;max-height:280px;object-fit:contain;display:block;border-radius:12px}
.photo-remove{font-size:.72rem;color:var(--red);cursor:pointer;margin-top:7px;
              display:none;background:none;border:none;padding:0}

/* action buttons */
.btn-ok{width:100%;padding:11px;border-radius:10px;border:none;
        background:linear-gradient(135deg,var(--acc),var(--acc2));
        color:#fff;font-family:'Syne',sans-serif;font-weight:700;font-size:.87rem;
        cursor:pointer;transition:transform .1s;margin-bottom:8px}
.btn-ok:active{transform:scale(.97)}
.btn-ok:disabled{opacity:.3;cursor:not-allowed}
.btn-undo{width:100%;padding:10px;border-radius:10px;border:1px solid var(--bor);
          background:transparent;color:var(--mut);font-family:'DM Sans',sans-serif;
          font-size:.82rem;cursor:pointer;transition:border-color .2s,color .2s}
.btn-undo:active{border-color:var(--red);color:var(--red)}
.btn-add-t{width:100%;padding:10px;border-radius:10px;border:none;
           background:linear-gradient(135deg,var(--acc),var(--acc2));
           color:#fff;font-family:'Syne',sans-serif;font-weight:700;font-size:.84rem;cursor:pointer}
.btn-add-t:disabled{opacity:.3;cursor:not-allowed}

/* saved photo thumbnail on card */
.photo-thumb{width:44px;height:44px;border-radius:8px;object-fit:cover;flex-shrink:0;border:1px solid var(--bor)}

/* URGENCY */
.urg-selector{display:flex;gap:7px;margin-bottom:12px}
.urg-opt{flex:1;padding:8px 4px;border-radius:9px;border:2px solid transparent;
         font-family:'Syne',sans-serif;font-weight:700;font-size:.75rem;cursor:pointer;
         text-align:center;transition:all .15s;background:var(--sur2);color:var(--mut)}
.urg-opt.sel-baja  {border-color:#4ade80;background:rgba(74,222,128,.12);color:#4ade80}
.urg-opt.sel-media {border-color:#fbbf24;background:rgba(251,191,36,.12);color:#fbbf24}
.urg-opt.sel-alta  {border-color:#f76a6a;background:rgba(247,106,106,.14);color:#f76a6a}

/* urgency pill on card */
.upill{font-size:.65rem;font-weight:700;font-family:'Syne',sans-serif;
       padding:2px 8px;border-radius:99px;flex-shrink:0;letter-spacing:.3px}
.upill-baja {background:rgba(74,222,128,.15);color:#4ade80;border:1px solid rgba(74,222,128,.3)}
.upill-media{background:rgba(251,191,36,.15);color:#fbbf24;border:1px solid rgba(251,191,36,.3)}
.upill-alta {background:rgba(247,106,106,.16);color:#f76a6a;border:1px solid rgba(247,106,106,.3)}

/* left bar on card by urgency */
.tcard[data-urg='baja']  .thead{border-left:3px solid #4ade80;padding-left:11px}
.tcard[data-urg='media'] .thead{border-left:3px solid #fbbf24;padding-left:11px}
.tcard[data-urg='alta']  .thead{border-left:3px solid #f76a6a;padding-left:11px}

/* PIN */
#pinLayer{display:none;position:fixed;inset:0;z-index:9000;background:rgba(5,5,11,.94);
          backdrop-filter:blur(8px);align-items:center;justify-content:center}
#pinLayer.show{display:flex}
.pinbox{background:var(--sur);border:1px solid var(--bor);border-radius:22px;
        padding:28px 22px 20px;width:290px;max-width:92vw;text-align:center;
        animation:pop .2s cubic-bezier(.34,1.56,.64,1)}
@keyframes pop{from{transform:scale(.87);opacity:0}to{transform:scale(1);opacity:1}}
.picon{font-size:2rem;margin-bottom:7px}
.ptitle{font-family:'Syne',sans-serif;font-weight:800;font-size:1.05rem}
.psub{font-size:.76rem;color:var(--mut);margin-top:3px;margin-bottom:18px}
.pdots{display:flex;justify-content:center;gap:13px;margin-bottom:6px}
.dot{width:13px;height:13px;border-radius:50%;background:var(--bor);transition:background .12s,transform .1s}
.dot.on{background:var(--acc);transform:scale(1.2)}
.perr{font-size:.74rem;color:var(--red);min-height:18px;margin-bottom:8px}
.pgrid{display:grid;grid-template-columns:repeat(3,1fr);gap:8px;max-width:210px;margin:0 auto 12px}
.pk{background:var(--sur2);border:1px solid var(--bor);border-radius:11px;color:var(--txt);
    font-family:'Syne',sans-serif;font-weight:700;font-size:1.2rem;padding:14px 0;
    cursor:pointer;transition:background .1s,transform .08s;-webkit-tap-highlight-color:transparent}
.pk:active{background:var(--bor);transform:scale(.91)}
.pk.g{visibility:hidden}
.pcancelbtn{width:100%;padding:9px;border-radius:10px;border:1px solid var(--bor);
            background:transparent;color:var(--mut);font-family:'DM Sans',sans-serif;font-size:.8rem;cursor:pointer}

/* BADGE */
.badge{text-align:center;margin:26px auto 0;max-width:340px;
       background:linear-gradient(135deg,rgba(124,106,247,.1),rgba(247,106,143,.1));
       border:1px solid var(--acc);border-radius:16px;padding:20px;display:none}
.badge.show{display:block;animation:drop .4s ease}
.badge .e{font-size:2.3rem}
.badge h2{font-family:'Syne',sans-serif;font-size:1.05rem;font-weight:800;margin-top:7px}
.badge p{font-size:.8rem;color:var(--mut);margin-top:3px}

/* CONFETTI */
.cp{position:fixed;width:8px;height:8px;border-radius:2px;pointer-events:none;z-index:9999;
    animation:fall 1.3s ease-in forwards}
@keyframes fall{0%{transform:translateY(-20px) rotate(0);opacity:1}100%{transform:translateY(100vh) rotate(720deg);opacity:0}}
</style>
</head>
<body>

<!-- PIN -->
<div id="pinLayer">
  <div class="pinbox">
    <div class="picon">🔐</div>
    <div class="ptitle">PIN requerido</div>
    <div class="psub">Solo el adulto puede modificar el checklist</div>
    <div class="pdots">
      <div class="dot" id="d0"></div><div class="dot" id="d1"></div>
      <div class="dot" id="d2"></div><div class="dot" id="d3"></div>
    </div>
    <div class="perr" id="perr"></div>
    <div class="pgrid">
      <button class="pk" onclick="pk('1')">1</button>
      <button class="pk" onclick="pk('2')">2</button>
      <button class="pk" onclick="pk('3')">3</button>
      <button class="pk" onclick="pk('4')">4</button>
      <button class="pk" onclick="pk('5')">5</button>
      <button class="pk" onclick="pk('6')">6</button>
      <button class="pk" onclick="pk('7')">7</button>
      <button class="pk" onclick="pk('8')">8</button>
      <button class="pk" onclick="pk('9')">9</button>
      <button class="pk g"></button>
      <button class="pk" onclick="pk('0')">0</button>
      <button class="pk" onclick="pk('X')">⌫</button>
    </div>
    <button class="pcancelbtn" onclick="closePin()">Cancelar</button>
  </div>
</div>

<!-- MAIN -->
<h1>Checklist de Adante</h1>
<p class="sub">Tocá una tarea para evaluarla</p>
<div class="bwrap"><div class="bfill" id="bfill"></div></div>
<div class="blbl" id="blbl">0 de 0 completadas</div>

<div class="admin-bar">
  <button class="abtn" id="abtn" onclick="toggleAdmin()">✏️ Modo edición</button>
</div>

<div class="add-panel" id="addPanel">
  <label>Agregar nueva tarea</label>
  <input class="add-inp" id="newInp" type="text" maxlength="140" placeholder="Ej: Leer capítulo 3 de Historia...">
  <label style="font-size:.77rem;color:var(--mut);display:block;margin-bottom:6px">Urgencia</label>
  <div class="urg-selector">
    <button class="urg-opt sel-baja" id="uBaja"  onclick="selectUrg('baja')" >🟢 Baja</button>
    <button class="urg-opt"          id="uMedia" onclick="selectUrg('media')">🟡 Media</button>
    <button class="urg-opt"          id="uAlta"  onclick="selectUrg('alta')" >🔴 Alta</button>
  </div>
  <button class="btn-add-t" id="btnAdd" onclick="addTask()" disabled>+ Agregar tarea</button>
</div>

<div class="tlist" id="tlist"></div>

<div class="badge" id="badge">
  <div class="e">🏆</div>
  <h2>¡Todo listo, Adante!</h2>
  <p>¡Completaste todas las tareas, sos un crack!</p>
</div>

<script>
const PIN = '3344';
const MIN_SCORE = 8; // nota MAYOR A 8

// ── STORAGE ──────────────────────────────────────────
const INIT_TASKS = [
  {id:1,name:'Caligrafía hasta pág 7'},
  {id:2,name:'Completar pág. 4 de Construcción Ciudadana'},
  {id:3,name:'Completar pág. 5 de Construcción Ciudadana'},
  {id:4,name:'Estudiar para el recuperativo de Inglés'},
  {id:5,name:'Hacer el trabajo de Inglés (está en el celu de Dante)'},
  {id:6,name:'Proceso de aprendizaje — libro de PDL'},
  {id:7,name:'Puntos 12 y 14 del calendario — Naturales'},
  {id:8,name:'Lectura rápida de todos los Classroom'},
  {id:9,name:'Fibrón permanente'},
];

function loadTasks(){
  try{ const t=JSON.parse(localStorage.getItem('ad_tasks')); return Array.isArray(t)&&t.length?t:INIT_TASKS; }catch{ return INIT_TASKS; }
}
function saveTasks(){ localStorage.setItem('ad_tasks',JSON.stringify(tasks)); }
function loadState(){
  try{ return JSON.parse(localStorage.getItem('ad_state')||'{}'); }catch{ return {}; }
}
function saveState(){ localStorage.setItem('ad_state',JSON.stringify(state)); }

let tasks   = loadTasks();
let state   = loadState(); // {id:{done,score,note,photo}}
let adminOn = false;
let editId  = null;

// ── PIN ──────────────────────────────────────────────
let pinBuf='', pinCb=null;

function openPin(callback){
  pinBuf=''; pinCb=callback;
  refreshDots();
  document.getElementById('perr').textContent='';
  document.getElementById('pinLayer').classList.add('show');
}
function closePin(){
  document.getElementById('pinLayer').classList.remove('show');
  pinBuf=''; pinCb=null;
}
function pk(k){
  if(k==='X'){ pinBuf=pinBuf.slice(0,-1); refreshDots(); return; }
  if(pinBuf.length>=4) return;
  pinBuf+=k; refreshDots();
  if(pinBuf.length===4){
    setTimeout(function(){
      if(pinBuf===PIN){
        var cb=pinCb; closePin(); if(cb) cb();
      } else {
        document.getElementById('perr').textContent='PIN incorrecto, intentá de nuevo';
        pinBuf=''; refreshDots();
      }
    },160);
  }
}
function refreshDots(){
  for(var i=0;i<4;i++) document.getElementById('d'+i).classList.toggle('on',i<pinBuf.length);
}

// ── ADMIN ────────────────────────────────────────────
function toggleAdmin(){
  if(!adminOn){
    openPin(function(){
      adminOn=true;
      document.body.classList.add('admin');
      document.getElementById('abtn').textContent='✅ Salir de edición';
      document.getElementById('abtn').classList.add('on');
      document.getElementById('addPanel').classList.add('show');
    });
  } else {
    adminOn=false; editId=null;
    document.body.classList.remove('admin');
    document.getElementById('abtn').textContent='✏️ Modo edición';
    document.getElementById('abtn').classList.remove('on');
    document.getElementById('addPanel').classList.remove('show');
    render();
  }
}

// ── AGREGAR ──────────────────────────────────────────
var newUrg='baja';
function selectUrg(u){
  newUrg=u;
  ['baja','media','alta'].forEach(function(x){
    var b=document.getElementById('u'+x.charAt(0).toUpperCase()+x.slice(1));
    if(b){ b.className='urg-opt'+(u===x?' sel-'+x:''); }
  });
}
function setupAddInp(){
  var inp=document.getElementById('newInp');
  var btn=document.getElementById('btnAdd');
  inp.oninput=function(){ btn.disabled=!inp.value.trim(); };
  inp.onkeydown=function(e){ if(e.key==='Enter') addTask(); };
}
function addTask(){
  var inp=document.getElementById('newInp');
  var n=inp.value.trim(); if(!n) return;
  tasks.push({id:Date.now(),name:n,urg:newUrg});
  saveTasks();
  inp.value='';
  document.getElementById('btnAdd').disabled=true;
  // reset urgency selector to baja
  selectUrg('baja');
  render();
}

// ── EDITAR / BORRAR ──────────────────────────────────
function changeUrg(id,u){
  var t=tasks.find(function(t){return t.id===id;});
  if(t){ t.urg=u; saveTasks(); render();
    // reopen card after render
    setTimeout(function(){
      var card=document.querySelector('.tcard[data-id="'+id+'"]');
      if(card) card.classList.add('open');
    },10);
  }
}
function delTask(id){
  if(!confirm('¿Eliminar esta tarea?')) return;
  tasks=tasks.filter(function(t){return t.id!==id;});
  delete state[id]; saveTasks(); saveState(); render();
}
function startEdit(id){
  editId=id; render();
  setTimeout(function(){
    var i=document.getElementById('ei'+id); if(i){i.focus();i.select();}
  },40);
}
function saveEdit(id){
  var i=document.getElementById('ei'+id);
  if(i){ var n=i.value.trim(); if(n){ var t=tasks.find(function(t){return t.id===id;}); if(t) t.name=n; saveTasks(); } }
  editId=null; render();
}
function editKey(e,id){
  if(e.key==='Enter') saveEdit(id);
  if(e.key==='Escape'){editId=null;render();}
}

// ── ABRIR PANEL (sin PIN) ────────────────────────────
function toggleCard(id){
  var card=document.querySelector('.tcard[data-id="'+id+'"]');
  if(!card) return;
  if(card.classList.contains('open')){ card.classList.remove('open'); return; }
  document.querySelectorAll('.tcard.open').forEach(function(c){c.classList.remove('open');});
  card.classList.add('open');
}

// ── FOTO ─────────────────────────────────────────────
function handlePhoto(id, input){
  if(!input.files||!input.files[0]) return;
  var file=input.files[0];
  var reader=new FileReader();
  reader.onload=function(e){
    var b64=e.target.result;
    if(!state[id]) state[id]={};
    state[id].photo=b64;
    saveState();
    showPhoto(id, b64);
  };
  reader.readAsDataURL(file);
}
function showPhoto(id, src){
  var prev=document.getElementById('prev'+id);
  var img=document.getElementById('pimg'+id);
  var rm=document.getElementById('prm'+id);
  if(prev&&img){
    img.src=src;
    img.onload=function(){ prev.style.display='block'; };
    if(img.complete && img.naturalWidth>0) prev.style.display='block';
    if(rm) rm.style.display='inline';
  }
}
function removePhoto(id){
  if(!confirm('¿Eliminar la foto?')) return;
  if(state[id]) delete state[id].photo;
  saveState();
  var prev=document.getElementById('prev'+id);
  var rm=document.getElementById('prm'+id);
  if(prev) prev.style.display='none';
  if(rm) rm.style.display='none';
  var inp=document.getElementById('ph'+id); if(inp) inp.value='';
}

// ── NOTA ─────────────────────────────────────────────
function checkScore(id){
  var inp=document.getElementById('sc'+id);
  var v=parseFloat(inp.value);
  var hint=document.getElementById('hi'+id);
  var btn=document.getElementById('bk'+id);
  var err=document.getElementById('er'+id);
  if(isNaN(v)){
    hint.textContent='Ingresá una nota del 1 al 10'; hint.className='shint';
    if(btn) btn.disabled=true; return;
  }
  if(v<1||v>10){
    hint.textContent='Tiene que ser entre 1 y 10'; hint.className='shint bad';
    if(btn) btn.disabled=true; return;
  }
  if(v>MIN_SCORE){
    hint.textContent='✓ Aprobada'; hint.className='shint ok';
    if(btn) btn.disabled=false;
    if(err) err.style.display='none';
  } else {
    hint.textContent='✗ Necesita más de '+MIN_SCORE; hint.className='shint bad';
    if(btn) btn.disabled=true;
  }
}

function confirmTask(id){
  var score=parseFloat(document.getElementById('sc'+id).value);
  var note=(document.getElementById('nt'+id).value||'').trim();
  var err=document.getElementById('er'+id);
  if(isNaN(score)||score<1||score>10||score<=MIN_SCORE){
    err.style.display='block'; return;
  }
  openPin(function(){
    if(!state[id]) state[id]={};
    state[id].done=true; state[id].score=score; state[id].note=note;
    saveState();
    document.querySelectorAll('.tcard.open').forEach(function(c){c.classList.remove('open');});
    confetti(); render();
  });
}

// ── DESMARCAR ────────────────────────────────────────
function undoTask(id){
  openPin(function(){
    if(!confirm('¿Desmarcar esta tarea?')) return;
    if(state[id]){state[id].done=false; delete state[id].score; delete state[id].note;}
    saveState();
    document.querySelectorAll('.tcard.open').forEach(function(c){c.classList.remove('open');});
    render();
  });
}

// ── RENDER ───────────────────────────────────────────
const URG_ORDER = {alta:0, media:1, baja:2, undefined:3};
function render(){
  var list=document.getElementById('tlist');
  list.innerHTML='';

  // sort: incomplete alta → media → baja, then done at bottom
  var sorted=tasks.slice().sort(function(a,b){
    var da=!!(state[a.id]&&state[a.id].done);
    var db=!!(state[b.id]&&state[b.id].done);
    if(da!==db) return da?1:-1;
    var ua=URG_ORDER[a.urg]!==undefined?URG_ORDER[a.urg]:3;
    var ub=URG_ORDER[b.urg]!==undefined?URG_ORDER[b.urg]:3;
    return ua-ub;
  });

  sorted.forEach(function(task){
    var s=state[task.id]||{};
    var done=!!s.done;
    var isEd=editId===task.id;

    var card=document.createElement('div');
    card.className='tcard'+(done?' done':'');
    card.dataset.id=task.id;
    if(task.urg) card.dataset.urg=task.urg;

    // urgency pill
    var urgLabels={baja:'🟢 Baja',media:'🟡 Media',alta:'🔴 Alta'};
    var pillHtml=task.urg&&!done?'<span class="upill upill-'+task.urg+'">'+urgLabels[task.urg]+'</span>':'';

    // name area
    var nameHtml=isEd
      ?'<input class="edit-inp" id="ei'+task.id+'" value="'+task.name.replace(/"/g,'&quot;')+'" onblur="saveEdit('+task.id+')" onkeydown="editKey(event,'+task.id+')" onclick="event.stopPropagation()">'
      :'<div class="tname">'+task.name+'</div>'+(done?'<div class="tmeta">Nota: '+s.score+'/10'+(s.note?' · '+s.note:'')+'</div>':'');

    // photo thumb on header if done
    var thumbHtml=done&&s.photo?'<img class="photo-thumb" src="'+s.photo+'" alt="foto">':'';

    // score for eval panel
    var sv=s.score!==undefined?s.score:'';
    var hv=sv!==''?(parseFloat(sv)>MIN_SCORE?'✓ Aprobada':'✗ Necesita más de '+MIN_SCORE):'Ingresá una nota del 1 al 10';
    var hc=sv!==''?(parseFloat(sv)>MIN_SCORE?'shint ok':'shint bad'):'shint';
    var bd=sv===''||isNaN(parseFloat(sv))||parseFloat(sv)<=MIN_SCORE||parseFloat(sv)<1||parseFloat(sv)>10;

    var evalHtml='<div class="epanel">'
      // URGENCY inside panel
      +'<label>Urgencia</label>'
      +'<div class="urg-selector" style="margin-bottom:14px">'
      +'<button class="urg-opt'+(task.urg==='baja'?' sel-baja':'')+'" onclick="changeUrg('+task.id+',\'baja\')">🟢 Baja</button>'
      +'<button class="urg-opt'+(task.urg==='media'?' sel-media':'')+'" onclick="changeUrg('+task.id+',\'media\')">🟡 Media</button>'
      +'<button class="urg-opt'+(task.urg==='alta'?' sel-alta':'')+'" onclick="changeUrg('+task.id+',\'alta\')">🔴 Alta</button>'
      +'</div>'
      +'<label>Comentario (opcional)</label>'
      +'<textarea id="nt'+task.id+'" placeholder="Ej: Completó todo correctamente...">'+( s.note||'')+'</textarea>'

      // FOTO
      +'<div class="photo-section">'
      +'<label>Foto o imagen adjunta</label>'
      +'<label class="photo-label-btn">📷 Subir foto<input type="file" id="ph'+task.id+'" accept="image/*" onchange="handlePhoto('+task.id+',this)"></label>'
      +'<div class="photo-preview" id="prev'+task.id+'">'
      +'<img id="pimg'+task.id+'" src="" alt="foto adjunta">'
      +'</div>'
      +'<button class="photo-remove" id="prm'+task.id+'" onclick="removePhoto('+task.id+')">✕ Eliminar foto</button>'
      +'</div>'

      // SCORE
      +'<div class="srow">'
      +'<label for="sc'+task.id+'">Nota</label>'
      +'<input class="sinp" type="number" id="sc'+task.id+'" min="1" max="10" step="0.5" value="'+sv+'" placeholder="1–10" oninput="checkScore('+task.id+')">'
      +'<span class="'+hc+'" id="hi'+task.id+'">'+hv+'</span>'
      +'</div>'
      +'<div class="srange">Escala 1 a 10 · Se aprueba con más de '+MIN_SCORE+'</div>'
      +'<div class="errmsg" id="er'+task.id+'">La nota debe ser mayor a '+MIN_SCORE+' y entre 1 y 10.</div>'

      +(done
        ?'<button class="btn-undo" onclick="undoTask('+task.id+')">↩ Desmarcar tarea</button>'
        :'<button class="btn-ok" id="bk'+task.id+'" onclick="confirmTask('+task.id+')" '+(bd?'disabled':'')+'>Marcar como completado ✓</button>'
      )
      +'</div>';

    card.innerHTML=
      '<div class="thead" onclick="toggleCard('+task.id+')">'
        +'<div class="chk"></div>'
        +'<div class="tinfo">'+nameHtml+'</div>'
        +pillHtml
        +thumbHtml
        +'<button class="be" onclick="event.stopPropagation();startEdit('+task.id+')">✏️</button>'
        +'<button class="bd" onclick="event.stopPropagation();delTask('+task.id+')">🗑</button>'
        +'<div class="chev">▼</div>'
      +'</div>'
      +evalHtml;

    list.appendChild(card);

    // restore photo if saved
    if(s.photo) showPhoto(task.id, s.photo);
  });

  // progress
  var done=tasks.filter(function(t){return state[t.id]&&state[t.id].done;}).length;
  var total=tasks.length;
  var pct=total?Math.round(done/total*100):0;
  document.getElementById('bfill').style.width=pct+'%';
  document.getElementById('blbl').textContent=done+' de '+total+' completadas';
  document.getElementById('badge').classList.toggle('show',total>0&&done===total);
}

// ── CONFETTI ─────────────────────────────────────────
function confetti(){
  var colors=['#7c6af7','#f76a8f','#4ade80','#fbbf24','#38bdf8'];
  for(var i=0;i<30;i++){
    var el=document.createElement('div');
    el.className='cp';
    el.style.left=Math.random()*100+'vw';
    el.style.top='-10px';
    el.style.background=colors[Math.floor(Math.random()*colors.length)];
    el.style.animationDelay=(Math.random()*.5)+'s';
    el.style.animationDuration=(.9+Math.random()*.8)+'s';
    el.style.borderRadius=Math.random()>.5?'50%':'2px';
    document.body.appendChild(el);
    setTimeout(function(){el.remove();},2200);
  }
}

// ── INIT ─────────────────────────────────────────────
setupAddInp();
render();
</script>
</body>
</html>
