<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta name="description" content="Farkhana: pueblo del Rif junto a Nador y Melilla. Costa mediterránea, frontera y vida local." />
  <title>Farkhana — Nador · Rif · Mediterráneo</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Instrument+Serif:ital@0;1&family=Inter:wght@100..900&display=swap" rel="stylesheet" />
  <link href="https://db.onlinewebfonts.com/c/440b53b1a1c65037f944ff19259d8014?family=Nokia+Cellphone+FC+Small" rel="stylesheet" />
  <style>
    :root {
      --bg: #F3F4ED;
      --ink: #1a1a1a;
      --blue: #0871E7;
      --font-instrument: "Instrument Serif", serif;
      --font-sans: "Inter", system-ui, sans-serif;
      --font-nokia: "Nokia Cellphone FC Small", monospace;
      --ease: cubic-bezier(0.16, 1, 0.3, 1);
    }

    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    html { scroll-behavior: smooth; }
    body {
      font-family: var(--font-sans);
      background: var(--bg);
      color: var(--ink);
      -webkit-font-smoothing: antialiased;
      overflow-x: hidden;
    }
    body.menu-open { overflow: hidden; }
    img, video { display: block; max-width: 100%; }
    a { color: inherit; text-decoration: none; }
    button { font-family: inherit; border: none; background: none; cursor: pointer; color: inherit; }

    .font-instrument { font-family: var(--font-instrument); }
    .font-nokia { font-family: var(--font-nokia); }

    /* NAV */
    .nav-wrap {
      position: fixed;
      top: 24px;
      left: 50%;
      transform: translateX(-50%);
      width: 95%;
      max-width: 64rem;
      z-index: 50;
      pointer-events: none;
    }
    .nav {
      pointer-events: auto;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 12px;
      padding: 10px 16px;
      border-radius: 999px;
      background: rgba(255,255,255,0.4);
      border: 1px solid rgba(0,0,0,0.1);
      backdrop-filter: blur(12px);
      -webkit-backdrop-filter: blur(12px);
      box-shadow: 0 1px 2px rgba(0,0,0,0.04);
    }
    .logo {
      font-family: var(--font-instrument);
      font-size: 28px;
      letter-spacing: -0.02em;
      color: var(--ink);
      line-height: 1;
    }
    .nav-links {
      display: none;
      align-items: center;
      gap: 40px;
    }
    .nav-links a {
      font-size: 14px;
      transition: opacity 0.2s;
    }
    .nav-links a:hover { opacity: 0.5; }
    .nav-actions { display: flex; align-items: center; gap: 8px; }

    .btn-blue {
      position: relative;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      padding: 10px 20px;
      border-radius: 999px;
      background: var(--blue);
      color: #fff;
      font-size: 14px;
      overflow: hidden;
      box-shadow: inset 0 -4px 4px rgba(255,255,255,0.39);
      outline: 1px solid var(--blue);
      outline-offset: -1px;
    }
    .btn-blue .glint {
      position: absolute;
      width: 80%;
      height: 16px;
      left: 10%;
      top: 1px;
      border-radius: 12px;
      background: linear-gradient(to bottom, #DEF0FC, transparent);
      pointer-events: none;
      transition: transform 0.25s var(--ease);
      transform-origin: center;
    }
    .btn-blue:hover .glint { transform: scaleX(1.05); }
    .btn-blue span.label { position: relative; }
    .btn-blue.desktop-only { display: none; }

    .menu-toggle {
      width: 40px;
      height: 40px;
      border-radius: 999px;
      background: var(--ink);
      color: #fff;
      font-size: 14px;
      display: inline-flex;
      align-items: center;
      justify-content: center;
    }

    @media (min-width: 768px) {
      .nav-links { display: flex; }
      .menu-toggle { display: none; }
      .btn-blue.desktop-only { display: inline-flex; }
    }

    /* MOBILE MENU */
    .overlay {
      position: fixed;
      inset: 0;
      z-index: 40;
      background: rgba(243,244,237,0.97);
      backdrop-filter: blur(16px);
      display: flex;
      flex-direction: column;
      justify-content: center;
      padding: 0 32px;
      opacity: 0;
      visibility: hidden;
      transition: opacity 0.3s ease, visibility 0.3s ease;
    }
    .overlay.open { opacity: 1; visibility: visible; }
    .overlay a {
      font-family: var(--font-instrument);
      font-size: 40px;
      letter-spacing: -0.03em;
      line-height: 1.05;
      padding: 8px 0;
      border-bottom: 1px solid rgba(0,0,0,0.1);
    }
    .overlay-tags {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin-top: 40px;
    }

    /* HERO */
    .hero {
      position: relative;
      min-height: 100vh;
      min-height: 100dvh;
      background: var(--bg);
      padding-top: 96px;
      display: flex;
      flex-direction: column;
      align-items: center;
      overflow: hidden;
    }
    @media (min-width: 768px) { .hero { padding-top: 128px; } }

    .video-bg {
      position: absolute;
      inset: 0;
      z-index: 0;
    }
    .video-bg video {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
    .video-tint {
      position: absolute;
      inset: 0;
      background: rgba(255,255,255,0.05);
    }

    .typing {
      position: absolute;
      left: 48.5%;
      bottom: 32%;
      transform: translateX(-50%);
      z-index: 30;
      width: 110px;
      display: flex;
      justify-content: flex-start;
      text-align: left;
      pointer-events: none;
    }
    @media (min-width: 640px) { .typing { width: 130px; } }
    @media (min-width: 768px) { .typing { left: 47.5%; } }
    @media (min-width: 1024px) { .typing { left: 48.5%; } }

    .typing p {
      font-family: var(--font-nokia);
      color: #2A3616;
      font-size: 10px;
      line-height: 1.25;
      word-break: break-word;
      min-height: 1.5em;
    }
    @media (min-width: 640px) { .typing p { font-size: 14px; } }
    .cursor {
      display: inline-block;
      width: 6px;
      height: 12px;
      background: #2A3616;
      margin-left: 4px;
      vertical-align: middle;
      animation: blink 0.8s linear infinite;
    }
    @keyframes blink {
      0%, 100% { opacity: 0; }
      50% { opacity: 1; }
    }

    .hero-copy {
      position: relative;
      z-index: 20;
      text-align: center;
      padding: 0 24px;
      pointer-events: none;
    }
    .hero h1 {
      font-family: var(--font-instrument);
      font-size: 38px;
      line-height: 0.85;
      letter-spacing: -0.03em;
      color: var(--ink);
      margin-bottom: 24px;
      animation: heroIn 1.5s var(--ease) both;
    }
    @media (min-width: 768px) { .hero h1 { font-size: 56px; } }
    @media (min-width: 1024px) { .hero h1 { font-size: 72px; } }

    .hero-sub {
      font-size: 16px;
      line-height: 1.6;
      color: rgba(26,26,26,0.7);
      max-width: 36rem;
      margin: 0 auto;
      animation: fadeUp 1.2s var(--ease) 0.3s both;
    }
    @media (min-width: 768px) { .hero-sub { font-size: 18px; } }

    .hero-actions {
      pointer-events: auto;
      margin-top: 32px;
      display: flex;
      flex-wrap: wrap;
      gap: 12px;
      justify-content: center;
      animation: fadeUp 0.9s var(--ease) 0.55s both;
    }
    .btn-ghost {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      padding: 12px 24px;
      border-radius: 999px;
      border: 1px solid rgba(0,0,0,0.15);
      background: rgba(255,255,255,0.5);
      backdrop-filter: blur(8px);
      font-size: 14px;
    }

    .hero-bottom {
      position: relative;
      z-index: 20;
      margin-top: auto;
      width: 100%;
      padding: 96px 24px 40px;
      background: linear-gradient(to top, var(--bg) 0%, rgba(243,244,237,0.85) 50%, transparent 100%);
    }
    .tags {
      max-width: 64rem;
      margin: 0 auto;
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      justify-content: center;
    }
    .pill {
      padding: 6px 14px;
      border-radius: 999px;
      background: rgba(255,255,255,0.7);
      border: 1px solid rgba(0,0,0,0.1);
      font-size: 12px;
      font-weight: 500;
      color: rgba(26,26,26,0.75);
      backdrop-filter: blur(6px);
    }
    .pill.light {
      background: transparent;
      color: rgba(26,26,26,0.7);
    }

    @keyframes heroIn {
      from { opacity: 0; transform: scale(0.95); }
      to { opacity: 1; transform: scale(1); }
    }
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }

    /* SECTIONS */
    .section {
      padding: 96px 24px;
      border-top: 1px solid rgba(0,0,0,0.05);
    }
    @media (min-width: 768px) { .section { padding: 128px 24px; } }
    .wrap { max-width: 64rem; margin: 0 auto; }

    .label {
      font-size: 13px;
      letter-spacing: 0.02em;
      color: rgba(26,26,26,0.5);
      margin-bottom: 16px;
    }
    .section h2 {
      font-family: var(--font-instrument);
      font-size: 36px;
      line-height: 0.95;
      letter-spacing: -0.03em;
      max-width: 36rem;
      margin-bottom: 24px;
    }
    @media (min-width: 768px) { .section h2 { font-size: 52px; } }
    .lead {
      font-size: 16px;
      line-height: 1.65;
      color: rgba(26,26,26,0.7);
      max-width: 36rem;
      margin-bottom: 48px;
    }
    @media (min-width: 768px) { .lead { font-size: 18px; } }

    .reveal {
      opacity: 0;
      transform: translateY(28px);
      transition: opacity 0.9s var(--ease), transform 0.9s var(--ease);
    }
    .reveal.in {
      opacity: 1;
      transform: translateY(0);
    }

    .grid-2 {
      display: grid;
      gap: 20px;
    }
    @media (min-width: 768px) { .grid-2 { grid-template-columns: 1fr 1fr; } }

    .grid-3 {
      display: grid;
      gap: 16px;
    }
    @media (min-width: 640px) { .grid-3 { grid-template-columns: 1fr 1fr; } }
    @media (min-width: 900px) { .grid-3 { grid-template-columns: 1fr 1fr 1fr; } }

    .photo {
      position: relative;
      overflow: hidden;
      border-radius: 24px;
      background: rgba(0,0,0,0.05);
      min-height: 220px;
    }
    .photo img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      min-height: 220px;
      transition: transform 0.7s ease;
    }
    .photo:hover img { transform: scale(1.03); }
    .photo figcaption {
      position: absolute;
      left: 0; right: 0; bottom: 0;
      padding: 16px;
      background: linear-gradient(to top, rgba(0,0,0,0.55), transparent);
      color: #fff;
      font-size: 13px;
      font-weight: 500;
    }

    .card-soft {
      border-radius: 22px;
      border: 1px solid rgba(0,0,0,0.1);
      background: rgba(255,255,255,0.5);
      padding: 24px;
      height: 100%;
    }
    .card-soft h3 {
      font-family: var(--font-instrument);
      font-size: 24px;
      letter-spacing: -0.02em;
      margin-bottom: 8px;
    }
    .card-soft p {
      font-size: 14px;
      line-height: 1.55;
      color: rgba(26,26,26,0.65);
    }

    .place-card {
      border-radius: 24px;
      overflow: hidden;
      border: 1px solid rgba(0,0,0,0.1);
      background: rgba(255,255,255,0.4);
    }
    .place-card .thumb {
      aspect-ratio: 16/10;
      overflow: hidden;
    }
    .place-card .thumb img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      transition: transform 0.7s ease;
    }
    .place-card:hover .thumb img { transform: scale(1.04); }
    .place-card .body { padding: 24px; }
    .tag {
      display: inline-flex;
      padding: 4px 12px;
      border-radius: 999px;
      background: rgba(26,26,26,0.05);
      font-size: 11px;
      font-weight: 500;
      margin-bottom: 12px;
    }
    .place-card h3 {
      font-family: var(--font-instrument);
      font-size: 28px;
      letter-spacing: -0.02em;
      line-height: 1;
      margin-bottom: 12px;
    }
    .place-card p {
      font-size: 14px;
      line-height: 1.55;
      color: rgba(26,26,26,0.65);
    }

    .gallery {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 12px;
    }
    @media (min-width: 768px) {
      .gallery {
        grid-template-columns: 1fr 1fr 1fr;
        gap: 16px;
      }
    }
    .gallery .span-2 { grid-column: span 2; }
    @media (min-width: 768px) {
      .gallery .md-span-1 { grid-column: span 1; }
      .gallery .md-span-2 { grid-column: span 2; }
      .gallery .md-span-3 { grid-column: span 3; }
    }
    .gallery .photo { min-height: 200px; }
    .gallery .tall img, .gallery .tall { min-height: 260px; }
    .gallery .wide img, .gallery .wide { min-height: 240px; }
    @media (min-width: 768px) {
      .gallery .wide img, .gallery .wide { min-height: 320px; }
      .gallery .banner img, .gallery .banner { min-height: 360px; }
    }

    .split {
      display: grid;
      gap: 40px;
    }
    @media (min-width: 1024px) {
      .split {
        grid-template-columns: 1fr 1fr;
        gap: 64px;
        align-items: start;
      }
    }
    .checklist { display: flex; flex-direction: column; gap: 12px; }
    .check-item {
      display: flex;
      gap: 12px;
      align-items: flex-start;
      padding: 12px 16px;
      border-radius: 16px;
      background: rgba(255,255,255,0.5);
      border: 1px solid rgba(0,0,0,0.08);
      font-size: 14px;
      line-height: 1.5;
      color: rgba(26,26,26,0.75);
    }
    .dot-blue {
      width: 8px;
      height: 8px;
      border-radius: 50%;
      background: var(--blue);
      margin-top: 6px;
      flex-shrink: 0;
    }

    .info-table {
      border-radius: 24px;
      border: 1px solid rgba(0,0,0,0.1);
      background: rgba(255,255,255,0.55);
      overflow: hidden;
    }
    .info-row {
      display: flex;
      justify-content: space-between;
      gap: 16px;
      padding: 16px 20px;
      border-bottom: 1px solid rgba(0,0,0,0.06);
      font-size: 14px;
    }
    .info-row:last-child { border-bottom: none; }
    .info-row span:last-child {
      color: rgba(26,26,26,0.55);
      text-align: right;
    }

    .tips { display: flex; flex-direction: column; gap: 16px; }
    .tip {
      border-radius: 20px;
      background: var(--ink);
      color: #fff;
      padding: 20px;
      display: flex;
      gap: 16px;
    }
    .tip-n {
      font-family: var(--font-nokia);
      font-size: 11px;
      color: rgba(255,255,255,0.5);
      padding-top: 4px;
      flex-shrink: 0;
    }
    .tip h3 {
      font-family: var(--font-instrument);
      font-size: 22px;
      letter-spacing: -0.02em;
      margin-bottom: 4px;
    }
    .tip p {
      font-size: 13px;
      line-height: 1.5;
      color: rgba(255,255,255,0.65);
    }

    .cta-block {
      position: relative;
      border-radius: 32px;
      overflow: hidden;
      min-height: 380px;
      display: flex;
      align-items: flex-end;
    }
    .cta-block > img {
      position: absolute;
      inset: 0;
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
    .cta-block .shade {
      position: absolute;
      inset: 0;
      background: linear-gradient(to top, rgba(0,0,0,0.7), rgba(0,0,0,0.3), rgba(0,0,0,0.1));
    }
    .cta-content {
      position: relative;
      z-index: 2;
      padding: 32px;
      max-width: 36rem;
    }
    @media (min-width: 768px) { .cta-content { padding: 48px; } }
    .cta-content h2 {
      font-family: var(--font-instrument);
      font-size: 36px;
      line-height: 0.95;
      letter-spacing: -0.03em;
      color: #fff;
      margin-bottom: 16px;
      max-width: none;
    }
    @media (min-width: 768px) { .cta-content h2 { font-size: 48px; } }
    .cta-content p {
      color: rgba(255,255,255,0.75);
      font-size: 15px;
      line-height: 1.6;
      margin-bottom: 24px;
    }
    .cta-actions { display: flex; flex-wrap: wrap; gap: 12px; }
    .btn-white-ghost {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      padding: 12px 24px;
      border-radius: 999px;
      border: 1px solid rgba(255,255,255,0.3);
      color: #fff;
      font-size: 14px;
    }

    .site-footer {
      border-top: 1px solid rgba(0,0,0,0.08);
      padding: 48px 24px;
    }
    .footer-inner {
      max-width: 64rem;
      margin: 0 auto;
      display: flex;
      flex-direction: column;
      gap: 32px;
    }
    @media (min-width: 768px) {
      .footer-inner {
        flex-direction: row;
        align-items: center;
        justify-content: space-between;
      }
    }
    .footer-brand {
      font-family: var(--font-instrument);
      font-size: 28px;
      letter-spacing: -0.02em;
    }
    .footer-sub {
      font-size: 13px;
      color: rgba(26,26,26,0.5);
      margin-top: 4px;
    }
    .footer-links {
      display: flex;
      flex-wrap: wrap;
      gap: 8px 24px;
    }
    .footer-links a {
      font-size: 13px;
      color: rgba(26,26,26,0.55);
    }
    .footer-copy {
      font-size: 12px;
      color: rgba(26,26,26,0.4);
    }

    .mt-10 { margin-top: 40px; }
    .mb-5 { margin-bottom: 20px; }
    .mt-8 { margin-top: 32px; }
  </style>
</head>
<body>
  <!-- MENU MÓVIL -->
  <div class="overlay" id="menu" aria-hidden="true">
    <a href="#descubrir" data-nav>Descubrir</a>
    <a href="#lugares" data-nav>Lugares</a>
    <a href="#galeria" data-nav>Galería</a>
    <a href="#vivir" data-nav>Vivir</a>
    <a href="#practico" data-nav>Práctico</a>
    <div class="overlay-tags">
      <span class="pill light">Nador</span>
      <span class="pill light">Melilla</span>
      <span class="pill light">Rif</span>
      <span class="pill light">Mediterráneo</span>
    </div>
  </div>

  <!-- NAV -->
  <div class="nav-wrap">
    <nav class="nav" aria-label="Principal">
      <a href="#inicio" class="logo" id="logo">farkhana.</a>
      <div class="nav-links">
        <a href="#descubrir">Descubrir</a>
        <a href="#lugares">Lugares</a>
        <a href="#galeria">Galería</a>
        <a href="#vivir">Vivir</a>
        <a href="#practico">Práctico</a>
      </div>
      <div class="nav-actions">
        <a href="#practico" class="btn-blue desktop-only">
          <span class="glint" aria-hidden="true"></span>
          <span class="label">Planificar</span>
        </a>
        <button type="button" class="menu-toggle" id="menu-btn" aria-label="Abrir menú" aria-expanded="false">☰</button>
      </div>
    </nav>
  </div>

  <!-- HERO -->
  <header class="hero" id="inicio">
    <div class="video-bg">
      <video
        src="https://d8j0ntlcm91z4.cloudfront.net/user_38xzZboKViGWJOttwIXH07lWA1P/hf_20260427_054418_a6d194f0-ac86-4df9-abe5-ded73e596d7c.mp4"
        autoplay muted loop playsinline
      ></video>
      <div class="video-tint"></div>
    </div>

    <div class="typing" aria-hidden="true">
      <p><span id="typed"></span><span class="cursor"></span></p>
    </div>

    <div class="hero-copy">
      <h1>Frontera, mar<br />y casa. Farkhana.</h1>
      <p class="hero-sub">
        Pueblo del Rif junto a Nador y Melilla. Un ritmo local entre el
        Mediterráneo, el paso fronterizo y la vida cotidiana del norte de Marruecos.
      </p>
      <div class="hero-actions">
        <a href="#descubrir" class="btn-blue">
          <span class="glint" aria-hidden="true"></span>
          <span class="label">Descubrir Farkhana</span>
        </a>
        <a href="#galeria" class="btn-ghost">Ver fotos</a>
      </div>
    </div>

    <div class="hero-bottom">
      <div class="tags">
        <span class="pill">Nador</span>
        <span class="pill">Melilla</span>
        <span class="pill">Rif</span>
        <span class="pill">Mediterráneo</span>
      </div>
    </div>
  </header>

  <!-- DESCUBRIR -->
  <section class="section" id="descubrir">
    <div class="wrap">
      <div class="reveal">
        <p class="label">01 — Sobre el lugar</p>
        <h2>Un pueblo rifeño<br />entre dos orillas.</h2>
        <p class="lead">
          Farkhana (فرخانة) está en la provincia de Nador, muy cerca de Melilla.
          Es un punto de paso y de vida diaria: frontera, familia, comercio y
          el Mediterráneo a poca distancia.
        </p>
      </div>

      <div class="grid-2 mb-5">
        <figure class="photo reveal">
          <img src="https://images.unsplash.com/photo-1539020140153-e479b8c22e70?auto=format&fit=crop&w=1400&q=80" alt="Arquitectura y calles del norte de Marruecos" loading="lazy" />
          <figcaption>Ambiente urbano del Rif oriental</figcaption>
        </figure>
        <figure class="photo reveal">
          <img src="https://images.unsplash.com/photo-1555881400-74d7acaacd8b?auto=format&fit=crop&w=1400&q=80" alt="Costa mediterránea" loading="lazy" />
          <figcaption>El mar cerca de Nador y Farkhana</figcaption>
        </figure>
      </div>

      <div class="grid-3 mt-10">
        <div class="card-soft reveal">
          <h3>Ubicación</h3>
          <p>Provincia de Nador, noreste de Marruecos, junto a Melilla.</p>
        </div>
        <div class="card-soft reveal">
          <h3>Identidad</h3>
          <p>Pueblo rifeño con ritmo fronterizo, familiar y comercial.</p>
        </div>
        <div class="card-soft reveal">
          <h3>Entorno</h3>
          <p>Costa mediterránea, Nador, Marchica y el macizo del Rif.</p>
        </div>
      </div>
    </div>
  </section>

  <!-- LUGARES -->
  <section class="section" id="lugares">
    <div class="wrap">
      <div class="reveal">
        <p class="label">02 — Qué ver y hacer</p>
        <h2>Farkhana y sus<br />alrededores.</h2>
        <p class="lead">
          El interés está en el cruce de caminos, la costa cercana y la conexión
          con Nador y Melilla.
        </p>
      </div>

      <div class="grid-2">
        <article class="place-card reveal">
          <div class="thumb">
            <img src="https://images.unsplash.com/photo-1548013146-72479768bada?auto=format&fit=crop&w=1400&q=80" alt="Calles locales" loading="lazy" />
          </div>
          <div class="body">
            <span class="tag">Pueblo</span>
            <h3>Centro de Farkhana</h3>
            <p>Calles locales, cafeterías, comercio y el pulso diario de un pueblo fronterizo del Rif.</p>
          </div>
        </article>

        <article class="place-card reveal">
          <div class="thumb">
            <img src="https://images.unsplash.com/photo-1569383746724-6f1b882b8f46?auto=format&fit=crop&w=1400&q=80" alt="Puertas y arquitectura" loading="lazy" />
          </div>
          <div class="body">
            <span class="tag">Frontera</span>
            <h3>Paso hacia Melilla</h3>
            <p>La cercanía con Melilla define parte de la economía y de la vida familiar de la zona.</p>
          </div>
        </article>

        <article class="place-card reveal">
          <div class="thumb">
            <img src="https://images.unsplash.com/photo-1507525428034-b723cf961d3e?auto=format&fit=crop&w=1400&q=80" alt="Mar Mediterráneo" loading="lazy" />
          </div>
          <div class="body">
            <span class="tag">Ciudad</span>
            <h3>Nador</h3>
            <p>A pocos minutos: servicios, costa, laguna de Marchica y el corazón urbano de la región.</p>
          </div>
        </article>

        <article class="place-card reveal">
          <div class="thumb">
            <img src="https://images.unsplash.com/photo-1469854523086-cc02fe5d8800?auto=format&fit=crop&w=1400&q=80" alt="Paisaje al atardecer" loading="lazy" />
          </div>
          <div class="body">
            <span class="tag">Naturaleza</span>
            <h3>Costa y Marchica</h3>
            <p>Playas del Mediterráneo y la gran laguna de Marchica para pasear y respirar.</p>
          </div>
        </article>
      </div>
    </div>
  </section>

  <!-- GALERÍA -->
  <section class="section" id="galeria">
    <div class="wrap">
      <div class="reveal">
        <p class="label">03 — Imágenes reales</p>
        <h2>Luz del norte,<br />textura del Rif.</h2>
        <p class="lead">
          Mar, calles, montaña, té y vida cotidiana del Magreb mediterráneo.
        </p>
      </div>

      <div class="gallery">
        <figure class="photo tall span-2 md-span-1 reveal">
          <img src="https://images.unsplash.com/photo-1489749798305-4fea3ae63d43?auto=format&fit=crop&w=1400&q=80" alt="Mercado marroquí" loading="lazy" />
          <figcaption>Mercado</figcaption>
        </figure>
        <figure class="photo tall reveal">
          <img src="https://images.unsplash.com/photo-1516026672322-bc52d61a55d5?auto=format&fit=crop&w=1400&q=80" alt="Montañas del norte de África" loading="lazy" />
          <figcaption>Montaña</figcaption>
        </figure>
        <figure class="photo tall reveal">
          <img src="https://images.unsplash.com/photo-1578662996442-48f60103fc96?auto=format&fit=crop&w=1400&q=80" alt="Té marroquí" loading="lazy" />
          <figcaption>Té</figcaption>
        </figure>
        <figure class="photo tall reveal">
          <img src="https://images.unsplash.com/photo-1523805009345-7448845a9e53?auto=format&fit=crop&w=1400&q=80" alt="Vida local" loading="lazy" />
          <figcaption>Gente</figcaption>
        </figure>
        <figure class="photo wide span-2 reveal">
          <img src="https://images.unsplash.com/photo-1507525428034-b723cf961d3e?auto=format&fit=crop&w=1600&q=80" alt="Mediterráneo" loading="lazy" />
          <figcaption>Mar</figcaption>
        </figure>
        <figure class="photo banner span-2 md-span-3 reveal">
          <img src="https://images.unsplash.com/photo-1469854523086-cc02fe5d8800?auto=format&fit=crop&w=1800&q=80" alt="Atardecer" loading="lazy" />
          <figcaption>Atardecer</figcaption>
        </figure>
      </div>
    </div>
  </section>

  <!-- VIVIR -->
  <section class="section" id="vivir">
    <div class="wrap">
      <div class="split">
        <div class="reveal">
          <p class="label">04 — Cultura y día a día</p>
          <h2>Tarifit, frontera<br />y mesa compartida.</h2>
          <p class="lead" style="margin-bottom:32px">
            En Farkhana se cruzan el amazigh del Rif (tarifit), el árabe y el
            contacto con el español de Melilla. La hospitalidad y el té marcan el ritmo.
          </p>
          <div class="checklist">
            <div class="check-item"><span class="dot-blue"></span>Lengua rifeña presente en la calle y en casa</div>
            <div class="check-item"><span class="dot-blue"></span>Influencia fronteriza con Melilla</div>
            <div class="check-item"><span class="dot-blue"></span>Comercio, transporte y redes familiares</div>
            <div class="check-item"><span class="dot-blue"></span>Cocina sencilla: té, pan, pescado y platos de casa</div>
          </div>
        </div>
        <div class="grid-2 reveal">
          <figure class="photo"><img src="https://images.unsplash.com/photo-1578662996442-48f60103fc96?auto=format&fit=crop&w=1000&q=80" alt="Té" loading="lazy" /></figure>
          <figure class="photo mt-8"><img src="https://images.unsplash.com/photo-1489749798305-4fea3ae63d43?auto=format&fit=crop&w=1000&q=80" alt="Mercado" loading="lazy" /></figure>
          <figure class="photo span-2" style="grid-column:1/-1"><img src="https://images.unsplash.com/photo-1548013146-72479768bada?auto=format&fit=crop&w=1400&q=80" alt="Calle" loading="lazy" /></figure>
        </div>
      </div>
    </div>
  </section>

  <!-- PRÁCTICO -->
  <section class="section" id="practico">
    <div class="wrap">
      <div class="reveal">
        <p class="label">05 — Información práctica</p>
        <h2>Datos útiles para<br />moverte por la zona.</h2>
      </div>

      <div class="grid-2" style="margin-top:48px">
        <div class="info-table reveal">
          <div class="info-row"><span>Región</span><span>Nador · Rif oriental</span></div>
          <div class="info-row"><span>País</span><span>Marruecos</span></div>
          <div class="info-row"><span>Cerca de</span><span>Melilla · Nador · Beni Ensar</span></div>
          <div class="info-row"><span>Aeropuerto</span><span>Nador El Aroui (NDR)</span></div>
          <div class="info-row"><span>Mar</span><span>Mediterráneo</span></div>
          <div class="info-row"><span>Moneda</span><span>Dirham marroquí (MAD)</span></div>
          <div class="info-row"><span>Idiomas</span><span>Tarifit · Árabe · ES · FR</span></div>
          <div class="info-row"><span>Mejor época</span><span>Primavera y otoño</span></div>
        </div>

        <div class="tips">
          <div class="tip reveal">
            <span class="tip-n">01</span>
            <div>
              <h3>Combina Farkhana + Nador</h3>
              <p>Pueblo, ciudad y costa se pueden hacer el mismo día sin prisas.</p>
            </div>
          </div>
          <div class="tip reveal">
            <span class="tip-n">02</span>
            <div>
              <h3>Respeta el ritmo fronterizo</h3>
              <p>El paso y el tráfico pueden variar; planifica con margen.</p>
            </div>
          </div>
          <div class="tip reveal">
            <span class="tip-n">03</span>
            <div>
              <h3>Marchica al atardecer</h3>
              <p>La laguna cerca de Nador regala muy buena luz al final del día.</p>
            </div>
          </div>
          <div class="tip reveal">
            <span class="tip-n">04</span>
            <div>
              <h3>Habla con la gente local</h3>
              <p>La hospitalidad y las recomendaciones de calle valen más que el mapa.</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- CTA -->
  <section class="section" style="border-top:none; padding-top:0">
    <div class="wrap">
      <div class="cta-block reveal">
        <img src="https://images.unsplash.com/photo-1555881400-74d7acaacd8b?auto=format&fit=crop&w=1600&q=80" alt="Costa cerca de Farkhana" />
        <div class="shade"></div>
        <div class="cta-content">
          <h2>Empieza en Farkhana.<br />Sigue por el mar.</h2>
          <p>Una base real para entender el Rif oriental: frontera, familia y Mediterráneo en el mismo paisaje.</p>
          <div class="cta-actions">
            <a href="#lugares" class="btn-blue">
              <span class="glint" aria-hidden="true"></span>
              <span class="label">Ver lugares</span>
            </a>
            <a href="#galeria" class="btn-white-ghost">Galería</a>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- FOOTER -->
  <footer class="site-footer">
    <div class="footer-inner">
      <div>
        <div class="footer-brand">farkhana.</div>
        <p class="footer-sub">Nador · Rif · Mediterráneo</p>
      </div>
      <div class="footer-links">
        <a href="#descubrir">Descubrir</a>
        <a href="#lugares">Lugares</a>
        <a href="#galeria">Galería</a>
        <a href="#vivir">Vivir</a>
        <a href="#practico">Práctico</a>
      </div>
      <p class="footer-copy">Guía local · Fotos Unsplash</p>
    </div>
  </footer>

  <script>
    /* Menú móvil */
    (function () {
      var btn = document.getElementById('menu-btn');
      var menu = document.getElementById('menu');
      var open = false;
      function set(v) {
        open = v;
        menu.classList.toggle('open', v);
        menu.setAttribute('aria-hidden', v ? 'false' : 'true');
        btn.setAttribute('aria-expanded', v ? 'true' : 'false');
        btn.textContent = v ? '✕' : '☰';
        document.body.classList.toggle('menu-open', v);
      }
      btn.addEventListener('click', function () { set(!open); });
      menu.querySelectorAll('[data-nav]').forEach(function (a) {
        a.addEventListener('click', function () { set(false); });
      });
      document.getElementById('logo').addEventListener('click', function () { set(false); });
      document.addEventListener('keydown', function (e) {
        if (e.key === 'Escape' && open) set(false);
      });
    })();

    /* Typing en la pantalla del móvil del vídeo */
    (function () {
      var messages = ['¿Estás aquí?', 'Sí, en Farkhana.', 'Hasta pronto.'];
      var el = document.getElementById('typed');
      var i = 0, text = '', deleting = false;
      function tick() {
        var full = messages[i];
        if (!deleting && text === full) {
          setTimeout(function () { deleting = true; tick(); }, 2000);
          return;
        }
        if (deleting && text === '') {
          deleting = false;
          i = (i + 1) % messages.length;
          setTimeout(tick, 200);
          return;
        }
        text = deleting ? full.slice(0, text.length - 1) : full.slice(0, text.length + 1);
        el.textContent = text;
        setTimeout(tick, deleting ? 50 : 100);
      }
      tick();
    })();

    /* Animaciones al hacer scroll (toda la página) */
    (function () {
      var nodes = document.querySelectorAll('.reveal');
      if (!('IntersectionObserver' in window)) {
        nodes.forEach(function (n) { n.classList.add('in'); });
        return;
      }
      var io = new IntersectionObserver(function (entries) {
        entries.forEach(function (e) {
          if (e.isIntersecting) {
            e.target.classList.add('in');
            io.unobserve(e.target);
          }
        });
      }, { threshold: 0.12, rootMargin: '0px 0px -40px 0px' });
      nodes.forEach(function (n) { io.observe(n); });
    })();
  </script>
</body>
</html>
