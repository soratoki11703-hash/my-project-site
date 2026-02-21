<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>KAZUSORA</title>
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;1,300;1,400&family=Syne:wght@400;700;800&display=swap" rel="stylesheet">
  <style>
    *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }


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
