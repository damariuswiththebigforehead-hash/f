<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>GOAT Launcher — Play & Explore</title>
  <meta name="description" content="GOAT Launcher — curated browser games, creative tools and AI experiences. A safe, ad-ready portal for students and creators." />
  <meta name="robots" content="index,follow" />
  <style>
    /* ---------- Fonts & variables ---------- */
    @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap');
    :root{
      --accent: #4f9cff;
      --bg1: #000007;
      --bg2: #071023;
      --text: #eef6ff;
      --muted: #9fb7ff;
      --card: rgba(255,255,255,0.04);
      --glass: rgba(255,255,255,0.06);
      --success: #bff7d6;
    }
    * { box-sizing: border-box; }
    body { margin:0; font-family:'Poppins',sans-serif; color:var(--text); background:linear-gradient(180deg,var(--bg2),var(--bg1)); -webkit-font-smoothing:antialiased; min-height:100vh; }

    /* ---------- Water shimmer background ---------- */
    .bg-shimmer {
      position:fixed; inset:0; z-index:-2; pointer-events:none;
      background:
        radial-gradient(circle at 50% 30%, rgba(79,156,255,0.06), transparent 25%),
        radial-gradient(circle at 20% 70%, rgba(123,97,255,0.03), transparent 22%);
      overflow:hidden;
      filter:contrast(1.05) saturate(1.05);
      animation:bgMove 18s ease-in-out infinite;
    }
    @keyframes bgMove {
      0% { transform:translateY(0) scale(1); }
      50% { transform:translateY(-18px) scale(1.02); }
      100% { transform:translateY(0) scale(1); }
    }

    /* subtle texture overlay */
    .bg-texture { position:fixed; inset:0; z-index:-1; background-image:url('https://www.transparenttextures.com/patterns/diagmonds.png'); opacity:0.05; }

    /* ---------- Layout ---------- */
    header { height:100vh; display:flex; align-items:center; justify-content:center; text-align:center; padding:3rem 1.25rem; }
    header h1 { font-size:5rem; margin:0; line-height:1; text-shadow:0 0 36px rgba(79,156,255,0.45); transition:opacity .35s ease; }
    header p.lead { margin-top:1rem; color:var(--muted); font-size:1.05rem; }

    main { max-width:1100px; margin:0 auto; padding: 2rem 1rem 6rem; }

    section { padding: 3.25rem 0; }

    h2.section-title { font-size:2rem; margin:0 0 1.25rem; text-shadow:0 0 14px rgba(79,156,255,0.18); }

    /* grid */
    .grid { display:grid; gap:1.25rem; grid-template-columns:repeat(auto-fit,minmax(220px,1fr)); margin-top:1rem; }

    /* cards as links (safe) */
    a.card { display:block; text-decoration:none; color:inherit; background:var(--card); padding:1.25rem; border-radius:14px; border:1px solid rgba(255,255,255,0.03); backdrop-filter: blur(8px); transition:transform .28s ease, box-shadow .28s ease; }
    a.card:hover { transform:translateY(-6px); box-shadow:0 18px 50px rgba(0,0,0,0.6); border-color:var(--accent); }
    .card img { width:56px; height:56px; border-radius:10px; object-fit:cover; display:block; margin:0 auto 0.9rem; box-shadow:0 6px 18px rgba(0,0,0,0.45); }
    .card h3 { font-size:1.05rem; margin:0 0 .25rem; text-align:center; }
    .card p { font-size:.92rem; color:#d6e9ff; text-align:center; margin:0; opacity:.9; }

    /* Show More button */
    .center { text-align:center; margin-top:2rem; }
    button.btn {
      background: linear-gradient(180deg,var(--accent),#2e8ee6);
      border:none; color:#00111a; padding:12px 20px; font-weight:700; border-radius:12px; cursor:pointer; box-shadow:0 10px 30px rgba(79,156,255,0.12);
    }

    /* Info panel (hidden) */
    #infoPanel {
      opacity:0; transform:translateY(30px); transition:all .9s ease; margin-top:1.5rem;
      background: linear-gradient(180deg, rgba(10,12,16,0.72), rgba(12,14,18,0.56));
      border-radius:14px; padding:1.2rem; border:1px solid rgba(255,255,255,0.03); backdrop-filter:blur(10px);
      max-height:60vh; overflow:auto;
    }
    #infoPanel.visible { opacity:1; transform:translateY(0); }

    #infoPanel h3 { margin:0 0 .6rem; opacity:0; transform:translateY(12px); transition:all .75s ease; }
    #infoPanel p { margin:0 0 .8rem; opacity:0; transform:translateY(12px); transition:all .75s ease; color:#dbefff; }

    /* W4XJLIP glowing signature */
    #w4xjlip {
      text-align:center; font-size:2.4rem; font-weight:800; letter-spacing:5px; color:var(--accent); margin-top:1rem;
      text-shadow:0 0 18px rgba(79,156,255,0.85);
      opacity:0; transform:translateY(12px); transition:all .75s ease;
      animation:floatRipple 3s ease-in-out infinite, textGlow 2.4s ease-in-out infinite alternate;
    }
    @keyframes floatRipple {0%{transform:translateY(0)}50%{transform:translateY(-6px)}100%{transform:translateY(0)}}
    @keyframes textGlow {0%{text-shadow:0 0 14px rgba(79,156,255,0.5)}50%{text-shadow:0 0 36px rgba(79,156,255,0.95)}100%{text-shadow:0 0 14px rgba(79,156,255,0.5)}}

    /* About & Contact */
    .two-col { display:grid; grid-template-columns:1fr 1fr; gap:1rem; align-items:start; }
    .card-box { background:var(--glass); padding:1rem; border-radius:12px; border:1px solid rgba(255,255,255,0.03); color:#eaf6ff; }
    .contact-form input, .contact-form textarea { width:100%; padding:.7rem .9rem; border-radius:10px; border:1px solid rgba(255,255,255,0.06); background:transparent; color:var(--text); margin-bottom:.6rem; }
    .contact-form button { background:linear-gradient(180deg,#ffd47f,#ff8fbf); border:none; padding:10px 14px; border-radius:10px; cursor:pointer; font-weight:700; }

    /* footer & privacy */
    footer { margin-top:2.5rem; color:var(--muted); text-align:center; padding-bottom:3rem; font-size:.95rem; }

    /* cookie consent */
    .cookie { position:fixed; left:12px; right:12px; bottom:12px; background:rgba(6,10,16,0.95); color:#dff2ff; padding:12px 14px; border-radius:12px; border:1px solid rgba(255,255,255,0.03); display:flex; gap:12px; align-items:center; justify-content:space-between; max-width:920px; margin:auto; z-index:1200; }
    .cookie button { background:var(--accent); border:none; color:#001; padding:8px 12px; border-radius:8px; font-weight:700; cursor:pointer; }

    /* fade-in helper for cards*/
    .reveal { opacity:1 !important; transform:translateY(0) !important; transition:all .9s ease-out; }

    /* responsive */
    @media (max-width:880px){ .two-col{grid-template-columns:1fr} header h1{font-size:3.2rem} #w4xjlip{font-size:2rem} }
  </style>
</head>
<body>
  <!-- background layers -->
  <div class="bg-shimmer" aria-hidden="true"></div>
  <div class="bg-texture" aria-hidden="true"></div>

  <!-- Header hero -->
  <header id="hero">
    <div>
      <h1 id="mainTitle">🚀 GOAT Launcher</h1>
      <p class="lead">A curated portal of web games, art and AI tools — safe, simple, and ready to explore.</p>
    </div>
  </header>

  <main>
    <!-- Games Hub -->
    <section id="games">
      <h2 class="section-title">🎮 Games Hub</h2>

      <div class="grid" id="cardsGrid">
        <a class="card" href="https://emupedia.net/beta/emuos/" target="_blank" rel="noopener noreferrer">
          <img src="https://emupedia.net/favicon.ico" alt="">
          <h3>EmuOS</h3>
          <p>Classic browser games & emulation hub</p>
        </a>

        <a class="card" href="https://hordes.io/" target="_blank" rel="noopener noreferrer">
          <img src="https://hordes.io/favicon.ico" alt="">
          <h3>Hordes.io</h3>
          <p>MMO arena battles</p>
        </a>

        <a class="card" href="https://duck.alltutors.org/" target="_blank" rel="noopener noreferrer">
          <img src="https://upload.wikimedia.org/wikipedia/commons/7/70/Duck_icon.png" alt="">
          <h3>Duck</h3>
          <p>Fun & random adventures</p>
        </a>

        <a class="card" href="https://www.fridaynightfunkin.net/" target="_blank" rel="noopener noreferrer">
          <img src="https://www.fridaynightfunkin.net/wp-content/uploads/2021/05/fnf-icon.png" alt="">
          <h3>Friday Night Funkin'</h3>
          <p>Rhythm game & community</p>
        </a>

        <a class="card" href="https://www.emugames.com/" target="_blank" rel="noopener noreferrer">
          <img src="https://www.emugames.com/favicon.ico" alt="">
          <h3>EmuGames</h3>
          <p>Retro & emulated classics</p>
        </a>

        <a class="card" href="https://www.intangible.ai/" target="_blank" rel="noopener noreferrer">
          <img src="https://www.intangible.ai/favicon.ico" alt="">
          <h3>Intangible AI</h3>
          <p>AI-driven interactive experiences</p>
        </a>

        <a class="card" href="https://pakohighway.online/" target="_blank" rel="noopener noreferrer">
          <img src="https://pakohighway.online/favicon.ico" alt="">
          <h3>Pako Highway</h3>
          <p>Drive fast and dodge traffic</p>
        </a>

        <a class="card" href="https://art.fullsusmtb.org/" target="_blank" rel="noopener noreferrer">
          <img src="https://art.fullsusmtb.org/favicon.ico" alt="">
          <h3>FullSus Art</h3>
          <p>Creative digital artwork</p>
        </a>
      </div>

      <div class="center">
        <button id="showMoreBtn" class="btn">Show More</button>
      </div>

      <!-- Info panel (hidden until Show More) -->
      <div id="infoPanel" aria-hidden="true">
        <h3>About GOAT Launcher</h3>
        <p>This launcher was created to help students and creators quickly discover browser-based games, art galleries, and experimental AI experiences. It's built with accessible web technologies and designed to be lightweight and fast.</p>

        <p>How this works: each card is a safe link that opens the original site in a new tab. No embedding is used — this avoids Terms of Service and copyright issues and keeps the user experience simple.</p>

        <p>Tech highlights: HTML, modern CSS (backdrop-filter & CSS animations), and vanilla JavaScript. A startup ripple and shimmer give a cinematic water-like feel.</p>

        <p style="font-weight:700; color:var(--muted)">Why this helps bored students:</p>
        <p>Curated, playable, and immediate — no installs, no sign-ups required for most sites. Explore short bursts of fun between study sessions.</p>

        <!-- big glowing signature -->
        <div id="w4xjlip">W4XJLIP</div>
      </div>
    </section>

    <!-- About / Contact (adds original content for AdSense) -->
    <section id="aboutContact">
      <h2 class="section-title">About & Contact</h2>
      <div class="two-col">
        <div class="card-box">
          <h4 style="margin-top:0">About</h4>
          <p style="color:#dbefff">GOAT Launcher is an independent, fan-created portal. It is not affiliated with the linked sites. The goal is to provide a safe, curated place for quick games, creative tools, and experimental AI demos.</p>

          <p style="color:#dbefff">If you'd like to contribute a site suggestion, or request removal of a link or icon, please contact the creator using the form to the right.</p>
        </div>

        <div class="card-box">
          <h4 style="margin-top:0">Contact</h4>
          <div class="contact-form">
            <!-- mailto fallback; replace mail@example.com with your email -->
            <form id="contactForm" action="mailto:mail@example.com" method="post" enctype="text/plain" onsubmit="alert('This demo form uses mailto: — replace with a server endpoint to receive messages.'); return false;">
              <input type="text" name="name" placeholder="Your name" required>
              <input type="email" name="email" placeholder="Your email" required>
              <textarea name="message" rows="4" placeholder="Message (suggestions, sponsorship interest, removals)" required></textarea>
              <div style="display:flex; gap:.6rem;">
                <button type="submit" class="btn" style="background:linear-gradient(180deg,#6ee7f3,#7b61ff);color:#001;">Send</button>
                <a href="mailto:mail@example.com" class="btn" style="background:#ffd47f;text-decoration:none;padding:10px 14px;border-radius:10px;color:#001;font-weight:700;">Email</a>
              </div>
            </form>
          </div>
        </div>
      </div>
    </section>

    <!-- Privacy & AdSense info -->
    <section id="privacy">
      <h2 class="section-title">Privacy & Ads</h2>
      <div class="card-box">
        <p style="color:#dbefff">This site does not store personal data by default. If you enable third-party services (analytics, ads), those providers may collect information per their policies. By using this site you consent to collection by third parties used on the page.</p>

        <p style="color:#dbefff">Google AdSense: to enable AdSense, publish this site on a real HTTPS domain, add a privacy policy page, and then insert your AdSense script where indicated below. Do not place AdSense into iframes or inside pages that embed other sites.</p>

        <details style="margin-top:.6rem; color:#dbefff;">
          <summary style="cursor:pointer">How to add AdSense (quick)</summary>
          <ol style="color:#dbefff">
            <li>Sign up at <a href="https://www.google.com/adsense/start/" target="_blank" rel="noopener noreferrer">Google AdSense</a>.</li>
            <li>When approved, copy the global site tag and paste it inside the <code>&lt;head&gt;</code> of your published pages.</li>
            <li>Place ad units in your layout — keep them visible, not overlaying other sites or copyrighted content.</li>
            <li>Ensure you have a visible <strong>Privacy Policy</strong> page (you can expand the policy here or link to a full page).</li>
          </ol>
        </details>
      </div>
    </section>

    <footer>Made by 🐐 GOAT Mode — <a href="#privacy" style="color:var(--muted); text-decoration:underline;">Privacy</a></footer>
  </main>

  <!-- Cookie consent (small) -->
  <div id="cookie" class="cookie" style="display:none">
    <div style="flex:1">This site uses minimal cookies and may use third-party services (analytics/ads). By continuing you accept our use — see Privacy above.</div>
    <div style="display:flex; gap:.6rem">
      <button id="acceptCookies">Accept</button>
      <button id="declineCookies" style="background:transparent;border:1px solid rgba(255,255,255,0.06);color:var(--muted);padding:8px 10px;border-radius:8px;cursor:pointer">Decline</button>
    </div>
  </div>

  <!-- ========== JS: interactions ========== -->
  <script>
    // Fade title on scroll
    const title = document.getElementById('mainTitle');
    window.addEventListener('scroll', ()=> {
      const fadePoint = window.innerHeight * 0.7;
      title.style.opacity = Math.max(0, 1 - window.scrollY / fadePoint);
    });

    // Reveal cards with observer
    const cards = document.querySelectorAll('.card');
    const cardObserver = new IntersectionObserver((entries)=>{
      entries.forEach(en=>{
        if(en.isIntersecting) en.target.classList.add('reveal');
      });
    }, { threshold: 0.18 });
    cards.forEach(c=>cardObserver.observe(c));

    // Show More splash + reveal info with per-paragraph animation
    const showBtn = document.getElementById('showMoreBtn');
    const infoPanel = document.getElementById('infoPanel');
    const waveBg = document.querySelector('.bg-shimmer');

    showBtn.addEventListener('click', ()=>{
      // create ripple element centered on viewport
      const splash = document.createElement('div');
      splash.style.position = 'fixed';
      splash.style.left = '50%';
      splash.style.top = '50%';
      splash.style.width = '160px';
      splash.style.height = '160px';
      splash.style.borderRadius = '50%';
      splash.style.background = 'radial-gradient(circle, rgba(79,156,255,0.5) 0%, rgba(79,156,255,0) 70%)';
      splash.style.transform = 'translate(-50%,-50%) scale(0)';
      splash.style.zIndex = '1200';
      splash.style.transition = 'transform 1s ease, opacity 1s ease';
      document.body.appendChild(splash);

      requestAnimationFrame(()=> {
        splash.style.transform = 'translate(-50%,-50%) scale(22)';
        splash.style.opacity = '0';
      });

      setTimeout(()=> {
        splash.remove();
        infoPanel.classList.add('visible');
        infoPanel.setAttribute('aria-hidden','false');
        // per-element emergence
        const nodes = infoPanel.querySelectorAll('h3, p, #w4xjlip');
        nodes.forEach((n, i)=> setTimeout(()=> { n.style.opacity = 1; n.style.transform = 'translateY(0)'; }, 220 + i*180));
        // gentle wave blur to accent
        waveBg.style.filter = 'blur(18px) saturate(1.05)';
        setTimeout(()=> waveBg.style.filter = '', 1600);
      }, 950);
    });

    // Cookie consent logic
    const cookie = document.getElementById('cookie');
    const acceptCookies = document.getElementById('acceptCookies');
    const declineCookies = document.getElementById('declineCookies');
    const cookieKey = 'goat_cookie_accept';
    if(!localStorage.getItem(cookieKey)) cookie.style.display = 'flex';

    acceptCookies && acceptCookies.addEventListener('click', ()=>{
      localStorage.setItem(cookieKey, '1');
      cookie.style.display = 'none';
      // at this point you could enable analytics or ad scripts
    });
    declineCookies && declineCookies.addEventListener('click', ()=>{
      localStorage.setItem(cookieKey, '0');
      cookie.style.display = 'none';
    });

    // Contact form: (demo) focus first field
    const contactForm = document.getElementById('contactForm');
    if(contactForm) contactForm.querySelector('input')?.focus();

    /* ============================
       AdSense instructions - where to paste your script
       ============================
       1) When Google approves your site, they give you a "global site tag" <script> to paste inside <head>.
       2) Paste it at the top of this file (inside <head>), before other scripts.
       3) Add ad units into the layout (e.g., inside main) where you want them to appear.
       4) Make sure you are not inserting ads into pages that embed other sites.

       Example (do NOT paste now unless you have AdSense script):
       <!-- Google AdSense -->
       <script data-ad-client="ca-pub-XXXXXXXXXXXX" async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
    */

  </script>
</body>
</html>
