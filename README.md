<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>PawMatch — Adopción responsable de mascotas</title>
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
  --r:14px;--r-sm:8px;
}
html{scroll-behavior:smooth;}
body{font-family:'Instrument Sans',sans-serif;background:var(--cream);color:var(--ink);line-height:1.6;overflow-x:hidden;}

/* CURSOR */
*{cursor:none!important;}
.cur{position:fixed;width:10px;height:10px;background:var(--sage);border-radius:50%;pointer-events:none;z-index:9999;transform:translate(-50%,-50%);transition:width .2s,height .2s,background .2s;}
.cur-ring{position:fixed;width:34px;height:34px;border:1.5px solid var(--sage);border-radius:50%;pointer-events:none;z-index:9998;transform:translate(-50%,-50%);transition:left .07s,top .07s;}

/* NAV */
nav{position:fixed;top:0;left:0;right:0;z-index:200;height:66px;padding:0 3rem;display:flex;align-items:center;justify-content:space-between;background:rgba(250,248,242,.92);backdrop-filter:blur(18px);border-bottom:1px solid var(--border);}
.nav-logo{font-family:'Fraunces',serif;font-size:1.4rem;font-weight:600;color:var(--sage);text-decoration:none;letter-spacing:-.02em;display:flex;align-items:center;gap:.4rem;}
.nav-dot{width:7px;height:7px;background:var(--amber);border-radius:50%;}
.nav-links{display:flex;gap:2rem;list-style:none;}
.nav-links a{text-decoration:none;color:var(--muted);font-size:.83rem;font-weight:500;transition:color .2s;}
.nav-links a:hover{color:var(--sage);}
.nav-cta{background:var(--ink)!important;color:var(--white)!important;padding:.42rem 1.1rem;border-radius:50px;font-size:.8rem!important;font-weight:600!important;transition:background .2s!important;}
.nav-cta:hover{background:var(--sage)!important;}
@media(max-width:800px){.nav-links{display:none;}nav{padding:0 1.2rem;}}

/* HERO */
.hero{min-height:100vh;display:grid;grid-template-columns:1fr 1fr;padding-top:66px;}
.hero-left{padding:5.5rem 4rem 5rem 5rem;display:flex;flex-direction:column;justify-content:center;}
.hero-right{background:var(--sage);position:relative;overflow:hidden;display:flex;flex-direction:column;justify-content:center;padding:4rem 3.5rem;}
.hero-right::before{content:'';position:absolute;top:-100px;right:-100px;width:350px;height:350px;border-radius:50%;background:rgba(255,255,255,.05);}
.hero-right::after{content:'';position:absolute;bottom:-70px;left:-70px;width:240px;height:240px;border-radius:50%;background:rgba(255,255,255,.04);}
.hero-badge{display:inline-flex;align-items:center;gap:.4rem;background:var(--sage-light);color:var(--sage);font-size:.7rem;font-weight:600;letter-spacing:.1em;text-transform:uppercase;padding:.32rem .85rem;border-radius:50px;margin-bottom:1.4rem;}
.vf-tag{background:var(--amber);color:var(--white);font-size:.65rem;padding:.2rem .5rem;border-radius:50px;margin-left:.3rem;}
.hero h1{font-family:'Fraunces',serif;font-size:clamp(2.8rem,4.5vw,4.5rem);line-height:1.05;font-weight:900;letter-spacing:-.04em;margin-bottom:1.1rem;}
.hero h1 em{font-style:italic;color:var(--sage);}
.hero-desc{font-size:1rem;color:var(--muted);max-width:460px;line-height:1.8;margin-bottom:2rem;}
.hero-btns{display:flex;gap:.85rem;flex-wrap:wrap;}
.btn-dark{background:var(--ink);color:var(--white);text-decoration:none;padding:.78rem 1.7rem;border-radius:50px;font-weight:600;font-size:.88rem;transition:background .2s,transform .15s;display:inline-block;}
.btn-dark:hover{background:var(--sage);transform:translateY(-1px);}
.btn-ghost{border:1.5px solid var(--border);color:var(--ink);text-decoration:none;padding:.78rem 1.7rem;border-radius:50px;font-weight:500;font-size:.88rem;transition:border-color .2s,color .2s;display:inline-block;}
.btn-ghost:hover{border-color:var(--sage);color:var(--sage);}
.hero-card{background:rgba(255,255,255,.13);border:1px solid rgba(255,255,255,.2);border-radius:var(--r);padding:1.5rem;margin-bottom:.9rem;position:relative;z-index:1;}
.hero-card h3{font-family:'Fraunces',serif;color:var(--white);font-size:1.05rem;font-weight:600;margin-bottom:.2rem;}
.hero-card p{color:rgba(255,255,255,.65);font-size:.82rem;margin-bottom:.9rem;}
.compat-row{display:flex;justify-content:space-between;align-items:center;margin-bottom:.35rem;}
.compat-lbl{font-size:.78rem;color:rgba(255,255,255,.75);}
.compat-pct{font-family:'Fraunces',serif;font-size:.95rem;font-weight:700;color:var(--white);}
.compat-bar{background:rgba(255,255,255,.18);height:5px;border-radius:50px;overflow:hidden;}
.compat-fill{height:100%;border-radius:50px;background:var(--white);animation:grow 1.6s ease-out forwards;}
@keyframes grow{from{width:0}to{width:var(--w)}}
.hero-stats{display:grid;grid-template-columns:1fr 1fr;gap:.7rem;position:relative;z-index:1;}
.stat-c{background:rgba(255,255,255,.1);border:1px solid rgba(255,255,255,.14);border-radius:var(--r-sm);padding:.9rem 1.1rem;text-align:center;}
.stat-n{font-family:'Fraunces',serif;font-size:1.75rem;font-weight:900;color:var(--white);display:block;}
.stat-l{font-size:.7rem;color:rgba(255,255,255,.6);letter-spacing:.03em;}
@media(max-width:900px){.hero{grid-template-columns:1fr;}.hero-left{padding:3rem 1.5rem;}.hero-right{padding:3rem 1.5rem;min-height:auto;}}

/* BASE SECCIONES */
section{padding:6.5rem 2rem;}
.inner{max-width:1120px;margin:0 auto;}
.sec-tag{display:inline-flex;align-items:center;gap:.4rem;background:var(--amber-light);color:var(--amber);font-size:.7rem;font-weight:600;letter-spacing:.1em;text-transform:uppercase;padding:.32rem .85rem;border-radius:50px;margin-bottom:.8rem;}
.sec-title{font-family:'Fraunces',serif;font-size:clamp(1.9rem,3.2vw,2.85rem);font-weight:900;letter-spacing:-.03em;line-height:1.1;margin-bottom:.8rem;}
.sec-sub{font-size:.97rem;color:var(--muted);max-width:540px;line-height:1.78;margin-bottom:2.8rem;}

/* REVEAL */
.reveal{opacity:0;transform:translateY(20px);transition:opacity .6s ease,transform .6s ease;}
.reveal.in{opacity:1;transform:translateY(0);}

/* DEMO ALGORITMO */
.demo-section{background:var(--ink);}
.demo-section .sec-title{color:var(--white);}
.demo-section .sec-tag{background:rgba(255,255,255,.08);color:rgba(255,255,255,.6);}
.demo-section .sec-sub{color:rgba(255,255,255,.5);}
.demo-grid{display:grid;grid-template-columns:1fr 1fr;gap:2rem;}
.quiz-panel,.results-panel{background:rgba(255,255,255,.05);border:1px solid rgba(255,255,255,.1);border-radius:var(--r);padding:1.75rem;}
.quiz-panel h3,.results-panel h3{font-family:'Fraunces',serif;color:var(--white);font-size:1.1rem;font-weight:600;margin-bottom:1.25rem;}
.qprog{display:flex;gap:.35rem;margin-bottom:1.25rem;}
.qp-d{width:7px;height:7px;border-radius:50%;background:rgba(255,255,255,.18);transition:background .3s;}
.qp-d.done{background:var(--sage-mid);}
.qp-d.active{background:var(--white);}
.quiz-step{display:none;}
.quiz-step.active{display:block;}
.quiz-q{font-size:.88rem;color:rgba(255,255,255,.8);margin-bottom:.8rem;font-weight:500;}
.quiz-opts{display:flex;flex-direction:column;gap:.45rem;}
.qopt{background:rgba(255,255,255,.06);border:1px solid rgba(255,255,255,.11);border-radius:var(--r-sm);padding:.65rem .9rem;font-size:.83rem;color:rgba(255,255,255,.7);transition:all .2s;}
.qopt:hover,.qopt.sel{background:var(--sage);border-color:var(--sage);color:var(--white);}
.quiz-nav{display:flex;gap:.7rem;margin-top:1.1rem;}
.qbtn{padding:.5rem 1.1rem;border-radius:50px;border:none;font-family:'Instrument Sans',sans-serif;font-size:.83rem;font-weight:600;transition:all .2s;}
.qbtn-next{background:var(--sage);color:var(--white);}
.qbtn-back{background:rgba(255,255,255,.08);color:rgba(255,255,255,.65);}
.rcard{background:rgba(255,255,255,.07);border:1px solid rgba(255,255,255,.1);border-radius:var(--r-sm);padding:1rem;margin-bottom:.75rem;display:flex;align-items:center;gap:.9rem;opacity:.35;transform:translateY(6px);transition:all .5s;}
.rcard.vis{opacity:1;transform:translateY(0);}
.r-icon{font-size:1.6rem;flex-shrink:0;}
.r-info{flex:1;}
.r-name{font-family:'Fraunces',serif;color:var(--white);font-size:.95rem;font-weight:600;}
.r-breed{font-size:.74rem;color:rgba(255,255,255,.45);margin-bottom:.35rem;}
.r-bw{background:rgba(255,255,255,.14);border-radius:50px;height:4px;overflow:hidden;}
.r-bar{height:100%;background:var(--sage-mid);border-radius:50px;width:0;transition:width 1s ease-out;}
.r-pct{font-family:'Fraunces',serif;color:var(--white);font-size:.95rem;font-weight:900;flex-shrink:0;}
.demo-ph{display:flex;flex-direction:column;align-items:center;justify-content:center;height:220px;color:rgba(255,255,255,.35);font-size:.85rem;text-align:center;gap:.6rem;}
.demo-ph span{font-size:2.5rem;}
@media(max-width:900px){.demo-grid{grid-template-columns:1fr;}}

/* SERVICIOS */
.svc-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:1.15rem;}
.svc-card{background:var(--white);border:1px solid var(--border);border-radius:var(--r);padding:1.85rem;transition:box-shadow .25s,transform .25s;position:relative;overflow:hidden;}
.svc-card::before{content:'';position:absolute;top:0;left:0;right:0;height:3px;background:var(--sage);transform:scaleX(0);transform-origin:left;transition:transform .35s;}
.svc-card:hover::before{transform:scaleX(1);}
.svc-card:hover{box-shadow:0 12px 40px rgba(0,0,0,.07);transform:translateY(-2px);}
.svc-feat{background:var(--sage);grid-column:span 2;display:grid;grid-template-columns:1fr 1fr;gap:2rem;align-items:center;}
.svc-feat::before{display:none;}
.svc-tag-sm{display:inline-block;background:var(--sage-light);color:var(--sage);font-size:.68rem;font-weight:600;letter-spacing:.06em;text-transform:uppercase;padding:.22rem .55rem;border-radius:50px;margin-bottom:.65rem;}
.svc-card h3{font-family:'Fraunces',serif;font-size:1.15rem;font-weight:600;margin-bottom:.5rem;letter-spacing:-.01em;}
.svc-card p{font-size:.85rem;color:var(--muted);line-height:1.7;margin-bottom:.9rem;}
.svc-feat h3{color:var(--white);font-size:1.45rem;}
.svc-feat p{color:rgba(255,255,255,.75);}
.svc-icon{font-size:1.9rem;margin-bottom:.85rem;display:block;}
.sdl{list-style:none;display:flex;flex-direction:column;gap:.4rem;}
.sdl li{font-size:.81rem;color:var(--muted);display:flex;align-items:flex-start;gap:.45rem;}
.sdl li::before{content:"→";color:var(--sage);flex-shrink:0;font-size:.76rem;margin-top:.06rem;}
.svc-feat .sdl li{color:rgba(255,255,255,.72);}
.svc-feat .sdl li::before{color:rgba(255,255,255,.45);}
@media(max-width:900px){.svc-grid{grid-template-columns:1fr;}.svc-feat{grid-column:span 1;grid-template-columns:1fr;}}

/* GALERÍA ADOPCIONES EXITOSAS */
.gallery-section{background:var(--ink);}
.gallery-section .sec-title{color:var(--white);}
.gallery-section .sec-tag{background:rgba(255,255,255,.08);color:rgba(255,255,255,.6);}
.gallery-section .sec-sub{color:rgba(255,255,255,.5);}
.gallery-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:1.15rem;}
.gallery-card{background:rgba(255,255,255,.06);border:1px solid rgba(255,255,255,.1);border-radius:var(--r);overflow:hidden;transition:transform .3s,box-shadow .3s;}
.gallery-card:hover{transform:translateY(-4px);box-shadow:0 16px 50px rgba(0,0,0,.4);}
.gallery-photo{height:160px;display:flex;align-items:center;justify-content:center;font-size:4.5rem;position:relative;}
.gallery-badge{position:absolute;top:.75rem;right:.75rem;background:var(--sage);color:var(--white);font-size:.68rem;font-weight:700;padding:.25rem .65rem;border-radius:50px;letter-spacing:.04em;}
.gallery-body{padding:1.25rem;}
.gallery-names{display:flex;align-items:center;gap:.5rem;margin-bottom:.3rem;}
.gallery-pet{font-family:'Fraunces',serif;color:var(--white);font-size:1rem;font-weight:600;}
.gallery-adopter{font-size:.78rem;color:rgba(255,255,255,.5);}
.gallery-score{display:inline-flex;align-items:center;gap:.3rem;background:rgba(106,155,118,.25);color:var(--sage-mid);font-size:.72rem;font-weight:700;padding:.22rem .6rem;border-radius:50px;margin-bottom:.65rem;}
.gallery-quote{font-family:'Fraunces',serif;font-style:italic;font-size:.88rem;color:rgba(255,255,255,.65);line-height:1.6;font-weight:300;}
.gallery-meta{display:flex;justify-content:space-between;align-items:center;margin-top:.85rem;padding-top:.85rem;border-top:1px solid rgba(255,255,255,.08);}
.gallery-city{font-size:.74rem;color:rgba(255,255,255,.4);}
.gallery-months{font-size:.74rem;color:var(--sage-mid);font-weight:600;}
@media(max-width:900px){.gallery-grid{grid-template-columns:1fr;}}

/* COMO FUNCIONA */
.how-bg{background:var(--warm);}
.steps-row{display:grid;grid-template-columns:repeat(4,1fr);gap:0;position:relative;}
.steps-row::before{content:'';position:absolute;top:2.4rem;left:12%;right:12%;height:1px;background:linear-gradient(to right,var(--sage-mid),var(--border),var(--sage-mid));z-index:0;}
.step-it{text-align:center;padding:0 1rem;position:relative;z-index:1;}
.step-num{width:4.8rem;height:4.8rem;background:var(--white);border:2px solid var(--sage-mid);border-radius:50%;display:flex;align-items:center;justify-content:center;margin:0 auto 1.1rem;font-family:'Fraunces',serif;font-size:1.35rem;font-weight:900;color:var(--sage);box-shadow:0 4px 16px rgba(61,107,71,.12);transition:background .3s,color .3s;}
.step-it:hover .step-num{background:var(--sage);color:var(--white);}
.step-it h4{font-family:'Fraunces',serif;font-size:.97rem;font-weight:600;margin-bottom:.35rem;}
.step-it p{font-size:.8rem;color:var(--muted);line-height:1.65;}
@media(max-width:800px){.steps-row{grid-template-columns:repeat(2,1fr);gap:2rem;}.steps-row::before{display:none;}}

/* MAPA REFUGIOS */
.map-section{background:var(--sage-pale);}
.map-layout{display:grid;grid-template-columns:1fr 1.4fr;gap:2.5rem;align-items:start;}
.refugios-list{display:flex;flex-direction:column;gap:.75rem;}
.refugio-item{background:var(--white);border:1px solid var(--border);border-radius:var(--r-sm);padding:1rem 1.25rem;transition:border-color .2s,box-shadow .2s;}
.refugio-item:hover,.refugio-item.active{border-color:var(--sage);box-shadow:0 4px 16px rgba(61,107,71,.1);}
.refugio-name{font-family:'Fraunces',serif;font-size:.98rem;font-weight:600;margin-bottom:.2rem;}
.refugio-info{font-size:.78rem;color:var(--muted);display:flex;gap:1rem;}
.refugio-dot{display:inline-block;width:8px;height:8px;border-radius:50%;background:var(--sage);margin-right:.35rem;flex-shrink:0;}
.map-svg-wrap{background:var(--white);border:1px solid var(--border);border-radius:var(--r);overflow:hidden;position:relative;}
.map-svg-wrap svg{width:100%;height:auto;display:block;}
.map-pin{transition:transform .2s;}
.map-pin:hover{transform:scale(1.2);}
.map-tooltip{position:absolute;background:var(--ink);color:var(--white);font-size:.78rem;padding:.4rem .75rem;border-radius:var(--r-sm);pointer-events:none;display:none;white-space:nowrap;z-index:10;}
@media(max-width:900px){.map-layout{grid-template-columns:1fr;}}

/* PRECIOS */
.pricing-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:1.15rem;align-items:start;}
.plan{background:var(--white);border:1.5px solid var(--border);border-radius:var(--r);padding:1.85rem;position:relative;}
.plan.hl{border-color:var(--sage);box-shadow:0 0 0 4px rgba(61,107,71,.09);}
.plan-badge{position:absolute;top:-12px;left:50%;transform:translateX(-50%);background:var(--sage);color:var(--white);font-size:.68rem;font-weight:700;letter-spacing:.06em;text-transform:uppercase;padding:.28rem .95rem;border-radius:50px;white-space:nowrap;}
.plan-name{font-size:.72rem;font-weight:600;color:var(--muted);letter-spacing:.07em;text-transform:uppercase;margin-bottom:.7rem;}
.plan-price{font-family:'Fraunces',serif;font-size:2.5rem;font-weight:900;letter-spacing:-.04em;line-height:1;margin-bottom:.2rem;}
.plan-price sup{font-size:1rem;font-family:'Instrument Sans',sans-serif;font-weight:600;vertical-align:super;}
.plan-price sub{font-size:.82rem;font-family:'Instrument Sans',sans-serif;font-weight:400;color:var(--muted);}
.plan-desc{font-size:.82rem;color:var(--muted);margin-bottom:1.4rem;padding-bottom:1.4rem;border-bottom:1px solid var(--border);line-height:1.65;}
.plan-feats{list-style:none;display:flex;flex-direction:column;gap:.5rem;margin-bottom:1.65rem;}
.plan-feats li{display:flex;align-items:flex-start;gap:.45rem;font-size:.83rem;}
.pf-y{color:var(--sage);font-weight:700;flex-shrink:0;}
.pf-n{color:var(--border);flex-shrink:0;}
.plan-btn{display:block;text-align:center;text-decoration:none;padding:.72rem;border-radius:50px;font-weight:600;font-size:.85rem;transition:all .2s;border:1.5px solid var(--border);color:var(--ink);}
.plan-btn:hover{border-color:var(--sage);color:var(--sage);}
.plan-btn.cta{background:var(--sage);color:var(--white);border-color:var(--sage);}
.plan-btn.cta:hover{background:#4d8459;}
@media(max-width:900px){.pricing-grid{grid-template-columns:1fr;}}

/* TESTIMONIOS */
.testi-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:1.15rem;}
.testi-card{background:var(--white);border:1px solid var(--border);border-radius:var(--r);padding:1.65rem;}
.testi-stars{color:var(--amber);font-size:.85rem;margin-bottom:.7rem;}
.testi-q{font-family:'Fraunces',serif;font-size:.97rem;font-weight:300;font-style:italic;line-height:1.7;color:var(--ink);margin-bottom:1rem;}
.testi-auth{display:flex;align-items:center;gap:.7rem;}
.testi-av{width:36px;height:36px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-weight:700;font-size:.82rem;}
.testi-n{font-weight:600;font-size:.82rem;}
.testi-r{font-size:.72rem;color:var(--muted);}
@media(max-width:900px){.testi-grid{grid-template-columns:1fr;}}

/* FAQ */
.faq-bg{background:var(--sage-pale);}
.faq-list{max-width:780px;display:flex;flex-direction:column;gap:.7rem;}
.faq-item{background:var(--white);border:1px solid var(--border);border-radius:var(--r-sm);overflow:hidden;}
.faq-q{width:100%;background:none;border:none;padding:1.1rem 1.4rem;text-align:left;font-family:'Instrument Sans',sans-serif;font-size:.92rem;font-weight:600;color:var(--ink);display:flex;justify-content:space-between;align-items:center;gap:1rem;transition:color .2s;}
.faq-q:hover{color:var(--sage);}
.faq-arr{width:18px;height:18px;border:1.5px solid var(--border);border-radius:50%;display:flex;align-items:center;justify-content:center;flex-shrink:0;font-size:.65rem;transition:transform .3s,background .2s,border-color .2s;}
.faq-item.open .faq-arr{transform:rotate(180deg);background:var(--sage);border-color:var(--sage);color:var(--white);}
.faq-a{max-height:0;overflow:hidden;transition:max-height .4s ease;}
.faq-a-in{padding:0 1.4rem 1.15rem;font-size:.85rem;color:var(--muted);line-height:1.75;}
.faq-item.open .faq-a{max-height:280px;}

/* REGISTRO */
.reg-section{background:var(--sage);}
.reg-inner{display:grid;grid-template-columns:1fr 1fr;gap:4rem;align-items:center;}
.reg-text h2{font-family:'Fraunces',serif;font-size:clamp(1.9rem,3.2vw,3rem);font-weight:900;color:var(--white);letter-spacing:-.03em;line-height:1.1;margin-bottom:.8rem;}
.reg-text p{font-size:.97rem;color:rgba(255,255,255,.72);line-height:1.78;}
.reg-form-wrap{background:rgba(255,255,255,.1);border:1px solid rgba(255,255,255,.18);border-radius:var(--r);padding:2.1rem;}
.form-title{font-family:'Fraunces',serif;color:var(--white);font-size:1.2rem;font-weight:600;margin-bottom:1.35rem;}
.fg{margin-bottom:1rem;}
.fl{display:block;font-size:.76rem;font-weight:600;color:rgba(255,255,255,.7);letter-spacing:.04em;margin-bottom:.35rem;}
.fi,.fs{width:100%;background:rgba(255,255,255,.11);border:1px solid rgba(255,255,255,.18);border-radius:var(--r-sm);padding:.65rem .95rem;font-family:'Instrument Sans',sans-serif;font-size:.85rem;color:var(--white);outline:none;transition:border-color .2s,background .2s;}
.fi::placeholder{color:rgba(255,255,255,.38);}
.fi:focus,.fs:focus{border-color:rgba(255,255,255,.55);background:rgba(255,255,255,.17);}
.fs option{color:var(--ink);background:var(--white);}
.f-row{display:grid;grid-template-columns:1fr 1fr;gap:.8rem;}
.f-submit{width:100%;background:var(--white);color:var(--sage);border:none;border-radius:50px;padding:.82rem;font-family:'Instrument Sans',sans-serif;font-size:.88rem;font-weight:700;transition:background .2s,transform .15s;margin-top:.4rem;}
.f-submit:hover{background:var(--warm);transform:translateY(-1px);}
.f-note{font-size:.72rem;color:rgba(255,255,255,.45);text-align:center;margin-top:.7rem;}
.f-success{display:none;text-align:center;padding:2rem;color:var(--white);}
.f-success span{font-size:2.75rem;display:block;margin-bottom:.65rem;}
.f-success h3{font-family:'Fraunces',serif;font-size:1.4rem;font-weight:600;margin-bottom:.4rem;}
.f-success p{font-size:.85rem;color:rgba(255,255,255,.7);}
@media(max-width:900px){.reg-inner{grid-template-columns:1fr;}.f-row{grid-template-columns:1fr;}}

/* REDES */
.social-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:1rem;}
.social-card{background:var(--white);border:1px solid var(--border);border-radius:var(--r);padding:1.4rem;text-align:center;text-decoration:none;color:inherit;transition:box-shadow .2s,transform .2s;display:block;}
.social-card:hover{box-shadow:0 8px 28px rgba(0,0,0,.07);transform:translateY(-2px);}
.social-icon{font-size:1.85rem;margin-bottom:.65rem;display:block;}
.social-card h4{font-family:'Fraunces',serif;font-size:.95rem;font-weight:600;margin-bottom:.2rem;}
.social-card p{font-size:.75rem;color:var(--muted);}
@media(max-width:800px){.social-grid{grid-template-columns:repeat(2,1fr);}}

/* CTA FINAL */
.cta-final{background:var(--ink);text-align:center;padding:7rem 2rem;}
.cta-final h2{font-family:'Fraunces',serif;font-size:clamp(2.4rem,5vw,3.9rem);font-weight:900;color:var(--white);letter-spacing:-.04em;line-height:1.05;margin-bottom:.95rem;}
.cta-final h2 em{font-style:italic;color:var(--sage-mid);}
.cta-final p{font-size:.97rem;color:rgba(255,255,255,.5);max-width:460px;margin:0 auto 2rem;line-height:1.78;}
.btn-white{background:var(--white);color:var(--ink);text-decoration:none;padding:.88rem 2.2rem;border-radius:50px;font-weight:700;font-size:.92rem;display:inline-block;transition:transform .15s,box-shadow .15s;box-shadow:0 4px 20px rgba(0,0,0,.22);}
.btn-white:hover{transform:translateY(-2px);box-shadow:0 8px 30px rgba(0,0,0,.3);}

/* FOOTER */
footer{background:var(--ink);border-top:1px solid rgba(255,255,255,.05);padding:2.8rem 2rem;text-align:center;}
.footer-logo{font-family:'Fraunces',serif;font-size:1.4rem;color:var(--white);margin-bottom:.35rem;font-weight:600;}
.footer-tag{font-size:.76rem;color:rgba(255,255,255,.35);margin-bottom:1.75rem;}
.footer-links{display:flex;justify-content:center;gap:1.75rem;list-style:none;flex-wrap:wrap;margin-bottom:1.75rem;}
.footer-links a{color:rgba(255,255,255,.35);text-decoration:none;font-size:.76rem;transition:color .2s;}
.footer-links a:hover{color:var(--sage-mid);}
.footer-copy{font-size:.72rem;color:rgba(255,255,255,.2);}

/* ── CHATBOT ── */
.chat-bubble{position:fixed;bottom:1.75rem;right:1.75rem;z-index:500;}
.chat-toggle{width:56px;height:56px;background:var(--sage);border:none;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:1.5rem;box-shadow:0 6px 24px rgba(61,107,71,.4);transition:transform .2s,background .2s;}
.chat-toggle:hover{transform:scale(1.08);background:#4d8459;}
.chat-notif{position:absolute;top:-4px;right:-4px;width:18px;height:18px;background:var(--amber);border-radius:50%;border:2px solid var(--cream);display:flex;align-items:center;justify-content:center;font-size:.6rem;color:var(--white);font-weight:700;}
.chat-window{position:absolute;bottom:70px;right:0;width:330px;background:var(--white);border:1px solid var(--border);border-radius:var(--r);box-shadow:0 16px 60px rgba(0,0,0,.16);display:none;flex-direction:column;overflow:hidden;max-height:460px;}
.chat-window.open{display:flex;}
.chat-header{background:var(--sage);padding:1rem 1.25rem;display:flex;align-items:center;gap:.75rem;}
.chat-avatar{width:36px;height:36px;background:rgba(255,255,255,.2);border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:1.1rem;flex-shrink:0;}
.chat-header-info h4{font-family:'Fraunces',serif;color:var(--white);font-size:.95rem;font-weight:600;}
.chat-header-info p{font-size:.72rem;color:rgba(255,255,255,.7);}
.chat-close{margin-left:auto;background:none;border:none;color:rgba(255,255,255,.7);font-size:1.1rem;padding:.2rem;}
.chat-msgs{flex:1;overflow-y:auto;padding:1rem;display:flex;flex-direction:column;gap:.65rem;}
.msg{max-width:85%;padding:.65rem .9rem;border-radius:12px;font-size:.83rem;line-height:1.55;}
.msg.bot{background:var(--sage-pale);color:var(--ink);border-bottom-left-radius:4px;align-self:flex-start;}
.msg.user{background:var(--sage);color:var(--white);border-bottom-right-radius:4px;align-self:flex-end;}
.chat-suggestions{padding:.6rem 1rem;display:flex;flex-wrap:wrap;gap:.4rem;border-top:1px solid var(--border);}
.sug-btn{background:var(--sage-light);color:var(--sage);border:none;border-radius:50px;padding:.32rem .75rem;font-family:'Instrument Sans',sans-serif;font-size:.75rem;font-weight:600;transition:background .2s;}
.sug-btn:hover{background:var(--sage);color:var(--white);}
.chat-input-row{display:flex;gap:.5rem;padding:.75rem 1rem;border-top:1px solid var(--border);}
.chat-input{flex:1;background:var(--sage-pale);border:1px solid var(--border);border-radius:50px;padding:.5rem .9rem;font-family:'Instrument Sans',sans-serif;font-size:.82rem;color:var(--ink);outline:none;}
.chat-input:focus{border-color:var(--sage-mid);}
.chat-send{background:var(--sage);color:var(--white);border:none;border-radius:50px;padding:.5rem .9rem;font-size:.8rem;font-weight:600;font-family:'Instrument Sans',sans-serif;transition:background .2s;}
.chat-send:hover{background:#4d8459;}
</style>
</head>
<body>

<div class="cur" id="cur"></div>
<div class="cur-ring" id="ring"></div>

<!-- NAV -->
<nav>
  <a href="#inicio" class="nav-logo">PawMatch <span class="nav-dot"></span></a>
  <ul class="nav-links">
    <li><a href="#demo">Demo IA</a></li>
    <li><a href="#servicios">Servicios</a></li>
    <li><a href="#galeria">Éxitos</a></li>
    <li><a href="#refugios">Refugios</a></li>
    <li><a href="#precios">Precios</a></li>
    <li><a href="#registro" class="nav-cta">Registrarse</a></li>
  </ul>
</nav>

<!-- HERO -->
<div id="inicio">
<div class="hero">
  <div class="hero-left">
    <div class="hero-badge">🐾 Versión Final <span class="vf-tag">2026</span></div>
    <h1>La adopción<br>que <em>conecta</em><br>de verdad.</h1>
    <p class="hero-desc">PawMatch usa inteligencia artificial para encontrar qué mascota es compatible contigo. No más decisiones por impulso — solo conexiones que duran toda la vida.</p>
    <div class="hero-btns">
      <a href="#registro" class="btn-dark">Crear cuenta gratis</a>
      <a href="#demo" class="btn-ghost">Ver demo del algoritmo →</a>
    </div>
  </div>
  <div class="hero-right">
    <div class="hero-card">
      <h3>Luna — Labrador, 2 años</h3>
      <p>Refugio Animal Tijuana · Disponible para adopción</p>
      <div class="compat-row"><span class="compat-lbl">Compatibilidad con tu perfil</span><span class="compat-pct">87%</span></div>
      <div class="compat-bar"><div class="compat-fill" style="--w:87%"></div></div>
    </div>
    <div class="hero-stats">
      <div class="stat-c"><span class="stat-n">1,200+</span><span class="stat-l">Mascotas disponibles</span></div>
      <div class="stat-c"><span class="stat-n">340+</span><span class="stat-l">Adopciones exitosas</span></div>
      <div class="stat-c"><span class="stat-n">50+</span><span class="stat-l">Refugios aliados</span></div>
      <div class="stat-c"><span class="stat-n">94%</span><span class="stat-l">Adopciones permanentes</span></div>
    </div>
  </div>
</div>
</div>

<!-- DEMO INTERACTIVA -->
<section class="demo-section" id="demo">
  <div class="inner">
    <div class="sec-tag">Demo interactiva</div>
    <h2 class="sec-title reveal">Prueba el algoritmo<br>de compatibilidad</h2>
    <p class="sec-sub reveal">Responde 5 preguntas y el algoritmo calculará en tiempo real qué mascotas son más compatibles contigo.</p>
    <div class="demo-grid">
      <div class="quiz-panel">
        <div class="qprog" id="qprog">
          <div class="qp-d active"></div><div class="qp-d"></div><div class="qp-d"></div><div class="qp-d"></div><div class="qp-d"></div>
        </div>
        <h3>Cuéntanos sobre ti</h3>
        <div class="quiz-step active" data-step="0">
          <p class="quiz-q">¿Cuánto espacio tienes en casa?</p>
          <div class="quiz-opts">
            <div class="qopt" data-val="small">Departamento pequeño (menos de 60 m²)</div>
            <div class="qopt" data-val="medium">Departamento o casa mediana (60–100 m²)</div>
            <div class="qopt" data-val="large">Casa grande con jardín (más de 100 m²)</div>
          </div>
        </div>
        <div class="quiz-step" data-step="1">
          <p class="quiz-q">¿Qué tan activo es tu estilo de vida?</p>
          <div class="quiz-opts">
            <div class="qopt" data-val="low">Tranquilo — prefiero quedarme en casa</div>
            <div class="qopt" data-val="medium">Moderado — salgo a caminar regularmente</div>
            <div class="qopt" data-val="high">Muy activo — hago ejercicio a diario</div>
          </div>
        </div>
        <div class="quiz-step" data-step="2">
          <p class="quiz-q">¿Cuántas horas al día estás fuera de casa?</p>
          <div class="quiz-opts">
            <div class="qopt" data-val="few">Menos de 4 horas — trabajo remoto</div>
            <div class="qopt" data-val="moderate">Entre 4 y 8 horas — horario de oficina</div>
            <div class="qopt" data-val="many">Más de 8 horas — horario extendido</div>
          </div>
        </div>
        <div class="quiz-step" data-step="3">
          <p class="quiz-q">¿Tienes experiencia con mascotas?</p>
          <div class="quiz-opts">
            <div class="qopt" data-val="none">Primera vez que adopto</div>
            <div class="qopt" data-val="some">He tenido mascotas antes</div>
            <div class="qopt" data-val="expert">Tengo mucha experiencia</div>
          </div>
        </div>
        <div class="quiz-step" data-step="4">
          <p class="quiz-q">¿Hay niños o adultos mayores en tu hogar?</p>
          <div class="quiz-opts">
            <div class="qopt" data-val="kids">Sí, hay niños menores de 10 años</div>
            <div class="qopt" data-val="elderly">Sí, hay adultos mayores</div>
            <div class="qopt" data-val="adults">No, solo adultos</div>
          </div>
        </div>
        <div class="quiz-nav" id="qnav">
          <button class="qbtn qbtn-back" id="qback" onclick="qBack()" style="display:none">← Atrás</button>
          <button class="qbtn qbtn-next" id="qnext" onclick="qNext()">Siguiente →</button>
        </div>
      </div>
      <div class="results-panel">
        <h3>Mascotas compatibles</h3>
        <div class="demo-ph" id="demo-ph"><span>🔮</span>Responde las preguntas para ver tus matches.</div>
        <div id="res-list" style="display:none">
          <div class="rcard" id="rc0"><div class="r-icon">🐕</div><div class="r-info"><div class="r-name">Luna</div><div class="r-breed">Labrador · 2 años · Hembra</div><div class="r-bw"><div class="r-bar" id="rb0"></div></div></div><div class="r-pct" id="rp0">—</div></div>
          <div class="rcard" id="rc1"><div class="r-icon">🐈</div><div class="r-info"><div class="r-name">Mochi</div><div class="r-breed">Gato doméstico · 3 años · Macho</div><div class="r-bw"><div class="r-bar" id="rb1"></div></div></div><div class="r-pct" id="rp1">—</div></div>
          <div class="rcard" id="rc2"><div class="r-icon">🐕</div><div class="r-info"><div class="r-name">Rocky</div><div class="r-breed">Boxer · 1 año · Macho</div><div class="r-bw"><div class="r-bar" id="rb2"></div></div></div><div class="r-pct" id="rp2">—</div></div>
          <div class="rcard" id="rc3"><div class="r-icon">🐇</div><div class="r-info"><div class="r-name">Nube</div><div class="r-breed">Conejo · 1 año · Hembra</div><div class="r-bw"><div class="r-bar" id="rb3"></div></div></div><div class="r-pct" id="rp3">—</div></div>
          <p style="font-size:.72rem;color:rgba(255,255,255,.35);margin-top:.85rem;text-align:center;">Calculado con similitud coseno sobre 5 dimensiones</p>
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
    <p class="sec-sub reveal">Una plataforma completa para adoptantes, refugios y organizaciones de rescate.</p>
    <div class="svc-grid">
      <div class="svc-card svc-feat reveal">
        <div>
          <span class="svc-tag-sm">Core</span>
          <span class="svc-icon">🤖</span>
          <h3>Algoritmo de compatibilidad IA</h3>
          <p>Motor de matching que analiza 5 dimensiones de tu perfil usando similitud coseno para encontrar tu mascota ideal.</p>
          <ul class="sdl">
            <li>Score de compatibilidad en porcentaje con explicación por factor</li>
            <li>Aprende con cada adopción exitosa reportada</li>
            <li>API disponible para refugios aliados</li>
            <li>Respuesta en menos de 200 ms — microservicio FastAPI en AWS</li>
          </ul>
        </div>
        <div style="background:rgba(255,255,255,.1);border-radius:10px;padding:1.4rem;">
          <div style="font-size:.76rem;color:rgba(255,255,255,.55);margin-bottom:.8rem;">Tu perfil vs. mascotas disponibles</div>
          <div style="display:flex;flex-direction:column;gap:.6rem;">
            <div><div style="display:flex;justify-content:space-between;font-size:.78rem;color:rgba(255,255,255,.85);margin-bottom:4px;"><span>🐕 Luna</span><span>87%</span></div><div style="background:rgba(255,255,255,.14);border-radius:50px;height:4px;"><div style="background:white;width:87%;height:100%;border-radius:50px;"></div></div></div>
            <div><div style="display:flex;justify-content:space-between;font-size:.78rem;color:rgba(255,255,255,.85);margin-bottom:4px;"><span>🐈 Mochi</span><span>74%</span></div><div style="background:rgba(255,255,255,.14);border-radius:50px;height:4px;"><div style="background:rgba(255,255,255,.65);width:74%;height:100%;border-radius:50px;"></div></div></div>
            <div><div style="display:flex;justify-content:space-between;font-size:.78rem;color:rgba(255,255,255,.85);margin-bottom:4px;"><span>🐕 Rocky</span><span>61%</span></div><div style="background:rgba(255,255,255,.14);border-radius:50px;height:4px;"><div style="background:rgba(255,255,255,.45);width:61%;height:100%;border-radius:50px;"></div></div></div>
          </div>
        </div>
      </div>
      <div class="svc-card reveal">
        <span class="svc-tag-sm">Adoptantes</span><span class="svc-icon">🏠</span>
        <h3>Catálogo inteligente</h3>
        <p>Mascotas en tiempo real desde refugios aliados, ordenadas por compatibilidad personalizada.</p>
        <ul class="sdl"><li>Ficha médica y de comportamiento por animal</li><li>Filtros por especie, tamaño, edad y energía</li><li>Función de favoritos y comparación lado a lado</li></ul>
      </div>
      <div class="svc-card reveal">
        <span class="svc-tag-sm">Post-adopción</span><span class="svc-icon">📱</span>
        <h3>Seguimiento post-adopción</h3>
        <p>Acompañamiento continuo para garantizar una adaptación exitosa.</p>
        <ul class="sdl"><li>Registro semanal de bienestar con indicadores</li><li>Recordatorios automáticos de vacunas</li><li>Alertas tempranas si la adaptación muestra riesgo</li></ul>
      </div>
      <div class="svc-card reveal">
        <span class="svc-tag-sm">Refugios</span><span class="svc-icon">🏥</span>
        <h3>Panel para refugios</h3>
        <p>Dashboard profesional para gestión de animales y solicitudes.</p>
        <ul class="sdl"><li>Alta masiva con importación desde hojas de cálculo</li><li>Estadísticas de tasa de adopción y retorno</li><li>Reportes mensuales descargables en PDF</li></ul>
      </div>
      <div class="svc-card reveal">
        <span class="svc-tag-sm">Comunidad</span><span class="svc-icon">👥</span>
        <h3>Comunidad de adoptantes</h3>
        <p>Espacio social con guías, consejos y directorio de aliados.</p>
        <ul class="sdl"><li>Foro segmentado por tipo de mascota y región</li><li>Guías de cuidado redactadas por veterinarios</li><li>Directorio con descuentos en clínicas aliadas</li></ul>
      </div>
    </div>
  </div>
</section>

<!-- GALERÍA ADOPCIONES EXITOSAS -->
<section class="gallery-section" id="galeria">
  <div class="inner">
    <div class="sec-tag">Historias reales</div>
    <h2 class="sec-title reveal">Adopciones que cambiaron<br>dos vidas a la vez</h2>
    <p class="sec-sub reveal">Estas son algunas de las 340+ historias de adopción exitosa facilitadas por el algoritmo de PawMatch.</p>
    <div class="gallery-grid">
      <div class="gallery-card reveal">
        <div class="gallery-photo" style="background:linear-gradient(135deg,#2d5c37,#3d6b47);">🐕<span class="gallery-badge">87% match</span></div>
        <div class="gallery-body">
          <div class="gallery-names"><span class="gallery-pet">Luna</span><span class="gallery-adopter">adoptada por Sofía M.</span></div>
          <div class="gallery-score">✓ Adopción permanente · 8 meses</div>
          <p class="gallery-quote">"El algoritmo entendió mejor que yo misma qué tipo de perro necesitaba. Luna es perfecta para mi departamento y mi ritmo de vida."</p>
          <div class="gallery-meta"><span class="gallery-city">📍 Tijuana, BC</span><span class="gallery-months">8 meses juntos</span></div>
        </div>
      </div>
      <div class="gallery-card reveal">
        <div class="gallery-photo" style="background:linear-gradient(135deg,#4a3728,#6b5040);">🐈<span class="gallery-badge">92% match</span></div>
        <div class="gallery-body">
          <div class="gallery-names"><span class="gallery-pet">Mochi</span><span class="gallery-adopter">adoptado por Diego R.</span></div>
          <div class="gallery-score">✓ Adopción permanente · 11 meses</div>
          <p class="gallery-quote">"Trabajo desde casa y necesitaba compañía sin mucho ruido. Mochi es exactamente eso — silencioso, cariñoso y perfecto para espacios pequeños."</p>
          <div class="gallery-meta"><span class="gallery-city">📍 Ensenada, BC</span><span class="gallery-months">11 meses juntos</span></div>
        </div>
      </div>
      <div class="gallery-card reveal">
        <div class="gallery-photo" style="background:linear-gradient(135deg,#1a3a2a,#2d5c3f);">🐕<span class="gallery-badge">79% match</span></div>
        <div class="gallery-body">
          <div class="gallery-names"><span class="gallery-pet">Rocky</span><span class="gallery-adopter">adoptado por Ana L.</span></div>
          <div class="gallery-score">✓ Adopción permanente · 5 meses</div>
          <p class="gallery-quote">"Tengo una casa con jardín y hago ejercicio todos los días. Rocky tiene energía de sobra y ya es parte de mi rutina matutina."</p>
          <div class="gallery-meta"><span class="gallery-city">📍 Tijuana, BC</span><span class="gallery-months">5 meses juntos</span></div>
        </div>
      </div>
      <div class="gallery-card reveal">
        <div class="gallery-photo" style="background:linear-gradient(135deg,#3d2a4a,#5c3d6b);">🐇<span class="gallery-badge">88% match</span></div>
        <div class="gallery-body">
          <div class="gallery-names"><span class="gallery-pet">Nube</span><span class="gallery-adopter">adoptada por Karla V.</span></div>
          <div class="gallery-score">✓ Adopción permanente · 6 meses</div>
          <p class="gallery-quote">"Vivo en un depto sin espacio para un perro grande. PawMatch me sugirió a Nube y nunca pensé que un conejo pudiera ser tan sociable."</p>
          <div class="gallery-meta"><span class="gallery-city">📍 Mexicali, BC</span><span class="gallery-months">6 meses juntos</span></div>
        </div>
      </div>
      <div class="gallery-card reveal">
        <div class="gallery-photo" style="background:linear-gradient(135deg,#3a2a1a,#6b4a2d);">🐕<span class="gallery-badge">83% match</span></div>
        <div class="gallery-body">
          <div class="gallery-names"><span class="gallery-pet">Coco</span><span class="gallery-adopter">adoptado por familia Torres</span></div>
          <div class="gallery-score">✓ Adopción permanente · 9 meses</div>
          <p class="gallery-quote">"Tenemos dos niños de 6 y 8 años. El algoritmo priorizó razas conocidas por ser gentiles con niños. Coco es el mejor compañero de juegos que pudieron tener."</p>
          <div class="gallery-meta"><span class="gallery-city">📍 Tijuana, BC</span><span class="gallery-months">9 meses juntos</span></div>
        </div>
      </div>
      <div class="gallery-card reveal">
        <div class="gallery-photo" style="background:linear-gradient(135deg,#1a2a3a,#2d4a5c);">🐈<span class="gallery-badge">95% match</span></div>
        <div class="gallery-body">
          <div class="gallery-names"><span class="gallery-pet">Sombra</span><span class="gallery-adopter">adoptada por Marco P.</span></div>
          <div class="gallery-score">✓ Adopción permanente · 14 meses</div>
          <p class="gallery-quote">"95% de match y así se siente. Sombra y yo tenemos exactamente el mismo ritmo — tranquilos por la mañana, activos por la noche."</p>
          <div class="gallery-meta"><span class="gallery-city">📍 Ensenada, BC</span><span class="gallery-months">14 meses juntos</span></div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- COMO FUNCIONA -->
<section class="how-bg">
  <div class="inner">
    <div class="sec-tag">Proceso</div>
    <h2 class="sec-title reveal">De cero a tu nueva<br>mascota en 4 pasos</h2>
    <p class="sec-sub reveal">Un proceso diseñado para que la adopción sea segura, informada y exitosa para ambos.</p>
    <div class="steps-row">
      <div class="step-it reveal"><div class="step-num">1</div><h4>Crea tu perfil</h4><p>Responde el cuestionario de compatibilidad sobre tu espacio, actividad, horario y experiencia con animales.</p></div>
      <div class="step-it reveal"><div class="step-num">2</div><h4>Explora tu match</h4><p>El algoritmo calcula tu afinidad con cada mascota y te presenta una lista priorizada de mayor a menor compatibilidad.</p></div>
      <div class="step-it reveal"><div class="step-num">3</div><h4>Conecta con el refugio</h4><p>Solicita información o agenda una visita directamente con el refugio responsable del animal desde la plataforma.</p></div>
      <div class="step-it reveal"><div class="step-num">4</div><h4>Adopta y da seguimiento</h4><p>Completa la adopción y registra el bienestar de tu mascota con nuestra herramienta de seguimiento post-adopción.</p></div>
    </div>
  </div>
</section>

<!-- MAPA DE REFUGIOS ALIADOS -->
<section class="map-section" id="refugios">
  <div class="inner">
    <div class="sec-tag">Red de refugios</div>
    <h2 class="sec-title reveal">Refugios aliados en<br>Baja California</h2>
    <p class="sec-sub reveal">Trabajamos con 50 refugios verificados en Tijuana y Ensenada. Cada refugio integrado tiene animales disponibles en tiempo real en el catálogo.</p>
    <div class="map-layout reveal">
      <div>
        <div class="refugios-list" id="refugios-list">
          <div class="refugio-item active" onclick="highlightPin(0)">
            <div class="refugio-name"><span class="refugio-dot"></span>Refugio Animal Tijuana</div>
            <div class="refugio-info"><span>📍 Zona Río, Tijuana</span><span>🐾 48 animales</span></div>
          </div>
          <div class="refugio-item" onclick="highlightPin(1)">
            <div class="refugio-name"><span class="refugio-dot"></span>Patitas sin Hogar AC</div>
            <div class="refugio-info"><span>📍 Otay, Tijuana</span><span>🐾 31 animales</span></div>
          </div>
          <div class="refugio-item" onclick="highlightPin(2)">
            <div class="refugio-name"><span class="refugio-dot"></span>Centro de Adopción SPCA</div>
            <div class="refugio-info"><span>📍 Playas, Tijuana</span><span>🐾 27 animales</span></div>
          </div>
          <div class="refugio-item" onclick="highlightPin(3)">
            <div class="refugio-name"><span class="refugio-dot"></span>Huellitas Ensenada</div>
            <div class="refugio-info"><span>📍 Centro, Ensenada</span><span>🐾 22 animales</span></div>
          </div>
          <div class="refugio-item" onclick="highlightPin(4)">
            <div class="refugio-name"><span class="refugio-dot"></span>Rescate Baja Animal</div>
            <div class="refugio-info"><span>📍 Mesa de Otay, Tijuana</span><span>🐾 19 animales</span></div>
          </div>
          <div style="padding:.85rem 1.25rem;font-size:.8rem;color:var(--muted);border-top:1px solid var(--border);text-align:center;">
            + 45 refugios más en la red PawMatch
          </div>
        </div>
      </div>
      <div class="map-svg-wrap">
        <div class="map-tooltip" id="mtt"></div>
        <svg viewBox="0 0 500 380" xmlns="http://www.w3.org/2000/svg">
          <!-- Fondo mapa -->
          <rect width="500" height="380" fill="#f3f8f4"/>
          <!-- Cuadrícula sutil -->
          <g stroke="#ddd9cf" stroke-width="0.5">
            <line x1="0" y1="95" x2="500" y2="95"/><line x1="0" y1="190" x2="500" y2="190"/>
            <line x1="0" y1="285" x2="500" y2="285"/>
            <line x1="125" y1="0" x2="125" y2="380"/><line x1="250" y1="0" x2="250" y2="380"/>
            <line x1="375" y1="0" x2="375" y2="380"/>
          </g>
          <!-- Silueta de Baja California simplificada -->
          <path d="M60,20 L80,40 L140,80 L180,120 L200,160 L195,200 L210,240 L230,280 L240,340 L220,360 L200,340 L190,300 L170,260 L150,220 L120,180 L90,140 L60,100 L40,60 Z"
            fill="#e4efe6" stroke="#6a9b76" stroke-width="1.5" opacity="0.7"/>
          <!-- Océano Pacífico label -->
          <text x="310" y="200" font-family="'Instrument Sans',sans-serif" font-size="11" fill="#6a9b76" opacity="0.5" font-style="italic">Océano Pacífico</text>
          <!-- USA border -->
          <line x1="0" y1="55" x2="180" y2="55" stroke="#b8621a" stroke-width="1" stroke-dasharray="4,3" opacity="0.5"/>
          <text x="85" y="45" font-family="'Instrument Sans',sans-serif" font-size="9" fill="#b8621a" opacity="0.6">— Frontera EE.UU. —</text>
          <!-- Etiquetas de ciudades -->
          <text x="155" y="100" font-family="'Fraunces',serif" font-size="13" fill="#3d6b47" font-weight="600">Tijuana</text>
          <text x="170" y="310" font-family="'Fraunces',serif" font-size="11" fill="#3d6b47" font-weight="600">Ensenada</text>
          <!-- PINES de refugios -->
          <!-- Pin 0: Zona Río Tijuana -->
          <g class="map-pin" id="pin0" onclick="highlightPin(0)" onmouseenter="showTip(event,'Refugio Animal Tijuana · 48 animales')" onmouseleave="hideTip()">
            <circle cx="148" cy="118" r="12" fill="#3d6b47" opacity="0.15"/>
            <circle cx="148" cy="118" r="7" fill="#3d6b47"/>
            <circle cx="148" cy="118" r="3" fill="white"/>
          </g>
          <!-- Pin 1: Otay -->
          <g class="map-pin" id="pin1" onclick="highlightPin(1)" onmouseenter="showTip(event,'Patitas sin Hogar AC · 31 animales')" onmouseleave="hideTip()">
            <circle cx="168" cy="130" r="12" fill="#3d6b47" opacity="0.15"/>
            <circle cx="168" cy="130" r="7" fill="#3d6b47"/>
            <circle cx="168" cy="130" r="3" fill="white"/>
          </g>
          <!-- Pin 2: Playas -->
          <g class="map-pin" id="pin2" onclick="highlightPin(2)" onmouseenter="showTip(event,'Centro de Adopción SPCA · 27 animales')" onmouseleave="hideTip()">
            <circle cx="125" cy="125" r="12" fill="#3d6b47" opacity="0.15"/>
            <circle cx="125" cy="125" r="7" fill="#3d6b47"/>
            <circle cx="125" cy="125" r="3" fill="white"/>
          </g>
          <!-- Pin 3: Ensenada Centro -->
          <g class="map-pin" id="pin3" onclick="highlightPin(3)" onmouseenter="showTip(event,'Huellitas Ensenada · 22 animales')" onmouseleave="hideTip()">
            <circle cx="172" cy="300" r="12" fill="#3d6b47" opacity="0.15"/>
            <circle cx="172" cy="300" r="7" fill="#3d6b47"/>
            <circle cx="172" cy="300" r="3" fill="white"/>
          </g>
          <!-- Pin 4: Mesa Otay -->
          <g class="map-pin" id="pin4" onclick="highlightPin(4)" onmouseenter="showTip(event,'Rescate Baja Animal · 19 animales')" onmouseleave="hideTip()">
            <circle cx="185" cy="140" r="12" fill="#3d6b47" opacity="0.15"/>
            <circle cx="185" cy="140" r="7" fill="#3d6b47"/>
            <circle cx="185" cy="140" r="3" fill="white"/>
          </g>
          <!-- Leyenda -->
          <circle cx="320" cy="340" r="6" fill="#3d6b47"/>
          <text x="332" y="344" font-family="'Instrument Sans',sans-serif" font-size="10" fill="#6b6860">Refugio aliado verificado</text>
        </svg>
      </div>
    </div>
  </div>
</section>

<!-- PRECIOS -->
<section id="precios">
  <div class="inner">
    <div class="sec-tag">Precios</div>
    <h2 class="sec-title reveal">Planes para cada necesidad</h2>
    <p class="sec-sub reveal">Comenzar es completamente gratuito. Sin tarjeta de crédito.</p>
    <div class="pricing-grid">
      <div class="plan reveal">
        <div class="plan-name">Básico</div>
        <div class="plan-price">Gratis</div>
        <p class="plan-desc">Para explorar la adopción responsable sin compromiso económico.</p>
        <ul class="plan-feats">
          <li><span class="pf-y">✓</span> Perfil de adoptante completo</li>
          <li><span class="pf-y">✓</span> Catálogo de mascotas disponibles</li>
          <li><span class="pf-y">✓</span> Compatibilidad básica (top 10)</li>
          <li><span class="pf-y">✓</span> Contacto con refugios aliados</li>
          <li><span class="pf-n">–</span> Compatibilidad IA extendida</li>
          <li><span class="pf-n">–</span> Seguimiento post-adopción</li>
          <li><span class="pf-n">–</span> Soporte prioritario</li>
        </ul>
        <a href="#registro" class="plan-btn">Comenzar gratis</a>
      </div>
      <div class="plan hl reveal">
        <div class="plan-badge">Más popular</div>
        <div class="plan-name">Pro Adoptante</div>
        <div class="plan-price"><sup>$</sup>149<sub>/mes MXN</sub></div>
        <p class="plan-desc">Para adoptantes que quieren la experiencia completa con IA y seguimiento.</p>
        <ul class="plan-feats">
          <li><span class="pf-y">✓</span> Todo lo del plan Básico</li>
          <li><span class="pf-y">✓</span> Compatibilidad IA completa</li>
          <li><span class="pf-y">✓</span> Explicación del score por factor</li>
          <li><span class="pf-y">✓</span> Seguimiento post-adopción</li>
          <li><span class="pf-y">✓</span> Recordatorios veterinarios</li>
          <li><span class="pf-y">✓</span> Comunidad premium</li>
          <li><span class="pf-y">✓</span> Soporte prioritario 24/7</li>
        </ul>
        <a href="#registro" class="plan-btn cta">Elegir Pro</a>
      </div>
      <div class="plan reveal">
        <div class="plan-name">Refugios</div>
        <div class="plan-price"><sup>$</sup>499<sub>/mes MXN</sub></div>
        <p class="plan-desc">Para refugios y organizaciones de rescate que quieren maximizar adopciones.</p>
        <ul class="plan-feats">
          <li><span class="pf-y">✓</span> Panel de gestión de animales</li>
          <li><span class="pf-y">✓</span> Gestión de solicitudes</li>
          <li><span class="pf-y">✓</span> Estadísticas e impacto</li>
          <li><span class="pf-y">✓</span> Integración vía API</li>
          <li><span class="pf-y">✓</span> Perfiles verificados</li>
          <li><span class="pf-y">✓</span> Reportes mensuales PDF</li>
          <li><span class="pf-y">✓</span> Capacitación incluida</li>
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
        <p class="testi-q">"El algoritmo fue increíblemente preciso. Llevamos 8 meses juntos y no podría estar más feliz con la decisión."</p>
        <div class="testi-auth"><div class="testi-av" style="background:var(--sage-light);color:var(--sage);">SM</div><div><div class="testi-n">Sofía Martínez</div><div class="testi-r">Adoptante en Tijuana</div></div></div>
      </div>
      <div class="testi-card reveal">
        <div class="testi-stars">★★★★★</div>
        <p class="testi-q">"Nuestra tasa de retorno bajó de 28% a menos del 4%. PawMatch transformó completamente cómo operamos."</p>
        <div class="testi-auth"><div class="testi-av" style="background:var(--amber-light);color:var(--amber);">CR</div><div><div class="testi-n">Carlos Reyes</div><div class="testi-r">Director, Refugio Animal Tijuana</div></div></div>
      </div>
      <div class="testi-card reveal">
        <div class="testi-stars">★★★★★</div>
        <p class="testi-q">"Vivo en depto pequeño. PawMatch me explicó exactamente por qué ciertos animales eran compatibles con mi vida."</p>
        <div class="testi-auth"><div class="testi-av" style="background:var(--sage-light);color:var(--sage);">AL</div><div><div class="testi-n">Andrea López</div><div class="testi-r">Adoptante en Ensenada</div></div></div>
      </div>
    </div>
  </div>
</section>

<!-- FAQ -->
<section class="faq-bg" id="faq">
  <div class="inner">
    <div class="sec-tag">Preguntas frecuentes</div>
    <h2 class="sec-title reveal">Todo lo que necesitas<br>saber antes de empezar</h2>
    <div class="faq-list reveal">
      <div class="faq-item"><button class="faq-q" onclick="toggleFaq(this)">¿Cómo funciona el algoritmo de compatibilidad? <span class="faq-arr">▾</span></button><div class="faq-a"><div class="faq-a-in">El algoritmo convierte tu perfil y el de cada mascota en vectores de 5 dimensiones. Luego calcula la similitud coseno entre ambos vectores, generando un score de 0 a 100% que representa qué tan alineados son tus necesidades y las del animal.</div></div></div>
      <div class="faq-item"><button class="faq-q" onclick="toggleFaq(this)">¿El plan Básico es realmente gratuito? <span class="faq-arr">▾</span></button><div class="faq-a"><div class="faq-a-in">Sí, completamente gratuito y sin límite de tiempo. No te pedimos tarjeta de crédito. Incluye catálogo completo, perfil de adoptante y las 10 mejores coincidencias de compatibilidad.</div></div></div>
      <div class="faq-item"><button class="faq-q" onclick="toggleFaq(this)">¿Cómo puedo registrar mi refugio? <span class="faq-arr">▾</span></button><div class="faq-a"><div class="faq-a-in">Elige el plan Refugios y completa el registro. Nuestro equipo valida la información en 48 horas y habilita el panel de gestión, incluyendo una capacitación gratuita de 1 hora.</div></div></div>
      <div class="faq-item"><button class="faq-q" onclick="toggleFaq(this)">¿Qué pasa si la adopción no funciona? <span class="faq-arr">▾</span></button><div class="faq-a"><div class="faq-a-in">Nuestro equipo de seguimiento te contactará para orientarte. En casos donde la devolución sea necesaria, facilitamos el proceso con el refugio de forma respetuosa y sin juicios.</div></div></div>
      <div class="faq-item"><button class="faq-q" onclick="toggleFaq(this)">¿Mis datos están seguros? <span class="faq-arr">▾</span></button><div class="faq-a"><div class="faq-a-in">Sí. Datos en AWS con cifrado TLS 1.3 en tránsito y AES-256 en reposo. Nunca vendemos tus datos. Puedes solicitar la eliminación de tu cuenta en cualquier momento.</div></div></div>
      <div class="faq-item"><button class="faq-q" onclick="toggleFaq(this)">¿En qué ciudades está disponible PawMatch? <span class="faq-arr">▾</span></button><div class="faq-a"><div class="faq-a-in">Actualmente en Tijuana y Ensenada con 50 refugios aliados. Expansión hacia Mexicali y CDMX durante el segundo semestre de 2026.</div></div></div>
    </div>
  </div>
</section>

<!-- REGISTRO -->
<section class="reg-section" id="registro">
  <div class="inner">
    <div class="reg-inner">
      <div class="reg-text reveal">
        <h2>Empieza hoy.<br>Es gratis.</h2>
        <p>Crea tu cuenta en menos de 2 minutos y descubre qué mascota es tu match perfecto. Sin tarjeta de crédito, sin compromisos.</p>
      </div>
      <div class="reg-form-wrap reveal" id="rfwrap">
        <div class="form-title">Crear cuenta gratuita</div>
        <form id="rform" onsubmit="submitForm(event)">
          <div class="f-row">
            <div class="fg"><label class="fl">Nombre</label><input class="fi" type="text" placeholder="Tu nombre" required></div>
            <div class="fg"><label class="fl">Apellido</label><input class="fi" type="text" placeholder="Tu apellido" required></div>
          </div>
          <div class="fg"><label class="fl">Correo electrónico</label><input class="fi" type="email" placeholder="correo@ejemplo.com" required></div>
          <div class="fg"><label class="fl">Ciudad</label>
            <select class="fs" required><option value="" disabled selected>Selecciona tu ciudad</option><option>Tijuana</option><option>Ensenada</option><option>Mexicali</option><option>Otra ciudad</option></select>
          </div>
          <div class="fg"><label class="fl">Me registro como</label>
            <select class="fs" required><option value="" disabled selected>Selecciona tu perfil</option><option>Adoptante potencial</option><option>Refugio u organización de rescate</option><option>Veterinaria o petshop aliado</option></select>
          </div>
          <button type="submit" class="f-submit">Crear cuenta gratis →</button>
          <p class="f-note">Al registrarte aceptas nuestros términos de uso y política de privacidad</p>
        </form>
        <div class="f-success" id="fsuccess"><span>🐾</span><h3>¡Bienvenido a PawMatch!</h3><p>Revisa tu bandeja de entrada para activar tu cuenta.</p></div>
      </div>
    </div>
  </div>
</section>

<!-- REDES SOCIALES -->
<section style="background:var(--warm);">
  <div class="inner">
    <div class="sec-tag">Síguenos</div>
    <h2 class="sec-title reveal">Conecta con la comunidad</h2>
    <p class="sec-sub reveal">Historias de adopción, consejos de cuidado y actualizaciones de la plataforma.</p>
    <div class="social-grid">
      <div class="social-card reveal"><span class="social-icon">📸</span><h4>Instagram</h4><p>@PawMatchMX · Historias y mascotas</p></div>
      <div class="social-card reveal"><span class="social-icon">📘</span><h4>Facebook</h4><p>@PawMatchMX · Comunidad y noticias</p></div>
      <div class="social-card reveal"><span class="social-icon">💼</span><h4>LinkedIn</h4><p>PawMatch · Impacto y actualizaciones</p></div>
      <div class="social-card reveal"><span class="social-icon">🐦</span><h4>Twitter / X</h4><p>@PawMatchMX · Conversaciones</p></div>
    </div>
  </div>
</section>

<!-- CTA FINAL -->
<div class="cta-final">
  <h2>Tu compañero de vida<br>está <em>esperando.</em></h2>
  <p>Más de 1,200 mascotas en refugios aliados esperan un hogar compatible. El algoritmo ya calculó quién podría ser el tuyo.</p>
  <a href="#registro" class="btn-white">Encontrar mi match ahora</a>
</div>

<!-- FOOTER -->
<footer>
  <div class="footer-logo">PawMatch</div>
  <p class="footer-tag">Adopción responsable, impulsada por inteligencia artificial · Versión Final 2026</p>
  <ul class="footer-links">
    <li><a href="#servicios">Servicios</a></li><li><a href="#galeria">Historias</a></li>
    <li><a href="#refugios">Refugios</a></li><li><a href="#precios">Precios</a></li>
    <li><a href="#faq">FAQ</a></li><li><a href="#registro">Registro</a></li>
    <li><a href="mailto:contacto@pawmatch.mx">Contacto</a></li>
  </ul>
  <p class="footer-copy">© 2026 PawMatch · Tijuana, Baja California, México · Todos los derechos reservados</p>
</footer>

<!-- CHATBOT -->
<div class="chat-bubble" id="chatbubble">
  <div class="chat-window" id="chatwin">
    <div class="chat-header">
      <div class="chat-avatar">🐾</div>
      <div class="chat-header-info"><h4>PawBot</h4><p>Asistente de adopción · En línea</p></div>
      <button class="chat-close" onclick="toggleChat()">✕</button>
    </div>
    <div class="chat-msgs" id="chatmsgs">
      <div class="msg bot">¡Hola! Soy PawBot 🐾 ¿En qué puedo ayudarte hoy?</div>
    </div>
    <div class="chat-suggestions" id="chat-sug">
      <button class="sug-btn" onclick="sendSug('¿Cómo funciona el algoritmo?')">¿Cómo funciona el algoritmo?</button>
      <button class="sug-btn" onclick="sendSug('¿Es gratuito?')">¿Es gratuito?</button>
      <button class="sug-btn" onclick="sendSug('¿Cómo registro mi refugio?')">¿Registro de refugio?</button>
      <button class="sug-btn" onclick="sendSug('¿En qué ciudades operan?')">¿Ciudades disponibles?</button>
    </div>
    <div class="chat-input-row">
      <input class="chat-input" id="chatinput" type="text" placeholder="Escribe tu pregunta..." onkeydown="if(event.key==='Enter')sendMsg()">
      <button class="chat-send" onclick="sendMsg()">Enviar</button>
    </div>
  </div>
  <button class="chat-toggle" onclick="toggleChat()">🐾
    <span class="chat-notif" id="chatnotif">1</span>
  </button>
</div>

<script>
// ── CURSOR ──────────────────────────────────────────────────────────────────
const cur=document.getElementById('cur'),ring=document.getElementById('ring');
let mx=0,my=0,rx=0,ry=0;
document.addEventListener('mousemove',e=>{mx=e.clientX;my=e.clientY;cur.style.left=mx+'px';cur.style.top=my+'px';});
setInterval(()=>{rx+=(mx-rx)*.15;ry+=(my-ry)*.15;ring.style.left=rx+'px';ring.style.top=ry+'px';},16);

// ── REVEAL ──────────────────────────────────────────────────────────────────
const obs=new IntersectionObserver(es=>{es.forEach(e=>{if(e.isIntersecting)e.target.classList.add('in');});},{threshold:.1});
document.querySelectorAll('.reveal').forEach(el=>obs.observe(el));

// ── QUIZ ────────────────────────────────────────────────────────────────────
let qStep=0;const qAns={};
const qSteps=document.querySelectorAll('.quiz-step');
const qDots=document.querySelectorAll('.qp-d');
function updDots(){qDots.forEach((d,i)=>{d.classList.remove('active','done');if(i<qStep)d.classList.add('done');if(i===qStep)d.classList.add('active');});}
document.querySelectorAll('.qopt').forEach(o=>{o.addEventListener('click',()=>{
  o.closest('.quiz-step').querySelectorAll('.qopt').forEach(x=>x.classList.remove('sel'));
  o.classList.add('sel');qAns[qStep]=o.dataset.val;calcResults();
});});
function qNext(){if(!qAns[qStep])return;if(qStep<4){qSteps[qStep].classList.remove('active');qStep++;qSteps[qStep].classList.add('active');updDots();document.getElementById('qback').style.display='inline-block';if(qStep===4)document.getElementById('qnext').textContent='Resultados completos →';}}
function qBack(){if(qStep>0){qSteps[qStep].classList.remove('active');qStep--;qSteps[qStep].classList.add('active');updDots();if(qStep===0)document.getElementById('qback').style.display='none';document.getElementById('qnext').textContent='Siguiente →';}}
function calcResults(){
  let l=50,m=50,r=50,n=50;
  const s=qAns[0],a=qAns[1],t=qAns[2],e=qAns[3],f=qAns[4];
  if(s==='small'){l-=10;m+=15;r-=15;n+=10;}else if(s==='large'){l+=15;r+=15;m-=5;n-=5;}
  if(a==='high'){l+=15;r+=20;m-=10;n-=15;}else if(a==='low'){m+=15;n+=20;l-=10;r-=20;}
  if(t==='many'){m+=10;n+=10;l-=10;r-=15;}
  if(e==='none'){l+=5;m+=5;r-=10;}
  if(f==='kids'){l+=10;r+=5;m-=5;n-=5;}
  const cl=v=>Math.min(99,Math.max(30,Math.round(v)));
  const scores=[cl(l),cl(m),cl(r),cl(n)];
  document.getElementById('demo-ph').style.display='none';
  document.getElementById('res-list').style.display='block';
  scores.forEach((sc,i)=>{
    const card=document.getElementById('rc'+i);
    const bar=document.getElementById('rb'+i);
    const pct=document.getElementById('rp'+i);
    card.classList.remove('vis');
    setTimeout(()=>{bar.style.width=sc+'%';pct.textContent=sc+'%';card.classList.add('vis');},i*140);
  });
}

// ── FAQ ─────────────────────────────────────────────────────────────────────
function toggleFaq(btn){const it=btn.closest('.faq-item');const o=it.classList.contains('open');document.querySelectorAll('.faq-item').forEach(i=>i.classList.remove('open'));if(!o)it.classList.add('open');}

// ── FORMULARIO ───────────────────────────────────────────────────────────────
function submitForm(e){e.preventDefault();document.getElementById('rform').style.display='none';document.getElementById('fsuccess').style.display='block';}

// ── MAPA REFUGIOS ────────────────────────────────────────────────────────────
function highlightPin(idx){
  document.querySelectorAll('.refugio-item').forEach((it,i)=>{it.classList.toggle('active',i===idx);});
}
function showTip(e,txt){const t=document.getElementById('mtt');t.textContent=txt;t.style.display='block';t.style.left=(e.offsetX+10)+'px';t.style.top=(e.offsetY-30)+'px';}
function hideTip(){document.getElementById('mtt').style.display='none';}

// ── CHATBOT ─────────────────────────────────────────────────────────────────
const respuestas={
  'algoritmo':'El algoritmo convierte tu perfil en un vector de 5 dimensiones (espacio, actividad, horario, experiencia y convivencia familiar) y calcula la similitud coseno con cada mascota disponible. El resultado es un score de compatibilidad de 0 a 100% 🤖',
  'gratuito':'¡Sí! El plan Básico es completamente gratuito y sin límite de tiempo. No necesitas tarjeta de crédito para registrarte. Incluye catálogo completo y las 10 mejores coincidencias de compatibilidad 🎉',
  'refugio':'Para registrar tu refugio, elige el plan Refugios desde la sección de precios. Nuestro equipo valida la información en 48 horas y te habilita el panel de gestión con capacitación gratuita incluida 🏥',
  'ciudades':'Actualmente operamos en Tijuana y Ensenada, Baja California, con 50 refugios aliados. Estamos expandiéndonos hacia Mexicali y Ciudad de México durante el segundo semestre de 2026 📍',
  'seguridad':'Tus datos están protegidos con cifrado TLS 1.3 en tránsito y AES-256 en reposo en servidores de AWS. Nunca vendemos ni compartimos tu información con terceros 🔒',
  'precio':'Tenemos tres planes: Básico (gratis), Pro Adoptante ($149 MXN/mes) y Refugios ($499 MXN/mes). Puedes ver todos los detalles en la sección de precios de esta página 💰',
  'default':'Gracias por tu pregunta 🐾 Para información más detallada puedes revisar la sección FAQ de esta página o escribirnos a contacto@pawmatch.mx y te respondemos en menos de 24 horas.'
};
function getResp(msg){
  const m=msg.toLowerCase();
  if(m.includes('algoritmo')||m.includes('funciona')||m.includes('compatib'))return respuestas.algoritmo;
  if(m.includes('gratis')||m.includes('gratuito')||m.includes('costo')||m.includes('precio'))return respuestas.gratuito;
  if(m.includes('refugio')||m.includes('registro')||m.includes('registrar'))return respuestas.refugio;
  if(m.includes('ciudad')||m.includes('disponible')||m.includes('donde')||m.includes('tijuana'))return respuestas.ciudades;
  if(m.includes('segur')||m.includes('datos')||m.includes('privac'))return respuestas.seguridad;
  if(m.includes('plan')||m.includes('pro')||m.includes('149')||m.includes('499'))return respuestas.precio;
  return respuestas.default;
}
function addMsg(txt,type){
  const d=document.createElement('div');d.className='msg '+type;d.textContent=txt;
  document.getElementById('chatmsgs').appendChild(d);
  document.getElementById('chatmsgs').scrollTop=9999;
}
function sendMsg(){
  const inp=document.getElementById('chatinput');
  const txt=inp.value.trim();if(!txt)return;
  addMsg(txt,'user');inp.value='';
  document.getElementById('chat-sug').style.display='none';
  setTimeout(()=>addMsg(getResp(txt),'bot'),600);
}
function sendSug(txt){
  addMsg(txt,'user');
  document.getElementById('chat-sug').style.display='none';
  setTimeout(()=>addMsg(getResp(txt),'bot'),600);
}
let chatOpen=false;
function toggleChat(){
  chatOpen=!chatOpen;
  document.getElementById('chatwin').classList.toggle('open',chatOpen);
  document.getElementById('chatnotif').style.display='none';
}
</script>
</body>
</html>
