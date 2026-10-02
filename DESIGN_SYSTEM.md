# J&J Co. — Design System Reference (v2)

> Read this ENTIRE file before building ANY page.

---

## Colors
```css
:root{
  --ink:#080705;--cream:#F2EFE9;
  --a:rgba(242,239,233,.7);--b:rgba(242,239,233,.35);
  --c:rgba(242,239,233,.12);--d:rgba(242,239,233,.05);
  --gold:#d4b896;--green:#7ecf82;
  --card:rgba(11,9,7,.97);
  --mono:'JetBrains Mono',monospace;
}
```

## Typography
- Display italic: `Instrument Serif` 400 italic → hero titles, emphasis
- Display sans: `Space Grotesk` 700 → headings, nav
- Body: `Inter` 300-500 → paragraphs
- Mono: `JetBrains Mono` 400-500 → labels, numbers, metrics

Split-typography pattern: Line 1 in Space Grotesk 700, Line 2 in Instrument Serif italic.
Hero size: `clamp(2.6rem, 6vw, 7rem)`. Body: `clamp(0.84rem, 1.2vw, 0.94rem)`.

## EXACT Cursor Code (MUST use on ALL pages)

### CSS
```css
#cur{position:fixed;top:0;left:0;width:34px;height:34px;border-radius:50%;
border:1px solid var(--b);pointer-events:none;z-index:9999;
transform:translate(-50%,-50%);transition:width .25s,height .25s,border-color .2s}
#dot{position:fixed;top:0;left:0;width:4px;height:4px;background:var(--cream);
border-radius:50%;pointer-events:none;z-index:9999;transform:translate(-50%,-50%)}
body.hov #cur{width:52px;height:52px;border-color:rgba(242,239,233,.6)}
@media(pointer:coarse){#cur,#dot{display:none}body{cursor:auto}}
```

### HTML
```html
<div id="cur" aria-hidden="true"></div>
<div id="dot" aria-hidden="true"></div>
```

### JS (EXACT — do not modify)
```js
var curEl = document.getElementById('cur'), dotEl = document.getElementById('dot');
var cx = -200, cy = -200, rx = -200, ry = -200;
window.addEventListener('mousemove', function(e) {
  cx = e.clientX; cy = e.clientY;
  gsap.to(dotEl, { x: cx, y: cy, duration: .04, ease: 'none' });
});
(function curLoop() {
  rx += (cx - rx) * .1; ry += (cy - ry) * .1;
  gsap.set(curEl, { x: rx, y: ry });
  requestAnimationFrame(curLoop);
})();
document.querySelectorAll('a,button,.wc,.faq-q').forEach(function(el) {
  el.addEventListener('mouseenter', function() { document.body.classList.add('hov'); });
  el.addEventListener('mouseleave', function() { document.body.classList.remove('hov'); });
});
```

## EXACT Logo/Nav (MUST use on ALL pages)
```html
<header id="nav">
  <a href="index.html" class="logo">
    <svg width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2L2 7l10 5 10-5-10-5Z"/><path d="M2 17l10 5 10-5M2 12l10 5 10-5"/></svg>
    J&amp;J Co.
    <span class="logo-tag">EST. 2026</span>
  </a>
  <nav class="nav-links">
    <a href="studio.html" class="nl">Studio</a>
    <a href="engine.html" class="nl">How It Works</a>
    <a href="services.html" class="nl">Services</a>
    <a href="contact.html" class="nl">Contact</a>
  </nav>
  <div class="nav-live"><span class="pls"></span><span id="navt">MORBI • ONLINE</span></div>
</header>
```

### Nav CSS
```css
#nav{position:fixed;top:0;left:0;right:0;z-index:8000;
padding:clamp(.9rem,1.8vw,1.3rem) clamp(1.5rem,5vw,4rem);
display:flex;align-items:center;justify-content:space-between;
transition:background .4s,border-color .4s;border-bottom:1px solid transparent}
#nav.scl{background:rgba(8,7,5,.94);backdrop-filter:blur(24px);-webkit-backdrop-filter:blur(24px);border-color:var(--d)}
.logo{display:flex;align-items:center;gap:.5rem;text-decoration:none;cursor:none;
font-family:'Space Grotesk',sans-serif;font-weight:700;font-size:.95rem;
letter-spacing:-.02em;color:var(--cream)}
.logo-tag{font-family:var(--mono);font-size:.46rem;letter-spacing:.12em;
border:1px solid var(--c);color:var(--b);padding:.12em .45em;border-radius:20px}
.nav-links{display:flex;gap:2.2rem}
@media(max-width:720px){.nav-links{display:none}}
.nl{font-family:'Space Grotesk',sans-serif;font-size:.62rem;letter-spacing:.2em;
text-transform:uppercase;color:var(--b);text-decoration:none;cursor:none;transition:color .2s}
.nl:hover{color:var(--cream)}
.nl.active{color:var(--cream)}
.nav-live{display:flex;align-items:center;gap:.45rem;font-family:var(--mono);
font-size:.52rem;color:var(--b);letter-spacing:.04em}
@media(max-width:860px){.nav-live{display:none}}
.pls{width:6px;height:6px;border-radius:50%;background:var(--green);
box-shadow:0 0 8px rgba(126,207,130,.9);animation:blink 2s infinite}
@keyframes blink{0%,100%{opacity:1}50%{opacity:.3}}
```

## Grain Overlay
```css
#grain{position:fixed;inset:0;pointer-events:none;z-index:9990;opacity:.028;
background-image:url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.85' numOctaves='4'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");
background-size:180px;animation:gr .1s steps(1) infinite}
@keyframes gr{0%{transform:translate(0,0)}50%{transform:translate(-3px,3px)}100%{transform:translate(3px,-3px)}}
```

## Footer (EXACT)
```html
<footer id="ft">
  <div class="ft-wm"><span class="ft-wm-dark">J&amp;J Co.</span><span class="ft-wm-light">J&amp;J Co.</span></div>
  <div class="ft-bot">
    <p class="ft-copy">&copy; 2026 J&amp;J Co. — AI Automation &amp; Engineering Studio. Morbi, Gujarat, India.</p>
    <nav class="ft-links">
      <a href="https://wa.me/919537097033" class="fa" target="_blank">WhatsApp</a>
      <a href="mailto:jndjcoai@gmail.com" class="fa copy-email">Email</a>
      <a href="https://instagram.com/jndj_co" class="fa" target="_blank">Instagram</a>
    </nav>
  </div>
</footer>
```

## Footer CSS
```css
#ft{position:relative;z-index:2;padding:3rem clamp(1.5rem,5vw,4rem) 1.2rem;background:var(--ink);border-top:1px solid var(--d)}
.ft-wm{font-family:'Instrument Serif',serif;font-style:italic;font-size:clamp(4rem,12vw,11rem);color:rgba(242,239,233,.02);text-align:center;line-height:1;margin-bottom:1rem;user-select:none;overflow:hidden;position:relative}
.ft-wm-dark{display:block}
.ft-wm-light{position:absolute;inset:0;color:rgba(242,239,233,.06);clip-path:inset(0 100% 0 0)}
.ft-bot{display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:1rem}
.ft-copy{font-family:var(--mono);font-size:.48rem;color:var(--b);letter-spacing:.06em}
.ft-links{display:flex;gap:1.5rem}
.fa{font-family:var(--mono);font-size:.5rem;letter-spacing:.12em;text-transform:uppercase;color:var(--b);text-decoration:none;cursor:none;transition:color .2s}
.fa:hover{color:var(--cream)}
```

## Lenis + ScrollTrigger Setup (EXACT)
```js
var lenis = new Lenis({ lerp: .07, smoothWheel: true, wheelMultiplier: .92 });
gsap.ticker.add(function(time) { lenis.raf(time * 1000); });
gsap.ticker.lagSmoothing(0);
lenis.on('scroll', ScrollTrigger.update);
```

## Nav Scroll Background
```js
ScrollTrigger.create({
  start: 'top -60', onUpdate: function(self) {
    document.getElementById('nav').classList.toggle('scl', self.progress > 0);
  }
});
```

## Clock
```js
void function updateClock() {
  var now = new Date();
  var ist = new Date(now.getTime() + (330 + now.getTimezoneOffset()) * 60000);
  var h = ist.getHours(), m = ist.getMinutes();
  var ap = h >= 12 ? 'PM' : 'AM';
  h = h % 12 || 12;
  var el = document.getElementById('navt');
  if (el) el.textContent = 'MORBI ' + (h < 10 ? '0' : '') + h + ':' + (m < 10 ? '0' : '') + m + ' ' + ap + ' \u00b7 ONLINE';
  setTimeout(updateClock, 10000);
}();
```

## Page Transition (Exit — on nav clicks)
```js
document.querySelectorAll('a[href$=".html"]').forEach(function(link) {
  link.addEventListener('click', function(e) {
    var href = link.getAttribute('href');
    if (!href) return;
    if (window.location.pathname.endsWith(href)) return;
    e.preventDefault();
    var trans = document.getElementById('page-trans');
    if (!trans) { window.location.href = href; return; }
    trans.style.display = '';
    trans.style.pointerEvents = 'all';
    var children = trans.children;
    if (children.length >= 2) {
      gsap.to(children[0], { x: '0%', y: '0%', scale: 1, opacity: 1, duration: 0.7, ease: 'power4.inOut' });
      gsap.to(children[1], { x: '0%', y: '0%', scale: 1, opacity: 1, duration: 0.7, ease: 'power4.inOut',
        onComplete: function() { window.location.href = href; }
      });
    } else if (children.length === 1) {
      gsap.to(children[0], { scale: 1, opacity: 1, duration: 0.7, ease: 'power3.inOut',
        onComplete: function() { window.location.href = href; }
      });
    }
  });
});
```

## Scroll Reveal
```js
gsap.utils.toArray('.rv').forEach(function(el) {
  gsap.fromTo(el, { opacity:0, y:24 }, { opacity:1, y:0, duration:1, ease:'expo',
    scrollTrigger: { trigger:el, start:'top 88%', once:true } });
});
```

## Contact Info
- Instagram: @jndj_co → https://instagram.com/jndj_co
- Email: jndjcoai@gmail.com
- WhatsApp: +91 95370 97033 → https://wa.me/919537097033
- Location: Morbi, Gujarat, India

## DESIGN RULES
1. NO basic boxy cards for content sections. Use text-only layouts with scroll animations.
2. Backgrounds must be high-end — animated gradients, WebGL effects, or CSS blend-mode compositions.
3. Text reveals should use character-by-character or word-by-word GSAP SplitText-style animations.
4. Every page must feel DIFFERENT from other pages — unique backgrounds, unique scroll interactions.
5. Cursor, logo, nav, grain, footer must be IDENTICAL across all pages (copy from above).
6. Fonts loaded from Google Fonts. Libs from assets/libs/.
7. Zero console errors. Brace balance = 0.
