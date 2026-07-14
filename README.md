[os.html](https://github.com/user-attachments/files/30013160/os.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>COMPUTIA-OS / NET-TERMINAL v3.1</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=VT323&display=swap');

*{box-sizing:border-box;margin:0;padding:0}

:root{
  --amber:#FFB000;
  --amber-dim:#8a5f00;
  --amber-bright:#FFD060;
  --amber-glow:#ffc93322;
  --bg:#0d0800;
  --bg2:#150e00;
  --border:#5a3a00;
  --green:#44ff44;
  --red:#ff4444;
  --cyan:#44ffee;
  --font:'VT323',monospace;
}

html,body{
  background:#000;
  height:100%;
  display:flex;
  align-items:center;
  justify-content:center;
  font-family:var(--font);
  overflow:hidden;
}

.monitor{
  position:relative;
  width:97vw;
  height:95vh;
  background:#1a0f00;
  border:3px solid #3a2200;
  border-radius:18px;
  padding:20px 20px 30px;
  box-shadow:0 0 60px #ff880022, inset 0 0 30px #00000080;
  display:flex;
  flex-direction:column;
}

.monitor-label{
  position:absolute;
  bottom:6px;
  left:50%;
  transform:translateX(-50%);
  font-family:var(--font);
  font-size:13px;
  color:#5a3a00;
  letter-spacing:4px;
}

.screen{
  background:var(--bg);
  border:2px solid var(--border);
  border-radius:6px;
  position:relative;
  overflow:hidden;
  flex:1;
  display:flex;
  flex-direction:column;
}

/* scanlines */
.screen::after{
  content:'';
  position:absolute;
  inset:0;
  background:repeating-linear-gradient(
    0deg,transparent,transparent 3px,
    rgba(0,0,0,0.12) 3px,rgba(0,0,0,0.12) 4px
  );
  pointer-events:none;
  z-index:100;
}

.screen::before{
  content:'';
  position:absolute;
  inset:0;
  background:radial-gradient(ellipse at 50% 40%, rgba(255,176,0,0.04) 0%, transparent 70%);
  pointer-events:none;
  z-index:99;
}

/* ---- BOOT SCREEN ---- */
#boot{
  display:flex;
  flex-direction:column;
  align-items:center;
  justify-content:center;
  flex:1;
  padding:30px;
  text-align:center;
}

.agat-logo{
  font-family:var(--font);
  font-size:64px;
  color:var(--amber);
  letter-spacing:8px;
  line-height:1;
  text-shadow:0 0 20px var(--amber-dim);
  margin-bottom:4px;
}

.agat-cyrillic{
  font-size:24px;
  color:var(--amber-dim);
  letter-spacing:6px;
  margin-bottom:20px;
}

.boot-divider{
  width:500px;
  max-width:80vw;
  border:none;
  border-top:1px solid var(--border);
  margin:16px auto;
}

.boot-info{
  font-size:17px;
  color:var(--amber-dim);
  line-height:1.7;
  letter-spacing:1px;
}

.boot-info span{color:var(--amber)}

.boot-progress{
  margin-top:22px;
  width:400px;
  max-width:80vw;
  height:14px;
  border:1px solid var(--border);
  position:relative;
  overflow:hidden;
}

.boot-bar{
  height:100%;
  background:var(--amber);
  width:0%;
  transition:width 0.1s linear;
}

.boot-status{
  font-size:17px;
  color:var(--amber-dim);
  margin-top:8px;
  min-height:20px;
  letter-spacing:1px;
}

.boot-prompt{
  margin-top:22px;
  font-size:19px;
  color:var(--amber);
  animation:blink 0.9s step-end infinite;
  display:none;
}

/* ---- DESKTOP / SHELL ---- */
#shell{display:none;flex:1;flex-direction:column;min-height:0;}

.topbar{
  background:var(--bg2);
  border-bottom:1px solid var(--border);
  padding:4px 12px;
  display:flex;
  align-items:center;
  justify-content:space-between;
  font-size:16px;
  color:var(--amber-dim);
  letter-spacing:1px;
  flex-shrink:0;
}

.topbar .logo{color:var(--amber);font-size:18px;letter-spacing:3px;}
.topbar .time-display{color:var(--amber);min-width:80px;text-align:right}

.menu-bar{
  background:var(--bg2);
  border-bottom:1px solid var(--border);
  display:flex;
  gap:0;
  flex-shrink:0;
}

.menu-item{
  font-size:16px;
  color:var(--amber-dim);
  padding:4px 14px;
  cursor:pointer;
  border-right:1px solid var(--border);
  letter-spacing:1px;
  user-select:none;
}
.menu-item:hover,.menu-item.active{background:var(--amber-glow);color:var(--amber)}

.content{
  display:flex;
  flex:1;
  gap:0;
  min-height:0;
}

/* SIDEBAR */
.sidebar{
  width:210px;
  border-right:1px solid var(--border);
  padding:8px 0;
  flex-shrink:0;
  overflow-y:auto;
}

.sidebar-title{
  font-size:12px;
  color:var(--amber-dim);
  padding:0 10px 6px;
  letter-spacing:2px;
  border-bottom:1px solid var(--border);
  margin-bottom:4px;
  margin-top:8px;
}
.sidebar-title:first-child{margin-top:0}

.sidebar-item{
  display:flex;
  align-items:center;
  gap:6px;
  padding:4px 10px;
  font-size:16px;
  color:var(--amber-dim);
  cursor:pointer;
  letter-spacing:0.5px;
}
.sidebar-item:hover,.sidebar-item.active{background:var(--amber-glow);color:var(--amber)}
.sidebar-item .ico{font-size:14px;min-width:16px;text-align:center}

/* MAIN AREA */
.main{flex:1;padding:0;overflow:hidden;display:flex;flex-direction:column;min-width:0}

/* BROWSER PANEL */
#panel-browser{display:flex;flex-direction:column;height:100%}
.addr-row{
  display:flex;
  align-items:center;
  gap:6px;
  padding:6px 10px;
  background:var(--bg2);
  border-bottom:1px solid var(--border);
  flex-shrink:0;
}
.nav-btn{
  background:transparent;
  border:1px solid var(--border);
  color:var(--amber-dim);
  font-family:var(--font);
  font-size:16px;
  padding:2px 10px;
  cursor:pointer;
  letter-spacing:1px;
}
.nav-btn:hover{background:var(--amber-glow);color:var(--amber)}
.nav-btn:disabled{opacity:0.3;cursor:default}
.nav-btn:disabled:hover{background:transparent;color:var(--amber-dim)}
.addr-label{font-size:15px;color:var(--amber-dim);white-space:nowrap}
.addr-path{
  flex:1;
  background:var(--bg);
  border:1px solid var(--border);
  color:var(--amber);
  font-family:var(--font);
  font-size:16px;
  padding:3px 8px;
  outline:none;
}
.browser-frame-wrap{flex:1;background:#fff;min-height:0}
#site-frame{width:100%;height:100%;border:none;display:block}
.browser-status{
  font-size:13px;
  color:var(--amber-dim);
  padding:2px 10px;
  background:var(--bg2);
  border-top:1px solid var(--border);
  flex-shrink:0;
}

/* TERMINAL */
#panel-terminal{display:none;flex-direction:column;height:100%}
.term-out{
  flex:1;
  overflow-y:auto;
  padding:8px 12px;
  font-size:16px;
  color:var(--amber);
  line-height:1.5;
  font-family:var(--font);
  min-height:0;
}
.term-out .sys{color:var(--amber-dim)}
.term-out .err{color:var(--red)}
.term-out .ok{color:var(--green)}
.term-out .hi{color:var(--amber-bright)}
.term-out .cmd{color:var(--cyan)}
.term-input-row{
  display:flex;
  align-items:center;
  border-top:1px solid var(--border);
  padding:6px 12px;
  gap:6px;
  background:var(--bg2);
  flex-shrink:0;
}
.prompt-label{font-size:17px;color:var(--amber);white-space:nowrap}
.term-input{
  background:transparent;
  border:none;
  color:var(--amber);
  font-family:var(--font);
  font-size:17px;
  flex:1;
  outline:none;
  caret-color:var(--amber);
  letter-spacing:0.5px;
}

/* SYSINFO */
#panel-sysinfo{display:none;flex-direction:column;padding:12px;overflow-y:auto}
.sysinfo-grid{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-bottom:8px}
.info-card{
  border:1px solid var(--border);
  padding:8px 12px;
  background:var(--bg2);
}
.info-card-title{font-size:12px;color:var(--amber-dim);letter-spacing:2px;border-bottom:1px solid var(--border);padding-bottom:4px;margin-bottom:6px}
.info-row{display:flex;justify-content:space-between;font-size:15px;margin:2px 0}
.info-label{color:var(--amber-dim)}
.info-val{color:var(--amber)}
.info-val.ok{color:var(--green)}
.mem-bar{margin-top:4px}
.mem-track{background:var(--bg);border:1px solid var(--border);height:10px}
.mem-fill{height:100%;background:var(--amber)}

/* STATUSBAR */
.statusbar{
  background:var(--bg2);
  border-top:1px solid var(--border);
  padding:3px 12px;
  display:flex;
  justify-content:space-between;
  font-size:13px;
  color:var(--amber-dim);
  letter-spacing:0.5px;
  flex-shrink:0;
}

@keyframes blink{0%,100%{opacity:1}50%{opacity:0}}
::-webkit-scrollbar{width:4px}
::-webkit-scrollbar-track{background:var(--bg)}
::-webkit-scrollbar-thumb{background:var(--border)}
</style>
</head>
<body>

<div class="monitor">
  <div class="screen" id="screen">

    <!-- BOOT SCREEN -->
    <div id="boot">
      <div class="agat-logo">COMPUTIA</div>
      <div class="agat-cyrillic">NET-TERMINAL OS</div>
      <hr class="boot-divider">
      <div class="boot-info">
        <span>REPUBLIC OF COMPUTIA</span> // OFFICIAL PORTAL ACCESS TERMINAL<br>
        CPU: <span>WEB-6502 @ 1MHz</span> &nbsp;|&nbsp; RAM: <span>128 KB</span> &nbsp;|&nbsp; ROM: <span>2 KB</span><br>
        ISSUED BY: <span>NATIONAL INFORMATICS CENTRE</span> &nbsp;|&nbsp; EST: <span>2009</span>
      </div>
      <div class="boot-progress"><div class="boot-bar" id="boot-bar"></div></div>
      <div class="boot-status" id="boot-status">INITIALIZING SYSTEM...</div>
      <div class="boot-prompt" id="boot-prompt">PRESS ANY KEY TO CONTINUE ▋</div>
    </div>

    <!-- SHELL -->
    <div id="shell">

      <div class="topbar">
        <span class="logo">COMPUTIA-OS v3.1</span>
        <span>NET-TERMINAL | GOVT.PORTAL ACCESS</span>
        <span class="time-display" id="clock">--:--:--</span>
      </div>

      <div class="menu-bar">
        <div class="menu-item active" onclick="setTab('browser')">BROWSER</div>
        <div class="menu-item" onclick="setTab('terminal')">TERMINAL</div>
        <div class="menu-item" onclick="setTab('sysinfo')">SYSTEM</div>
        <div class="menu-item" onclick="reboot()">REBOOT</div>
      </div>

      <div class="content">
        <div class="sidebar" id="sidebar"></div>

        <div class="main">

          <!-- BROWSER PANEL -->
          <div id="panel-browser">
            <div class="addr-row">
              <button class="nav-btn" id="btn-back" onclick="goBack()">&lt;</button>
              <button class="nav-btn" id="btn-fwd" onclick="goForward()">&gt;</button>
              <button class="nav-btn" onclick="goHome()">HOME</button>
              <button class="nav-btn" onclick="reloadFrame()">RELOAD</button>
              <span class="addr-label">A:\&gt;</span>
              <input class="addr-path" id="addr-path" spellcheck="false">
            </div>
            <div class="browser-frame-wrap">
              <iframe id="site-frame" src="computia/index.html"></iframe>
            </div>
            <div class="browser-status" id="browser-status">LOADING computia/index.html ...</div>
          </div>

          <!-- TERMINAL PANEL -->
          <div id="panel-terminal">
            <div class="term-out" id="term-out"></div>
            <div class="term-input-row">
              <span class="prompt-label" id="prompt-label">A:\&gt;</span>
              <input class="term-input" id="term-input" placeholder="type a command..." autocomplete="off" spellcheck="false">
            </div>
          </div>

          <!-- SYSINFO PANEL -->
          <div id="panel-sysinfo">
            <div class="sysinfo-grid">
              <div class="info-card">
                <div class="info-card-title">PROCESSOR / CPU</div>
                <div class="info-row"><span class="info-label">MODEL:</span><span class="info-val">WEB-6502</span></div>
                <div class="info-row"><span class="info-label">CLOCK:</span><span class="info-val">1.023 MHz</span></div>
                <div class="info-row"><span class="info-label">LOAD:</span><span class="info-val ok" id="cpu-load">12%</span></div>
              </div>
              <div class="info-card">
                <div class="info-card-title">MEMORY</div>
                <div class="info-row"><span class="info-label">TOTAL RAM:</span><span class="info-val">128 KB</span></div>
                <div class="info-row"><span class="info-label">FREE RAM:</span><span class="info-val ok" id="ram-free">91 KB</span></div>
                <div class="mem-bar"><div class="mem-track"><div class="mem-fill" id="mem-fill" style="width:29%"></div></div></div>
              </div>
              <div class="info-card">
                <div class="info-card-title">SITE / PORTAL</div>
                <div class="info-row"><span class="info-label">NAME:</span><span class="info-val">REPUBLIC OF COMPUTIA</span></div>
                <div class="info-row"><span class="info-label">PAGES:</span><span class="info-val" id="page-count">--</span></div>
                <div class="info-row"><span class="info-label">SECTIONS:</span><span class="info-val" id="sec-count">--</span></div>
                <div class="info-row"><span class="info-label">STATUS:</span><span class="info-val ok">ONLINE (LOCAL)</span></div>
              </div>
              <div class="info-card">
                <div class="info-card-title">SYSTEM / OS</div>
                <div class="info-row"><span class="info-label">OS:</span><span class="info-val">COMPUTIA-OS</span></div>
                <div class="info-row"><span class="info-label">VERSION:</span><span class="info-val">3.1</span></div>
                <div class="info-row"><span class="info-label">RENDERER:</span><span class="info-val">IFRAME/HTML</span></div>
                <div class="info-row"><span class="info-label">STATUS:</span><span class="info-val ok">RUNNING</span></div>
              </div>
            </div>
            <div style="font-size:12px;color:var(--amber-dim);text-align:center;letter-spacing:1px;margin-top:4px">
              ISSUED BY THE NATIONAL INFORMATICS CENTRE &middot; REPUBLIC OF COMPUTIA &middot; ALL RIGHTS RESERVED
            </div>
          </div>

        </div>
      </div>

      <div class="statusbar">
        <span id="status-left">COMPUTIA-OS READY</span>
        <span id="status-mid">A:\&gt;</span>
        <span id="status-right">DATE: <span id="sdate">--/--/--</span></span>
      </div>

    </div>
  </div>
  <div class="monitor-label">COMPUTIA-OS &middot; NET-TERMINAL &middot; LOCAL VIEWER</div>
</div>

<script>
// ============ SITE MAP ============
// Real directory tree of the uploaded Computia site, used to drive the sidebar,
// the terminal DIR/CD/OPEN commands, and the browser panel.
const siteTree = {
  '/': {label:'ROOT', files:[
    {f:'index.html', t:'Home Portal'},
    {f:'about.html', t:'About Computia'},
    {f:'government.html', t:'Government'},
    {f:'ministries.html', t:'Ministries'},
    {f:'citizens.html', t:'Citizens'},
    {f:'business.html', t:'Business'},
    {f:'tourism.html', t:'Tourism'},
    {f:'documents.html', t:'Documents'},
    {f:'legislation.html', t:'Legislation'},
    {f:'eservices.html', t:'E-Services'},
    {f:'search.html', t:'Search'},
    {f:'sitemap.html', t:'Site Map'},
    {f:'faqs.html', t:'FAQs'},
    {f:'rti.html', t:'RTI Portal'},
    {f:'contact.html', t:'Contact Us'},
    {f:'feedback.html', t:'Feedback'},
    {f:'accessibility.html', t:'Accessibility'},
    {f:'privacy.html', t:'Privacy Policy'},
    {f:'terms.html', t:'Terms of Use'},
  ]},
  'about': {label:'ABOUT', files:[
    {f:'about/culture.html', t:'Culture & Heritage'},
    {f:'about/economy.html', t:'Economy'},
    {f:'about/geography.html', t:'Geography & Climate'},
    {f:'about/history.html', t:'History of Computia'},
    {f:'about/symbols.html', t:'National Symbols'},
    {f:'about/tourism.html', t:'Tourism'},
  ]},
  'government': {label:'GOVERNMENT', files:[
    {f:'government/cabinet.html', t:'Cabinet Members'},
    {f:'government/constitution.html', t:'Constitution'},
    {f:'government/electoral.html', t:'Electoral Commission'},
    {f:'government/nic.html', t:'National Informatics Centre'},
    {f:'government/parliament.html', t:'National Assembly'},
    {f:'government/president.html', t:'Office of the President'},
    {f:'government/primeminister.html', t:"Prime Minister's Office"},
    {f:'government/states.html', t:'State Governments'},
    {f:'government/supremecourt.html', t:'Supreme Court'},
  ]},
  'ministries': {label:'MINISTRIES', files:[
    {f:'ministries/agriculture.html', t:'Agriculture'},
    {f:'ministries/commerce.html', t:'Commerce'},
    {f:'ministries/defence.html', t:'Defence'},
    {f:'ministries/education.html', t:'Education'},
    {f:'ministries/finance.html', t:'Finance'},
    {f:'ministries/foreignaffairs.html', t:'Foreign Affairs'},
    {f:'ministries/health.html', t:'Health'},
    {f:'ministries/internalaffairs.html', t:'Internal Affairs'},
    {f:'ministries/technology.html', t:'Technology'},
    {f:'ministries/transport.html', t:'Transport'},
  ]},
  'citizens': {label:'CITIZENS', files:[
    {f:'citizens/acts.html', t:'Acts & Rules'},
    {f:'citizens/charter.html', t:'Citizen Charter'},
    {f:'citizens/documents.html', t:'Documents & Forms'},
    {f:'citizens/grievances.html', t:'Public Grievances'},
    {f:'citizens/nationalid.html', t:'National ID Card'},
    {f:'citizens/services.html', t:'Services Directory'},
    {f:'citizens/vitals.html', t:'Birth & Death Certificates'},
    {f:'citizens/voterreg.html', t:'Voter Registration'},
  ]},
  'eservices': {label:'E-SERVICES', files:[
    {f:'eservices/businessreg.html', t:'Business Registration'},
    {f:'eservices/census.html', t:'Census Data'},
    {f:'eservices/court.html', t:'Court Services'},
    {f:'eservices/drivinglicence.html', t:'Driving Licence'},
    {f:'eservices/education.html', t:'Education Portal'},
    {f:'eservices/health.html', t:'Health Services'},
    {f:'eservices/passport.html', t:'Passport Services'},
    {f:'eservices/property.html', t:'Property Records'},
    {f:'eservices/tax.html', t:'Pay Taxes Online'},
    {f:'eservices/vehiclereg.html', t:'Vehicle Registry'},
  ]},
};
const dirOrder = ['/','about','government','ministries','citizens','eservices'];
let totalPages = 0;
dirOrder.forEach(k=>totalPages += siteTree[k].files.length);

// ============ SIDEBAR ============
function buildSidebar(){
  const sb = document.getElementById('sidebar');
  sb.innerHTML = '';
  dirOrder.forEach(key=>{
    const dir = siteTree[key];
    const title = document.createElement('div');
    title.className = 'sidebar-title';
    title.textContent = 'DIR: ' + dir.label;
    sb.appendChild(title);
    dir.files.forEach(entry=>{
      const item = document.createElement('div');
      item.className = 'sidebar-item';
      item.innerHTML = `<span class="ico">&gt;</span> ${entry.t}`;
      item.onclick = ()=>{
        document.querySelectorAll('.sidebar-item').forEach(x=>x.classList.remove('active'));
        item.classList.add('active');
        navigateTo(entry.f);
        setTab('browser');
      };
      sb.appendChild(item);
    });
  });
}

// ============ BROWSER NAV ============
let navHistory = ['index.html'];
let navPos = 0;
const frame = document.getElementById('site-frame');
const addrPath = document.getElementById('addr-path');

function navigateTo(path, pushHistory=true){
  frame.src = 'computia/' + path;
  addrPath.value = 'computia\\' + path.replace(/\//g,'\\');
  document.getElementById('browser-status').textContent = 'LOADING computia/' + path + ' ...';
  if(pushHistory){
    navHistory = navHistory.slice(0, navPos+1);
    navHistory.push(path);
    navPos = navHistory.length - 1;
  }
  updateNavButtons();
}
frame.addEventListener('load', ()=>{
  document.getElementById('browser-status').textContent = 'OK — computia/' + navHistory[navPos];
});

function goBack(){ if(navPos>0){ navPos--; navigateTo(navHistory[navPos], false); } }
function goForward(){ if(navPos<navHistory.length-1){ navPos++; navigateTo(navHistory[navPos], false); } }
function goHome(){ navigateTo('index.html'); }
function reloadFrame(){ frame.src = frame.src; }
function updateNavButtons(){
  document.getElementById('btn-back').disabled = navPos<=0;
  document.getElementById('btn-fwd').disabled = navPos>=navHistory.length-1;
}
addrPath.addEventListener('keydown', e=>{
  if(e.key==='Enter'){
    let p = addrPath.value.replace(/^computia\\?/,'').replace(/\\/g,'/').replace(/^\/+/,'');
    if(!p) p='index.html';
    navigateTo(p);
  }
});

// ============ TABS ============
function setTab(name){
  ['browser','terminal','sysinfo'].forEach(t=>{
    const p = document.getElementById('panel-'+t);
    if(p) p.style.display = (t===name) ? 'flex' : 'none';
  });
  document.querySelectorAll('.menu-item').forEach((el,i)=>{
    el.classList.toggle('active', ['browser','terminal','sysinfo',''].indexOf(name) === i);
  });
  if(name==='terminal') document.getElementById('term-input').focus();
}

// ============ TERMINAL ============
let cwd = '/';
let termHistory = [];
let histIdx = -1;
const termOut = document.getElementById('term-out');
const termIn  = document.getElementById('term-input');

function tlog(text, cls=''){
  const d = document.createElement('div');
  if(cls) d.className = cls;
  d.innerHTML = text;
  termOut.appendChild(d);
  termOut.scrollTop = termOut.scrollHeight;
}

function initTerminal(){
  tlog('','');
  tlog('  &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;','hi');
  tlog('  &#9474;   COMPUTIA-OS  NET-TERMINAL v3.1  (c)2009  &#9474;','hi');
  tlog('  &#9474;   REPUBLIC OF COMPUTIA &middot; NIC PORTAL       &#9474;','hi');
  tlog('  &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;','hi');
  tlog('','');
  tlog('  CPU: WEB-6502 @ 1MHz    RAM: 128 KB    PAGES: '+totalPages,'sys');
  tlog('  FS: COMPUTIA-VFS    RENDERER: LOCAL IFRAME','sys');
  tlog('','');
  tlog('  Type HELP for a list of commands.','sys');
  tlog('','');
  document.getElementById('prompt-label').textContent = 'A:\\>';
  document.getElementById('status-mid').textContent = 'A:\\>';
  termIn.addEventListener('keydown', termKey);
}

function termKey(e){
  if(e.key==='Enter'){
    const cmd = termIn.value.trim();
    if(cmd){
      termHistory.unshift(cmd);
      histIdx = -1;
      tlog('A:\\> '+cmd,'cmd');
      runCmd(cmd);
    }
    termIn.value='';
  } else if(e.key==='ArrowUp'){
    e.preventDefault();
    if(histIdx < termHistory.length-1){ histIdx++; termIn.value=termHistory[histIdx]; }
  } else if(e.key==='ArrowDown'){
    e.preventDefault();
    if(histIdx > 0){ histIdx--; termIn.value=termHistory[histIdx]; } else { histIdx=-1; termIn.value=''; }
  }
}

const cmdHelp = [
  ['HELP','List commands'],
  ['DIR [section]','List files in a section (or current)'],
  ['LIST','List all sections'],
  ['CD [section]','Change current section'],
  ['OPEN [file]','Open a file in the browser panel'],
  ['BROWSER','Switch to browser panel'],
  ['SYSINFO','Show system information'],
  ['TIME','Show current time'],
  ['MEM','Show memory status'],
  ['VER','Show OS version'],
  ['CLS','Clear the screen'],
  ['REBOOT','Restart the system'],
];

function resolveSection(arg){
  if(!arg) return cwd;
  const a = arg.toLowerCase();
  if(a==='/' || a==='root') return '/';
  if(siteTree[a]) return a;
  return null;
}

function runCmd(raw){
  const parts = raw.split(/\s+/);
  const cmd = parts[0].toUpperCase();
  const args = parts.slice(1);

  switch(cmd){
    case 'HELP':
      tlog('AVAILABLE COMMANDS:','sys');
      cmdHelp.forEach(([c,d])=>tlog(`  ${c.padEnd(20)} &mdash; ${d}`,''));
      break;
    case 'DIR':{
      const key = resolveSection(args[0]);
      if(key===null){ tlog('ERROR: Section not found &mdash; '+args[0],'err'); break; }
      const dir = siteTree[key];
      tlog(`Directory A:\\${key==='/'?'':key}\\  (${dir.label})`,'sys');
      tlog('FILE                        DESCRIPTION','sys');
      tlog('&#9472;'.repeat(50),'sys');
      dir.files.forEach(e=>tlog(`${e.f.split('/').pop().padEnd(28)}${e.t}`,''));
      tlog(`Total: ${dir.files.length} file(s)`,'sys');
      break;
    }
    case 'LIST':
      tlog('SECTIONS ON DISK A:','sys');
      dirOrder.forEach(k=>tlog('  [DIR] '+siteTree[k].label,''));
      break;
    case 'CD':{
      const key = resolveSection(args[0]);
      if(key===null){ tlog('ERROR: Section not found &mdash; '+args[0],'err'); break; }
      cwd = key;
      tlog('Current section: '+siteTree[key].label,'ok');
      break;
    }
    case 'OPEN':{
      if(!args[0]){ tlog('Usage: OPEN [file]','err'); break; }
      const dir = siteTree[cwd];
      const wanted = args[0].toLowerCase();
      const match = dir.files.find(e=>e.f.split('/').pop().toLowerCase()===wanted) ||
                    dir.files.find(e=>e.f.split('/').pop().toLowerCase()===wanted+'.html');
      if(!match){ tlog('ERROR: File not found in current section &mdash; '+args[0],'err'); break; }
      tlog('Opening '+match.f+' ...','ok');
      navigateTo(match.f);
      setTab('browser');
      break;
    }
    case 'BROWSER': setTab('browser'); tlog('Switched to browser panel.','ok'); break;
    case 'SYSINFO': setTab('sysinfo'); tlog('Opened system information.','ok'); break;
    case 'TIME': tlog('CURRENT TIME: '+document.getElementById('clock').textContent,'ok'); break;
    case 'MEM':
      tlog('MEMORY STATUS:','sys');
      tlog('  TOTAL RAM:    128 KB',''); 
      tlog('  USED RAM:      37 KB','');
      tlog('  FREE RAM:      91 KB','ok');
      tlog('  ROM:            2 KB','');
      break;
    case 'VER':
      tlog('COMPUTIA-OS / NET-TERMINAL v3.1','ok');
      tlog('ISSUED BY: NATIONAL INFORMATICS CENTRE, 2009','sys');
      break;
    case 'CLS': termOut.innerHTML = ''; break;
    case 'REBOOT': reboot(); break;
    default: tlog('UNKNOWN COMMAND: '+cmd+' &mdash; type HELP','err');
  }
  tlog('','');
}

// ============ SYSINFO FLICKER ============
function flickerSys(){
  const loads = ['8%','12%','19%','7%','14%','22%','11%','6%'];
  const rams  = ['89 KB','91 KB','88 KB','94 KB','90 KB'];
  const el1 = document.getElementById('cpu-load');
  const el2 = document.getElementById('ram-free');
  if(el1) el1.textContent = loads[Math.floor(Math.random()*loads.length)];
  if(el2) el2.textContent = rams[Math.floor(Math.random()*rams.length)];
  const pct = 25+Math.floor(Math.random()*12);
  const mf = document.getElementById('mem-fill');
  if(mf) mf.style.width = pct+'%';
}

// ============ BOOT SEQUENCE ============
const bootMessages = [
  'CHECKING RAM... 128 KB OK',
  'LOADING COMPUTIA-VFS...',
  'MOUNTING computia/ ...',
  'CHECKING DRIVE A: ... OK',
  'INDEXING PORTAL PAGES...',
  'LOADING NET-TERMINAL BROWSER...',
  'INITIALIZING DISPLAY 1024x768...',
  'LOADING NIC PORTAL SUITE...',
  'SYSTEM READY.',
];
let bi = 0;
const bar = document.getElementById('boot-bar');
const bstat = document.getElementById('boot-status');
const bprompt = document.getElementById('boot-prompt');

function bootStep(){
  if(bi < bootMessages.length){
    bstat.textContent = bootMessages[bi];
    bar.style.width = Math.round((bi+1)/bootMessages.length*100)+'%';
    bi++;
    setTimeout(bootStep, 320 + Math.random()*180);
  } else {
    bprompt.style.display='block';
    document.addEventListener('keydown', startOS, {once:true});
    document.getElementById('boot').addEventListener('click', startOS, {once:true});
  }
}

function startOS(){
  document.getElementById('boot').style.display='none';
  const sh = document.getElementById('shell');
  sh.style.display='flex';
  buildSidebar();
  initTerminal();
  updateClock();
  setInterval(updateClock,1000);
  setInterval(flickerSys,2500);
  setTab('browser');
  navigateTo('index.html', false);
  navHistory=['index.html']; navPos=0; updateNavButtons();
  document.getElementById('page-count').textContent = totalPages;
  document.getElementById('sec-count').textContent = dirOrder.length;
}

setTimeout(bootStep, 500);

// ============ CLOCK ============
function updateClock(){
  const n = new Date();
  const t = [n.getHours(),n.getMinutes(),n.getSeconds()].map(x=>String(x).padStart(2,'0')).join(':');
  const d = [String(n.getDate()).padStart(2,'0'),String(n.getMonth()+1).padStart(2,'0'),String(n.getFullYear()).slice(2)].join('/');
  document.getElementById('clock').textContent = t;
  document.getElementById('sdate').textContent = d;
}

function reboot(){
  const sh = document.getElementById('shell');
  sh.style.display='none';
  const b = document.getElementById('boot');
  b.style.display='flex';
  bi=0;
  document.getElementById('boot-bar').style.width='0%';
  document.getElementById('boot-prompt').style.display='none';
  document.getElementById('term-out').innerHTML='';
  setTimeout(bootStep,400);
}
</script>
</body>
</html>
