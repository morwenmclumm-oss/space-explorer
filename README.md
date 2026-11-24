<!DOCTYPE html>
<html lang="uk">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SPACE EXPLORER — Подорож Всесвітом</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Comfortaa:wght@400;500;600;700&family=Nunito:wght@400;600;700;800&display=swap" rel="stylesheet">
<style>
/* =========================
   1. ОСНОВНІ НАЛАШТУВАННЯ
========================= */
:root {
  --bg: #050612;
  --text: #f7f5ff;
  --muted: #c4c5e0;
  --purple: #b79aff;
  --blue: #8ddcff;
  --pink: #f0a7ff;
  --transition: 850ms cubic-bezier(.22,.8,.22,1);
}
* { margin: 0; padding: 0; box-sizing: border-box; }
html { scroll-behavior: smooth; }
body {
  min-height: 100vh; overflow-x: hidden; background: var(--bg); color: var(--text);
  font-family: 'Nunito', sans-serif;
}
button, a { font: inherit; } button { cursor: pointer; }

/* =========================
   2. КОСМІЧНИЙ ФОН І ЗОРІ
========================= */
.space-bg {
  position: fixed; inset: 0; z-index: -3;
  background:
    radial-gradient(ellipse at 15% 20%, rgba(74,49,139,.30), transparent 42%),
    radial-gradient(ellipse at 80% 75%, rgba(28,76,133,.25), transparent 42%),
    radial-gradient(ellipse at 55% 45%, rgba(82,33,108,.16), transparent 45%),
    linear-gradient(145deg, #040511, #080b20 50%, #050612);
}
.stars, .stars::before, .stars::after {
  position: fixed; inset: 0; pointer-events: none; z-index: -2;
  content: ''; background-repeat: repeat;
}
.stars {
  background-image: radial-gradient(1px 1px at 20px 30px, #fff 99%, transparent),
                  radial-gradient(1.5px 1.5px at 140px 110px, #c6c8ff 99%, transparent),
                  radial-gradient(1px 1px at 250px 60px, #fff 99%, transparent);
  background-size: 310px 220px; opacity: .6; animation: starDrift 100s linear infinite;
}
.stars::before {
  background-image: radial-gradient(1px 1px at 90px 150px, #fff 99%, transparent),
                  radial-gradient(2px 2px at 230px 40px, #c8aaff 99%, transparent);
  background-size: 390px 300px; opacity: .5; animation: starDrift 140s linear infinite reverse;
}
.stars::after {
  background-image: radial-gradient(1px 1px at 70px 70px, #b5eaff 99%, transparent),
                  radial-gradient(1px 1px at 280px 190px, #fff 99%, transparent);
  background-size: 480px 360px; opacity: .35; animation: twinkle 5s ease-in-out infinite alternate;
}
@keyframes starDrift { from { transform: translateY(0); } to { transform: translateY(-400px); } }
@keyframes twinkle { from { opacity: .18; } to { opacity: .65; } }

/* =========================
   3. ШАПКА ТА МЕНЮ
========================= */
header {
  position: fixed; top: 0; left: 0; width: 100%; z-index: 100;
  padding: 17px 7%; display: flex; align-items: center; justify-content: space-between;
  background: rgba(5,6,18,.60); backdrop-filter: blur(16px);
  border-bottom: 1px solid rgba(255,255,255,.08);
}
.logo { text-decoration: none; color: white; font: 700 21px 'Comfortaa', sans-serif; letter-spacing: 1px; }
.logo span { color: var(--purple); }
nav { display: flex; align-items: center; gap: 26px; }
nav button {
  color: #d3d1eb; background: transparent; border: 0; font-size: 13px;
  padding: 8px 2px; position: relative; transition: color .4s ease;
}
nav button::after {
  content: ''; position: absolute; bottom: 0; left: 50%; width: 0; height: 1px;
  background: linear-gradient(90, var(--purple), var(--blue)); transition: .4s ease; transform: translateX(-50%);
}
nav button:hover, nav button.active { color: #fff; }
nav button:hover::after, nav button.active::after { width: 100%; }
.menu-toggle { display: none; border: 0; background: transparent; color: white; font-size: 25px; }

/* =========================
   4. СТОРІНКИ І ПЛАВНА ЗМІНА
========================= */
main { min-height: 100vh; }
.page {
  display: none; min-height: 100vh; padding: 120px 8% 70px;
  opacity: 0; transform: translateY(14px);
}
.page.active { display: block; }
.page.show { animation: pageReveal 1s cubic-bezier(.2,.75,.25,1) forwards; }
@keyframes pageReveal {
  0% { opacity: 0; transform: translateY(18px); filter: blur(4px); }
  100% { opacity: 1; transform: translateY(0); filter: blur(0); }
}
.page-title { text-align: center; margin: 0 auto 18px; font: 700 clamp(30px,5vw,56px) 'Comfortaa', sans-serif; }
.page-title span { color: var(--purple); }
.page-lead { max-width: 720px; text-align: center; color: var(--muted); line-height: 1.85; margin: 0 auto 46px; }

/* =========================
   5. ГОЛОВНИЙ ЕКРАН
========================= */
.hero { min-height: calc(100vh - 40px); display: grid; grid-template-columns: 1.1fr .9fr; align-items: center; gap: 35px; padding-top: 30px; }
.hero-copy { max-width: 690px; animation: gentleIn 1.2s ease both; }
.eyebrow { color: #c4aaff; letter-spacing: 3px; font-size: 12px; text-transform: uppercase; margin-bottom: 20px; }
.hero h1 { font: 700 clamp(38px,6.6vw,78px)/1.13 'Comfortaa', sans-serif; margin-bottom: 24px; }
.hero h1 span { background: linear-gradient(95deg, #c7a7ff, #8bdcff, #f2b9ff); -webkit-background-clip: text; background-clip: text; color: transparent; }
.hero p { color: var(--muted); font-size: 16px; line-height: 1.9; max-width: 580px; margin-bottom: 30px; }
.hero-buttons { display: flex; gap: 14px; flex-wrap: wrap; }
.btn {
  border: 1px solid rgba(255,255,255,.12); border-radius: 999px; padding: 13px 25px;
  color: white; text-decoration: none; background: linear-gradient(115deg, #7856c9, #416ec7);
  box-shadow: 0 6px 28px rgba(108,75,202,.25); transition: transform .5s ease, box-shadow .5s ease, background .5s ease;
}
.btn:hover { transform: translateY(-3px); box-shadow: 0 9px 32px rgba(142,109,237,.42); }
.btn.secondary { background: rgba(255,255,255,.04); box-shadow: none; }
.btn.secondary:hover { background: rgba(255,255,255,.1); }
@keyframes gentleIn { from { opacity: 0; transform: translateY(18px); } to { opacity: 1; transform: translateY(0); } }

/* Космічна система на головній */
.space-art { width: min(43vw, 440px); aspect-ratio: 1; position: relative; margin: auto; animation: floaty 7s ease-in-out infinite; }
@keyframes floaty { 0%,100% { transform: translateY(0); } 50% { transform: translateY(-13px); } }
.sun {
  width: 100px; height: 100px; position: absolute; top: 50%; left: 50%; transform: translate(-50%,-50%); border-radius: 50%;
  background: radial-gradient(circle at 30% 30%, #fff5bd, #ffc66d 45%, #f78a3c 75%, #e45c25);
  box-shadow: 0 0 28px #ffbd6b, 0 0 70px rgba(255,162,77,.42), 0 0 125px rgba(255,130,50,.18);
}
.orbit { position: absolute; top: 50%; left: 50%; border: 1px solid rgba(188,183,255,.19); border-radius: 50%; transform: translate(-50%,-50%); }
.orbit.o1 { width: 170px; height: 170px; animation: orbitSpin 8s linear infinite; }
.orbit.o2 { width: 260px; height: 260px; animation: orbitSpin 15s linear infinite; }
.orbit.o3 { width: 360px; height: 360px; animation: orbitSpin 23s linear infinite; }
.orbit.o4 { width: 430px; height: 430px; animation: orbitSpin 30s linear infinite; }
@keyframes orbitSpin { to { transform: translate(-50%,-50%) rotate(360deg); } }
.orbit .planet { position: absolute; left: -8px; top: 50%; transform: translateY(-50%); border-radius: 50%; cursor: pointer; }
.p-mercury { width: 15px; height: 15px; background: #b8b9c5; box-shadow: 0 0 10px #b8b9c566; }
.p-venus { width: 24px; height: 24px; background: radial-gradient(circle at 30% 30%, #ffe4b1, #c77b45); }
.p-earth { width: 29px; height: 29px; background: radial-gradient(circle at 30% 30%, #b8f0ff, #3479d7 60%, #153b78); }
.p-saturn { width: 34px; height: 34px; background: radial-gradient(circle at 30% 30%, #ffe5b6, #bd9765); }
.p-saturn::after { content: ''; position: absolute; width: 53px; height: 17px; border: 3px solid #dfc18f; border-radius: 50%; left: -10px; top: 8px; transform: rotate(-25deg); }

/* =========================
   6. КАРТКИ ПЛАНЕТ / ГАЛАКТИК
========================= */
.cards { display: grid; grid-template-columns: repeat(auto-fit, minmax(220px,1fr)); gap: 22px; }
.card {
  position: relative; overflow: hidden; border: 1px solid rgba(190,180,255,.13); border-radius: 23px;
  background: linear-gradient(145deg, rgba(24,26,58,.78), rgba(10,12,31,.82));
  padding: 24px; transition: transform .55s ease, border-color .6s ease, box-shadow .7s ease;
}
.card:hover { transform: translateY(-7px); border-color: rgba(181,155,255,.42); box-shadow: 0 12px 40px rgba(84,55,160,.16); }
.planet-visual { min-height: 150px; display: grid; place-items: center; position: relative; margin-bottom: 15px; }
.planet-ball { border-radius: 50%; position: relative; cursor: pointer; transition: transform .6s ease, filter .6s ease; }
.planet-ball::after { content: ''; position: absolute; inset: -12px; border: 1px solid transparent; border-radius: 50%; transition: border-color .5s ease, box-shadow .6s ease, transform .6s ease; }
.planet-ball:hover { transform: scale(1.08); }
.planet-ball.selected { transform: scale(1.09); filter: brightness(1.22); }
.planet-ball.selected::after { border-color: var(--glow, #c5a6ff); box-shadow: 0 0 14px var(--glow, #c5a6ff), 0 0 34px var(--glow, #c5a6ff), inset 0 0 12px rgba(255,255,255,.05); animation: ringPulse 2.6s ease-in-out infinite; }
@keyframes ringPulse { 0%,100% { opacity: .65; transform: scale(.96); } 50% { opacity: 1; transform: scale(1.05); } }
.mercury { width: 65px; height: 65px; background: radial-gradient(circle at 28% 25%, #e0e0e7, #777988 70%, #4c4d5a); --glow: #bfc6d9; }
.venus { width: 85px; height: 85px; background: radial-gradient(circle at 30% 28%, #ffe3a7, #d88d52 55%, #9c542f); --glow: #ffc887; }
.earth { width: 94px; height: 94px; background: radial-gradient(circle at 28% 25%, #a7efff, #367cda 40%, #16417e 75%); --glow: #70caff; }
.mars { width: 78px; height: 78px; background: radial-gradient(circle at 30% 25%, #ffc2a2, #d45c3d 55%, #873b2a); --glow: #ff9d77; }
.jupiter { width: 120px; height: 120px; background: repeating-linear-gradient(0deg, #b77b50 0 12px, #e7c49a 12px 23px, #9d6848 23px 33px, #e2b985 33px 43px); --glow: #e8b987; }
.saturn { width: 94px; height: 94px; background: radial-gradient(circle at 30% 25%, #ffe9bd, #c7a16d 60%, #8b714d); --glow: #f3d59c; }
.saturn::before { content: ''; position: absolute; width: 150px; height: 43px; border: 8px solid rgba(219,192,149,.75); border-left-color: rgba(244,224,190,.7); border-right-color: rgba(180,151,111,.7); border-radius: 50%; top: 25px; left: -28px; transform: rotate(-20deg); }
.uranus { width: 84px; height: 84px; background: radial-gradient(circle at 30% 25%, #d4fbff, #77cbd7 60%, #478a9a); --glow: #9bf4ff; }
.neptune { width: 82px; height: 82px; background: radial-gradient(circle at 30% 25%, #91c4ff, #3155d5 60%, #172f91); --glow: #7eaaff; }
.card h3 { font: 700 20px 'Comfortaa', sans-serif; margin-bottom: 9px; }
.card p { color: var(--muted); line-height: 1.7; font-size: 14px; }
.card .fact { display: inline-block; margin-top: 14px; color: #c6adff; font-size: 12px; letter-spacing: .4px; }
.card-hint { color: #aeb2d1; font-size: 12px; text-align: center; margin-top: 25px; }

/* =========================
   7. ГАЛАКТИКИ / ДОСЛІДЖЕННЯ
========================= */
.feature-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(260px,1fr)); gap: 22px; }
.feature { padding: 27px; border-radius: 22px; border: 1px solid rgba(180,170,255,.13); background: rgba(16,18,42,.65); transition: .5s ease; }
.feature:hover { background: rgba(28,29,61,.78); transform: translateY(-5px); }
.feature .icon { font-size: 35px; margin-bottom: 15px; }
.feature h3 { font: 700 19px 'Comfortaa', sans-serif; margin-bottom: 10px; }
.feature p { color: var(--muted); line-height: 1.75; font-size: 14px; }
.cosmic-banner { margin-top: 35px; padding: 30px; border-radius: 24px; background: linear-gradient(120deg, rgba(99,67,170,.2), rgba(36,105,155,.18)); border: 1px solid rgba(190,180,255,.14); text-align: center; }
.cosmic-banner h3 { font-family: 'Comfortaa', sans-serif; margin-bottom: 10px; }
.cosmic-banner p { color: var(--muted); line-height: 1.8; }

/* =========================
   8. ПІДВАЛ / АВТОРСЬКИЙ ПІДПИС
========================= */
footer { text-align: center; padding: 32px 18px 40px; border-top: 1px solid rgba(255,255,255,.08); color: #bcb8d7; font-size: 13px; line-height: 1.8; }
footer .signature { color: #d6c5ff; font-family: 'Comfortaa', sans-serif; }
footer .thanks { color: #a8dfff; margin-top: 5px; }

/* =========================
   9. АДАПТИВНІСТЬ
========================= */
@media (max-width: 900px) {
  .hero { grid-template-columns: 1fr; text-align: center; padding-top: 55px; }
  .hero-copy { margin: auto; }
  .hero p { margin-left: auto; margin-right: auto; }
  .hero-buttons { justify-content: center; }
  .space-art { width: min(80vw, 420px); margin: 20px auto 0; }
}
@media (max-width: 680px) {
  header { padding: 14px 5%; }
  .logo { font-size: 17px; }
  .menu-toggle { display: block; }
  nav { display: none; position: absolute; top: 100%; right: 5%; left: 5%; padding: 18px; flex-direction: column; gap: 12px; border-radius: 18px; background: rgba(10,11,30,.96); border: 1px solid rgba(255,255,255,.1); }
  nav.open { display: flex; }
  nav button { font-size: 15px; }
  .page { padding: 100px 5% 55px; }
  .hero h1 { font-size: clamp(35px,11vw,58px); }
  .hero p { font-size: 15px; }
  .space-art { width: 88vw; max-width: 370px; }
  .orbit.o4 { width: 96%; height: 96%; }
  .page-title { font-size: 31px; }
  .page-lead { font-size: 14px; }
  .cards { grid-template-columns: 1fr; }
}
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after { animation-duration: .01ms !important; animation-iteration-count: 1 !important; scroll-behavior: auto !important; transition-duration: .01ms !important; }
}

/* =========================
   13. ІНТЕРАКТИВНІ ПОСИЛАННЯ
========================= */
.link-card { display:flex; flex-direction:column; min-height:100%; }
.link-card .link-tag { color:#bca8ff; font-size:11px; letter-spacing:1.4px; text-transform:uppercase; margin-bottom:10px; }
.link-card a { display:inline-flex; align-items:center; gap:8px; width:fit-content; margin-top:auto; padding-top:18px; color:#b8e8ff; text-decoration:none; font-weight:800; font-size:13px; }
.link-card a:hover { color:#fff; text-decoration:underline; text-underline-offset:4px; }
.link-card a span { transition:transform .25s ease; }
.link-card a:hover span { transform:translate(3px,-3px); }
.mission-intro { display:flex; align-items:center; gap:18px; max-width:820px; margin:0 auto 30px; padding:18px 22px; border:1px solid rgba(190,180,255,.16); border-radius:20px; background:rgba(255,255,255,.035); color:var(--muted); line-height:1.75; }
.mission-intro strong { color:#fff; }
.mission-intro .spark { font-size:30px; flex:0 0 auto; }
.hello-wrap { min-height:65vh; display:grid; place-items:center; text-align:center; }
.hello-card { width:min(100%,700px); padding:35px 25px 42px; border:1px solid rgba(190,180,255,.17); border-radius:30px; background:linear-gradient(145deg,rgba(28,27,65,.72),rgba(10,12,31,.76)); box-shadow:0 20px 80px rgba(0,0,0,.2); }
.hello-card h2 { font:700 clamp(30px,5vw,48px) 'Comfortaa',sans-serif; margin-bottom:12px; }
.hello-card h2 span { color:var(--purple); }
.hello-card p { max-width:480px; margin:0 auto; color:var(--muted); line-height:1.8; }
.mascot { display:block; width:min(100%,300px); height:auto; margin:0 auto 18px; overflow:visible; }
.mascot-wave { transform-box:fill-box; transform-origin:20% 85%; animation: waveHello 1.7s ease-in-out infinite; }
.mascot-head { transform-box:fill-box; transform-origin:50% 70%; animation: headTilt 3.4s ease-in-out infinite; }
@keyframes waveHello { 0%,100%{transform:rotate(0)} 15%,35%{transform:rotate(17deg)} 25%,45%{transform:rotate(-5deg)} 55%{transform:rotate(12deg)} }
@keyframes headTilt { 0%,100%{transform:rotate(-5deg)} 50%{transform:rotate(3deg)} }
@media (max-width:680px) { .mission-intro { align-items:flex-start; } .hello-card { padding:28px 18px 34px; } }

</style>
</head>
<body>
<div class="space-bg"></div>
<div class="stars"></div>

<header>
  <a class="logo" href="#" onclick="showPage('home'); return false;">SPACE <span>EXPLORER</span></a>
  <button class="menu-toggle" aria-label="Відкрити меню" onclick="toggleMenu()">☰</button>
  <nav id="navigation">
    <button class="active" data-page="home" onclick="showPage('home')">Головна</button>
    <button data-page="planets" onclick="showPage('planets')">Планети</button>
    <button data-page="galaxies" onclick="showPage('galaxies')">Галактики</button>
    <button data-page="exploration" onclick="showPage('exploration')">Дослідження</button>
    <button data-page="missions" onclick="showPage('missions')">Місії та відкриття</button>
    <button data-page="hello" onclick="showPage('hello')">Привіт ✦</button>
  </nav>
</header>

<main>
  <!-- ГОЛОВНА -->
  <section class="page active show" id="home">
    <div class="hero">
      <div class="hero-copy">
        <div class="eyebrow">Нескінченність поруч</div>
        <h1>Відкрий<br><span>таємниці Всесвіту</span></h1>
        <p>Космос — це безмежний простір, де народжуються зорі, рухаються планети та ховаються дивовижні галактики. Запрошую у маленьку подорож найзагадковішими куточками Всесвіту.</p>
        <div class="hero-buttons">
          <button class="btn" onclick="showPage('planets')">Дослідити космос ✦</button>
          <button class="btn secondary" onclick="showPage('galaxies')">Побачити галактики</button>
        </div>
      </div>
      <div class="space-art" aria-label="Анімована модель планет">
        <div class="sun"></div>
        <div class="orbit o1"><div class="planet p-mercury" title="Меркурій"></div></div>
        <div class="orbit o2"><div class="planet p-venus" title="Венера"></div></div>
        <div class="orbit o3"><div class="planet p-earth" title="Земля"></div></div>
        <div class="orbit o4"><div class="planet p-saturn" title="Сатурн"></div></div>
      </div>
    </div>
  </section>


  <!-- ПЛАНЕТИ -->
  <section class="page" id="planets">
    <h2 class="page-title">Планети <span>Сонячної системи</span></h2>
    <p class="page-lead">Вісім планет обертаються навколо Сонця. Кожна має власний характер, кольори та загадки. Натисни на планету, щоб побачити її сяйво.</p>
    <div class="cards">
      <article class="card"><div class="planet-visual"><div class="planet-ball mercury" onclick="glowPlanet(this)" title="Натисни, щоб підсвітити"></div></div><h3>Меркурій</h3><p>Найменша планета Сонячної системи та найближча до Сонця. Його поверхня вкрита численними кратерами.</p><span class="fact">☀ Найближчий до Сонця</span></article>
      <article class="card"><div class="planet-visual"><div class="planet-ball venus" onclick="glowPlanet(this)" title="Натисни, щоб підсвітити"></div></div><h3>Венера</h3><p>Яскрава планета з густою атмосферою. Її часто називають ранковою або вечірньою зорею.</p><span class="fact">☁ Дуже щільна атмосфера</span></article>
      <article class="card"><div class="planet-visual"><div class="planet-ball earth" onclick="glowPlanet(this)" title="Натисни, щоб підсвітити"></div></div><h3>Земля</h3><p>Наш дім — планета океанів, материків, атмосфери та відомого нам життя.</p><span class="fact">🌱 Єдина відома планета з життям</span></article>
      <article class="card"><div class="planet-visual"><div class="planet-ball mars" onclick="glowPlanet(this)" title="Натисни, щоб підсвітити"></div></div><h3>Марс</h3><p>Червона планета, поверхня якої має пустелі, вулкани, долини та сліди давньої води.</p><span class="fact">🔴 Червоний відтінок поверхні</span></article>
      <article class="card"><div class="planet-visual"><div class="planet-ball jupiter" onclick="glowPlanet(this)" title="Натисни, щоб підсвітити"></div></div><h3>Юпітер</h3><p>Найбільша планета системи. Це газовий гігант із потужними атмосферними вихорами.</p><span class="fact">🌪 Найбільша планета</span></article>
      <article class="card"><div class="planet-visual"><div class="planet-ball saturn" onclick="glowPlanet(this)" title="Натисни, щоб підсвітити"></div></div><h3>Сатурн</h3><p>Відомий своїми широкими кільцями, які складаються переважно з частинок льоду та каміння.</p><span class="fact">💫 Система яскравих кілець</span></article>
      <article class="card"><div class="planet-visual"><div class="planet-ball uranus" onclick="glowPlanet(this)" title="Натисни, щоб підсвітити"></div></div><h3>Уран</h3><p>Крижаний гігант із блакитно-зеленим кольором. Він обертається майже лежачи на боці.</p><span class="fact">🌀 Незвичайний нахил осі</span></article>
      <article class="card"><div class="planet-visual"><div class="planet-ball neptune" onclick="glowPlanet(this)" title="Натисни, щоб підсвітити"></div></div><h3>Нептун</h3><p>Далекий крижаний гігант із насиченим синім кольором та дуже сильними вітрами.</p><span class="fact">🔵 Найдальша планета від Сонця</span></article>
    </div>
    <p class="card-hint">✦ Натискай на планети, щоб увімкнути або вимкнути їхнє світлове обрамлення ✦</p>
  </section>


  <!-- ГАЛАКТИКИ -->
  <section class="page" id="galaxies">
    <h2 class="page-title">Мільярди <span>галактик</span></h2>
    <p class="page-lead">Галактики — величезні системи із зірок, газу, космічного пилу та темної матерії. Вони бувають різних форм і розмірів.</p>
    <div class="feature-grid">
      <article class="feature"><div class="icon">🌌</div><h3>Чумацький Шлях</h3><p>Галактика, у якій розташована наша Сонячна система. Вона має спіральну структуру та містить сотні мільярдів зірок.</p></article>
      <article class="feature"><div class="icon">🌀</div><h3>Галактика Андромеди</h3><p>Велика спіральна галактика — один із найближчих до Чумацького Шляху великих галактичних сусідів.</p></article>
      <article class="feature"><div class="icon">✨</div><h3>Галактики-супутники</h3><p>Невеликі галактики, які гравітаційно пов'язані з більшими. Вони допомагають вченим вивчати розвиток космосу.</p></article>
    </div>
    <div class="cosmic-banner"><h3>Всесвіт набагато більший, ніж ми можемо уявити</h3><p>Кожна далека точка світла може бути цілим світом із мільярдами зірок.</p></div>
  </section>


  <!-- ДОСЛІДЖЕННЯ -->
  <section class="page" id="exploration">
    <h2 class="page-title">Досліджуючи <span>невідоме</span></h2>
    <p class="page-lead">Людство відкриває космос завдяки сміливим ідеям, науковим знанням та технологіям. Кожна місія наближає нас до нових відкриттів.</p>
    <div class="feature-grid">
      <article class="feature"><div class="icon">👩‍🚀</div><h3>Космонавти</h3><p>Люди, які вирушають за межі Землі, проводять наукові експерименти та досліджують умови космосу.</p></article>
      <article class="feature"><div class="icon">🛰️</div><h3>Супутники</h3><p>Штучні супутники допомагають спостерігати за Землею, прогнозувати погоду, передавати інформацію та вивчати Всесвіт.</p></article>
      <article class="feature"><div class="icon">🔭</div><h3>Телескопи</h3><p>Наземні та космічні телескопи збирають світло від далеких об'єктів, даючи можливість досліджувати зорі та галактики.</p></article>
      <article class="feature"><div class="icon">🚀</div><h3>Космічні апарати</h3><p>Роботизовані станції, зонди та марсоходи досліджують планети, астероїди й інші небесні тіла.</p></article>
    </div>
    <div class="cosmic-banner"><h3>Майбутнє починається з цікавості</h3><p>Можливо, саме наступне покоління дослідників відкриє найбільші таємниці Всесвіту.</p></div>
  </section>

  <!-- МІСІЇ ТА ВІДКРИТТЯ -->
  <section class="page" id="missions">
    <h2 class="page-title">Люди, місії та <span>відкриття</span></h2>
    <p class="page-lead">Космос стає ближчим завдяки людям, телескопам і роботизованим апаратам. Обери тему та перейди на сторінку NASA, щоб дізнатися більше.</p>
    <div class="mission-intro"><div class="spark">✦</div><div><strong>Маленька космічна підказка:</strong> картки нижче — це не просто описи. Кожна веде до офіційного матеріалу, де можна побачити фотографії, відео та справжні результати досліджень.</div></div>
    <div class="feature-grid">
      <article class="feature link-card">
        <div class="icon">👩‍🚀</div><div class="link-tag">Люди в космосі</div>
        <h3>Астронавти</h3>
        <p>Хто такі астронавти, як вони готуються до польотів і чим займаються на орбіті: від наукових експериментів до роботи на МКС.</p>
        <a href="https://www.nasa.gov/humans-in-space/" target="_blank" rel="noopener noreferrer">Дізнатися про астронавтів <span>↗</span></a>
      </article>
      <article class="feature link-card">
        <div class="icon">🛰️</div><div class="link-tag">Орбітальна лабораторія</div>
        <h3>Міжнародна космічна станція</h3>
        <p>МКС — велика наукова лабораторія на орбіті, де міжнародні екіпажі досліджують, як космічне середовище впливає на людей і технології.</p>
        <a href="https://www.nasa.gov/international-space-station/" target="_blank" rel="noopener noreferrer">Побачити МКС <span>↗</span></a>
      </article>
      <article class="feature link-card">
        <div class="icon">🌕</div><div class="link-tag">Польоти до Місяця</div>
        <h3>Програма Artemis</h3>
        <p>Програма NASA, мета якої — повернути людей до дослідження Місяця та підготувати нові можливості для майбутніх польотів.</p>
        <a href="https://www.nasa.gov/humans-in-space/artemis/" target="_blank" rel="noopener noreferrer">Відкрити Artemis <span>↗</span></a>
      </article>
      <article class="feature link-card">
        <div class="icon">🔴</div><div class="link-tag">Дослідження Марса</div>
        <h3>Марсохід Perseverance</h3>
        <p>Роботизований дослідник вивчає геологію Марса, шукає ознаки давнього життя та збирає зразки порід для майбутніх місій.</p>
        <a href="https://science.nasa.gov/mission/mars-2020-perseverance/" target="_blank" rel="noopener noreferrer">Стежити за місією <span>↗</span></a>
      </article>
      <article class="feature link-card">
        <div class="icon">🔭</div><div class="link-tag">Погляд у глибини космосу</div>
        <h3>Телескоп James Webb</h3>
        <p>Космічний телескоп спостерігає Всесвіт в інфрачервоному діапазоні та допомагає досліджувати ранні галактики й атмосфери екзопланет.</p>
        <a href="https://science.nasa.gov/mission/webb/" target="_blank" rel="noopener noreferrer">Дивитися знімки Webb <span>↗</span></a>
      </article>
      <article class="feature link-card">
        <div class="icon">🌌</div><div class="link-tag">Космічна класика</div>
        <h3>Телескоп Hubble</h3>
        <p>Hubble десятиліттями надсилає зображення галактик, туманностей і зоряних скупчень, змінюючи наше уявлення про Всесвіт.</p>
        <a href="https://science.nasa.gov/mission/hubble/" target="_blank" rel="noopener noreferrer">Дослідити Hubble <span>↗</span></a>
      </article>
      <article class="feature link-card">
        <div class="icon">🚀</div><div class="link-tag">На межі Сонячної системи</div>
        <h3>Voyager 1 і 2</h3>
        <p>Два апарати Voyager вирушили в подорож у 1977 році. Вони дослідили зовнішні планети й тепер рухаються крізь міжзоряний простір.</p>
        <a href="https://science.nasa.gov/mission/voyager/" target="_blank" rel="noopener noreferrer">Простежити шлях Voyager <span>↗</span></a>
      </article>
      <article class="feature link-card">
        <div class="icon">🪐</div><div class="link-tag">Планети зблизька</div>
        <h3>Сонячна система NASA</h3>
        <p>Добірка матеріалів про планети, карликові планети, супутники, астероїди та комети — з фактами й дивовижними світлинами.</p>
        <a href="https://science.nasa.gov/solar-system/" target="_blank" rel="noopener noreferrer">Мандрувати Сонячною системою <span>↗</span></a>
      </article>
    </div>
    <div class="cosmic-banner"><h3>Кожне відкриття починається з питання</h3><p>А найкраще в космосі те, що відповідей стає більше — і нових запитань теж.</p></div>
  </section>

  <!-- ФІНАЛЬНА СТОРІНКА -->
  <section class="page" id="hello">
    <div class="hello-wrap">
      <div class="hello-card">
        <svg class="mascot" viewBox="0 0 300 300" role="img" aria-label="Маленька стилізована людина з кучерявим коричневим волоссям усміхається та махає рукою">
          <defs>
            <linearGradient id="shirt" x1="0" y1="0" x2="1" y2="1"><stop offset="0" stop-color="#b7a5ef"/><stop offset="1" stop-color="#7465b5"/></linearGradient>
          </defs>
          <!-- тіло, намальоване простими формами -->
          <path d="M112 191 Q150 169 188 191 L211 268 L88 268 Z" fill="url(#shirt)" stroke="#d5c8ff" stroke-width="2"/>
          <path d="M126 190 L150 222 L174 190" fill="none" stroke="#e9ddff" stroke-width="5" stroke-linecap="round"/>
          <path d="M111 205 L76 244" stroke="#d9b08d" stroke-width="13" stroke-linecap="round"/>
          <path d="M188 205 L222 235" stroke="#d9b08d" stroke-width="13" stroke-linecap="round"/>
          <circle cx="75" cy="245" r="9" fill="#d9b08d"/>
          <!-- рука, що махає -->
          <g class="mascot-wave">
            <path d="M219 235 Q235 213 239 185" fill="none" stroke="#d9b08d" stroke-width="13" stroke-linecap="round"/>
            <path d="M239 188 Q230 174 230 160 M239 188 Q242 169 248 157 M239 188 Q254 174 261 168 M239 188 Q263 186 270 181" fill="none" stroke="#d9b08d" stroke-width="8" stroke-linecap="round"/>
            <circle cx="239" cy="188" r="10" fill="#d9b08d"/>
          </g>
          <!-- голова і кучері -->
          <g class="mascot-head">
            <circle cx="150" cy="112" r="62" fill="#d9b08d"/>
            <g fill="#65412f">
              <circle cx="99" cy="78" r="19"/><circle cx="112" cy="55" r="18"/><circle cx="133" cy="47" r="19"/>
              <circle cx="155" cy="46" r="18"/><circle cx="177" cy="55" r="20"/><circle cx="194" cy="75" r="19"/>
              <circle cx="204" cy="96" r="16"/><circle cx="96" cy="103" r="15"/><circle cx="116" cy="85" r="17"/>
              <circle cx="139" cy="67" r="16"/><circle cx="164" cy="68" r="17"/><circle cx="185" cy="88" r="16"/>
            </g>
            <path d="M124 119 Q130 113 136 119 M164 119 Q170 113 176 119" fill="none" stroke="#4b3027" stroke-width="4" stroke-linecap="round"/>
            <path d="M141 139 Q151 151 164 137" fill="none" stroke="#9b5146" stroke-width="4" stroke-linecap="round"/>
            <circle cx="120" cy="132" r="6" fill="#e9a08d" opacity=".65"/><circle cx="181" cy="132" r="6" fill="#e9a08d" opacity=".65"/>
          </g>
          <circle cx="48" cy="90" r="4" fill="#bda7ff"/><circle cx="253" cy="75" r="5" fill="#8ddcff"/>
          <path d="M40 125 l7 7 m0 -7 l-7 7 M254 117 l8 8 m0 -8 l-8 8" stroke="#c9b6ff" stroke-width="2" stroke-linecap="round"/>
        </svg>
        <h2>До нових <span>відкриттів!</span></h2>
        <p>Дякую, що завітали у мою маленьку космічну подорож. Нехай цікавість завжди веде до нових світів ✦</p>
        <div style="margin-top:26px"><button class="btn" onclick="showPage('home')">На початок подорожі ↗</button></div>
      </div>
    </div>
  </section>

</main>

<footer>
  <div class="signature">Зробила Біліченко Анастасія.</div>
  <div class="thanks">Дякую, що завітали. ✦</div>
  <div>SPACE EXPLORER · Подорож Всесвітом</div>
</footer>

<script>
/* =========================
   10. ПЕРЕМИКАННЯ РОЗДІЛІВ
========================= */
function showPage(pageId) {
  const pages = document.querySelectorAll('.page');
  pages.forEach(page => {
    page.classList.remove('active', 'show');
  });
  const selected = document.getElementById(pageId);
  if (!selected) return;
  selected.classList.add('active');
  // Перезапуск анімації появи, щоб перехід спрацьовував щоразу
  requestAnimationFrame(() => selected.classList.add('show'));

  document.querySelectorAll('nav button').forEach(button => {
    button.classList.toggle('active', button.dataset.page === pageId);
  });
  document.getElementById('navigation').classList.remove('open');
  window.scrollTo({ top: 0, behavior: 'smooth' });
}


/* =========================
   11. ПІДСВІЧУВАННЯ ПЛАНЕТ ПРИ НАТИСКАННІ
========================= */
function glowPlanet(planet) {
  planet.classList.toggle('selected');
}


/* =========================
   12. МОБІЛЬНЕ МЕНЮ
========================= */
function toggleMenu() {
  document.getElementById('navigation').classList.toggle('open');
}
</script>
</body>
</html>
