<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Bab's Journal</title>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,500;1,400;1,600&family=Dancing+Script:wght@500;700&family=IM+Fell+English:ital@1&display=swap" rel="stylesheet">
<style>
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
:root{
  --cover-dk:#c87880;--cover-lt:#f2bfc5;
  --page-bg:#faf6ef;--dash:rgba(175,148,112,.36);
  --tape:rgba(235,200,148,.7);--ink:#52422e;--ink2:#7d6048;
  --spine:#c87880;--spine-dk:#a85c66;
}
html,body{min-height:100%;overflow-x:hidden}
body{
  background:linear-gradient(150deg,#fdeaef 0%,#fdf3e8 45%,#fdeaef 100%);
  font-family:'Cormorant Garamond',serif;
  display:flex;flex-direction:column;align-items:center;
  padding:28px 16px 56px;min-height:100vh;
  transform:translateZ(0);
}
body::before{
  content:'';position:fixed;inset:0;pointer-events:none;z-index:0;
  background:
    radial-gradient(ellipse at 18% 14%,rgba(255,210,220,.38) 0%,transparent 50%),
    radial-gradient(ellipse at 82% 86%,rgba(255,190,205,.28) 0%,transparent 46%);
}
.journal-title{
  font-family:'Dancing Script',cursive;font-size:clamp(1.8rem,5.5vw,2.6rem);
  color:var(--spine-dk);text-align:center;margin-bottom:3px;letter-spacing:1.5px;
  text-shadow:0 2px 10px rgba(168,92,102,.2);position:relative;z-index:2;
  animation:fadeUp .7s cubic-bezier(.25,.46,.45,.94) both;
}
.journal-sub{
  font-family:'IM Fell English',serif;font-style:italic;
  font-size:clamp(.74rem,2.2vw,.88rem);color:var(--ink2);letter-spacing:4px;
  margin-bottom:26px;position:relative;z-index:2;text-align:center;
  animation:fadeUp .7s .1s cubic-bezier(.25,.46,.45,.94) both;
}
@keyframes fadeUp{from{opacity:0;transform:translateY(14px)}to{opacity:1;transform:translateY(0)}}

.book-wrapper{
  position:relative;z-index:2;width:100%;max-width:500px;
  perspective:1800px;perspective-origin:50% 50%;
}
.book-wrapper::before{
  content:'';position:absolute;top:6px;bottom:6px;left:-18px;width:20px;
  background:repeating-linear-gradient(to left,#f4ede1 0,#f4ede1 2px,#ece4d5 2px,#ece4d5 4px,#e7dfc8 4px,#e7dfc8 5px,#f0e8d8 5px,#f0e8d8 7px);
  border-radius:3px 0 0 3px;box-shadow:-3px 0 8px rgba(0,0,0,.06);pointer-events:none;z-index:1;
}
.book-wrapper::after{
  content:'';position:absolute;top:10px;bottom:10px;left:-24px;width:7px;
  background:linear-gradient(to left,#ddd5c2,#cbc2b0);border-radius:2px 0 0 2px;
  box-shadow:-2px 0 5px rgba(0,0,0,.05);pointer-events:none;z-index:1;
}

/* ── PAGE CARD ── */
.page-card{
  width:100%;background:var(--page-bg);border-radius:2px 12px 12px 2px;
  border-left:5px solid var(--spine);position:relative;overflow:hidden;
  box-shadow:3px 4px 0 #f0e6d8,6px 8px 0 #e8dac8,9px 13px 0 rgba(210,185,155,.45),14px 22px 36px rgba(155,85,95,.18),0 1px 4px rgba(155,85,95,.1);
  will-change:transform,opacity;transform:translateZ(0);
  animation:pageAppear .5s cubic-bezier(.25,.46,.45,.94) both;
}
@keyframes pageAppear{from{opacity:0;transform:translateZ(0) translateY(16px)}to{opacity:1;transform:translateZ(0) translateY(0)}}
.page-card.no-appear{animation:none!important}

/* ruled lines */
.page-card::before{
  content:'';position:absolute;inset:0;z-index:1;pointer-events:none;
  background-image:repeating-linear-gradient(transparent 0,transparent 32px,var(--dash) 32px,var(--dash) 33px);
  background-size:100% 33px;background-position:0 56px;
}
/* margin line */
.page-card::after{
  content:'';position:absolute;top:0;bottom:0;left:46px;width:1px;
  background:rgba(200,140,128,.28);pointer-events:none;z-index:1;
}

/* torn top edge */
.torn-edge{
  position:absolute;top:0;left:0;right:0;height:18px;z-index:8;
  background:var(--page-bg);pointer-events:none;
  clip-path:polygon(0% 100%,0.5% 18%,1.5% 70%,2.5% 25%,3.5% 78%,4.5% 16%,5.5% 62%,6.5% 20%,7.5% 74%,8.5% 16%,9.5% 56%,10.5% 8%,11.5% 50%,12.5% 18%,13.5% 66%,14.5% 22%,15.5% 72%,16.5% 26%,17.5% 66%,18.5% 12%,19.5% 56%,20.5% 18%,21.5% 62%,22.5% 8%,23.5% 52%,24.5% 16%,25.5% 64%,26.5% 20%,27.5% 68%,28.5% 24%,29.5% 72%,30.5% 14%,31.5% 60%,32.5% 18%,33.5% 64%,34.5% 10%,35.5% 54%,36.5% 18%,37.5% 66%,38.5% 22%,39.5% 68%,40.5% 14%,41.5% 60%,42.5% 18%,43.5% 64%,44.5% 10%,45.5% 54%,46.5% 16%,47.5% 62%,48.5% 14%,49.5% 66%,50.5% 18%,51.5% 68%,52.5% 24%,53.5% 72%,54.5% 14%,55.5% 58%,56.5% 16%,57.5% 62%,58.5% 8%,59.5% 54%,60.5% 18%,61.5% 66%,62.5% 22%,63.5% 70%,64.5% 14%,65.5% 60%,66.5% 18%,67.5% 64%,68.5% 10%,69.5% 54%,70.5% 16%,71.5% 62%,72.5% 14%,73.5% 66%,74.5% 18%,75.5% 68%,76.5% 24%,77.5% 72%,78.5% 14%,79.5% 58%,80.5% 16%,81.5% 62%,82.5% 8%,83.5% 54%,84.5% 18%,85.5% 66%,86.5% 22%,87.5% 70%,88.5% 14%,89.5% 60%,90.5% 18%,91.5% 64%,92.5% 10%,93.5% 54%,94.5% 16%,95.5% 62%,96.5% 14%,97.5% 58%,98.5% 20%,99.5% 66%,100% 58%,100% 100%);
}

.tape{position:absolute;pointer-events:none;z-index:9;border-radius:2px;background:var(--tape);background-image:repeating-linear-gradient(90deg,transparent 0,transparent 3px,rgba(255,255,255,.2) 3px,rgba(255,255,255,.2) 4px);box-shadow:0 1px 3px rgba(150,110,55,.16),inset 0 1px 0 rgba(255,255,255,.3);}
.tape-tl{top:3px;left:22px;width:56px;height:15px;transform:rotate(-11deg)}
.tape-tr{top:4px;right:20px;width:52px;height:15px;transform:rotate(9deg)}
.tape-bl{bottom:20px;left:16px;width:46px;height:13px;transform:rotate(7deg)}

.deco{position:absolute;pointer-events:none;z-index:9;opacity:.5;user-select:none;animation:decoFloat 6s ease-in-out infinite alternate;will-change:transform;}
.deco-tr{top:16px;right:26px;font-size:1.35rem;animation-name:decoFloatTr;animation-delay:.5s}
.deco-bl{bottom:28px;left:50px;font-size:1rem;animation-name:decoFloatBl}
@keyframes decoFloatTr{from{transform:rotate(13deg) translateY(0)}to{transform:rotate(13deg) translateY(-5px)}}
@keyframes decoFloatBl{from{transform:rotate(-11deg) translateY(0)}to{transform:rotate(-11deg) translateY(-4px)}}

/* ── SCROLL AREA ── */
.page-scroll{
  position:relative;z-index:4;max-height:70vh;
  overflow-y:auto;overflow-x:hidden;overscroll-behavior:contain;
  -webkit-overflow-scrolling:touch;padding:30px 28px 52px 60px;
  scrollbar-width:thin;scrollbar-color:rgba(175,130,100,.28) transparent;
  animation:contentIn .35s cubic-bezier(.25,.46,.45,.94) both;
}
.page-scroll::-webkit-scrollbar{width:3px}
.page-scroll::-webkit-scrollbar-thumb{background:rgba(175,130,100,.32);border-radius:3px}
@keyframes contentIn{from{opacity:0;transform:translateY(8px)}to{opacity:1;transform:translateY(0)}}

.page-header{
  display:flex;align-items:center;gap:10px;margin-bottom:18px;padding-bottom:10px;
  border-bottom:1.5px dashed rgba(175,145,108,.32);margin-top:12px;
}
.page-icon{font-size:1.4rem;line-height:1;flex-shrink:0}
.page-title{font-family:'Dancing Script',cursive;font-size:clamp(1.22rem,3.8vw,1.6rem);color:var(--ink);line-height:1.2;}

/* ── BODY TEXT ── */
.page-body p{
  font-family:'Cormorant Garamond',serif;font-style:italic;
  font-size:clamp(.95rem,2.8vw,1.1rem);color:var(--ink);line-height:2.27;margin-bottom:0;
}
.page-body p.gap{height:33px;margin:0;}
.page-body p strong{font-weight:600;color:var(--spine-dk);font-style:italic}
.page-body p em{color:var(--ink2)}

.page-num{
  text-align:right;padding:8px 22px 16px 0;
  font-family:'IM Fell English',serif;font-style:italic;
  font-size:.77rem;color:rgba(130,100,80,.48);position:relative;z-index:4;
}

/* ── COVER ── */
.page-card.cover{
  background:linear-gradient(145deg,#f4c2c8 0%,#e8a0a8 40%,#d08090 100%);
  border-left:6px solid var(--spine-dk);min-height:480px;
  display:flex;flex-direction:column;align-items:center;justify-content:center;
  text-align:center;padding:50px 28px;
}
.page-card.cover::before,.page-card.cover::after{display:none}
.cover-stitch{position:absolute;inset:13px;border:1.5px dashed rgba(255,255,255,.38);border-radius:6px;pointer-events:none;z-index:2;}
.cover-svg{position:absolute;inset:0;width:100%;height:100%;pointer-events:none;z-index:2;}
.cover-inner{position:relative;z-index:3;display:flex;flex-direction:column;align-items:center;gap:5px;}
.cover-vintage{font-family:'IM Fell English',serif;font-style:italic;font-size:clamp(.72rem,2vw,.86rem);color:rgba(255,255,255,.72);letter-spacing:4px;margin-bottom:4px;}
.cover-main-title{font-family:'Dancing Script',cursive;font-size:clamp(1.9rem,6.5vw,2.8rem);color:rgba(255,255,255,.95);text-shadow:0 3px 12px rgba(110,45,58,.35);line-height:1.2;letter-spacing:1px;}
.cover-lock{font-size:2.4rem;margin:8px 0 4px;animation:lockSway 5s ease-in-out infinite;will-change:transform;}
@keyframes lockSway{0%,100%{transform:rotate(-5deg) translateY(0)}50%{transform:rotate(5deg) translateY(-3px)}}
.cover-sub{font-family:'Cormorant Garamond',serif;font-style:italic;font-size:clamp(.72rem,2vw,.84rem);color:rgba(255,255,255,.6);letter-spacing:4px;margin-top:4px;}

/* ── BACK COVER ── */
.page-card.back-cover{
  background:linear-gradient(145deg,#d08090 0%,#e8a0a8 50%,#f4c2c8 100%);
  border-left:6px solid var(--spine-dk);min-height:480px;
  display:flex;flex-direction:column;align-items:center;justify-content:center;
  text-align:center;padding:50px 28px;
}
.page-card.back-cover::before,.page-card.back-cover::after{display:none}
.back-stitch{position:absolute;inset:13px;border:1.5px dashed rgba(255,255,255,.32);border-radius:6px;pointer-events:none;z-index:2;}
.back-cover-svg{position:absolute;inset:0;width:100%;height:100%;pointer-events:none;z-index:2;opacity:.58;}
.back-quote{font-family:'IM Fell English',serif;font-style:italic;font-size:clamp(1rem,3vw,1.2rem);color:rgba(255,255,255,.92);line-height:1.9;text-shadow:0 2px 8px rgba(110,40,52,.22);max-width:300px;margin-bottom:18px;position:relative;z-index:3;}
.back-author{font-family:'Cormorant Garamond',serif;font-style:italic;color:rgba(255,255,255,.62);font-size:.82rem;letter-spacing:2px;position:relative;z-index:3;}

/* ── FLIP ── */
@keyframes outFwd{from{transform:perspective(1800px) rotateY(0deg);opacity:1}to{transform:perspective(1800px) rotateY(-90deg);opacity:.2}}
@keyframes outBack{from{transform:perspective(1800px) rotateY(0deg);opacity:1}to{transform:perspective(1800px) rotateY(90deg);opacity:.2}}
@keyframes inFwd{from{transform:perspective(1800px) rotateY(90deg);opacity:.2}to{transform:perspective(1800px) rotateY(0deg);opacity:1}}
@keyframes inBack{from{transform:perspective(1800px) rotateY(-90deg);opacity:.2}to{transform:perspective(1800px) rotateY(0deg);opacity:1}}
.page-card.out-fwd{transform-origin:right center;animation:outFwd .3s ease-in both}
.page-card.out-back{transform-origin:left center;animation:outBack .3s ease-in both}
.page-card.in-fwd{transform-origin:left center;animation:inFwd .3s ease-out both}
.page-card.in-back{transform-origin:right center;animation:inBack .3s ease-out both}

/* ── NAV ── */
.nav-bar{position:relative;z-index:10;display:flex;align-items:center;justify-content:center;gap:16px;margin-top:24px;width:100%;max-width:500px;}
.nav-btn{
  background:rgba(255,255,255,.88);border:1.5px solid rgba(210,150,160,.38);color:var(--ink);
  font-family:'Dancing Script',cursive;font-size:1.1rem;padding:11px 28px;border-radius:32px;
  cursor:pointer;transition:transform .18s,background .2s,color .2s;
  box-shadow:0 3px 12px rgba(170,85,100,.14),inset 0 1px 0 rgba(255,255,255,.65);
  white-space:nowrap;user-select:none;-webkit-tap-highlight-color:transparent;will-change:transform;
}
.nav-btn:hover:not(:disabled){background:rgba(220,145,155,.75);color:white;transform:translateY(-2px)}
.nav-btn:active:not(:disabled){transform:translateY(0)}
.nav-btn:disabled{opacity:.28;cursor:not-allowed}
.nav-ind{
  font-family:'IM Fell English',serif;font-style:italic;color:var(--ink2);font-size:.92rem;
  text-align:center;background:rgba(255,255,255,.7);padding:9px 20px;border-radius:22px;
  min-width:108px;box-shadow:0 2px 10px rgba(170,85,100,.1),inset 0 1px 0 rgba(255,255,255,.75);
  border:1px solid rgba(210,150,160,.22);
}
.dots{display:flex;gap:8px;justify-content:center;flex-wrap:wrap;max-width:380px;margin-top:16px;position:relative;z-index:2;}
.dot{width:7px;height:7px;border-radius:50%;background:rgba(210,145,158,.28);border:1px solid rgba(210,145,158,.18);transition:transform .25s cubic-bezier(.34,1.56,.64,1),background .25s;will-change:transform;}
.dot.active{background:var(--spine-dk);border-color:var(--spine-dk);transform:scale(1.55);box-shadow:0 0 0 3px rgba(168,92,102,.15)}
.dot.done{background:rgba(210,145,158,.5);border-color:rgba(210,145,158,.38)}

/* ── PETALS ── */
.petal{position:fixed;pointer-events:none;z-index:0;animation:petalFall linear infinite;opacity:0;will-change:transform,opacity;}
@keyframes petalFall{0%{transform:translate(0,-20px) rotate(0deg);opacity:0}8%{opacity:.55}92%{opacity:.35}100%{transform:translate(15px,105vh) rotate(300deg);opacity:0}}

@media(max-width:420px){
  body{padding:14px 8px 46px}
  .page-scroll{padding:24px 14px 48px 44px;max-height:66vh}
  .page-card.cover,.page-card.back-cover{min-height:400px;padding:38px 20px}
  .nav-btn{padding:9px 18px;font-size:1rem}
  .book-wrapper::before,.book-wrapper::after{display:none}
  .page-card::after{left:32px}
}
</style>
</head>
<body>

<h1 class="journal-title">&#x1F338; Bab's Journal</h1>
<p class="journal-sub">~ A silent reflection ~</p>

<div class="book-wrapper">
  <div class="page-card" id="pageCard"></div>
</div>

<nav class="nav-bar">
  <button class="nav-btn" id="prevBtn" onclick="navigate(-1)" disabled>&#x2190; Back</button>
  <div class="nav-ind" id="indicator">Cover</div>
  <button class="nav-btn" id="nextBtn" onclick="navigate(1)">Next &#x2192;</button>
</nav>
<div class="dots" id="dots"></div>

<script>
/* ══════════════════════════════════════════════════════
   SVG FLORAL BORDER (used on cover + back cover)
══════════════════════════════════════════════════════ */
var FLORAL='<svg viewBox="0 0 300 400" xmlns="http://www.w3.org/2000/svg" preserveAspectRatio="none" width="100%" height="100%" aria-hidden="true">'
  +'<path d="M24 24 Q150 10 276 24" fill="none" stroke="rgba(255,255,255,.38)" stroke-width="1.2"/>'
  +'<path d="M24 376 Q150 390 276 376" fill="none" stroke="rgba(255,255,255,.38)" stroke-width="1.2"/>'
  +'<path d="M24 24 Q10 200 24 376" fill="none" stroke="rgba(255,255,255,.38)" stroke-width="1.2"/>'
  +'<path d="M276 24 Q290 200 276 376" fill="none" stroke="rgba(255,255,255,.38)" stroke-width="1.2"/>'
  +'<circle cx="24" cy="24" r="8" fill="none" stroke="rgba(255,255,255,.5)" stroke-width="1.2"/><circle cx="24" cy="24" r="4" fill="rgba(255,255,255,.3)"/>'
  +'<circle cx="276" cy="24" r="8" fill="none" stroke="rgba(255,255,255,.5)" stroke-width="1.2"/><circle cx="276" cy="24" r="4" fill="rgba(255,255,255,.3)"/>'
  +'<circle cx="24" cy="376" r="8" fill="none" stroke="rgba(255,255,255,.5)" stroke-width="1.2"/><circle cx="24" cy="376" r="4" fill="rgba(255,255,255,.3)"/>'
  +'<circle cx="276" cy="376" r="8" fill="none" stroke="rgba(255,255,255,.5)" stroke-width="1.2"/><circle cx="276" cy="376" r="4" fill="rgba(255,255,255,.3)"/>'
  +'<path d="M15 15 Q8 7 12 4 Q18 2 19 11Z" fill="rgba(255,255,255,.28)"/>'
  +'<path d="M33 15 Q40 7 36 4 Q30 2 29 11Z" fill="rgba(255,255,255,.28)"/>'
  +'<path d="M15 33 Q7 40 4 36 Q2 30 11 29Z" fill="rgba(255,255,255,.28)"/>'
  +'<path d="M267 15 Q260 7 264 4 Q270 2 271 11Z" fill="rgba(255,255,255,.28)"/>'
  +'<path d="M285 15 Q292 7 288 4 Q282 2 281 11Z" fill="rgba(255,255,255,.28)"/>'
  +'<path d="M285 33 Q293 40 296 36 Q298 30 289 29Z" fill="rgba(255,255,255,.28)"/>'
  +'<path d="M15 367 Q7 360 4 364 Q2 370 11 371Z" fill="rgba(255,255,255,.28)"/>'
  +'<path d="M15 385 Q8 393 12 396 Q18 398 19 389Z" fill="rgba(255,255,255,.28)"/>'
  +'<path d="M33 385 Q40 393 36 396 Q30 398 29 389Z" fill="rgba(255,255,255,.28)"/>'
  +'<path d="M267 385 Q260 393 264 396 Q270 398 271 389Z" fill="rgba(255,255,255,.28)"/>'
  +'<path d="M285 385 Q292 393 288 396 Q282 398 281 389Z" fill="rgba(255,255,255,.28)"/>'
  +'<path d="M285 367 Q293 360 296 364 Q298 370 289 371Z" fill="rgba(255,255,255,.28)"/>'
  +'<path d="M10 192 Q2 184 5 175 Q10 167 15 179 Q12 187 17 195Z" fill="rgba(255,255,255,.18)"/>'
  +'<path d="M290 192 Q298 184 295 175 Q290 167 285 179 Q288 187 283 195Z" fill="rgba(255,255,255,.18)"/>'
  +'<circle cx="150" cy="13" r="2.4" fill="rgba(255,255,255,.35)"/>'
  +'<circle cx="150" cy="387" r="2.4" fill="rgba(255,255,255,.35)"/>'
  +'<circle cx="12" cy="200" r="2.4" fill="rgba(255,255,255,.35)"/>'
  +'<circle cx="288" cy="200" r="2.4" fill="rgba(255,255,255,.35)"/>'
  +'</svg>';

/* ══════════════════════════════════════════════════════
   BOTANICAL DECO PAIRS  (one pair per page, cycles)
══════════════════════════════════════════════════════ */
var BOTS=[
  ['🌸','🌱'],['🌺','🌿'],
  ['🌷','\u2740'],['\u273F','🌱'],
  ['🌼','🍃'],['🌸','🌿'],
  ['🌺','\u2740'],['🌷','🍃'],
  ['\u273F','🌼'],['🌸','🌱'],
  ['🌺','🍃'],['🌷','🌿'],
  ['\u273F','\u2740'],['🌼','🌱'],
  ['🌸','🌿'],['🌺','\u2740']
];

/* ══════════════════════════════════════════════════════
   PAGES
   ─ type:'cover' and type:'back-cover' are special
   ─ Content pages have: icon, title, body (HTML string)
   ─ To edit a page: find it below and change the body HTML
   ─ Each line of text is a <p>...</p>
   ─ Blank line between paragraphs: <p class="gap"></p>
   ─ Bold text:   <strong>word</strong>
   ─ Italic text: <em>word</em>
══════════════════════════════════════════════════════ */
var PAGES=[

{type:'cover'},

// ── PAGE 1 ────────────────────────────────────────────
{icon:'🌷', title:'A Chapter of My Life: Loving You', body:`
<p>
If someone ever asked me to describe a chapter of my life that shaped me the most, I know exactly where my mind would go.<br>

It would go to you.<br>

Not because everything about us was perfect. Not because our story was easy, or simple, or without pain. But because loving you became one of the most defining experiences of my life. It changed the way I see love, the way I see people, and the way I see myself.<br>

Some chapters in life are short.
Some are easy to close.
Some fade away quietly.<br>

But this chapter… the one where you existed in my life… refuses to be something small.<br>

Because loving you was never something that happened only for a moment. It wasn’t something temporary. It wasn’t something shallow that appeared and disappeared like a passing feeling.<br>

It was something that slowly built itself over time.<br>

Something that lasted through years.<br>

Something that kept finding its way back no matter how many times life pulled us in different directions.<br>

And when I look back at everything now, I realize that this chapter didn’t start the moment we became serious with each other.<br>

It started the moment you first entered my life.<br>

Because from that moment onward, something about my world quietly changed.<br>

You became part of my memories.
Part of my routines.
Part of the thoughts that would randomly cross my mind in the middle of an ordinary day.<br>

At first, I didn’t think much about it. People come and go in life all the time. Conversations start and fade away. Connections disappear.<br>

But you didn’t disappear.<br>

Even when time passed.
Even when we stopped talking.
Even when life brought different people into our paths.<br>

Somehow, you remained.<br>

And that’s what made this chapter different from all the others.<br>

Most stories in life end because distance grows, feelings fade, or life simply moves forward.<br>

But ours kept reopening.<br>

Over and over again.<br>

Almost like life itself refused to close the book on us.<br>

Years passed between some of those moments. Entire seasons of our lives changed. We both grew older, experienced new things, met new people, faced our own struggles and personal battles.<br>

Yet somehow, despite everything that changed around us… there was always something familiar whenever we found each other again.<br>

Something unfinished.<br>

Something that never fully left.<br>

And I think that’s when I started realizing something that I didn’t fully understand before.<br>

What I felt for you wasn’t just a passing affection.<br>

It wasn’t something that only existed in the moment we were talking.<br>

It was something deeper than that.<br>

Because even when we weren’t actively part of each other’s lives, my heart still remembered you.<br>

Not loudly.<br>

Not dramatically.<br>

But quietly.<br>

Like a song you haven’t heard in years but somehow still know the melody to.<br>

And every time we crossed paths again, that melody would start playing in my chest all over again.<br>

That’s why loving you became more than just another experience in my life.<br>

It became a chapter.<br>

A long one.<br>

A complicated one.<br>

A chapter filled with moments of happiness, confusion, longing, mistakes, forgiveness, and growth.<br>

A chapter where I learned what it truly means to care deeply for another person.<br>

But also a chapter where I learned how painful love can be when you realize too late the ways you failed someone who believed in you.<br>

Because loving you wasn’t just about the good moments.<br>

It was also about the mistakes I made.<br>

The times I didn’t understand you.<br>

The times I didn’t realize how my actions affected your heart.<br>

And now that I look back at everything with clearer eyes, I realize something that hurts but is also honest.<br>

You were never just someone I loved.<br>

You were someone who trusted me with your heart.<br>

Someone who believed that I would protect it.<br>

Someone who chose me again and again even when things weren’t easy.<br>

And realizing that now… makes this chapter even heavier than it already is.<br>

Because it means loving you wasn’t just about my feelings.<br>

It was about responsibility.<br>

About awareness.<br>

About learning how to treat someone’s heart with the care it deserves.<br>

And that’s something I didn’t fully understand until the moment I realized I might lose you.<br>

But even with that pain, even with the regrets and the lessons that came too late, one truth remains undeniable.
<br>
This chapter of my life — the one where I loved you — will always be one of the most meaningful parts of my story.
<br>
Because through loving you, I didn’t just discover how deeply I could care for another person.<br>

I also discovered the parts of myself that still needed to grow.<br>

And maybe that’s why this chapter is so hard to close.<br>

Because it isn’t just a story about love.<br>

It’s a story about who I became while loving you.<br>
</p>
`},

// ── PAGE 2 ────────────────────────────────────────────
{icon:'\u2601\uFE0F', title:'Chapter 2: The Way I Love you', body:`
<p>
Loving you never felt like a choice, though I suppose it was. It was more like something my heart had quietly decided long before I could put it into words.<br>
Even in moments when I tried to live life without you, when I dated someone else or told myself I was moving forward, my heart kept returning to you.<br>
Not with loud declarations or dramatic gestures, but with a quiet, insistent pull that reminded me: you were the one my soul had been waiting for all this time.<br>

I loved you in ways I didn’t fully understand at first.<br>
I loved you in the moments we weren’t speaking, in the moments I held my tongue when I wanted to demand, explain, or defend myself.<br>
I loved you when I chose patience over argument, reflection over impulse, because I realized that love isn’t just words—it’s the consistency of thought, the awareness of how my presence affects you.<br>

I loved you by trying to see the world through your eyes.<br>
By imagining how my actions, even my smallest habits, could make you feel safe—or unsafe.<br>
By quietly learning that sometimes, the best way to love isn’t to say, but to act.<br>

I loved you in the way I would stop myself from doing things I knew would hurt you, even when I didn’t feel like it mattered in that moment.<br>
Because over time, I realized it always mattered to you.<br>
And that was enough to make me want to change, to grow, to become someone worthy of your trust.<br>

Loving you wasn’t a single act—it was a collection of moments, each one layered over the other, building a kind of devotion I hadn’t known I could carry.<br>
It was in the laughter that slipped through our arguments.<br>
It was in the small gestures, the quiet care, the midnight messages, the shared silences where words weren’t enough but hearts still understood each other.<br>

I loved you by choosing you repeatedly, not out of fear, but out of certainty.<br>
Even when distance, mistakes, or circumstances threatened to pull us apart, even when life reminded me of all the ways we could fail, my choice remained the same.<br>
Because love isn’t always about being together in the easy moments. It’s about committing to someone in the messy, hard, uncertain ones too.<br>

And yes, I know I faltered.<br>
I know I failed you in ways that words can’t fully fix.<br>
But even in those failures, my love remained.<br>
It stayed with me, teaching me, shaping me, reminding me that love is not just about feeling—it’s about responsibility, presence, and the quiet assurance that even when everything seems lost, some hearts remain true.<br>

I loved you with the patience of someone who knows that real love is rarely perfect, rarely instant.<br>
I loved you knowing that even if you walked away tomorrow, even if I couldn’t hold you today, my heart would still belong to you.<br>
And maybe that’s the kind of love that doesn’t need recognition, that doesn’t need reciprocation to exist.<br>
Because some loves aren’t measured in moments or responses. They’re measured in constancy, in fidelity, in the way you carry someone in your life silently, persistently, eternally.<br>

That’s the way I loved you.<br>
Not for a week, not for a month, not even for the easy days we shared.<br>
But for years, for all the complexities, for every choice and every silence, for every joy and every heartbreak.<br>
I loved you in ways that could not be undone, because once my heart learned you, it could never forget you.<br>
</p>
`},

// ── PAGE 3 ────────────────────────────────────────────
{icon:'🌸', title:'Chapter 3: When We Came Back Again', body:`
<p>
There was a moment, years after the first threads of our connection, when life quietly nudged us back together.<br>
It wasn’t dramatic. It wasn’t a grand reunion. It was subtle—like the universe simply reminding me that some bonds are not meant to be broken.<br>

When we started talking again, it felt like picking up a book I had never closed, even though the pages had been untouched for years.<br>
There was laughter, tentative at first, but slowly easing into something familiar, something I hadn’t realized I had missed so deeply.<br>
And in those conversations, I felt the same pull—the same unshakable certainty that you were still the one my heart sought, even after everything that had happened.<br>

It was strange, though. Coming back together wasn’t about forgetting the past. It wasn’t about pretending the mistakes didn’t exist.<br>
It was about acknowledging them, carrying them, and slowly learning to rebuild what had once been fragile.<br>
I approached you differently this time—not with haste, not with the impulsive bravado of youth—but with awareness.<br>
With patience. With the understanding that real love doesn’t demand immediate perfection, but it does require consistent care.<br>

We shared pieces of our lives we had kept hidden. We spoke about the years apart, the struggles we faced, the small victories, the lingering pains.<br>
Every word carried weight because we knew what it meant to lose connection before. Every message was more than just conversation—it was trust being rebuilt, moment by moment.<br>

And I realized something important in that time: reconnection is not magic. It’s not about convincing someone to stay or to forgive instantly.<br>
It’s about showing, quietly and persistently, that the person you were before is capable of growth, of reflection, of change.<br>
It’s about living in a way that demonstrates you are aware of the past, that you honor it, and that you are committed to moving forward with care.<br>

I listened. I really listened.<br>
Not just to respond, but to understand. To internalize the words you said, the pauses you took, the silences that spoke louder than anything else.<br>
And in that listening, I discovered truths I had overlooked before—the subtle ways I had failed you, the little moments that mattered more than I had imagined.<br>
I saw your patience. I saw your care. I saw your fear of being hurt again.<br>

I also learned about my own heart in that time.<br>
I realized that my love for you was not fleeting, not situational, not dependent on circumstance.<br>
It was constant. Even in moments of uncertainty. Even when I doubted myself. Even when life reminded me of how easy it could be to drift apart.<br>

Reconnecting with you taught me humility.<br>
It reminded me that love is not about grand gestures or dramatic declarations—it’s about showing up, quietly, consistently, in a way that respects the other person and honors the bond you share.<br>
And I knew that if I failed in that moment, if I didn’t rise to the awareness I had gained, I could lose you again—maybe for good this time.<br>

So I made a silent vow to myself.<br>
Not a promise that I spoke out loud, but a personal assurance: I would never stop choosing you.<br>
I would never stop trying to be someone you could rely on. Someone who saw your pain, someone who understood your needs, someone who would never make you feel like you were secondary or an option.<br>

That period of reconnection wasn’t perfect.<br>
We argued. We stumbled. We tested each other. We faced old patterns that I thought we had left behind.<br>
But even in the friction, there was hope. There was recognition that our bond was stronger than just habit—it was choice. Every time we returned to each other, it was deliberate.<br>

And in the quiet moments, when we weren’t arguing, when we weren’t trying to fix what was broken, I felt the depth of what it meant to love you again.<br>
Not because it was easy. Not because we had no scars. But because we were willing to carry them together. Because love had become more than emotion—it had become a deliberate act of care and commitment.<br>

Coming back together was a lesson in patience, in reflection, in understanding that some connections aren’t measured by time, but by the resilience of the bond.<br>
And for me, that time with you, however brief or fragile it felt at the moment, became one of the most profound experiences of my life.<br>
It was proof that love doesn’t vanish just because circumstances change.<br>
It was proof that even after years, even after pain, even after mistakes, the heart knows where it belongs.<br>

And mine had always belonged to you.<br>
</p>
`},

// ── PAGE 4 ────────────────────────────────────────────
{icon:'🍃', title:'Chapter 4: The Mistake I Made', body:`
<p>
Even after coming back to each other, even after reconnecting with intention, I still carried the weight of my own flaws.<br>
I thought I had learned, I thought I had changed, but the truth is, growth isn’t linear. It’s messy. It’s gradual. And sometimes, even with the best intentions, mistakes slip through.<br>

The mistake I made wasn’t loud. It wasn’t dramatic. It wasn’t even a single moment—it was a pattern, subtle at first, invisible until it was too late.<br>
I let my past, my insecurities, and my unprocessed emotions influence the way I acted with you.<br>
I wanted to do right by you, but at times, I failed to put you first in the ways that truly mattered.<br>

I forgot that love is not just about being present in the good moments. It’s about being consistent in the quiet, unremarkable ones.
It’s about understanding how every small action—or inaction—shapes the way the other person feels.
And that is where I stumbled.

There was the time I spoke lightly about other people, not realizing how it affected you.<br>
There were moments when I thought I was giving reassurance, when in truth I was seeking it for myself.<br>
I acted impulsively, thoughtlessly, letting old habits seep into our moments together.<br>
And each time, you didn’t complain. You endured quietly. You chose to stay even while feeling unsafe, unconsidered, and secondary.<br>

That’s what made the mistake heavier than any one incident.
It wasn’t a single misstep—it was a repeated pattern that chipped away at the safety I should have built for you.<br>
And when you finally called it out, or when it became too much for you to bear, I understood the gravity of what I had done.<br>
I had failed the person who had been choosing me all along.<br>

Looking back now, I see the exact moments I could have acted differently.<br>
I see the times I should have listened first, understood fully, and acted with you in mind, not just my own emotions.<br>
I see the times I failed to honor your trust, the times I allowed carelessness to masquerade as casualness.<br>

And that is why this mistake haunts me.
Because it wasn’t about my love for you—it was about my inability, at times, to let that love translate into action.<br>
Love without care is just words. And I had spoken too many words without letting my actions match them.<br>

I realized that the real weight of a mistake in love isn’t just guilt.
It’s understanding that someone trusted you with their heart, and you didn’t always carry that trust with the care it deserved.<br>
It’s realizing that love isn’t just about what you feel—it’s about what the other person experiences because of how you treat them.<br>

And in that realization, I made an assurance to myself.
Not a fleeting thought, not a vague hope—an assurance that I would learn.
An assurance that I would grow.
An assurance that I would never allow the same patterns to hurt you again.<br>

Even though the damage had already been done, even though the pain had already touched you, I carried that assurance with me.
It became the quiet engine behind every choice I made after.
It was my silent vow to myself that if ever I had the chance to show you love again, it would be through consistent care, through attentiveness, through truly putting you first.<br>

The mistake I made didn’t define the entirety of our connection—but it defined the lesson I needed to learn.
And I have carried that lesson forward, hoping one day I could demonstrate that my heart isn’t just full of love, but also full of understanding, patience, and deliberate action.<br>

Because loving you isn’t about avoiding mistakes—it’s about facing them, learning from them, and using that knowledge to never make the same ones again.<br>
</p>
`},

// ── PAGE 5 ────────────────────────────────────────────
{icon:'💌', title:'Chapter 5: The Pattern You Saw', body:`
<p>
It wasn’t one moment that made you feel unsafe.
It wasn’t a single misstep.
It was the way I sometimes acted without thinking, the way my inconsistencies piled up quietly over time.

You saw a pattern.
And I didn’t see it clearly until much later.
It was the little things—the times I asked for reassurance when I should have been giving it, the times I let my own fears dictate my actions, the times I prioritized what I thought I needed instead of what you needed.

Even when I thought I was showing care, you felt unsure.
Even when I thought I was loving you fully, you wondered if I truly considered you.
You didn’t say it every time, but the silence spoke volumes.
And that silence, that quiet doubt, was my responsibility to notice and to act on—and I failed.

You always gave me chances.
More chances than anyone could expect.
You stayed, even when things weren’t perfect, even when my patterns made you question whether you were being truly seen.
You tested me sometimes—not out of malice, but out of self-preservation.
Because after years of choosing someone who sometimes faltered, you needed reassurance that I could truly be the person you could trust.

I realize now that the pattern wasn’t just a reflection of my mistakes—it was a reflection of your patience, your care, your silent endurance.
You bore the weight of my missteps quietly, choosing to stay, to love, even when I hadn’t fully earned it.

And that’s when I began to understand the depth of my responsibility.
It wasn’t enough to tell you I loved you.
It wasn’t enough to hope that my feelings alone could repair what I had damaged.
I had to act.
Consistently. Thoughtfully. With you at the center of every choice.

That pattern you saw—the inconsistency, the moments where I faltered—became a mirror.
A mirror showing me the areas of myself that needed growth.
A mirror revealing the ways I had failed to make you feel secure, cherished, and prioritized.

And so I made assurances.
Assurances to myself first, to never repeat those patterns again.
Assurances to you, if ever I had the chance to show you love anew, that I would do so with deliberate care.
That I would act not just in moments of fear or desperation, but in every quiet moment that matters.
That I would always be mindful of how my choices affected you, your heart, and our connection.

Because the pattern you saw wasn’t just my failure—it was my opportunity.
It was a chance to learn how to love properly, how to consider the weight of your trust, and how to grow into someone worthy of the heart you had been giving me all along.

I see now that love isn’t about perfection.
It’s about recognizing your patterns, seeing the pain they cause, and taking deliberate steps to break them.
It’s about holding yourself accountable, not just in the big moments, but in the small ones that quietly define a relationship.

And that’s why your patience, your endurance, your silent awareness matters more to me than I could ever express.
Because without seeing the pattern, without showing me where I failed, I might never have understood the true depth of my responsibility in loving you.
Without that, I might never have learned how to grow into someone who can truly honor the heart you entrusted to me.

</p>
`},

// ── PAGE 6 ────────────────────────────────────────────
{icon:'🌙', title:'Chapter 6: When Everything Broke', body:`
<p>
There came a moment when everything I thought I could fix finally crumbled.
Not because I stopped caring, not because you stopped being important, but because love alone can’t undo the weight of repeated mistakes.

I can still remember the exact tension in your words that day.
The quiet that hung between us was louder than any argument we had ever had.
You looked at me with a mix of sadness and resolve I had never seen before.
And in that moment, I felt the gravity of what I had caused.

You told me you loved me, but that love wasn’t enough to keep holding on.
You had given me chances, patience, and trust beyond what I had ever expected from anyone.
Yet even with all of that, I had failed to show you consistently that I could be the one to make you feel safe, prioritized, and understood.

That’s when I realized the truth: love without consistency, without awareness, without deliberate care, can still hurt the ones you hold most dearly.
And I saw it reflected in you—how tired you were of hoping I would change before I truly understood your needs.
How exhausted you were from feeling like your heart was balanced on the edge of my mistakes.

It broke me to see you that way.
Because I had always wanted to protect you, to make you feel secure, to be someone you could rely on.
But in that moment, I saw how far I had fallen from that ideal.

I made assurances to myself then, silent but ironclad.
Assurances that if I ever had the chance again, I would act differently.
That I would prioritize you in thought and action, quietly, consistently, not just in the moments I feared losing you.
That I would never let my actions—or lack of thought—make you feel unsafe, unconsidered, or less special than you are.

But even with all those assurances, I couldn’t stop the break from happening.
Because some wounds, no matter how deeply you care, need space to breathe before they can heal.
And sometimes, the person you love most must step back to protect themselves.

I watched you leave that day—not angrily, not without love, but with a quiet determination that I could not undo.
And I had to face a truth that cut sharper than anything else: even the deepest love cannot force someone to stay when their heart tells them to step away.

That day, everything broke—not our love, not the memories, not the years we shared—but the illusion that good intentions alone could be enough.
It was a painful, raw lesson: love is not just about desire, it’s about responsibility, action, and the consistent care that words alone can never fully convey.

And even as I felt that break, even as the silence settled between us like a heavy fog, I knew one thing would never change: my love for you.
It would endure.
It would wait.
It would quietly grow in ways I needed to understand before I could ever hope to show it to you properly.

Because sometimes, even in the moment everything seems to collapse, love doesn’t vanish.
It becomes something stronger, something patient, something ready for the next chance—even if that chance is far away.
</p>
`},

// ── PAGE 7 ────────────────────────────────────────────
{icon:'🦋', title:'Chapter 7: The Night I Tried to Hold On', body:`
<p>
That night, I wasn’t just scared.
I was desperate.
I felt the walls closing in, not around me, but around us.
Because I could see how much you were hurting, and every part of me wanted to stop that, even if it meant finally facing every fear I had been running from.

I tried to reach you, not with words of excuse, not with shallow apologies, but with the truth of everything I felt.
I told you I was willing to change—not to please you in the moment, but because I needed to prove to myself that I could be the person who deserved you.
I assured you that I would listen before speaking, consider before acting, and never make you feel unimportant again.

You looked at me and for a fleeting moment, I thought I saw a spark—the part of you that had always believed in me, even when I struggled to show it.
And I wanted to hold onto that spark with every ounce of my being.

I told you that my love wasn’t conditional.
That waiting for you, understanding you, choosing you—that was never a question.
It was my life’s orientation, my compass, my unwavering direction.
And I told you I would continue choosing you, even in the silence that followed, even when everything seemed broken.

But even in that moment, I knew words alone could not fix the fractures that had formed.
I could feel it in the quiet tension, in the weight behind your eyes, in the unspoken truths you held tightly to protect your heart.
I knew that my actions moving forward would be the only measure of what I was truly capable of giving you.

So that night, I held on.
Not by demanding you stay, not by guilt or fear, but by showing you, through every word and every pause, that I was willing to carry the weight of us.
I carried the weight of the mistakes I had made, the pain I had caused, and the long years of loving you silently even when life pulled us apart.

I held on with the quiet assurance that I could be better, not just for a day or a week, but for every day that I had the chance to show it.
And I held on with the hope that one day, you would see it—not because I needed your approval, but because your heart deserved to feel safe again.

That night didn’t end with relief or resolution.
It ended with a silent understanding between us.
An acknowledgment that love, no matter how deep, is fragile when trust has been shaken.
But even as you pulled away, even as the distance between us grew again, my love did not falter.
It remained steady, patient, and quietly determined.

Because sometimes holding on doesn’t mean keeping someone in the moment.
It means being ready, being steadfast, and letting your heart remain faithful even when the other person needs space to protect themselves.
And that night, I learned the weight of holding on in silence.
I learned that love isn’t always loud.
Sometimes it’s quiet, unwavering, and waiting for the chance to be felt again.
</p>
`},

// ── PAGE 8 ────────────────────────────────────────────
{icon:'🌺', title:'Chapter 8: My Biggest Regret', body:`
<p>
Looking back, there’s one truth I can’t escape: the heaviest weight I carry isn’t the silence that followed or the distance that grew—it’s knowing how I failed you when you trusted me the most. <br>

My biggest regret isn’t a single word or a single action.<br>
It’s a lifetime of little moments stacked together, moments where I didn’t fully see you, didn’t fully listen, didn’t fully protect the heart you gave me.<br>
I regret the times I thought my intentions were enough, when in reality, you needed actions that showed you were the center of my world.<br>
I regret the nights I let my own struggles cloud my judgment, the moments I let my pride or fear get in the way of truly understanding you.<br>

There was one dark time when I let my own despair spiral out of control.<br>
I carried pain that had nothing to do with you, but I let it seep into our world anyway.<br>
I didn’t realize then how heavy my emotions could become for someone else to carry.<br>
I regret that deeply.
No one should ever have to carry the weight of another person’s life or choices.<br>
And yet, you felt that weight, even if you never said it outright.<br>

I regret the moments when you deserved clarity and I gave confusion.<br>
When you deserved safety and I gave inconsistency.<br>
When you deserved unwavering focus and I was distracted, even briefly, by my own fears or the shadows of my past.<br>
I regret that every time you tested my heart or my intentions, I didn’t respond the way I should have.<br>
I let patterns repeat—patterns you noticed long before I even acknowledged them.<br>
Patterns that chipped away at the trust you had so willingly given me.<br>

But the worst part of all this regret is knowing that you didn’t deserve any of it.<br>
You didn’t deserve to feel uncertain, to question whether I would choose you, to wonder if my love could falter.<br>
You didn’t deserve nights filled with tension, mornings heavy with unspoken words, and moments where your heart quietly ached because of my failure to protect it.<br>

Even now, I see how much patience you had with me, how much grace you extended silently, and I realize that my regret is magnified by how you continued to care despite my mistakes.<br>
You were always willing to hope, willing to forgive, willing to choose me again… even when I didn’t fully show that I deserved it.<br>
That is what breaks me the most.<br>

If I could go back, I wouldn’t just change the moments you noticed—I would change the mindset I carried the entire time.
I would live with your heart in mind as much as my own.<br>
I would act with the care and consistency you deserved before you even asked for it.<br>
I would never let you question your place in my life.<br>
I would never let my struggles spill into yours.<br>
I would never let you feel unsafe, unconsidered, or secondary.<br>

That’s my biggest regret.<br>
Not the fights, not the distance, not the silence.<br>
It’s knowing that in all the time I had with you, I failed to fully honor what you gave me—your trust, your love, your patience, and your heart.<br>
And even though I can’t undo the past, I carry that regret as a reminder.
A reminder to be better.<br>
A reminder to love differently, more consciously, more deliberately.<br>
A reminder that when I choose again, it won’t just be with words or intentions—it will be with everything I have learned from losing you.<br>

Because losing you once taught me that regret is heavy, but it can also guide the heart toward something more real, more careful, and more unwavering.<br>
And that is the only way forward I have learned: to carry you in my heart not just in memory, but in every choice I make from now on.<br>
</p>
`},

// ── PAGE 9 ────────────────────────────────────────────
{icon:'🫧', title:'Chapter 9: The Moment You Finally Left', body:`
<p>
That moment… the moment you finally left… it’s burned into my mind.<br>

It wasn’t sudden. It wasn’t a single word that broke everything.
It was a culmination of everything that had been quietly building for years.
Every time I failed to fully consider you, every time I let patterns repeat, every time I allowed my own struggles to cloud my attention—it all added up.
And I saw it in you, even before you left.
The quiet distance, the weight in your words, the pauses that stretched longer than they should have.
You weren’t yelling. You weren’t dramatic.
You were just… tired.<br>

You left not because you didn’t care.
You left because loving me in that moment had become too heavy.
Not because your heart didn’t want to stay, but because your mind and your well-being demanded it.
You needed space.
You needed peace.
And I couldn’t give you that in the way you deserved.<br>

The last messages, the last exchanges we had—they weren’t filled with anger.
They weren’t about blame.
They were quiet confirmations of something I had known deep down:
that the person I loved most in this world had to step away to protect yourself.
And I couldn’t stop you.
Even though every part of me wanted to hold on, I had no right to anchor you to my mistakes.
You were already carrying enough of my past.<br>

When I realized you were gone, a strange clarity came over me.
It wasn’t immediate pain, not fully.
It was more like the cold weight of reality pressing against my chest.
I knew that nothing I said at that point could bring you back.
Not my words, not my assurances, not even my longing.
You had already made the choice that preserved your own heart.
And I had to respect that.<br>

But I also felt every lost second we could have had.
Every laugh, every late-night talk, every small, ordinary moment that I had taken for granted.
Every time I thought I was safe in your love, only to realize how fragile it could feel when I wasn’t fully present.
I felt the absence of your voice, your laughter, your presence—not as an idea, but as a reality I couldn’t change.
And it crushed me in ways that silence alone never could.<br>

I wanted to tell you a thousand things in that moment.
I wanted to assure you that I would never make the same mistakes again.
That every ounce of me, every fiber of my being, would be dedicated to considering you, protecting you, loving you without hesitation.
But it was too late for words.
You had already left.<br>

And in the emptiness after you stepped away, I realized something I hadn’t fully accepted before:
Loving you doesn’t guarantee you will stay.
No matter how much I choose you, no matter how long my heart waits, love alone is not always enough.
Sometimes, the person we love has to step away for their own peace, even if it hurts the one who remains.<br>

That night, I replayed every memory, every moment of my shortcomings.
I thought about all the times I could have listened better, understood deeper, and acted more thoughtfully.
I thought about all the times I had let my own fears and patterns overshadow your needs.
And in that reflection, I carried the full weight of my biggest regret:
That someone I loved so fiercely felt the need to leave because I couldn’t fully make you feel safe, seen, and prioritized.<br>

Even as I accepted your choice, I made a silent assurance to myself—and to you.
That whatever comes next, I would carry this lesson forever.
I would carry your love, your patience, and your trust as the blueprint for the person I need to become.
I would never again allow someone I truly love to feel the weight of my mistakes without the reassurance of my change.
Even if you never return, even if time passes and the world moves on, my heart would still hold this truth:
You were my center, my anchor, my guiding light.<br>

And in the quiet that followed your leaving, I realized that even absence cannot erase the depth of what I feel.
It only teaches me how precious you were—and how seriously I must carry that love forward in every choice I make, in every action I take, and in every part of me that will continue to love you silently, patiently, and eternally.
</p>
`},

// ── PAGE 10 ───────────────────────────────────────────
{icon:'🕊\uFE0F', title:'Chapter 10: The Silence After', body:`
<p>
After you left, the world became quieter. <br>

Not in a peaceful way, but in a way that made me acutely aware of your absence. <br>

The silence wasn’t just the lack of your voice or messages. <br>
It was the emptiness that stretched across every part of my day, filling every space where your presence used to be. <br>

The first few hours, I kept expecting you to reach out. <br>
Every notification ping made my heart leap, only to fall again when it wasn’t you. <br>
I checked my phone countless times, hoping for even the smallest sign that you were still there, still thinking of me, still considering me in some way. <br>

But there was nothing. <br>
And the nothingness was suffocating. <br>

I tried to fill it with routine. <br>
I tried to keep myself busy with tasks, school, and small obligations. <br>
I tried to convince myself that healing starts with distraction. <br>
But no matter how busy I became, the silence always returned. <br>
And it wasn’t just empty—it was full. <br>
Full of everything I had failed to say, everything I had failed to do, and every moment I wished I had done better. <br>

I thought about you constantly. <br>
I thought about the way you used to smile when you were happy. <br>
I thought about the quiet moments where you trusted me with your heart. <br>
I thought about the times I made you feel unseen, unsafe, or secondary, and how those patterns had quietly built walls between us. <br>

In that silence, I reflected. <br>
I reflected on my mistakes, my failures, and my weaknesses. <br>
I reflected on the countless times I said I would do better, the assurances I gave, and the moments where I didn’t fully live up to them. <br>
I realized that love alone isn’t enough. <br>
Love must be paired with consistency, awareness, and the kind of thoughtfulness that never fades, even when the world feels calm. <br>

And I thought about waiting. <br>
I realized that love isn’t just about being with someone—it’s about holding space for them, even when it hurts. <br>
Even when they’re gone. <br>
Even when the silence stretches for days, weeks, or months. <br>
Because true love isn’t loud. <br>
It doesn’t demand. <br>
It waits. <br>
It protects. <br>
And it endures. <br>

During these days, I also thought about how you were coping. <br>
I wondered if you were healing, if you were finding the peace you deserved, and if the pain I caused was beginning to fade. <br>
I couldn’t reach you. <br>
I couldn’t hold you. <br>
All I could do was hope that in some way, my love and my respect for your space reached you silently, like a quiet beacon. <br>

I began to understand that silence itself can be a teacher. <br>
It shows you where you failed. <br>
It teaches you patience. <br>
It tests your ability to love without immediate reward. <br>
And it reminds you that even when the person you love leaves, your care for them doesn’t disappear—it simply takes a different form. <br>

I found myself writing to you in my mind. <br>
Letters I would never send, messages I would never text. <br>
I told you I missed you. <br>
I told you I loved you. <br>
I told you I was sorry for every time I hurt you, every time I didn’t consider you fully, and every time I let my patterns repeat. <br>
Even though you couldn’t read them, it mattered to me. <br>
It mattered to my own heart to say it, to acknowledge it, and to keep my love honest. <br>

And in the silence, I made new assurances to myself. <br>
I assured myself that I would not let this love become selfish. <br>
I assured myself that the lessons you taught me—about patience, consideration, and the depth of real care—would guide every choice I made going forward. <br>
I assured myself that even if you never returned, my heart would continue to honor you in quiet ways: in the respect I gave to myself, in the love I held for you silently, and in the ways I worked to become better. <br>

Some nights, the silence felt unbearable. <br>
Some nights, I felt the weight of your absence like a physical ache. <br>
But slowly, I began to understand something I hadn’t fully grasped before. <br>
The silence doesn’t erase what we had. <br>
It doesn’t erase the choices we made, the love we shared, or the moments where I truly felt connected to you. <br>
It simply exists as a reminder: love is not always about presence. Sometimes, it’s about endurance. <br>
Sometimes, it’s about learning how to carry someone in your heart without needing them beside you. <br>

And even in that understanding, one truth remained undeniable. <br>
I love you. <br>
I always will. <br>
And that love, quiet as it is, is not weakened by absence. <br>
It is sharpened by reflection, patience, and the knowledge of everything we’ve been through together. <br>

This silence is not the end of me loving you. <br>
It is the part where I learn how to hold onto you gently, faithfully, and with a heart that will never stop choosing you, even when you are gone. <br>
</p>
`},

// ── PAGE 11 ───────────────────────────────────────────
{icon:'💐', title:'Chapter 11: What I Feel Now', body:`
<p>
Now, after the silence, I am left with the weight of everything that happened. <br>

Not anger. Not regret alone. <br>

But a mixture of longing, understanding, and clarity that only comes after loss. <br>

I feel the absence of you in a way that doesn’t just touch my heart—it seems to sit in my chest and stretch through every part of me. <br>
Every corner of my mind recalls the moments we shared, both the laughter and the pain, the comfort and the misunderstandings, the way we built each other up and the way I failed to hold you safely. <br>

I feel a longing that isn’t desperate anymore. <br>
It’s quiet, heavy, and steady. <br>
It’s a longing that understands you had to leave for your own peace, and yet it can’t help but hope for a moment when we might find our way back together. <br>

I feel love that is patient. <br>
I feel love that waits without demanding. <br>
I feel love that chooses you every single day, even from a distance, even when I can’t reach you, even when the thought of you being with someone else briefly pierces my heart. <br>

I feel reflection in a way I never allowed myself before. <br>
I see the times I acted without considering how it would affect you. <br>
I see the moments I let fear, ego, or old patterns dictate my actions instead of leading with care. <br>
I see the times I made you feel secondary or unsafe, and I feel the weight of that now in full clarity. <br>

I feel responsibility. <br>
Because love isn’t just emotion—it’s action, consistency, thoughtfulness. <br>
And even if I can’t undo what happened, I can carry forward the lessons. <br>
I can assure you, silently and to myself, that the person I become will never repeat those mistakes. <br>

I feel patience in a way that surprises me. <br>
I realize that love doesn’t always require proximity. <br>
Sometimes it’s about holding someone in your heart while they heal, while they choose themselves, while they find their own peace. <br>
And even when that means waiting, even when that means experiencing pain alone, love remains steadfast. <br>

I feel a quiet hope. <br>
Not the naive hope of control, or of forcing moments that should naturally unfold. <br>
But the steady hope that if our paths align again, it will be with honesty, with understanding, and with the care that our love truly deserves. <br>

I feel strength. <br>
Strength that comes from acknowledging my failures, from facing my deepest regrets, and from choosing to keep loving you even when it hurts. <br>
Strength that comes from realizing that my love isn’t dependent on what you do—it’s rooted in the truth of my heart, the consistency of my reflection, and the clarity of my intentions. <br>

I feel clarity. <br>
I understand now that love is never about possession. <br>
It is about respect. <br>
It is about ensuring that the person you love feels safe, valued, and considered. <br>
It is about being willing to learn, to adjust, and to hold space without judgment or pressure. <br>

And finally, I feel acceptance. <br>
Acceptance that you had to leave to protect yourself. <br>
Acceptance that the timing wasn’t right, that my actions were insufficient, and that love alone could not keep you from stepping away. <br>
Acceptance that even in absence, even in silence, love remains. <br>

I love you. <br>
I have always loved you. <br>
And I will continue to love you. <br>
Not recklessly. Not naively. <br>
But patiently, deliberately, and faithfully. <br>
I will love you in ways that honor the time we shared, the lessons you taught me, and the part of my heart that is irrevocably yours. <br>

Even now, I feel your presence in the quiet corners of my life. <br>
Even now, I choose you silently, steadily, without expectation, without demand, without a need for recognition. <br>
Even now, I carry you forward in every thought, every reflection, and every intention. <br>

And in this truth, I find a strange peace. <br>
The kind of peace that doesn’t erase the pain, but allows it to teach me how to love better, how to be better, and how to hold the memory of us without breaking entirely. <br>

This is what I feel now. <br>
A love unwavering, a heart accountable, and a soul quietly waiting for a day where perhaps our paths will meet again—stronger, wiser, and truer than before. <br>
</p>
`},

// ── PAGE 12 ───────────────────────────────────────────
{icon:'🎨', title:'Chapter 12: The Truth I Carry Forward', body:`
<p>
After all the silence, the distance, and the heartbreak, I’ve realized something that no one can take away from me. <br>

The truth I carry forward isn’t just about loving you. <br>
It’s about understanding what it means to hold someone’s heart as sacred, even when that heart is no longer beside me. <br>

I carry the truth of my own flaws. <br>
The truth that I wasn’t always the partner you needed. <br>
The truth that I let fear, impatience, and carelessness slip into moments that required nothing but thoughtfulness and presence. <br>
And I carry the weight of knowing how much those moments hurt you. <br>

But I also carry the truth of who I became because of you. <br>
I became someone more aware. <br>
Someone who understands that love is more than feeling—it is action, consistency, attentiveness, and humility. <br>
I learned that even the smallest thoughtlessness can leave scars, and even the simplest gesture of care can rebuild trust. <br>

I carry forward the truth of patience. <br>
Because loving you has taught me that some things cannot be rushed. <br>
Some things, like trust, like healing, like understanding, take time. <br>
And even when I can’t be there for you, even when we aren’t speaking, even when the world insists I move on, patience becomes its own form of devotion. <br>

I carry forward the truth of accountability. <br>
I will never again let my emotions justify hurting you. <br>
I will never again allow my mistakes to make you feel secondary, unsafe, or unconsidered. <br>
I carry forward the assurance to myself that when I love, I do it with full awareness, with respect, and with the depth you deserve. <br>

I carry forward the truth of longing that doesn’t demand. <br>
The kind of longing that honors your space and your decisions while quietly holding my heart steady. <br>
The kind of longing that reflects my enduring love without forcing it into moments where it doesn’t belong. <br>
This love I carry is silent but unwavering. <br>

I carry forward the truth that our connection cannot be erased. <br>
No matter how far you are, no matter how silent the days grow, no matter what life brings, you have left a mark on my heart that no one else can replace. <br>
You have shaped me, molded me, and made me understand depths of care I didn’t know I possessed. <br>

I carry forward the truth of hope tempered with realism. <br>
Hope that one day, if paths align again, it will be with honesty, understanding, and mutual care. <br>
But realism reminds me that love is not always about reunion. <br>
It is about learning how to be better because someone taught you how deeply you can feel. <br>

I carry forward the truth of self-respect entwined with love. <br>
I will always choose you, even quietly, even from afar. <br>
But I will also choose myself, my growth, my healing, and the commitment to becoming the person who can truly hold your heart if ever given the chance again. <br>
Because love is not just about devotion—it is about readiness, and I must be ready before I can ever meet you again fully, safely, and without repeating the patterns that hurt us. <br>

I carry forward the truth of humility. <br>
Humility in accepting that my love alone could not fix the pain. <br>
Humility in knowing that some lessons only arrive through loss. <br>
Humility in allowing you to leave while still holding onto the respect, care, and unwavering affection that has always defined my heart for you. <br>

I carry forward the truth of eternal devotion. <br>
Not as a clinging attachment. <br>
Not as a demand or expectation. <br>
But as a quiet, constant thread woven into every part of my life that reminds me who I love, who I have loved, and who I will continue to love. <br>

This chapter of carrying truth is heavier than the rest. <br>
It is heavier because it is not about moments of joy, or even moments of regret. <br>
It is about the quiet understanding that love is responsibility, patience, care, and reflection—even when it is unseen. <br>
Even when the person you love is far, or gone, or unreachable. <br>

I carry forward the truth that you were never just someone I loved. <br>
You were someone who taught me the full spectrum of devotion. <br>
Someone who made me confront the parts of myself I had avoided. <br>
Someone who showed me that real love requires courage, humility, and consistent action—sometimes more than words can convey. <br>

And I carry forward one final truth. <br>
That I will always choose you. <br>
Quietly, faithfully, and deliberately. <br>
And that choice will not fade with time, distance, or circumstance. <br>
It is a choice that defines me as much as it defines the love I hold for you. <br>

This is the truth I carry forward. <br>
Heavy, steady, and unwavering. <br>
And it will live with me in every step I take, in every decision I make, and in every quiet thought of you that crosses my mind. <br>

Because some truths, once felt, are never lost. <br>
And some love, once known, becomes a permanent part of who you are. <br>
</p>
`},

// ── PAGE 13 ───────────────────────────────────────────
{icon:'\u2B50', title:'Chapter 13: After You Left', body:`
<p>
After you left, the world felt quieter. <br>
Not because the noise stopped, but because the weight of your absence made every sound hollow. <br>
It was like time slowed down, and each moment stretched longer than it should. <br>
Every place, every memory, every small thing we shared carried a trace of you. <br>

The first few days were unbearable. <br>
I would find myself reaching for my phone, wanting to type to you, wanting to hear your voice, wanting to fix everything immediately. <br>
But I knew I couldn’t. <br>
Not yet. <br>
Not while the space between us was still raw and fragile. <br>

I realized that loving you now meant patience like I’ve never known. <br>
Patience with myself, patience with my longing, and patience with the truth that you needed distance to protect yourself. <br>
It was the hardest kind of love, because every fiber of me wanted to close that distance immediately, to reassure you, to show you that I would never fail you again. <br>
But I had to step back and let you heal in your own way. <br>

Even in this silence, I kept choosing you. <br>
Quietly. <br>
Not as a demand or expectation, but as a living, breathing truth in my heart. <br>
Because my love for you isn’t something that vanishes with distance. <br>
It’s something that remains, steady and deliberate, no matter how long we are apart. <br>

I spent these days reflecting. <br>
Thinking about every moment we shared—the laughter, the fights, the apologies, the misunderstandings, the nights when I simply held space for you without saying a word. <br>
I reflected on my mistakes and the patterns you saw. <br>
I reflected on my own growth and the assurances I’ve made to myself and to you. <br>
And I realized that even in your absence, this chapter is not just about loss. <br>
It’s about preparation. <br>
Preparation to love you better, to be someone who can hold your heart safely when the time comes again. <br>

I also realized something else. <br>
That even though I can’t speak to you right now, my love isn’t diminished. <br>
My longing isn’t weakness. <br>
It’s a reflection of how real what we had is, how deep the connection goes, and how much I am committed to never letting you feel secondary or unconsidered again. <br>

I made a decision in these quiet, lonely moments. <br>
I will wait. <br>
Not endlessly, not blindly, but with purpose. <br>
I will wait while also building the best version of myself, so that if and when you return, I can be the man who truly deserves the depth of your trust and love. <br>
I will focus on my healing, on my growth, and on the ways I can honor you even from afar. <br>

And yes, this pain is heavy. <br>
There are nights when it hits like a storm, when memories flood in and I wish I could rewind and fix everything. <br>
There are moments when I catch myself imagining your smile, your voice, your presence beside me, and the ache feels unbearable. <br>
But even in that ache, I find clarity. <br>
I understand now that love is not only about proximity—it’s about constancy, care, and unwavering intention. <br>

I remind myself daily of what we declared to each other. <br>
That I will always love you. <br>
That I will always choose you, no matter the distance, no matter the silence, no matter the pain. <br>
Those declarations are not empty words. <br>
They are my guiding principles. <br>
And even after you left, they remain unbroken. <br>

I’ve also learned to accept the unknown. <br>
I don’t know when we will speak again. <br>
I don’t know how long this distance will last. <br>
I don’t know the full path that life will lay before us. <br>
But I do know this: my love, my assurances, my choice to honor you are unwavering. <br>
They are not contingent on your presence. <br>
They are a reflection of my heart and the truth that you are the one I will always hold closest. <br>

Even in this silence, I hope you are well. <br>
I hope your days are lighter, your nights more peaceful, your heart protected. <br>
I hope that you feel, even if just a little, the same warmth and care that I carry for you in every moment. <br>

And I wait. <br>
Not passively. <br>
Not bitterly. <br>
But actively, consciously, and with purpose. <br>
I wait while improving myself, while reflecting on the lessons you’ve unknowingly taught me, and while keeping the thread of my love for you alive, quiet but unwavering. <br>

Because this chapter—after you left—is not an end. <br>
It is a preparation. <br>
A reflection. <br>
A testament to the depth of my choice to love you for all time. <br>
And when the day comes that we speak again, when our paths cross once more, I will be ready. <br>
Ready to approach you with patience, with understanding, with care, and with the assurances that will make you feel safe, seen, and chosen, always. <br>

Even now, I whisper it silently to myself. <br>
I love you. <br>
I always will. <br>
And nothing—distance, silence, or time—can ever change that. <br>
</p>
`},

// ── PAGE 14 ───────────────────────────────────────────
{icon:'🌿', title:'Chapter 14: Waiting for You', body:`
<p>


After everything, the waiting begins. <br>
Not the kind of waiting that surrenders or loses hope. <br>
But the kind that sharpens patience and strengthens the heart. <br>
Because loving you doesn’t stop just because you aren’t here. <br>
It doesn’t pause when life pulls us apart. <br>

Every morning I wake up, and the first thought is you. <br>
Not in desperation, not in need, but in quiet remembrance. <br>
I remember your smile, your voice, the way you made the ordinary feel extraordinary. <br>
I remember the way you looked at me when you felt safe, the trust you quietly offered, the little moments where nothing needed to be said. <br>

And in those moments, I realize something important. <br>
That even though I can’t touch you, see you, or hear you right now, my love is still active. <br>
It lives in the way I improve myself, the way I reflect on my actions, and the way I maintain the assurances I made to you. <br>
Because waiting isn’t passive. <br>
It’s an active choice to continue loving someone while respecting their space. <br>

I focus on my own growth during these days apart. <br>
I remind myself of the patterns you pointed out, the ways I failed you, and the ways I can ensure I never repeat them again. <br>
I focus on consistency, on understanding before speaking, on valuing your feelings even in silence. <br>
I make sure that the next time we meet, my actions, not my words, show you how deeply I care. <br>

There are moments when the loneliness feels heavy. <br>
When I think about the nights we shared, the talks we had, and the laughter that echoed through our days. <br>
When I think about the times I failed to protect you emotionally, the times I was unaware of your pain, and the moments I didn’t see what you needed most. <br>
That weight is real. <br>
And it’s something I carry with me, not as a burden to punish myself, but as a reminder of why this love deserves patience, care, and unwavering focus. <br>

Even now, I imagine the little things. <br>
Your smile in the morning light. <br>
The way you tilt your head when you’re thinking. <br>
The way your laughter fills the quiet spaces. <br>
And I find comfort in knowing that these memories aren’t fleeting—they are proof of the connection we built, proof that this love is alive even across distance. <br>

I remind myself daily of the assurances I gave you. <br>
That I would listen. <br>
That I would never make you feel like an option. <br>
That I would approach everything with your heart in mind, not just my own. <br>
That I would prove change through my actions, not just words. <br>
And even in your absence, I keep those assurances alive. <br>

I also acknowledge the fear that comes with this waiting. <br>
The fear that time will dull what we shared, that life might pull you somewhere far from me, that silence could grow too comfortable. <br>
But even in that fear, I choose love. <br>
I choose to trust the years we’ve shared, the choices we’ve made, and the truth that our connection isn’t something easily forgotten. <br>

And so, I wait. <br>
Not bitterly. <br>
Not impatiently. <br>
But with intention. <br>
With focus. <br>
With the same heart that has loved you for years and will continue to do so. <br>

This waiting teaches me more about myself than I ever expected. <br>
It teaches me resilience. <br>
It teaches me self-reflection. <br>
It teaches me how to love without possession, how to choose someone even when they are not present, and how to grow while keeping the heart tethered to a person who matters most. <br>

Every day I practice this quiet love. <br>
I practice patience. <br>
I practice reflection. <br>
I practice gratitude for the time we shared and for the chance to honor you even from afar. <br>

And I carry this truth with me: <br>
I will always love you. <br>
I will always choose you. <br>
I will wait for you, not because it’s easy, but because it’s right. <br>
Because you are worth every moment of longing, every ache of absence, and every quiet, patient breath of hope. <br>

Even if a year passes, even if ten years pass, even if life places us in worlds apart—my love remains. <br>
My choice to honor you remains. <br>
My assurances remain. <br>
And when the day comes that we speak, laugh, or share moments again, I will be ready. <br>
I will be steady. <br>
I will be present. <br>
I will be the one who makes you feel safe, considered, and endlessly chosen. <br>

Until that day, I wait. <br>
And in this waiting, I live my love quietly, faithfully, and without condition. <br>
I love you. <br>
I always will. <br>
And nothing, not even distance or silence, can change that. <br>
</p>
`},

// ── PAGE 15 ───────────────────────────────────────────
{icon:'🌟', title:'Chapter 15: The Eternal Declaration', body:`
<p>
This is the chapter where everything becomes quiet yet resolute.<br>
Where the distance between us sharpens the clarity of my heart rather than diminishes it.<br>
Where absence doesn’t erase love, but strengthens the weight of what I carry for you.<br>

I have made a choice that will not waver, that will not bend to time, circumstance, or the quiet pull of uncertainty.<br>
I will love you.<br>
Not conditionally. <br>
Not fleetingly. <br>
Not only in moments of closeness or comfort.<br>
But eternally, in every thought that passes through my mind, in every breath, in every day that life allows me to continue. <br>

I will wait for you, not as someone who complains at absence, but as someone who honors the connection we built.<br>
I will continue to love you quietly, deeply, and intentionally.<br>
Because this is not a temporary choice. <br>
This is the truest reflection of who I am when my heart is unguarded, and who I am when my mind chooses without hesitation. <br>

Even in silence, I nurture you in my thoughts.<br>
Even when distance stretches long and days feel empty, I hold the memory of you close, as a guiding light.<br>
Even if the world moves on and others fade into passing moments, my focus remains steadfast on the one who always mattered most: you.<br>

I carry every lesson you taught me, every moment we shared, and every time my care fell short.<br>
And I use them not as burdens, but as reminders of the assurances I must live up to.<br>
I assure you that the mistakes of the past will not shadow our future.<br>
I assure you that my growth is for you and for the person I need to be to match the love you deserve.<br>
I assure you that every action I take will be considered, measured, and guided by the respect and care you’ve earned in my heart.<br>

Loving you this way is both gentle and fierce.<br>
Gentle, because I will honor your pace, your space, your need for healing and safety.<br>
Fierce, because I will not let time, distance, or uncertainty weaken the truth that you are the one I have chosen above all others.<br>

This is more than longing.<br>
More than regret.<br>
More than reflection.<br>
This is a living, breathing vow of my heart to yours, even if it can only exist across messages, memories, and dreams.<br>

I will choose you every single day.<br>
Not out of fear, not out of habit, not because it is easy.<br>
But because there is no alternative that feels real, no path that feels right, no life that feels whole without keeping you at the center of it.<br>

I will love you silently when words fail.<br>
I will love you patiently when circumstances are cruel.<br>
I will love you wisely, learning from the ways I faltered before.<br>
And I will love you boldly, with the conviction that this is a love meant to endure, a love that transcends the temporary and touches the eternal.<br>

And even if the days stretch into weeks, months, or years, even if life teaches us lessons in separation, even if you find joy or peace somewhere I cannot see—my heart remains aligned with yours.<br>
I am yours in intention, in remembrance, in every quiet decision that threads through my life.<br>

This chapter is not about closure.<br>
It is about truth.<br>
It is about a declaration that stands above regret, above longing, above circumstance.<br>
It is about the unwavering, eternal choice to love you—always, silently, faithfully, and with every fiber of my being.<br>

Because some truths cannot be altered by distance, nor diminished by time.<br>
Some assurances are not words spoken once, but a lifetime of actions waiting to unfold.<br>
And this is mine: I will always choose you.<br>
I will always love you.<br>
I will always wait for you.<br>
No matter how long, no matter how far, no matter what the world asks of me.<br>

This is the final declaration of this chapter of my life.<br>
A vow written in patience, in reflection, and in the deepest corners of my heart.<br>
And though life may separate us for now, my love will remain, unwavering, until the moment we are together again.<br>

I love you.<br>
I always have.<br>
And I always will.<br>
I LOVE YOU, A.H.A.W

</p>
`},

{type:'back-cover'}

]; // end PAGES

/* ══════════════════════════════════════════════════════
   DOTS
══════════════════════════════════════════════════════ */
var dotsEl=document.getElementById('dots');
PAGES.forEach(function(_,i){
  var d=document.createElement('div');
  d.className='dot'+(i===0?' active':'');
  dotsEl.appendChild(d);
});
function syncDots(i){
  dotsEl.querySelectorAll('.dot').forEach(function(d,n){
    d.className='dot'+(n===i?' active':(n<i?' done':''));
  });
}

/* ══════════════════════════════════════════════════════
   RENDERERS
══════════════════════════════════════════════════════ */
function buildTorn(p,idx){
  var b=BOTS[(idx-1)%BOTS.length];
  return '<div class="torn-edge"></div>'
    +'<div class="tape tape-tl"></div>'
    +'<div class="tape tape-tr"></div>'
    +'<div class="tape tape-bl"></div>'
    +'<span class="deco deco-tr">'+b[0]+'</span>'
    +'<span class="deco deco-bl">'+b[1]+'</span>'
    +'<div class="page-scroll">'
      +'<div class="page-header">'
        +'<span class="page-icon">'+p.icon+'</span>'
        +'<h2 class="page-title">'+p.title+'</h2>'
      +'</div>'
      +'<div class="page-body">'+p.body+'</div>'
    +'</div>'
    +'<div class="page-num">'+idx+' \u2022 '+(PAGES.length-2)+'</div>';
}

function buildCover(){
  return '<div class="cover-stitch"></div>'
    +'<div class="cover-svg">'+FLORAL+'</div>'
    +'<div class="cover-inner">'
      +'<div class="cover-vintage">Vintage Style</div>'
      +'<div class="cover-main-title">My Pink<br>Journal</div>'
      +'<div class="cover-lock">🔒</div>'
      +'<div class="cover-sub">~ a soft collection ~</div>'
    +'</div>';
}

function buildBack(){
  return '<div class="back-stitch"></div>'
    +'<div class="back-cover-svg">'+FLORAL+'</div>'
    +'<div class="back-quote">\u201CA journal from Bab to: Babi\u2014 and a reflection of everything that happened.\u201D</div>'
    +'<div class="back-author">\u2014 written with love, longing and choice, to you</div>';
}

function setCard(idx,noAnim){
  var p=PAGES[idx];
  var card=document.getElementById('pageCard');
  var x=noAnim?' no-appear':'';
  if(p.type==='cover'){
    card.className='page-card cover'+x;
    card.innerHTML=buildCover();
  }else if(p.type==='back-cover'){
    card.className='page-card back-cover'+x;
    card.innerHTML=buildBack();
  }else{
    card.className='page-card'+x;
    card.innerHTML=buildTorn(p,idx);
  }
  var sc=card.querySelector('.page-scroll');
  if(sc)sc.scrollTop=0;
}

/* ══════════════════════════════════════════════════════
   NAVIGATION
══════════════════════════════════════════════════════ */
var cur=0,busy=false;

function updateUI(i){
  document.getElementById('prevBtn').disabled=(i===0);
  document.getElementById('nextBtn').disabled=(i===PAGES.length-1);
  var ind=document.getElementById('indicator');
  if(i===0) ind.textContent='Cover';
  else if(i===PAGES.length-1) ind.textContent='The End';
  else ind.textContent='Page '+i+' \u2022 '+(PAGES.length-2);
  syncDots(i);
}

function navigate(dir){
  if(busy)return;
  var next=cur+dir;
  if(next<0||next>=PAGES.length)return;
  busy=true;
  var card=document.getElementById('pageCard');
  card.classList.add(dir>0?'out-fwd':'out-back');
  setTimeout(function(){
    card.classList.remove('out-fwd','out-back');
    cur=next;
    setCard(cur,true);
    updateUI(cur);
    card.classList.add(dir>0?'in-fwd':'in-back');
    setTimeout(function(){
      card.classList.remove('in-fwd','in-back');
      busy=false;
    },310);
  },300);
}

document.addEventListener('keydown',function(e){
  if(e.key==='ArrowRight')navigate(1);
  if(e.key==='ArrowLeft')navigate(-1);
});

/* floating petals */
var PE=['🌸','🌺','🌷','\u273F','\u2740'];
for(var pi=0;pi<8;pi++){
  var el=document.createElement('div');
  el.className='petal';
  el.textContent=PE[pi%PE.length];
  el.style.left=Math.random()*100+'vw';
  el.style.fontSize=(10+Math.random()*8)+'px';
  el.style.animationDuration=(18+Math.random()*14)+'s';
  el.style.animationDelay=(Math.random()*20)+'s';
  document.body.appendChild(el);
}

setCard(0,false);
updateUI(0);
</script>
</body>
</html>
