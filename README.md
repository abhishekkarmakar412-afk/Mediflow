# Mediflow
Medical appoitment website 
<!doctype html>
<html lang="en"><head><meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>MediFlow</title>
<link rel="preconnect" href="https://fonts.googleapis.com"><link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Figtree:wght@400;500;600;700&display=swap" rel="stylesheet">
<style>
:root{--bg:#fff;--surf:#f3faf8;--ink:#12302b;--mut:#5c7771;--line:#d6e7e3;--acc:#0f766e;--on:#fff;--soft:#d9f1ea;--warn:#92400e;--warnbg:#fef3c7;--bad:#b91c1c;color-scheme:light;box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media(prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#0c1a18;--surf:#12251f;--ink:#e3f3ef;--mut:#92b0a9;--line:#244039;--acc:#2dd4bf;--on:#06201c;--soft:#15403a;--warn:#fcd34d;--warnbg:#3a2e0a;--bad:#f87171;color-scheme:dark}}
:root[data-theme="dark"]{--bg:#0c1a18;--surf:#12251f;--ink:#e3f3ef;--mut:#92b0a9;--line:#244039;--acc:#2dd4bf;--on:#06201c;--soft:#15403a;--warn:#fcd34d;--warnbg:#3a2e0a;--bad:#f87171;color-scheme:dark}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
*{box-sizing:border-box}body{margin:0;background:var(--bg);color:var(--ink);font:16px/1.5 Figtree,system-ui,sans-serif}
header{border-bottom:1px solid var(--line);position:sticky;top:env(safe-area-inset-top,0px);background:var(--bg);z-index:5}
.bar{max-width:880px;margin:auto;padding:12px 16px;display:flex;gap:12px;align-items:center;flex-wrap:wrap}
.logo{font-weight:700;font-size:20px;color:var(--acc);margin-right:auto}
nav{display:flex;gap:4px}nav a{padding:8px 14px;border-radius:99px;color:var(--mut);text-decoration:none;font-weight:500}
nav a.on{background:var(--soft);color:var(--ink)}
main{max-width:880px;margin:auto;padding:20px 16px 48px}
h1{font-size:26px;line-height:1.2;margin:0 0 4px}h2{font-size:18px;margin:0 0 10px}p{margin:0 0 12px}.mut{color:var(--mut)}
.card{border:1px solid var(--line);border-radius:16px;padding:18px;margin-bottom:16px;background:var(--bg)}
.card.tint{background:var(--surf)}
.slots{display:grid;grid-template-columns:repeat(auto-fill,minmax(96px,1fr));gap:8px}
button,.btn{font:inherit;cursor:pointer;border-radius:10px;border:1px solid var(--line);background:var(--bg);color:var(--ink);padding:9px 14px;min-height:44px}
button:hover{border-color:var(--acc)}button:focus-visible,input:focus-visible,select:focus-visible,a:focus-visible{outline:3px solid var(--acc);outline-offset:2px}
button.on{background:var(--acc);color:var(--on);border-color:var(--acc)}button.pri{background:var(--acc);color:var(--on);border-color:var(--acc);font-weight:600}
button:disabled{opacity:.45;cursor:not-allowed}
button.sm{min-height:36px;padding:5px 11px;font-size:14px}
label{display:block;font-weight:500;margin:12px 0 4px}
input,select{font:inherit;width:100%;padding:10px 12px;border-radius:10px;border:1px solid var(--line);background:var(--bg);color:var(--ink);min-height:44px}
.row{display:flex;gap:10px;flex-wrap:wrap;align-items:center}.row>*{flex:1 1 150px}.row .fit{flex:0 0 auto}
.chk{display:flex;gap:10px;align-items:flex-start;font-weight:400}.chk input{width:22px;min-height:22px;margin-top:3px}
.badge{display:inline-block;padding:2px 10px;border-radius:99px;font-size:13px;font-weight:600;background:var(--soft);color:var(--ink)}
.badge.w{background:var(--warnbg);color:var(--warn)}.badge.x{background:transparent;border:1px solid var(--line);color:var(--mut)}
.big{font-size:44px;font-weight:700;line-height:1;color:var(--acc)}
.grid3{display:grid;grid-template-columns:repeat(auto-fit,minmax(150px,1fr));gap:12px}
.item{display:flex;gap:12px;align-items:center;justify-content:space-between;flex-wrap:wrap;padding:12px 0;border-top:1px solid var(--line)}
.item:first-child{border-top:0}.acts{display:flex;gap:6px;flex-wrap:wrap}
.note{font-size:14px;color:var(--mut);border-left:3px solid var(--line);padding-left:12px;margin-top:24px}
.err{color:var(--bad);font-size:14px;margin-top:8px}
.nums{display:flex;gap:20px;flex-wrap:wrap}.nums div{min-width:110px}.nums b{display:block;font-size:24px}
</style></head>
<body>
<header><div class="bar"><span class="logo">MediFlow</span>
<nav aria-label="Main"><a href="#book" id="n-book">Book</a><a href="#track" id="n-track">Track</a><a href="#reception" id="n-reception">Reception</a></nav></div></header>
<main id="app"></main>
<script>
const K="mediflow-demo-v1",MIN=6e4;
let S=load();
function load(){try{const s=JSON.parse(localStorage.getItem(K));if(s&&s.a)return s}catch(e){}return{a:[],n:0,doc:false,avg:15,me:null}}
function save(){try{localStorage.setItem(K,JSON.stringify(S))}catch(e){}}
const $=s=>document.querySelector(s),esc=t=>String(t).replace(/[&<>"']/g,c=>({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;"}[c]));
const tm=t=>new Date(t).toLocaleTimeString([],{hour:"numeric",minute:"2-digit"});
const LABEL={bk:"Booked",arr:"Waiting",in:"In consultation",done:"Completed",abs:"Absent",can:"Cancelled"};
function slots(){const b=Math.ceil(Date.now()/9e5)*9e5,o=[];for(let i=0;o.length<12;i++){const t=b+i*9e5;if(new Date(t).getHours()===13)continue;o.push(t)}return o}
function lunch(s,avg){const d=new Date(s),a=new Date(d).setHours(13,0,0,0),b=new Date(d).setHours(14,0,0,0);return(s<b&&s+avg>a)?b:s}
const rank=x=>x.st==="arr"?{emergency:0,priority:1,normal:2}[x.pr]:2;
function compute(){const now=Date.now(),avg=S.avg*MIN,out={},sd1=(avg*.25)**2;let sd=0;
 const cur=S.a.find(x=>x.st==="in");
 const pend=S.a.filter(x=>x.st==="arr"||(x.st==="bk"&&now-x.slot<=15*MIN)).sort((p,q)=>rank(p)-rank(q)||(p.slot||p.arrived)-(q.slot||q.arrived));
 let c=S.doc?now:now+10*MIN;
 if(cur){const r=Math.max(avg-(now-cur.started),3*MIN);c=now+r;sd=sd1*Math.min(1,r/avg);out[cur.id]={pos:0,ahead:0,lo:0,hi:0,s:cur.started,e:c,state:"in"}}
 pend.forEach((x,i)=>{let s=c;if(x.st==="bk"&&x.slot>s)s=x.slot;s=lunch(s,avg);const e=s+avg,w=Math.max(0,(s-now)/MIN),sp=Math.sqrt(sd)/MIN;
  out[x.id]={pos:i+1+(cur?1:0),ahead:i+(cur?1:0),lo:Math.max(0,Math.round(w-sp)),hi:Math.round(w+sp),s,e,state:!S.doc?"nodoc":x.st};sd+=sd1;c=e});
 return out}
function act(id,a){const x=S.a.find(y=>y.id===id);if(!x)return;const now=Date.now();
 if(a==="arr"){x.st="arr";x.arrived=now}
 if(a==="in"){if(S.a.some(y=>y.st==="in"))return alert("Complete the current consultation first.");x.st="in";x.started=now}
 if(a==="done"){x.st="done";const m=(now-x.started)/MIN;if(m>=1&&m<=120){S.hist=(S.hist||[]).concat(m).slice(-30);const h=S.hist;S.avg=Math.round(((h.reduce((p,q)=>p+q,0)+15*5)/(h.length+5))*10)/10}}
 if(a==="abs")x.st="abs";if(a==="can")x.st="can";save();render()}
function addWalk(name,pr){const now=Date.now();S.n++;S.a.push({id:"w"+now,no:S.n,name,mobile:"",st:"arr",pr,slot:null,arrived:now,walk:1});save();render()}
function book(slot,name,mobile){S.n++;const x={id:"a"+Date.now(),no:S.n,name,mobile,st:"bk",pr:"normal",slot};S.a.push(x);S.me=x.id;save();location.hash="#track"}
function badge(st){return`<span class="badge ${st==="arr"?"w":st==="done"||st==="abs"||st==="can"?"x":""}">${LABEL[st]}</span>`}

let pick=null;
function vBook(){const taken=new Set(S.a.filter(x=>x.slot&&x.st!=="can"&&x.st!=="abs").map(x=>x.slot));
 return`<h1>Book a visit</h1><p class="mut">No app and no account. You get a personal link to follow your place in line.</p>
 <div class="card tint"><h2>Demo Family Clinic</h2><p class="mut" style="margin:0">Dr. Asha Rao, General Physician · Today · Lunch break 1:00–2:00 PM</p></div>
 <div class="card"><h2>Choose a time</h2><div class="slots" role="group" aria-label="Available times">${slots().map(t=>`<button data-slot="${t}" class="${pick===t?"on":""}" ${taken.has(t)?"disabled":""}>${tm(t)}</button>`).join("")}</div>
 <label for="nm">Full name</label><input id="nm" autocomplete="name">
 <label for="mb">Mobile number</label><input id="mb" inputmode="numeric" autocomplete="tel" placeholder="10 digits">
 <label class="chk" style="margin-top:16px"><input type="checkbox" id="cs"><span>I agree to receive WhatsApp updates about this appointment.</span></label>
 <p class="err" id="er" role="alert"></p><button class="pri" id="go" style="width:100%;margin-top:8px">Confirm booking</button></div>`}
function bindBook(){document.querySelectorAll("[data-slot]").forEach(b=>b.onclick=()=>{pick=+b.dataset.slot;render()});
 $("#go").onclick=()=>{const n=$("#nm").value.trim(),m=$("#mb").value.replace(/\D/g,""),e=$("#er");
  if(!pick)return e.textContent="Choose a time first.";if(n.length<2)return e.textContent="Enter your full name.";
  if(m.length!==10)return e.textContent="Enter a 10-digit mobile number.";if(!$("#cs").checked)return e.textContent="Please tick the consent box to continue.";
  if(S.a.some(x=>x.slot===pick&&x.st!=="can"&&x.st!=="abs"))return e.textContent="That time was just taken. Pick another.";
  const p=pick;pick=null;book(p,n,m)}}

function vTrack(){const x=S.a.find(y=>y.id===S.me);
 if(!x)return`<h1>Track your place</h1><p class="mut">Enter your appointment number and the last 4 digits of your mobile.</p><div class="card"><div class="row"><div><label for="tn">Appointment number</label><input id="tn" inputmode="numeric"></div><div><label for="t4">Last 4 digits</label><input id="t4" inputmode="numeric" maxlength="4"></div></div><p class="err" id="er" role="alert"></p><button class="pri" id="tg">Find my appointment</button></div>`;
 const q=compute()[x.id],pad=String(x.no).padStart(2,"0");
 let body;
 if(!q)body=`<p>${x.st==="done"?"Your consultation is complete. Thank you for visiting.":x.st==="can"?"This appointment was cancelled.":"You are no longer in today’s queue. Please speak to reception."}</p>`;
 else if(q.state==="in")body=`<p class="big" style="font-size:30px">It’s your turn</p><p class="mut">Your consultation is in progress.</p>`;
 else body=`<div class="nums"><div><span class="mut">People ahead</span><b>${q.ahead}</b></div><div><span class="mut">Estimated wait</span><b>${q.lo===q.hi?q.hi:q.lo+"–"+q.hi} min</b></div><div><span class="mut">Estimated time</span><b>${tm(q.s)}–${tm(q.e)}</b></div></div>
 ${x.st==="bk"?`<p class="mut" style="margin-top:14px">Please arrive by ${tm(x.slot-10*MIN)} and tell reception your number.</p>`:""}`;
 return`<h1>Your appointment</h1><div class="card tint"><div class="row" style="justify-content:space-between"><div class="fit"><span class="mut">Appointment number</span><div class="big">${pad}</div></div><div class="fit">${badge(x.st)}</div></div></div>
 <div class="card">${body}</div>
 <div class="card"><div class="row"><div><b>Doctor</b><br>${S.doc?"Has arrived":"Not checked in yet"}</div><div><b>Clinic</b><br>${S.avg>18?"Running slower than usual":"On schedule"}</div></div></div>
 <button id="lo" class="sm">Look up a different appointment</button>`}
function bindTrack(){const g=$("#tg");if(g)g.onclick=()=>{const no=+$("#tn").value,l=$("#t4").value,x=S.a.find(y=>y.no===no&&y.mobile.slice(-4)===l);if(!x)return $("#er").textContent="No match. Check the number and the last 4 digits.";S.me=x.id;save();render()};
 const l=$("#lo");if(l)l.onclick=()=>{S.me=null;save();render()}}

let q="";
function vRec(){const Q=compute(),list=S.a.filter(x=>(x.name+x.mobile+x.no).toLowerCase().includes(q.toLowerCase()));
 const ord=a=>a.st==="in"?0:a.st==="arr"?1:a.st==="bk"?2:3;list.sort((a,b)=>ord(a)-ord(b)||(Q[a.id]?.pos??99)-(Q[b.id]?.pos??99)||a.no-b.no);
 const wait=S.a.filter(x=>x.st==="arr").length,inn=S.a.find(x=>x.st==="in");
 return`<h1>Reception</h1>
 <div class="card tint"><div class="row"><div><b>Dr. Asha Rao</b><br><span class="mut">${S.doc?"Checked in":"Not checked in"}</span></div><div class="fit"><button id="dc" class="${S.doc?"":"pri"}">${S.doc?"Check out doctor":"Check in doctor"}</button></div></div>
 <div class="nums" style="margin-top:12px"><div><span class="mut">Waiting</span><b>${wait}</b></div><div><span class="mut">In consultation</span><b>${inn?"#"+String(inn.no).padStart(2,"0"):"None"}</b></div><div><span class="mut">Avg. visit</span><b>${S.avg} min</b></div></div></div>
 <div class="card"><h2>Add walk-in</h2><div class="row"><input id="wn" placeholder="Patient name" aria-label="Patient name"><select id="wp" class="fit" aria-label="Priority"><option value="normal">Normal</option><option value="priority">Priority</option><option value="emergency">Emergency</option></select><button id="wa" class="pri fit">Add to queue</button></div></div>
 <div class="card"><div class="row"><h2 style="flex:0 0 auto;margin:0">Today’s patients</h2><input id="sq" value="${esc(q)}" placeholder="Search name, mobile or number" aria-label="Search"></div>
 ${list.length?list.map(x=>{const r=Q[x.id];return`<div class="item"><div><b>#${String(x.no).padStart(2,"0")} ${esc(x.name)}</b> ${badge(x.st)}${x.pr!=="normal"?` <span class="badge w">${x.pr}</span>`:""}<br><span class="mut" style="font-size:14px">${x.slot?tm(x.slot):"Walk-in"}${x.mobile?" · "+esc(x.mobile):""}${r&&r.state!=="in"?` · ${r.ahead} ahead · about ${tm(r.s)}`:""}</span></div>
 <div class="acts">${x.st==="bk"?`<button class="sm pri" data-a="arr" data-id="${x.id}">Arrived</button><button class="sm" data-a="abs" data-id="${x.id}">Absent</button><button class="sm" data-a="can" data-id="${x.id}">Cancel</button>`:""}${x.st==="arr"?`<button class="sm pri" data-a="in" data-id="${x.id}">Start</button><button class="sm" data-a="can" data-id="${x.id}">Cancel</button>`:""}${x.st==="in"?`<button class="sm pri" data-a="done" data-id="${x.id}">Complete</button>`:""}</div></div>`}).join(""):`<p class="mut">No patients yet. Book a visit on the Book tab or add a walk-in above.</p>`}</div>
 <button class="sm" id="rs">Reset demo data</button>`}
function bindRec(){$("#dc").onclick=()=>{S.doc=!S.doc;save();render()};
 $("#wa").onclick=()=>{const n=$("#wn").value.trim();if(n)addWalk(n,$("#wp").value);else $("#wn").focus()};
 $("#sq").oninput=e=>{q=e.target.value;render();const i=$("#sq");i.focus();i.setSelectionRange(q.length,q.length)};
 document.querySelectorAll("[data-a]").forEach(b=>b.onclick=()=>act(b.dataset.id,b.dataset.a));
 $("#rs").onclick=()=>{if(confirm("Delete all demo patients?")){S={a:[],n:0,doc:false,avg:15,me:null};save();render()}}}

function render(){const v=(location.hash||"#book").slice(1),V={book:[vBook,bindBook],track:[vTrack,bindTrack],reception:[vRec,bindRec]}[v]||[vBook,bindBook];
 ["book","track","reception"].forEach(n=>$("#n-"+n).classList.toggle("on",n===v));
 $("#app").innerHTML=V[0]()+`<p class="note">Demo mode: data is stored only in this browser. WhatsApp messages, accounts and the database are not connected, so nothing is actually sent.</p>`;V[1]()}
addEventListener("hashchange",render);addEventListener("storage",e=>{if(e.key===K){S=load();render()}});
setInterval(()=>{const a=document.activeElement;if(a&&/INPUT|SELECT/.test(a.tagName))return;S=load();render()},5000);
render();
</script></body></html>
