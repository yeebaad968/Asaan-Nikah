<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Asaan Nikah – Find Your Perfect Match</title>
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link href="https://fonts.googleapis.com/css2?family=Amiri:ital,wght@0,400;0,700;1,400&family=Nunito:wght@300;400;500;600;700&display=swap" rel="stylesheet" />

<style>
  /* ─── RESET & BASE ───────────────────────────────── */
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  html { scroll-behavior: smooth; }
  body {
    font-family: 'Nunito', sans-serif;
    background: #faf8f4;
    color: #2d2d2d;
    overflow-x: hidden;
  }

  /* ─── CSS VARIABLES ──────────────────────────────── */
  :root {
    --cream:   #faf8f4;
    --sand:    #f0ebe0;
    --blush:   #e8d5c4;
    --rose:    #c9856a;
    --rose-d:  #a86550;
    --green:   #3d6b5e;
    --green-l: #4e8a7a;
    --gold:    #c4973a;
    --dark:    #1e1e1e;
    --text:    #3a3530;
    --muted:   #7a7068;
  }

  /* ─── NAVBAR ─────────────────────────────────────── */
  nav {
    position: fixed; top: 0; width: 100%; z-index: 999;
    padding: 1rem 2rem;
    display: flex; align-items: center; justify-content: space-between;
    background: rgba(250,248,244,0.92);
    backdrop-filter: blur(10px);
    border-bottom: 1px solid rgba(196,151,58,0.15);
    transition: box-shadow 0.3s;
  }
  nav.scrolled { box-shadow: 0 2px 20px rgba(0,0,0,0.08); }
  .nav-logo {
    font-family: 'Amiri', serif;
    font-size: 1.6rem;
    color: var(--green);
    letter-spacing: 0.02em;
  }
  .nav-logo span { color: var(--rose); }
  .nav-links { display: flex; gap: 2rem; list-style: none; }
  .nav-links a {
    text-decoration: none;
    font-size: 0.9rem;
    font-weight: 600;
    color: var(--text);
    letter-spacing: 0.04em;
    transition: color 0.2s;
  }
  .nav-links a:hover { color: var(--green); }
  .nav-cta {
    background: var(--green);
    color: #fff !important;
    padding: 0.5rem 1.3rem;
    border-radius: 50px;
    transition: background 0.2s !important;
  }
  .nav-cta:hover { background: var(--green-l) !important; color: #fff !important; }

  /* hamburger */
  .hamburger { display: none; flex-direction: column; gap: 5px; cursor: pointer; }
  .hamburger span { width: 24px; height: 2px; background: var(--text); border-radius: 2px; transition: 0.3s; }
  .mobile-menu {
    display: none; position: fixed; top: 64px; left: 0; right: 0; z-index: 998;
    background: var(--cream); padding: 1.5rem 2rem;
    border-bottom: 1px solid var(--sand);
    flex-direction: column; gap: 1.2rem;
  }
  .mobile-menu.open { display: flex; }
  .mobile-menu a {
    text-decoration: none; font-size: 1rem; font-weight: 600;
    color: var(--text); transition: color 0.2s;
  }
  .mobile-menu a:hover { color: var(--green); }

  /* ─── HERO ───────────────────────────────────────── */
  .hero {
    min-height: 100vh;
    display: flex; align-items: center; justify-content: center;
    text-align: center;
    padding: 8rem 1.5rem 5rem;
    position: relative;
    overflow: hidden;
    background: linear-gradient(160deg, #f5f0e8 0%, #faf8f4 60%, #ede8e0 100%);
  }

  /* Geometric SVG background pattern */
  .hero-pattern {
    position: absolute; inset: 0; opacity: 0.06; pointer-events: none;
    background-image: url("data:image/svg+xml,%3Csvg width='80' height='80' viewBox='0 0 80 80' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='none' stroke='%233d6b5e' stroke-width='1'%3E%3Cpolygon points='40,4 76,22 76,58 40,76 4,58 4,22'/%3E%3Cpolygon points='40,14 66,27 66,53 40,66 14,53 14,27'/%3E%3Cpolygon points='40,24 56,32 56,48 40,56 24,48 24,32'/%3E%3C/g%3E%3C/svg%3E");
    background-size: 80px 80px;
  }

  /* Decorative arches */
  .hero-arch {
    position: absolute; bottom: -2px; left: 0; right: 0;
    height: 80px;
    background: var(--cream);
    clip-path: ellipse(60% 100% at 50% 100%);
  }

  .hero-content { position: relative; z-index: 1; max-width: 720px; }

  .hero-bismillah {
    font-family: 'Amiri', serif;
    font-size: 1.6rem;
    color: var(--gold);
    letter-spacing: 0.1em;
    margin-bottom: 1.2rem;
    opacity: 0;
    animation: fadeUp 0.8s 0.1s forwards;
  }

  .hero-tag {
    display: inline-block;
    background: var(--green);
    color: #fff;
    font-size: 0.75rem;
    font-weight: 700;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    padding: 0.3rem 1rem;
    border-radius: 50px;
    margin-bottom: 1.4rem;
    opacity: 0;
    animation: fadeUp 0.8s 0.25s forwards;
  }

  .hero h1 {
    font-family: 'Amiri', serif;
    font-size: clamp(2.6rem, 6vw, 4.4rem);
    line-height: 1.15;
    color: var(--text);
    margin-bottom: 1.2rem;
    opacity: 0;
    animation: fadeUp 0.8s 0.4s forwards;
  }
  .hero h1 em { color: var(--rose); font-style: normal; }

  .hero-sub {
    font-size: clamp(1rem, 2.2vw, 1.15rem);
    color: var(--muted);
    line-height: 1.75;
    max-width: 560px;
    margin: 0 auto 2.5rem;
    font-weight: 400;
    opacity: 0;
    animation: fadeUp 0.8s 0.55s forwards;
  }

  .hero-actions {
    display: flex; flex-wrap: wrap; gap: 1rem; justify-content: center;
    opacity: 0;
    animation: fadeUp 0.8s 0.7s forwards;
  }

  .btn-primary {
    display: inline-flex; align-items: center; gap: 0.5rem;
    background: var(--green);
    color: #fff;
    font-family: 'Nunito', sans-serif;
    font-size: 1rem; font-weight: 700;
    padding: 0.9rem 2rem;
    border-radius: 50px;
    text-decoration: none;
    border: none; cursor: pointer;
    transition: background 0.25s, transform 0.2s, box-shadow 0.25s;
    box-shadow: 0 4px 18px rgba(61,107,94,0.3);
  }
  .btn-primary:hover {
    background: var(--green-l);
    transform: translateY(-2px);
    box-shadow: 0 8px 24px rgba(61,107,94,0.35);
  }
  .btn-secondary {
    display: inline-flex; align-items: center; gap: 0.5rem;
    background: transparent;
    color: var(--green);
    font-family: 'Nunito', sans-serif;
    font-size: 1rem; font-weight: 700;
    padding: 0.9rem 2rem;
    border-radius: 50px;
    text-decoration: none;
    border: 2px solid var(--green);
    transition: background 0.25s, color 0.25s, transform 0.2s;
  }
  .btn-secondary:hover {
    background: var(--green);
    color: #fff;
    transform: translateY(-2px);
  }

  /* stats row */
  .hero-stats {
    display: flex; flex-wrap: wrap; justify-content: center; gap: 2rem;
    margin-top: 3.5rem;
    opacity: 0;
    animation: fadeUp 0.8s 0.9s forwards;
  }
  .stat { text-align: center; }
  .stat-number {
    font-family: 'Amiri', serif;
    font-size: 2rem; font-weight: 700;
    color: var(--green);
    line-height: 1;
  }
  .stat-label { font-size: 0.8rem; color: var(--muted); margin-top: 0.2rem; letter-spacing: 0.05em; }

  /* ─── SECTION SHARED ──────────────────────────────── */
  section { padding: 5rem 1.5rem; }
  .section-inner { max-width: 1100px; margin: 0 auto; }
  .section-label {
    font-size: 0.75rem; font-weight: 700; letter-spacing: 0.14em; text-transform: uppercase;
    color: var(--gold); margin-bottom: 0.6rem;
  }
  .section-title {
    font-family: 'Amiri', serif;
    font-size: clamp(1.9rem, 4vw, 2.8rem);
    color: var(--text); margin-bottom: 0.8rem; line-height: 1.2;
  }
  .section-sub {
    color: var(--muted); font-size: 1rem; line-height: 1.7;
    max-width: 600px;
  }

  /* ─── WHY US ──────────────────────────────────────── */
  .why { background: var(--cream); }
  .why-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
    gap: 1.5rem;
    margin-top: 3rem;
  }
  .why-card {
    background: #fff;
    border-radius: 18px;
    padding: 2rem 1.8rem;
    border: 1px solid rgba(196,151,58,0.12);
    transition: transform 0.3s, box-shadow 0.3s;
    position: relative; overflow: hidden;
  }
  .why-card::before {
    content: '';
    position: absolute; top: 0; left: 0; right: 0; height: 3px;
    background: linear-gradient(90deg, var(--green), var(--gold));
    border-radius: 18px 18px 0 0;
  }
  .why-card:hover { transform: translateY(-6px); box-shadow: 0 12px 32px rgba(0,0,0,0.08); }
  .why-icon {
    width: 52px; height: 52px; border-radius: 14px;
    background: linear-gradient(135deg, #e8f2ef, #d0e8e2);
    display: flex; align-items: center; justify-content: center;
    font-size: 1.5rem; margin-bottom: 1.2rem;
  }
  .why-card h3 {
    font-family: 'Amiri', serif;
    font-size: 1.25rem; color: var(--text);
    margin-bottom: 0.5rem;
  }
  .why-card p { font-size: 0.9rem; color: var(--muted); line-height: 1.65; }

  /* ─── HOW IT WORKS ───────────────────────────────── */
  .how { background: var(--sand); }
  .steps {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 2rem; margin-top: 3rem; position: relative;
  }
  .step { text-align: center; position: relative; }
  .step-num {
    width: 56px; height: 56px; border-radius: 50%;
    background: var(--green); color: #fff;
    font-family: 'Amiri', serif; font-size: 1.4rem; font-weight: 700;
    display: flex; align-items: center; justify-content: center;
    margin: 0 auto 1.2rem;
    box-shadow: 0 4px 14px rgba(61,107,94,0.35);
  }
  .step h3 {
    font-family: 'Amiri', serif;
    font-size: 1.15rem; color: var(--text); margin-bottom: 0.5rem;
  }
  .step p { font-size: 0.88rem; color: var(--muted); line-height: 1.65; }

  /* ─── TESTIMONIALS ────────────────────────────────── */
  .testimonials { background: var(--cream); }
  .testi-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 1.5rem; margin-top: 3rem;
  }
  .testi-card {
    background: #fff;
    border-radius: 18px;
    padding: 2rem;
    border: 1px solid rgba(0,0,0,0.05);
    box-shadow: 0 2px 12px rgba(0,0,0,0.04);
    position: relative;
  }
  .testi-quote {
    font-size: 2.5rem; color: var(--blush); line-height: 1;
    font-family: Georgia, serif; margin-bottom: 0.5rem;
  }
  .testi-card p {
    font-size: 0.92rem; color: var(--muted);
    line-height: 1.7; margin-bottom: 1.2rem;
    font-style: italic;
  }
  .testi-author {
    display: flex; align-items: center; gap: 0.8rem;
  }
  .testi-avatar {
    width: 40px; height: 40px; border-radius: 50%;
    background: linear-gradient(135deg, var(--green), var(--gold));
    display: flex; align-items: center; justify-content: center;
    color: #fff; font-weight: 700; font-size: 0.9rem;
  }
  .testi-name { font-weight: 700; font-size: 0.9rem; color: var(--text); }
  .testi-loc { font-size: 0.78rem; color: var(--muted); }
  .testi-stars { color: var(--gold); font-size: 0.85rem; margin-bottom: 0.2rem; }

  /* ─── VALUES / ISLAMIC SECTION ───────────────────── */
  .values {
    background: var(--green);
    color: #fff;
    text-align: center;
    padding: 5rem 1.5rem;
  }
  .values .section-label { color: var(--gold); }
  .values .section-title { color: #fff; margin: 0 auto 1rem; }
  .values .section-sub { color: rgba(255,255,255,0.75); margin: 0 auto 3rem; }
  .values-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 1.5rem;
    max-width: 900px; margin: 0 auto;
  }
  .value-item {
    background: rgba(255,255,255,0.08);
    border: 1px solid rgba(255,255,255,0.12);
    border-radius: 16px;
    padding: 1.8rem 1.5rem;
    transition: background 0.3s;
  }
  .value-item:hover { background: rgba(255,255,255,0.14); }
  .value-item .vi-icon { font-size: 1.8rem; margin-bottom: 0.8rem; }
  .value-item h4 { font-family: 'Amiri', serif; font-size: 1.1rem; margin-bottom: 0.4rem; }
  .value-item p { font-size: 0.83rem; color: rgba(255,255,255,0.7); line-height: 1.6; }

  /* ─── CTA / WHATSAPP ─────────────────────────────── */
  .cta-section {
    background: linear-gradient(135deg, #f5f0e8, #faf8f4);
    text-align: center;
    padding: 6rem 1.5rem;
  }
  .cta-section .section-title { color: var(--text); }
  .cta-section .section-sub { margin: 0 auto 2.5rem; }
  .whatsapp-btn {
    display: inline-flex; align-items: center; gap: 0.7rem;
    background: #25D366;
    color: #fff;
    font-family: 'Nunito', sans-serif;
    font-size: 1.1rem; font-weight: 700;
    padding: 1rem 2.4rem;
    border-radius: 50px;
    text-decoration: none;
    border: none; cursor: pointer;
    transition: background 0.25s, transform 0.2s, box-shadow 0.25s;
    box-shadow: 0 6px 24px rgba(37,211,102,0.4);
  }
  .whatsapp-btn:hover {
    background: #1ebe5d;
    transform: translateY(-3px);
    box-shadow: 0 10px 30px rgba(37,211,102,0.45);
  }
  .whatsapp-btn svg { width: 24px; height: 24px; fill: #fff; }
  .cta-note { margin-top: 1.2rem; font-size: 0.83rem; color: var(--muted); }

  /* ─── FOOTER ─────────────────────────────────────── */
  footer {
    background: var(--dark); color: rgba(255,255,255,0.6);
    text-align: center; padding: 2.5rem 1.5rem;
    font-size: 0.85rem;
  }
  footer .footer-logo {
    font-family: 'Amiri', serif; font-size: 1.5rem; color: #fff;
    margin-bottom: 0.5rem;
  }
  footer .footer-logo span { color: var(--rose); }
  footer p { margin-bottom: 0.3rem; }
  footer a { color: var(--gold); text-decoration: none; }

  /* ─── ANIMATIONS ─────────────────────────────────── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(24px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  .reveal {
    opacity: 0; transform: translateY(28px);
    transition: opacity 0.65s ease, transform 0.65s ease;
  }
  .reveal.visible { opacity: 1; transform: translateY(0); }

  /* ─── RESPONSIVE ─────────────────────────────────── */
  @media (max-width: 768px) {
    .nav-links { display: none; }
    .hamburger { display: flex; }
    .hero { padding: 7rem 1.2rem 4rem; }
    .hero-stats { gap: 1.2rem; }
    section { padding: 4rem 1.2rem; }
  }
  @media (max-width: 480px) {
    .steps { grid-template-columns: 1fr; }
    .hero-actions { flex-direction: column; align-items: center; }
  }

  /* ─── SCROLL DIVIDER ──────────────────────────────── */
  .wave-divider { width: 100%; overflow: hidden; line-height: 0; }
  .wave-divider svg { display: block; }
</style>
</head>
<body>

<!-- ── NAVBAR ──────────────────────────────────── -->
<nav id="navbar">
  <div class="nav-logo">Asaan <span>Nikah</span></div>
  <ul class="nav-links">
    <li><a href="#why">Why Us</a></li>
    <li><a href="#how">How It Works</a></li>
    <li><a href="#testimonials">Success Stories</a></li>
    <li><a href="#contact" class="nav-cta">Get Started</a></li>
  </ul>
  <div class="hamburger" onclick="toggleMenu()" aria-label="Menu">
    <span></span><span></span><span></span>
  </div>
</nav>
<div class="mobile-menu" id="mobileMenu">
  <a href="#why" onclick="toggleMenu()">Why Us</a>
  <a href="#how" onclick="toggleMenu()">How It Works</a>
  <a href="#testimonials" onclick="toggleMenu()">Success Stories</a>
  <a href="#contact" onclick="toggleMenu()">Get Started →</a>
</div>

<!-- ── HERO ────────────────────────────────────── -->
<section class="hero" id="home">
  <div class="hero-pattern"></div>
  <div class="hero-content">
    <div class="hero-bismillah">بِسْمِ اللَّهِ الرَّحْمَنِ الرَّحِيم</div>
    <span class="hero-tag">Trusted Muslim Matrimonial Service</span>
    <h1>Find Your <em>Perfect</em><br/>Halal Match</h1>
    <p class="hero-sub">Asaan Nikah makes your journey to a blessed marriage simple, sincere, and rooted in Islamic values. Connecting hearts with trust and care.</p>
    <div class="hero-actions">
      <a href="#contact" class="btn-primary">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"></path></svg>
        Contact on WhatsApp
      </a>
      <a href="#how" class="btn-secondary">Learn How It Works</a>
    </div>
    <div class="hero-stats">
      <div class="stat">
        <div class="stat-number">500+</div>
        <div class="stat-label">Families Served</div>
      </div>
      <div class="stat">
        <div class="stat-number">120+</div>
        <div class="stat-label">Successful Marriages</div>
      </div>
      <div class="stat">
        <div class="stat-number">100%</div>
        <div class="stat-label">Halal Process</div>
      </div>
    </div>
  </div>
  <div class="hero-arch"></div>
</section>

<!-- ── WHY ASAAN NIKAH ─────────────────────────── -->
<section class="why" id="why">
  <div class="section-inner">
    <div class="reveal">
      <div class="section-label">Why Choose Us</div>
      <h2 class="section-title">Marriage Made Meaningful</h2>
      <p class="section-sub">We combine caring personal guidance with a values-driven approach — so you can focus on finding the right person.</p>
    </div>
    <div class="why-grid">
      <div class="why-card reveal">
        <div class="why-icon">🤲</div>
        <h3>Wali-Friendly Process</h3>
        <p>Our process fully respects the role of parents and guardians (wali) at every stage — family involvement is not optional, it's central.</p>
      </div>
      <div class="why-card reveal">
        <div class="why-icon">🛡️</div>
        <h3>Privacy & Safety First</h3>
        <p>Your personal details are never shared without your explicit consent. We vet every profile personally before any introduction.</p>
      </div>
      <div class="why-card reveal">
        <div class="why-icon">💬</div>
        <h3>Personal Matchmaking</h3>
        <p>No algorithms, no swiping. Real human consultation to understand your needs and find genuinely compatible matches.</p>
      </div>
      <div class="why-card reveal">
        <div class="why-icon">🌍</div>
        <h3>Diverse Community</h3>
        <p>Serving Muslims from all backgrounds, ethnicities, and madhabs — unity in diversity, guided by shared values.</p>
      </div>
    </div>
  </div>
</section>

<!-- ── HOW IT WORKS ────────────────────────────── -->
<section class="how" id="how">
  <div class="section-inner">
    <div class="reveal" style="text-align:center; max-width: 600px; margin: 0 auto 0;">
      <div class="section-label">The Process</div>
      <h2 class="section-title">Simple. Transparent. Halal.</h2>
      <p class="section-sub">Getting started takes just a few minutes. Here's how we guide you every step of the way.</p>
    </div>
    <div class="steps">
      <div class="step reveal">
        <div class="step-num">1</div>
        <h3>Register & Share</h3>
        <p>Contact us via WhatsApp and share a brief profile about yourself, your deen, and what you're looking for in a spouse.</p>
      </div>
      <div class="step reveal">
        <div class="step-num">2</div>
        <h3>Personal Consultation</h3>
        <p>Our team speaks with you (and your family) to understand your priorities, values, and expectations deeply.</p>
      </div>
      <div class="step reveal">
        <div class="step-num">3</div>
        <h3>Curated Introductions</h3>
        <p>We present carefully selected profiles that truly align with your needs — no flood of random suggestions.</p>
      </div>
      <div class="step reveal">
        <div class="step-num">4</div>
        <h3>Guided Meetings</h3>
        <p>Introductions happen with proper Islamic etiquette — chaperoned, respectful, and focused on what matters.</p>
      </div>
    </div>
  </div>
</section>

<!-- ── ISLAMIC VALUES ──────────────────────────── -->
<section class="values">
  <div class="section-label">Our Foundation</div>
  <h2 class="section-title">Rooted in Islamic Values</h2>
  <p class="section-sub">"And among His signs is that He created for you mates from among yourselves, that you may dwell in tranquility with them." — Qur'an 30:21</p>
  <div class="values-grid">
    <div class="value-item reveal">
      <div class="vi-icon">☪️</div>
      <h4>Taqwa-Centred</h4>
      <p>Deen and character come first. We prioritise faith over appearance or status.</p>
    </div>
    <div class="value-item reveal">
      <div class="vi-icon">🤝</div>
      <h4>Family Honour</h4>
      <p>We work with families respectfully, preserving tradition and family dignity.</p>
    </div>
    <div class="value-item reveal">
      <div class="vi-icon">💎</div>
      <h4>Honest & Clear</h4>
      <p>No false promises. We give honest guidance and transparent expectations.</p>
    </div>
    <div class="value-item reveal">
      <div class="vi-icon">🕊️</div>
      <h4>Barakah in Process</h4>
      <p>Every step is conducted with sincerity, making dua central to our work.</p>
    </div>
  </div>
</section>

<!-- ── TESTIMONIALS ────────────────────────────── -->
<section class="testimonials" id="testimonials">
  <div class="section-inner">
    <div class="reveal" style="text-align:center; max-width:600px; margin: 0 auto 0;">
      <div class="section-label">Alhamdulillah</div>
      <h2 class="section-title">Love Stories That Began Here</h2>
      <p class="section-sub">Real couples who found their partner through Asaan Nikah — with Allah's blessings and our guidance.</p>
    </div>
    <div class="testi-grid">
      <div class="testi-card reveal">
        <div class="testi-stars">★★★★★</div>
        <div class="testi-quote">"</div>
        <p>I was skeptical at first, but Asaan Nikah's team was so warm and professional. Within three months, they introduced me to my husband. Alhamdulillah, we've been happily married for over a year.</p>
        <div class="testi-author">
          <div class="testi-avatar">SA</div>
          <div>
            <div class="testi-name">Sister Amina</div>
            <div class="testi-loc">Muscat, Oman</div>
          </div>
        </div>
      </div>
      <div class="testi-card reveal">
        <div class="testi-stars">★★★★★</div>
        <div class="testi-quote">"</div>
        <p>The team truly listened. They found someone who shared my deen and my life goals. What stood out was how respectfully they handled everything — my parents felt completely at ease.</p>
        <div class="testi-author">
          <div class="testi-avatar">BR</div>
          <div>
            <div class="testi-name">Brother Yusuf</div>
            <div class="testi-loc">Dubai, UAE</div>
          </div>
        </div>
      </div>
      <div class="testi-card reveal">
        <div class="testi-stars">★★★★★</div>
        <div class="testi-quote">"</div>
        <p>As a revert, I was nervous about the process. But Asaan Nikah made it so welcoming and judgement-free. JazakAllah khair for finding me such a kind and caring partner.</p>
        <div class="testi-author">
          <div class="testi-avatar">SK</div>
          <div>
            <div class="testi-name">Sister Khadijah</div>
            <div class="testi-loc">London, UK</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ── CTA / WHATSAPP ──────────────────────────── -->
<section class="cta-section" id="contact">
  <div class="section-inner">
    <div class="reveal">
      <div class="section-label">Begin Your Journey</div>
      <h2 class="section-title">Ready to Find Your<br/>Perfect Companion?</h2>
      <p class="section-sub" style="margin: 0 auto 2.5rem;">Drop us a message on WhatsApp and our team will respond within 24 hours. No commitment required — just a warm, private conversation.</p>
      <!-- Replace +96XXXXXXXXX with your actual WhatsApp number -->
      <a href="https://wa.me/96XXXXXXXXX?text=Assalamu%20Alaikum!%20I%20am%20interested%20in%20learning%20more%20about%20Asaan%20Nikah." class="whatsapp-btn" target="_blank" rel="noopener">
        <svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413Z"/></svg>
        Chat With Us on WhatsApp
      </a>
      <p class="cta-note">🔒 Your privacy is sacred to us. All enquiries are 100% confidential.</p>
    </div>
  </div>
</section>

<!-- ── FOOTER ──────────────────────────────────── -->
<footer>
  <div class="footer-logo">Asaan <span>Nikah</span></div>
  <p>Helping Muslim families find blessed companionship, one heart at a time.</p>
  <p style="margin-top:1rem;">© 2025 Asaan Nikah. All rights reserved. | <a href="mailto:hello@asaannikah.com">hello@asaannikah.com</a></p>
  <p style="margin-top:0.5rem; font-size:0.75rem; color:rgba(255,255,255,0.3);">Built with care & barakah 🤍</p>
</footer>

<!-- ── JAVASCRIPT ───────────────────────────────── -->
<script>
  // Navbar scroll effect
  const navbar = document.getElementById('navbar');
  window.addEventListener('scroll', () => {
    navbar.classList.toggle('scrolled', window.scrollY > 30);
  });

  // Mobile menu
  function toggleMenu() {
    document.getElementById('mobileMenu').classList.toggle('open');
  }
  // Close on outside click
  document.addEventListener('click', (e) => {
    const menu = document.getElementById('mobileMenu');
    const ham = document.querySelector('.hamburger');
    if (!menu.contains(e.target) && !ham.contains(e.target)) {
      menu.classList.remove('open');
    }
  });

  // Scroll reveal
  const reveals = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry, i) => {
      if (entry.isIntersecting) {
        setTimeout(() => entry.target.classList.add('visible'), i * 80);
        observer.unobserve(entry.target);
      }
    });
  }, { threshold: 0.12 });
  reveals.forEach(el => observer.observe(el));
</script>
</body>
</html>
