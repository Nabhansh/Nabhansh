<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Nabhansh Rishi Gaur // Portfolio</title>
<link href="https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Orbitron:wght@400;700;900&family=VT323&display=swap" rel="stylesheet">
<style>
  :root {
    --green: #00ff41;
    --green-dim: #00b32c;
    --green-glow: rgba(0, 255, 65, 0.15);
    --red: #ff3c3c;
    --cyan: #00e5ff;
    --amber: #ffb300;
    --bg: #020b04;
    --bg2: #041008;
    --panel: rgba(0, 255, 65, 0.04);
    --border: rgba(0, 255, 65, 0.2);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--green);
    font-family: 'Share Tech Mono', monospace;
    min-height: 100vh;
    overflow-x: hidden;
    cursor: crosshair;
  }

  /* Scanlines overlay */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background: repeating-linear-gradient(
      0deg,
      transparent,
      transparent 2px,
      rgba(0,0,0,0.08) 2px,
      rgba(0,0,0,0.08) 4px
    );
    pointer-events: none;
    z-index: 9999;
  }

  /* Noise texture */
  body::after {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.03'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 9998;
    opacity: 0.4;
  }

  .container {
    max-width: 900px;
    margin: 0 auto;
    padding: 40px 20px;
  }

  /* HEADER BOOT SEQUENCE */
  .boot-header {
    margin-bottom: 40px;
    border: 1px solid var(--border);
    background: var(--panel);
    padding: 20px 24px;
    position: relative;
    overflow: hidden;
  }
  .boot-header::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, transparent, var(--green), transparent);
    animation: scanbar 3s linear infinite;
  }
  @keyframes scanbar {
    0% { transform: translateX(-100%); }
    100% { transform: translateX(100%); }
  }

  .boot-line {
    font-size: 11px;
    color: var(--green-dim);
    margin-bottom: 4px;
    opacity: 0;
    animation: fadein 0.3s forwards;
  }
  .boot-line:nth-child(1) { animation-delay: 0.1s; }
  .boot-line:nth-child(2) { animation-delay: 0.4s; }
  .boot-line:nth-child(3) { animation-delay: 0.7s; }
  .boot-line:nth-child(4) { animation-delay: 1.0s; }
  @keyframes fadein { to { opacity: 1; } }

  /* MAIN TERMINAL */
  .terminal {
    border: 1px solid var(--border);
    background: var(--panel);
    margin-bottom: 24px;
    position: relative;
  }

  .terminal-bar {
    background: rgba(0, 255, 65, 0.08);
    border-bottom: 1px solid var(--border);
    padding: 8px 16px;
    display: flex;
    align-items: center;
    gap: 8px;
    font-size: 11px;
    color: var(--green-dim);
  }
  .dot { width: 8px; height: 8px; border-radius: 50%; }
  .dot.red { background: var(--red); box-shadow: 0 0 6px var(--red); }
  .dot.amber { background: var(--amber); box-shadow: 0 0 6px var(--amber); }
  .dot.green { background: var(--green); box-shadow: 0 0 6px var(--green); }
  .terminal-title { margin-left: 8px; letter-spacing: 2px; text-transform: uppercase; }

  .terminal-body { padding: 24px; }

  /* WHOAMI BLOCK */
  .whoami-grid {
    display: grid;
    gap: 6px;
  }
  .cmd-line {
    display: flex;
    gap: 12px;
    font-size: 13px;
  }
  .prompt { color: var(--green-dim); user-select: none; }
  .cmd-text { color: var(--cyan); }

  .output-block {
    margin: 12px 0 20px 0;
    border-left: 2px solid var(--green-dim);
    padding-left: 16px;
  }

  .info-row {
    display: grid;
    grid-template-columns: 100px 1fr;
    gap: 8px;
    margin: 4px 0;
    font-size: 13px;
    opacity: 0;
    animation: fadein 0.4s forwards;
  }
  .info-row:nth-child(1) { animation-delay: 1.4s; }
  .info-row:nth-child(2) { animation-delay: 1.7s; }
  .info-row:nth-child(3) { animation-delay: 2.0s; }
  .info-row:nth-child(4) { animation-delay: 2.3s; }
  .info-row:nth-child(5) { animation-delay: 2.6s; }

  .key { color: var(--green-dim); }
  .val { color: #fff; }
  .val .highlight { color: var(--green); font-weight: bold; }

  /* BIG NAME */
  .hero-name {
    font-family: 'Orbitron', monospace;
    font-size: clamp(28px, 5vw, 52px);
    font-weight: 900;
    letter-spacing: 4px;
    text-transform: uppercase;
    color: var(--green);
    text-shadow: 0 0 20px var(--green), 0 0 60px rgba(0,255,65,0.3);
    margin: 20px 0 6px;
    line-height: 1.1;
    opacity: 0;
    animation: fadein 0.6s 2.9s forwards;
  }
  .hero-sub {
    font-family: 'VT323', monospace;
    font-size: 22px;
    color: var(--cyan);
    letter-spacing: 3px;
    opacity: 0;
    animation: fadein 0.6s 3.2s forwards;
  }

  /* CURSOR BLINK */
  .cursor {
    display: inline-block;
    width: 10px;
    height: 16px;
    background: var(--green);
    animation: blink 1s step-end infinite;
    vertical-align: middle;
    margin-left: 4px;
    box-shadow: 0 0 8px var(--green);
  }
  @keyframes blink { 50% { opacity: 0; } }

  /* SKILLS SECTION */
  .section-header {
    font-size: 11px;
    letter-spacing: 4px;
    color: var(--green-dim);
    text-transform: uppercase;
    margin-bottom: 16px;
    display: flex;
    align-items: center;
    gap: 12px;
  }
  .section-header::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  .skill-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  .skill-tag {
    font-size: 11px;
    letter-spacing: 1px;
    padding: 6px 12px;
    border: 1px solid var(--border);
    color: var(--green);
    text-transform: uppercase;
    position: relative;
    overflow: hidden;
    transition: all 0.2s;
    cursor: default;
  }
  .skill-tag::before {
    content: '';
    position: absolute;
    inset: 0;
    background: var(--green-glow);
    transform: translateX(-100%);
    transition: transform 0.3s;
  }
  .skill-tag:hover::before { transform: translateX(0); }
  .skill-tag:hover {
    border-color: var(--green);
    box-shadow: 0 0 12px var(--green-glow), inset 0 0 12px var(--green-glow);
    text-shadow: 0 0 8px var(--green);
  }

  .skill-tag.lang { border-color: rgba(0,229,255,0.3); color: var(--cyan); }
  .skill-tag.lang:hover { border-color: var(--cyan); box-shadow: 0 0 12px rgba(0,229,255,0.2); }
  .skill-tag.ml { border-color: rgba(255,179,0,0.3); color: var(--amber); }
  .skill-tag.ml:hover { border-color: var(--amber); box-shadow: 0 0 12px rgba(255,179,0,0.2); }
  .skill-tag.sec { border-color: rgba(255,60,60,0.3); color: var(--red); }
  .skill-tag.sec:hover { border-color: var(--red); box-shadow: 0 0 12px rgba(255,60,60,0.2); }

  /* PROGRESS BARS */
  .progress-section { margin-top: 8px; }
  .progress-row {
    display: grid;
    grid-template-columns: 120px 1fr 40px;
    align-items: center;
    gap: 12px;
    margin: 10px 0;
    font-size: 12px;
  }
  .progress-bar {
    height: 6px;
    background: rgba(0,255,65,0.08);
    border: 1px solid var(--border);
    position: relative;
    overflow: hidden;
  }
  .progress-fill {
    height: 100%;
    background: linear-gradient(90deg, var(--green-dim), var(--green));
    box-shadow: 0 0 8px var(--green);
    width: 0;
    transition: width 1.5s cubic-bezier(0.4, 0, 0.2, 1);
  }
  .progress-fill.cyan { background: linear-gradient(90deg, rgba(0,229,255,0.5), var(--cyan)); box-shadow: 0 0 8px var(--cyan); }
  .progress-fill.amber { background: linear-gradient(90deg, rgba(255,179,0,0.5), var(--amber)); box-shadow: 0 0 8px var(--amber); }
  .progress-val { color: var(--green-dim); font-size: 11px; text-align: right; }

  /* SOCIALS */
  .social-links {
    display: flex;
    gap: 12px;
    flex-wrap: wrap;
    margin-top: 8px;
  }
  .social-link {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 8px 16px;
    border: 1px solid var(--border);
    color: var(--green-dim);
    text-decoration: none;
    font-size: 12px;
    letter-spacing: 2px;
    text-transform: uppercase;
    transition: all 0.2s;
    position: relative;
    overflow: hidden;
  }
  .social-link::before {
    content: '';
    position: absolute;
    bottom: 0; left: 0;
    height: 2px;
    width: 0;
    background: var(--green);
    transition: width 0.3s;
    box-shadow: 0 0 8px var(--green);
  }
  .social-link:hover::before { width: 100%; }
  .social-link:hover { color: var(--green); border-color: var(--green); background: var(--green-glow); }
  .social-link svg { width: 14px; height: 14px; }

  /* MOTTO */
  .motto-block {
    text-align: center;
    padding: 32px;
    border: 1px solid var(--border);
    background: var(--panel);
    margin-bottom: 24px;
    position: relative;
  }
  .motto-block::before, .motto-block::after {
    content: '[ ';
    font-family: 'VT323', monospace;
    font-size: 36px;
    color: rgba(0,255,65,0.2);
    position: absolute;
  }
  .motto-block::before { top: 12px; left: 16px; content: '[ '; }
  .motto-block::after { bottom: 12px; right: 16px; content: ' ]'; }
  .motto-text {
    font-family: 'VT323', monospace;
    font-size: 28px;
    letter-spacing: 2px;
    color: #fff;
    text-shadow: 0 0 20px var(--green);
  }
  .motto-text span { color: var(--green); }

  /* GITHUB STATS */
  .stats-grid {
    display: grid;
    gap: 16px;
  }
  .stats-grid img {
    width: 100%;
    border: 1px solid var(--border);
    display: block;
    filter: drop-shadow(0 0 8px var(--green-glow));
    transition: filter 0.3s;
  }
  .stats-grid img:hover {
    filter: drop-shadow(0 0 16px rgba(0,255,65,0.3));
  }

  /* FOOTER */
  .footer {
    text-align: center;
    padding: 20px;
    font-size: 11px;
    color: rgba(0,255,65,0.3);
    letter-spacing: 3px;
    text-transform: uppercase;
    border-top: 1px solid var(--border);
    margin-top: 8px;
  }

  /* GLITCH EFFECT ON NAME HOVER */
  .hero-name:hover {
    animation: glitch 0.3s linear;
  }
  @keyframes glitch {
    0% { text-shadow: 0 0 20px var(--green), 2px 0 var(--red), -2px 0 var(--cyan); }
    25% { text-shadow: 0 0 20px var(--green), -2px 0 var(--red), 2px 0 var(--cyan); }
    50% { text-shadow: 0 0 20px var(--green), 2px 2px var(--red), -2px -2px var(--cyan); }
    100% { text-shadow: 0 0 20px var(--green), 0 0 60px rgba(0,255,65,0.3); }
  }

  /* SECTION TAGS */
  .tag-label {
    font-size: 10px;
    letter-spacing: 3px;
    color: var(--red);
    text-transform: uppercase;
    margin-bottom: 4px;
  }

  /* MISSION STATUS */
  .mission-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
  }
  @media (max-width: 600px) {
    .mission-grid { grid-template-columns: 1fr; }
    .progress-row { grid-template-columns: 90px 1fr 36px; }
  }
  .mission-card {
    border: 1px solid var(--border);
    padding: 16px;
    background: var(--panel);
    position: relative;
  }
  .mission-card::before {
    content: attr(data-status);
    position: absolute;
    top: 8px; right: 8px;
    font-size: 9px;
    letter-spacing: 2px;
    padding: 2px 6px;
    border: 1px solid;
  }
  .mission-card[data-status="ACTIVE"]::before { color: var(--green); border-color: var(--green); }
  .mission-card[data-status="LEARNING"]::before { color: var(--amber); border-color: var(--amber); }
  .mission-card-title {
    font-size: 12px;
    letter-spacing: 2px;
    color: var(--cyan);
    margin-bottom: 6px;
  }
  .mission-card-desc {
    font-size: 11px;
    color: var(--green-dim);
    line-height: 1.6;
  }
</style>
</head>
<body>
<div class="container">

  <!-- BOOT SEQUENCE -->
  <div class="boot-header">
    <div class="boot-line">[ BIOS ] Initializing secure shell... OK</div>
    <div class="boot-line">[ SYS  ] Loading identity module... OK</div>
    <div class="boot-line">[ NET  ] Establishing connection... OK</div>
    <div class="boot-line">[ AUTH ] Access granted. Welcome, user.</div>
  </div>

  <!-- MAIN WHOAMI TERMINAL -->
  <div class="terminal">
    <div class="terminal-bar">
      <div class="dot red"></div>
      <div class="dot amber"></div>
      <div class="dot green"></div>
      <span class="terminal-title">bash — nabhansh@portfolio ~ — 80x24</span>
    </div>
    <div class="terminal-body">
      <div class="whoami-grid">
        <div class="cmd-line">
          <span class="prompt">nabhansh@kali:~$</span>
          <span class="cmd-text">cat ./identity.conf</span>
        </div>
        <div class="output-block">
          <div class="info-row">
            <span class="key">Name      :</span>
            <span class="val">Nabhansh Rishi Gaur</span>
          </div>
          <div class="info-row">
            <span class="key">Role      :</span>
            <span class="val"><span class="highlight">Full-stack Dev</span> | Cybersecurity Learner</span>
          </div>
          <div class="info-row">
            <span class="key">Location  :</span>
            <span class="val">India 🇮🇳</span>
          </div>
          <div class="info-row">
            <span class="key">Mission   :</span>
            <span class="val">100 Days of Code // Building & Pentesting</span>
          </div>
          <div class="info-row">
            <span class="key">Status    :</span>
            <span class="val"><span class="highlight">[ ONLINE ]</span><span class="cursor"></span></span>
          </div>
        </div>
      </div>

      <div class="hero-name">Nabhansh<br>Rishi Gaur</div>
      <div class="hero-sub">> Full-Stack // Security // Builder</div>
    </div>
  </div>

  <!-- MOTTO -->
  <div class="motto-block">
    <div class="motto-text">
      <span>Keep building.</span> Keep breaking. <span>Keep learning.</span>
    </div>
  </div>

  <!-- SKILL MATRIX -->
  <div class="terminal">
    <div class="terminal-bar">
      <div class="dot red"></div><div class="dot amber"></div><div class="dot green"></div>
      <span class="terminal-title">skill_matrix.sh</span>
    </div>
    <div class="terminal-body">
      <div class="section-header">// Tech Stack</div>

      <div class="tag-label">$ languages</div>
      <div class="skill-grid" style="margin-bottom:16px">
        <span class="skill-tag lang">Python</span>
        <span class="skill-tag lang">C</span>
        <span class="skill-tag lang">Java</span>
        <span class="skill-tag lang">JavaScript</span>
        <span class="skill-tag lang">HTML5</span>
        <span class="skill-tag lang">CSS3</span>
      </div>

      <div class="tag-label">$ machine_learning</div>
      <div class="skill-grid" style="margin-bottom:16px">
        <span class="skill-tag ml">TensorFlow</span>
        <span class="skill-tag ml">PyTorch</span>
        <span class="skill-tag ml">NumPy</span>
        <span class="skill-tag ml">Pandas</span>
      </div>

      <div class="tag-label">$ databases & tools</div>
      <div class="skill-grid" style="margin-bottom:16px">
        <span class="skill-tag">MongoDB</span>
        <span class="skill-tag">MySQL</span>
        <span class="skill-tag">Git</span>
        <span class="skill-tag">GitHub</span>
      </div>

      <div class="tag-label">$ security</div>
      <div class="skill-grid" style="margin-bottom:24px">
        <span class="skill-tag sec">Kali Linux</span>
        <span class="skill-tag sec">Pentesting</span>
        <span class="skill-tag sec">CTF // WIP</span>
      </div>

      <div class="section-header">// Proficiency</div>
      <div class="progress-section" id="progressSection">
        <div class="progress-row">
          <span>Python</span>
          <div class="progress-bar"><div class="progress-fill" data-width="85"></div></div>
          <span class="progress-val">85%</span>
        </div>
        <div class="progress-row">
          <span>C</span>
          <div class="progress-bar"><div class="progress-fill" data-width="78"></div></div>
          <span class="progress-val">78%</span>
        </div>
        <div class="progress-row">
          <span>Web (HTML/CSS/JS)</span>
          <div class="progress-bar"><div class="progress-fill cyan" data-width="80"></div></div>
          <span class="progress-val">80%</span>
        </div>
        <div class="progress-row">
          <span>ML / AI</span>
          <div class="progress-bar"><div class="progress-fill amber" data-width="60"></div></div>
          <span class="progress-val">60%</span>
        </div>
        <div class="progress-row">
          <span>Cybersecurity</span>
          <div class="progress-bar"><div class="progress-fill" style="background:linear-gradient(90deg,rgba(255,60,60,0.5),var(--red));box-shadow:0 0 8px var(--red);" data-width="45"></div></div>
          <span class="progress-val">45%</span>
        </div>
      </div>
    </div>
  </div>

  <!-- MISSIONS -->
  <div class="terminal">
    <div class="terminal-bar">
      <div class="dot red"></div><div class="dot amber"></div><div class="dot green"></div>
      <span class="terminal-title">missions.log</span>
    </div>
    <div class="terminal-body">
      <div class="section-header">// Current Objectives</div>
      <div class="mission-grid">
        <div class="mission-card" data-status="ACTIVE">
          <div class="mission-card-title">> 100 Days of Code</div>
          <div class="mission-card-desc">Daily coding streak — building projects, solving problems, leveling up skills consistently.</div>
        </div>
        <div class="mission-card" data-status="ACTIVE">
          <div class="mission-card-title">> Full-Stack Projects</div>
          <div class="mission-card-desc">Designing and deploying complete web applications from backend to frontend.</div>
        </div>
        <div class="mission-card" data-status="LEARNING">
          <div class="mission-card-title">> Pentesting</div>
          <div class="mission-card-desc">Learning ethical hacking, recon, exploitation, and vulnerability analysis with Kali Linux.</div>
        </div>
        <div class="mission-card" data-status="LEARNING">
          <div class="mission-card-title">> ML / AI</div>
          <div class="mission-card-desc">Exploring PyTorch and TensorFlow for building and training intelligent models.</div>
        </div>
      </div>
    </div>
  </div>

  <!-- GITHUB STATS -->
  <div class="terminal">
    <div class="terminal-bar">
      <div class="dot red"></div><div class="dot amber"></div><div class="dot green"></div>
      <span class="terminal-title">github_stats.sh --user Nabhansh</span>
    </div>
    <div class="terminal-body">
      <div class="section-header">// GitHub Telemetry</div>
      <div class="stats-grid">
        <img src="https://github-readme-stats.vercel.app/api?username=Nabhansh&theme=dark&hide_border=false&include_all_commits=true&count_private=true&bg_color=020b04&title_color=00ff41&text_color=00b32c&icon_color=00e5ff" alt="GitHub Stats" loading="lazy">
        <img src="https://nirzak-streak-stats.vercel.app/?user=Nabhansh&theme=dark&hide_border=false&background=020b04&ring=00ff41&fire=ff3c3c&currStreakLabel=00ff41&sideLabels=00b32c&dates=00b32c&border=1a3a1a" alt="Streak Stats" loading="lazy">
        <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Nabhansh&theme=dark&hide_border=false&include_all_commits=true&count_private=true&layout=compact&bg_color=020b04&title_color=00ff41&text_color=00b32c" alt="Top Languages" loading="lazy">
      </div>
    </div>
  </div>

  <!-- SOCIALS -->
  <div class="terminal">
    <div class="terminal-bar">
      <div class="dot red"></div><div class="dot amber"></div><div class="dot green"></div>
      <span class="terminal-title">connect --open-channels</span>
    </div>
    <div class="terminal-body">
      <div class="section-header">// Establish Connection</div>
      <div class="social-links">
        <a href="https://instagram.com/nabhansh01" class="social-link" target="_blank">
          <svg viewBox="0 0 24 24" fill="currentColor"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/></svg>
          Instagram
        </a>
        <a href="https://linkedin.com/in/nabhansh-rishi-gaur-ba8902376" class="social-link" target="_blank">
          <svg viewBox="0 0 24 24" fill="currentColor"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
          LinkedIn
        </a>
        <a href="mailto:nabhanshg01@gmail.com" class="social-link">
          <svg viewBox="0 0 24 24" fill="currentColor"><path d="M24 5.457v13.909c0 .904-.732 1.636-1.636 1.636h-3.819V11.73L12 16.64l-6.545-4.91v9.273H1.636A1.636 1.636 0 0 1 0 19.366V5.457c0-2.023 2.309-3.178 3.927-1.964L5.455 4.64 12 9.548l6.545-4.910 1.528-1.145C21.69 2.28 24 3.434 24 5.457z"/></svg>
          Email
        </a>
        <a href="https://github.com/Nabhansh" class="social-link" target="_blank">
          <svg viewBox="0 0 24 24" fill="currentColor"><path d="M12 .297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12"/></svg>
          GitHub
        </a>
      </div>
    </div>
  </div>

  <div class="footer">
    // Nabhansh Rishi Gaur // Portfolio // 2025 // Keep Building. Keep Breaking.
  </div>

</div>

<script>
  // Animate progress bars on load
  setTimeout(() => {
    document.querySelectorAll('.progress-fill').forEach(bar => {
      bar.style.width = bar.dataset.width + '%';
    });
  }, 500);

  // Random glitch flicker on skills
  function randomGlitch() {
    const tags = document.querySelectorAll('.skill-tag');
    const tag = tags[Math.floor(Math.random() * tags.length)];
    tag.style.opacity = '0.3';
    setTimeout(() => tag.style.opacity = '1', 80);
    setTimeout(randomGlitch, Math.random() * 4000 + 1000);
  }
  setTimeout(randomGlitch, 3000);

  // Matrix rain in background
  const canvas = document.createElement('canvas');
  canvas.style.cssText = 'position:fixed;top:0;left:0;width:100%;height:100%;z-index:0;pointer-events:none;opacity:0.04;';
  document.body.prepend(canvas);
  const ctx = canvas.getContext('2d');

  function resizeCanvas() {
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
  }
  resizeCanvas();
  window.addEventListener('resize', resizeCanvas);

  const chars = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789@#$%&*<>[]{}';
  const fontSize = 12;
  let columns = Math.floor(canvas.width / fontSize);
  let drops = Array(columns).fill(1);

  function drawMatrix() {
    ctx.fillStyle = 'rgba(2, 11, 4, 0.05)';
    ctx.fillRect(0, 0, canvas.width, canvas.height);
    ctx.fillStyle = '#00ff41';
    ctx.font = fontSize + 'px Share Tech Mono';

    columns = Math.floor(canvas.width / fontSize);
    if (drops.length < columns) drops = [...drops, ...Array(columns - drops.length).fill(1)];

    for (let i = 0; i < columns; i++) {
      const char = chars[Math.floor(Math.random() * chars.length)];
      ctx.fillText(char, i * fontSize, drops[i] * fontSize);
      if (drops[i] * fontSize > canvas.height && Math.random() > 0.975) drops[i] = 0;
      drops[i]++;
    }
  }
  setInterval(drawMatrix, 60);
</script>
</body>
</html>
