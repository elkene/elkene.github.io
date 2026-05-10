<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>PawMatch — Adopcion responsable de mascotas</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --sage: #5a7d5a;
    --sage-light: #e8f0e8;
    --sage-mid: #8fad8f;
    --amber: #c97d3a;
    --amber-light: #fdf3e7;
    --cream: #faf8f3;
    --warm-white: #ffffff;
    --charcoal: #2b2b2b;
    --muted: #6b6b6b;
    --border: #e0dbd2;
    --radius: 16px;
    --radius-sm: 8px;
  }

  html { scroll-behavior: smooth; }

  body {
    font-family: 'DM Sans', sans-serif;
    background: var(--cream);
    color: var(--charcoal);
    line-height: 1.65;
    font-size: 16px;
  }

  /* NAV */
  nav {
    position: sticky;
    top: 0;
    z-index: 100;
    background: rgba(250,248,243,0.92);
    backdrop-filter: blur(12px);
    border-bottom: 1px solid var(--border);
    padding: 0 2rem;
    height: 64px;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .nav-logo {
    font-family: 'Playfair Display', serif;
    font-size: 1.4rem;
    color: var(--sage);
    text-decoration: none;
    display: flex;
    align-items: center;
    gap: 0.4rem;
  }

  .nav-logo .paw { font-size: 1.2rem; }

  .nav-links {
    display: flex;
    gap: 2rem;
    list-style: none;
  }

  .nav-links a {
    text-decoration: none;
    color: var(--muted);
    font-size: 0.9rem;
    font-weight: 500;
    letter-spacing: 0.01em;
    transition: color 0.2s;
  }

  .nav-links a:hover { color: var(--sage); }

  .nav-cta {
    background: var(--sage);
    color: white !important;
    padding: 0.5rem 1.2rem;
    border-radius: 50px;
    font-size: 0.85rem !important;
    font-weight: 600 !important;
    transition: background 0.2s !important;
  }

  .nav-cta:hover { background: #4a6b4a !important; color: white !important; }

  /* HERO */
  .hero {
    min-height: 92vh;
    display: grid;
    grid-template-columns: 1fr 1fr;
    align-items: center;
    gap: 4rem;
    padding: 5rem 5rem 4rem;
    max-width: 1200px;
    margin: 0 auto;
  }

  .hero-badge {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    background: var(--sage-light);
    color: var(--sage);
    font-size: 0.78rem;
    font-weight: 600;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    padding: 0.4rem 0.9rem;
    border-radius: 50px;
    margin-bottom: 1.5rem;
  }

  .hero h1 {
    font-family: 'Playfair Display', serif;
    font-size: clamp(2.6rem, 4vw, 3.8rem);
    line-height: 1.15;
    color: var(--charcoal);
    margin-bottom: 1.25rem;
    font-weight: 700;
  }

  .hero h1 em {
    font-style: italic;
    color: var(--sage);
  }

  .hero p {
    font-size: 1.1rem;
    color: var(--muted);
    max-width: 500px;
    margin-bottom: 2.2rem;
    line-height: 1.75;
  }

  .hero-buttons {
    display: flex;
    gap: 1rem;
    flex-wrap: wrap;
    align-items: center;
  }

  .btn-primary {
    background: var(--sage);
    color: white;
    text-decoration: none;
    padding: 0.85rem 2rem;
    border-radius: 50px;
    font-weight: 600;
    font-size: 0.95rem;
    transition: background 0.2s, transform 0.15s;
    display: inline-block;
  }

  .btn-primary:hover { background: #4a6b4a; transform: translateY(-1px); }

  .btn-outline {
    border: 1.5px solid var(--border);
    color: var(--charcoal);
    text-decoration: none;
    padding: 0.85rem 2rem;
    border-radius: 50px;
    font-weight: 500;
    font-size: 0.95rem;
    transition: border-color 0.2s, color 0.2s;
    display: inline-block;
  }

  .btn-outline:hover { border-color: var(--sage); color: var(--sage); }

  .hero-visual {
    position: relative;
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }

  .hero-card-main {
    background: white;
    border-radius: var(--radius);
    border: 1px solid var(--border);
    padding: 1.5rem;
    box-shadow: 0 8px 40px rgba(0,0,0,0.07);
  }

  .pet-photo-placeholder {
    width: 100%;
    height: 200px;
    background: linear-gradient(135deg, #e8f0e8 0%, #d4e6d4 100%);
    border-radius: 12px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 4rem;
    margin-bottom: 1rem;
  }

  .pet-info h3 {
    font-family: 'Playfair Display', serif;
    font-size: 1.3rem;
    margin-bottom: 0.25rem;
  }

  .pet-info p { color: var(--muted); font-size: 0.9rem; margin-bottom: 0.75rem; }

  .compatibility-bar {
    background: var(--sage-light);
    border-radius: 50px;
    height: 8px;
    overflow: hidden;
    margin-bottom: 0.4rem;
  }

  .compatibility-fill {
    background: var(--sage);
    height: 100%;
    border-radius: 50px;
    width: 87%;
    animation: fillBar 1.5s ease-out forwards;
  }

  @keyframes fillBar { from { width: 0; } to { width: 87%; } }

  .compat-label {
    display: flex;
    justify-content: space-between;
    font-size: 0.78rem;
    color: var(--muted);
  }

  .compat-score {
    font-weight: 600;
    color: var(--sage);
    font-size: 0.9rem;
  }

  .hero-stats {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 0.75rem;
  }

  .stat-mini {
    background: white;
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 1rem 1.25rem;
    text-align: center;
  }

  .stat-mini .num {
    font-family: 'Playfair Display', serif;
    font-size: 1.6rem;
    color: var(--sage);
    display: block;
    font-weight: 700;
  }

  .stat-mini .lbl {
    font-size: 0.78rem;
    color: var(--muted);
  }

  /* SECTIONS COMMON */
  section {
    padding: 6rem 2rem;
  }

  .section-inner {
    max-width: 1100px;
    margin: 0 auto;
  }

  .section-label {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    background: var(--amber-light);
    color: var(--amber);
    font-size: 0.78rem;
    font-weight: 600;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    padding: 0.4rem 0.9rem;
    border-radius: 50px;
    margin-bottom: 1rem;
  }

  .section-title {
    font-family: 'Playfair Display', serif;
    font-size: clamp(2rem, 3vw, 2.8rem);
    line-height: 1.2;
    margin-bottom: 1rem;
    font-weight: 700;
  }

  .section-sub {
    font-size: 1.05rem;
    color: var(--muted);
    max-width: 560px;
    line-height: 1.75;
    margin-bottom: 3rem;
  }

  /* PROBLEM */
  .problem-bg {
    background: var(--charcoal);
    color: white;
  }

  .problem-bg .section-label {
    background: rgba(255,255,255,0.1);
    color: #b0c4b0;
  }

  .problem-bg .section-title { color: white; }
  .problem-bg .section-sub { color: #a0a0a0; }

  .problem-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1.5rem;
  }

  .problem-card {
    background: rgba(255,255,255,0.05);
    border: 1px solid rgba(255,255,255,0.1);
    border-radius: var(--radius);
    padding: 1.75rem;
  }

  .problem-icon {
    font-size: 2rem;
    margin-bottom: 0.75rem;
    display: block;
  }

  .problem-card h4 {
    font-size: 1rem;
    font-weight: 600;
    color: white;
    margin-bottom: 0.5rem;
  }

  .problem-card p {
    font-size: 0.9rem;
    color: #a0a0a0;
    line-height: 1.6;
  }

  /* SOLUTION / FEATURES */
  .features-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 1.5rem;
  }

  .feature-card {
    background: white;
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 2rem;
    transition: box-shadow 0.2s, transform 0.2s;
  }

  .feature-card:hover {
    box-shadow: 0 8px 30px rgba(0,0,0,0.08);
    transform: translateY(-2px);
  }

  .feature-card.featured {
    background: var(--sage);
    color: white;
    border-color: var(--sage);
    grid-column: span 2;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2rem;
    align-items: center;
  }

  .feature-icon {
    font-size: 2rem;
    margin-bottom: 1rem;
    display: block;
  }

  .feature-card h3 {
    font-family: 'Playfair Display', serif;
    font-size: 1.2rem;
    margin-bottom: 0.6rem;
    font-weight: 700;
  }

  .feature-card p {
    font-size: 0.9rem;
    color: var(--muted);
    line-height: 1.65;
  }

  .feature-card.featured p { color: rgba(255,255,255,0.8); }
  .feature-card.featured h3 { color: white; font-size: 1.6rem; }
  .feature-card.featured .feature-icon { font-size: 3rem; }

  .feature-bullets {
    list-style: none;
    margin-top: 1rem;
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
  }

  .feature-bullets li {
    display: flex;
    align-items: flex-start;
    gap: 0.5rem;
    font-size: 0.9rem;
    color: rgba(255,255,255,0.85);
  }

  .feature-bullets li::before {
    content: "✓";
    font-weight: 700;
    flex-shrink: 0;
    margin-top: 0.05rem;
  }

  /* HOW IT WORKS */
  .how-bg { background: var(--sage-light); }

  .steps {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 0;
    position: relative;
  }

  .steps::before {
    content: '';
    position: absolute;
    top: 2.5rem;
    left: 12%;
    right: 12%;
    height: 2px;
    background: var(--sage-mid);
    opacity: 0.4;
    z-index: 0;
  }

  .step {
    text-align: center;
    padding: 0 1.5rem;
    position: relative;
    z-index: 1;
  }

  .step-num {
    width: 5rem;
    height: 5rem;
    background: var(--sage);
    color: white;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Playfair Display', serif;
    font-size: 1.6rem;
    font-weight: 700;
    margin: 0 auto 1.25rem;
    border: 4px solid var(--sage-light);
    box-shadow: 0 0 0 2px var(--sage-mid);
  }

  .step h4 { font-size: 1rem; font-weight: 600; margin-bottom: 0.5rem; }
  .step p { font-size: 0.85rem; color: var(--muted); line-height: 1.6; }

  /* PRICING */
  .pricing-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1.5rem;
    align-items: start;
  }

  .plan-card {
    background: white;
    border: 1.5px solid var(--border);
    border-radius: var(--radius);
    padding: 2rem;
    position: relative;
  }

  .plan-card.popular {
    border-color: var(--sage);
    box-shadow: 0 0 0 4px rgba(90,125,90,0.1);
  }

  .popular-badge {
    position: absolute;
    top: -14px;
    left: 50%;
    transform: translateX(-50%);
    background: var(--sage);
    color: white;
    font-size: 0.72rem;
    font-weight: 700;
    letter-spacing: 0.06em;
    text-transform: uppercase;
    padding: 0.3rem 1rem;
    border-radius: 50px;
    white-space: nowrap;
  }

  .plan-name {
    font-size: 0.8rem;
    font-weight: 600;
    color: var(--muted);
    letter-spacing: 0.06em;
    text-transform: uppercase;
    margin-bottom: 0.75rem;
  }

  .plan-price {
    font-family: 'Playfair Display', serif;
    font-size: 2.4rem;
    font-weight: 700;
    margin-bottom: 0.25rem;
    color: var(--charcoal);
    line-height: 1;
  }

  .plan-price sup {
    font-size: 1rem;
    font-family: 'DM Sans', sans-serif;
    font-weight: 600;
    vertical-align: super;
    margin-right: 2px;
  }

  .plan-price sub {
    font-size: 0.9rem;
    font-family: 'DM Sans', sans-serif;
    font-weight: 400;
    color: var(--muted);
  }

  .plan-desc {
    font-size: 0.85rem;
    color: var(--muted);
    margin-bottom: 1.5rem;
    padding-bottom: 1.5rem;
    border-bottom: 1px solid var(--border);
    line-height: 1.6;
  }

  .plan-features {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 0.6rem;
    margin-bottom: 1.75rem;
  }

  .plan-features li {
    display: flex;
    align-items: flex-start;
    gap: 0.5rem;
    font-size: 0.88rem;
    color: var(--charcoal);
  }

  .check { color: var(--sage); font-weight: 700; flex-shrink: 0; }
  .cross { color: #c0b8b0; flex-shrink: 0; }

  .plan-btn {
    display: block;
    text-align: center;
    text-decoration: none;
    padding: 0.8rem;
    border-radius: 50px;
    font-weight: 600;
    font-size: 0.9rem;
    transition: all 0.2s;
    border: 1.5px solid var(--border);
    color: var(--charcoal);
  }

  .plan-btn:hover { border-color: var(--sage); color: var(--sage); }
  .plan-btn.primary-btn { background: var(--sage); color: white; border-color: var(--sage); }
  .plan-btn.primary-btn:hover { background: #4a6b4a; }

  /* TESTIMONIALS */
  .test-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1.5rem;
  }

  .test-card {
    background: white;
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 1.75rem;
  }

  .test-stars {
    color: var(--amber);
    font-size: 0.9rem;
    margin-bottom: 0.75rem;
  }

  .test-quote {
    font-size: 0.92rem;
    line-height: 1.7;
    color: var(--charcoal);
    margin-bottom: 1rem;
    font-style: italic;
  }

  .test-author {
    display: flex;
    align-items: center;
    gap: 0.75rem;
  }

  .test-avatar {
    width: 38px;
    height: 38px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1rem;
    font-weight: 600;
  }

  .test-author-info .name { font-weight: 600; font-size: 0.85rem; }
  .test-author-info .role { font-size: 0.78rem; color: var(--muted); }

  /* CTA FINAL */
  .cta-section {
    background: var(--sage);
    color: white;
    text-align: center;
    padding: 6rem 2rem;
  }

  .cta-section h2 {
    font-family: 'Playfair Display', serif;
    font-size: clamp(2rem, 3.5vw, 3rem);
    margin-bottom: 1rem;
    font-weight: 700;
  }

  .cta-section p {
    font-size: 1.05rem;
    color: rgba(255,255,255,0.8);
    max-width: 500px;
    margin: 0 auto 2rem;
    line-height: 1.75;
  }

  .btn-white {
    background: white;
    color: var(--sage);
    text-decoration: none;
    padding: 0.9rem 2.2rem;
    border-radius: 50px;
    font-weight: 700;
    font-size: 0.95rem;
    display: inline-block;
    transition: transform 0.15s, box-shadow 0.15s;
    box-shadow: 0 4px 20px rgba(0,0,0,0.15);
  }

  .btn-white:hover { transform: translateY(-2px); box-shadow: 0 8px 30px rgba(0,0,0,0.2); }

  /* FOOTER */
  footer {
    background: var(--charcoal);
    color: #9a9a9a;
    padding: 3rem 2rem;
    text-align: center;
  }

  .footer-logo {
    font-family: 'Playfair Display', serif;
    font-size: 1.5rem;
    color: white;
    margin-bottom: 0.5rem;
  }

  .footer-tagline { font-size: 0.85rem; margin-bottom: 2rem; }

  .footer-links {
    display: flex;
    justify-content: center;
    gap: 2rem;
    list-style: none;
    margin-bottom: 2rem;
    flex-wrap: wrap;
  }

  .footer-links a {
    color: #9a9a9a;
    text-decoration: none;
    font-size: 0.85rem;
    transition: color 0.2s;
  }

  .footer-links a:hover { color: var(--sage-mid); }

  .footer-copy { font-size: 0.78rem; }

  /* REDES SOCIALES */
  .social-section { background: var(--amber-light); }

  .social-cards {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 1rem;
  }

  .social-card {
    background: white;
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 1.5rem;
    text-align: center;
    text-decoration: none;
    color: inherit;
    transition: box-shadow 0.2s, transform 0.2s;
    display: block;
  }

  .social-card:hover { box-shadow: 0 4px 20px rgba(0,0,0,0.08); transform: translateY(-2px); }

  .social-icon { font-size: 2rem; margin-bottom: 0.75rem; display: block; }

  .social-card h4 { font-size: 0.95rem; font-weight: 600; margin-bottom: 0.25rem; }

  .social-card p { font-size: 0.8rem; color: var(--muted); }

  /* RESPONSIVE */
  @media (max-width: 900px) {
    .hero { grid-template-columns: 1fr; padding: 3rem 1.5rem; min-height: auto; gap: 3rem; }
    .features-grid { grid-template-columns: 1fr; }
    .feature-card.featured { grid-column: span 1; grid-template-columns: 1fr; }
    .problem-grid { grid-template-columns: 1fr; }
    .pricing-grid { grid-template-columns: 1fr; }
    .test-grid { grid-template-columns: 1fr; }
    .steps { grid-template-columns: repeat(2, 1fr); gap: 2rem; }
    .steps::before { display: none; }
    .social-cards { grid-template-columns: repeat(2, 1fr); }
    .hero-stats { grid-template-columns: repeat(2, 1fr); }
    nav { padding: 0 1rem; }
    .nav-links { display: none; }
  }

  /* ANIMACIONES DE ENTRADA */
  .fade-in {
    opacity: 0;
    transform: translateY(20px);
    transition: opacity 0.6s ease, transform 0.6s ease;
  }

  .fade-in.visible {
    opacity: 1;
    transform: translateY(0);
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <a href="#inicio" class="nav-logo">
    <span class="paw">🐾</span> PawMatch
  </a>
  <ul class="nav-links">
    <li><a href="#problema">El problema</a></li>
    <li><a href="#servicios">Servicios</a></li>
    <li><a href="#como-funciona">Como funciona</a></li>
    <li><a href="#precios">Precios</a></li>
    <li><a href="#contacto" class="nav-cta">Comenzar gratis</a></li>
  </ul>
</nav>

<!-- HERO -->
<div id="inicio">
<div class="hero">
  <div class="hero-content">
    <div class="hero-badge">🐾 Plataforma de adopcion inteligente</div>
    <h1>Encuentra tu <em>compañero</em> de vida ideal</h1>
    <p>PawMatch conecta a personas con mascotas en adopcion usando un algoritmo de compatibilidad basado en inteligencia artificial, promoviendo la adopcion responsable y reduciendo el abandono animal.</p>
    <div class="hero-buttons">
      <a href="#precios" class="btn-primary">Comenzar gratis</a>
      <a href="#como-funciona" class="btn-outline">Ver como funciona →</a>
    </div>
  </div>

  <div class="hero-visual">
    <div class="hero-card-main">
      <div class="pet-photo-placeholder">🐕</div>
      <div class="pet-info">
        <h3>Luna — Labrador, 2 años</h3>
        <p>Refugio Animal Tijuana · Disponible para adopcion</p>
        <div class="compatibility-bar">
          <div class="compatibility-fill"></div>
        </div>
        <div class="compat-label">
          <span>Compatibilidad con tu perfil</span>
          <span class="compat-score">87% match</span>
        </div>
      </div>
    </div>

    <div class="hero-stats">
      <div class="stat-mini">
        <span class="num">1,200+</span>
        <span class="lbl">Mascotas disponibles</span>
      </div>
      <div class="stat-mini">
        <span class="num">340+</span>
        <span class="lbl">Adopciones exitosas</span>
      </div>
      <div class="stat-mini">
        <span class="num">50+</span>
        <span class="lbl">Refugios aliados</span>
      </div>
      <div class="stat-mini">
        <span class="num">94%</span>
        <span class="lbl">Adopciones permanentes</span>
      </div>
    </div>
  </div>
</div>
</div>

<!-- PROBLEMA -->
<section class="problem-bg" id="problema">
  <div class="section-inner">
    <div class="section-label">El problema</div>
    <h2 class="section-title" style="color:white;">La adopcion tradicional falla a personas y mascotas</h2>
    <p class="section-sub">Miles de animales son devueltos o abandonados nuevamente por incompatibilidades que pudieron prevenirse desde el inicio.</p>
    <div class="problem-grid">
      <div class="problem-card fade-in">
        <span class="problem-icon">😔</span>
        <h4>Adopciones fallidas</h4>
        <p>El 30% de las mascotas adoptadas regresan al refugio en los primeros 6 meses por falta de compatibilidad real entre el animal y el adoptante.</p>
      </div>
      <div class="problem-card fade-in">
        <span class="problem-icon">🔍</span>
        <h4>Busqueda ineficiente</h4>
        <p>Los adoptantes navegan catálogos interminables sin criterios claros, lo que genera decision por impulso y no por compatibilidad real.</p>
      </div>
      <div class="problem-card fade-in">
        <span class="problem-icon">📋</span>
        <h4>Procesos sin seguimiento</h4>
        <p>Los refugios no tienen herramientas para monitorear el bienestar post-adopcion, perdiendo contacto con el adoptante inmediatamente despues del proceso.</p>
      </div>
    </div>
  </div>
</section>

<!-- SERVICIOS / FEATURES -->
<section id="servicios">
  <div class="section-inner">
    <div class="section-label">Nuestros servicios</div>
    <h2 class="section-title">Todo lo que necesitas para <em>adoptar bien</em></h2>
    <p class="section-sub">Una plataforma completa que atiende tanto a adoptantes como a refugios y organizaciones de rescate animal.</p>

    <div class="features-grid">
      <div class="feature-card featured fade-in">
        <div>
          <span class="feature-icon">🤖</span>
          <h3>Algoritmo de compatibilidad IA</h3>
          <p>Nuestro motor de inteligencia artificial analiza tu estilo de vida, espacio, experiencia con mascotas y preferencias para calcular un score de compatibilidad unico con cada animal disponible.</p>
          <ul class="feature-bullets">
            <li>Modelo de similitud coseno sobre vectores de perfil</li>
            <li>Aprende y mejora con cada adopcion exitosa</li>
            <li>Explica por que una mascota es compatible contigo</li>
            <li>Disponible via API para refugios aliados</li>
          </ul>
        </div>
        <div style="background:rgba(255,255,255,0.1); border-radius:12px; padding:1.5rem;">
          <div style="font-size:0.85rem; color:rgba(255,255,255,0.7); margin-bottom:0.75rem;">Tu perfil vs. mascotas disponibles</div>
          <div style="display:flex; flex-direction:column; gap:0.6rem;">
            <div>
              <div style="display:flex;justify-content:space-between;font-size:0.8rem;color:rgba(255,255,255,0.9);margin-bottom:4px;"><span>🐕 Luna</span><span>87%</span></div>
              <div style="background:rgba(255,255,255,0.2);border-radius:50px;height:6px;"><div style="background:white;width:87%;height:100%;border-radius:50px;"></div></div>
            </div>
            <div>
              <div style="display:flex;justify-content:space-between;font-size:0.8rem;color:rgba(255,255,255,0.9);margin-bottom:4px;"><span>🐈 Mochi</span><span>74%</span></div>
              <div style="background:rgba(255,255,255,0.2);border-radius:50px;height:6px;"><div style="background:white;width:74%;height:100%;border-radius:50px;"></div></div>
            </div>
            <div>
              <div style="display:flex;justify-content:space-between;font-size:0.8rem;color:rgba(255,255,255,0.9);margin-bottom:4px;"><span>🐕 Rocky</span><span>61%</span></div>
              <div style="background:rgba(255,255,255,0.2);border-radius:50px;height:6px;"><div style="background:rgba(255,255,255,0.6);width:61%;height:100%;border-radius:50px;"></div></div>
            </div>
          </div>
        </div>
      </div>

      <div class="feature-card fade-in">
        <span class="feature-icon">🏠</span>
        <h3>Catalogo inteligente</h3>
        <p>Accede a un catalogo de mascotas en tiempo real, conectado directamente a los sistemas de refugios aliados. Filtra por especie, tamaño, edad, energia y compatibilidad con tu perfil.</p>
      </div>

      <div class="feature-card fade-in">
        <span class="feature-icon">📱</span>
        <h3>Seguimiento post-adopcion</h3>
        <p>Recibe recordatorios de vacunas, citas veterinarias y registra el progreso de tu nueva mascota. Comparte actualizaciones con la comunidad y con el refugio de origen.</p>
      </div>

      <div class="feature-card fade-in">
        <span class="feature-icon">🏥</span>
        <h3>Panel para refugios</h3>
        <p>Herramientas especializadas para que los refugios gestionen sus animales, procesen solicitudes de adopcion, y accedan a estadisticas de impacto en tiempo real.</p>
      </div>

      <div class="feature-card fade-in">
        <span class="feature-icon">👥</span>
        <h3>Comunidad de adoptantes</h3>
        <p>Conecta con otros adoptantes, comparte consejos, recursos y experiencias. Accede a contenido educativo sobre cuidado animal responsable.</p>
      </div>
    </div>
  </div>
</section>

<!-- COMO FUNCIONA -->
<section class="how-bg" id="como-funciona">
  <div class="section-inner">
    <div class="section-label">Como funciona</div>
    <h2 class="section-title">De cero a tu nueva mascota en 4 pasos</h2>
    <p class="section-sub">Un proceso disenado para que la adopcion sea segura, informada y exitosa para ambos.</p>

    <div class="steps">
      <div class="step fade-in">
        <div class="step-num">1</div>
        <h4>Crea tu perfil</h4>
        <p>Responde un cuestionario sobre tu estilo de vida, espacio disponible, experiencia con mascotas y preferencias personales.</p>
      </div>
      <div class="step fade-in">
        <div class="step-num">2</div>
        <h4>Explora tu match</h4>
        <p>Nuestro algoritmo calcula tu compatibilidad con cada mascota disponible y te presenta los mejores candidatos ordenados por afinidad.</p>
      </div>
      <div class="step fade-in">
        <div class="step-num">3</div>
        <h4>Conecta con el refugio</h4>
        <p>Solicita informacion adicional o agenda una visita directamente a traves de la plataforma con el refugio responsable del animal.</p>
      </div>
      <div class="step fade-in">
        <div class="step-num">4</div>
        <h4>Adopta y haz seguimiento</h4>
        <p>Completa el proceso de adopcion y usa la app para registrar el bienestar de tu mascota a lo largo del tiempo.</p>
      </div>
    </div>
  </div>
</section>

<!-- PRECIOS -->
<section id="precios">
  <div class="section-inner">
    <div class="section-label">Precios</div>
    <h2 class="section-title">Planes para cada necesidad</h2>
    <p class="section-sub">Comenzar a explorar es gratuito. Las herramientas avanzadas estan disponibles para adoptantes serios y refugios profesionales.</p>

    <div class="pricing-grid">
      <div class="plan-card fade-in">
        <div class="plan-name">Basico</div>
        <div class="plan-price">Gratis</div>
        <p class="plan-desc">Para cualquier persona que quiera comenzar a explorar la adopcion responsable sin costo.</p>
        <ul class="plan-features">
          <li><span class="check">✓</span> Perfil de adoptante completo</li>
          <li><span class="check">✓</span> Catalogo de mascotas disponibles</li>
          <li><span class="check">✓</span> Compatibilidad basica (top 10)</li>
          <li><span class="check">✓</span> Contacto con refugios aliados</li>
          <li><span class="cross">–</span> Compatibilidad extendida IA</li>
          <li><span class="cross">–</span> Seguimiento post-adopcion</li>
          <li><span class="cross">–</span> Soporte prioritario</li>
        </ul>
        <a href="#contacto" class="plan-btn">Comenzar gratis</a>
      </div>

      <div class="plan-card popular fade-in">
        <div class="popular-badge">Mas popular</div>
        <div class="plan-name">Pro Adoptante</div>
        <div class="plan-price"><sup>$</sup>149<sub>/mes MXN</sub></div>
        <p class="plan-desc">Para adoptantes que quieren la experiencia completa con todas las herramientas de IA y seguimiento.</p>
        <ul class="plan-features">
          <li><span class="check">✓</span> Todo lo del plan Basico</li>
          <li><span class="check">✓</span> Compatibilidad IA completa</li>
          <li><span class="check">✓</span> Explicacion del score de match</li>
          <li><span class="check">✓</span> Seguimiento post-adopcion</li>
          <li><span class="check">✓</span> Recordatorios veterinarios</li>
          <li><span class="check">✓</span> Acceso a comunidad premium</li>
          <li><span class="check">✓</span> Soporte prioritario 24/7</li>
        </ul>
        <a href="#contacto" class="plan-btn primary-btn">Elegir Pro</a>
      </div>

      <div class="plan-card fade-in">
        <div class="plan-name">Refugios</div>
        <div class="plan-price"><sup>$</sup>499<sub>/mes MXN</sub></div>
        <p class="plan-desc">Para organizaciones de rescate y refugios que quieren gestionar sus animales y maximizar adopciones exitosas.</p>
        <ul class="plan-features">
          <li><span class="check">✓</span> Panel de gestion de animales</li>
          <li><span class="check">✓</span> Gestion de solicitudes</li>
          <li><span class="check">✓</span> Estadisticas e impacto</li>
          <li><span class="check">✓</span> Integracion via API</li>
          <li><span class="check">✓</span> Perfiles verificados</li>
          <li><span class="check">✓</span> Reportes mensuales</li>
          <li><span class="check">✓</span> Capacitacion incluida</li>
        </ul>
        <a href="#contacto" class="plan-btn">Contactar ventas</a>
      </div>
    </div>
  </div>
</section>

<!-- TESTIMONIOS -->
<section style="background: var(--sage-light);">
  <div class="section-inner">
    <div class="section-label">Testimonios</div>
    <h2 class="section-title">Lo que dicen nuestros usuarios</h2>
    <p class="section-sub">Historias reales de adopciones exitosas facilitadas por PawMatch.</p>

    <div class="test-grid">
      <div class="test-card fade-in">
        <div class="test-stars">★★★★★</div>
        <p class="test-quote">"El algoritmo fue increiblemente preciso. Me mostro a Max y desde el primer momento supe que eramos perfectos el uno para el otro. Ya llevamos 8 meses juntos y no podria estar mas feliz."</p>
        <div class="test-author">
          <div class="test-avatar" style="background:#e8f0e8; color:#5a7d5a;">SM</div>
          <div class="test-author-info">
            <div class="name">Sofia Martinez</div>
            <div class="role">Adoptante en Tijuana</div>
          </div>
        </div>
      </div>

      <div class="test-card fade-in">
        <div class="test-stars">★★★★★</div>
        <p class="test-quote">"Como refugio, siempre temimos que las mascotas fueran devueltas. Desde que usamos PawMatch, nuestra tasa de retorno bajo de 28% a menos del 4%. Es una herramienta transformadora."</p>
        <div class="test-author">
          <div class="test-avatar" style="background:#fdf3e7; color:#c97d3a;">CR</div>
          <div class="test-author-info">
            <div class="name">Carlos Reyes</div>
            <div class="role">Director, Refugio Animal Tijuana</div>
          </div>
        </div>
      </div>

      <div class="test-card fade-in">
        <div class="test-stars">★★★★★</div>
        <p class="test-quote">"Vivo en un departamento pequeño y tenia dudas sobre que mascota era adecuada. PawMatch me explico exactamente por que ciertos perros eran compatibles con mi estilo de vida. Excelente experiencia."</p>
        <div class="test-author">
          <div class="test-avatar" style="background:#e8f0e8; color:#5a7d5a;">AL</div>
          <div class="test-author-info">
            <div class="name">Andrea Lopez</div>
            <div class="role">Adoptante en Ensenada</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- REDES SOCIALES -->
<section class="social-section" id="redes">
  <div class="section-inner">
    <div class="section-label">Siguenos</div>
    <h2 class="section-title">Conecta con la comunidad PawMatch</h2>
    <p class="section-sub">Encontranos en redes sociales para contenido sobre adopcion responsable, consejos de cuidado animal y actualizaciones de la plataforma.</p>

    <div class="social-cards">
      <div class="social-card">
        <span class="social-icon">📘</span>
        <h4>Facebook</h4>
        <p>@PawMatchMX · Noticias, eventos y comunidad</p>
      </div>
      <div class="social-card">
        <span class="social-icon">📸</span>
        <h4>Instagram</h4>
        <p>@PawMatchMX · Historias de adopcion exitosas</p>
      </div>
      <div class="social-card">
        <span class="social-icon">💼</span>
        <h4>LinkedIn</h4>
        <p>PawMatch · Actualizaciones del producto e impacto</p>
      </div>
      <div class="social-card">
        <span class="social-icon">🐦</span>
        <h4>Twitter / X</h4>
        <p>@PawMatchMX · Noticias y conversaciones</p>
      </div>
    </div>
  </div>
</section>

<!-- CTA FINAL -->
<section class="cta-section" id="contacto">
  <h2>¿Listo para encontrar a tu companero de vida?</h2>
  <p>Unete a miles de personas que ya encontraron a su mascota ideal a traves de PawMatch. Comenzar es completamente gratuito.</p>
  <a href="mailto:contacto@pawmatch.mx" class="btn-white">Comenzar ahora — es gratis</a>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-logo">🐾 PawMatch</div>
  <p class="footer-tagline">Adopcion responsable, impulsada por inteligencia artificial.</p>
  <ul class="footer-links">
    <li><a href="#servicios">Servicios</a></li>
    <li><a href="#precios">Precios</a></li>
    <li><a href="#redes">Redes sociales</a></li>
    <li><a href="mailto:contacto@pawmatch.mx">Contacto</a></li>
    <li><a href="#">Terminos de uso</a></li>
    <li><a href="#">Privacidad</a></li>
  </ul>
  <p class="footer-copy">© 2026 PawMatch. Todos los derechos reservados. · Tijuana, Baja California, Mexico.</p>
</footer>

<script>
const observer = new IntersectionObserver((entries) => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      e.target.classList.add('visible');
    }
  });
}, { threshold: 0.1 });

document.querySelectorAll('.fade-in').forEach(el => observer.observe(el));
</script>

</body>
</html>
