<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>PawMatch v2 — Adopción responsable de mascotas</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Fraunces:ital,wght@0,300;0,600;0,900;1,300;1,600&family=Instrument+Sans:wght@400;500;600&display=swap" rel="stylesheet">
<style>
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0;}
:root{
  --ink:#1a1a18;
  --sage:#3d6b47;
  --sage-mid:#6a9b76;
  --sage-light:#e4efe6;
  --sage-pale:#f3f8f4;
  --amber:#b8621a;
  --amber-light:#fdf0e4;
  --cream:#faf8f2;
  --warm:#f2ede3;
  --muted:#6b6860;
  --border:#ddd9cf;
  --white:#ffffff;
  --r:14px;
  --r-sm:8px;
}
html{scroll-behavior:smooth;}
body{font-family:'Instrument Sans',sans-serif;background:var(--cream);color:var(--ink);line-height:1.6;overflow-x:hidden;}

/* ── CURSOR ── */
*{cursor:none!important;}
.cursor{position:fixed;width:12px;height:12px;background:var(--sage);border-radius:50%;pointer-events:none;z-index:9999;transform:translate(-50%,-50%);transition:transform .15s,background .2s,width .2s,height .2s;}
.cursor-ring{position:fixed;width:36px;height:36px;border:1.5px solid var(--sage);border-radius:50%;pointer-events:none;z-index:9998;transform:translate(-50%,-50%);transition:transform .25s ease,border-color .2s;}
body:hover .cursor{opacity:1;}

/* ── NAV ── */
nav{position:fixed;top:0;left:0;right:0;z-index:100;padding:0 3rem;height:68px;display:flex;align-items:center;justify-content:space-between;background:rgba(250,248,242,.88);backdrop-filter:blur(16px);border-bottom:1px solid var(--border);}
.nav-logo{font-family:'Fraunces',serif;font-size:1.45rem;font-weight:600;color:var(--sage);text-decoration:none;letter-spacing:-.02em;display:flex;align-items:center;gap:.35rem;}
.nav-dot{width:8px;height:8px;background:var(--amber);border-radius:50%;display:inline-block;}
.nav-links{display:flex;gap:2.2rem;list-style:none;}
.nav-links a{text-decoration:none;color:var(--muted);font-size:.85rem;font-weight:500;letter-spacing:.02em;transition:color .2s;}
.nav-links a:hover{color:var(--sage);}
.nav-cta{background:var(--ink)!important;color:var(--white)!important;padding:.45rem 1.1rem;border-radius:50px;font-size:.82rem!important;font-weight:600!important;transition:background .2s!important;}
.nav-cta:hover{background:var(--sage)!important;}
@media(max-width:800px){.nav-links{display:none;}nav{padding:0 1.2rem;}}

/* ── HERO ── */
.hero{min-height:100vh;display:grid;grid-template-columns:1fr 1fr;align-items:center;gap:0;padding-top:68px;}
.hero-left{padding:6rem 4rem 6rem 5rem;background:var(--cream);}
.hero-right{background:var(--sage);height:100%;min-height:calc(100vh - 68px);display:flex;flex-direction:column;justify-content:center;padding:4rem 3.5rem;position:relative;overflow:hidden;}
.hero-right::before{content:'';position:absolute;top:-80px;right:-80px;width:320px;height:320px;border-radius:50%;background:rgba(255,255,255,.06);}
.hero-right::after{content:'';position:absolute;bottom:-60px;left:-60px;width:220px;height:220px;border-radius:50%;background:rgba(255,255,255,.05);}
.hero-tag{display:inline-flex;align-items:center;gap:.5rem;background:var(--sage-light);color:var(--sage);font-size:.72rem;font-weight:600;letter-spacing:.1em;text-transform:uppercase;padding:.35rem .85rem;border-radius:50px;margin-bottom:1.5rem;}
.hero h1{font-family:'Fraunces',serif;font-size:clamp(3rem,5vw,4.8rem);line-height:1.05;font-weight:900;letter-spacing:-.03em;margin-bottom:1.25rem;}
.hero h1 em{font-style:italic;color:var(--sage);}
.hero-desc{font-size:1.05rem;color:var(--muted);max-width:480px;line-height:1.75;margin-bottom:2.2rem;}
.hero-btns{display:flex;gap:.9rem;flex-wrap:wrap;}
.btn-dark{background:var(--ink);color:var(--white);text-decoration:none;padding:.8rem 1.8rem;border-radius:50px;font-weight:600;font-size:.9rem;transition:background .2s,transform .15s;display:inline-block;}
.btn-dark:hover{background:var(--sage);transform:translateY(-1px);}
.btn-ghost{border:1.5px solid var(--border);color:var(--ink);text-decoration:none;padding:.8rem 1.8rem;border-radius:50px;font-weight:500;font-size:.9rem;transition:border-color .2s,color .2s;display:inline-block;}
.btn-ghost:hover{border-color:var(--sage);color:var(--sage);}
/* Hero derecha */
.hero-card{background:rgba(255,255,255,.12);border:1px solid rgba(255,255,255,.2);border-radius:var(--r);padding:1.5rem;margin-bottom:1rem;position:relative;z-index:1;}
.hero-card h3{font-family:'Fraunces',serif;color:var(--white);font-size:1.1rem;font-weight:600;margin-bottom:.25rem;}
.hero-card p{color:rgba(255,255,255,.7);font-size:.85rem;margin-bottom:1rem;}
.compat-row{display:flex;justify-content:space-between;align-items:center;margin-bottom:.4rem;}
.compat-label{font-size:.8rem;color:rgba(255,255,255,.8);}
.compat-score{font-family:'Fraunces',serif;font-size:1rem;font-weight:600;color:var(--white);}
.compat-bar{background:rgba(255,255,255,.2);height:6px;border-radius:50px;overflow:hidden;}
.compat-fill{height:100%;border-radius:50px;background:var(--white);animation:grow 1.5s ease-out forwards;}
@keyframes grow{from{width:0;}to{width:var(--w);}}
.hero-stats-grid{display:grid;grid-template-columns:1fr 1fr;gap:.75rem;position:relative;z-index:1;}
.stat-card{background:rgba(255,255,255,.1);border:1px solid rgba(255,255,255,.15);border-radius:var(--r-sm);padding:1rem 1.25rem;text-align:center;}
.stat-num{font-family:'Fraunces',serif;font-size:1.8rem;font-weight:900;color:var(--white);display:block;}
.stat-lbl{font-size:.72rem;color:rgba(255,255,255,.65);letter-spacing:.04em;}
@media(max-width:900px){.hero{grid-template-columns:1fr;}.hero-left{padding:3rem 1.5rem;}.hero-right{min-height:auto;padding:3rem 1.5rem;}}

/* ── SECCIONES BASE ── */
section{padding:7rem 2rem;}
.inner{max-width:1140px;margin:0 auto;}
.sec-tag{display:inline-flex;align-items:center;gap:.4rem;background:var(--amber-light);color:var(--amber);font-size:.72rem;font-weight:600;letter-spacing:.1em;text-transform:uppercase;padding:.35rem .85rem;border-radius:50px;margin-bottom:.85rem;}
.sec-title{font-family:'Fraunces',serif;font-size:clamp(2rem,3.5vw,3rem);font-weight:900;letter-spacing:-.03em;line-height:1.1;margin-bottom:.85rem;}
.sec-sub{font-size:1rem;color:var(--muted);max-width:560px;line-height:1.75;margin-bottom:3rem;}

/* ── DEMO INTERACTIVA DEL ALGORITMO ── */
.demo-section{background:var(--ink);}
.demo-section .sec-title{color:var(--white);}
.demo-section .sec-tag{background:rgba(255,255,255,.1);color:rgba(255,255,255,.7);}
.demo-section .sec-sub{color:rgba(255,255,255,.55);}
.demo-container{display:grid;grid-template-columns:1fr 1fr;gap:2.5rem;align-items:start;}
.quiz-panel{background:rgba(255,255,255,.05);border:1px solid rgba(255,255,255,.1);border-radius:var(--r);padding:2rem;}
.quiz-panel h3{font-family:'Fraunces',serif;color:var(--white);font-size:1.2rem;margin-bottom:1.5rem;font-weight:600;}
.quiz-step{margin-bottom:1.5rem;display:none;}
.quiz-step.active{display:block;}
.quiz-q{font-size:.9rem;color:rgba(255,255,255,.8);margin-bottom:.85rem;font-weight:500;}
.quiz-opts{display:flex;flex-direction:column;gap:.5rem;}
.quiz-opt{background:rgba(255,255,255,.06);border:1px solid rgba(255,255,255,.12);border-radius:var(--r-sm);padding:.7rem 1rem;font-size:.85rem;color:rgba(255,255,255,.75);transition:all .2s;cursor:none!important;}
.quiz-opt:hover,.quiz-opt.selected{background:var(--sage);border-color:var(--sage);color:var(--white);}
.quiz-progress{display:flex;gap:.4rem;margin-bottom:1.5rem;}
.qp-dot{width:8px;height:8px;border-radius:50%;background:rgba(255,255,255,.2);transition:background .3s;}
.qp-dot.done{background:var(--sage-mid);}
.qp-dot.active{background:var(--white);}
.quiz-nav{display:flex;gap:.75rem;margin-top:1.25rem;}
.quiz-btn{padding:.55rem 1.2rem;border-radius:50px;border:none;font-family:'Instrument Sans',sans-serif;font-size:.85rem;font-weight:600;cursor:none!important;transition:all .2s;}
.quiz-btn-next{background:var(--sage);color:var(--white);}
.quiz-btn-next:hover{background:#4d8459;}
.quiz-btn-back{background:rgba(255,255,255,.08);color:rgba(255,255,255,.7);}
.results-panel{background:rgba(255,255,255,.05);border:1px solid rgba(255,255,255,.1);border-radius:var(--r);padding:2rem;}
.results-panel h3{font-family:'Fraunces',serif;color:var(--white);font-size:1.2rem;margin-bottom:1.5rem;font-weight:600;}
.result-card{background:rgba(255,255,255,.07);border:1px solid rgba(255,255,255,.1);border-radius:var(--r-sm);padding:1.1rem;margin-bottom:.85rem;display:flex;align-items:center;gap:1rem;opacity:.4;transform:translateY(8px);transition:all .5s;}
.result-card.visible{opacity:1;transform:translateY(0);}
.result-icon{font-size:1.8rem;flex-shrink:0;}
.result-info{flex:1;}
.result-name{font-family:'Fraunces',serif;color:var(--white);font-size:1rem;font-weight:600;}
.result-breed{font-size:.78rem;color:rgba(255,255,255,.5);margin-bottom:.4rem;}
.result-bar-wrap{background:rgba(255,255,255,.15);border-radius:50px;height:5px;overflow:hidden;}
.result-bar{height:100%;background:var(--sage-mid);border-radius:50px;width:0;transition:width 1s ease-out;}
.result-pct{font-family:'Fraunces',serif;color:var(--white);font-size:1rem;font-weight:900;flex-shrink:0;}
.demo-placeholder{display:flex;flex-direction:column;align-items:center;justify-content:center;height:100%;text-align:center;color:rgba(255,255,255,.4);font-size:.9rem;padding:2rem;}
.demo-placeholder span{font-size:3rem;display:block;margin-bottom:.75rem;}
@media(max-width:900px){.demo-container{grid-template-columns:1fr;}}

/* ── SERVICIOS ── */
.services-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:1.25rem;}
.svc-card{background:var(--white);border:1px solid var(--border);border-radius:var(--r);padding:2rem;transition:box-shadow .25s,transform .25s;position:relative;overflow:hidden;}
.svc-card::before{content:'';position:absolute;top:0;left:0;right:0;height:3px;background:var(--sage);transform:scaleX(0);transform-origin:left;transition:transform .3s;}
.svc-card:hover::before{transform:scaleX(1);}
.svc-card:hover{box-shadow:0 12px 40px rgba(0,0,0,.08);transform:translateY(-3px);}
.svc-card.featured{background:var(--sage);grid-column:span 2;display:grid;grid-template-columns:1fr 1fr;gap:2rem;align-items:center;}
.svc-icon{font-size:2rem;margin-bottom:1rem;display:block;}
.svc-card h3{font-family:'Fraunces',serif;font-size:1.2rem;font-weight:600;margin-bottom:.6rem;letter-spacing:-.01em;}
.svc-card p{font-size:.88rem;color:var(--muted);line-height:1.7;margin-bottom:1rem;}
.svc-card.featured h3{color:var(--white);font-size:1.5rem;}
.svc-card.featured p{color:rgba(255,255,255,.8);}
.svc-detail-list{list-style:none;display:flex;flex-direction:column;gap:.45rem;}
.svc-detail-list li{font-size:.83rem;color:var(--muted);display:flex;align-items:flex-start;gap:.5rem;}
.svc-detail-list li::before{content:"→";color:var(--sage);flex-shrink:0;font-size:.8rem;margin-top:.05rem;}
.svc-card.featured .svc-detail-list li{color:rgba(255,255,255,.75);}
.svc-card.featured .svc-detail-list li::before{color:rgba(255,255,255,.5);}
.svc-tag{display:inline-block;background:var(--sage-light);color:var(--sage);font-size:.7rem;font-weight:600;letter-spacing:.06em;text-transform:uppercase;padding:.25rem .6rem;border-radius:50px;margin-bottom:.75rem;}
@media(max-width:900px){.services-grid{grid-template-columns:1fr;}.svc-card.featured{grid-column:span 1;grid-template-columns:1fr;}}

/* ── COMO FUNCIONA / ANIMACION ── */
.how-bg{background:var(--warm);}
.steps-visual{display:grid;grid-template-columns:repeat(4,1fr);gap:0;position:relative;}
.steps-visual::before{content:'';position:absolute;top:2.5rem;left:12.5%;right:12.5%;height:1px;background:linear-gradient(to right,var(--sage-mid),var(--border),var(--sage-mid));z-index:0;}
.step-item{text-align:center;padding:0 1rem;position:relative;z-index:1;}
.step-num{width:5rem;height:5rem;background:var(--white);border:2px solid var(--sage-mid);border-radius:50%;display:flex;align-items:center;justify-content:center;margin:0 auto 1.25rem;font-family:'Fraunces',serif;font-size:1.4rem;font-weight:900;color:var(--sage);transition:background .3s,color .3s;box-shadow:0 4px 16px rgba(61,107,71,.15);}
.step-item:hover .step-num{background:var(--sage);color:var(--white);}
.step-item h4{font-family:'Fraunces',serif;font-size:1rem;font-weight:600;margin-bottom:.4rem;}
.step-item p{font-size:.83rem;color:var(--muted);line-height:1.65;}
@media(max-width:800px){.steps-visual{grid-template-columns:repeat(2,1fr);gap:2rem;}.steps-visual::before{display:none;}}

/* ── PRECIOS ── */
.pricing-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:1.25rem;align-items:start;}
.plan{background:var(--white);border:1.5px solid var(--border);border-radius:var(--r);padding:2rem;position:relative;}
.plan.highlight{border-color:var(--sage);box-shadow:0 0 0 4px rgba(61,107,71,.1);}
.plan-badge{position:absolute;top:-13px;left:50%;transform:translateX(-50%);background:var(--sage);color:var(--white);font-size:.7rem;font-weight:700;letter-spacing:.06em;text-transform:uppercase;padding:.3rem 1rem;border-radius:50px;white-space:nowrap;}
.plan-name{font-size:.75rem;font-weight:600;color:var(--muted);letter-spacing:.07em;text-transform:uppercase;margin-bottom:.75rem;}
.plan-price{font-family:'Fraunces',serif;font-size:2.6rem;font-weight:900;letter-spacing:-.04em;line-height:1;margin-bottom:.25rem;}
.plan-price sup{font-size:1.1rem;font-family:'Instrument Sans',sans-serif;font-weight:600;vertical-align:super;}
.plan-price sub{font-size:.85rem;font-family:'Instrument Sans',sans-serif;font-weight:400;color:var(--muted);}
.plan-desc{font-size:.83rem;color:var(--muted);margin-bottom:1.5rem;padding-bottom:1.5rem;border-bottom:1px solid var(--border);line-height:1.65;}
.plan-features{list-style:none;display:flex;flex-direction:column;gap:.55rem;margin-bottom:1.75rem;}
.plan-features li{display:flex;align-items:flex-start;gap:.5rem;font-size:.85rem;}
.pf-yes{color:var(--sage);font-weight:700;flex-shrink:0;}
.pf-no{color:var(--border);flex-shrink:0;}
.plan-btn{display:block;text-align:center;text-decoration:none;padding:.75rem;border-radius:50px;font-weight:600;font-size:.88rem;transition:all .2s;border:1.5px solid var(--border);color:var(--ink);}
.plan-btn:hover{border-color:var(--sage);color:var(--sage);}
.plan-btn.cta{background:var(--sage);color:var(--white);border-color:var(--sage);}
.plan-btn.cta:hover{background:#4d8459;}
@media(max-width:900px){.pricing-grid{grid-template-columns:1fr;}}

/* ── TESTIMONIOS ── */
.testi-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:1.25rem;}
.testi-card{background:var(--white);border:1px solid var(--border);border-radius:var(--r);padding:1.75rem;}
.testi-stars{color:var(--amber);font-size:.9rem;margin-bottom:.75rem;}
.testi-quote{font-family:'Fraunces',serif;font-size:1rem;font-weight:300;font-style:italic;line-height:1.7;color:var(--ink);margin-bottom:1.1rem;}
.testi-author{display:flex;align-items:center;gap:.75rem;}
.testi-av{width:38px;height:38px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-weight:700;font-size:.85rem;}
.testi-name{font-weight:600;font-size:.85rem;}
.testi-role{font-size:.75rem;color:var(--muted);}
@media(max-width:900px){.testi-grid{grid-template-columns:1fr;}}

/* ── FAQ ── */
.faq-section{background:var(--sage-pale);}
.faq-list{display:flex;flex-direction:column;gap:.75rem;max-width:800px;}
.faq-item{background:var(--white);border:1px solid var(--border);border-radius:var(--r-sm);overflow:hidden;}
.faq-q{width:100%;background:none;border:none;padding:1.2rem 1.5rem;text-align:left;font-family:'Instrument Sans',sans-serif;font-size:.95rem;font-weight:600;color:var(--ink);display:flex;justify-content:space-between;align-items:center;gap:1rem;cursor:none!important;transition:color .2s;}
.faq-q:hover{color:var(--sage);}
.faq-arrow{width:20px;height:20px;border:1.5px solid var(--border);border-radius:50%;display:flex;align-items:center;justify-content:center;flex-shrink:0;font-size:.7rem;transition:transform .3s,background .2s,border-color .2s;}
.faq-item.open .faq-arrow{transform:rotate(180deg);background:var(--sage);border-color:var(--sage);color:var(--white);}
.faq-a{max-height:0;overflow:hidden;transition:max-height .4s ease,padding .3s;}
.faq-a-inner{padding:0 1.5rem 1.25rem;font-size:.88rem;color:var(--muted);line-height:1.75;}
.faq-item.open .faq-a{max-height:300px;}

/* ── REGISTRO ── */
.register-section{background:var(--sage);}
.register-inner{display:grid;grid-template-columns:1fr 1fr;gap:4rem;align-items:center;}
.register-text h2{font-family:'Fraunces',serif;font-size:clamp(2rem,3.5vw,3rem);font-weight:900;color:var(--white);letter-spacing:-.03em;line-height:1.1;margin-bottom:.85rem;}
.register-text p{font-size:1rem;color:rgba(255,255,255,.75);line-height:1.75;}
.register-form{background:rgba(255,255,255,.1);border:1px solid rgba(255,255,255,.2);border-radius:var(--r);padding:2.25rem;}
.form-title{font-family:'Fraunces',serif;color:var(--white);font-size:1.25rem;font-weight:600;margin-bottom:1.5rem;}
.form-group{margin-bottom:1.1rem;}
.form-label{display:block;font-size:.8rem;font-weight:600;color:rgba(255,255,255,.75);letter-spacing:.04em;margin-bottom:.4rem;}
.form-input,.form-select{width:100%;background:rgba(255,255,255,.12);border:1px solid rgba(255,255,255,.2);border-radius:var(--r-sm);padding:.7rem 1rem;font-family:'Instrument Sans',sans-serif;font-size:.88rem;color:var(--white);outline:none;transition:border-color .2s,background .2s;}
.form-input::placeholder{color:rgba(255,255,255,.4);}
.form-input:focus,.form-select:focus{border-color:rgba(255,255,255,.6);background:rgba(255,255,255,.18);}
.form-select option{color:var(--ink);background:var(--white);}
.form-row{display:grid;grid-template-columns:1fr 1fr;gap:.85rem;}
.form-submit{width:100%;background:var(--white);color:var(--sage);border:none;border-radius:50px;padding:.85rem;font-family:'Instrument Sans',sans-serif;font-size:.9rem;font-weight:700;cursor:none!important;transition:background .2s,transform .15s;margin-top:.5rem;}
.form-submit:hover{background:var(--warm);transform:translateY(-1px);}
.form-note{font-size:.75rem;color:rgba(255,255,255,.5);text-align:center;margin-top:.75rem;}
.form-success{display:none;text-align:center;padding:2rem;color:var(--white);}
.form-success span{font-size:3rem;display:block;margin-bottom:.75rem;}
.form-success h3{font-family:'Fraunces',serif;font-size:1.5rem;font-weight:600;margin-bottom:.5rem;}
.form-success p{font-size:.9rem;color:rgba(255,255,255,.75);}
@media(max-width:900px){.register-inner{grid-template-columns:1fr;}.form-row{grid-template-columns:1fr;}}

/* ── REDES SOCIALES ── */
.social-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:1rem;}
.social-card{background:var(--white);border:1px solid var(--border);border-radius:var(--r);padding:1.5rem;text-align:center;text-decoration:none;color:inherit;transition:box-shadow .2s,transform .2s;display:block;}
.social-card:hover{box-shadow:0 8px 30px rgba(0,0,0,.07);transform:translateY(-2px);}
.social-icon{font-size:2rem;margin-bottom:.7rem;display:block;}
.social-card h4{font-family:'Fraunces',serif;font-size:1rem;font-weight:600;margin-bottom:.25rem;}
.social-card p{font-size:.78rem;color:var(--muted);}
@media(max-width:800px){.social-grid{grid-template-columns:repeat(2,1fr);}}

/* ── CTA FINAL ── */
.cta-final{background:var(--ink);text-align:center;padding:7rem 2rem;}
.cta-final h2{font-family:'Fraunces',serif;font-size:clamp(2.5rem,5vw,4rem);font-weight:900;color:var(--white);letter-spacing:-.04em;line-height:1.05;margin-bottom:1rem;}
.cta-final h2 em{font-style:italic;color:var(--sage-mid);}
.cta-final p{font-size:1rem;color:rgba(255,255,255,.55);max-width:480px;margin:0 auto 2rem;line-height:1.75;}
.btn-white{background:var(--white);color:var(--ink);text-decoration:none;padding:.9rem 2.2rem;border-radius:50px;font-weight:700;font-size:.95rem;display:inline-block;transition:transform .15s,box-shadow .15s;box-shadow:0 4px 20px rgba(0,0,0,.2);}
.btn-white:hover{transform:translateY(-2px);box-shadow:0 8px 30px rgba(0,0,0,.3);}

/* ── FOOTER ── */
footer{background:var(--ink);border-top:1px solid rgba(255,255,255,.06);padding:3rem 2rem;text-align:center;}
.footer-logo{font-family:'Fraunces',serif;font-size:1.5rem;color:var(--white);margin-bottom:.4rem;font-weight:600;}
.footer-tag{font-size:.8rem;color:rgba(255,255,255,.4);margin-bottom:2rem;}
.footer-links{display:flex;justify-content:center;gap:2rem;list-style:none;flex-wrap:wrap;margin-bottom:2rem;}
.footer-links a{color:rgba(255,255,255,.4);text-decoration:none;font-size:.8rem;transition:color .2s;}
.footer-links a:hover{color:var(--sage-mid);}
.footer-copy{font-size:.75rem;color:rgba(255,255,255,.25);}

/* ── FADE IN ── */
.reveal{opacity:0;transform:translateY(22px);transition:opacity .65s ease,transform .65s ease;}
.reveal.in{opacity:1;transform:translateY(0);}

/* ── VERSION BADGE ── */
.v-badge{display:inline-flex;align-items:center;gap:.35rem;background:var(--amber);color:var(--white);font-size:.7rem;font-weight:700;letter-spacing:.06em;text-transform:uppercase;padding:.25rem .65rem;border-radius:50px;margin-left:.5rem;vertical-align:middle;}
</style>
</head>
<body>

<!-- CURSOR PERSONALIZADO -->
<div class="cursor" id="cur"></div>
<div class="cursor-ring" id="ring"></div>

<!-- NAV -->
<nav>
  <a href="#inicio" class="nav-logo">PawMatch <span class="nav-dot"></span></a>
  <ul class="nav-links">
    <li><a href="#demo">Demo IA</a></li>
    <li><a href="#servicios">Servicios</a></li>
    <li><a href="#precios">Precios</a></li>
    <li><a href="#faq">FAQ</a></li>
    <li><a href="#registro" class="nav-cta">Comenzar gratis</a></li>
  </ul>
</nav>

<!-- HERO -->
<div id="inicio">
<div class="hero">
  <div class="hero-left">
    <div class="hero-tag">🐾 Versión 2 <span class="v-badge">Nuevo</span></div>
    <h1>La adopción<br>que <em>conecta</em><br>de verdad.</h1>
    <p class="hero-desc">PawMatch usa inteligencia artificial para calcular qué tan compatible eres con cada mascota en adopción. No más decisiones por impulso — solo conexiones que duran.</p>
    <div class="hero-btns">
      <a href="#registro" class="btn-dark">Crear cuenta gratis</a>
      <a href="#demo" class="btn-ghost">Ver demo del algoritmo →</a>
    </div>
  </div>

  <div class="hero-right">
    <div class="hero-card">
      <h3>Luna — Labrador, 2 años</h3>
      <p>Refugio Animal Tijuana · Disponible para adopción</p>
      <div class="compat-row"><span class="compat-label">Compatibilidad con tu perfil</span><span class="compat-score">87%</span></div>
      <div class="compat-bar"><div class="compat-fill" style="--w:87%"></div></div>
    </div>
    <div class="hero-stats-grid">
      <div class="stat-card"><span class="stat-num">1,200+</span><span class="stat-lbl">Mascotas disponibles</span></div>
      <div class="stat-card"><span class="stat-num">340+</span><span class="stat-lbl">Adopciones exitosas</span></div>
      <div class="stat-card"><span class="stat-num">50+</span><span class="stat-lbl">Refugios aliados</span></div>
      <div class="stat-card"><span class="stat-num">94%</span><span class="stat-lbl">Adopciones permanentes</span></div>
    </div>
  </div>
</div>
</div>

<!-- DEMO INTERACTIVA -->
<section class="demo-section" id="demo">
  <div class="inner">
    <div class="sec-tag">Demo interactiva</div>
    <h2 class="sec-title reveal" style="color:var(--white)">Prueba el algoritmo<br>de compatibilidad</h2>
    <p class="sec-sub reveal">Responde 5 preguntas sobre tu estilo de vida y el algoritmo calculará qué mascotas son más compatibles contigo en tiempo real.</p>

    <div class="demo-container">
      <div class="quiz-panel">
        <div class="quiz-progress" id="qprog">
          <div class="qp-dot active"></div>
          <div class="qp-dot"></div>
          <div class="qp-dot"></div>
          <div class="qp-dot"></div>
          <div class="qp-dot"></div>
        </div>
        <h3 id="quiz-title">Cuéntanos sobre ti</h3>

        <div class="quiz-step active" data-step="0">
          <p class="quiz-q">¿Cuánto espacio tienes en casa?</p>
          <div class="quiz-opts">
            <div class="quiz-opt" data-val="small">Departamento pequeño (menos de 60 m²)</div>
            <div class="quiz-opt" data-val="medium">Departamento o casa mediana (60–100 m²)</div>
            <div class="quiz-opt" data-val="large">Casa grande con jardín (más de 100 m²)</div>
          </div>
        </div>

        <div class="quiz-step" data-step="1">
          <p class="quiz-q">¿Qué tan activo es tu estilo de vida?</p>
          <div class="quiz-opts">
            <div class="quiz-opt" data-val="low">Tranquilo — prefiero quedarme en casa</div>
            <div class="quiz-opt" data-val="medium">Moderado — salgo a caminar con regularidad</div>
            <div class="quiz-opt" data-val="high">Muy activo — hago ejercicio a diario</div>
          </div>
        </div>

        <div class="quiz-step" data-step="2">
          <p class="quiz-q">¿Cuántas horas al día estás fuera de casa?</p>
          <div class="quiz-opts">
            <div class="quiz-opt" data-val="few">Menos de 4 horas — trabajo remoto o en casa</div>
            <div class="quiz-opt" data-val="moderate">Entre 4 y 8 horas — horario de oficina</div>
            <div class="quiz-opt" data-val="many">Más de 8 horas — viajo o tengo horario extendido</div>
          </div>
        </div>

        <div class="quiz-step" data-step="3">
          <p class="quiz-q">¿Tienes experiencia con mascotas?</p>
          <div class="quiz-opts">
            <div class="quiz-opt" data-val="none">Primera vez que adopto</div>
            <div class="quiz-opt" data-val="some">He tenido mascotas antes</div>
            <div class="quiz-opt" data-val="expert">Tengo mucha experiencia con animales</div>
          </div>
        </div>

        <div class="quiz-step" data-step="4">
          <p class="quiz-q">¿Hay niños o adultos mayores en tu hogar?</p>
          <div class="quiz-opts">
            <div class="quiz-opt" data-val="kids">Sí, hay niños menores de 10 años</div>
            <div class="quiz-opt" data-val="elderly">Sí, hay adultos mayores</div>
            <div class="quiz-opt" data-val="adults">No, solo adultos</div>
          </div>
        </div>

        <div class="quiz-nav" id="quiz-nav">
          <button class="quiz-btn quiz-btn-back" id="btn-back" onclick="quizBack()" style="display:none">← Atrás</button>
          <button class="quiz-btn quiz-btn-next" id="btn-next" onclick="quizNext()">Siguiente →</button>
        </div>
      </div>

      <div class="results-panel">
        <h3>Mascotas compatibles</h3>
        <div id="results-placeholder" class="demo-placeholder">
          <span>🔮</span>
          Responde las preguntas y el algoritmo calculará tus mejores matches al instante.
        </div>
        <div id="results-list" style="display:none">
          <div class="result-card" id="rc0">
            <div class="result-icon">🐕</div>
            <div class="result-info">
              <div class="result-name">Luna</div>
              <div class="result-breed">Labrador · 2 años · Hembra</div>
              <div class="result-bar-wrap"><div class="result-bar" id="rb0"></div></div>
            </div>
            <div class="result-pct" id="rp0">—</div>
          </div>
          <div class="result-card" id="rc1">
            <div class="result-icon">🐈</div>
            <div class="result-info">
              <div class="result-name">Mochi</div>
              <div class="result-breed">Gato doméstico · 3 años · Macho</div>
              <div class="result-bar-wrap"><div class="result-bar" id="rb1"></div></div>
            </div>
            <div class="result-pct" id="rp1">—</div>
          </div>
          <div class="result-card" id="rc2">
            <div class="result-icon">🐕</div>
            <div class="result-info">
              <div class="result-name">Rocky</div>
              <div class="result-breed">Boxer · 1 año · Macho</div>
              <div class="result-bar-wrap"><div class="result-bar" id="rb2"></div></div>
            </div>
            <div class="result-pct" id="rp2">—</div>
          </div>
          <div class="result-card" id="rc3">
            <div class="result-icon">🐇</div>
            <div class="result-info">
              <div class="result-name">Nube</div>
              <div class="result-breed">Conejo · 1 año · Hembra</div>
              <div class="result-bar-wrap"><div class="result-bar" id="rb3"></div></div>
            </div>
            <div class="result-pct" id="rp3">—</div>
          </div>
          <p style="font-size:.78rem;color:rgba(255,255,255,.4);margin-top:1rem;text-align:center;">Scores calculados con similitud coseno sobre 5 dimensiones de perfil</p>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- SERVICIOS -->
<section id="servicios">
  <div class="inner">
    <div class="sec-tag">Servicios</div>
    <h2 class="sec-title reveal">Todo lo que necesitas<br>para adoptar bien</h2>
    <p class="sec-sub reveal">Una plataforma completa que atiende a adoptantes, refugios y organizaciones de rescate en cada etapa del proceso.</p>

    <div class="services-grid">
      <!-- Tarjeta grande: algoritmo IA -->
      <div class="svc-card featured reveal">
        <div>
          <span class="svc-tag">Core</span>
          <span class="svc-icon">🤖</span>
          <h3>Algoritmo de compatibilidad IA</h3>
          <p>Nuestro motor de inteligencia artificial analiza tu perfil completo y lo compara con cada mascota disponible usando similitud coseno sobre vectores multidimensionales.</p>
          <ul class="svc-detail-list">
            <li>5 dimensiones de perfil: espacio, actividad, horario, experiencia y convivencia familiar</li>
            <li>Score de compatibilidad en porcentaje con explicación detallada por factor</li>
            <li>Aprende y mejora con cada adopción exitosa reportada</li>
            <li>API disponible para integración con sistemas de refugios aliados</li>
            <li>Respuesta en menos de 200 ms gracias a microservicio FastAPI en AWS</li>
          </ul>
        </div>
        <div style="background:rgba(255,255,255,.1);border-radius:10px;padding:1.5rem;">
          <div style="font-size:.78rem;color:rgba(255,255,255,.6);margin-bottom:.85rem;">Tu perfil vs. mascotas disponibles</div>
          <div style="display:flex;flex-direction:column;gap:.65rem;">
            <div><div style="display:flex;justify-content:space-between;font-size:.8rem;color:rgba(255,255,255,.85);margin-bottom:5px;"><span>🐕 Luna</span><span>87%</span></div><div style="background:rgba(255,255,255,.15);border-radius:50px;height:5px;"><div style="background:white;width:87%;height:100%;border-radius:50px;"></div></div></div>
            <div><div style="display:flex;justify-content:space-between;font-size:.8rem;color:rgba(255,255,255,.85);margin-bottom:5px;"><span>🐈 Mochi</span><span>74%</span></div><div style="background:rgba(255,255,255,.15);border-radius:50px;height:5px;"><div style="background:rgba(255,255,255,.7);width:74%;height:100%;border-radius:50px;"></div></div></div>
            <div><div style="display:flex;justify-content:space-between;font-size:.8rem;color:rgba(255,255,255,.85);margin-bottom:5px;"><span>🐕 Rocky</span><span>61%</span></div><div style="background:rgba(255,255,255,.15);border-radius:50px;height:5px;"><div style="background:rgba(255,255,255,.5);width:61%;height:100%;border-radius:50px;"></div></div></div>
            <div><div style="display:flex;justify-content:space-between;font-size:.8rem;color:rgba(255,255,255,.85);margin-bottom:5px;"><span>🐇 Nube</span><span>55%</span></div><div style="background:rgba(255,255,255,.15);border-radius:50px;height:5px;"><div style="background:rgba(255,255,255,.4);width:55%;height:100%;border-radius:50px;"></div></div></div>
          </div>
        </div>
      </div>

      <div class="svc-card reveal">
        <span class="svc-tag">Adoptantes</span>
        <span class="svc-icon">🏠</span>
        <h3>Catálogo inteligente</h3>
        <p>Acceso en tiempo real a mascotas disponibles en refugios aliados, con filtros avanzados y ordenamiento por compatibilidad personalizada.</p>
        <ul class="svc-detail-list">
          <li>Fotos, historial médico y ficha de comportamiento por animal</li>
          <li>Filtros por especie, tamaño, edad, energía y compatibilidad</li>
          <li>Actualización automática desde los sistemas del refugio</li>
          <li>Función de favoritos y comparación lado a lado</li>
        </ul>
      </div>

      <div class="svc-card reveal">
        <span class="svc-tag">Post-adopción</span>
        <span class="svc-icon">📱</span>
        <h3>Seguimiento post-adopción</h3>
        <p>Acompañamiento continuo después de que la mascota llega a su nuevo hogar, para garantizar una adaptación exitosa.</p>
        <ul class="svc-detail-list">
          <li>Registro de bienestar semanal con indicadores de adaptación</li>
          <li>Recordatorios automáticos de vacunas y citas veterinarias</li>
          <li>Álbum de progreso compartible con el refugio de origen</li>
          <li>Alertas tempranas si el proceso de adaptación muestra señales de riesgo</li>
        </ul>
      </div>

      <div class="svc-card reveal">
        <span class="svc-tag">Refugios</span>
        <span class="svc-icon">🏥</span>
        <h3>Panel para refugios</h3>
        <p>Dashboard profesional diseñado para que los refugios gestionen sus animales, procesen solicitudes y midan su impacto social.</p>
        <ul class="svc-detail-list">
          <li>Alta masiva de animales con importación desde hojas de cálculo</li>
          <li>Gestión de solicitudes con historial y notas del adoptante</li>
          <li>Estadísticas de tasa de adopción, retorno y tiempo promedio en refugio</li>
          <li>Reportes mensuales descargables en PDF</li>
        </ul>
      </div>

      <div class="svc-card reveal">
        <span class="svc-tag">Comunidad</span>
        <span class="svc-icon">👥</span>
        <h3>Comunidad de adoptantes</h3>
        <p>Espacio social donde adoptantes comparten su experiencia, se apoyan mutuamente y acceden a contenido educativo sobre cuidado animal responsable.</p>
        <ul class="svc-detail-list">
          <li>Foro segmentado por tipo de mascota y región</li>
          <li>Biblioteca de guías de cuidado redactadas por veterinarios</li>
          <li>Directorio de veterinarias y petshops aliados con descuentos</li>
          <li>Red de padrinazgo para animales de refugio sin adoptante</li>
        </ul>
      </div>
    </div>
  </div>
</section>

<!-- COMO FUNCIONA -->
<section class="how-bg" id="como-funciona">
  <div class="inner">
    <div class="sec-tag">Proceso</div>
    <h2 class="sec-title reveal">De cero a tu nueva<br>mascota en 4 pasos</h2>
    <p class="sec-sub reveal">Un proceso diseñado para que la adopción sea segura, informada y exitosa para el adoptante y el animal.</p>

    <div class="steps-visual">
      <div class="step-item reveal">
        <div class="step-num">1</div>
        <h4>Crea tu perfil</h4>
        <p>Responde el cuestionario de compatibilidad de 5 preguntas sobre tu espacio, actividad, horario y experiencia con animales.</p>
      </div>
      <div class="step-item reveal">
        <div class="step-num">2</div>
        <h4>Explora tu match</h4>
        <p>El algoritmo calcula tu score con cada mascota y te presenta una lista priorizada de candidatos ordenados de mayor a menor afinidad.</p>
      </div>
      <div class="step-item reveal">
        <div class="step-num">3</div>
        <h4>Conecta con el refugio</h4>
        <p>Solicita más información o agenda una visita directamente desde la plataforma con el refugio responsable del animal.</p>
      </div>
      <div class="step-item reveal">
        <div class="step-num">4</div>
        <h4>Adopta y da seguimiento</h4>
        <p>Completa el proceso de adopción y usa la app para registrar el bienestar de tu mascota y compartir su progreso.</p>
      </div>
    </div>
  </div>
</section>

<!-- PRECIOS -->
<section id="precios">
  <div class="inner">
    <div class="sec-tag">Precios</div>
    <h2 class="sec-title reveal">Planes para cada necesidad</h2>
    <p class="sec-sub reveal">Comenzar a explorar es completamente gratuito. Las herramientas avanzadas están disponibles para adoptantes serios y refugios profesionales.</p>

    <div class="pricing-grid">
      <div class="plan reveal">
        <div class="plan-name">Básico</div>
        <div class="plan-price">Gratis</div>
        <p class="plan-desc">Para cualquier persona que quiera explorar la adopción responsable sin compromiso económico.</p>
        <ul class="plan-features">
          <li><span class="pf-yes">✓</span> Perfil de adoptante completo</li>
          <li><span class="pf-yes">✓</span> Catálogo de mascotas disponibles</li>
          <li><span class="pf-yes">✓</span> Compatibilidad básica (top 10)</li>
          <li><span class="pf-yes">✓</span> Contacto con refugios aliados</li>
          <li><span class="pf-no">–</span> Compatibilidad IA extendida</li>
          <li><span class="pf-no">–</span> Seguimiento post-adopción</li>
          <li><span class="pf-no">–</span> Soporte prioritario</li>
        </ul>
        <a href="#registro" class="plan-btn">Comenzar gratis</a>
      </div>

      <div class="plan highlight reveal">
        <div class="plan-badge">Más popular</div>
        <div class="plan-name">Pro Adoptante</div>
        <div class="plan-price"><sup>$</sup>149<sub>/mes MXN</sub></div>
        <p class="plan-desc">Para adoptantes que quieren la experiencia completa con todas las herramientas de IA y seguimiento personalizado.</p>
        <ul class="plan-features">
          <li><span class="pf-yes">✓</span> Todo lo del plan Básico</li>
          <li><span class="pf-yes">✓</span> Compatibilidad IA completa</li>
          <li><span class="pf-yes">✓</span> Explicación del score por factor</li>
          <li><span class="pf-yes">✓</span> Seguimiento post-adopción</li>
          <li><span class="pf-yes">✓</span> Recordatorios veterinarios</li>
          <li><span class="pf-yes">✓</span> Comunidad premium</li>
          <li><span class="pf-yes">✓</span> Soporte prioritario 24/7</li>
        </ul>
        <a href="#registro" class="plan-btn cta">Elegir Pro</a>
      </div>

      <div class="plan reveal">
        <div class="plan-name">Refugios</div>
        <div class="plan-price"><sup>$</sup>499<sub>/mes MXN</sub></div>
        <p class="plan-desc">Para organizaciones de rescate y refugios que quieren gestionar sus animales y maximizar adopciones exitosas.</p>
        <ul class="plan-features">
          <li><span class="pf-yes">✓</span> Panel de gestión de animales</li>
          <li><span class="pf-yes">✓</span> Gestión de solicitudes</li>
          <li><span class="pf-yes">✓</span> Estadísticas e impacto</li>
          <li><span class="pf-yes">✓</span> Integración vía API</li>
          <li><span class="pf-yes">✓</span> Perfiles verificados</li>
          <li><span class="pf-yes">✓</span> Reportes mensuales PDF</li>
          <li><span class="pf-yes">✓</span> Capacitación incluida</li>
        </ul>
        <a href="#registro" class="plan-btn">Contactar ventas</a>
      </div>
    </div>
  </div>
</section>

<!-- TESTIMONIOS -->
<section style="background:var(--warm);">
  <div class="inner">
    <div class="sec-tag">Testimonios</div>
    <h2 class="sec-title reveal">Lo que dicen nuestros usuarios</h2>
    <div class="testi-grid">
      <div class="testi-card reveal">
        <div class="testi-stars">★★★★★</div>
        <p class="testi-quote">"El algoritmo fue increíblemente preciso. Me mostró a Max y desde el primer momento supe que éramos perfectos el uno para el otro. Ya llevamos 8 meses juntos."</p>
        <div class="testi-author">
          <div class="testi-av" style="background:var(--sage-light);color:var(--sage);">SM</div>
          <div><div class="testi-name">Sofía Martínez</div><div class="testi-role">Adoptante en Tijuana</div></div>
        </div>
      </div>
      <div class="testi-card reveal">
        <div class="testi-stars">★★★★★</div>
        <p class="testi-quote">"Nuestra tasa de retorno bajó de 28% a menos del 4% desde que usamos PawMatch. Es una herramienta que transforma completamente cómo operamos."</p>
        <div class="testi-author">
          <div class="testi-av" style="background:var(--amber-light);color:var(--amber);">CR</div>
          <div><div class="testi-name">Carlos Reyes</div><div class="testi-role">Director, Refugio Animal Tijuana</div></div>
        </div>
      </div>
      <div class="testi-card reveal">
        <div class="testi-stars">★★★★★</div>
        <p class="testi-quote">"Vivo en un depto pequeño y tenía muchas dudas. PawMatch me explicó exactamente por qué ciertos perros eran compatibles con mi estilo de vida. Excelente."</p>
        <div class="testi-author">
          <div class="testi-av" style="background:var(--sage-light);color:var(--sage);">AL</div>
          <div><div class="testi-name">Andrea López</div><div class="testi-role">Adoptante en Ensenada</div></div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- FAQ -->
<section class="faq-section" id="faq">
  <div class="inner">
    <div class="sec-tag">Preguntas frecuentes</div>
    <h2 class="sec-title reveal">Todo lo que necesitas<br>saber antes de empezar</h2>
    <div class="faq-list reveal">
      <div class="faq-item">
        <button class="faq-q" onclick="toggleFaq(this)">¿Cómo funciona el algoritmo de compatibilidad? <span class="faq-arrow">▾</span></button>
        <div class="faq-a"><div class="faq-a-inner">El algoritmo convierte tu perfil de adoptante y el perfil de cada mascota en vectores numéricos de 5 dimensiones (espacio, actividad, horario, experiencia y convivencia familiar). Luego calcula la similitud coseno entre tu vector y el de cada animal, generando un score de 0 a 100% que representa qué tan alineados son tus necesidades y las del animal.</div></div>
      </div>
      <div class="faq-item">
        <button class="faq-q" onclick="toggleFaq(this)">¿El plan Básico es realmente gratuito? <span class="faq-arrow">▾</span></button>
        <div class="faq-a"><div class="faq-a-inner">Sí, el plan Básico es completamente gratuito sin límite de tiempo. No te pedimos tarjeta de crédito para registrarte. Incluye acceso al catálogo completo de mascotas, tu perfil de adoptante y las 10 mejores coincidencias de compatibilidad. El plan Pro añade el análisis completo, seguimiento post-adopción y soporte prioritario.</div></div>
      </div>
      <div class="faq-item">
        <button class="faq-q" onclick="toggleFaq(this)">¿Cómo puedo registrar mi refugio en la plataforma? <span class="faq-arrow">▾</span></button>
        <div class="faq-a"><div class="faq-a-inner">Los refugios pueden registrarse eligiendo el plan Refugios desde esta página. Una vez completado el registro, nuestro equipo valida la información en 48 horas y habilita el panel de gestión. El proceso incluye una sesión de capacitación gratuita de 1 hora para familiarizarse con todas las herramientas disponibles.</div></div>
      </div>
      <div class="faq-item">
        <button class="faq-q" onclick="toggleFaq(this)">¿Qué pasa si la adopción no funciona? <span class="faq-arrow">▾</span></button>
        <div class="faq-a"><div class="faq-a-inner">En PawMatch tomamos muy en serio el bienestar animal. Si la adopción presenta problemas de adaptación, nuestro equipo de seguimiento te contactará para orientarte. En casos extremos donde la devolución sea necesaria, facilitamos el proceso con el refugio de origen de forma respetuosa y sin juicios. La transparencia y el bienestar del animal son nuestra prioridad.</div></div>
      </div>
      <div class="faq-item">
        <button class="faq-q" onclick="toggleFaq(this)">¿En qué ciudades está disponible PawMatch? <span class="faq-arrow">▾</span></button>
        <div class="faq-a"><div class="faq-a-inner">Actualmente operamos en Tijuana y Ensenada, Baja California, con 50 refugios aliados. Estamos en proceso de expansión hacia Mexicali, Ciudad de México y Guadalajara durante el segundo semestre de 2025. Si eres un refugio fuera de estas ciudades, puedes registrarte y serás de los primeros en integrarse cuando lleguemos a tu zona.</div></div>
      </div>
      <div class="faq-item">
        <button class="faq-q" onclick="toggleFaq(this)">¿Mis datos están seguros en PawMatch? <span class="faq-arrow">▾</span></button>
        <div class="faq-a"><div class="faq-a-inner">Sí. Todos los datos se almacenan en servidores de Amazon Web Services con cifrado en tránsito (TLS 1.3) y en reposo (AES-256). Nunca vendemos ni compartimos tus datos personales con terceros. Solo usamos tu perfil para calcular compatibilidades dentro de la plataforma. Puedes solicitar la eliminación de tu cuenta y todos tus datos en cualquier momento.</div></div>
      </div>
    </div>
  </div>
</section>

<!-- FORMULARIO DE REGISTRO -->
<section class="register-section" id="registro">
  <div class="inner">
    <div class="register-inner">
      <div class="register-text reveal">
        <h2>Empieza hoy.<br>Es gratis.</h2>
        <p>Crea tu cuenta en menos de 2 minutos y descubre qué mascota es tu match perfecto. Sin tarjeta de crédito, sin compromisos.</p>
      </div>
      <div class="register-form reveal" id="reg-form-container">
        <div class="form-title">Crear cuenta gratuita</div>
        <form id="reg-form" onsubmit="submitForm(event)">
          <div class="form-row">
            <div class="form-group">
              <label class="form-label">Nombre</label>
              <input class="form-input" type="text" placeholder="Tu nombre" required>
            </div>
            <div class="form-group">
              <label class="form-label">Apellido</label>
              <input class="form-input" type="text" placeholder="Tu apellido" required>
            </div>
          </div>
          <div class="form-group">
            <label class="form-label">Correo electrónico</label>
            <input class="form-input" type="email" placeholder="correo@ejemplo.com" required>
          </div>
          <div class="form-group">
            <label class="form-label">Ciudad</label>
            <select class="form-select" required>
              <option value="" disabled selected>Selecciona tu ciudad</option>
              <option>Tijuana</option>
              <option>Ensenada</option>
              <option>Mexicali</option>
              <option>Otra ciudad</option>
            </select>
          </div>
          <div class="form-group">
            <label class="form-label">Me registro como</label>
            <select class="form-select" required>
              <option value="" disabled selected>Selecciona tu perfil</option>
              <option>Adoptante potencial</option>
              <option>Refugio u organización de rescate</option>
              <option>Veterinaria o petshop aliado</option>
            </select>
          </div>
          <button type="submit" class="form-submit">Crear cuenta gratis →</button>
          <p class="form-note">Al registrarte aceptas nuestros términos de uso y política de privacidad</p>
        </form>
        <div class="form-success" id="form-success">
          <span>🐾</span>
          <h3>¡Bienvenido a PawMatch!</h3>
          <p>Te enviamos un correo de confirmación. Revisa tu bandeja de entrada para activar tu cuenta.</p>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- REDES SOCIALES -->
<section style="background:var(--warm);">
  <div class="inner">
    <div class="sec-tag">Síguenos</div>
    <h2 class="sec-title reveal">Conecta con la comunidad</h2>
    <p class="sec-sub reveal">Encontranos en redes sociales para historias de adopción, consejos de cuidado y actualizaciones de la plataforma.</p>
    <div class="social-grid">
      <div class="social-card reveal"><span class="social-icon">📸</span><h4>Instagram</h4><p>@PawMatchMX · Historias y mascotas disponibles</p></div>
      <div class="social-card reveal"><span class="social-icon">📘</span><h4>Facebook</h4><p>@PawMatchMX · Comunidad y noticias</p></div>
      <div class="social-card reveal"><span class="social-icon">💼</span><h4>LinkedIn</h4><p>PawMatch · Impacto y actualizaciones</p></div>
      <div class="social-card reveal"><span class="social-icon">🐦</span><h4>Twitter / X</h4><p>@PawMatchMX · Conversaciones</p></div>
    </div>
  </div>
</section>

<!-- CTA FINAL -->
<div class="cta-final">
  <h2>Tu compañero de vida<br>está <em>esperando.</em></h2>
  <p>Más de 1,200 mascotas en refugios aliados esperan encontrar un hogar compatible. El algoritmo ya calculó quién podría ser el tuyo.</p>
  <a href="#registro" class="btn-white">Encontrar mi match ahora</a>
</div>

<!-- FOOTER -->
<footer>
  <div class="footer-logo">PawMatch</div>
  <p class="footer-tag">Adopción responsable, impulsada por inteligencia artificial · Versión 2.0</p>
  <ul class="footer-links">
    <li><a href="#servicios">Servicios</a></li>
    <li><a href="#precios">Precios</a></li>
    <li><a href="#faq">FAQ</a></li>
    <li><a href="#registro">Registro</a></li>
    <li><a href="mailto:contacto@pawmatch.mx">Contacto</a></li>
  </ul>
  <p class="footer-copy">© 2025 PawMatch · Tijuana, Baja California, México · Todos los derechos reservados</p>
</footer>

<script>
// ── CURSOR ─────────────────────────────────────────────────────────────────
const cur = document.getElementById('cur');
const ring = document.getElementById('ring');
document.addEventListener('mousemove', e => {
  cur.style.left = e.clientX + 'px';
  cur.style.top = e.clientY + 'px';
  setTimeout(() => {
    ring.style.left = e.clientX + 'px';
    ring.style.top = e.clientY + 'px';
  }, 60);
});

// ── REVEAL ON SCROLL ────────────────────────────────────────────────────────
const obs = new IntersectionObserver(entries => {
  entries.forEach(e => { if(e.isIntersecting) e.target.classList.add('in'); });
}, { threshold: 0.1 });
document.querySelectorAll('.reveal').forEach(el => obs.observe(el));

// ── QUIZ INTERACTIVO ────────────────────────────────────────────────────────
let step = 0;
const answers = {};
const steps = document.querySelectorAll('.quiz-step');
const dots = document.querySelectorAll('.qp-dot');

function updateDots() {
  dots.forEach((d, i) => {
    d.classList.remove('active', 'done');
    if(i < step) d.classList.add('done');
    if(i === step) d.classList.add('active');
  });
}

document.querySelectorAll('.quiz-opt').forEach(opt => {
  opt.addEventListener('click', () => {
    const parent = opt.closest('.quiz-step');
    parent.querySelectorAll('.quiz-opt').forEach(o => o.classList.remove('selected'));
    opt.classList.add('selected');
    answers[step] = opt.dataset.val;
    updateResults();
  });
});

function quizNext() {
  if(!answers[step]) return;
  if(step < 4) {
    steps[step].classList.remove('active');
    step++;
    steps[step].classList.add('active');
    updateDots();
    document.getElementById('btn-back').style.display = 'inline-block';
    if(step === 4) document.getElementById('btn-next').textContent = 'Ver resultados completos →';
  }
}

function quizBack() {
  if(step > 0) {
    steps[step].classList.remove('active');
    step--;
    steps[step].classList.add('active');
    updateDots();
    if(step === 0) document.getElementById('btn-back').style.display = 'none';
    document.getElementById('btn-next').textContent = 'Siguiente →';
  }
}

function updateResults() {
  // Calcular scores simulados basados en respuestas
  const space = answers[0]; const activity = answers[1];
  const time = answers[2]; const exp = answers[3]; const family = answers[4];

  let luna = 50, mochi = 50, rocky = 50, nube = 50;

  if(space === 'small') { luna -= 10; mochi += 15; rocky -= 15; nube += 10; }
  else if(space === 'large') { luna += 15; rocky += 15; mochi -= 5; nube -= 5; }

  if(activity === 'high') { luna += 15; rocky += 20; mochi -= 10; nube -= 15; }
  else if(activity === 'low') { mochi += 15; nube += 20; luna -= 10; rocky -= 20; }

  if(time === 'many') { mochi += 10; nube += 10; luna -= 10; rocky -= 15; }
  if(exp === 'none') { luna += 5; mochi += 5; rocky -= 10; }
  if(family === 'kids') { luna += 10; rocky += 5; mochi -= 5; nube -= 5; }

  // Normalizar 0-99
  const clamp = v => Math.min(99, Math.max(30, Math.round(v)));
  const scores = [clamp(luna), clamp(mochi), clamp(rocky), clamp(nube)];

  // Ordenar por score
  const pets = [
    { id: 0, score: scores[0] },
    { id: 1, score: scores[1] },
    { id: 2, score: scores[2] },
    { id: 3, score: scores[3] },
  ].sort((a, b) => b.score - a.score);

  document.getElementById('results-placeholder').style.display = 'none';
  document.getElementById('results-list').style.display = 'block';

  pets.forEach((pet, rank) => {
    const card = document.getElementById(`rc${rank}`);
    const bar = document.getElementById(`rb${rank}`);
    const pct = document.getElementById(`rp${rank}`);
    // Mover contenido al rank
    const srcCard = document.getElementById(`rc${pet.id}`);
    card.classList.remove('visible');
    setTimeout(() => {
      bar.style.width = pet.score + '%';
      pct.textContent = pet.score + '%';
      card.classList.add('visible');
    }, rank * 150);
  });
}

// ── FAQ ─────────────────────────────────────────────────────────────────────
function toggleFaq(btn) {
  const item = btn.closest('.faq-item');
  const isOpen = item.classList.contains('open');
  document.querySelectorAll('.faq-item').forEach(i => i.classList.remove('open'));
  if(!isOpen) item.classList.add('open');
}

// ── FORMULARIO ──────────────────────────────────────────────────────────────
function submitForm(e) {
  e.preventDefault();
  document.getElementById('reg-form').style.display = 'none';
  document.getElementById('form-success').style.display = 'block';
}
</script>
</body>
</html>
