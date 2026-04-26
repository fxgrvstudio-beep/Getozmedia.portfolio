# Getozmedia.portfolio
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Getoz · Motion Designer</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;500;600;700;800&family=DM+Sans:ital,wght@0,300;0,400;0,500;1,300&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }
  :root {
    --bg: #090909; --bg2: #111111; --card: #141414;
    --border: rgba(255,255,255,0.07); --border2: rgba(255,255,255,0.13);
    --text: #f0ede8; --muted: #888580;
    --accent: #D4F45A; --accent2: #B8E040;
    --accent-dim: rgba(212,244,90,0.12);
  }
  html { scroll-behavior: smooth; }
  body { background: var(--bg); color: var(--text); font-family: 'DM Sans', sans-serif; font-size: 16px; line-height: 1.7; overflow-x: hidden; }

  /* NAV */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    display: flex; align-items: center; justify-content: space-between;
    padding: 1.25rem 5%;
    background: rgba(9,9,9,0.9); backdrop-filter: blur(18px);
    border-bottom: 1px solid var(--border);
  }
  .logo { font-family: 'Syne', sans-serif; font-weight: 800; font-size: 1.3rem; letter-spacing: -0.02em; color: var(--text); text-decoration: none; }
  .logo span { color: var(--accent); }
  nav ul { display: flex; gap: 2.5rem; list-style: none; }
  nav ul a { text-decoration: none; color: var(--muted); font-size: 0.88rem; font-weight: 400; transition: color 0.2s; }
  nav ul a:hover { color: var(--text); }
  .nav-cta { background: var(--accent) !important; color: #090909 !important; padding: 0.5rem 1.4rem; border-radius: 100px; font-weight: 600 !important; }
  .nav-cta:hover { background: var(--accent2) !important; }

  /* HERO */
  .hero { min-height: 100vh; display: flex; flex-direction: column; justify-content: center; padding: 8rem 5% 5rem; position: relative; overflow: hidden; }
  .hero-grid-bg {
    position: absolute; inset: 0;
    background-image: linear-gradient(rgba(255,255,255,0.025) 1px, transparent 1px), linear-gradient(90deg, rgba(255,255,255,0.025) 1px, transparent 1px);
    background-size: 60px 60px;
    mask-image: radial-gradient(ellipse 80% 60% at 50% 40%, black 30%, transparent 100%);
  }
  .hero-glow { position: absolute; top: 20%; left: 50%; transform: translateX(-50%); width: 700px; height: 400px; background: radial-gradient(ellipse, rgba(212,244,90,0.08) 0%, transparent 70%); pointer-events: none; }
  .hero-tag { display: inline-flex; align-items: center; gap: 0.5rem; background: var(--accent-dim); border: 1px solid rgba(212,244,90,0.25); color: var(--accent); font-size: 0.8rem; font-weight: 500; padding: 0.35rem 0.9rem; border-radius: 100px; margin-bottom: 2rem; width: fit-content; animation: fadeUp 0.8s ease both; }
  .hero-tag::before { content: ''; width: 6px; height: 6px; border-radius: 50%; background: var(--accent); animation: pulse 2s infinite; }
  @keyframes pulse { 0%,100%{opacity:1} 50%{opacity:0.4} }
  .hero h1 { font-family: 'Syne', sans-serif; font-weight: 800; font-size: clamp(3rem, 7vw, 6.5rem); line-height: 1.0; letter-spacing: -0.03em; max-width: 900px; animation: fadeUp 0.8s 0.1s ease both; }
  .hero h1 em { font-style: normal; color: var(--accent); }
  .hero > p { font-size: 1.1rem; color: var(--muted); max-width: 520px; margin-top: 1.5rem; font-weight: 300; animation: fadeUp 0.8s 0.2s ease both; }
  .hero-actions { display: flex; gap: 1rem; margin-top: 2.5rem; animation: fadeUp 0.8s 0.3s ease both; }
  .btn-primary { background: var(--accent); color: #090909; border: none; padding: 0.85rem 2rem; border-radius: 100px; font-family: 'DM Sans', sans-serif; font-size: 0.95rem; font-weight: 600; cursor: pointer; text-decoration: none; display: inline-block; transition: background 0.2s, transform 0.15s; }
  .btn-primary:hover { background: var(--accent2); transform: translateY(-1px); }
  .btn-secondary { background: transparent; color: var(--text); border: 1px solid var(--border2); padding: 0.85rem 2rem; border-radius: 100px; font-family: 'DM Sans', sans-serif; font-size: 0.95rem; font-weight: 400; cursor: pointer; text-decoration: none; display: inline-block; transition: border-color 0.2s, transform 0.15s; }
  .btn-secondary:hover { border-color: rgba(255,255,255,0.35); transform: translateY(-1px); }
  .hero-stats { display: flex; gap: 3rem; margin-top: 5rem; padding-top: 2.5rem; border-top: 1px solid var(--border); animation: fadeUp 0.8s 0.4s ease both; }
  .stat-num { font-family: 'Syne', sans-serif; font-size: 2rem; font-weight: 700; }
  .stat-num span { color: var(--accent); }
  .stat-label { font-size: 0.82rem; color: var(--muted); margin-top: 0.15rem; }
  @keyframes fadeUp { from{opacity:0;transform:translateY(28px)} to{opacity:1;transform:translateY(0)} }

  /* SECTIONS */
  section { padding: 7rem 5%; }
  .section-label { font-size: 0.75rem; font-weight: 500; letter-spacing: 0.15em; text-transform: uppercase; color: var(--accent); margin-bottom: 1rem; }
  .section-title { font-family: 'Syne', sans-serif; font-weight: 700; font-size: clamp(2rem, 4vw, 3.2rem); line-height: 1.1; letter-spacing: -0.02em; max-width: 600px; }

  /* SKILLS */
  .skills-section { background: var(--bg2); }
  .skills-inner { display: grid; grid-template-columns: 1fr 1fr; gap: 5rem; align-items: center; }
  .skills-text p { color: var(--muted); margin-top: 1.25rem; font-size: 1.05rem; font-weight: 300; }
  .skills-cards { display: flex; flex-direction: column; gap: 1rem; }
  .skill-card { background: var(--card); border: 1px solid var(--border); border-radius: 16px; padding: 1.5rem; display: flex; align-items: center; gap: 1.25rem; transition: border-color 0.3s, transform 0.3s; }
  .skill-card:hover { border-color: rgba(212,244,90,0.3); transform: translateX(6px); }
  .skill-icon { width: 48px; height: 48px; border-radius: 12px; background: var(--accent-dim); border: 1px solid rgba(212,244,90,0.2); display: flex; align-items: center; justify-content: center; font-size: 1.3rem; flex-shrink: 0; }
  .skill-name { font-family: 'Syne', sans-serif; font-weight: 600; font-size: 1rem; margin-bottom: 0.2rem; }
  .skill-desc { font-size: 0.83rem; color: var(--muted); font-weight: 300; }

  /* WORKS */
  .works-header { display: flex; justify-content: space-between; align-items: flex-end; margin-bottom: 3rem; }
  .works-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 1.5rem; }
  .work-card { background: var(--card); border: 1px solid var(--border); border-radius: 20px; overflow: hidden; transition: border-color 0.3s, transform 0.3s; }
  .work-card:hover { border-color: rgba(212,244,90,0.3); transform: translateY(-5px); }
  .work-thumb { position: relative; width: 100%; padding-top: 56.25%; background: #000; overflow: hidden; }
  .work-thumb.vertical { padding-top: 75%; }
  .work-thumb iframe { position: absolute; top: 0; left: 0; width: 100%; height: 100%; border: none; pointer-events: none; }
  .thumb-overlay { position: absolute; inset: 0; display: flex; align-items: center; justify-content: center; background: rgba(0,0,0,0.35); cursor: pointer; z-index: 2; transition: background 0.3s; }
  .work-card:hover .thumb-overlay { background: rgba(0,0,0,0.15); }
  .play-btn { width: 60px; height: 60px; border-radius: 50%; background: rgba(9,9,9,0.8); border: 1.5px solid rgba(255,255,255,0.2); display: flex; align-items: center; justify-content: center; backdrop-filter: blur(10px); transition: background 0.25s, transform 0.25s; }
  .work-card:hover .play-btn { background: var(--accent); transform: scale(1.1); }
  .work-card:hover .play-btn svg path { fill: #090909; }
  .work-thumb.playing .thumb-overlay { display: none; }
  .work-thumb.playing iframe { pointer-events: all; }
  .work-info { padding: 1.25rem 1.5rem 1.5rem; }
  .work-tag { display: inline-block; font-size: 0.72rem; font-weight: 500; letter-spacing: 0.08em; text-transform: uppercase; color: var(--accent); background: var(--accent-dim); border-radius: 100px; padding: 0.25rem 0.75rem; margin-bottom: 0.6rem; }
  .work-title { font-family: 'Syne', sans-serif; font-weight: 600; font-size: 1.05rem; }
  .work-meta { font-size: 0.82rem; color: var(--muted); margin-top: 0.3rem; }

  /* REVIEWS */
  .reviews-section { background: var(--bg2); }
  .reviews-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 1.25rem; margin-top: 3rem; }
  .review-card { background: var(--card); border: 1px solid var(--border); border-radius: 18px; padding: 1.75rem; transition: border-color 0.3s; }
  .review-card:hover { border-color: var(--border2); }
  .stars { color: var(--accent); font-size: 0.9rem; margin-bottom: 1rem; letter-spacing: 2px; }
  .review-text { font-size: 0.92rem; color: var(--muted); font-weight: 300; line-height: 1.8; font-style: italic; margin-bottom: 1.5rem; }
  .reviewer { display: flex; align-items: center; gap: 0.75rem; }
  .reviewer-avatar { width: 38px; height: 38px; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-family: 'Syne', sans-serif; font-weight: 700; font-size: 0.85rem; color: #090909; background: var(--accent); flex-shrink: 0; }
  .reviewer-name { font-family: 'Syne', sans-serif; font-size: 0.9rem; font-weight: 600; }
  .reviewer-role { font-size: 0.78rem; color: var(--muted); }

  /* PRICING */
  .pricing-section { background: var(--bg); }
  .pricing-subtitle { color: var(--muted); margin-top: 1rem; font-size: 1rem; font-weight: 300; }
  .pricing-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 1.25rem; margin-top: 3rem; }
  .pricing-card { background: var(--card); border: 1px solid var(--border); border-radius: 22px; padding: 2.25rem 2rem; position: relative; transition: border-color 0.3s, transform 0.3s; display: flex; flex-direction: column; }
  .pricing-card:hover { transform: translateY(-5px); }
  .pricing-card.featured { border-color: rgba(212,244,90,0.35); background: linear-gradient(160deg, #161f00 0%, #111600 100%); }
  .featured-badge { position: absolute; top: -14px; left: 50%; transform: translateX(-50%); background: var(--accent); color: #090909; font-size: 0.72rem; font-weight: 700; letter-spacing: 0.08em; text-transform: uppercase; padding: 0.3rem 1rem; border-radius: 100px; white-space: nowrap; }
  .plan-name { font-family: 'Syne', sans-serif; font-weight: 700; font-size: 1.1rem; margin-bottom: 0.5rem; }
  .plan-tagline { font-size: 0.82rem; color: var(--muted); margin-bottom: 1.75rem; font-weight: 300; }
  .plan-price { font-family: 'Syne', sans-serif; font-size: 3.5rem; font-weight: 800; line-height: 1; letter-spacing: -0.03em; margin-bottom: 0.3rem; }
  .plan-price span { font-size: 1.5rem; font-weight: 500; vertical-align: super; color: var(--muted); }
  .plan-duration { font-size: 0.8rem; color: var(--muted); margin-bottom: 2rem; padding-bottom: 1.75rem; border-bottom: 1px solid var(--border); }
  .plan-features { list-style: none; flex: 1; }
  .plan-features li { font-size: 0.88rem; color: var(--muted); padding: 0.55rem 0; display: flex; align-items: center; gap: 0.75rem; border-bottom: 1px solid var(--border); font-weight: 300; }
  .plan-features li:last-child { border-bottom: none; }
  .check { width: 18px; height: 18px; border-radius: 50%; background: var(--accent-dim); border: 1px solid rgba(212,244,90,0.25); display: flex; align-items: center; justify-content: center; flex-shrink: 0; font-size: 0.65rem; color: var(--accent); }
  .plan-cta { margin-top: 2rem; display: block; text-align: center; padding: 0.9rem; border-radius: 100px; font-size: 0.9rem; font-weight: 500; font-family: 'DM Sans', sans-serif; cursor: pointer; text-decoration: none; transition: all 0.2s; }
  .plan-cta-outline { border: 1px solid var(--border2); color: var(--text); background: transparent; }
  .plan-cta-outline:hover { border-color: rgba(255,255,255,0.35); }
  .plan-cta-filled { background: var(--accent); color: #090909; border: none; font-weight: 600; }
  .plan-cta-filled:hover { background: var(--accent2); }

  /* CONTACT */
  .contact-section { background: var(--bg2); }
  .contact-inner { display: grid; grid-template-columns: 1fr 1fr; gap: 5rem; align-items: start; }
  .contact-left p { color: var(--muted); margin-top: 1.25rem; font-size: 1.05rem; font-weight: 300; margin-bottom: 2rem; }
  .contact-links { display: flex; flex-direction: column; gap: 1rem; }
  .contact-link { display: flex; align-items: center; gap: 1rem; text-decoration: none; color: var(--text); background: var(--card); border: 1px solid var(--border); border-radius: 14px; padding: 1.25rem 1.5rem; transition: border-color 0.3s, transform 0.2s; }
  .contact-link:hover { border-color: rgba(212,244,90,0.35); transform: translateX(5px); }
  .contact-link-icon { width: 44px; height: 44px; border-radius: 12px; background: var(--accent-dim); border: 1px solid rgba(212,244,90,0.2); display: flex; align-items: center; justify-content: center; flex-shrink: 0; }
  .contact-link-icon svg { width: 20px; height: 20px; }
  .contact-link-info strong { display: block; font-weight: 600; margin-bottom: 0.15rem; font-size: 0.88rem; font-family: 'Syne', sans-serif; }
  .contact-link-info span { font-size: 0.82rem; color: var(--muted); }
  .contact-form { display: flex; flex-direction: column; gap: 1rem; }
  .form-group { display: flex; flex-direction: column; gap: 0.4rem; }
  .form-label { font-size: 0.8rem; color: var(--muted); font-weight: 400; }
  .form-input, .form-textarea { background: var(--card); border: 1px solid var(--border); color: var(--text); border-radius: 12px; padding: 0.85rem 1.1rem; font-family: 'DM Sans', sans-serif; font-size: 0.92rem; font-weight: 300; outline: none; transition: border-color 0.2s; resize: none; }
  .form-input::placeholder, .form-textarea::placeholder { color: var(--muted); }
  .form-input:focus, .form-textarea:focus { border-color: rgba(212,244,90,0.4); }
  .form-textarea { height: 130px; }
  .form-submit { background: var(--accent); color: #090909; border: none; padding: 0.9rem 2rem; border-radius: 100px; font-family: 'DM Sans', sans-serif; font-size: 0.95rem; font-weight: 600; cursor: pointer; transition: background 0.2s; margin-top: 0.5rem; }
  .form-submit:hover { background: var(--accent2); }

  /* FOOTER */
  footer { background: var(--bg); border-top: 1px solid var(--border); padding: 2rem 5%; display: flex; justify-content: space-between; align-items: center; }
  footer p { font-size: 0.82rem; color: var(--muted); }

  .reveal { opacity: 0; transform: translateY(30px); transition: opacity 0.7s ease, transform 0.7s ease; }
  .reveal.visible { opacity: 1; transform: none; }
  ::-webkit-scrollbar { width: 6px; }
  ::-webkit-scrollbar-track { background: var(--bg); }
  ::-webkit-scrollbar-thumb { background: #2a2a2a; border-radius: 3px; }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <a href="#" class="logo">Getoz<span>.</span></a>
  <ul>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#works">Work</a></li>
    <li><a href="#reviews">Reviews</a></li>
    <li><a href="#pricing">Pricing</a></li>
    <li><a href="#contact" class="nav-cta">Hire Me</a></li>
  </ul>
</nav>

<!-- HERO -->
<section class="hero" id="home">
  <div class="hero-grid-bg"></div>
  <div class="hero-glow"></div>
  <div class="hero-tag">Available for freelance work</div>
  <h1>I turn <em>complex SaaS</em><br>into clean motion.</h1>
  <p>Hi, I'm Getoz — a motion designer specializing in SaaS explanation videos, app walkthroughs, and talking head content that converts viewers into customers.</p>
  <div class="hero-actions">
    <a href="#works" class="btn-primary">View My Work</a>
    <a href="#pricing" class="btn-secondary">See Pricing →</a>
  </div>
  <div class="hero-stats">
    <div><div class="stat-num">50<span>+</span></div><div class="stat-label">Projects Delivered</div></div>
    <div><div class="stat-num">30<span>+</span></div><div class="stat-label">Happy Clients</div></div>
    <div><div class="stat-num">3<span>yr</span></div><div class="stat-label">Experience</div></div>
  </div>
</section>

<!-- SKILLS -->
<section class="skills-section" id="skills">
  <div class="skills-inner">
    <div class="skills-text reveal">
      <div class="section-label">What I Do</div>
      <h2 class="section-title">Crafted motion for the digital product era.</h2>
      <p>I specialize in breaking down complex software into visually engaging stories — turning features into feelings, and walkthroughs into conversions.</p>
      <br>
      <p>Every frame is intentional. Every transition earns its place. I design motion that makes your product <em>feel</em> inevitable.</p>
    </div>
    <div class="skills-cards reveal">
      <div class="skill-card">
        <div class="skill-icon">✦</div>
        <div>
          <div class="skill-name">Motion Graphics</div>
          <div class="skill-desc">Dynamic animated visuals, kinetic typography, logo reveals & brand motion</div>
        </div>
      </div>
      <div class="skill-card">
        <div class="skill-icon">◈</div>
        <div>
          <div class="skill-name">Talking Head Videos</div>
          <div class="skill-desc">Polished talking head edits with motion overlays, captions & B-roll</div>
        </div>
      </div>
      <div class="skill-card">
        <div class="skill-icon">⬡</div>
        <div>
          <div class="skill-name">SaaS / App Explanations</div>
          <div class="skill-desc">Product walkthroughs, feature explainers & onboarding animations that convert</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- WORKS -->
<section id="works">
  <div class="works-header reveal">
    <div>
      <div class="section-label">Portfolio</div>
      <h2 class="section-title">Selected Work</h2>
    </div>
    <a href="#contact" class="btn-secondary">Work With Me →</a>
  </div>
  <div class="works-grid">

    <!-- Video 1: gLR-Wagfm6M (Short) -->
    <div class="work-card reveal">
      <div class="work-thumb vertical" id="thumb-1">
        <iframe src="https://www.youtube.com/embed/gLR-Wagfm6M?rel=0&modestbranding=1" title="Product Feature Breakdown" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
        <div class="thumb-overlay" onclick="playVideo('thumb-1')">
          <div class="play-btn"><svg viewBox="0 0 16 16" fill="none"><path d="M4 2.5L13 8L4 13.5V2.5Z" fill="white"/></svg></div>
        </div>
      </div>
      <div class="work-info">
        <span class="work-tag">SaaS Explainer</span>
        <div class="work-title">Product Feature Breakdown</div>
        <div class="work-meta">Short · Motion Graphics</div>
      </div>
    </div>

    <!-- Video 2: 4PSa1qhU-wU -->
    <div class="work-card reveal">
      <div class="work-thumb" id="thumb-2">
        <iframe src="https://www.youtube.com/embed/4PSa1qhU-wU?rel=0&modestbranding=1" title="App Walkthrough Animation" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
        <div class="thumb-overlay" onclick="playVideo('thumb-2')">
          <div class="play-btn"><svg viewBox="0 0 16 16" fill="none"><path d="M4 2.5L13 8L4 13.5V2.5Z" fill="white"/></svg></div>
        </div>
      </div>
      <div class="work-info">
        <span class="work-tag">App Explanation</span>
        <div class="work-title">App Walkthrough Animation</div>
        <div class="work-meta">2D Animation · Motion Design</div>
      </div>
    </div>

    <!-- Video 3: tirW1hHvtiI -->
    <div class="work-card reveal">
      <div class="work-thumb" id="thumb-3">
        <iframe src="https://www.youtube.com/embed/tirW1hHvtiI?rel=0&modestbranding=1" title="Animated Explainer Video" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
        <div class="thumb-overlay" onclick="playVideo('thumb-3')">
          <div class="play-btn"><svg viewBox="0 0 16 16" fill="none"><path d="M4 2.5L13 8L4 13.5V2.5Z" fill="white"/></svg></div>
        </div>
      </div>
      <div class="work-info">
        <span class="work-tag">Motion Graphics</span>
        <div class="work-title">Animated Explainer Video</div>
        <div class="work-meta">Kinetic Typography · 2D Animation</div>
      </div>
    </div>

    <!-- Video 4: 4gLnfYropqc -->
    <div class="work-card reveal">
      <div class="work-thumb" id="thumb-4">
        <iframe src="https://www.youtube.com/embed/4gLnfYropqc?rel=0&modestbranding=1" title="Talking Head with Motion Overlays" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
        <div class="thumb-overlay" onclick="playVideo('thumb-4')">
          <div class="play-btn"><svg viewBox="0 0 16 16" fill="none"><path d="M4 2.5L13 8L4 13.5V2.5Z" fill="white"/></svg></div>
        </div>
      </div>
      <div class="work-info">
        <span class="work-tag">Talking Head</span>
        <div class="work-title">Talking Head with Motion Overlays</div>
        <div class="work-meta">Editing · Motion Overlay · Captions</div>
      </div>
    </div>

  </div>
</section>

<!-- REVIEWS -->
<section class="reviews-section" id="reviews">
  <div class="reveal" style="text-align:center; max-width:560px; margin:0 auto 0.5rem;">
    <div class="section-label">Testimonials</div>
    <h2 class="section-title" style="max-width:100%;">What clients are saying</h2>
  </div>
  <div class="reviews-grid">
    <div class="review-card reveal">
      <div class="stars">★★★★★</div>
      <p class="review-text">"Absolutely blew me away. Getoz took our complicated product and made it look effortless in under 30 seconds. Our demo conversion went up significantly after using his animation."</p>
      <div class="reviewer">
        <div class="reviewer-avatar">SJ</div>
        <div><div class="reviewer-name">Sarah J.</div><div class="reviewer-role">Product Lead, NovaSaaS</div></div>
      </div>
    </div>
    <div class="review-card reveal" style="border-color:rgba(212,244,90,0.2)">
      <div class="stars">★★★★★</div>
      <p class="review-text">"Delivered in 3 days and the quality was insane. Exactly the clean motion design our brand needed. Will definitely be coming back for our next product launch."</p>
      <div class="reviewer">
        <div class="reviewer-avatar">MR</div>
        <div><div class="reviewer-name">Marcus R.</div><div class="reviewer-role">Founder, Stackly.io</div></div>
      </div>
    </div>
    <div class="review-card reveal">
      <div class="stars">★★★★★</div>
      <p class="review-text">"Professional, fast, and deeply understands SaaS. Getoz didn't just animate — he helped us simplify our entire messaging. The talking head edit was super polished."</p>
      <div class="reviewer">
        <div class="reviewer-avatar">AL</div>
        <div><div class="reviewer-name">Aisha L.</div><div class="reviewer-role">Marketing Dir., Clarityx</div></div>
      </div>
    </div>
  </div>
</section>

<!-- PRICING -->
<section class="pricing-section" id="pricing">
  <div class="reveal" style="text-align:center;">
    <div class="section-label">Packages</div>
    <h2 class="section-title" style="max-width:100%; text-align:center; margin:0 auto;">Simple, transparent pricing.</h2>
    <p class="pricing-subtitle">No hidden fees. Pick a package and let's get started.</p>
  </div>
  <div class="pricing-grid">
    <div class="pricing-card reveal">
      <div class="plan-name">Starter</div>
      <div class="plan-tagline">Perfect for short promos & ads</div>
      <div class="plan-price"><span>$</span>40</div>
      <div class="plan-duration">15–20 second animation · Delivered in 3 days</div>
      <ul class="plan-features">
        <li><span class="check">✓</span>Up to 20 seconds animation</li>
        <li><span class="check">✓</span>Custom motion graphics</li>
        <li><span class="check">✓</span>1 revision included</li>
        <li><span class="check">✓</span>Delivered in 3 days</li>
        <li><span class="check">✓</span>HD export (1080p)</li>
      </ul>
      <a href="#contact" class="plan-cta plan-cta-outline">Get Started →</a>
    </div>
    <div class="pricing-card featured reveal">
      <div class="featured-badge">Most Popular</div>
      <div class="plan-name">Growth</div>
      <div class="plan-tagline">Ideal for SaaS & app explanations</div>
      <div class="plan-price" style="color:var(--accent)"><span>$</span>75</div>
      <div class="plan-duration">30–40 second animation · Delivered in 4–5 days</div>
      <ul class="plan-features">
        <li><span class="check">✓</span>Up to 40 seconds animation</li>
        <li><span class="check">✓</span>Advanced motion graphics</li>
        <li><span class="check">✓</span>2 revisions included</li>
        <li><span class="check">✓</span>Delivered in 4–5 days</li>
        <li><span class="check">✓</span>4K export available</li>
        <li><span class="check">✓</span>Script feedback included</li>
      </ul>
      <a href="#contact" class="plan-cta plan-cta-filled">Get Started →</a>
    </div>
    <div class="pricing-card reveal">
      <div class="plan-name">Pro</div>
      <div class="plan-tagline">Full-length product explainer</div>
      <div class="plan-price"><span>$</span>100</div>
      <div class="plan-duration">1 minute animation · Delivered in 5 days</div>
      <ul class="plan-features">
        <li><span class="check">✓</span>Up to 60 seconds animation</li>
        <li><span class="check">✓</span>Premium motion & storytelling</li>
        <li><span class="check">✓</span>3 revisions included</li>
        <li><span class="check">✓</span>Delivered in 5 days</li>
        <li><span class="check">✓</span>4K export + source file</li>
        <li><span class="check">✓</span>Script writing assistance</li>
      </ul>
      <a href="#contact" class="plan-cta plan-cta-outline">Get Started →</a>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section class="contact-section" id="contact">
  <div class="contact-inner">
    <div class="contact-left reveal">
      <div class="section-label">Contact</div>
      <h2 class="section-title">Let's make something great together.</h2>
      <p>Have a project in mind? Drop me an email or DM me on Instagram — I'll get back to you within 24 hours.</p>

      <div class="contact-links">

        <!-- Email -->
        <a class="contact-link" href="mailto:fxgrvstudio@gmail.com">
          <div class="contact-link-icon">
            <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
              <rect x="2" y="4" width="20" height="16" rx="3" stroke="#D4F45A" stroke-width="1.5"/>
              <path d="M2 8l10 6 10-6" stroke="#D4F45A" stroke-width="1.5" stroke-linecap="round"/>
            </svg>
          </div>
          <div class="contact-link-info">
            <strong>Email</strong>
            <span>fxgrvstudio@gmail.com</span>
          </div>
        </a>

        <!-- Instagram -->
        <a class="contact-link" href="https://instagram.com/getozmedia" target="_blank">
          <div class="contact-link-icon">
            <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
              <rect x="2" y="2" width="20" height="20" rx="6" stroke="#D4F45A" stroke-width="1.5"/>
              <circle cx="12" cy="12" r="4.5" stroke="#D4F45A" stroke-width="1.5"/>
              <circle cx="17.5" cy="6.5" r="1" fill="#D4F45A"/>
            </svg>
          </div>
          <div class="contact-link-info">
            <strong>Instagram</strong>
            <span>@getozmedia</span>
          </div>
        </a>

      </div>
    </div>

    <!-- FORM -->
    <div class="reveal">
      <div class="contact-form">
        <div class="form-group">
          <label class="form-label">Your Name</label>
          <input class="form-input" type="text" placeholder="John Smith">
        </div>
        <div class="form-group">
          <label class="form-label">Email Address</label>
          <input class="form-input" type="email" placeholder="john@company.com">
        </div>
        <div class="form-group">
          <label class="form-label">Project Type</label>
          <input class="form-input" type="text" placeholder="SaaS explainer, Talking head, etc.">
        </div>
        <div class="form-group">
          <label class="form-label">Tell me about your project</label>
          <textarea class="form-textarea" placeholder="Describe your animation needs, target audience, preferred package..."></textarea>
        </div>
        <button class="form-submit">Send Message →</button>
      </div>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <a href="#" class="logo">Getoz<span style="color:var(--accent)">.</span></a>
  <p>© 2025 Getoz · Motion Designer · Rajasthan, India</p>
  <p style="font-size:0.78rem; color:#2e2e2e;">Made with motion & intent.</p>
</footer>

<script>
  function playVideo(id) {
    const thumb = document.getElementById(id);
    if (!thumb) return;
    const iframe = thumb.querySelector('iframe');
    if (!iframe.src.includes('autoplay')) iframe.src = iframe.src + '&autoplay=1';
    thumb.classList.add('playing');
  }

  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry, i) => {
      if (entry.isIntersecting) setTimeout(() => entry.target.classList.add('visible'), i * 80);
    });
  }, { threshold: 0.1, rootMargin: '0px 0px -40px 0px' });
  document.querySelectorAll('.reveal').forEach(el => observer.observe(el));

  document.querySelectorAll('.works-grid .work-card, .reviews-grid .review-card, .pricing-grid .pricing-card, .skills-cards .skill-card').forEach((el, i) => {
    el.style.transitionDelay = (i * 0.09) + 's';
  });

  const sections = document.querySelectorAll('section[id]');
  window.addEventListener('scroll', () => {
    let current = '';
    sections.forEach(s => { if (window.scrollY >= s.offsetTop - 120) current = s.getAttribute('id'); });
    document.querySelectorAll('nav ul a').forEach(a => {
      a.style.color = a.getAttribute('href') === '#' + current ? 'var(--text)' : '';
    });
  });
</script>
</body>
</html>
