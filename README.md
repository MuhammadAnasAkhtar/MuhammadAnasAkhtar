<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Muhammad Anas Akhtar — AI Engineer</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;600;700&family=Inter:wght@400;500;600&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  :root{
    --bg:#070a12;
    --surface:#10141f;
    --surface-2:#151b2a;
    --line: rgba(220,227,240,0.09);
    --text:#dce3f0;
    --muted:#7480a0;
    --cyan:#ff7a45;
    --violet:#e8542e;
    --amber:#ffcf70;
  }
  *{box-sizing:border-box;}
  html{scroll-behavior:smooth;}
  body{
    margin:0;
    background:var(--bg);
    color:var(--text);
    font-family:'Inter', sans-serif;
    overflow-x:hidden;
  }
  ::selection{ background: var(--violet); color:#070a12; }

  h1,h2,h3,.display{
    font-family:'Space Grotesk', sans-serif;
    letter-spacing:-0.01em;
  }
  .mono{ font-family:'JetBrains Mono', monospace; }

  /* ---------- HERO ---------- */
  #hero{
    position:relative;
    height:100vh;
    min-height:640px;
    display:flex;
    align-items:center;
    justify-content:center;
    overflow:hidden;
    background:
      radial-gradient(ellipse at 50% 20%, rgba(232,84,46,0.10), transparent 55%),
      radial-gradient(ellipse at 30% 80%, rgba(255,122,69,0.08), transparent 55%),
      var(--bg);
  }
  #graph-canvas{
    position:absolute;
    inset:0;
    width:100%;
    height:100%;
    display:block;
  }
  .hero-content{
    position:relative;
    z-index:2;
    text-align:center;
    padding:0 24px;
    pointer-events:none;
  }
  .eyebrow{
    display:inline-flex;
    align-items:center;
    gap:8px;
    font-family:'JetBrains Mono', monospace;
    font-size:12.5px;
    letter-spacing:0.14em;
    text-transform:uppercase;
    color:var(--cyan);
    background:rgba(255,122,69,0.08);
    border:1px solid rgba(255,122,69,0.25);
    padding:6px 14px;
    border-radius:100px;
    margin-bottom:26px;
    pointer-events:auto;
  }
  .eyebrow .dot{
    width:6px; height:6px; border-radius:50%;
    background:var(--cyan);
    box-shadow:0 0 8px var(--cyan);
  }
  h1.name{
    font-size:clamp(2.6rem, 7vw, 5.2rem);
    line-height:1.02;
    margin:0 0 14px;
    background:linear-gradient(120deg, #f2f5fb 30%, var(--cyan) 65%, var(--violet) 100%);
    -webkit-background-clip:text;
    background-clip:text;
    color:transparent;
    font-weight:700;
  }
  .role{
    font-size:clamp(1rem, 2.4vw, 1.35rem);
    color:var(--muted);
    margin:0 0 34px;
    font-weight:500;
  }
  .role strong{ color:var(--text); font-weight:600; }
  .hero-links{
    display:flex;
    flex-wrap:wrap;
    gap:12px;
    justify-content:center;
    pointer-events:auto;
  }
  .pill{
    font-family:'JetBrains Mono', monospace;
    font-size:13px;
    text-decoration:none;
    color:var(--text);
    border:1px solid var(--line);
    background:rgba(255,255,255,0.02);
    padding:9px 18px;
    border-radius:8px;
    transition:border-color .25s ease, transform .25s ease, background .25s ease;
  }
  .pill:hover{
    border-color:var(--cyan);
    background:rgba(255,122,69,0.08);
    transform:translateY(-2px);
  }
  .scroll-cue{
    position:absolute;
    bottom:28px;
    left:50%;
    transform:translateX(-50%);
    font-family:'JetBrains Mono', monospace;
    font-size:11px;
    letter-spacing:0.15em;
    text-transform:uppercase;
    color:var(--muted);
    z-index:2;
    display:flex;
    flex-direction:column;
    align-items:center;
    gap:8px;
  }
  .scroll-cue .line{
    width:1px; height:26px;
    background:linear-gradient(var(--cyan), transparent);
    animation:scrollpulse 1.8s ease-in-out infinite;
  }
  @keyframes scrollpulse{ 0%,100%{opacity:.2;} 50%{opacity:1;} }

  /* ---------- SECTIONS ---------- */
  section{
    max-width:1080px;
    margin:0 auto;
    padding:110px 24px;
    position:relative;
  }
  .section-head{
    display:flex;
    align-items:baseline;
    gap:16px;
    margin-bottom:48px;
  }
  .section-num{
    font-family:'JetBrains Mono', monospace;
    color:var(--muted);
    font-size:13px;
  }
  .section-head h2{
    font-size:clamp(1.6rem, 3vw, 2.2rem);
    margin:0;
    font-weight:600;
  }
  .section-head::after{
    content:"";
    flex:1;
    height:1px;
    background:var(--line);
  }

  .reveal{
    opacity:0;
    transform:translateY(28px);
    transition:opacity .8s ease, transform .8s ease;
  }
  .reveal.in{ opacity:1; transform:translateY(0); }

  #about p{
    font-size:1.05rem;
    line-height:1.85;
    color:#c4cce0;
    max-width:760px;
  }
  #about .metric-row{
    display:flex;
    gap:36px;
    margin-top:36px;
    flex-wrap:wrap;
  }
  .metric{
    border-left:2px solid var(--cyan);
    padding-left:16px;
  }
  .metric .num{
    font-family:'Space Grotesk', sans-serif;
    font-size:2rem;
    font-weight:700;
    color:var(--text);
  }
  .metric .lbl{
    font-size:12.5px;
    color:var(--muted);
    font-family:'JetBrains Mono', monospace;
  }

  /* Expertise cards w/ tilt */
  .grid{
    display:grid;
    grid-template-columns:repeat(auto-fit, minmax(230px, 1fr));
    gap:18px;
  }
  .card{
    background:linear-gradient(160deg, var(--surface), var(--surface-2));
    border:1px solid var(--line);
    border-radius:14px;
    padding:22px 22px 20px;
    transition:transform .12s ease, border-color .3s ease, box-shadow .3s ease;
    transform-style:preserve-3d;
    will-change:transform;
  }
  .card:hover{
    border-color:rgba(232,84,46,0.4);
    box-shadow:0 20px 40px -20px rgba(255,122,69,0.25);
  }
  .card h3{
    font-size:1.02rem;
    margin:0 0 10px;
    color:var(--cyan);
    font-weight:600;
  }
  .card p{
    margin:0;
    font-size:13.5px;
    line-height:1.6;
    color:var(--muted);
  }
  .tag-row{ display:flex; flex-wrap:wrap; gap:6px; margin-top:12px; }
  .tag{
    font-family:'JetBrains Mono', monospace;
    font-size:11px;
    color:var(--violet);
    background:rgba(232,84,46,0.08);
    border:1px solid rgba(232,84,46,0.2);
    padding:3px 9px;
    border-radius:100px;
  }

  /* Timeline */
  .timeline{
    position:relative;
    padding-left:28px;
    border-left:1px solid var(--line);
  }
  .t-item{ position:relative; padding-bottom:44px; }
  .t-item:last-child{ padding-bottom:0; }
  .t-item::before{
    content:"";
    position:absolute;
    left:-33px;
    top:4px;
    width:10px; height:10px;
    border-radius:50%;
    background:var(--bg);
    border:2px solid var(--cyan);
    box-shadow:0 0 12px rgba(255,122,69,0.6);
  }
  .t-item .t-date{
    font-family:'JetBrains Mono', monospace;
    font-size:12px;
    color:var(--muted);
    margin-bottom:6px;
    display:block;
  }
  .t-item h3{ margin:0 0 10px; font-size:1.1rem; }
  .t-item ul{ margin:0; padding-left:18px; color:#c4cce0; font-size:14px; line-height:1.75; }
  .t-item li::marker{ color:var(--violet); }

  /* Projects */
  .proj-card{
    background:var(--surface);
    border:1px solid var(--line);
    border-radius:14px;
    padding:24px;
    transition:transform .12s ease, border-color .3s ease;
    transform-style:preserve-3d;
  }
  .proj-card:hover{ border-color:rgba(255,122,69,0.4); }
  .proj-stack{
    font-family:'JetBrains Mono', monospace;
    font-size:11.5px;
    color:var(--amber);
    margin-bottom:10px;
    display:block;
  }
  .proj-card h3{ margin:0 0 8px; font-size:1.05rem; }
  .proj-card p{ margin:0; font-size:13.5px; color:var(--muted); line-height:1.65; }

  /* Achievements */
  .ach-list{ list-style:none; margin:0; padding:0; display:grid; gap:14px; }
  .ach-list li{
    display:flex;
    gap:14px;
    align-items:flex-start;
    font-size:14.5px;
    color:#c4cce0;
    line-height:1.6;
  }
  .ach-list .marker{
    color:var(--amber);
    font-family:'JetBrains Mono', monospace;
    flex-shrink:0;
  }

  /* two-col */
  .twocol{ display:grid; grid-template-columns:1fr 1fr; gap:40px; }
  @media (max-width:720px){ .twocol{ grid-template-columns:1fr; } }
  .mini-list{ list-style:none; margin:0; padding:0; }
  .mini-list li{
    padding:12px 0;
    border-bottom:1px solid var(--line);
    font-size:14px;
    display:flex;
    justify-content:space-between;
    gap:12px;
    color:#c4cce0;
  }
  .mini-list li span.p{ color:var(--muted); font-family:'JetBrains Mono', monospace; font-size:12px; text-align:right;}

  /* Footer / contact */
  #contact{
    text-align:center;
    padding-bottom:140px;
  }
  #contact h2{ font-size:clamp(1.8rem,4vw,2.6rem); margin-bottom:14px; }
  #contact p{ color:var(--muted); margin-bottom:36px; }
  footer{
    text-align:center;
    padding:28px 24px 40px;
    color:var(--muted);
    font-family:'JetBrains Mono', monospace;
    font-size:12px;
    border-top:1px solid var(--line);
  }

  @media (prefers-reduced-motion: reduce){
    .reveal{ transition:none; opacity:1; transform:none; }
    .scroll-cue .line{ animation:none; }
  }
</style>
</head>
<body>

<section id="hero">
  <canvas id="graph-canvas"></canvas>
  <div class="hero-content">
    <div class="eyebrow"><span class="dot"></span> Open to Remote · Relocation · Visa Sponsorship</div>
    <h1 class="name">Muhammad Anas Akhtar</h1>
    <p class="role">AI Engineer — <strong>Generative AI</strong>, <strong>Agentic Systems</strong> &amp; <strong>MLOps</strong></p>
    <div class="hero-links">
      <a class="pill" href="mailto:muhammadanasakhtar19@gmail.com">email</a>
      <a class="pill" href="https://www.linkedin.com/in/muhammad-anas-akhtar-78644a253/" target="_blank" rel="noopener">linkedin</a>
      <a class="pill" href="https://github.com/MuhammadAnasAkhtar" target="_blank" rel="noopener">github</a>
      <a class="pill" href="https://huggingface.co/ANASAKHTAR" target="_blank" rel="noopener">hugging face</a>
      <a class="pill" href="https://muhammad-anas-akhtar-m8xc4yv.gamma.site/" target="_blank" rel="noopener">portfolio</a>
    </div>
  </div>
  <div class="scroll-cue"><span>scroll</span><span class="line"></span></div>
</section>

<section id="about">
  <div class="section-head reveal"><span class="section-num">01</span><h2>About</h2></div>
  <div class="reveal">
    <p>I build production-grade RAG pipelines, autonomous multi-agent workflows, and MLOps infrastructure that solve real enterprise problems — spanning healthcare AI, business automation, and cloud deployment. I hold a BS in Artificial Intelligence from The Islamia University of Bahawalpur (2020–2024) and have delivered independent consulting work for clients in the USA and Austria.</p>
    <div class="metric-row">
      <div class="metric"><div class="num">15%</div><div class="lbl">retrieval accuracy gain</div></div>
      <div class="metric"><div class="num">2</div><div class="lbl">countries served as consultant</div></div>
      <div class="metric"><div class="num">5+</div><div class="lbl">certifications completed</div></div>
    </div>
  </div>
</section>

<section id="expertise">
  <div class="section-head reveal"><span class="section-num">02</span><h2>Technical Expertise</h2></div>
  <div class="grid">
    <div class="card reveal">
      <h3>Generative AI &amp; LLMs</h3>
      <p>Building and adapting large language models for enterprise use cases.</p>
      <div class="tag-row"><span class="tag">LLaMA-2</span><span class="tag">GPT</span><span class="tag">Mistral</span><span class="tag">RAG</span><span class="tag">LoRA</span></div>
    </div>
    <div class="card reveal">
      <h3>Agentic Frameworks</h3>
      <p>Orchestrating autonomous, observable multi-agent systems.</p>
      <div class="tag-row"><span class="tag">LangGraph</span><span class="tag">LangChain</span><span class="tag">CrewAI</span><span class="tag">AutoGen</span><span class="tag">DSPy</span></div>
    </div>
    <div class="card reveal">
      <h3>MLOps &amp; Cloud</h3>
      <p>Shipping and monitoring models in production environments.</p>
      <div class="tag-row"><span class="tag">SageMaker</span><span class="tag">Vertex AI</span><span class="tag">Docker</span><span class="tag">FastAPI</span></div>
    </div>
    <div class="card reveal">
      <h3>Vector Databases</h3>
      <p>Semantic search infrastructure for retrieval-heavy systems.</p>
      <div class="tag-row"><span class="tag">Pinecone</span><span class="tag">ChromaDB</span><span class="tag">Weaviate</span><span class="tag">FAISS</span></div>
    </div>
    <div class="card reveal">
      <h3>Machine Learning</h3>
      <p>Core ML across language and vision, tuned for real constraints.</p>
      <div class="tag-row"><span class="tag">NLP</span><span class="tag">Computer Vision</span><span class="tag">Predictive Analytics</span></div>
    </div>
    <div class="card reveal">
      <h3>Automation &amp; Tools</h3>
      <p>Connecting models to workflows people actually use.</p>
      <div class="tag-row"><span class="tag">n8n</span><span class="tag">Make.com</span><span class="tag">Python</span><span class="tag">SQL</span></div>
    </div>
  </div>
</section>

<section id="experience">
  <div class="section-head reveal"><span class="section-num">03</span><h2>Experience</h2></div>
  <div class="timeline">
    <div class="t-item reveal">
      <span class="t-date">Jan 2024 — Present</span>
      <h3>Generative AI Engineer</h3>
      <ul>
        <li>Architected scalable RAG pipelines with a 15% improvement in retrieval accuracy through optimized vector search</li>
        <li>Built autonomous multi-agent workflows using LangGraph with full observability via LangSmith</li>
        <li>Deployed production AI models on AWS SageMaker &amp; GCP Vertex AI with automated scaling and monitoring</li>
        <li>Fine-tuned LLaMA-2 and OpenAI models using PEFT/LoRA for enterprise document processing</li>
      </ul>
    </div>
    <div class="t-item reveal">
      <span class="t-date">Feb 2022 — Dec 2023</span>
      <h3>Machine Learning Engineer</h3>
      <ul>
        <li>Engineered end-to-end ML pipelines for NLP and predictive analytics in global startup environments</li>
        <li>Optimized model inference through hyperparameter tuning and compression, reducing real-time latency</li>
        <li>Containerized ML workflows with Docker for seamless CI/CD across cloud platforms</li>
      </ul>
    </div>
  </div>
</section>

<section id="projects">
  <div class="section-head reveal"><span class="section-num">04</span><h2>Featured Projects</h2></div>
  <div class="grid">
    <div class="proj-card reveal">
      <span class="proj-stack">LLaMA-2 · LangChain · Pinecone · RAG</span>
      <h3>AI-Powered Medical Document QA Chatbot</h3>
      <p>Production-grade chatbot for clinical document querying with multi-stage RAG, contextual memory, and semantic chunking for precise medical retrieval.</p>
    </div>
    <div class="proj-card reveal">
      <span class="proj-stack">OpenAI · LangChain · RAG · FastAPI</span>
      <h3>ICD &amp; CPT Medical Billing Predictor</h3>
      <p>Maps raw clinical notes to standardized billing codes with 15% improved retrieval quality, reducing manual billing errors.</p>
    </div>
    <div class="proj-card reveal">
      <span class="proj-stack">Speech Synthesis · Deep Learning · Python</span>
      <h3>AI Voice Cloning &amp; Text-to-Speech</h3>
      <p>Realistic voice cloning generating natural speech from minimal reference audio, applied to accessibility and content automation.</p>
    </div>
    <div class="proj-card reveal">
      <span class="proj-stack">LLMs · LangChain · Python</span>
      <h3>AI-Based Smart Interview Assistant</h3>
      <p>Automated candidate evaluation system that conducts structured AI-driven interviews and generates recruiter-ready reports.</p>
    </div>
    <div class="proj-card reveal">
      <span class="proj-stack">CrewAI · LangGraph · LangSmith</span>
      <h3>Multi-Agent Research Workflow</h3>
      <p>Orchestrates specialized AI agents for autonomous research, data gathering, and report generation with full traceability.</p>
    </div>
  </div>
</section>

<section id="achievements">
  <div class="section-head reveal"><span class="section-num">05</span><h2>Key Achievements</h2></div>
  <ul class="ach-list reveal">
    <li><span class="marker">→</span> Designed RAG solutions achieving 15% improved retrieval quality for enterprise clients</li>
    <li><span class="marker">→</span> Served international clients across the USA and Austria as an independent AI consultant</li>
    <li><span class="marker">→</span> Built and deployed multi-agent systems with CrewAI, AutoGen, and LangGraph</li>
    <li><span class="marker">→</span> Integrated vector databases — Pinecone, ChromaDB, FAISS — for semantic search at scale</li>
    <li><span class="marker">→</span> Engineered computer vision pipelines for real-time object detection and image captioning</li>
    <li><span class="marker">→</span> Completed 5+ certifications from DeepLearning.AI, IBM, Coursera, and iNeuron</li>
  </ul>
</section>

<section id="creds">
  <div class="section-head reveal"><span class="section-num">06</span><h2>Certifications &amp; Education</h2></div>
  <div class="twocol reveal">
    <div>
      <ul class="mini-list">
        <li>Generative AI with LLMs &amp; Transformers <span class="p">Coursera / DLAI</span></li>
        <li>Enterprise Generative AI <span class="p">IBM</span></li>
        <li>LangChain for LLMs <span class="p">Coursera</span></li>
        <li>AWS &amp; Google Cloud for ML <span class="p">Udemy</span></li>
        <li>Foundational Generative AI <span class="p">iNeuron</span></li>
      </ul>
    </div>
    <div>
      <ul class="mini-list">
        <li>BS, Artificial Intelligence <span class="p">2020 – 2024</span></li>
        <li>The Islamia University of Bahawalpur <span class="p">Pakistan</span></li>
      </ul>
    </div>
  </div>
</section>

<section id="contact">
  <div class="reveal">
    <h2>Let's build something.</h2>
    <p>Open to full-time roles, consulting engagements, and research collaborations —<br>remote, hybrid, or on-site with visa sponsorship.</p>
    <div class="hero-links" style="pointer-events:auto;">
      <a class="pill" href="mailto:muhammadanasakhtar19@gmail.com">muhammadanasakhtar19@gmail.com</a>
      <a class="pill" href="tel:+923247953020">+92-324-7953020</a>
      <a class="pill" href="https://www.linkedin.com/in/muhammad-anas-akhtar-78644a253/" target="_blank" rel="noopener">LinkedIn</a>
      <a class="pill" href="https://github.com/MuhammadAnasAkhtar" target="_blank" rel="noopener">GitHub</a>
    </div>
  </div>
</section>

<footer>AI Engineer · Generative AI · RAG · LangGraph · CrewAI · AWS · GCP</footer>

<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
<script>
/* ---------------- Scroll reveal ---------------- */
const revealEls = document.querySelectorAll('.reveal');
const io = new IntersectionObserver((entries)=>{
  entries.forEach(e=>{
    if(e.isIntersecting){ e.target.classList.add('in'); io.unobserve(e.target); }
  });
}, { threshold: 0.15 });
revealEls.forEach(el=>io.observe(el));

/* ---------------- Card 3D tilt ---------------- */
document.querySelectorAll('.card, .proj-card').forEach(card=>{
  card.addEventListener('mousemove', (e)=>{
    const r = card.getBoundingClientRect();
    const x = (e.clientX - r.left)/r.width - 0.5;
    const y = (e.clientY - r.top)/r.height - 0.5;
    card.style.transform = `perspective(600px) rotateX(${(-y*8).toFixed(2)}deg) rotateY(${(x*8).toFixed(2)}deg) translateY(-2px)`;
  });
  card.addEventListener('mouseleave', ()=>{ card.style.transform = 'perspective(600px) rotateX(0) rotateY(0)'; });
});

/* ---------------- Three.js knowledge-graph hero ---------------- */
(function(){
  const canvas = document.getElementById('graph-canvas');
  const hero = document.getElementById('hero');
  const renderer = new THREE.WebGLRenderer({ canvas, antialias:true, alpha:true });
  renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));
  renderer.setSize(hero.clientWidth, hero.clientHeight);

  const scene = new THREE.Scene();
  const camera = new THREE.PerspectiveCamera(52, hero.clientWidth/hero.clientHeight, 0.1, 100);
  camera.position.set(0, 0, 15);

  const group = new THREE.Group();
  scene.add(group);

  const labels = ["RAG","LangGraph","CrewAI","Fine-Tuning","Vertex AI","SageMaker","Vector DB","Multi-Agent","MLOps","Prompt Eng","Docker","FastAPI"];
  const nodeCount = labels.length;
  const nodes = [];
  const cyan = new THREE.Color(0xff7a45);
  const violet = new THREE.Color(0xe8542e);

  // place nodes on a sphere (fibonacci distribution)
  const radius = 6.2;
  for(let i=0;i<nodeCount;i++){
    const y = 1 - (i/(nodeCount-1))*2;
    const r = Math.sqrt(1-y*y);
    const theta = Math.PI * (1+Math.sqrt(5)) * i;
    const pos = new THREE.Vector3(Math.cos(theta)*r*radius, y*radius, Math.sin(theta)*r*radius);

    const isAccent = i % 3 === 0;
    const color = isAccent ? violet : cyan;
    const geo = new THREE.IcosahedronGeometry(isAccent ? 0.22 : 0.15, 0);
    const mat = new THREE.MeshBasicMaterial({ color, wireframe:false, transparent:true, opacity:0.9 });
    const mesh = new THREE.Mesh(geo, mat);
    mesh.position.copy(pos);
    group.add(mesh);

    // glow halo
    const haloGeo = new THREE.SphereGeometry(isAccent?0.42:0.3, 12, 12);
    const haloMat = new THREE.MeshBasicMaterial({ color, transparent:true, opacity:0.12 });
    const halo = new THREE.Mesh(haloGeo, haloMat);
    halo.position.copy(pos);
    group.add(halo);

    nodes.push({ pos, mesh, halo, basePos: pos.clone(), phase: Math.random()*Math.PI*2 });
  }

  // connections: connect each node to its 2 nearest neighbours
  const edges = [];
  for(let i=0;i<nodeCount;i++){
    const dists = [];
    for(let j=0;j<nodeCount;j++){
      if(i===j) continue;
      dists.push({ j, d: nodes[i].basePos.distanceTo(nodes[j].basePos) });
    }
    dists.sort((a,b)=>a.d-b.d);
    for(let k=0;k<2;k++){
      const j = dists[k].j;
      const key = [i,j].sort().join('-');
      if(!edges.find(e=>e.key===key)) edges.push({ key, a:i, b:j });
    }
  }

  const lineMat = new THREE.LineBasicMaterial({ color: 0x2a3550, transparent:true, opacity:0.5 });
  edges.forEach(edge=>{
    const geo = new THREE.BufferGeometry().setFromPoints([nodes[edge.a].basePos, nodes[edge.b].basePos]);
    const line = new THREE.Line(geo, lineMat);
    group.add(line);
  });

  // traveling data-flow particles along edges
  const particles = edges.map((edge, idx)=>{
    const geo = new THREE.SphereGeometry(0.06, 8, 8);
    const mat = new THREE.MeshBasicMaterial({ color: idx % 2 === 0 ? cyan : violet, transparent:true, opacity:0.95 });
    const mesh = new THREE.Mesh(geo, mat);
    group.add(mesh);
    return { mesh, edge, t: Math.random(), speed: 0.15 + Math.random()*0.15 };
  });

  let mouseX = 0, mouseY = 0;
  window.addEventListener('mousemove', (e)=>{
    mouseX = (e.clientX / window.innerWidth) - 0.5;
    mouseY = (e.clientY / window.innerHeight) - 0.5;
  });

  const clock = new THREE.Clock();
  function animate(){
    requestAnimationFrame(animate);
    const t = clock.getElapsedTime();

    // gentle bob per node
    nodes.forEach(n=>{
      const bob = Math.sin(t*0.8 + n.phase) * 0.12;
      n.mesh.position.copy(n.basePos).addScaledVector(n.basePos.clone().normalize(), bob*0);
      n.mesh.position.y = n.basePos.y + bob;
      n.halo.position.copy(n.mesh.position);
    });

    // move particles along edges
    particles.forEach(p=>{
      p.t += p.speed * 0.01;
      if(p.t > 1) p.t = 0;
      const a = nodes[p.edge.a].mesh.position;
      const b = nodes[p.edge.b].mesh.position;
      p.mesh.position.lerpVectors(a, b, p.t);
    });

    // auto-rotate whole graph + subtle mouse parallax
    group.rotation.y = t * 0.12 + mouseX * 0.4;
    group.rotation.x = mouseY * 0.25;

    renderer.render(scene, camera);
  }
  animate();

  window.addEventListener('resize', ()=>{
    const w = hero.clientWidth, h = hero.clientHeight;
    camera.aspect = w/h;
    camera.updateProjectionMatrix();
    renderer.setSize(w,h);
  });
})();
</script>

</body>
</html>
