<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="Una sorpresa de primavera para Jani, hecha con amor por Rey.">
  <meta property="og:title" content="Una sorpresa de primavera">
  <meta property="og:description" content="Feliz segunda primavera juntos, Jani.">
  <meta property="og:type" content="website">
  <meta name="twitter:card" content="summary_large_image">
  <title>Una sorpresa de primavera — Para Jani</title>
  <style>
    :root {
      --cream: #fff9df;
      --cream-deep: #f6ecc9;
      --sun: #f1ca63;
      --gold: #d9a936;
      --sunset: #dda26d;
      --leaf: #889666;
      --olive: #5f6848;
      --wood: #69513b;
      --wood-dark: #3f372d;
      --ink: #514638;
      --paper: #f8edcf;
      --shadow: rgba(89, 66, 39, .2);
      --serif: Georgia, "Times New Roman", serif;
      --sans: "Trebuchet MS", "Segoe UI", sans-serif;
      --script: "Segoe Script", "Bradley Hand", "Snell Roundhand", cursive;
    }

    * { box-sizing: border-box; }
    html { scroll-behavior: smooth; }
    body {
      margin: 0;
      color: var(--ink);
      background: var(--cream);
      font-family: var(--sans);
      overflow-x: hidden;
    }

    .scene {
      position: relative;
      height: 100svh;
      min-height: 650px;
      overflow: hidden;
      isolation: isolate;
      background:
        radial-gradient(circle at 67% 58%, rgba(255, 244, 177, .98) 0 4%, rgba(242, 192, 91, .38) 12%, transparent 29%),
        linear-gradient(180deg, #f8edbb 0%, #f5dd9c 35%, #e4c286 65%, #9c9b68 100%);
      transition: filter 1.8s ease;
    }
    .scene::after {
      content: "";
      position: absolute;
      inset: 0;
      z-index: 20;
      pointer-events: none;
      background: linear-gradient(90deg, rgba(111, 92, 55, .12), transparent 36%, rgba(255,255,255,.07));
      box-shadow: inset 0 0 120px rgba(105, 74, 37, .13);
      animation: lightBreath 9s ease-in-out infinite;
    }
    body.letter-near .scene { filter: sepia(.08) saturate(1.04) brightness(1.03); }

    .sky-haze {
      position: absolute;
      inset: 0;
      z-index: 0;
      background:
        radial-gradient(ellipse at 50% 48%, transparent 10%, rgba(255,250,220,.16) 50%, transparent 72%),
        linear-gradient(180deg, rgba(255,255,255,.38), transparent 45%);
    }
    .sun {
      position: absolute;
      left: 66%;
      top: 55%;
      width: clamp(52px, 7vw, 92px);
      aspect-ratio: 1;
      transform: translate(-50%, -50%);
      border-radius: 50%;
      z-index: 1;
      background: rgba(255, 242, 175, .96);
      box-shadow: 0 0 35px 18px rgba(248, 214, 127, .45), 0 0 120px 60px rgba(242, 181, 91, .22);
      animation: sunPulse 8s ease-in-out infinite;
    }
    .horizon-back, .horizon-front {
      position: absolute;
      left: -5%; right: -5%;
      border-radius: 50% 50% 0 0 / 100% 100% 0 0;
    }
    .horizon-back {
      height: 25%; bottom: 22%; z-index: 2;
      background: rgba(117, 126, 82, .33);
      filter: blur(2px);
      clip-path: polygon(0 47%, 8% 41%, 15% 49%, 25% 33%, 38% 48%, 51% 24%, 63% 44%, 74% 27%, 85% 46%, 100% 34%, 100% 100%, 0 100%);
    }
    .horizon-front {
      height: 32%; bottom: -6%; z-index: 4;
      background: linear-gradient(180deg, rgba(139, 139, 80, .73), #77764e 58%, #626043 100%);
      clip-path: polygon(0 22%, 10% 16%, 20% 24%, 31% 12%, 45% 25%, 58% 16%, 72% 28%, 83% 13%, 100% 24%, 100% 100%, 0 100%);
    }

    .title-wrap {
      position: absolute;
      z-index: 30;
      top: clamp(60px, 10vh, 105px);
      left: 50%;
      width: min(92%, 820px);
      transform: translateX(-50%);
      text-align: center;
      color: var(--wood-dark);
      text-shadow: 0 2px 20px rgba(255, 250, 220, .75);
      opacity: 0;
      animation: titleReveal 2.8s .7s ease forwards;
    }
    .title-wrap .eyebrow {
      display: block;
      margin-bottom: 16px;
      font: 500 11px/1 var(--sans);
      letter-spacing: .3em;
      text-transform: uppercase;
      color: var(--olive);
    }
    h1 {
      margin: 0;
      font: 400 clamp(2.7rem, 6.7vw, 6rem)/.96 var(--serif);
      letter-spacing: 0;
    }
    .subtitle {
      margin: 18px 0 0;
      font: italic 400 clamp(1rem, 2vw, 1.35rem)/1.5 var(--serif);
      color: #6c6049;
    }
    .title-flower {
      display: inline-block;
      margin-top: 22px;
      width: 54px;
      height: 1px;
      background: var(--gold);
      position: relative;
      opacity: .7;
    }
    .title-flower::before {
      content: "✦";
      position: absolute;
      left: 50%; top: 50%;
      padding: 0 8px;
      transform: translate(-50%, -50%);
      background: rgba(246, 226, 166, .75);
      color: var(--gold);
      font-size: 12px;
    }

    .tree {
      position: absolute;
      left: -2%;
      bottom: 12%;
      width: min(47vw, 620px);
      height: min(78vh, 760px);
      z-index: 9;
      transform-origin: 20% 100%;
      filter: drop-shadow(0 18px 18px rgba(60, 52, 38, .14));
      animation: treeReveal 2.5s .2s ease both, treeSway 12s 3s ease-in-out infinite;
    }
    .branch-group { transform-origin: 21% 83%; animation: branchSway 8s ease-in-out infinite; }
    .branch-group.soft { animation-delay: -3s; animation-duration: 11s; }
    .tree .branch { fill: none; stroke: #514434; stroke-linecap: round; }
    .tree .twig { fill: none; stroke: #69543c; stroke-linecap: round; opacity: .86; }
    .tree .leaf { fill: #70805a; opacity: .74; }
    .tree .bloom { fill: #e8bc4d; opacity: .94; }
    .tree .bloom-light { fill: #f3d874; opacity: .84; filter: blur(.35px); }
    .tree .bloom-soft { fill: #dba837; opacity: .48; filter: blur(2px); }

    .couple {
      position: absolute;
      left: 58%; bottom: 17%;
      width: clamp(150px, 20vw, 245px);
      z-index: 10;
      transform: translateX(-50%);
      opacity: 0;
      filter: drop-shadow(0 9px 8px rgba(40, 35, 29, .18));
      animation: coupleReveal 2.5s 1.25s ease forwards, breathe 7s 3.7s ease-in-out infinite;
    }
    .couple path, .couple ellipse { fill: #3f3b32; }
    .couple .light-edge { fill: #554b3c; }
    .couple .joined-hands { fill: none; stroke: #403b31; stroke-width: 7; stroke-linecap: round; }

    .grass {
      position: absolute; inset: auto 0 0; height: 30%; z-index: 11; pointer-events: none;
    }
    .blade {
      position: absolute; bottom: -4px;
      width: 2px; height: var(--h);
      border-radius: 100% 0;
      transform-origin: bottom;
      transform: rotate(var(--r));
      background: linear-gradient(to top, #5e6141, #a6a166);
      opacity: var(--o);
      animation: grassWave var(--d) ease-in-out var(--delay) infinite alternate;
    }
    .foreground-flower {
      position: absolute;
      bottom: var(--bottom); left: var(--left);
      z-index: 13;
      width: var(--size); height: var(--size);
      transform-origin: 50% 150%;
      animation: flowerSway var(--duration) ease-in-out var(--delay) infinite alternate;
    }
    .foreground-flower::before {
      content: ""; position: absolute; inset: 36% 48% -170%; width: 2px;
      background: #65704a;
    }
    .foreground-flower span, .falling-flower span, .rising-flower span {
      position: absolute; left: 50%; top: 50%; width: 48%; height: 48%;
      border-radius: 60% 45% 60% 45%;
      background: var(--sun);
      box-shadow: 0 0 4px rgba(238, 190, 63, .35);
    }
    .foreground-flower span:nth-child(1), .falling-flower span:nth-child(1), .rising-flower span:nth-child(1) { transform: translate(-50%, -105%); }
    .foreground-flower span:nth-child(2), .falling-flower span:nth-child(2), .rising-flower span:nth-child(2) { transform: translate(5%, -50%) rotate(90deg); }
    .foreground-flower span:nth-child(3), .falling-flower span:nth-child(3), .rising-flower span:nth-child(3) { transform: translate(-50%, 5%) rotate(180deg); }
    .foreground-flower span:nth-child(4), .falling-flower span:nth-child(4), .rising-flower span:nth-child(4) { transform: translate(-105%, -50%) rotate(270deg); }

    .particles, .falling-layer { position: absolute; inset: 0; z-index: 18; pointer-events: none; overflow: hidden; }
    .mote {
      position: absolute; border-radius: 50%;
      width: var(--s); height: var(--s);
      left: var(--x); top: var(--y);
      background: rgba(255, 238, 159, .78);
      box-shadow: 0 0 8px rgba(255, 220, 110, .7);
      animation: moteFloat var(--d) ease-in-out var(--delay) infinite alternate;
    }
    .falling-flower {
      position: absolute; top: -30px; left: var(--x);
      width: var(--s); height: var(--s);
      opacity: 0;
      will-change: transform, opacity;
      animation: petalFall var(--d) linear var(--delay) infinite;
    }
    .falling-flower span { background: var(--petal, #e7ba44); }

    .scroll-cue {
      position: absolute; bottom: 25px; left: 50%; z-index: 30;
      transform: translateX(-50%); color: rgba(63, 55, 45, .7);
      text-align: center; font-size: 10px; letter-spacing: .24em; text-transform: uppercase;
      opacity: 0; animation: titleReveal 2s 3s ease forwards;
    }
    .scroll-cue::after {
      content: ""; display: block; width: 1px; height: 28px; margin: 9px auto 0;
      background: linear-gradient(var(--wood), transparent);
      animation: scrollLine 2.2s ease-in-out infinite;
    }

    .letter-section {
      position: relative;
      min-height: 130vh;
      padding: clamp(100px, 14vw, 190px) 20px;
      overflow: hidden;
      background:
        radial-gradient(circle at 50% 8%, rgba(238, 198, 100, .25), transparent 32%),
        linear-gradient(180deg, #e8d79d 0%, #f8efcf 13%, #fffaf0 55%, #f4e8bd 100%);
    }
    .letter-section::before {
      content: ""; position: absolute; inset: 0; pointer-events: none; opacity: .28;
      background-image: radial-gradient(rgba(111,86,48,.2) .6px, transparent .8px);
      background-size: 9px 9px;
    }
    .letter-aura {
      position: absolute; left: 50%; top: 24%; width: 95vw; height: 70vh;
      transform: translate(-50%, -50%); pointer-events: none;
      background: radial-gradient(ellipse, rgba(242, 198, 86, .25), transparent 67%);
      opacity: 0; transition: opacity 1.8s ease;
    }
    .letter-section.visible .letter-aura { opacity: 1; }
    .letter-wrap { position: relative; width: min(810px, 94vw); margin: 0 auto; perspective: 1200px; }
    .letter {
      position: relative;
      z-index: 3;
      padding: clamp(50px, 8vw, 90px) clamp(28px, 8vw, 90px);
      border: 1px solid rgba(130, 98, 52, .22);
      border-radius: 4px 10px 5px 8px;
      color: #514538;
      background:
        linear-gradient(100deg, rgba(139,104,52,.04), transparent 22%, rgba(255,255,255,.16) 54%, transparent),
        repeating-linear-gradient(4deg, rgba(103,77,38,.015) 0 1px, transparent 1px 5px),
        #f8edcf;
      box-shadow: 0 30px 65px rgba(91, 67, 37, .17), 0 2px 5px rgba(91,67,37,.13), inset 0 0 60px rgba(166,124,57,.08);
      opacity: 0;
      transform: translateY(70px) rotateX(3deg);
      transition: opacity 1.7s ease, transform 1.7s cubic-bezier(.2,.72,.24,1), box-shadow .7s ease;
    }
    .letter::before, .letter::after {
      content: ""; position: absolute; pointer-events: none;
    }
    .letter::before { inset: 10px; border: 1px solid rgba(135,103,54,.14); }
    .letter::after {
      inset: 0;
      background: radial-gradient(circle at 0 0, rgba(124,89,45,.1), transparent 16%), radial-gradient(circle at 100% 100%, rgba(124,89,45,.08), transparent 19%);
      mix-blend-mode: multiply;
    }
    .letter-section.visible .letter { opacity: 1; transform: translateY(0) rotateX(0); }
    .letter:hover { transform: translateY(-8px) rotateX(.4deg); box-shadow: 0 42px 80px rgba(91,67,37,.22), 0 4px 8px rgba(91,67,37,.12), inset 0 0 80px rgba(255,248,207,.38); }
    .ribbon {
      position: absolute; top: -12px; right: 8%; z-index: 5;
      width: 38px; height: 84px; opacity: .8;
      background: linear-gradient(90deg, #b69253, #d6bd7c 45%, #a98346);
      clip-path: polygon(0 0,100% 0,100% 100%,50% 81%,0 100%);
      filter: drop-shadow(1px 2px 2px rgba(80,60,35,.15));
    }
    .letter h2 {
      margin: 0 0 38px; text-align: center;
      font: 400 clamp(2.8rem, 8vw, 5.2rem)/1 var(--script);
      color: #8c683e;
    }
    .salutation { font: italic 1.12rem/1.8 var(--serif); }
    .letter p { margin: 0 0 1.4em; font: 400 clamp(1rem, 2vw, 1.13rem)/1.95 var(--serif); }
    .code {
      display: block;
      margin: 26px auto;
      padding: 17px 18px;
      border-top: 1px solid rgba(126,96,54,.2);
      border-bottom: 1px solid rgba(126,96,54,.2);
      color: #746044;
      font: 500 clamp(.69rem, 1.6vw, .84rem)/1.8 "Courier New", monospace;
      text-align: center;
      overflow-wrap: anywhere;
      background: rgba(255, 249, 224, .35);
    }
    .signature { margin-top: 42px !important; text-align: right; font-family: var(--script) !important; font-size: clamp(1.35rem, 3vw, 1.8rem) !important; line-height: 1.55 !important; color: #765437; }
    .letter-sprig { position: absolute; z-index: 4; width: 110px; height: 150px; opacity: .85; transition: transform 1.5s ease; }
    .letter-section.visible .sprig-left { transform: rotate(-14deg) translate(0); }
    .letter-section.visible .sprig-right { transform: rotate(166deg) translate(0); }
    .sprig-left { left: -58px; top: 11%; transform: rotate(-24deg) translate(-20px, 30px); }
    .sprig-right { right: -60px; bottom: 9%; transform: rotate(177deg) translate(-20px, 30px); }
    .letter-sprig .stem { position:absolute; left:52px; top:10px; width:2px; height:135px; background:#7c8258; transform:rotate(-14deg); transform-origin:bottom; }
    .letter-sprig i { position:absolute; width:18px; height:18px; border-radius:50%; background:#e3b840; box-shadow: 13px 4px 0 -3px #efd068, -8px 10px 0 -4px #d6a52d; }

    .finale {
      position: relative; min-height: 100svh; padding: 90px 20px;
      display: grid; place-items: center; overflow: hidden;
      background: radial-gradient(circle at 50% 50%, #fff8d9, #f4df98 70%, #ddc77f);
    }
    .finale::before {
      content:""; position:absolute; inset:0;
      background: linear-gradient(180deg, rgba(255,255,255,.25), transparent 35%, rgba(148,124,61,.08));
    }
    .final-content { position: relative; z-index: 3; text-align: center; width: min(850px, 94vw); }
    .final-line {
      margin: 0 0 24px; color: var(--wood-dark);
      font: italic 400 clamp(1.55rem, 4vw, 3.25rem)/1.35 var(--serif);
      opacity: 0; transform: translateY(22px); transition: opacity 1.7s ease, transform 1.7s ease;
    }
    .finale.visible .final-line:nth-child(1) { opacity:1; transform:none; transition-delay:.3s; }
    .finale.visible .final-line:nth-child(2) { opacity:1; transform:none; transition-delay:2s; }
    .finale.visible .final-line:nth-child(3) { opacity:1; transform:none; transition-delay:3.8s; }
    .final-line:last-child { margin-top: 44px; font-family: var(--script); color:#7d5b35; }
    .rising-layer { position:absolute; inset:0; pointer-events:none; z-index:2; }
    .rising-flower {
      position:absolute; bottom:-30px; left:var(--x); width:var(--s); height:var(--s); opacity:0;
      animation:risingPetal var(--d) ease-in var(--delay) infinite;
    }

    @keyframes titleReveal { from { opacity:0; transform:translate(-50%, 22px); } to { opacity:1; transform:translate(-50%, 0); } }
    @keyframes treeReveal { from { opacity:0; transform:translateX(-45px); filter:blur(5px); } to { opacity:1; transform:translateX(0); filter:blur(0); } }
    @keyframes coupleReveal { from { opacity:0; transform:translate(-50%, 24px); } to { opacity:1; transform:translate(-50%, 0); } }
    @keyframes treeSway { 0%,100% { rotate:-.25deg; } 50% { rotate:.35deg; } }
    @keyframes branchSway { 0%,100% { transform:rotate(-.7deg); } 50% { transform:rotate(1deg); } }
    @keyframes breathe { 0%,100% { scale:1; } 50% { scale:1.006 .998; } }
    @keyframes sunPulse { 0%,100% { opacity:.9; scale:1; } 50% { opacity:1; scale:1.045; } }
    @keyframes lightBreath { 0%,100% { opacity:.82; } 50% { opacity:1; } }
    @keyframes grassWave { from { transform:rotate(calc(var(--r) - 2deg)); } to { transform:rotate(calc(var(--r) + 3deg)); } }
    @keyframes flowerSway { from { transform:rotate(-4deg); } to { transform:rotate(5deg); } }
    @keyframes moteFloat { from { transform:translate(0, 6px); opacity:.18; } to { transform:translate(18px, -14px); opacity:.9; } }
    @keyframes petalFall {
      0% { opacity:0; transform:translate3d(0,-5vh,0) rotate(0deg); }
      12% { opacity:.82; }
      88% { opacity:.7; }
      100% { opacity:0; transform:translate3d(var(--drift),108vh,0) rotate(var(--spin)); }
    }
    @keyframes risingPetal { 0% { opacity:0; transform:translate(0,0) rotate(0); } 16% { opacity:.65; } 85% { opacity:.45; } 100% { opacity:0; transform:translate(var(--drift),-105vh) rotate(280deg); } }
    @keyframes scrollLine { 0%,100% { transform:scaleY(.45); transform-origin:top; opacity:.35; } 50% { transform:scaleY(1); opacity:.8; } }

    @media (max-width: 760px) {
      .scene { min-height: 620px; height: 92svh; }
      .title-wrap { top: 68px; }
      .title-wrap .eyebrow { letter-spacing:.2em; }
      .tree { width: 63vw; left:-16%; bottom:14%; height:57vh; }
      .couple { left:62%; bottom:18%; width:145px; }
      .sun { left:70%; top:57%; }
      .horizon-front { height:29%; }
      .letter-section { padding-inline:12px; }
      .letter { padding:55px 26px; }
      .letter p { line-height:1.82; }
      .letter-sprig { width:75px; transform:scale(.8); }
      .sprig-left { left:-30px; }
      .sprig-right { right:-24px; }
      .scroll-cue { bottom:16px; }
    }
    @media (max-width: 390px) {
      .tree { left:-23%; width:72vw; }
      .couple { left:64%; width:128px; }
      .title-wrap { top:52px; }
      .subtitle { margin-top:12px; }
      .letter { padding-inline:21px; }
    }
    @media (prefers-reduced-motion: reduce) {
      html { scroll-behavior:auto; }
      *, *::before, *::after { animation-duration:.01ms !important; animation-iteration-count:1 !important; transition-duration:.01ms !important; }
      .title-wrap, .tree, .couple, .letter, .final-line { opacity:1 !important; transform:none !important; }
      .falling-layer, .particles, .rising-layer { display:none; }
    }
  </style>
</head>
<body>
  <main>
    <section class="scene" aria-labelledby="main-title">
      <div class="sky-haze"></div>
      <div class="sun" aria-hidden="true"></div>
      <div class="horizon-back" aria-hidden="true"></div>
      <div class="horizon-front" aria-hidden="true"></div>

      <header class="title-wrap">
        <span class="eyebrow">21 de septiembre · nuestra segunda vez</span>
        <h1 id="main-title">Una sorpresa<br>de primavera</h1>
        <p class="subtitle">Feliz segunda primavera juntos</p>
        <span class="title-flower" aria-hidden="true"></span>
      </header>

      <svg class="tree" viewBox="0 0 560 720" role="img" aria-label="Árbol de aromo cubierto de pequeñas flores amarillas">
        <g opacity=".9">
          <path class="branch" stroke-width="25" d="M100 720 C112 610 106 505 151 388 C173 327 196 271 204 193"/>
          <path class="branch" stroke-width="14" d="M139 445 C100 367 76 296 45 229"/>
          <path class="branch" stroke-width="12" d="M154 387 C218 315 278 257 360 212"/>
          <path class="branch" stroke-width="9" d="M177 316 C231 245 245 164 263 75"/>
          <path class="branch" stroke-width="8" d="M205 273 C306 250 382 167 452 91"/>
        </g>
        <g class="branch-group">
          <path class="twig" stroke-width="5" d="M49 231 Q92 170 150 140 M74 189 Q43 139 32 89 M107 160 Q123 92 174 44"/>
          <path class="twig" stroke-width="4" d="M178 310 Q109 268 58 273 M168 326 Q113 329 76 367 M153 376 Q104 385 68 431"/>
          <g class="leaf"><ellipse cx="70" cy="198" rx="15" ry="5" transform="rotate(-25 70 198)"/><ellipse cx="112" cy="155" rx="17" ry="5" transform="rotate(20 112 155)"/><ellipse cx="60" cy="281" rx="16" ry="5"/><ellipse cx="98" cy="346" rx="15" ry="5" transform="rotate(-30 98 346)"/></g>
          <g class="bloom">
            <circle cx="33" cy="88" r="8"/><circle cx="46" cy="104" r="6"/><circle cx="64" cy="77" r="7"/><circle cx="83" cy="120" r="9"/><circle cx="110" cy="98" r="7"/><circle cx="137" cy="74" r="8"/><circle cx="170" cy="44" r="10"/><circle cx="189" cy="62" r="7"/><circle cx="144" cy="122" r="9"/><circle cx="105" cy="157" r="8"/><circle cx="62" cy="161" r="9"/><circle cx="36" cy="190" r="7"/>
            <circle cx="58" cy="255" r="9"/><circle cx="81" cy="274" r="7"/><circle cx="106" cy="290" r="10"/><circle cx="63" cy="316" r="8"/><circle cx="98" cy="338" r="9"/><circle cx="67" cy="372" r="7"/><circle cx="115" cy="387" r="10"/><circle cx="78" cy="422" r="9"/>
          </g>
        </g>
        <g class="branch-group soft">
          <path class="twig" stroke-width="5" d="M201 273 Q290 217 345 137 M263 240 Q307 172 329 101 M321 174 Q390 152 444 107 M357 214 Q423 209 497 173"/>
          <path class="twig" stroke-width="4" d="M251 175 Q208 120 208 62 M281 221 Q282 151 270 91 M403 146 Q436 87 481 56 M428 196 Q486 131 526 125"/>
          <g class="leaf"><ellipse cx="299" cy="177" rx="17" ry="5" transform="rotate(-58 299 177)"/><ellipse cx="370" cy="157" rx="17" ry="5" transform="rotate(-12 370 157)"/><ellipse cx="431" cy="122" rx="15" ry="5" transform="rotate(-40 431 122)"/><ellipse cx="466" cy="183" rx="17" ry="5" transform="rotate(20 466 183)"/></g>
          <g class="bloom-light">
            <circle cx="209" cy="62" r="8"/><circle cx="224" cy="78" r="6"/><circle cx="253" cy="104" r="9"/><circle cx="270" cy="78" r="7"/><circle cx="297" cy="119" r="8"/><circle cx="329" cy="99" r="10"/><circle cx="347" cy="127" r="7"/><circle cx="371" cy="143" r="9"/><circle cx="399" cy="119" r="8"/><circle cx="427" cy="102" r="10"/><circle cx="452" cy="76" r="7"/><circle cx="481" cy="54" r="9"/><circle cx="500" cy="88" r="8"/><circle cx="529" cy="124" r="10"/><circle cx="502" cy="154" r="7"/><circle cx="475" cy="180" r="9"/><circle cx="438" cy="195" r="8"/><circle cx="405" cy="171" r="7"/><circle cx="360" cy="207" r="10"/><circle cx="316" cy="218" r="7"/><circle cx="285" cy="239" r="9"/>
          </g>
          <g class="bloom-soft"><circle cx="468" cy="91" r="18"/><circle cx="344" cy="154" r="16"/><circle cx="242" cy="130" r="15"/><circle cx="509" cy="177" r="14"/></g>
        </g>
      </svg>

      <svg class="couple" viewBox="0 0 240 330" role="img" aria-label="Una pareja, ella de cabello liso y él de cabello rizado, contempla el horizonte">
        <g>
          <ellipse cx="84" cy="83" rx="30" ry="35"/>
          <path d="M52 81 Q51 39 85 35 Q116 40 116 83 L112 151 L57 151 Z"/>
          <path class="light-edge" d="M63 59 Q84 39 106 59 L109 147 L101 144 L100 68 Q79 55 64 71 L64 143 L57 150 Z"/>
          <path d="M53 139 Q84 121 115 141 L131 267 L42 267 Z"/>
          <path d="M61 260 L50 330 L80 330 L87 265 Z M95 262 L102 330 L132 330 L119 258 Z"/>
        </g>
        <g>
          <circle cx="164" cy="76" r="30"/>
          <g><circle cx="143" cy="49" r="13"/><circle cx="158" cy="39" r="14"/><circle cx="176" cy="42" r="13"/><circle cx="188" cy="55" r="12"/><circle cx="139" cy="68" r="11"/><circle cx="184" cy="73" r="12"/></g>
          <path d="M136 122 Q164 108 193 124 L208 262 L123 262 Z"/>
          <path d="M136 255 L125 330 L153 330 L163 265 Z M171 263 L180 330 L209 330 L196 257 Z"/>
        </g>
        <path class="joined-hands" d="M112 175 Q132 190 142 174"/>
      </svg>

      <div class="grass" id="grass" aria-hidden="true"></div>
      <div class="particles" id="particles" aria-hidden="true"></div>
      <div class="falling-layer" id="fallingFlowers" aria-hidden="true"></div>
      <div class="scroll-cue" aria-hidden="true">Desliza</div>
    </section>

    <section class="letter-section" id="letterSection" aria-labelledby="letter-title">
      <div class="letter-aura" aria-hidden="true"></div>
      <div class="letter-wrap">
        <div class="ribbon" aria-hidden="true"></div>
        <div class="letter-sprig sprig-left" aria-hidden="true"><b class="stem"></b><i style="left:20px;top:18px"></i><i style="left:42px;top:48px"></i><i style="left:15px;top:78px"></i><i style="left:48px;top:105px"></i></div>
        <article class="letter">
          <h2 id="letter-title">Para mi nubesita</h2>
          <p class="salutation">“Felicidades mi princesita, parece que aún no pierdes el toque,”</p>
          <code class="code">01110100 01100101 00100000 01100001 01101101 01101111</code>
          <code class="code">--.- ..- . / - . / .- -- --- / .. -. ..-. .. -. .. - .- -- . -. - . --..-- / -.-- / .--. .- .-. .- / - --- -.. .- / .-.. .- / ...- .. -.. .- .-.-.</code>
          <p>Te amo demasiado mi reina hermosa, tanto que busco cada instancia y capacidad para hacerte sentir amada, a veces siento que estas cosas salen feas</p>
          <p>pero quiero demostrarte mi amor hacia a ti, y mi dedicación de muchas maneras, y si so dedicado ahora, es poque quiero demostrarte que vivirás con un hombre que dedicará atención y mimos hacia su mujer.</p>
          <p>También sabes que no me suele gustar regalar por tradición o moda, si no que lo hago con un fin especifico, espero que estos dias no te hayas sentido mal porque no te llegó algo.</p>
          <p>puedes deducir que la espera es mejor que recibirlo inmediatamente.</p>
          <p>Quiero seguir descubriendo lugares contigo, seguir riéndome de nuestras pequeñas tonterías, superar contigo los días difíciles, celebrar nuestros logros y construir poco a poco ese futuro que tantas veces imaginamos.</p>
          <p>Quiero que algún día podamos mirar hacia atrás y recordar estas primeras primaveras como el comienzo de algo mucho más grande.</p>
          <p>Porque si hoy puedo imaginar un horizonte y verte en él, no es solamente porque te amo.</p>
          <p>Es porque cuando pienso en el futuro, inevitablemente apareces tú.</p>
          <p>Feliz segunda primavera juntos, mi princesita.</p>
          <p>Que esta sea una de tantas que todavía nos quedan por vivir.</p>
          <p class="signature">Con todo mi amor,<br>Rey ❤️</p>
        </article>
        <div class="letter-sprig sprig-right" aria-hidden="true"><b class="stem"></b><i style="left:20px;top:18px"></i><i style="left:42px;top:48px"></i><i style="left:15px;top:78px"></i><i style="left:48px;top:105px"></i></div>
      </div>
    </section>

    <section class="finale" id="finale" aria-label="Mensaje final para Jani">
      <div class="rising-layer" id="risingFlowers" aria-hidden="true"></div>
      <div class="final-content">
        <p class="final-line">“Y esto recién comienza...”</p>
        <p class="final-line">“Nos quedan muchas primaveras por vivir.”</p>
        <p class="final-line">“Te amo, mi corderita!”</p>
      </div>
    </section>
  </main>

  <script>
    (() => {
      const reducedMotion = window.matchMedia('(prefers-reduced-motion: reduce)').matches;
      const grass = document.getElementById('grass');
      const particles = document.getElementById('particles');
      const falling = document.getElementById('fallingFlowers');
      const rising = document.getElementById('risingFlowers');
      const flowerMarkup = '<span></span><span></span><span></span><span></span>';
      const random = (min, max) => Math.random() * (max - min) + min;

      function createGrass() {
        const count = window.innerWidth < 600 ? 75 : 145;
        const fragment = document.createDocumentFragment();
        for (let i = 0; i < count; i++) {
          const blade = document.createElement('i');
          blade.className = 'blade';
          blade.style.left = `${random(0, 100)}%`;
          blade.style.setProperty('--h', `${random(28, 112)}px`);
          blade.style.setProperty('--r', `${random(-14, 14)}deg`);
          blade.style.setProperty('--o', random(.25, .76).toFixed(2));
          blade.style.setProperty('--d', `${random(3.8, 7.5)}s`);
          blade.style.setProperty('--delay', `${random(-7, 0)}s`);
          fragment.appendChild(blade);
        }
        grass.appendChild(fragment);

        for (let i = 0; i < (window.innerWidth < 600 ? 7 : 13); i++) {
          const flower = document.createElement('div');
          flower.className = 'foreground-flower';
          flower.innerHTML = flowerMarkup;
          flower.style.setProperty('--left', `${random(5, 96)}%`);
          flower.style.setProperty('--bottom', `${random(3, 15)}%`);
          flower.style.setProperty('--size', `${random(8, 15)}px`);
          flower.style.setProperty('--duration', `${random(4, 8)}s`);
          flower.style.setProperty('--delay', `${random(-6, 0)}s`);
          document.querySelector('.scene').appendChild(flower);
        }
      }

      function createMotes() {
        const fragment = document.createDocumentFragment();
        const count = window.innerWidth < 600 ? 12 : 24;
        for (let i = 0; i < count; i++) {
          const mote = document.createElement('i');
          mote.className = 'mote';
          mote.style.setProperty('--x', `${random(24, 94)}%`);
          mote.style.setProperty('--y', `${random(30, 85)}%`);
          mote.style.setProperty('--s', `${random(1.5, 4.5)}px`);
          mote.style.setProperty('--d', `${random(5, 11)}s`);
          mote.style.setProperty('--delay', `${random(-10, 0)}s`);
          fragment.appendChild(mote);
        }
        particles.appendChild(fragment);
      }

      function createFallingFlowers() {
        const fragment = document.createDocumentFragment();
        const count = window.innerWidth < 600 ? 18 : 32;
        for (let i = 0; i < count; i++) {
          const flower = document.createElement('div');
          flower.className = 'falling-flower';
          flower.innerHTML = flowerMarkup;
          flower.style.setProperty('--x', `${random(-3, 48)}%`);
          flower.style.setProperty('--s', `${random(5, 11)}px`);
          flower.style.setProperty('--d', `${random(11, 23)}s`);
          flower.style.setProperty('--delay', `${random(-22, 0)}s`);
          flower.style.setProperty('--drift', `${random(20, 180)}px`);
          flower.style.setProperty('--spin', `${random(120, 540)}deg`);
          flower.style.setProperty('--petal', Math.random() > .45 ? '#e7b83f' : '#f0ce68');
          fragment.appendChild(flower);
        }
        falling.appendChild(fragment);
      }

      function createRisingFlowers() {
        const fragment = document.createDocumentFragment();
        const count = window.innerWidth < 600 ? 15 : 25;
        for (let i = 0; i < count; i++) {
          const flower = document.createElement('div');
          flower.className = 'rising-flower';
          flower.innerHTML = flowerMarkup;
          flower.style.setProperty('--x', `${random(4, 96)}%`);
          flower.style.setProperty('--s', `${random(5, 12)}px`);
          flower.style.setProperty('--d', `${random(12, 22)}s`);
          flower.style.setProperty('--delay', `${random(2, 12)}s`);
          flower.style.setProperty('--drift', `${random(-80, 80)}px`);
          fragment.appendChild(flower);
        }
        rising.appendChild(fragment);
      }

      if (!reducedMotion) {
        createGrass();
        createMotes();
        createFallingFlowers();
        createRisingFlowers();
      }

      const letterSection = document.getElementById('letterSection');
      const finale = document.getElementById('finale');
      const observer = new IntersectionObserver((entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) {
            entry.target.classList.add('visible');
            if (entry.target === letterSection) document.body.classList.add('letter-near');
          }
        });
      }, { threshold: .16 });
      observer.observe(letterSection);
      observer.observe(finale);
    })();
  </script>
</body>
</html>
