<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Para Diego — Mensajes de tus amigos</title>
<meta name="description" content="Una tarjeta virtual para Diego con mensajes de sus amigos: Renzo, Demi, Andre, Yashira y Miguel." />

<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@500;600;700&family=Nunito:wght@400;600;700;800&family=Caveat:wght@500;600;700&display=swap" rel="stylesheet" />

<script src="https://cdn.tailwindcss.com"></script>
<script>
  tailwind.config = {
    theme: {
      extend: {
        colors: {
          dbg: '#1B1224',
          dpanel: '#2A1C33',
          dpanel2: '#341F3E',
          coral: '#FF7A8A',
          gold: '#FFC864',
          peri: '#8FA6FF',
          mint: '#6FE3C4',
          blush: '#FF9ECF',
          cream: '#FDF6EC',
          mutelav: '#C9B8D6',
        },
        fontFamily: {
          display: ['Fredoka', 'sans-serif'],
          body: ['Nunito', 'sans-serif'],
          hand: ['Caveat', 'cursive'],
        },
      },
    },
  };
</script>

<style>
  html{ scroll-behavior:smooth; }
  body{ background: radial-gradient(circle at 50% -10%, #3a2447 0%, #1B1224 55%); }
  ::selection{ background:rgba(255,122,138,.3); color:#FDF6EC; }

  .skip-link{ position:absolute; left:-999px; top:0; background:var(--coral,#FF7A8A); color:#1B1224; padding:.7rem 1.1rem; z-index:999; font-family:'Fredoka',sans-serif; font-weight:600; border-radius:0 0 10px 0; }
  .skip-link:focus{ left:0; }

  /* floating sparkles */
  #particles{ position:fixed; inset:0; pointer-events:none; z-index:0; overflow:hidden; }
  .spark{ position:absolute; bottom:-10px; border-radius:9999px; opacity:.55; animation: drift linear infinite; }
  @keyframes drift{
    0%{ transform: translateY(0) translateX(0) scale(1); opacity:0; }
    10%{ opacity:.6; }
    90%{ opacity:.5; }
    100%{ transform: translateY(-110vh) translateX(var(--sway,20px)) scale(.8); opacity:0; }
  }

  /* envelope */
  @keyframes envBob{ 0%,100%{ transform: translateY(0) rotate(-1deg);} 50%{ transform: translateY(-5px) rotate(1deg);} }
  .envelope{ animation: envBob 6s ease-in-out infinite; }
  @keyframes heartPop{ 0%,100%{ transform: translateY(0) scale(1); opacity:.85;} 50%{ transform: translateY(-4px) scale(1.05); opacity:1;} }
  .heart-pop{ animation: heartPop 4s ease-in-out infinite; }

  .text-glow{ text-shadow: 0 0 26px rgba(255,200,100,.35), 0 0 60px rgba(255,122,138,.18); }

  /* flip cards */
  .flip-card{ perspective:1400px; background:transparent; border:0; padding:0; width:100%; cursor:pointer; transition: transform .25s ease; }
  .flip-card:hover{ transform: translateY(-4px); }
  .flip-card-inner{ display:block; position:relative; width:100%; height:100%; transition: transform .65s cubic-bezier(.4,0,.2,1); transform-style:preserve-3d; }
  .flip-card.flipped .flip-card-inner{ transform: rotateY(180deg); }
  .flip-card-face{ position:absolute; inset:0; backface-visibility:hidden; -webkit-backface-visibility:hidden; border-radius:22px; border-width:2px; border-style:solid; display:flex; flex-direction:column; align-items:center; justify-content:center; text-align:center; padding:1.25rem; overflow-y:auto; overflow-x:hidden; }
  .flip-card-face::-webkit-scrollbar{ width:5px; }
  .flip-card-face::-webkit-scrollbar-thumb{ background:rgba(255,255,255,.25); border-radius:6px; }
  .flip-card-back{ transform: rotateY(180deg); }
  .flip-card:focus-visible{ outline:2px solid var(--cream,#FDF6EC); outline-offset:4px; border-radius:22px; }

  .reveal{ opacity:0; transform:translateY(24px); transition:opacity .7s ease, transform .7s ease; }
  .reveal.is-visible{ opacity:1; transform:translateY(0); }

  ::-webkit-scrollbar{ width:10px; }
  ::-webkit-scrollbar-track{ background:#1B1224; }
  ::-webkit-scrollbar-thumb{ background:linear-gradient(#FF7A8A,#341F3E); border-radius:6px; }

  a:focus-visible, button:focus-visible{ outline:2px solid #FDF6EC; outline-offset:3px; border-radius:4px; }

  .sr-only{ position:absolute; width:1px; height:1px; padding:0; margin:-1px; overflow:hidden; clip:rect(0,0,0,0); white-space:nowrap; border:0; }

  @media (prefers-reduced-motion: reduce){
    *{ animation-duration:.001ms !important; animation-iteration-count:1 !important; }
    html{ scroll-behavior:auto !important; }
    .reveal{ opacity:1; transform:none; }
    .flip-card-inner{ transition:none; }
  }
</style>
</head>

<body class="bg-dbg text-cream font-body antialiased min-h-screen relative">

<a href="#mensajes" class="skip-link">Saltar a los mensajes</a>
<div id="particles" aria-hidden="true"></div>

<main class="relative z-10">

  <!-- ============ HERO ============ -->
  <header class="px-6 pt-20 pb-14 text-center max-w-2xl mx-auto">
    <div class="envelope inline-block" aria-hidden="true">
      <svg width="72" height="72" viewBox="0 0 100 100" fill="none">
        <rect x="8" y="26" width="84" height="58" rx="10" fill="#2A1C33" stroke="#FFC864" stroke-width="2.5"/>
        <path d="M10 30 L50 60 L90 30" stroke="#FF7A8A" stroke-width="3" stroke-linecap="round" stroke-linejoin="round" fill="none"/>
        <text x="50" y="20" text-anchor="middle" font-size="26" class="heart-pop">💛</text>
      </svg>
    </div>

    <p class="font-display font-semibold text-gold text-xs sm:text-sm tracking-[0.3em] uppercase mt-4">Para Diego</p>
    <h1 class="font-display font-bold text-4xl sm:text-5xl md:text-6xl mt-3 text-cream text-glow leading-tight">
      Querido amigo Diego,
    </h1>
    <p class="font-hand text-2xl sm:text-3xl text-mutelav mt-4">
      tus amigos te queremos dejar estos mensajes 🤍
    </p>
    <p class="text-sm text-mutelav/80 mt-5">Toca cada tarjeta para revelar lo que te tenemos preparado</p>
  </header>

  <!-- ============ MENSAJES ============ -->
  <section id="mensajes" class="px-6 pb-24">
    <div class="max-w-4xl mx-auto flex flex-wrap justify-center gap-6">

      <!-- CARD: Renzo -->
      <button type="button" class="flip-card reveal grow-0 shrink-0 basis-full sm:basis-[calc(50%-0.75rem)] lg:basis-[calc(33.333%-1rem)] h-72 sm:h-80" style="--accent:#FF7A8A" data-friend="Renzo" aria-pressed="false">
        <span class="flip-card-inner">
          <span class="flip-card-face flip-card-front" style="border-color:#FF7A8A; background:linear-gradient(160deg, rgba(255,122,138,.16), rgba(42,28,51,.9));">
            <span class="text-3xl" aria-hidden="true">💌</span>
            <span class="font-display font-semibold text-lg mt-2 text-cream">Renzo</span>
            <span class="text-[11px] mt-2 text-mutelav">Toca para leer</span>
          </span>
          <span class="flip-card-face flip-card-back" style="border-color:#FF7A8A; background:#2A1C33;" aria-hidden="true">
            <p class="font-body text-sm sm:text-base leading-relaxed text-cream">"Lamento mucho tu pérdida. Espero que puedas recordar siempre los buenos momentos que viviste con tu mascota. Te deseo lo mejor y espero que te guste el regalito."</p>
            <span class="block mt-3 font-display text-sm text-coral">— Renzo</span>
          </span>
        </span>
      </button>

      <!-- CARD: Demi -->
      <button type="button" class="flip-card reveal grow-0 shrink-0 basis-full sm:basis-[calc(50%-0.75rem)] lg:basis-[calc(33.333%-1rem)] h-72 sm:h-80" style="--accent:#FFC864" data-friend="Demi" aria-pressed="false">
        <span class="flip-card-inner">
          <span class="flip-card-face flip-card-front" style="border-color:#FFC864; background:linear-gradient(160deg, rgba(255,200,100,.16), rgba(42,28,51,.9));">
            <span class="text-3xl" aria-hidden="true">🧡</span>
            <span class="font-display font-semibold text-lg mt-2 text-cream">Demi</span>
            <span class="text-[11px] mt-2 text-mutelav">Toca para leer</span>
          </span>
          <span class="flip-card-face flip-card-back" style="border-color:#FFC864; background:#2A1C33;" aria-hidden="true">
            <p class="font-body text-sm sm:text-base leading-relaxed text-cream">"Diego, tienes todo mi apoyo, cuidate y quiero que sepas que todos tus amigos estamos contigo en este proceso."</p>
            <span class="block mt-3 font-display text-sm text-gold">— Demi</span>
          </span>
        </span>
      </button>

      <!-- CARD: Andre -->
      <button type="button" class="flip-card reveal grow-0 shrink-0 basis-full sm:basis-[calc(50%-0.75rem)] lg:basis-[calc(33.333%-1rem)] h-72 sm:h-80" style="--accent:#8FA6FF" data-friend="Andre" aria-pressed="false">
        <span class="flip-card-inner">
          <span class="flip-card-face flip-card-front" style="border-color:#8FA6FF; background:linear-gradient(160deg, rgba(143,166,255,.16), rgba(42,28,51,.9));">
            <span class="text-3xl" aria-hidden="true">💙</span>
            <span class="font-display font-semibold text-lg mt-2 text-cream">Andre</span>
            <span class="text-[11px] mt-2 text-mutelav">Toca para leer</span>
          </span>
          <span class="flip-card-face flip-card-back" style="border-color:#8FA6FF; background:#2A1C33;" aria-hidden="true">
            <p class="font-body text-xs sm:text-sm leading-relaxed text-cream">"Hola patito, que tal? espero te guste este pequeño detalle organizado en conjunto, eres un amigo cercano y muy querido, no quiero ser entrometido ni metiche, pero realmente no puedo evitar no tratar de alegrarte aunq sea un poquito. Sé que es un proceso difícil, y si algún día necesitas ayuda, nos tienes a nosotros."</p>
            <span class="block mt-3 font-display text-sm text-peri">— Andre</span>
          </span>
        </span>
      </button>

      <!-- CARD: Yashira -->
      <button type="button" class="flip-card reveal grow-0 shrink-0 basis-full sm:basis-[calc(50%-0.75rem)] lg:basis-[calc(33.333%-1rem)] h-72 sm:h-80" style="--accent:#6FE3C4" data-friend="Yashira" aria-pressed="false">
        <span class="flip-card-inner">
          <span class="flip-card-face flip-card-front" style="border-color:#6FE3C4; background:linear-gradient(160deg, rgba(111,227,196,.16), rgba(42,28,51,.9));">
            <span class="text-3xl" aria-hidden="true">💚</span>
            <span class="font-display font-semibold text-lg mt-2 text-cream">Yashira</span>
            <span class="text-[11px] mt-2 text-mutelav">Toca para leer</span>
          </span>
          <span class="flip-card-face flip-card-back" style="border-color:#6FE3C4; background:#2A1C33;" aria-hidden="true">
            <p class="font-body text-xs sm:text-sm leading-relaxed text-cream">"Dieguito espero estés algo mejorcito, sé que no era solo una mascota, sino parte de tu familia y que debe ser muy difícil para ti. Quédate con todos los momentos bonitos que compartieron y con el cariño que siempre le diste. Te mando un abrazo enorme y sabes que estoy aquí para ti si necesitas hablar. 🤍"</p>
            <span class="block mt-3 font-display text-sm text-mint">— Yashira</span>
          </span>
        </span>
      </button>

      <!-- CARD: Miguel -->
      <button type="button" class="flip-card reveal grow-0 shrink-0 basis-full sm:basis-[calc(50%-0.75rem)] lg:basis-[calc(33.333%-1rem)] h-72 sm:h-80" style="--accent:#FF9ECF" data-friend="Miguel" aria-pressed="false">
        <span class="flip-card-inner">
          <span class="flip-card-face flip-card-front" style="border-color:#FF9ECF; background:linear-gradient(160deg, rgba(255,158,207,.16), rgba(42,28,51,.9));">
            <span class="text-3xl" aria-hidden="true">💗</span>
            <span class="font-display font-semibold text-lg mt-2 text-cream">Miguel</span>
            <span class="text-[11px] mt-2 text-mutelav">Toca para leer</span>
          </span>
          <span class="flip-card-face flip-card-back" style="border-color:#FF9ECF; background:#2A1C33;" aria-hidden="true">
            <p class="font-body text-sm sm:text-base leading-relaxed text-cream">"Cuentas conmigo para lo q necesites y que se q es difícil por lo q está pasando y q comprendo y un abrazo a la distancia."</p>
            <span class="block mt-3 font-display text-sm text-blush">— Miguel</span>
          </span>
        </span>
      </button>

    </div>

    <p id="liveMsg" class="sr-only" role="status" aria-live="polite"></p>
  </section>

  <!-- ============ CIERRE ============ -->
  <footer class="text-center pb-16 px-6">
    <p class="font-hand text-2xl text-mutelav">Con cariño, tus amigos 💛</p>
    <p class="text-[11px] font-body text-mutelav/50 mt-5 tracking-wide">Esperemos que te guste <3</p>
  </footer>

</main>

<script>
  const prefersReducedMotion = window.matchMedia('(prefers-reduced-motion: reduce)').matches;

  // ---------- Floating sparkles ----------
  if (!prefersReducedMotion) {
    const container = document.getElementById('particles');
    const colors = ['#FF7A8A', '#FFC864', '#8FA6FF', '#6FE3C4', '#FF9ECF'];
    const count = window.innerWidth < 640 ? 14 : 26;
    for (let i = 0; i < count; i++) {
      const s = document.createElement('span');
      s.className = 'spark';
      const size = 3 + Math.random() * 5;
      s.style.width = size + 'px';
      s.style.height = size + 'px';
      s.style.left = Math.random() * 100 + '%';
      s.style.background = colors[Math.floor(Math.random() * colors.length)];
      s.style.setProperty('--sway', (Math.random() * 60 - 30) + 'px');
      s.style.animationDuration = (9 + Math.random() * 10) + 's';
      s.style.animationDelay = (Math.random() * 10) + 's';
      container.appendChild(s);
    }
  }

  // ---------- Scroll reveal ----------
  const revealEls = document.querySelectorAll('.reveal');
  const revealObserver = new IntersectionObserver((entries) => {
    entries.forEach((entry, i) => {
      if (entry.isIntersecting) {
        setTimeout(() => entry.target.classList.add('is-visible'), i * 60);
        revealObserver.unobserve(entry.target);
      }
    });
  }, { threshold: 0.15 });
  revealEls.forEach(el => revealObserver.observe(el));

  // ---------- Flip cards ----------
  const liveMsg = document.getElementById('liveMsg');
  document.querySelectorAll('.flip-card').forEach(card => {
    const back = card.querySelector('.flip-card-back');
    const friend = card.dataset.friend;

    card.addEventListener('click', () => {
      const isFlipped = card.classList.toggle('flipped');
      card.setAttribute('aria-pressed', String(isFlipped));
      back.setAttribute('aria-hidden', String(!isFlipped));
      if (isFlipped) {
        const message = back.querySelector('p').textContent;
        liveMsg.textContent = `Mensaje de ${friend}: ${message}`;
      } else {
        liveMsg.textContent = '';
      }
    });
  });
</script>

</body>
</html>
