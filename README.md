<!DOCTYPE html>
<html lang="it">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover"/>
<meta name="apple-mobile-web-app-capable" content="yes"/>
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent"/>
<meta name="apple-mobile-web-app-title" content="Tipster Pro"/>
<meta name="theme-color" content="#0a0a0f"/>
<title>Tipster Pro</title>
<link rel="manifest" href="data:application/json;charset=utf-8,%7B%22name%22%3A%22Tipster%20Pro%22%2C%22short_name%22%3A%22Tipster%22%2C%22start_url%22%3A%22.%22%2C%22display%22%3A%22standalone%22%2C%22background_color%22%3A%22%230a0a0f%22%2C%22theme_color%22%3A%22%2322c55e%22%7D"/>
<style>
@import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Mono:wght@300;400;500&display=swap');
*{box-sizing:border-box;margin:0;padding:0;-webkit-tap-highlight-color:transparent}
html,body{height:100%;background:#0a0a0f;color:#e2e8f0;font-family:'DM Mono','Courier New',monospace;overscroll-behavior:none}
::-webkit-scrollbar{width:3px}::-webkit-scrollbar-track{background:#0a0a0f}::-webkit-scrollbar-thumb{background:#22c55e44;border-radius:2px}
.tk{font-family:'Bebas Neue',cursive;letter-spacing:.05em}
.glow{text-shadow:0 0 20px #22c55e88}
.card{background:#0f1117;border:1px solid #1e2533;border-radius:12px}
input,select{background:#0a0a0f;border:1px solid #1e2533;color:#e2e8f0;border-radius:8px;padding:11px 14px;font-family:inherit;font-size:14px;outline:none;width:100%;transition:border-color .2s;-webkit-appearance:none}
input:focus,select:focus{border-color:#22c55e66}
select{background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='12' viewBox='0 0 12 12'%3E%3Cpath fill='%2364748b' d='M6 8L1 3h10z'/%3E%3C/svg%3E");background-repeat:no-repeat;background-position:right 12px center;padding-right:32px}
.btn{border:none;border-radius:10px;padding:12px 20px;cursor:pointer;font-family:inherit;font-size:12px;font-weight:600;transition:all .2s;letter-spacing:.08em;text-transform:uppercase;-webkit-appearance:none}
.btng{background:#22c55e;color:#0a0a0f}
.btng:active{background:#16a34a;transform:scale(.97)}
.btns{background:transparent;color:#64748b;border:1px solid #1e2533}
.btns:active{background:#ffffff08}
.tag{display:inline-flex;align-items:center;padding:3px 10px;border-radius:20px;font-size:10px;font-weight:600;letter-spacing:.06em}
.pb{height:8px;background:#1e2533;border-radius:4px;overflow:hidden}
.pbf{height:100%;background:linear-gradient(90deg,#22c55e,#86efac);border-radius:4px;transition:width 1.2s cubic-bezier(.4,0,.2,1);position:relative;overflow:hidden}
.pbf::after{content:'';position:absolute;top:0;left:-100%;width:100%;height:100%;background:linear-gradient(90deg,transparent,rgba(255,255,255,.25),transparent);animation:sh 2.5s infinite}
@keyframes sh{to{left:100%}}
@keyframes pulse{0%,100%{opacity:1}50%{opacity:.35}}
@keyframes fadeup{from{opacity:0;transform:translateY(10px)}to{opacity:1;transform:translateY(0)}}
.fadeup{animation:fadeup .3s ease-out}
.overlay{position:fixed;inset:0;background:rgba(0,0,0,.8);backdrop-filter:blur(8px);-webkit-backdrop-filter:blur(8px);z-index:100;display:flex;align-items:flex-end;justify-content:center;padding:0}
.modal{background:#0f1117;border:1px solid #22c55e22;border-radius:20px 20px 0 0;padding:24px 20px 40px;width:100%;max-width:600px;max-height:92vh;overflow-y:auto}
.modal-handle{width:40px;height:4px;background:#1e2533;border-radius:2px;margin:0 auto 20px}
.lbl{font-size:10px;color:#64748b;letter-spacing:.12em;text-transform:uppercase;margin-bottom:6px}
.g2{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.section{padding:0 16px 24px}

/* BOTTOM NAV */
.bnav{position:fixed;bottom:0;left:0;right:0;background:#0c0e14;border-top:1px solid #1e2533;display:flex;z-index:50;padding-bottom:env(safe-area-inset-bottom)}
.bnav-btn{flex:1;display:flex;flex-direction:column;align-items:center;justify-content:center;padding:10px 0;cursor:pointer;border:none;background:transparent;color:#475569;font-family:inherit;font-size:9px;letter-spacing:.08em;text-transform:uppercase;gap:4px;transition:color .2s}
.bnav-btn.active{color:#22c55e}
.bnav-btn .ico{font-size:20px;line-height:1}

/* HEADER */
.header{background:linear-gradient(180deg,#0f1117,#0a0a0f);border-bottom:1px solid #1e2533;padding:16px 16px 12px;padding-top:calc(16px + env(safe-area-inset-top))}

/* CONTENT */
.content{padding-bottom:calc(80px + env(safe-area-inset-bottom));min-height:100vh}

/* STAT GRID */
.stat-grid{display:grid;grid-template-columns:1fr 1fr;gap:10px;padding:0 16px;margin-bottom:12px}
.stat-card{background:#0f1117;border:1px solid #1e2533;border-radius:12px;padding:16px}

/* BET ROW */
.bet-row{padding:14px 16px;border-bottom:1px solid #1e253866}
.bet-row:last-child{border-bottom:none}
.bet-row:active{background:#ffffff03}
.action-btn{border:none;border-radius:8px;padding:8px 14px;font-family:inherit;font-size:11px;font-weight:700;cursor:pointer;letter-spacing:.06em}

/* TOAST */
.toast{position:fixed;top:calc(20px + env(safe-area-inset-top));left:50%;transform:translateX(-50%);background:#22c55e;color:#0a0a0f;padding:10px 20px;border-radius:20px;font-size:12px;font-weight:700;letter-spacing:.06em;z-index:200;animation:fadeup .3s ease-out;white-space:nowrap}
</style>
</head>
<body>

<div id="app"></div>

<script>
// ── DATA ──────────────────────────────────────────────────────────────────────
const GOAL = 150000;
const BASE_BK = 1000;
const CATS = {Calcio:"#22c55e",Tennis:"#f59e0b",Basket:"#f97316",Horse:"#8b5cf6","MMA/UFC":"#ef4444",Altro:"#64748b"};
const SAMPLE = [
  {id:1,date:"2025-01-10",description:"Juventus vs Milan — 1X",category:"Calcio",stake:200,odds:1.85,result:"win",matchDate:"",matchTime:""},
  {id:2,date:"2025-01-15",description:"Sinner vs Djokovic — Sinner",category:"Tennis",stake:500,odds:2.1,result:"win",matchDate:"",matchTime:""},
  {id:3,date:"2025-01-20",description:"Inter vs Napoli — Over 2.5",category:"Calcio",stake:300,odds:1.7,result:"loss",matchDate:"",matchTime:""},
  {id:4,date:"2025-02-05",description:"Lakers vs Warriors — Lakers",category:"Basket",stake:400,odds:2.4,result:"win",matchDate:"",matchTime:""},
  {id:5,date:"2025-02-18",description:"Roma vs Lazio — BTTS",category:"Calcio",stake:250,odds:1.9,result:"loss",matchDate:"",matchTime:""},
];

const fmt = n => new Intl.NumberFormat("it-IT",{style:"currency",currency:"EUR",minimumFractionDigits:2}).format(n);
const fmtDate = d => new Date(d).toLocaleDateString("it-IT",{day:"2-digit",month:"short",year:"numeric"});
const fmtCountdown = ms => {
  if(ms<=0) return "ORA IN CAMPO";
  const s=Math.floor(ms/1000),m=Math.floor(s/60)%60,h=Math.floor(s/3600)%24,d=Math.floor(s/86400);
  if(d>0) return `${d}g ${h}h ${m}m`;
  if(h>0) return `${h}h ${m}m`;
  return `${m}m ${s%60}s`;
};

// ── STATE ─────────────────────────────────────────────────────────────────────
let state = {
  bets: [],
  tab: 0, // 0=dashboard 1=scommesse 2=aggiungi
  filter: "all",
  showForm: false,
  editId: null,
  form: emptyForm(),
  toast: null,
  timers: {},
};

function emptyForm(){
  return {date:new Date().toISOString().split("T")[0],description:"",category:"Calcio",stake:"",odds:"",result:"pending",matchDate:"",matchTime:""};
}

// ── STORAGE ───────────────────────────────────────────────────────────────────
function load(){
  try{
    const raw = localStorage.getItem("tipster-bets-v2");
    if(raw){ const p=JSON.parse(raw); if(Array.isArray(p)&&p.length) return p; }
  }catch(_){}
  return [...SAMPLE];
}
function save(bets){
  try{ localStorage.setItem("tipster-bets-v2",JSON.stringify(bets)); }catch(_){}
}

state.bets = load();

// ── STATS ─────────────────────────────────────────────────────────────────────
function calcStats(bets){
  const closed=bets.filter(b=>b.result!=="pending");
  const staked=closed.reduce((s,b)=>s+b.stake,0);
  const ret=closed.reduce((s,b)=>b.result==="win"?s+b.stake*b.odds:s,0);
  const net=ret-staked;
  const wins=closed.filter(b=>b.result==="win").length;
  const losses=closed.filter(b=>b.result==="loss").length;
  const pending=bets.filter(b=>b.result==="pending").length;
  const roi=staked>0?((net/staked)*100).toFixed(2):0;
  const wr=closed.length>0?((wins/closed.length)*100).toFixed(1):0;
  const bankroll=BASE_BK+net;
  const progress=Math.min((Math.max(bankroll,0)/GOAL)*100,100);
  const pendStake=bets.filter(b=>b.result==="pending").reduce((s,b)=>s+b.stake,0);
  const pendPot=bets.filter(b=>b.result==="pending").reduce((s,b)=>s+b.stake*(b.odds-1),0);
  return{staked,net,wins,losses,pending,roi,wr,bankroll,progress,pendStake,pendPot,total:bets.length};
}

// ── COUNTDOWN TIMERS ──────────────────────────────────────────────────────────
let countdownInterval = null;
function startCountdowns(){
  if(countdownInterval) clearInterval(countdownInterval);
  countdownInterval = setInterval(()=>{
    const hasPending = state.bets.some(b=>b.result==="pending"&&b.matchDate);
    if(hasPending) render();
  },1000);
}
startCountdowns();

// ── TOAST ─────────────────────────────────────────────────────────────────────
function showToast(msg){
  state.toast=msg;
  render();
  setTimeout(()=>{state.toast=null;render();},2500);
}

// ── ACTIONS ───────────────────────────────────────────────────────────────────
function setResult(id,result){
  state.bets=state.bets.map(b=>b.id===id?{...b,result}:b);
  save(state.bets);
  showToast(result==="win"?"✓ WIN registrato!":"✗ LOSS registrato");
}
function deleteBet(id){
  if(!confirm("Eliminare questa scommessa?")) return;
  state.bets=state.bets.filter(b=>b.id!==id);
  save(state.bets);
  render();
}
function editBet(bet){
  state.form={...bet,stake:String(bet.stake),odds:String(bet.odds)};
  state.editId=bet.id;
  state.showForm=true;
  render();
}
function submitForm(){
  const f=state.form;
  if(!f.description||!f.stake||!f.odds) return;
  const entry={...f,stake:+f.stake,odds:+f.odds};
  if(state.editId!==null){
    state.bets=state.bets.map(b=>b.id===state.editId?{...entry,id:state.editId}:b);
  }else{
    state.bets=[...state.bets,{...entry,id:Date.now()}];
  }
  save(state.bets);
  state.form=emptyForm();
  state.editId=null;
  state.showForm=false;
  showToast(state.editId!==null?"✓ Scommessa aggiornata":"✓ Scommessa aggiunta");
}
function closeForm(){
  state.showForm=false;
  state.editId=null;
  state.form=emptyForm();
  render();
}

// ── RENDER ────────────────────────────────────────────────────────────────────
function render(){
  const app=document.getElementById("app");
  app.innerHTML="";
  app.appendChild(buildApp());
  // Attach events after render
  attachEvents();
}

function buildApp(){
  const frag=document.createDocumentFragment();
  frag.appendChild(buildHeader());
  frag.appendChild(buildContent());
  frag.appendChild(buildBottomNav());
  if(state.showForm) frag.appendChild(buildModal());
  if(state.toast){
    const t=el("div","toast",state.toast);
    frag.appendChild(t);
  }
  return frag;
}

// ── HEADER ────────────────────────────────────────────────────────────────────
function buildHeader(){
  const stats=calcStats(state.bets);
  const h=el("div","header");
  const row=el("div","","",[["display","flex"],["justifyContent","space-between"],["alignItems","center"]]);
  const left=el("div");
  left.appendChild(el("div","tk glow","TIPSTER PRO",[["fontSize","28px"],["color","#22c55e"],["lineHeight","1"]]));
  left.appendChild(el("div","","BANKROLL TRACKER",[["fontSize","9px"],["color","#334155"],["letterSpacing",".18em"],["marginTop","3px"]]));
  const right=el("div","",[["display","flex"],["gap","12px"],["alignItems","center"]]);
  const bkDiv=el("div","",[["textAlign","right"]]);
  bkDiv.appendChild(el("div","","BANKROLL",[["fontSize","9px"],["color","#475569"],["letterSpacing",".1em"]]));
  bkDiv.appendChild(el("div","tk",fmt(stats.bankroll),[["fontSize","20px"],["color",stats.bankroll>=BASE_BK?"#22c55e":"#ef4444"]]));
  const goalDiv=el("div","",[["textAlign","right"]]);
  goalDiv.appendChild(el("div","","GOAL",[["fontSize","9px"],["color","#475569"],["letterSpacing",".1em"]]));
  goalDiv.appendChild(el("div","tk glow",stats.progress.toFixed(1)+"%",[["fontSize","20px"],["color","#f59e0b"]]));
  right.appendChild(bkDiv);
  right.appendChild(goalDiv);
  row.appendChild(left);
  row.appendChild(right);
  h.appendChild(row);
  if(stats.pending>0){
    const pill=el("div","","● "+stats.pending+" PENDING",[["fontSize","10px"],["color","#f59e0b"],["background","#f59e0b11"],["border","1px solid #f59e0b33"],["borderRadius","8px"],["padding","5px 12px"],["marginTop","10px"],["display","inline-block"],["letterSpacing",".08em"],["animation","pulse 1.5s infinite"]]);
    h.appendChild(pill);
  }
  return h;
}

// ── CONTENT ───────────────────────────────────────────────────────────────────
function buildContent(){
  const div=el("div","content fadeup");
  if(state.tab===0) div.appendChild(buildDashboard());
  else if(state.tab===1) div.appendChild(buildBetList());
  else if(state.tab===2) div.appendChild(buildAddForm());
  return div;
}

// ── DASHBOARD ─────────────────────────────────────────────────────────────────
function buildDashboard(){
  const stats=calcStats(state.bets);
  const div=el("div");

  // Goal bar
  const goalCard=el("div","card",[["margin","16px"],["padding","20px"],["borderColor","#22c55e22"]]);
  const goalTop=el("div","",[["display","flex"],["justifyContent","space-between"],["alignItems","flex-end"],["marginBottom","12px"]]);
  const goalLeft=el("div");
  goalLeft.appendChild(el("div","","PROGRESSO OBIETTIVO",[["fontSize","9px"],["color","#475569"],["letterSpacing",".12em"],["marginBottom","6px"]]));
  goalLeft.appendChild(el("div","tk",fmt(Math.max(stats.bankroll,0)),[["fontSize","20px"]]));
  goalLeft.appendChild(el("div","","/ "+fmt(GOAL),[["fontSize","11px"],["color","#334155"],["marginTop","2px"]]));
  const pctEl=el("div","tk glow",stats.progress.toFixed(1)+"%",[["fontSize","40px"],["color","#22c55e"]]);
  goalTop.appendChild(goalLeft);
  goalTop.appendChild(pctEl);
  goalCard.appendChild(goalTop);
  const pb=el("div","pb");
  const pbf=el("div","pbf");
  pbf.style.width=stats.progress+"%";
  pb.appendChild(pbf);
  goalCard.appendChild(pb);
  goalCard.appendChild(el("div","","Mancano "+fmt(Math.max(GOAL-stats.bankroll,0))+" al traguardo",[["fontSize","11px"],["color","#475569"],["marginTop","8px"]]));
  div.appendChild(goalCard);

  // Stat grid
  const sg=el("div","stat-grid");
  [
    {label:"P/L Netto",value:(stats.net>=0?"+":"")+fmt(stats.net),color:stats.net>=0?"#22c55e":"#ef4444"},
    {label:"ROI",value:(+stats.roi>=0?"+":"")+stats.roi+"%",color:+stats.roi>=0?"#22c55e":"#ef4444"},
    {label:"Win Rate",value:stats.wr+"%",color:"#f59e0b"},
    {label:"Pending",value:String(stats.pending),color:"#f59e0b"},
  ].forEach(s=>{
    const sc=el("div","stat-card");
    sc.appendChild(el("div","",s.label,[["fontSize","9px"],["color","#475569"],["letterSpacing",".12em"],["textTransform","uppercase"],["marginBottom","8px"]]));
    sc.appendChild(el("div","tk",s.value,[["fontSize","24px"],["color",s.color],["lineHeight","1"]]));
    sg.appendChild(sc);
  });
  div.appendChild(sg);

  // Wins/Losses
  const wl=el("div","stat-grid");
  [{label:"Vittorie",val:stats.wins,col:"#22c55e",sub:"vinte"},{label:"Sconfitte",val:stats.losses,col:"#ef4444",sub:"perse"}].forEach(s=>{
    const sc=el("div","stat-card",[["display","flex"],["alignItems","center"],["gap","14px"]]);
    sc.appendChild(el("div","tk",String(s.val),[["fontSize","40px"],["color",s.col],["lineHeight","1"]]));
    const info=el("div");
    info.appendChild(el("div","",s.label,[["fontSize","13px"]]));
    info.appendChild(el("div","",s.sub,[["fontSize","11px"],["color","#475569"]]));
    sc.appendChild(info);
    wl.appendChild(sc);
  });
  div.appendChild(wl);

  // Pending section
  if(stats.pending>0){
    const pCard=el("div","card",[["margin","0 16px 16px"],["borderColor","#f59e0b44"],["overflow","hidden"]]);
    const pHead=el("div","",[["padding","12px 16px"],["borderBottom","1px solid #f59e0b22"],["display","flex"],["justifyContent","space-between"],["alignItems","center"],["flexWrap","wrap"],["gap","6px"]]);
    pHead.appendChild(el("div","","⏳ "+stats.pending+" SCOMMESSE PENDING",[["fontSize","10px"],["color","#f59e0b"],["letterSpacing",".1em"]]));
    pHead.appendChild(el("div","","Pot. +"+fmt(stats.pendPot),[["fontSize","11px"],["color","#22c55e"]]));
    pCard.appendChild(pHead);
    state.bets.filter(b=>b.result==="pending").forEach(b=>pCard.appendChild(buildBetRow(b)));
    div.appendChild(pCard);
  }

  return div;
}

// ── BET LIST ──────────────────────────────────────────────────────────────────
function buildBetList(){
  const div=el("div");

  // Filter bar
  const fb=el("div","",[["display","flex"],["gap","6px"],["padding","14px 16px 10px"],["overflowX","auto"]]);
  ["all","pending","win","loss"].forEach(f=>{
    const isActive=state.filter===f;
    const bg=isActive?(f==="win"?"#22c55e":f==="loss"?"#ef4444":f==="pending"?"#f59e0b":"#1e2533"):"transparent";
    const col=isActive?(f==="all"?"#e2e8f0":"#0a0a0f"):"#64748b";
    const label=f==="all"?"Tutte":f==="win"?"✓ Vinte":f==="loss"?"✗ Perse":"⏳ Pending";
    const btn=el("button","btn",label,[["background",bg],["color",col],["border","1px solid "+(isActive?"transparent":"#1e2533")],["padding","7px 14px"],["fontSize","10px"],["borderRadius","8px"],["flexShrink","0"]]);
    btn.dataset.filter=f;
    fb.appendChild(btn);
  });
  div.appendChild(fb);

  // List
  const listCard=el("div","card",[["margin","0 16px"],["overflow","hidden"]]);
  const filtered=state.filter==="all"?[...state.bets]:state.bets.filter(b=>b.result===state.filter);
  if(filtered.length===0){
    listCard.appendChild(el("div","","Nessuna scommessa",[["padding","40px"],["textAlign","center"],["color","#475569"],["fontSize","13px"]]));
  } else {
    [...filtered].reverse().forEach(b=>listCard.appendChild(buildBetRow(b)));
  }
  div.appendChild(listCard);
  div.appendChild(el("div","","DATI SALVATI • "+state.bets.length+" SCOMMESSE",[["textAlign","center"],["fontSize","9px"],["color","#1e293b"],["padding","14px"],["letterSpacing",".12em"]]));
  return div;
}

// ── BET ROW ───────────────────────────────────────────────────────────────────
function buildBetRow(bet){
  const isPending=bet.result==="pending";
  const catColor=CATS[bet.category]||"#64748b";
  const profit=bet.result==="win"?bet.stake*(bet.odds-1):bet.result==="loss"?-bet.stake:null;

  // Countdown
  let countdown=null,isLive=false;
  if(isPending&&bet.matchDate){
    const target=new Date(`${bet.matchDate}T${bet.matchTime||"00:00"}:00`);
    const diff=target-Date.now();
    countdown=Math.max(diff,0);
    isLive=diff<=0;
  }

  const row=el("div","bet-row");

  // Tags
  const tags=el("div","",[["display","flex"],["gap","6px"],["marginBottom","7px"],["flexWrap","wrap"],["alignItems","center"]]);
  const catTag=el("span","tag",bet.category,[["background",catColor+"22"],["color",catColor],["border","1px solid "+catColor+"44"]]);
  const resColor=bet.result==="win"?"#22c55e":bet.result==="loss"?"#ef4444":isLive?"#ef4444":"#f59e0b";
  const resLabel=bet.result==="win"?"✓ WIN":bet.result==="loss"?"✗ LOSS":isLive?"🔴 LIVE":"⏳ PENDING";
  const resTag=el("span","tag",resLabel,[["background",resColor+"11"],["color",resColor],["border","1px solid "+resColor+"33"]]);
  const dateEl=el("span","",fmtDate(bet.date),[["fontSize","10px"],["color","#475569"]]);
  tags.appendChild(catTag);tags.appendChild(resTag);tags.appendChild(dateEl);
  row.appendChild(tags);

  // Description
  row.appendChild(el("div","",bet.description,[["fontSize","14px"],["color","#cbd5e1"],["marginBottom","5px"]]));

  // Meta
  const meta=el("div","",[["fontSize","11px"],["color","#475569"]]);
  meta.innerHTML=`Stake: <span style="color:#94a3b8">${fmt(bet.stake)}</span> | Quota: <span style="color:#94a3b8">${bet.odds.toFixed(2)}</span
