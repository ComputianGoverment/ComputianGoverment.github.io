# ComputianGoverment.github.io
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>DRUG DANGER ZONE - SAY NO TO DRUGS!</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Impact&family=Comic+Sans+MS&display=swap');

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background-color: #000080;
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='20' height='20'%3E%3Crect width='10' height='10' fill='%23000090'/%3E%3Crect x='10' y='10' width='10' height='10' fill='%23000090'/%3E%3C/svg%3E");
    font-family: 'Comic Sans MS', 'Comic Sans', cursive;
    color: #ffffff;
    cursor: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='20' height='20'%3E%3Ccircle cx='10' cy='10' r='5' fill='red'/%3E%3C/svg%3E"), auto;
  }

  /* MARQUEE STYLES */
  .top-marquee {
    background: #ff0000;
    color: #ffff00;
    font-size: 18px;
    font-weight: bold;
    padding: 6px 0;
    border-top: 3px solid #ffff00;
    border-bottom: 3px solid #ffff00;
    white-space: nowrap;
    overflow: hidden;
    animation: marquee 18s linear infinite;
  }
  @keyframes marquee {
    0% { text-indent: 100vw; }
    100% { text-indent: -200%; }
  }

  .bottom-marquee {
    background: #00aa00;
    color: #ffffff;
    font-size: 14px;
    padding: 4px 0;
    border-top: 3px solid #ffff00;
    border-bottom: 3px solid #ffff00;
    white-space: nowrap;
    overflow: hidden;
    animation: marquee2 22s linear infinite;
  }
  @keyframes marquee2 {
    0% { text-indent: 100vw; }
    100% { text-indent: -250%; }
  }

  /* HEADER */
  .header {
    background: linear-gradient(180deg, #ff0000, #cc0000);
    border: 5px outset #ff8888;
    text-align: center;
    padding: 10px;
    margin: 8px;
  }

  .header h1 {
    font-family: Impact, 'Arial Black', sans-serif;
    font-size: 52px;
    color: #ffff00;
    text-shadow: 4px 4px 0 #000, -2px -2px 0 #ff8800;
    letter-spacing: 4px;
    animation: flash 1s step-end infinite;
  }

  @keyframes flash {
    0%, 100% { color: #ffff00; }
    50% { color: #ff8800; }
  }

  .header h2 {
    font-size: 20px;
    color: #ffffff;
    text-shadow: 2px 2px 0 #000;
    animation: colorshift 2s linear infinite;
  }

  @keyframes colorshift {
    0% { color: #ff0000; }
    16% { color: #ff8800; }
    33% { color: #ffff00; }
    50% { color: #00ff00; }
    66% { color: #00ffff; }
    83% { color: #ff00ff; }
    100% { color: #ff0000; }
  }

  .skull-row {
    font-size: 28px;
    letter-spacing: 8px;
    margin: 6px 0;
  }

  /* HIT COUNTER + VISITOR BADGE */
  .meta-bar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: #000000;
    border: 2px inset #888;
    margin: 0 8px 8px 8px;
    padding: 4px 12px;
    font-size: 12px;
    color: #00ff00;
    font-family: 'Courier New', monospace;
  }

  .hit-counter {
    background: #000;
    border: 2px inset #555;
    padding: 2px 8px;
    font-size: 13px;
    font-family: 'Courier New', monospace;
    color: #ff4400;
    letter-spacing: 3px;
  }

  /* MAIN LAYOUT */
  .main-layout {
    display: flex;
    gap: 8px;
    margin: 0 8px 8px 8px;
    align-items: flex-start;
  }

  /* SIDEBAR */
  .sidebar {
    width: 170px;
    flex-shrink: 0;
  }

  .nav-box {
    background: #c0c0c0;
    border: 3px outset #ffffff;
    padding: 6px;
    margin-bottom: 8px;
  }

  .nav-box h3 {
    background: #000080;
    color: #ffffff;
    font-size: 13px;
    padding: 3px 6px;
    margin: -6px -6px 6px -6px;
    font-family: Impact, sans-serif;
    letter-spacing: 1px;
  }

  .nav-box a {
    display: block;
    color: #0000cc;
    text-decoration: underline;
    font-size: 13px;
    padding: 2px 0;
    cursor: pointer;
  }

  .nav-box a:hover {
    color: #ff0000;
    background: #ffff99;
  }

  .award-box {
    background: #c0c0c0;
    border: 3px outset #ffffff;
    padding: 8px;
    text-align: center;
    margin-bottom: 8px;
    font-size: 11px;
    color: #000;
  }

  .award-badge {
    background: linear-gradient(135deg, #ffd700, #ffaa00, #ffd700);
    border: 3px outset #ffd700;
    border-radius: 50%;
    width: 80px;
    height: 80px;
    margin: 0 auto 6px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 10px;
    font-weight: bold;
    color: #000;
    text-align: center;
    line-height: 1.2;
    animation: spin 8s linear infinite;
  }

  @keyframes spin {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg); }
  }

  .webring-box {
    background: #c0c0c0;
    border: 3px outset #ffffff;
    padding: 6px;
    text-align: center;
    font-size: 11px;
    color: #000;
    margin-bottom: 8px;
  }

  .under-construction {
    background: #ffff00;
    border: 3px outset #888;
    padding: 6px;
    text-align: center;
    font-size: 11px;
    font-weight: bold;
    color: #000;
    animation: blink 0.8s step-end infinite;
  }

  @keyframes blink {
    0%, 100% { opacity: 1; }
    50% { opacity: 0; }
  }

  /* CONTENT AREA */
  .content {
    flex: 1;
  }

  .content-box {
    background: #c0c0c0;
    border: 3px outset #ffffff;
    padding: 8px;
    margin-bottom: 8px;
  }

  .content-box h2 {
    background: #000080;
    color: #ffffff;
    font-family: Impact, sans-serif;
    font-size: 18px;
    letter-spacing: 2px;
    padding: 4px 8px;
    margin: -8px -8px 10px -8px;
    border-bottom: 2px solid #ffff00;
  }

  .drug-table {
    width: 100%;
    border-collapse: collapse;
    font-size: 13px;
    color: #000;
  }

  .drug-table th {
    background: #000080;
    color: #ffff00;
    padding: 5px 8px;
    border: 2px outset #888;
    font-family: Impact, sans-serif;
    letter-spacing: 1px;
    text-align: left;
  }

  .drug-table td {
    background: #ffffff;
    border: 2px inset #888;
    padding: 5px 8px;
    vertical-align: top;
  }

  .drug-table tr:nth-child(even) td {
    background: #ddeeff;
  }

  .drug-table tr:hover td {
    background: #ffff99;
  }

  .danger-high { color: #cc0000; font-weight: bold; }
  .danger-med  { color: #ff8800; font-weight: bold; }
  .danger-low  { color: #007700; font-weight: bold; }

  /* QUOTE BOX */
  .quote-box {
    background: #ffff99;
    border: 3px inset #888;
    padding: 10px 14px;
    margin: 8px 0;
    font-size: 14px;
    color: #000080;
    font-style: italic;
    font-weight: bold;
    text-align: center;
  }

  .quote-box .attribution {
    font-style: normal;
    font-size: 12px;
    color: #333;
    margin-top: 4px;
  }

  /* WARNING BOX */
  .warning-box {
    background: #ff0000;
    border: 4px outset #ff8888;
    padding: 10px;
    margin: 8px 0;
    text-align: center;
    color: #ffff00;
    font-weight: bold;
    font-size: 15px;
    animation: warnpulse 1.5s ease-in-out infinite;
  }

  @keyframes warnpulse {
    0%, 100% { border-color: #ff8888; }
    50% { border-color: #ffffff; }
  }

  /* STATS */
  .stats-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 6px;
    margin: 8px 0;
  }

  .stat-cell {
    background: #000080;
    border: 3px outset #8888ff;
    padding: 8px;
    text-align: center;
    color: #ffffff;
  }

  .stat-number {
    font-family: Impact, sans-serif;
    font-size: 28px;
    color: #ffff00;
    display: block;
    text-shadow: 2px 2px 0 #000;
  }

  .stat-label {
    font-size: 11px;
    color: #aaddff;
  }

  /* GUESTBOOK */
  .guestbook-entry {
    background: #ffffff;
    border: 2px inset #888;
    padding: 6px 10px;
    margin: 6px 0;
    font-size: 12px;
    color: #000;
  }

  .guestbook-entry .gb-name {
    color: #0000cc;
    font-weight: bold;
    font-size: 13px;
  }

  .guestbook-entry .gb-date {
    color: #888;
    font-size: 11px;
  }

  /* TIPS BOX */
  .tips-list {
    list-style: none;
    padding: 0;
    color: #000;
    font-size: 13px;
  }

  .tips-list li {
    padding: 4px 0 4px 24px;
    border-bottom: 1px dashed #999;
    position: relative;
  }

  .tips-list li::before {
    content: "➤";
    position: absolute;
    left: 4px;
    color: #cc0000;
  }

  /* EMAIL LINK */
  .email-link {
    color: #0000ff;
    text-decoration: underline;
    font-size: 12px;
  }

  /* FOOTER */
  .footer {
    background: #000000;
    border: 3px outset #444;
    margin: 8px;
    padding: 10px;
    text-align: center;
    font-size: 11px;
    color: #aaaaaa;
  }

  .footer a { color: #ffff00; }

  .best-viewed {
    background: #333333;
    border: 2px inset #555;
    display: inline-block;
    padding: 4px 10px;
    margin-top: 6px;
    font-size: 11px;
    color: #00ff00;
    font-family: 'Courier New', monospace;
  }

  .rainbow-hr {
    height: 6px;
    border: none;
    background: linear-gradient(90deg, red, orange, yellow, green, cyan, blue, violet, red);
    margin: 8px 0;
  }

  /* POPUP OVERLAY */
  .popup-overlay {
    display: none;
    position: fixed;
    top: 0; left: 0; right: 0; bottom: 0;
    background: rgba(0,0,0,0.6);
    z-index: 999;
    justify-content: center;
    align-items: center;
  }
  .popup-overlay.active { display: flex; }

  .popup-win {
    background: #c0c0c0;
    border: 3px outset #ffffff;
    width: 360px;
    box-shadow: 6px 6px 0 #000;
  }

  .popup-titlebar {
    background: linear-gradient(90deg, #000080, #1084d0);
    color: #fff;
    font-size: 13px;
    font-weight: bold;
    padding: 4px 8px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-family: 'Arial', sans-serif;
  }

  .popup-close {
    background: #c0c0c0;
    border: 2px outset #fff;
    width: 18px; height: 18px;
    font-size: 12px;
    font-weight: bold;
    cursor: pointer;
    color: #000;
    display: flex; align-items: center; justify-content: center;
  }

  .popup-body {
    padding: 14px;
    font-size: 13px;
    color: #000;
    text-align: center;
  }

  .popup-btn {
    background: #c0c0c0;
    border: 3px outset #ffffff;
    padding: 5px 20px;
    font-size: 13px;
    font-family: 'Comic Sans MS', cursive;
    cursor: pointer;
    margin-top: 10px;
    font-weight: bold;
  }
  .popup-btn:active { border-style: inset; }

  /* SCROLLBAR */
  ::-webkit-scrollbar { width: 16px; }
  ::-webkit-scrollbar-track { background: #c0c0c0; border: 2px inset #888; }
  ::-webkit-scrollbar-thumb { background: #808080; border: 2px outset #ffffff; }
</style>
</head>
<body>

<!-- POPUP -->
<div class="popup-overlay active" id="popup">
  <div class="popup-win">
    <div class="popup-titlebar">
      <span>⚠️ IMPORTANT MESSAGE</span>
      <div class="popup-close" onclick="document.getElementById('popup').classList.remove('active')">✕</div>
    </div>
    <div class="popup-body">
      <div style="font-size:40px">☠️</div>
      <p style="font-weight:bold; font-size:15px; color:#cc0000; margin:8px 0">WELCOME VISITOR #083,241!</p>
      <p>This site contains <strong>SHOCKING FACTS</strong> about drugs that your school doesn't want you to know!</p>
      <p style="margin-top:8px; font-size:12px; color:#555">Please sign our guestbook before you leave!</p>
      <button class="popup-btn" onclick="document.getElementById('popup').classList.remove('active')">OK I Promise To Say NO To Drugs!</button>
    </div>
  </div>
</div>

<!-- TOP MARQUEE -->
<div class="top-marquee">
  ☠️ DRUGS KILL ☠️ &nbsp;&nbsp;&nbsp; SAY NO TO DRUGS!!! &nbsp;&nbsp;&nbsp; ☠️ JUST SAY NO ☠️ &nbsp;&nbsp;&nbsp; DRUGS ARE NOT COOL &nbsp;&nbsp;&nbsp; ☠️ DRUGS KILL ☠️ &nbsp;&nbsp;&nbsp; YOUR BRAIN ON DRUGS 🍳 &nbsp;&nbsp;&nbsp; JUST SAY NO!!! &nbsp;&nbsp;&nbsp; ☠️ DRUGS KILL ☠️
</div>

<!-- HEADER -->
<div class="header">
  <div class="skull-row">☠️ 💀 ☠️ 💀 ☠️ 💀 ☠️</div>
  <h1>⚠️ DRUG DANGER ZONE ⚠️</h1>
  <h2>★★★ THE #1 ANTI-DRUG WEBSITE ON THE WORLD WIDE WEB ★★★</h2>
  <div class="skull-row">☠️ 💀 ☠️ 💀 ☠️ 💀 ☠️</div>
</div>

<!-- META BAR -->
<div class="meta-bar">
  <span>🕐 Last Updated: March 1998 &nbsp;|&nbsp; Webmaster: drugfighter@aol.com</span>
  <span>Visitors: <span class="hit-counter">083241</span></span>
  <span>Best viewed in Netscape Navigator 4.0 at 800x600</span>
</div>

<!-- MAIN LAYOUT -->
<div class="main-layout">

  <!-- SIDEBAR -->
  <div class="sidebar">

    <div class="nav-box">
      <h3>📋 NAVIGATION</h3>
      <a href="#">🏠 Home Page</a>
      <a href="#">💊 Drug Facts</a>
      <a href="#">☠️ True Stories</a>
      <a href="#">📞 Get Help NOW</a>
      <a href="#">📖 Guestbook</a>
      <a href="#">🔗 Cool Links</a>
      <a href="#">✉️ Contact Us</a>
    </div>

    <div class="award-box">
      <div class="award-badge">⭐<br>SITE OF<br>THE<br>WEEK<br>⭐</div>
      <strong>Drug Free Web Ring Award!</strong><br>
      March 1998
    </div>

    <div class="nav-box">
      <h3>🔗 COOL LINKS</h3>
      <a href="#">DARE Program</a>
      <a href="#">Nancy Reagan's Page</a>
      <a href="#">Drug Free America</a>
      <a href="#">Teen Help Hotline</a>
      <a href="#">Geocities Homepage</a>
    </div>

    <div class="webring-box">
      <strong>[ Drug-Free Web Ring ]</strong><br>
      <a href="#" style="color:#0000cc; font-size:11px">◀ Prev</a>
      &nbsp;·&nbsp;
      <a href="#" style="color:#0000cc; font-size:11px">Next ▶</a>
      <br>
      <a href="#" style="color:#0000cc; font-size:11px">List All Sites</a>
    </div>

    <div class="under-construction">
      🚧 PAGE UNDER<br>CONSTRUCTION! 🚧
    </div>

  </div>

  <!-- CONTENT -->
  <div class="content">

    <!-- WELCOME -->
    <div class="content-box">
      <h2>🌐 WELCOME TO DRUG DANGER ZONE!</h2>
      <p style="color:#000; font-size:13px; margin-bottom:8px">
        Hello and welcome to <strong>Drug Danger Zone</strong>, the most comprehensive anti-drug resource on the WORLD WIDE WEB! Whether you are a teenager, a parent, or a concerned citizen, this page has everything you need to know about the <strong>DEADLY DANGERS</strong> of illegal drugs.
      </p>
      <div class="quote-box">
        "Drugs are not the answer. They are the question, and the answer is NO!"
        <div class="attribution">— Just Say No Foundation, 1997</div>
      </div>
      <div class="warning-box">
        ⚠️ WARNING: DRUG USE CAN KILL YOU ON THE VERY FIRST TRY! ⚠️
      </div>
    </div>

    <!-- STATS -->
    <div class="content-box">
      <h2>📊 SHOCKING STATISTICS</h2>
      <div class="stats-grid">
        <div class="stat-cell">
          <span class="stat-number">14M</span>
          <span class="stat-label">Americans using illegal drugs (1997)</span>
        </div>
        <div class="stat-cell">
          <span class="stat-number">52%</span>
          <span class="stat-label">Of high schoolers offered drugs</span>
        </div>
        <div class="stat-cell">
          <span class="stat-number">14,000</span>
          <span class="stat-label">Drug-related deaths per year</span>
        </div>
        <div class="stat-cell">
          <span class="stat-number">$67B</span>
          <span class="stat-label">Annual cost of drug abuse to America</span>
        </div>
      </div>
    </div>

    <hr class="rainbow-hr">

    <!-- DRUG TABLE -->
    <div class="content-box">
      <h2>💊 THE DANGER CHART — KNOW YOUR ENEMY!</h2>
      <table class="drug-table">
        <tr>
          <th>Drug</th>
          <th>Street Names / Also Known As</th>
          <th>Danger Level</th>
          <th>Main Risk</th>
        </tr>
        <tr><td><strong>Heroin</strong></td><td>Smack, H, Horse, Junk</td><td class="danger-high">☠️ EXTREME</td><td>Overdose, addiction, HIV, hepatitis</td></tr>
        <tr><td><strong>Cocaine</strong></td><td>Coke, Snow, Blow, Charlie</td><td class="danger-high">☠️ EXTREME</td><td>Heart attack, stroke, cardiac arrest</td></tr>
        <tr><td><strong>Crystal Meth</strong></td><td>Ice, Crank, Speed, Tina</td><td class="danger-high">☠️ EXTREME</td><td>Brain damage, psychosis, tooth decay</td></tr>
        <tr><td><strong>Fentanyl</strong></td><td>China White, Apache, Dance Fever</td><td class="danger-high">☠️ EXTREME</td><td>100x stronger than morphine — tiny dose kills</td></tr>
        <tr><td><strong>Bath Salts</strong></td><td>Flakka, Vanilla Sky, Cloud Nine</td><td class="danger-high">☠️ EXTREME</td><td>Violent psychosis, excited delirium, death</td></tr>
        <tr><td><strong>PCP</strong></td><td>Angel Dust, Sherm, Wet</td><td class="danger-high">☠️ EXTREME</td><td>Psychosis, superhuman violence, seizures</td></tr>
        <tr><td><strong>25I-NBOMe</strong></td><td>N-Bomb, 25I, Smiles</td><td class="danger-high">☠️ EXTREME</td><td>Lethal in tiny doses, often sold as LSD!</td></tr>
        <tr><td><strong>Computer Cleaner</strong></td><td>Huffing, Canned Air, Duster</td><td class="danger-high">☠️ EXTREME</td><td>Sudden Sniffing Death on FIRST USE!</td></tr>
        <tr><td><strong>Carbon Monoxide</strong></td><td>Silent Killer, CO</td><td class="danger-high">☠️ EXTREME</td><td>Odorless, colorless — kills without warning!</td></tr>
        <tr><td><strong>Butane Honey Oil</strong></td><td>BHO, Dabs, Shatter, Wax</td><td class="danger-high">☠️ EXTREME</td><td>Explosion risk, 90% THC — overdose danger</td></tr>
        <tr><td><strong>Absolute Shatter</strong></td><td>Shatter, Glass, BHO</td><td class="danger-high">☠️ EXTREME</td><td>Ultra-potent cannabis extract, unknown doses</td></tr>
        <tr><td><strong>Opium</strong></td><td>Big O, Black Stuff, Chinese Tobacco</td><td class="danger-high">☠️ EXTREME</td><td>Highly addictive opioid — gateway to heroin</td></tr>
        <tr><td><strong>LSD</strong></td><td>Acid, Tabs, Blotter, Lucy</td><td class="danger-med">⚠️ VERY HIGH</td><td>Psychosis, flashbacks, dangerous behavior</td></tr>
        <tr><td><strong>Ketamine</strong></td><td>Special K, Vitamin K, Cat Tranquilizer</td><td class="danger-med">⚠️ VERY HIGH</td><td>Bladder destruction, k-hole dissociation</td></tr>
        <tr><td><strong>Lean</strong></td><td>Purple Drank, Sizzurp, Dirty Sprite</td><td class="danger-med">⚠️ VERY HIGH</td><td>Respiratory depression, opioid addiction</td></tr>
        <tr><td><strong>Nitrous Oxide</strong></td><td>Laughing Gas, Whippets, NOS</td><td class="danger-med">⚠️ VERY HIGH</td><td>Brain damage, asphyxiation, nerve damage</td></tr>
        <tr><td><strong>Ecstasy / MDMA</strong></td><td>X, Molly, Adam, Rolls</td><td class="danger-med">⚠️ VERY HIGH</td><td>Brain damage, overheating, bad batches</td></tr>
        <tr><td><strong>Marijuana</strong></td><td>Weed, Pot, Reefer, Mary Jane</td><td class="danger-med">⚠️ HIGH</td><td>Gateway drug! Kills motivation, psychosis risk</td></tr>
        <tr><td><strong>Xanax</strong> (abused)</td><td>Bars, Zannies, Planks, Benzos</td><td class="danger-high">☠️ EXTREME</td><td>Deadly withdrawal, respiratory depression</td></tr>
        <tr><td><strong>Ativan</strong> (abused)</td><td>Lorazepam, Benzos</td><td class="danger-med">⚠️ VERY HIGH</td><td>Severe dependence, withdrawal seizures</td></tr>
        <tr><td><strong>Abilify / Xanax / Ativan</strong> (mixed)</td><td>Cocktail, Poly-drug abuse</td><td class="danger-high">☠️ EXTREME</td><td>Dangerous CNS depression — DO NOT MIX!</td></tr>
        <tr><td><strong>Ativan / Haloperidol</strong> (mixed)</td><td>Chemical restraint cocktail</td><td class="danger-high">☠️ EXTREME</td><td>Respiratory arrest when combined illicitly</td></tr>
        <tr><td><strong>Adderall</strong> (abused)</td><td>Uppers, Study Drug, Bennies</td><td class="danger-med">⚠️ HIGH</td><td>Heart problems, psychosis, addiction</td></tr>
        <tr><td><strong>Ambien</strong> (abused)</td><td>Zombie Pills, A-minus, Sleepeasy</td><td class="danger-med">⚠️ HIGH</td><td>Sleepwalking, memory blackouts, dependence</td></tr>
        <tr><td><strong>Benzedrine</strong></td><td>Bennies, Peaches, Benz</td><td class="danger-med">⚠️ VERY HIGH</td><td>Heart failure, psychosis, severe addiction</td></tr>
        <tr><td><strong>Buspar</strong> (abused)</td><td>Buspirone, Busy Bee</td><td class="danger-low">⚠️ MODERATE</td><td>Dizziness, serotonin issues if misused</td></tr>
        <tr><td><strong>Butalbitals</strong></td><td>Fiorinal, Fioricet, Butalbital</td><td class="danger-med">⚠️ HIGH</td><td>Barbiturate — addiction, fatal withdrawal</td></tr>
        <tr><td><strong>Abilify</strong> (abused)</td><td>Aripiprazole, A-rip</td><td class="danger-low">⚠️ MODERATE</td><td>Compulsive behavior, serious side effects</td></tr>
        <tr><td><strong>Absinthe</strong></td><td>The Green Fairy, La Fée Verte</td><td class="danger-med">⚠️ HIGH</td><td>Extremely high alcohol, hallucinations, seizures</td></tr>
        <tr><td><strong>Celexa</strong> (abused)</td><td>Citalopram, Happy Pills</td><td class="danger-low">⚠️ MODERATE</td><td>Serotonin syndrome if misused or combined</td></tr>
        <tr><td><strong>Cephalexin</strong> (abused)</td><td>Keflex, Cepha</td><td class="danger-low">⚠️ LOW-MOD</td><td>Antibiotic misuse — resistant superbugs!</td></tr>
      </table>
    </div>

    <!-- TIPS -->
    <div class="content-box">
      <h2>✅ HOW TO SAY NO — TIPS FOR TEENS!</h2>
      <ul class="tips-list">
        <li>If someone offers you drugs, just walk away! You don't owe them an explanation!</li>
        <li>Find friends who share your values — real friends don't pressure you to do drugs!</li>
        <li>Get involved in sports, clubs, or church activities to stay busy and drug-free!</li>
        <li>If you're feeling pressured, talk to a trusted adult — parent, teacher, or counselor!</li>
        <li>Remember: drug dealers want your MONEY, not your friendship!</li>
        <li>Call 1-800-662-HELP if you or someone you know needs help with drugs!</li>
        <li>Bookmark this page and share it with your friends on AOL Instant Messenger!</li>
      </ul>
    </div>

    <hr class="rainbow-hr">

    <!-- GUESTBOOK -->
    <div class="content-box">
      <h2>📖 GUESTBOOK — SIGN AND SAY NO!</h2>

      <div class="guestbook-entry">
        <span class="gb-name">CoolDudeTX_1998</span> &nbsp;
        <span class="gb-date">March 14, 1998 | Dallas, TX</span>
        <p>Great site!!! My friend almost tried drugs but I showed him this page and he changed his mind!! JUST SAY NO!! ✌️</p>
      </div>

      <div class="guestbook-entry">
        <span class="gb-name">SoccerMom_Karen</span> &nbsp;
        <span class="gb-date">March 11, 1998 | Ohio</span>
        <p>I am sharing this with my son's entire soccer team. Every parent in America needs to see this website. GOD BLESS YOU for making this page!!</p>
      </div>

      <div class="guestbook-entry">
        <span class="gb-name">TeacherMrsHill</span> &nbsp;
        <span class="gb-date">March 9, 1998 | California</span>
        <p>I printed this out for my 8th grade health class. The drug chart is very informative. Bookmarked in Netscape!</p>
      </div>

      <div class="guestbook-entry">
        <span class="gb-name">xXDrugFighterXx</span> &nbsp;
        <span class="gb-date">March 7, 1998 | New York</span>
        <p>DRUGS ARE 4 LOSERS!!!! Real winners just say NO. This site RULES. Added to my Geocities homepage links!!!! 🤘</p>
      </div>

      <p style="font-size:12px; color:#000; margin-top:8px">
        ✉️ <a class="email-link" href="#">Click here to sign the guestbook!</a>
      </p>
    </div>

    <!-- HELPLINE -->
    <div class="warning-box" style="font-size:17px; padding:14px">
      📞 NATIONAL DRUG HELPLINE: <strong>1-800-662-HELP</strong><br>
      <span style="font-size:13px">FREE • CONFIDENTIAL • 24 HOURS A DAY • 7 DAYS A WEEK</span>
    </div>

  </div>
</div>

<!-- BOTTOM MARQUEE -->
<div class="bottom-marquee">
  📞 Need Help? Call 1-800-662-HELP &nbsp;&nbsp;&nbsp; ✉️ Sign our Guestbook! &nbsp;&nbsp;&nbsp; 🔗 Join the Drug-Free Web Ring! &nbsp;&nbsp;&nbsp; 💻 Best viewed in Netscape Navigator 4.0 &nbsp;&nbsp;&nbsp; 📞 Need Help? Call 1-800-662-HELP &nbsp;&nbsp;&nbsp; ✉️ Email us at drugfighter@aol.com
</div>

<!-- FOOTER -->
<div class="footer">
  <p>© 1998 Drug Danger Zone — All Rights Reserved — Made with ❤️ and Notepad.exe</p>
  <p style="margin-top:4px">
    <a href="#">Home</a> | <a href="#">About</a> | <a href="#">Links</a> | <a href="#">Guestbook</a> | <a href="#">Contact</a>
  </p>
  <div class="best-viewed">
    🖥️ Best viewed in Netscape Navigator 4.0 at 800×600 resolution with 256 colors
  </div>
  <p style="margin-top:8px; font-size:10px">
    This site is proudly hosted on <span style="color:#ffff00">GeoCities — Heartland/Meadows/4892</span>
  </p>
</div>

</body>
</html>
