<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>BloxySecurity | Roblox Anti-Exploit Testing</title>
  <meta name="description" content="BloxySecurity provides permission-based Roblox anti-exploit testing, RemoteEvent reviews, and secure scripting reports for developers." />
  <link rel="icon" href="Bloxy Security Emblem.png" />
  <style>
    :root {
      --bg: #2a0f05;
      --bg-2: #4b1d08;
      --cola: #331205;
      --cola-light: #6b2d0b;
      --gold: #c5c316;
      --gold-bright: #f2ef49;
      --gold-soft: #fff48f;
      --foam: #fff4cc;
      --cream: #ffe9a8;
      --cyan: #87e6f4;
      --cyan-dark: #1e6a70;
      --text: #fff7dc;
      --muted: #ecd992;
      --line: rgba(255, 244, 143, .22);
      --panel: rgba(57, 22, 6, .82);
      --panel-2: rgba(94, 43, 9, .72);
      --success: #9cffce;
      --warning: #ffdb55;
      --shadow: 0 28px 90px rgba(0, 0, 0, .45);
      --radius: 24px;
    }

    * { box-sizing: border-box; margin: 0; padding: 0; }
    html { scroll-behavior: smooth; }

    body {
      font-family: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
      color: var(--text);
      line-height: 1.6;
      min-height: 100vh;
      background:
        radial-gradient(circle at 18% 10%, rgba(242, 239, 73, .25), transparent 31%),
        radial-gradient(circle at 86% 8%, rgba(135, 230, 244, .14), transparent 29%),
        radial-gradient(circle at 58% 100%, rgba(107, 45, 11, .55), transparent 42%),
        linear-gradient(110deg, #421506 0%, #5b2509 43%, #a79d11 100%);
      overflow-x: hidden;
    }

    body::before {
      content: "";
      position: fixed;
      inset: 0;
      pointer-events: none;
      background-image:
        radial-gradient(circle, rgba(255, 244, 143, .22) 0 2px, transparent 3px),
        radial-gradient(circle, rgba(255, 255, 255, .16) 0 1px, transparent 2px);
      background-size: 86px 86px, 132px 132px;
      background-position: 16px 24px, 60px 70px;
      opacity: .55;
      mix-blend-mode: screen;
    }

    a { color: inherit; text-decoration: none; }
    img { max-width: 100%; display: block; }

    .container {
      width: min(1140px, calc(100% - 36px));
      margin: 0 auto;
    }

    header {
      position: sticky;
      top: 0;
      z-index: 20;
      backdrop-filter: blur(18px);
      background: rgba(42, 15, 5, .82);
      border-bottom: 1px solid var(--line);
    }

    .nav {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 20px;
      padding: 14px 0;
    }

    .brand {
      display: flex;
      align-items: center;
      gap: 12px;
      font-weight: 950;
      letter-spacing: .2px;
    }

    .brand img {
      width: 48px;
      height: 48px;
      object-fit: cover;
      border-radius: 14px;
      box-shadow: 0 0 0 1px rgba(255,244,143,.24), 0 0 28px rgba(242,239,73,.18);
    }

    .brand span {
      color: var(--cyan);
      text-shadow: 0 3px 0 rgba(30,106,112,.65);
      font-size: 18px;
    }

    .nav-links {
      display: flex;
      align-items: center;
      gap: 22px;
      color: var(--cream);
      font-size: 14px;
      font-weight: 750;
    }

    .nav-links a:hover { color: var(--gold-bright); }

    .btn {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
      padding: 12px 18px;
      border-radius: 999px;
      border: 1px solid rgba(255,244,143,.30);
      font-weight: 900;
      cursor: pointer;
      transition: transform .18s ease, box-shadow .18s ease, background .18s ease, border-color .18s ease;
      box-shadow: inset 0 -2px 0 rgba(0,0,0,.18);
    }

    .btn:hover {
      transform: translateY(-2px);
      border-color: rgba(242,239,73,.74);
      box-shadow: 0 16px 35px rgba(0,0,0,.25), inset 0 -2px 0 rgba(0,0,0,.18);
    }

    .btn-primary {
      color: #2a0f05;
      background: linear-gradient(135deg, var(--gold-bright), var(--gold-soft));
      border: none;
    }

    .btn-secondary {
      background: rgba(255,244,143,.08);
      color: var(--foam);
    }

    .hero { padding: 76px 0 52px; }

    .hero-grid {
      display: grid;
      grid-template-columns: 1fr .92fr;
      gap: 46px;
      align-items: center;
    }

    .eyebrow {
      display: inline-flex;
      align-items: center;
      gap: 9px;
      margin-bottom: 22px;
      padding: 8px 13px;
      border-radius: 999px;
      border: 1px solid var(--line);
      background: rgba(51,18,5,.48);
      color: var(--cream);
      font-size: 13px;
      font-weight: 850;
      box-shadow: inset 0 -2px 0 rgba(0,0,0,.16);
    }

    .bubble {
      width: 9px;
      height: 9px;
      border-radius: 50%;
      background: var(--gold-bright);
      box-shadow: 0 0 22px rgba(242,239,73,.75);
    }

    h1 {
      max-width: 740px;
      font-size: clamp(42px, 6vw, 74px);
      line-height: .96;
      letter-spacing: -2.4px;
      margin-bottom: 22px;
    }

    .soda-text {
      color: var(--cyan);
      text-shadow: 0 5px 0 rgba(30,106,112,.65), 0 0 28px rgba(135,230,244,.28);
    }

    .gold-text {
      color: var(--gold-bright);
      text-shadow: 0 0 26px rgba(242,239,73,.20);
    }

    .hero p {
      color: var(--cream);
      font-size: 18px;
      max-width: 650px;
      margin-bottom: 28px;
    }

    .hero-actions {
      display: flex;
      flex-wrap: wrap;
      gap: 14px;
      margin-bottom: 28px;
    }

    .trust-row {
      display: flex;
      flex-wrap: wrap;
      gap: 11px;
      color: var(--cream);
      font-size: 14px;
      font-weight: 750;
    }

    .pill {
      padding: 8px 12px;
      border-radius: 999px;
      border: 1px solid var(--line);
      background: rgba(51,18,5,.42);
    }

    .hero-art {
      position: relative;
      border-radius: 32px;
      overflow: hidden;
      border: 1px solid rgba(255,244,143,.32);
      background: linear-gradient(135deg, rgba(83,33,6,.88), rgba(179,170,17,.62));
      box-shadow: var(--shadow), inset 0 0 0 1px rgba(255,255,255,.04);
      transform: rotate(1.2deg);
    }

    .hero-art::after {
      content: "";
      position: absolute;
      inset: 0;
      pointer-events: none;
      background: linear-gradient(180deg, transparent 55%, rgba(42,15,5,.42));
    }

    .hero-art img.cover {
      width: 100%;
      height: auto;
      aspect-ratio: 1440 / 456;
      object-fit: contain;
      object-position: center;
      background: linear-gradient(90deg, #5b2108, #b8b014);
    }

    .scan-card {
      position: relative;
      z-index: 2;
      margin: 0 20px 20px;
      transform: translateY(-8px);
      background: rgba(42, 15, 5, .78);
      border: 1px solid rgba(255,244,143,.25);
      border-radius: 22px;
      padding: 18px;
      box-shadow: 0 20px 55px rgba(0,0,0,.28);
      font-family: "SFMono-Regular", Consolas, "Liberation Mono", monospace;
      font-size: 14px;
    }

    .scan-title {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      color: #2a0f05;
      background: linear-gradient(135deg, var(--gold-bright), var(--cream));
      padding: 6px 10px;
      border-radius: 999px;
      font-family: Inter, ui-sans-serif, system-ui, sans-serif;
      font-weight: 950;
      margin-bottom: 12px;
    }

    .line { margin: 9px 0; color: var(--cream); }
    .line b { color: var(--cyan); }
    .line .alert { color: var(--warning); }
    .line .ok { color: var(--success); }

    section { padding: 64px 0; }

    .section-head {
      max-width: 780px;
      margin-bottom: 30px;
    }

    h2 {
      font-size: clamp(30px, 4vw, 48px);
      line-height: 1.08;
      letter-spacing: -1.2px;
      margin-bottom: 12px;
    }

    .section-head p {
      color: var(--cream);
      font-size: 17px;
    }

    .cards {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 18px;
    }

    .card {
      background: var(--panel);
      border: 1px solid var(--line);
      border-radius: var(--radius);
      padding: 24px;
      box-shadow: 0 20px 55px rgba(0,0,0,.22), inset 0 1px 0 rgba(255,255,255,.04);
    }

    .card h3 {
      font-size: 20px;
      margin-bottom: 10px;
    }

    .card p, .card li { color: var(--cream); }

    .icon {
      width: 46px;
      height: 46px;
      border-radius: 16px;
      background: linear-gradient(135deg, rgba(242,239,73,.18), rgba(107,45,11,.68));
      border: 1px solid rgba(255,244,143,.28);
      display: grid;
      place-items: center;
      margin-bottom: 16px;
      font-size: 21px;
      box-shadow: inset 0 -5px 12px rgba(0,0,0,.14);
    }

    .pricing-grid {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 18px;
    }

    .price-card {
      position: relative;
      min-height: 430px;
      display: flex;
      flex-direction: column;
    }

    .price-card.featured {
      border-color: rgba(242,239,73,.65);
      background:
        radial-gradient(circle at 80% 0%, rgba(242,239,73,.20), transparent 32%),
        linear-gradient(180deg, rgba(99,40,8,.90), rgba(42,15,5,.88));
      transform: translateY(-8px);
    }

    .badge {
      position: absolute;
      top: 16px;
      right: 16px;
      font-size: 12px;
      font-weight: 950;
      color: #2a0f05;
      background: var(--gold-bright);
      border-radius: 999px;
      padding: 5px 9px;
    }

    .price {
      font-size: 46px;
      line-height: 1;
      font-weight: 950;
      letter-spacing: -1.7px;
      margin: 16px 0 6px;
      color: var(--cyan);
      text-shadow: 0 3px 0 rgba(30,106,112,.70);
    }

    .price span {
      font-size: 15px;
      color: var(--cream);
      font-weight: 850;
      letter-spacing: 0;
      text-shadow: none;
    }

    .small {
      color: var(--cream);
      font-size: 14px;
      min-height: 44px;
    }

    ul {
      list-style: none;
      margin: 20px 0 24px;
      display: grid;
      gap: 10px;
    }

    li {
      position: relative;
      padding-left: 26px;
      font-size: 14.5px;
    }

    li::before {
      content: "✓";
      position: absolute;
      left: 0;
      top: 0;
      color: var(--gold-bright);
      font-weight: 950;
    }

    .price-card .btn { margin-top: auto; width: 100%; }

    .split {
      display: grid;
      grid-template-columns: .95fr 1.05fr;
      gap: 22px;
      align-items: start;
    }

    .process {
      display: grid;
      gap: 14px;
    }

    .step {
      display: grid;
      grid-template-columns: 54px 1fr;
      gap: 16px;
      align-items: start;
      padding: 20px;
      background: rgba(42, 15, 5, .70);
      border: 1px solid var(--line);
      border-radius: 20px;
      box-shadow: inset 0 1px 0 rgba(255,255,255,.04);
    }

    .step-num {
      width: 44px;
      height: 44px;
      border-radius: 15px;
      background: linear-gradient(135deg, var(--gold-bright), var(--cream));
      color: #2a0f05;
      display: grid;
      place-items: center;
      font-weight: 950;
      box-shadow: inset 0 -4px 0 rgba(0,0,0,.12);
    }

    .step h3 { margin-bottom: 4px; font-size: 18px; }
    .step p { color: var(--cream); font-size: 14.5px; }

    .notice {
      background: rgba(255, 244, 143, .10);
      border: 1px solid rgba(255, 244, 143, .28);
      border-radius: var(--radius);
      padding: 24px;
    }

    .notice h3 { margin-bottom: 10px; }
    .notice p { color: var(--cream); margin-bottom: 12px; }

    .banner-strip {
      margin-top: 22px;
      border-radius: 20px;
      border: 1px solid rgba(255,244,143,.24);
      overflow: hidden;
      box-shadow: 0 18px 45px rgba(0,0,0,.24);
    }

    .banner-strip img {
      width: 100%;
      aspect-ratio: 16 / 5;
      object-fit: cover;
    }

    .faq {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 16px;
    }

    .faq-item {
      background: rgba(42, 15, 5, .70);
      border: 1px solid var(--line);
      border-radius: 20px;
      padding: 22px;
    }

    .faq-item h3 { font-size: 18px; margin-bottom: 8px; }
    .faq-item p { color: var(--cream); font-size: 14.5px; }

    .cta {
      text-align: center;
      background:
        radial-gradient(circle at 20% 0%, rgba(242,239,73,.20), transparent 32%),
        linear-gradient(135deg, rgba(42,15,5,.84), rgba(107,45,11,.70), rgba(167,157,17,.42));
      border: 1px solid rgba(255,244,143,.32);
      border-radius: 34px;
      padding: 48px 24px;
      box-shadow: var(--shadow);
    }

    .cta p {
      max-width: 660px;
      margin: 0 auto 24px;
      color: var(--cream);
      font-size: 17px;
    }

    .contact-box {
      display: inline-grid;
      gap: 6px;
      text-align: left;
      background: rgba(42,15,5,.58);
      border: 1px solid var(--line);
      border-radius: 18px;
      padding: 16px 18px;
      margin-top: 10px;
      color: var(--cream);
      font-size: 14px;
    }

    footer {
      border-top: 1px solid var(--line);
      padding: 26px 0 38px;
      color: var(--cream);
      font-size: 14px;
      background: rgba(42,15,5,.34);
    }

    .footer-grid {
      display: flex;
      justify-content: space-between;
      gap: 16px;
      flex-wrap: wrap;
    }

    @media (max-width: 1000px) {
      .hero-grid, .split { grid-template-columns: 1fr; }
      .pricing-grid { grid-template-columns: repeat(2, 1fr); }
      .cards { grid-template-columns: 1fr; }
      .hero-art { transform: none; }
    }

    @media (max-width: 660px) {
      .nav { align-items: flex-start; }
      .nav-links { display: none; }
      .hero { padding-top: 54px; }
      .hero-actions { flex-direction: column; }
      .btn { width: 100%; }
      .pricing-grid, .faq { grid-template-columns: 1fr; }
      .price-card.featured { transform: none; }
      h1 { letter-spacing: -1.4px; }
    }
  </style>
</head>
<body>
  <!-- Image files should stay named exactly: Bloxy Security Emblem.png and Bloxy Security Cover.png -->
  <header>
    <div class="container nav">
      <a class="brand" href="#top" aria-label="BloxySecurity Home">
        <img src="Bloxy Security Emblem.png" alt="BloxySecurity emblem" />
        <span>BloxySecurity</span>
      </a>
      <nav class="nav-links" aria-label="Main navigation">
        <a href="#services">Services</a>
        <a href="#pricing">Pricing</a>
        <a href="#process">Process</a>
        <a href="#faq">FAQ</a>
        <a class="btn btn-secondary" href="https://discord.gg/vpgpjcB8eG" target="_blank" rel="noopener noreferrer">Book a Review</a>
      </nav>
    </div>
  </header>

  <main id="top">
    <section class="hero">
      <div class="container hero-grid">
        <div>
          <div class="eyebrow"><span class="bubble"></span> Crack open cleaner Roblox security</div>
          <h1>Keep your Roblox game <span class="soda-text">fresh, fizzy,</span> and <span class="gold-text">secure.</span></h1>
          <p>
            BloxySecurity helps Roblox developers spot weak RemoteEvents, client-trust spill risks,
            unsafe economy systems, and common anti-exploit issues before they overflow into live games.
          </p>
          <div class="hero-actions">
            <a class="btn btn-primary" href="#pricing">View Pricing</a>
            <a class="btn btn-secondary" href="#process">How It Works</a>
          </div>
          <div class="trust-row">
            <span class="pill">RemoteEvent checks</span>
            <span class="pill">Server validation review</span>
            <span class="pill">Fresh reports</span>
          </div>
        </div>

        <div class="hero-art" aria-label="BloxySecurity cover and sample scan card">
          <img class="cover" src="Bloxy Security Cover.png" alt="BloxySecurity cover artwork" />
          <div class="scan-card">
            <div class="scan-title">🥤 BloxySecurity Scan</div>
            <div class="line"><b>pop:</b> shop_system_remote</div>
            <div class="line"><span class="alert">fizz alert:</span> client sends item price</div>
            <div class="line"><span class="alert">spill risk:</span> reward cooldown missing</div>
            <div class="line"><b>recommend:</b> let the server do the pouring</div>
            <div class="line"><span class="ok">report:</span> fresh, clear, and ready</div>
          </div>
        </div>
      </div>
    </section>

    <section id="services">
      <div class="container">
        <div class="section-head">
          <h2>What gets reviewed</h2>
          <p>Focused Roblox security checks for systems that can fizz over when a game trusts the client too much.</p>
        </div>
        <div class="cards">
          <article class="card">
            <div class="icon">🥤</div>
            <h3>RemoteEvents & Client Trust</h3>
            <p>Review systems where the client talks to the server, including reward claims, purchases, tools, and admin actions.</p>
          </article>
          <article class="card">
            <div class="icon">🫧</div>
            <h3>Economy & Progression</h3>
            <p>Check coins, gems, XP, shops, inventories, leaderboards, cooldowns, and reward logic for risky patterns.</p>
          </article>
          <article class="card">
            <div class="icon">🧊</div>
            <h3>Reports & Fix Suggestions</h3>
            <p>Receive a clear written report with issue severity, what could go wrong, and practical ways to improve the system.</p>
          </article>
        </div>
      </div>
    </section>

    <section id="pricing">
      <div class="container">
        <div class="section-head">
          <h2>Final pricing menu</h2>
          <p>Simple packages for Roblox developers, from quick sips to full fizz checks. No hidden syrup.</p>
        </div>

        <div class="pricing-grid">
          <article class="card price-card">
            <h3>Basic Audit</h3>
            <div class="price">$10</div>
            <p class="small">A quick sip for one small Roblox system.</p>
            <ul>
              <li>1 small system reviewed</li>
              <li>Basic RemoteEvent check</li>
              <li>Client-trust risk notes</li>
              <li>Short written report</li>
              <li>Simple fix suggestions</li>
            </ul>
            <a class="btn btn-secondary" href="https://discord.gg/vpgpjcB8eG" target="_blank" rel="noopener noreferrer">Pop Basic</a>
          </article>

          <article class="card price-card featured">
            <span class="badge">Popular</span>
            <h3>Extensive Testing</h3>
            <div class="price">$50</div>
            <p class="small">A full fizz test for one major Roblox system.</p>
            <ul>
              <li>1 major system tested</li>
              <li>Deeper exploit-risk review</li>
              <li>Server validation check</li>
              <li>Cooldown/rate-limit review</li>
              <li>Full report with severity levels</li>
            </ul>
            <a class="btn btn-primary" href="https://discord.gg/vpgpjcB8eG" target="_blank" rel="noopener noreferrer">Pop Extensive</a>
          </article>

          <article class="card price-card">
            <h3>Basic Monthly</h3>
            <div class="price">$30<span>/month</span></div>
            <p class="small">Steady refills for small devs who update often.</p>
            <ul>
              <li>2 Basic Audits per month</li>
              <li>Priority review queue</li>
              <li>Small re-check after fixes</li>
              <li>Monthly security notes</li>
              <li>Best for frequent updates</li>
            </ul>
            <a class="btn btn-secondary" href="https://discord.gg/vpgpjcB8eG" target="_blank" rel="noopener noreferrer">Start Basic Refill</a>
          </article>

          <article class="card price-card">
            <span class="badge">Launch</span>
            <h3>Extensive Monthly</h3>
            <div class="price">$60<span>/month</span></div>
            <p class="small">Launch refill pricing for active Roblox dev teams.</p>
            <ul>
              <li>2 Extensive Tests per month</li>
              <li>Priority review queue</li>
              <li>Follow-up after fixes</li>
              <li>Monthly risk summary</li>
              <li>Great for active dev teams</li>
            </ul>
            <a class="btn btn-secondary" href="https://discord.gg/vpgpjcB8eG" target="_blank" rel="noopener noreferrer">Start Fizz Plan</a>
          </article>
        </div>
      </div>
    </section>

    <section id="process">
      <div class="container split">
        <div>
          <div class="section-head">
            <h2>How it works</h2>
            <p>Every review is permission-based and focused on helping developers improve their own games.</p>
          </div>
          <div class="notice">
            <h3>Authorized testing only</h3>
            <p>
              BloxySecurity only reviews games, scripts, or test places where the game owner gives permission.
              No live-game attacks, no public game abuse, no account stealing, and no unauthorized testing.
            </p>
            <p>
              Security reviews reduce risk, but no audit can guarantee that a game is impossible to exploit.
            </p>
          </div>
          <div class="banner-strip">
            <img src="Bloxy Security Cover.png" alt="BloxySecurity cover banner" />
          </div>
        </div>

        <div class="process">
          <article class="step">
            <div class="step-num">1</div>
            <div>
              <h3>Send the system</h3>
              <p>Share the Roblox system you want reviewed, such as a shop, reward, inventory, combat, or admin system.</p>
            </div>
          </article>
          <article class="step">
            <div class="step-num">2</div>
            <div>
              <h3>Permission confirmed</h3>
              <p>Testing begins only after ownership or permission is clear. Private test places are preferred.</p>
            </div>
          </article>
          <article class="step">
            <div class="step-num">3</div>
            <div>
              <h3>Review and test</h3>
              <p>The system is checked for client-trust issues, weak RemoteEvents, missing validation, and risky logic.</p>
            </div>
          </article>
          <article class="step">
            <div class="step-num">4</div>
            <div>
              <h3>Receive the report</h3>
              <p>You get a fresh report with risks, severity levels, and recommended fixes written in developer-friendly language.</p>
            </div>
          </article>
        </div>
      </div>
    </section>

    <section id="faq">
      <div class="container">
        <div class="section-head">
          <h2>FAQ</h2>
          <p>Common questions developers may have before booking a Roblox security review.</p>
        </div>
        <div class="faq">
          <article class="faq-item">
            <h3>Do you exploit public Roblox games?</h3>
            <p>No. Reviews are only done with permission from the game owner or developer team.</p>
          </article>
          <article class="faq-item">
            <h3>What is a Basic Audit best for?</h3>
            <p>A Basic Audit is best for one small system, like a reward button, shop item, tool, or simple RemoteEvent setup.</p>
          </article>
          <article class="faq-item">
            <h3>What is Extensive Testing best for?</h3>
            <p>Extensive Testing is best for one larger system, like a full shop, currency, inventory, combat, trading, or admin system.</p>
          </article>
          <article class="faq-item">
            <h3>Can you guarantee my game is unexploitable?</h3>
            <p>No. The goal is to find and reduce common risks. No security review can guarantee perfect protection.</p>
          </article>
        </div>
      </div>
    </section>

    <section id="contact">
      <div class="container">
        <div class="cta">
          <h2>Ready to pop the tab on better security?</h2>
          <p>
            Send the package you want, a short description of your system, and proof that you own or have permission to test the game.
          </p>
          <a class="btn btn-primary" href="https://discord.gg/vpgpjcB8eG" target="_blank" rel="noopener noreferrer">Request a Review</a>
          <div class="contact-box" aria-label="Contact information">
            <strong>Contact</strong>
            <span>Email: <a href="mailto:kaydenjohnson312@gmail.com">kaydenjohnson312@gmail.com</a></span>
            <span>Discord: <a href="https://discord.gg/vpgpjcB8eG" target="_blank" rel="noopener noreferrer">steamuser9483</a></span>
            <span>Roblox Group: <a href="https://www.roblox.com/communities/3287589/Bloxy-Security#!/about" target="_blank" rel="noopener noreferrer">Bloxy Security</a></span>
          </div>
        </div>
      </div>
    </section>
  </main>

  <footer>
    <div class="container footer-grid">
      <span>© 2026 BloxySecurity. All rights reserved.</span>
      <span>Permission-based Roblox security reviews only.</span>
    </div>
  </footer>
</body>
</html>
