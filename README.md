<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>BrokenBrainCells</title>
<meta name="description" content="BrokenBrainCells — developer profile.">
<style>
  @import url('https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500;700;800&family=IBM+Plex+Sans:wght@400;500;600&display=swap');

  :root{
    --bg: #0B0E14;
    --bg-raised: #10141d;
    --ink: #E9EAEE;
    --ink-dim: #8890A2;
    --synapse: #8B7FE8;
    --synapse-2: #5CD9C8;
    --glitch: #FF5C7A;
    --line: #1E2330;
    --radius: 10px;
  }

  *{ box-sizing: border-box; margin:0; padding:0; }

  html{ scroll-behavior: smooth; }

  body{
    background: var(--bg);
    color: var(--ink);
    font-family: 'IBM Plex Sans', sans-serif;
    line-height: 1.6;
    overflow-x: hidden;
  }

  ::selection{ background: var(--synapse); color: #0B0E14; }

  a{ color: inherit; text-decoration: none; }

  .mono{ font-family: 'JetBrains Mono', monospace; }

  /* ---------- Background synapse canvas ---------- */
  #synapse-canvas{
    position: fixed;
    inset: 0;
    z-index: 0;
    opacity: 0.55;
  }

  /* ---------- Layout shell ---------- */
  .wrap{
    position: relative;
    z-index: 1;
    max-width: 860px;
    margin: 0 auto;
    padding: 0 28px;
  }

  header.nav{
    position: sticky;
    top: 0;
    z-index: 10;
    backdrop-filter: blur(10px);
    background: rgba(11,14,20,0.75);
    border-bottom: 1px solid var(--line);
  }
  header.nav .wrap{
    display:flex;
    align-items:center;
    justify-content:space-between;
    height: 60px;
    max-width: 860px;
  }
  .brand{
    font-family: 'JetBrains Mono', monospace;
    font-weight: 700;
    font-size: 14px;
    letter-spacing: 0.02em;
    color: var(--ink);
    display:flex; align-items:center; gap:8px;
  }
  .brand .dot{
    width:7px;height:7px;border-radius:50%;
    background: var(--synapse-2);
    box-shadow: 0 0 8px var(--synapse-2);
    animation: pulse-dot 2.2s ease-in-out infinite;
  }
  @keyframes pulse-dot{
    0%,100%{ opacity:1; transform:scale(1); }
    50%{ opacity:.4; transform:scale(0.7); }
  }
  nav.links{ display:flex; gap: 22px; font-size: 13px; }
  nav.links a{
    color: var(--ink-dim);
    font-family:'JetBrains Mono',monospace;
    transition: color .15s ease;
  }
  nav.links a:hover{ color: var(--synapse-2); }

  /* ---------- Hero ---------- */
  .hero{
    min-height: 86vh;
    display:flex;
    flex-direction: column;
    justify-content: center;
    padding-top: 40px;
    padding-bottom: 60px;
  }

  .eyebrow{
    font-family:'JetBrains Mono',monospace;
    font-size: 12.5px;
    color: var(--synapse-2);
    letter-spacing: 0.14em;
    text-transform: uppercase;
    margin-bottom: 22px;
    display:flex;
    align-items:center;
    gap: 10px;
  }
  .eyebrow::before{
    content:'';
    width: 26px; height:1px;
    background: var(--synapse-2);
  }

  h1.glitch-name{
    font-family:'JetBrains Mono',monospace;
    font-weight: 800;
    font-size: clamp(2.6rem, 9vw, 5.2rem);
    line-height: 1.02;
    letter-spacing: -0.02em;
    position: relative;
    color: var(--ink);
    display:inline-block;
  }
  h1.glitch-name .glitch-layer{
    position:absolute; top:0; left:0;
    width:100%; height:100%;
    overflow:hidden;
    color: var(--ink);
  }
  h1.glitch-name .layer-1{
    color: var(--glitch);
    clip-path: inset(0 0 0 0);
    animation: glitch-1 6.5s infinite steps(1);
    mix-blend-mode: screen;
  }
  h1.glitch-name .layer-2{
    color: var(--synapse-2);
    clip-path: inset(0 0 0 0);
    animation: glitch-2 6.5s infinite steps(1);
    mix-blend-mode: screen;
  }
  @keyframes glitch-1{
    0%, 92%, 100%{ clip-path: inset(0 0 0 0); transform: translate(0,0); opacity:0; }
    93%{ clip-path: inset(10% 0 60% 0); transform: translate(-3px,1px); opacity:0.85; }
    94%{ clip-path: inset(60% 0 5% 0); transform: translate(3px,-1px); opacity:0.85; }
    95%{ clip-path: inset(30% 0 40% 0); transform: translate(-2px,0); opacity:0.85; }
    96%{ opacity:0; }
  }
  @keyframes glitch-2{
    0%, 91%, 100%{ clip-path: inset(0 0 0 0); transform: translate(0,0); opacity:0; }
    92%{ clip-path: inset(70% 0 5% 0); transform: translate(3px,0); opacity:0.85; }
    93%{ clip-path: inset(5% 0 70% 0); transform: translate(-3px,1px); opacity:0.85; }
    94%{ clip-path: inset(45% 0 20% 0); transform: translate(2px,-1px); opacity:0.85; }
    95%{ opacity:0; }
  }
  @media (prefers-reduced-motion: reduce){
    h1.glitch-name .layer-1, h1.glitch-name .layer-2{ animation: none; opacity:0; }
    .brand .dot{ animation: none; }
  }

  .tagline{
    margin-top: 26px;
    font-size: clamp(1rem, 2.4vw, 1.2rem);
    color: var(--ink-dim);
    max-width: 46ch;
  }
  .tagline strong{ color: var(--ink); font-weight: 600; }

  .hero-cta{
    margin-top: 36px;
    display:flex;
    gap: 14px;
    flex-wrap: wrap;
  }
  .btn{
    font-family:'JetBrains Mono',monospace;
    font-size: 13.5px;
    padding: 12px 20px;
    border-radius: var(--radius);
    border: 1px solid var(--line);
    transition: border-color .18s ease, transform .18s ease, background .18s ease;
    display:inline-flex; align-items:center; gap:8px;
  }
  .btn.primary{
    background: var(--synapse);
    color: #0B0E14;
    border-color: var(--synapse);
    font-weight: 700;
  }
  .btn.primary:hover{ transform: translateY(-2px); }
  .btn.ghost:hover{
    border-color: var(--synapse-2);
    color: var(--synapse-2);
    transform: translateY(-2px);
  }

  /* ---------- Section shared ---------- */
  section{ padding: 90px 0; border-top: 1px solid var(--line); }
  .section-head{
    display:flex;
    align-items: baseline;
    gap: 14px;
    margin-bottom: 40px;
  }
  .section-head .tag{
    font-family:'JetBrains Mono',monospace;
    font-size: 12px;
    color: var(--synapse-2);
    background: rgba(92,217,200,0.08);
    border: 1px solid rgba(92,217,200,0.25);
    padding: 3px 9px;
    border-radius: 20px;
    white-space: nowrap;
  }
  .section-head h2{
    font-family:'JetBrains Mono',monospace;
    font-size: clamp(1.4rem, 3vw, 1.9rem);
    font-weight: 700;
    letter-spacing: -0.01em;
  }

  /* ---------- About ---------- */
  .about-body{
    color: var(--ink-dim);
    font-size: 1.02rem;
    max-width: 62ch;
  }
  .about-body p + p{ margin-top: 16px; }
  .stack-row{
    margin-top: 34px;
    display:flex;
    flex-wrap: wrap;
    gap: 10px;
  }
  .stack-pill{
    font-family:'JetBrains Mono',monospace;
    font-size: 12.5px;
    color: var(--ink);
    border: 1px solid var(--line);
    background: var(--bg-raised);
    padding: 7px 13px;
    border-radius: 20px;
  }

  /* ---------- Projects ---------- */
  .project-grid{
    display:grid;
    grid-template-columns: 1fr 1fr;
    gap: 18px;
  }
  @media (max-width: 620px){ .project-grid{ grid-template-columns: 1fr; } }

  .project-card{
    background: var(--bg-raised);
    border: 1px solid var(--line);
    border-radius: var(--radius);
    padding: 22px;
    position: relative;
    transition: border-color .18s ease, transform .18s ease;
  }
  .project-card:hover{
    border-color: var(--synapse);
    transform: translateY(-3px);
  }
  .project-card .pname{
    font-family:'JetBrains Mono',monospace;
    font-weight: 700;
    font-size: 15px;
    margin-bottom: 8px;
    display:flex; align-items:center; justify-content:space-between;
  }
  .project-card .pname svg{ opacity:.5; width:15px; height:15px; }
  .project-card p{ color: var(--ink-dim); font-size: 13.6px; margin-bottom: 14px; }
  .project-card .ptags{ display:flex; gap:7px; flex-wrap:wrap; }
  .project-card .ptags span{
    font-family:'JetBrains Mono',monospace;
    font-size: 11px;
    color: var(--synapse-2);
  }
  .project-card.placeholder{
    border-style: dashed;
    display:flex; align-items:center; justify-content:center;
    color: var(--ink-dim);
    font-family:'JetBrains Mono',monospace;
    font-size: 13px;
    text-align:center;
    min-height: 140px;
  }

  /* ---------- Contact ---------- */
  .contact-grid{
    display:grid;
    grid-template-columns: repeat(auto-fit, minmax(160px,1fr));
    gap: 14px;
  }
  .contact-card{
    border: 1px solid var(--line);
    border-radius: var(--radius);
    padding: 18px;
    background: var(--bg-raised);
    transition: border-color .18s ease, transform .18s ease;
  }
  .contact-card:hover{ border-color: var(--synapse-2); transform: translateY(-3px); }
  .contact-card .clabel{
    font-family:'JetBrains Mono',monospace;
    font-size: 11px;
    color: var(--ink-dim);
    text-transform: uppercase;
    letter-spacing: .08em;
    margin-bottom: 6px;
  }
  .contact-card .cvalue{
    font-family:'JetBrains Mono',monospace;
    font-size: 14px;
    color: var(--ink);
  }

  footer{
    padding: 40px 0 60px;
    color: var(--ink-dim);
    font-family:'JetBrains Mono',monospace;
    font-size: 12px;
    display:flex;
    justify-content: space-between;
    flex-wrap: wrap;
    gap: 10px;
  }

  :focus-visible{
    outline: 2px solid var(--synapse-2);
    outline-offset: 3px;
  }
</style>
</head>
<body>

<canvas id="synapse-canvas"></canvas>

<header class="nav">
  <div class="wrap">
    <div class="brand"><span class="dot"></span>brokenbraincells</div>
    <nav class="links">
      <a href="#about">about</a>
      <a href="#projects">projects</a>
      <a href="#contact">contact</a>
    </nav>
  </div>
</header>

<div class="wrap">

  <section class="hero" id="top">
    <div class="eyebrow">status: 6 neurons firing, rest on standby</div>
    <h1 class="glitch-name">
      BrokenBrainCells
      <span class="glitch-layer layer-1" aria-hidden="true">BrokenBrainCells</span>
      <span class="glitch-layer layer-2" aria-hidden="true">BrokenBrainCells</span>
    </h1>
    <p class="tagline">
      I write code that mostly works, powered by <strong>caffeine</strong> and the handful of
      brain cells still on payroll. Here's what's shipped, what's broken, and how to reach me.
    </p>
    <div class="hero-cta">
      <a class="btn primary" href="https://github.com/BrokenBrainCells" target="_blank" rel="noopener">View GitHub →</a>
      <a class="btn ghost" href="#projects">See projects</a>
    </div>
  </section>

  <section id="about">
    <div class="section-head">
      <span class="tag">01</span>
      <h2>about</h2>
    </div>
    <div class="about-body">
      <p>
        This page is a starting point for your GitHub profile — swap in your real bio here.
        A line or two about what you build, what you're learning, and what you're into is usually enough.
      </p>
      <p>
        Keep it honest and specific. "I build small tools that solve annoying problems" beats
        "passionate full-stack developer" every time.
      </p>
    </div>
    <div class="stack-row">
      <span class="stack-pill">JavaScript</span>
      <span class="stack-pill">Python</span>
      <span class="stack-pill">React</span>
      <span class="stack-pill">edit-me.exe</span>
    </div>
  </section>

  <section id="projects">
    <div class="section-head">
      <span class="tag">02</span>
      <h2>projects</h2>
    </div>
    <div class="project-grid">

      <div class="project-card">
        <div class="pname">project-one
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"/><path d="M15 3h6v6"/><path d="M10 14 21 3"/></svg>
        </div>
        <p>Replace this with a real repo — what it does and why you built it, in one or two sentences.</p>
        <div class="ptags"><span>#js</span><span>#cli</span></div>
      </div>

      <div class="project-card">
        <div class="pname">project-two
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"/><path d="M15 3h6v6"/><path d="M10 14 21 3"/></svg>
        </div>
        <p>Another repo slot. Link it, tag it, done. Delete this card if you'd rather keep the grid tighter.</p>
        <div class="ptags"><span>#python</span><span>#automation</span></div>
      </div>

      <div class="project-card placeholder">
        + add another project
      </div>

      <div class="project-card placeholder">
        + add another project
      </div>

    </div>
  </section>

  <section id="contact">
    <div class="section-head">
      <span class="tag">03</span>
      <h2>contact</h2>
    </div>
    <div class="contact-grid">
      <a class="contact-card" href="https://github.com/BrokenBrainCells" target="_blank" rel="noopener">
        <div class="clabel">GitHub</div>
        <div class="cvalue">@BrokenBrainCells</div>
      </a>
      <a class="contact-card" href="mailto:you@example.com">
        <div class="clabel">Email</div>
        <div class="cvalue">you@example.com</div>
      </a>
      <a class="contact-card" href="#">
        <div class="clabel">Twitter / X</div>
        <div class="cvalue">@handle</div>
      </a>
    </div>
  </section>

  <footer>
    <span>© <span id="year"></span> BrokenBrainCells</span>
    <span>built with what's left of the brain</span>
  </footer>

</div>

<script>
  document.getElementById('year').textContent = new Date().getFullYear();

  // ---- Synapse network background ----
  (function(){
    const canvas = document.getElementById('synapse-canvas');
    const ctx = canvas.getContext('2d');
    let w, h, nodes = [];
    const prefersReduced = window.matchMedia('(prefers-reduced-motion: reduce)').matches;

    function resize(){
      w = canvas.width = window.innerWidth;
      h = canvas.height = document.body.scrollHeight;
    }
    window.addEventListener('resize', resize);
    resize();

    const NODE_COUNT = Math.max(24, Math.floor((w*h) / 65000));
    for(let i=0;i<NODE_COUNT;i++){
      nodes.push({
        x: Math.random()*w,
        y: Math.random()*h,
        vx: (Math.random()-0.5)*0.15,
        vy: (Math.random()-0.5)*0.15,
        r: Math.random()*1.6 + 1,
        fire: Math.random()*Math.PI*2
      });
    }

    const maxDist = 150;

    function draw(){
      ctx.clearRect(0,0,w,h);

      for(let i=0;i<nodes.length;i++){
        const a = nodes[i];
        for(let j=i+1;j<nodes.length;j++){
          const b = nodes[j];
          const dx = a.x-b.x, dy = a.y-b.y;
          const dist = Math.sqrt(dx*dx+dy*dy);
          if(dist < maxDist){
            const alpha = (1 - dist/maxDist) * 0.18;
            ctx.strokeStyle = `rgba(139,127,232,${alpha})`;
            ctx.lineWidth = 1;
            ctx.beginPath();
            ctx.moveTo(a.x,a.y);
            ctx.lineTo(b.x,b.y);
            ctx.stroke();
          }
        }
      }

      for(const n of nodes){
        if(!prefersReduced){
          n.x += n.vx;
          n.y += n.vy;
          if(n.x < 0 || n.x > w) n.vx *= -1;
          if(n.y < 0 || n.y > h) n.vy *= -1;
          n.fire += 0.02;
        }
        const pulse = (Math.sin(n.fire)+1)/2;
        const glow = 0.4 + pulse*0.6;
        ctx.beginPath();
        ctx.arc(n.x, n.y, n.r + pulse*1.2, 0, Math.PI*2);
        ctx.fillStyle = `rgba(92,217,200,${glow*0.8})`;
        ctx.fill();
      }

      if(!prefersReduced){
        requestAnimationFrame(draw);
      }
    }
    draw();
    if(prefersReduced){
      // draw a single static frame
    }
  })();
</script>

</body>
</html>
