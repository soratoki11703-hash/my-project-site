<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>KAZUSORA</title>
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;1,300;1,400&family=Syne:wght@400;700;800&display=swap" rel="stylesheet">
  <style>
    *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

:root {
      --bg: #0C0C0B;
      --ink: #F0EDE6;
      --muted: rgba(240,237,230,0.38);
      --accent: #C8A96E;
      --line: rgba(240,237,230,0.08);
    }

html { scroll-behavior: smooth; }

body {
      background: var(--bg);
      color: var(--ink);
      font-family: 'Cormorant Garamond', Georgia, serif;
      overflow-x: hidden;
      cursor: none;
    }

/* CURSOR */
    #cur {
      position: fixed;
      top: 0; left: 0;
      width: 8px; height: 8px;
      background: var(--accent);
      border-radius: 50%;
      pointer-events: none;
      z-index: 9999;
      transform: translate(-50%,-50%);
      transition: width .35s cubic-bezier(.16,1,.3,1),
                  height .35s cubic-bezier(.16,1,.3,1),
                  background .35s;
    }
    #cur.hover {
      width: 48px; height: 48px;
      background: transparent;
      border: 1px solid var(--accent);
    }

 /* NOISE */
    body::after {
      content:'';
      position:fixed;
      inset:0;
      background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence baseFrequency='0.75' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.035'/%3E%3C/svg%3E");
      pointer-events:none;
      z-index:200;
    }

/* NAV */
    nav {
      position: fixed;
      top: 0; left: 0; right: 0;
      padding: 36px 56px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      z-index: 100;
      opacity: 0;
      animation: fadeIn .8s 1.6s forwards;
    }

.nav-logo {
      font-family: 'Syne', sans-serif;
      font-size: 13px;
      font-weight: 700;
      letter-spacing: .25em;
    }

.nav-links {
      display: flex;
      gap: 40px;
      list-style: none;
    }

.nav-links a {
      font-family: 'Syne', sans-serif;
      font-size: 10px;
      letter-spacing: .2em;
      color: var(--muted);
      text-decoration: none;
      transition: color .3s;
    }
    .nav-links a:hover { color: var(--ink); }

/* HERO */
    .hero {
      min-height: 100vh;
      display: grid;
      align-items: end;
      padding: 0 56px 80px;
      position: relative;
      overflow: hidden;
    }

.hero-bg-text {
      position: absolute;
      bottom: -60px;
      right: -20px;
      font-family: 'Syne', sans-serif;
      font-weight: 800;
      font-size: clamp(160px, 25vw, 380px);
      color: transparent;
      -webkit-text-stroke: 1px rgba(200,169,110,0.06);
      line-height: 1;
      pointer-events: none;
      user-select: none;
    }

.hero-content {
      position: relative;
      z-index: 2;
      display: grid;
      grid-template-columns: 1fr auto;
      align-items: end;
      gap: 60px;
    }

.hero-eyebrow {
      font-family: 'Syne', sans-serif;
      font-size: 10px;
      letter-spacing: .3em;
      color: var(--accent);
      margin-bottom: 28px;
      opacity: 0;
      animation: fadeUp .9s .3s forwards;
    }

.hero-name {
      font-family: 'Syne', sans-serif;
      font-weight: 800;
      font-size: clamp(72px, 12vw, 180px);
      line-height: .92;
      letter-spacing: -.02em;
      opacity: 0;
      animation: fadeUp .9s .5s forwards;
    }

.hero-name em {
      display: block;
      font-style: italic;
      font-family: 'Cormorant Garamond', serif;
      font-weight: 300;
      font-size: .55em;
      color: var(--accent);
      letter-spacing: .05em;
      margin-top: 8px;
    }

.hero-right {
      display: flex;
      flex-direction: column;
      align-items: flex-end;
      gap: 20px;
      opacity: 0;
      animation: fadeUp .9s .7s forwards;
    }

.hero-desc {
      font-size: 15px;
      line-height: 1.8;
      color: var(--muted);
      text-align: right;
      max-width: 240px;
    }

.hero-scroll {
      display: flex;
      align-items: center;
      gap: 12px;
      font-family: 'Syne', sans-serif;
      font-size: 9px;
      letter-spacing: .25em;
      color: var(--muted);
    }

.hero-scroll span {
      display: block;
      width: 1px;
      height: 0;
      background: var(--muted);
      animation: lineDown 1s 1.5s forwards;
    }

hr.thin {
      border: none;
      border-top: 1px solid var(--line);
      margin: 0 56px;
    }

/* SECTIONS */
    .section {
      padding: 120px 56px;
      max-width: 1360px;
      margin: 0 auto;
    }

.s-num {
      font-family: 'Syne', sans-serif;
      font-size: 10px;
      letter-spacing: .3em;
      color: var(--accent);
      margin-bottom: 60px;
      display: flex;
      align-items: center;
      gap: 16px;
    }
    .s-num::after {
      content: '';
      display: block;
      flex: 1;
      height: 1px;
      background: var(--line);
      max-width: 80px;
    }

 /* ABOUT */
    .about-grid {
      display: grid;
      grid-template-columns: 5fr 4fr;
      gap: 100px;
      align-items: start;
    }

.about-headline {
      font-family: 'Cormorant Garamond', serif;
      font-weight: 300;
      font-size: clamp(42px, 5vw, 72px);
      line-height: 1.15;
      letter-spacing: -.01em;
      margin-bottom: 40px;
    }
.about-headline em { font-style: italic; color: var(--accent); }

 .about-body p {
      font-size: 17px;
      line-height: 1.9;
      color: var(--muted);
      margin-bottom: 18px;
    }
.about-body strong { color: var(--ink); font-weight: 400; }

 /* FACTS */
    .facts { border-top: 1px solid var(--line); padding-top: 48px; }

.fact {
      padding: 28px 0;
      border-bottom: 1px solid var(--line);
      display: grid;
      grid-template-columns: 1fr auto;
      align-items: center;
    }

 .fact-label {
      font-family: 'Syne', sans-serif;
      font-size: 10px;
      letter-spacing: .25em;
      color: var(--muted);
    }

.fact-value {
      font-family: 'Cormorant Garamond', serif;
      font-size: 28px;
      font-weight: 300;
      color: var(--ink);
      text-align: right;
    }

 /* QUOTE */
    .quote-section {
      padding: 100px 56px;
      max-width: 1360px;
      margin: 0 auto;
      display: flex;
      justify-content: center;
    }

 blockquote { max-width: 800px; text-align: center; }

 blockquote p {
      font-family: 'Cormorant Garamond', serif;
      font-style: italic;
      font-size: clamp(28px, 4vw, 52px);
      font-weight: 300;
      line-height: 1.4;
      color: var(--ink);
      letter-spacing: -.01em;
    }
blockquote p span { color: var(--accent); }
    blockquote cite {
      display: block;
      margin-top: 32px;
      font-family: 'Syne', sans-serif;
      font-size: 10px;
      letter-spacing: .3em;
      color: var(--muted);
      font-style: normal;
    }
    
/* CONTACT */
    .contact-section {
      padding: 120px 56px;
      max-width: 1360px;
      margin: 0 auto;
    }

.contact-inner {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 100px;
      align-items: end;
    }
    .contact-headline {
      font-family: 'Cormorant Garamond', serif;
      font-weight: 300;
      font-size: clamp(48px, 6vw, 88px);
      line-height: 1.05;
      letter-spacing: -.02em;
    }
.contact-headline em { font-style: italic; color: var(--accent); }

.contact-right {
      display: flex;
      flex-direction: column;
      gap: 32px;
    }

.contact-right p {
      font-size: 16px;
      line-height: 1.8;
      color: var(--muted);
    }

.contact-link {
      display: inline-flex;
      align-items: center;
      gap: 16px;
      font-family: 'Syne', sans-serif;
      font-size: 13px;
      letter-spacing: .15em;
      color: var(--ink);
      text-decoration: none;
      border-bottom: 1px solid rgba(200,169,110,0.3);
      padding-bottom: 12px;
      transition: border-color .3s, gap .3s;
    }
    .contact-link:hover { border-color: var(--accent); gap: 24px; }
    .contact-link::after { content: '→'; color: var(--accent); }

/* FOOTER */
    footer {
      padding: 40px 56px;
      border-top: 1px solid var(--line);
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

 .footer-left {
      font-family: 'Syne', sans-serif;
      font-size: 10px;
      letter-spacing: .25em;
      color: var(--muted);
    }

.footer-right {
      font-family: 'Cormorant Garamond', serif;
      font-style: italic;
      font-size: 15px;
      color: rgba(200,169,110,0.5);
    }

 /* REVEAL */
    .reveal {
      opacity: 0;
     transform: translateY(24px);
      transition: opacity .9s cubic-bezier(.16,1,.3,1),
                  transform .9s cubic-bezier(.16,1,.3,1);
    }
    .reveal.in { opacity: 1; transform: none; }
    .reveal-d1 { transition-delay: .1s; }
    .reveal-d2 { transition-delay: .2s; }
    .reveal-d3 { transition-delay: .3s; }

@keyframes fadeUp {
      from { opacity:0; transform:translateY(20px); }
      to   { opacity:1; transform:translateY(0); }
    }
@keyframes fadeIn {
      from { opacity:0; }
      to   { opacity:1; }
    }
    @keyframes lineDown {
      from { height:0; }
      to   { height:48px; }
    }

@media (max-width:900px) {
      nav { padding:28px 24px; }
      .hero { padding:0 24px 64px; }
      .hero-content { grid-template-columns:1fr; gap:32px; }
      .hero-right { align-items:flex-start; }
      .hero-desc { text-align:left; max-width:100%; }
      hr.thin { margin:0 24px; }
      .section { padding:80px 24px; }
      .about-grid { grid-template-columns:1fr; gap:60px; }
      .quote-section { padding:80px 24px; }
      .contact-section { padding:80px 24px; }
      .contact-inner { grid-template-columns:1fr; gap:48px; }
     footer { padding:32px 24px; flex-direction:column; gap:12px; text-align:center; }
    }
  </style>
</head>
<body>

<div id="cur"></div>

<nav>
  <div class="nav-logo">KAZUSORA</div>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-bg-text">KS</div>
  <div class="hero-content">
    <div>
      <div class="hero-eyebrow">Portfolio — 2025</div>
      <h1 class="hero-name">
        KAZUSORA
        <em>自分の道を、自分で。</em>
      </h1>
    </div>
    <div class="hero-right">
      <p class="hero-desc">ゼロ高等学院 3年生。<br>型にはまらない学びと<br>挑戦を続けています。</p>
      <div class="hero-scroll">
        <span></span>
        SCROLL
      </div>
    </div>
  </div>
</section>

<hr class="thin">

<!-- ABOUT -->
<div class="section" id="about">
  <div class="s-num reveal">01 &nbsp; About</div>
  <div class="about-grid">
    <div>
      <h2 class="about-headline reveal reveal-d1">
        学校という<br>
        <em>枠を超えた</em><br>
        10代の挑戦者。
      </h2>
      <div class="about-body reveal reveal-d2">
        <p>はじめまして、<strong>KAZUSORA</strong> です。</p>
        <p>ゼロ高等学院で学びながら、授業や校舎にしばられない<strong>自由な学びの形</strong>を模索しています。</p>
        <p>失敗を恐れず、自分のペースで、でも確実に前進することを大切にしています。</p>
      </div>
    </div>
    <div class="facts reveal reveal-d3">
      <div class="fact">
        <span class="fact-label">SCHOOL</span>
        <span class="fact-value">ゼロ高等学院</span>
      </div>
      <div class="fact">
        <span class="fact-label">GRADE</span>
        <span class="fact-value">3年生</span>
      </div>
      <div class="fact">
        <span class="fact-label">YEAR</span>
        <span class="fact-value">2025</span>
      </div>
      <div class="fact">
        <span class="fact-label">STATUS</span>
        <span class="fact-value" style="color:var(--accent);">Available</span>
      </div>
    </div>
  </div>
</div>

<hr class="thin">

<!-- QUOTE -->
<div class="quote-section">
  <blockquote class="reveal">
    <p>
      "正解のない時代を生きるなら、<br>
      <span>自分だけの問いを立てることが</span><br>
      はじまりだと思う。"
    </p>
    <cite>— KAZUSORA</cite>
  </blockquote>
</div>

<hr class="thin">

<!-- CONTACT -->
<div class="contact-section" id="contact">
  <div class="s-num reveal">02 &nbsp; Contact</div>
  <div class="contact-inner">
    <h2 class="contact-headline reveal reveal-d1">
      一緒に<br>
      <em>何かを</em><br>
      つくろう。
    </h2>
    <div class="contact-right reveal reveal-d2">
      <p>お仕事のご依頼・コラボレーション・<br>なんでもお気軽にどうぞ。</p>
      <a class="contact-link" href="mailto:hello@kazusora.com">hello@kazusora.com</a>
    </div>
  </div>
</div>

<footer>
  <span class="footer-left">© 2025 KAZUSORA — All rights reserved</span>
  <span class="footer-right">Designed with intention.</span>
</footer>

<script>
  const cur = document.getElementById('cur');
  document.addEventListener('mousemove', e => {
    cur.style.left = e.clientX + 'px';
    cur.style.top  = e.clientY + 'px';
  });
  document.querySelectorAll('a').forEach(el => {
    el.addEventListener('mouseenter', () => cur.classList.add('hover'));
    el.addEventListener('mouseleave', () => cur.classList.remove('hover'));
  });

  const obs = new IntersectionObserver(entries => {
    entries.forEach(e => {
      if (e.isIntersecting) { e.target.classList.add('in'); obs.unobserve(e.target); }
    });
  }, { threshold: 0.12 });
  document.querySelectorAll('.reveal').forEach(el => obs.observe(el));
</script>
</body>
</html>
