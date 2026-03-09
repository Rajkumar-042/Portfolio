<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Raj Kumar — Portfolio</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:ital,wght@0,400;0,700;1,400&family=Clash+Display:wght@400;500;600;700&family=Syne:wght@400;500;600;700;800&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0a0a0f;
    --surface: #12121a;
    --card: #1a1a26;
    --accent: #00ff88;
    --accent2: #7c3aed;
    --accent3: #ff6b35;
    --text: #e8e8f0;
    --muted: #6b6b8a;
    --border: rgba(255,255,255,0.06);
    --glow: rgba(0,255,136,0.15);
  }

  *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Syne', sans-serif;
    overflow-x: hidden;
    cursor: none;
  }

  /* CUSTOM CURSOR */
  .cursor {
    position: fixed; width: 12px; height: 12px;
    background: var(--accent); border-radius: 50%;
    pointer-events: none; z-index: 9999;
    transition: transform 0.1s ease;
    mix-blend-mode: difference;
  }
  .cursor-trail {
    position: fixed; width: 40px; height: 40px;
    border: 1px solid rgba(0,255,136,0.4); border-radius: 50%;
    pointer-events: none; z-index: 9998;
    transition: all 0.15s ease;
  }

  /* NOISE OVERLAY */
  body::before {
    content: '';
    position: fixed; inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none; z-index: 0; opacity: 0.4;
  }

  /* NAV */
  nav {
    position: fixed; top: 0; left: 0; right: 0;
    z-index: 100; padding: 1.5rem 3rem;
    display: flex; justify-content: space-between; align-items: center;
    background: rgba(10,10,15,0.8);
    backdrop-filter: blur(20px);
    border-bottom: 1px solid var(--border);
  }
  .nav-logo {
    font-family: 'Space Mono', monospace;
    font-size: 1rem; color: var(--accent);
    letter-spacing: 2px;
  }
  .nav-links { display: flex; gap: 2.5rem; list-style: none; }
  .nav-links a {
    color: var(--muted); text-decoration: none;
    font-size: 0.85rem; font-weight: 600; letter-spacing: 1px;
    text-transform: uppercase; transition: color 0.3s;
    position: relative;
  }
  .nav-links a::after {
    content: ''; position: absolute; bottom: -4px; left: 0;
    width: 0; height: 1px; background: var(--accent);
    transition: width 0.3s;
  }
  .nav-links a:hover { color: var(--accent); }
  .nav-links a:hover::after { width: 100%; }

  /* HERO */
  .hero {
    min-height: 100vh; display: flex; align-items: center;
    padding: 0 3rem; position: relative; overflow: hidden;
  }
  .hero-bg {
    position: absolute; inset: 0; z-index: 0;
    background: radial-gradient(ellipse 80% 60% at 70% 50%, rgba(124,58,237,0.12) 0%, transparent 70%),
                radial-gradient(ellipse 50% 40% at 20% 80%, rgba(0,255,136,0.08) 0%, transparent 60%);
  }
  .hero-grid {
    position: absolute; inset: 0;
    background-image: linear-gradient(rgba(255,255,255,0.02) 1px, transparent 1px),
                      linear-gradient(90deg, rgba(255,255,255,0.02) 1px, transparent 1px);
    background-size: 60px 60px;
    mask-image: radial-gradient(ellipse at center, black 30%, transparent 80%);
  }
  .hero-content { position: relative; z-index: 1; max-width: 900px; }
  .hero-tag {
    display: inline-flex; align-items: center; gap: 0.5rem;
    font-family: 'Space Mono', monospace; font-size: 0.75rem;
    color: var(--accent); letter-spacing: 3px; text-transform: uppercase;
    margin-bottom: 1.5rem;
    border: 1px solid rgba(0,255,136,0.3); padding: 0.4rem 1rem;
    border-radius: 2px;
    animation: fadeSlideUp 0.8s ease both;
  }
  .hero-tag::before {
    content: ''; width: 6px; height: 6px;
    background: var(--accent); border-radius: 50%;
    animation: pulse 2s infinite;
  }
  @keyframes pulse { 0%,100%{opacity:1;transform:scale(1)} 50%{opacity:0.5;transform:scale(0.7)} }

  .hero h1 {
    font-family: 'Syne', sans-serif;
    font-size: clamp(3.5rem, 8vw, 7rem);
    font-weight: 800; line-height: 0.95;
    letter-spacing: -2px;
    animation: fadeSlideUp 0.8s 0.15s ease both;
  }
  .hero h1 .line2 {
    display: block; color: transparent;
    -webkit-text-stroke: 1px rgba(255,255,255,0.3);
  }
  .hero h1 .accent-word {
    color: var(--accent);
    -webkit-text-stroke: 0;
  }
  .hero-sub {
    margin-top: 2rem; max-width: 500px;
    color: var(--muted); font-size: 1.1rem; line-height: 1.7;
    animation: fadeSlideUp 0.8s 0.3s ease both;
  }
  .hero-cta {
    margin-top: 3rem; display: flex; gap: 1rem; align-items: center;
    animation: fadeSlideUp 0.8s 0.45s ease both;
  }
  .btn-primary {
    display: inline-flex; align-items: center; gap: 0.5rem;
    background: var(--accent); color: #000;
    padding: 0.85rem 2rem; font-weight: 700; font-size: 0.9rem;
    letter-spacing: 1px; text-transform: uppercase;
    text-decoration: none; border: none; cursor: none;
    transition: all 0.3s; clip-path: polygon(0 0, calc(100% - 12px) 0, 100% 12px, 100% 100%, 12px 100%, 0 calc(100% - 12px));
  }
  .btn-primary:hover { background: #00cc6e; transform: translateY(-2px); }
  .btn-outline {
    display: inline-flex; align-items: center; gap: 0.5rem;
    border: 1px solid var(--border); color: var(--muted);
    padding: 0.85rem 2rem; font-weight: 600; font-size: 0.9rem;
    letter-spacing: 1px; text-transform: uppercase;
    text-decoration: none; transition: all 0.3s; cursor: none;
  }
  .btn-outline:hover { border-color: var(--accent); color: var(--accent); }

  .hero-stats {
    position: absolute; right: 3rem; top: 50%;
    transform: translateY(-50%); z-index: 1;
    display: flex; flex-direction: column; gap: 2rem;
    animation: fadeSlideLeft 0.8s 0.6s ease both;
  }
  .stat { text-align: right; }
  .stat-num {
    font-family: 'Space Mono', monospace;
    font-size: 2.5rem; font-weight: 700; color: var(--text);
    display: block; line-height: 1;
  }
  .stat-label { font-size: 0.75rem; color: var(--muted); letter-spacing: 2px; text-transform: uppercase; }

  /* SCROLL INDICATOR */
  .scroll-ind {
    position: absolute; bottom: 2rem; left: 50%; transform: translateX(-50%);
    display: flex; flex-direction: column; align-items: center; gap: 0.5rem;
    font-family: 'Space Mono', monospace; font-size: 0.7rem; color: var(--muted);
    letter-spacing: 2px; animation: fadeSlideUp 1s 1s ease both;
  }
  .scroll-line {
    width: 1px; height: 50px; background: linear-gradient(to bottom, var(--muted), transparent);
    animation: scrollLine 2s infinite;
  }
  @keyframes scrollLine { 0%{transform:scaleY(0);transform-origin:top} 50%{transform:scaleY(1);transform-origin:top} 51%{transform:scaleY(1);transform-origin:bottom} 100%{transform:scaleY(0);transform-origin:bottom} }

  @keyframes fadeSlideUp { from{opacity:0;transform:translateY(30px)} to{opacity:1;transform:translateY(0)} }
  @keyframes fadeSlideLeft { from{opacity:0;transform:translate(30px,-50%)} to{opacity:1;transform:translate(0,-50%)} }

  /* SECTION BASICS */
  section { padding: 7rem 3rem; position: relative; }
  .section-label {
    font-family: 'Space Mono', monospace; font-size: 0.7rem;
    color: var(--accent); letter-spacing: 4px; text-transform: uppercase;
    margin-bottom: 1rem;
  }
  .section-title {
    font-family: 'Syne', sans-serif; font-size: clamp(2rem, 4vw, 3.5rem);
    font-weight: 800; line-height: 1.1; letter-spacing: -1px;
    margin-bottom: 3rem;
  }

  /* ABOUT */
  .about { background: var(--surface); }
  .about-grid {
    display: grid; grid-template-columns: 1fr 1fr; gap: 5rem; align-items: start;
  }
  .about-text p {
    color: var(--muted); line-height: 1.9; font-size: 1.05rem;
    margin-bottom: 1.5rem;
  }
  .about-text p strong { color: var(--text); }
  .skills-grid { display: flex; flex-wrap: wrap; gap: 0.5rem; margin-top: 2rem; }
  .skill-tag {
    font-family: 'Space Mono', monospace; font-size: 0.75rem;
    padding: 0.4rem 0.9rem; border: 1px solid var(--border);
    color: var(--muted); letter-spacing: 1px;
    transition: all 0.3s; cursor: default;
  }
  .skill-tag:hover { border-color: var(--accent); color: var(--accent); background: var(--glow); }

  .about-side {}
  .info-block { margin-bottom: 2.5rem; }
  .info-block h3 {
    font-size: 0.7rem; font-weight: 700; letter-spacing: 3px;
    text-transform: uppercase; color: var(--accent); margin-bottom: 1rem;
    font-family: 'Space Mono', monospace;
  }
  .contact-item {
    display: flex; align-items: center; gap: 0.75rem;
    padding: 0.6rem 0; border-bottom: 1px solid var(--border);
    color: var(--muted); font-size: 0.9rem; text-decoration: none;
    transition: color 0.3s;
  }
  .contact-item:hover { color: var(--accent); }
  .contact-item .icon {
    width: 16px; height: 16px; opacity: 0.5; flex-shrink: 0;
  }

  /* EXPERIENCE */
  .experience { background: var(--bg); }
  .exp-list { display: flex; flex-direction: column; gap: 1px; }
  .exp-item {
    display: grid; grid-template-columns: 200px 1fr auto;
    gap: 2rem; align-items: start;
    padding: 2rem; background: var(--card);
    border: 1px solid var(--border); border-left: 3px solid transparent;
    transition: all 0.3s; position: relative; overflow: hidden;
  }
  .exp-item::before {
    content: ''; position: absolute; left: 0; top: 0; bottom: 0; width: 3px;
    background: var(--accent); transform: scaleY(0); transform-origin: bottom;
    transition: transform 0.4s ease;
  }
  .exp-item:hover { background: var(--surface); transform: translateX(4px); }
  .exp-item:hover::before { transform: scaleY(1); }

  .exp-date {
    font-family: 'Space Mono', monospace; font-size: 0.75rem;
    color: var(--muted); line-height: 1.6; padding-top: 0.2rem;
  }
  .exp-role { font-size: 1.2rem; font-weight: 700; margin-bottom: 0.3rem; }
  .exp-company { color: var(--accent); font-size: 0.9rem; font-weight: 600; margin-bottom: 0.75rem; }
  .exp-desc { color: var(--muted); font-size: 0.9rem; line-height: 1.7; }
  .exp-tag {
    font-family: 'Space Mono', monospace; font-size: 0.65rem; letter-spacing: 2px;
    padding: 0.3rem 0.7rem; border: 1px solid var(--border); color: var(--muted);
    text-transform: uppercase; height: fit-content;
  }
  .exp-tag.ml { border-color: rgba(124,58,237,0.5); color: #a78bfa; }
  .exp-tag.dev { border-color: rgba(0,255,136,0.4); color: var(--accent); }
  .exp-tag.hr { border-color: rgba(255,107,53,0.4); color: var(--accent3); }

  /* PROJECTS */
  .projects { background: var(--surface); }
  .projects-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 1.5rem; }
  .project-card {
    background: var(--card); border: 1px solid var(--border);
    padding: 2rem; position: relative; overflow: hidden;
    transition: all 0.4s; group: true;
  }
  .project-card::after {
    content: ''; position: absolute; inset: 0;
    background: linear-gradient(135deg, rgba(0,255,136,0.05), transparent);
    opacity: 0; transition: opacity 0.3s;
  }
  .project-card:hover { border-color: rgba(0,255,136,0.3); transform: translateY(-6px); }
  .project-card:hover::after { opacity: 1; }
  .project-card:nth-child(2) { border-color: rgba(124,58,237,0.2); }
  .project-card:nth-child(2):hover { border-color: rgba(124,58,237,0.5); }
  .project-card:nth-child(2)::after { background: linear-gradient(135deg, rgba(124,58,237,0.08), transparent); }
  .project-card:nth-child(3) { border-color: rgba(255,107,53,0.2); }
  .project-card:nth-child(3):hover { border-color: rgba(255,107,53,0.5); }
  .project-card:nth-child(3)::after { background: linear-gradient(135deg, rgba(255,107,53,0.08), transparent); }

  .project-num {
    font-family: 'Space Mono', monospace; font-size: 0.65rem;
    color: var(--muted); letter-spacing: 3px; margin-bottom: 1.5rem;
    display: block;
  }
  .project-icon {
    width: 44px; height: 44px; margin-bottom: 1.5rem;
    display: flex; align-items: center; justify-content: center;
    border: 1px solid var(--border); font-size: 1.3rem;
  }
  .project-title { font-size: 1.15rem; font-weight: 700; margin-bottom: 0.75rem; }
  .project-desc { color: var(--muted); font-size: 0.875rem; line-height: 1.7; margin-bottom: 1.5rem; }
  .project-tags { display: flex; flex-wrap: wrap; gap: 0.4rem; }
  .project-tag {
    font-family: 'Space Mono', monospace; font-size: 0.65rem;
    padding: 0.2rem 0.6rem; background: rgba(255,255,255,0.04);
    color: var(--muted); letter-spacing: 1px;
  }
  .project-arrow {
    position: absolute; top: 1.5rem; right: 1.5rem;
    width: 32px; height: 32px; display: flex; align-items: center; justify-content: center;
    color: var(--muted); font-size: 1rem;
    opacity: 0; transform: translate(-4px, 4px);
    transition: all 0.3s;
  }
  .project-card:hover .project-arrow { opacity: 1; transform: translate(0, 0); color: var(--accent); }

  /* CERTIFICATIONS */
  .certs { background: var(--bg); }
  .certs-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 1rem; }
  .cert-item {
    display: flex; align-items: center; gap: 1rem;
    padding: 1.5rem 2rem; background: var(--card);
    border: 1px solid var(--border); transition: all 0.3s;
  }
  .cert-item:hover { border-color: rgba(0,255,136,0.3); }
  .cert-dot { width: 8px; height: 8px; background: var(--accent); flex-shrink: 0; }
  .cert-name { font-size: 0.95rem; font-weight: 600; }
  .cert-org { font-size: 0.8rem; color: var(--muted); font-family: 'Space Mono', monospace; margin-top: 0.2rem; }

  /* ACHIEVEMENTS */
  .achievements { background: var(--surface); }
  .ach-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 1.5rem; }
  .ach-card {
    padding: 2.5rem 2rem; text-align: center;
    background: var(--card); border: 1px solid var(--border);
    transition: all 0.3s; position: relative; overflow: hidden;
  }
  .ach-card::before {
    content: ''; position: absolute; top: 0; left: 0; right: 0; height: 2px;
    background: var(--accent); transform: scaleX(0);
    transition: transform 0.4s;
  }
  .ach-card:hover::before { transform: scaleX(1); }
  .ach-card:hover { transform: translateY(-4px); }
  .ach-emoji { font-size: 2rem; margin-bottom: 1rem; display: block; }
  .ach-title { font-size: 1.05rem; font-weight: 700; line-height: 1.4; }
  .ach-desc { font-size: 0.85rem; color: var(--muted); margin-top: 0.5rem; }

  /* EDUCATION */
  .education { background: var(--bg); }
  .edu-list { display: flex; flex-direction: column; gap: 1.5rem; }
  .edu-item {
    display: flex; gap: 2rem; align-items: start;
    padding: 2rem; background: var(--card); border: 1px solid var(--border);
  }
  .edu-year {
    font-family: 'Space Mono', monospace; font-size: 0.75rem;
    color: var(--muted); white-space: nowrap; padding-top: 0.2rem;
    min-width: 100px;
  }
  .edu-degree { font-size: 1.1rem; font-weight: 700; margin-bottom: 0.3rem; }
  .edu-school { color: var(--accent); font-size: 0.9rem; margin-bottom: 0.25rem; }
  .edu-loc { color: var(--muted); font-size: 0.85rem; }
  .edu-score {
    margin-left: auto; font-family: 'Space Mono', monospace;
    font-size: 1.4rem; font-weight: 700; color: var(--accent);
    text-align: right; flex-shrink: 0;
  }
  .edu-score span { display: block; font-size: 0.65rem; color: var(--muted); letter-spacing: 2px; margin-top: 0.2rem; }

  /* FOOTER */
  footer {
    background: var(--surface); padding: 4rem 3rem;
    border-top: 1px solid var(--border);
    display: flex; justify-content: space-between; align-items: center;
  }
  .footer-left .footer-name {
    font-family: 'Syne', sans-serif; font-size: 1.5rem; font-weight: 800;
  }
  .footer-left p { color: var(--muted); font-size: 0.85rem; margin-top: 0.3rem; }
  .footer-links { display: flex; gap: 1.5rem; }
  .footer-link {
    display: flex; align-items: center; justify-content: center;
    width: 44px; height: 44px; border: 1px solid var(--border);
    color: var(--muted); text-decoration: none; font-size: 0.9rem;
    transition: all 0.3s;
  }
  .footer-link:hover { border-color: var(--accent); color: var(--accent); }
  .footer-copy { font-family: 'Space Mono', monospace; font-size: 0.7rem; color: var(--muted); }

  /* REVEAL ANIMATIONS */
  .reveal {
    opacity: 0; transform: translateY(30px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }
  .reveal.visible { opacity: 1; transform: translateY(0); }

  /* FLOATING ORBS */
  .orb {
    position: absolute; border-radius: 50%; filter: blur(80px); pointer-events: none; z-index: 0;
  }

  /* SCROLLBAR */
  ::-webkit-scrollbar { width: 3px; }
  ::-webkit-scrollbar-track { background: var(--bg); }
  ::-webkit-scrollbar-thumb { background: var(--accent); }

  @media (max-width: 900px) {
    nav { padding: 1rem 1.5rem; }
    .nav-links { gap: 1.2rem; }
    section { padding: 5rem 1.5rem; }
    .hero { padding: 0 1.5rem; }
    .hero-stats { display: none; }
    .about-grid { grid-template-columns: 1fr; gap: 3rem; }
    .exp-item { grid-template-columns: 1fr; gap: 0.5rem; }
    .exp-date { order: -1; }
    .exp-tag { width: fit-content; }
    .projects-grid { grid-template-columns: 1fr; }
    .certs-grid { grid-template-columns: 1fr; }
    .ach-grid { grid-template-columns: 1fr; }
    footer { flex-direction: column; gap: 2rem; text-align: center; }
  }
</style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-trail" id="cursorTrail"></div>

<!-- NAV -->
<nav>
  <div class="nav-logo">RAJ.DEV</div>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#experience">Experience</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#education">Education</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>

<!-- HERO -->
<section class="hero" id="home">
  <div class="hero-bg"></div>
  <div class="hero-grid"></div>
  <div class="hero-content">
    <div class="hero-tag">Available for opportunities</div>
    <h1>
      RAJ<br>
      <span class="line2">KUMAR <span class="accent-word">S</span></span>
    </h1>
    <p class="hero-sub">
      Final-year <strong>CSE (AI & ML)</strong> engineer crafting intelligent systems — from deep learning medical tools to full-stack applications. Bridging technology with people.
    </p>
    <div class="hero-cta">
      <a href="#projects" class="btn-primary">View Projects ↓</a>
      <a href="https://mail.google.com/mail/?view=cm&to=rajkumar101104@gmail.com" class="btn-outline" target="_blank">Get in Touch →</a>
    </div>
  </div>
  <div class="hero-stats">
    <div class="stat">
      <span class="stat-num">5+</span>
      <span class="stat-label">Projects</span>
    </div>
    <div class="stat">
      <span class="stat-num">3</span>
      <span class="stat-label">Internships</span>
    </div>
    <div class="stat">
      <span class="stat-num">97%</span>
      <span class="stat-label">SSLC Score</span>
    </div>
  </div>
  <div class="scroll-ind">
    <div class="scroll-line"></div>
    SCROLL
  </div>
</section>

<!-- ABOUT -->
<section class="about" id="about">
  <div class="orb" style="width:400px;height:400px;background:rgba(0,255,136,0.04);top:-100px;left:-100px;"></div>
  <p class="section-label reveal">01 — About</p>
  <div class="about-grid">
    <div class="about-text reveal">
      <h2 class="section-title">Building at the<br>intersection of <em style="color:var(--accent);font-style:normal">AI</em> & people</h2>
      <p>I'm a final-year <strong>Computer Science Engineering student specializing in AI & ML</strong> at Sri Krishna College of Technology, Coimbatore. My work spans machine learning, deep learning, and full-stack development.</p>
      <p>What sets me apart is a rare combination — deep technical skills paired with a genuine passion for <strong>communication, team coordination, and people management</strong>. I thrive where technology meets human impact.</p>
      <p>From detecting spinopelvic parameters in medical X-rays using <strong>Swin Transformers</strong> to building full-stack Java applications and even doing HR recruitment — I bring versatility to every challenge.</p>
      <div class="skills-grid">
        <span class="skill-tag">Java</span>
        <span class="skill-tag">Python</span>
        <span class="skill-tag">C++</span>
        <span class="skill-tag">SQL</span>
        <span class="skill-tag">JavaScript</span>
        <span class="skill-tag">Spring Boot</span>
        <span class="skill-tag">Deep Learning</span>
        <span class="skill-tag">LLMs</span>
        <span class="skill-tag">REST APIs</span>
        <span class="skill-tag">Docker</span>
        <span class="skill-tag">Kubernetes</span>
        <span class="skill-tag">Git</span>
        <span class="skill-tag">OOP</span>
        <span class="skill-tag">Data Preprocessing</span>
        <span class="skill-tag">HTML</span>
        <span class="skill-tag">CSS</span>
        <span class="skill-tag">React</span>
        <span class="skill-tag">MySQL</span>
      </div>
    </div>
    <div class="about-side reveal" id="contact">
      <div class="info-block">
        <h3>Contact</h3>
        <a href="tel:6381561759" class="contact-item">
          <svg class="icon" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 8V5z"/></svg>
          +91 6381561759
        </a>
        <a href="mailto:rajkumar101104@gmail.com" class="contact-item">
          <svg class="icon" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"/></svg>
          rajkumar101104@gmail.com
        </a>
        <a href="https://linkedin.com/in/raj-kumar-s-91a933258/" target="_blank" class="contact-item">
          <svg class="icon" fill="currentColor" viewBox="0 0 24 24"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
          LinkedIn Profile
        </a>
        <a href="https://github.com/Rajkumar-042" target="_blank" class="contact-item">
          <svg class="icon" fill="currentColor" viewBox="0 0 24 24"><path d="M12 0C5.374 0 0 5.373 0 12c0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23A11.509 11.509 0 0112 5.803c1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576C20.566 21.797 24 17.3 24 12c0-6.627-5.373-12-12-12z"/></svg>
          github.com/Rajkumar-042
        </a>
      </div>
      <div class="info-block">
        <h3>Location</h3>
        <p style="color:var(--muted);font-size:0.9rem;padding-top:0.5rem;">Coimbatore, Tamil Nadu, India</p>
      </div>
      <div class="info-block">
        <h3>Status</h3>
        <p style="color:var(--accent);font-size:0.9rem;padding-top:0.5rem;font-weight:600;">
          🟢 Open to opportunities — Apr 2026 graduation
        </p>
      </div>
    </div>
  </div>
</section>

<!-- EXPERIENCE -->
<section class="experience" id="experience">
  <p class="section-label reveal">02 — Experience</p>
  <h2 class="section-title reveal">Where I've<br>contributed</h2>
  <div class="exp-list">
    <div class="exp-item reveal">
      <div class="exp-date">Oct 2025 – Feb 2026</div>
      <div>
        <div class="exp-role">Java Full Stack Developer</div>
        <div class="exp-company">Inmakes Info Tech Pvt Ltd — Kochi, Kerala</div>
        <div class="exp-desc">Developed backend functionalities using Java and Spring Boot. Integrated frontend, backend, and database components in full-stack applications. Built REST APIs, managed database operations, and improved end-to-end application workflows.</div>
      </div>
      <div class="exp-tag dev">Dev</div>
    </div>
    <div class="exp-item reveal">
      <div class="exp-date">Sep 2025 – Oct 2025</div>
      <div>
        <div class="exp-role">HR Intern</div>
        <div class="exp-company">Webocrates — Coimbatore, Tamil Nadu</div>
        <div class="exp-desc">Screened resumes and shortlisted candidates based on job requirements. Maintained candidate databases and recruitment trackers. Communicated with candidates regarding interview updates and follow-ups.</div>
      </div>
      <div class="exp-tag hr">HR</div>
    </div>
    <div class="exp-item reveal">
      <div class="exp-date">Jun 2024 – Jul 2024</div>
      <div>
        <div class="exp-role">Machine Learning Intern</div>
        <div class="exp-company">Brainery Tech — Coimbatore, Tamil Nadu</div>
        <div class="exp-desc">Worked on machine learning concepts and data analysis for real-world problem statements. Assisted in developing and evaluating ML models. Gained hands-on exposure to data preprocessing and result interpretation.</div>
      </div>
      <div class="exp-tag ml">ML</div>
    </div>
  </div>
</section>

<!-- PROJECTS -->
<section class="projects" id="projects">
  <p class="section-label reveal">03 — Projects</p>
  <h2 class="section-title reveal">Things I've<br>built</h2>
  <div class="projects-grid">

    <div class="project-card reveal">
      <span class="project-num">01 / CURRENT</span>
      <div class="project-icon">🦴</div>
      <div class="project-arrow">↗</div>
      <div class="project-title">Spinopelvic Parameter Detection</div>
      <div class="project-desc">Automated system for detecting and analyzing spinopelvic parameters from medical X-ray images using Swin Transformer architecture. Improves accuracy and consistency over manual clinical methods.</div>
      <div class="project-tags">
        <span class="project-tag">Deep Learning</span>
        <span class="project-tag">Swin Transformer</span>
        <span class="project-tag">Medical Imaging</span>
        <span class="project-tag">Python</span>
      </div>
    </div>

    <div class="project-card reveal">
      <span class="project-num">02 / ML</span>
      <div class="project-icon">🏥</div>
      <div class="project-arrow">↗</div>
      <div class="project-title">Hospital Re-admission Prediction</div>
      <div class="project-desc">ML model to predict hospital readmission risk using patient clinical and demographic data. Performed feature engineering to improve classification performance and enable early healthcare intervention.</div>
      <div class="project-tags">
        <span class="project-tag">Machine Learning</span>
        <span class="project-tag">Healthcare</span>
        <span class="project-tag">Feature Engineering</span>
      </div>
    </div>

    <div class="project-card reveal">
      <span class="project-num">03 / ML</span>
      <div class="project-icon">💧</div>
      <div class="project-arrow">↗</div>
      <div class="project-title">Water Quality Management</div>
      <div class="project-desc">Data-driven system to assess and categorize water quality using pH, turbidity, conductivity, and dissolved solids. Built during ML internship with real-world environmental datasets.</div>
      <div class="project-tags">
        <span class="project-tag">Data Science</span>
        <span class="project-tag">Classification</span>
        <span class="project-tag">Environment</span>
      </div>
    </div>

    <div class="project-card reveal">
      <span class="project-num">04 / AI</span>
      <div class="project-icon">🍳</div>
      <div class="project-arrow">↗</div>
      <div class="project-title">Cook Bot — Recipe ChatBot</div>
      <div class="project-desc">AI-powered chatbot that generates cooking recipes and step-by-step instructions based on user input. Integrates AI APIs with a backend application, featuring a simple and interactive user interface.</div>
      <div class="project-tags">
        <span class="project-tag">AI APIs</span>
        <span class="project-tag">Chatbot</span>
        <span class="project-tag">Backend</span>
        <span class="project-tag">LLM</span>
      </div>
    </div>

    <div class="project-card reveal">
      <span class="project-num">05 / FULL-STACK</span>
      <div class="project-icon">🎯</div>
      <div class="project-arrow">↗</div>
      <div class="project-title">D-Events — Event Management App</div>
      <div class="project-desc">Full-stack web application for event management — create, manage, and register for events. Built with Java, Spring Boot, MySQL, and a responsive front-end with seamless registration workflow.</div>
      <div class="project-tags">
        <span class="project-tag">Java</span>
        <span class="project-tag">Spring Boot</span>
        <span class="project-tag">MySQL</span>
        <span class="project-tag">Full-Stack</span>
      </div>
    </div>

    <div class="project-card reveal" style="background:linear-gradient(135deg,rgba(0,255,136,0.05),var(--card));border-color:rgba(0,255,136,0.2);display:flex;flex-direction:column;justify-content:center;align-items:center;text-align:center;min-height:200px;">
      <div style="font-size:2rem;margin-bottom:1rem;">🚀</div>
      <div style="font-size:1rem;font-weight:700;color:var(--accent);">More coming soon</div>
      <div style="font-size:0.85rem;color:var(--muted);margin-top:0.5rem;">Always building something new</div>
    </div>

  </div>
</section>

<!-- CERTIFICATIONS -->
<section class="certs" id="certifications">
  <p class="section-label reveal">04 — Certifications</p>
  <h2 class="section-title reveal">Credentials &<br>Learning</h2>
  <div class="certs-grid">
    <div class="cert-item reveal">
      <div class="cert-dot"></div>
      <div>
        <div class="cert-name">Data Science for Engineers</div>
        <div class="cert-org">NPTEL</div>
      </div>
    </div>
    <div class="cert-item reveal">
      <div class="cert-dot" style="background:var(--accent2)"></div>
      <div>
        <div class="cert-name">AWS Cloud Computation</div>
        <div class="cert-org">COURSERA</div>
      </div>
    </div>
  </div>
</section>

<!-- ACHIEVEMENTS -->
<section class="achievements" id="achievements">
  <p class="section-label reveal">05 — Achievements</p>
  <h2 class="section-title reveal">Recognition &<br>milestones</h2>
  <div class="ach-grid">
    <div class="ach-card reveal">
      <span class="ach-emoji">🏆</span>
      <div class="ach-title">Smart India Hackathon</div>
      <div class="ach-desc">Shortlisted for one of India's largest hackathons</div>
    </div>
    <div class="ach-card reveal">
      <span class="ach-emoji">🏸</span>
      <div class="ach-title">National Badminton U-19</div>
      <div class="ach-desc">Represented at national level competition</div>
    </div>
    <div class="ach-card reveal">
      <span class="ach-emoji">🥇</span>
      <div class="ach-title">1st Place — Badminton, Coimbatore</div>
      <div class="ach-desc">Won Men's Singles as Team Captain</div>
    </div>
  </div>
</section>

<!-- EDUCATION -->
<section class="education" id="education">
  <p class="section-label reveal">06 — Education</p>
  <h2 class="section-title reveal">Academic<br>background</h2>
  <div class="edu-list">
    <div class="edu-item reveal">
      <div class="edu-year">Oct 2022 –<br>Apr 2026</div>
      <div>
        <div class="edu-degree">B.E — Computer Science & Engineering (AI & ML)</div>
        <div class="edu-school">Sri Krishna College of Technology</div>
        <div class="edu-loc">Coimbatore, Tamil Nadu</div>
      </div>
      <div class="edu-score">🎓<span>CURRENT</span></div>
    </div>
    <div class="edu-item reveal">
      <div class="edu-year">May 2021 –<br>Apr 2022</div>
      <div>
        <div class="edu-degree">Higher Secondary Education (HSE)</div>
        <div class="edu-school">Adharsh Vidhyala Matric Hr Sec School</div>
        <div class="edu-loc">Anthiyur, Erode</div>
      </div>
      <div class="edu-score">83%<span>SCORE</span></div>
    </div>
    <div class="edu-item reveal">
      <div class="edu-year">May 2019 –<br>Mar 2020</div>
      <div>
        <div class="edu-degree">Secondary School Leaving Certificate (SSLC)</div>
        <div class="edu-school">St. Theresa's Matriculation School</div>
        <div class="edu-loc">Anthiyur, Erode</div>
      </div>
      <div class="edu-score">97%<span>SCORE</span></div>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-left">
    <div class="footer-name">Raj Kumar S</div>
    <p>Built with passion · Open to opportunities · Apr 2026</p>
  </div>
  <div class="footer-links">
    <a href="https://github.com/Rajkumar-042" target="_blank" class="footer-link" title="GitHub">
      <svg width="18" fill="currentColor" viewBox="0 0 24 24"><path d="M12 0C5.374 0 0 5.373 0 12c0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23A11.509 11.509 0 0112 5.803c1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576C20.566 21.797 24 17.3 24 12c0-6.627-5.373-12-12-12z"/></svg>
    </a>
    <a href="https://linkedin.com/in/raj-kumar-s-91a933258/" target="_blank" class="footer-link" title="LinkedIn">
      <svg width="18" fill="currentColor" viewBox="0 0 24 24"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
    </a>
    <a href="mailto:rajkumar101104@gmail.com" class="footer-link" title="Email">
      <svg width="18" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"/></svg>
    </a>
  </div>
  <div class="footer-copy">© 2026 Raj Kumar S. All rights reserved.</div>
</footer>

<script>
  // Custom cursor
  const cursor = document.getElementById('cursor');
  const trail = document.getElementById('cursorTrail');
  let mouseX = 0, mouseY = 0, trailX = 0, trailY = 0;

  document.addEventListener('mousemove', (e) => {
    mouseX = e.clientX; mouseY = e.clientY;
    cursor.style.left = mouseX - 6 + 'px';
    cursor.style.top = mouseY - 6 + 'px';
  });

  function animateTrail() {
    trailX += (mouseX - trailX) * 0.12;
    trailY += (mouseY - trailY) * 0.12;
    trail.style.left = trailX - 20 + 'px';
    trail.style.top = trailY - 20 + 'px';
    requestAnimationFrame(animateTrail);
  }
  animateTrail();

  document.querySelectorAll('a, button, .project-card, .exp-item, .ach-card').forEach(el => {
    el.addEventListener('mouseenter', () => {
      cursor.style.transform = 'scale(2.5)';
      trail.style.transform = 'scale(1.5)';
    });
    el.addEventListener('mouseleave', () => {
      cursor.style.transform = 'scale(1)';
      trail.style.transform = 'scale(1)';
    });
  });

  // Scroll reveal
  const reveals = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry, i) => {
      if (entry.isIntersecting) {
        setTimeout(() => entry.target.classList.add('visible'), i * 60);
      }
    });
  }, { threshold: 0.1, rootMargin: '0px 0px -50px 0px' });
  reveals.forEach(el => observer.observe(el));

  // Smooth active nav highlight
  const sections = document.querySelectorAll('section[id]');
  const navLinks = document.querySelectorAll('.nav-links a');
  window.addEventListener('scroll', () => {
    let current = '';
    sections.forEach(sec => {
      if (window.scrollY >= sec.offsetTop - 200) current = sec.getAttribute('id');
    });
    navLinks.forEach(link => {
      link.style.color = link.getAttribute('href') === '#' + current ? 'var(--accent)' : '';
    });
  });

  // Typing effect on hero
  const roles = ['AI Engineer', 'Full-Stack Developer', 'ML Researcher', 'Team Leader'];
  let ri = 0, ci = 0, deleting = false;
  const typeTarget = document.createElement('span');
  typeTarget.style.cssText = 'color:var(--accent3);font-style:normal;';
  document.querySelector('.hero-sub strong').after(typeTarget);

  function type() {
    const role = roles[ri];
    if (!deleting) {
      typeTarget.textContent = ' · ' + role.slice(0, ++ci);
      if (ci === role.length) { deleting = true; setTimeout(type, 1800); return; }
    } else {
      typeTarget.textContent = ' · ' + role.slice(0, --ci);
      if (ci === 0) { deleting = false; ri = (ri + 1) % roles.length; }
    }
    setTimeout(type, deleting ? 50 : 90);
  }
  setTimeout(type, 1200);
</script>
</body>
</html>
