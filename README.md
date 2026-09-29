<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>My Portfolio</title>

  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link
    href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&family=Poppins:wght@400;500;600;700;800&display=swap"
    rel="stylesheet"
  />

  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      scroll-behavior: smooth;
    }

    :root {
      --bg: #050816;
      --bg2: #080d20;
      --text: #f5f7ff;
      --muted: #9ba4bd;
      --primary: #7c3aed;
      --secondary: #06b6d4;
      --pink: #ec4899;
      --card: rgba(255, 255, 255, 0.05);
      --border: rgba(255, 255, 255, 0.1);
    }

    body {
      font-family: "Inter", sans-serif;
      background: var(--bg);
      color: var(--text);
      overflow-x: hidden;
      cursor: none;
    }

    a {
      color: inherit;
      text-decoration: none;
    }

    /* CURSOR */
    .cursor {
      position: fixed;
      width: 20px;
      height: 20px;
      border: 2px solid #fff;
      border-radius: 50%;
      pointer-events: none;
      z-index: 99999;
      transform: translate(-50%, -50%);
      transition: width .2s, height .2s, background .2s;
      mix-blend-mode: difference;
    }

    .cursor-dot {
      position: fixed;
      width: 5px;
      height: 5px;
      background: white;
      border-radius: 50%;
      pointer-events: none;
      z-index: 100000;
      transform: translate(-50%, -50%);
    }

    /* BACKGROUND */
    .background {
      position: fixed;
      inset: 0;
      z-index: -3;
      background:
        radial-gradient(circle at 20% 20%, rgba(124,58,237,.18), transparent 30%),
        radial-gradient(circle at 80% 30%, rgba(6,182,212,.14), transparent 30%),
        radial-gradient(circle at 50% 90%, rgba(236,72,153,.12), transparent 35%),
        var(--bg);
    }

    .grid {
      position: fixed;
      inset: 0;
      z-index: -2;
      opacity: .18;
      background-image:
        linear-gradient(rgba(255,255,255,.08) 1px, transparent 1px),
        linear-gradient(90deg, rgba(255,255,255,.08) 1px, transparent 1px);
      background-size: 60px 60px;
      mask-image: linear-gradient(to bottom, black, transparent);
    }

    #particles {
      position: fixed;
      inset: 0;
      z-index: -1;
      pointer-events: none;
    }

    /* NAVBAR */
    nav {
      position: fixed;
      top: 20px;
      left: 50%;
      transform: translateX(-50%);
      width: min(1100px, 92%);
      padding: 14px 22px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      border: 1px solid var(--border);
      background: rgba(5, 8, 22, .65);
      backdrop-filter: blur(18px);
      border-radius: 50px;
      z-index: 1000;
      box-shadow: 0 10px 40px rgba(0,0,0,.25);
    }

    .logo {
      font-family: Poppins;
      font-size: 20px;
      font-weight: 800;
      background: linear-gradient(90deg, #fff, #7c3aed, #06b6d4);
      -webkit-background-clip: text;
      color: transparent;
      background-size: 200%;
      animation: gradient 4s linear infinite;
    }

    nav ul {
      list-style: none;
      display: flex;
      gap: 28px;
    }

    nav li {
      color: #c4c9d8;
      font-size: 14px;
      transition: .3s;
    }

    nav li:hover {
      color: white;
      transform: translateY(-2px);
    }

    .nav-btn {
      padding: 10px 18px;
      border-radius: 30px;
      background: linear-gradient(90deg, var(--primary), var(--secondary));
      font-size: 13px;
      font-weight: 700;
    }

    /* HERO */
    .hero {
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: center;
      padding: 120px 20px 80px;
    }

    .hero-content {
      max-width: 900px;
    }

    .badge {
      display: inline-flex;
      padding: 8px 15px;
      border: 1px solid rgba(124,58,237,.5);
      background: rgba(124,58,237,.1);
      border-radius: 50px;
      color: #c4b5fd;
      font-size: 13px;
      margin-bottom: 25px;
      animation: float 3s ease-in-out infinite;
    }

    .hero h1 {
      font-family: Poppins;
      font-size: clamp(45px, 8vw, 95px);
      line-height: .95;
      font-weight: 800;
      letter-spacing: -5px;
    }

    .gradient-text {
      background: linear-gradient(
        90deg,
        #fff,
        #a78bfa,
        #22d3ee,
        #f472b6,
        #fff
      );
      background-size: 300%;
      -webkit-background-clip: text;
      color: transparent;
      animation: gradient 5s linear infinite;
    }

    .hero p {
      max-width: 650px;
      margin: 30px auto;
      color: var(--muted);
      line-height: 1.8;
      font-size: 17px;
    }

    .typing {
      color: #22d3ee;
      font-weight: 700;
    }

    .hero-buttons {
      display: flex;
      justify-content: center;
      gap: 15px;
      margin-top: 30px;
      flex-wrap: wrap;
    }

    .btn {
      padding: 15px 25px;
      border-radius: 12px;
      font-weight: 700;
      transition: .35s;
      position: relative;
      overflow: hidden;
    }

    .btn-primary {
      background: linear-gradient(90deg, #7c3aed, #06b6d4);
      box-shadow: 0 0 30px rgba(124,58,237,.35);
    }

    .btn-secondary {
      border: 1px solid var(--border);
      background: rgba(255,255,255,.04);
    }

    .btn:hover {
      transform: translateY(-5px) scale(1.03);
      box-shadow: 0 15px 40px rgba(0,0,0,.3);
    }

    /* SECTION */
    section {
      padding: 110px 7%;
      position: relative;
    }

    .section-title {
      text-align: center;
      margin-bottom: 60px;
    }

    .section-title span {
      color: #22d3ee;
      font-size: 13px;
      text-transform: uppercase;
      letter-spacing: 4px;
    }

    .section-title h2 {
      font-family: Poppins;
      font-size: clamp(35px, 5vw, 60px);
      margin-top: 10px;
    }

    /* ABOUT */
    .about {
      max-width: 1100px;
      margin: auto;
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 50px;
      align-items: center;
    }

    .about-image {
      height: 450px;
      border-radius: 30px;
      position: relative;
      background:
        linear-gradient(135deg, rgba(124,58,237,.4), rgba(6,182,212,.1)),
        #10152d;
      border: 1px solid var(--border);
      overflow: hidden;
      transform-style: preserve-3d;
      transition: transform .2s;
    }

    .about-image::before {
      content: "";
      position: absolute;
      width: 250px;
      height: 250px;
      background: #7c3aed;
      filter: blur(100px);
      top: -50px;
      left: -50px;
      opacity: .5;
    }

    .about-image::after {
      content: "CODE";
      position: absolute;
      font-family: Poppins;
      font-size: 100px;
      font-weight: 800;
      color: rgba(255,255,255,.05);
      bottom: 20px;
      right: 20px;
    }

    .about-content h3 {
      font-size: 35px;
      margin-bottom: 20px;
    }

    .about-content p {
      color: var(--muted);
      line-height: 1.9;
      margin-bottom: 20px;
    }

    .stats {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 15px;
      margin-top: 30px;
    }

    .stat {
      padding: 20px;
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 15px;
      text-align: center;
    }

    .stat h3 {
      color: #22d3ee;
      font-size: 28px;
    }

    .stat p {
      font-size: 12px;
      margin: 5px 0 0;
    }

    /* SKILLS */
    .skills-container {
      max-width: 1000px;
      margin: auto;
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 25px;
    }

    .skill {
      padding: 25px;
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 18px;
      transition: .3s;
    }

    .skill:hover {
      transform: translateY(-7px);
      border-color: #7c3aed;
    }

    .skill-head {
      display: flex;
      justify-content: space-between;
      margin-bottom: 12px;
    }

    .bar {
      height: 7px;
      background: rgba(255,255,255,.08);
      border-radius: 20px;
      overflow: hidden;
    }

    .bar span {
      display: block;
      height: 100%;
      width: 0;
      border-radius: 20px;
      background: linear-gradient(90deg, #7c3aed, #06b6d4);
      transition: width 1.5s cubic-bezier(.22,1,.36,1);
    }

    /* PROJECTS */
    .projects {
      max-width: 1200px;
      margin: auto;
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 25px;
    }

    .project {
      position: relative;
      min-height: 330px;
      padding: 30px;
      border-radius: 25px;
      border: 1px solid var(--border);
      background: linear-gradient(
        145deg,
        rgba(255,255,255,.08),
        rgba(255,255,255,.02)
      );
      overflow: hidden;
      transition: .5s;
    }

    .project::before {
      content: "";
      position: absolute;
      width: 180px;
      height: 180px;
      background: var(--primary);
      filter: blur(80px);
      opacity: .15;
      right: -50px;
      top: -50px;
    }

    .project:hover {
      transform: translateY(-15px) rotateX(3deg) rotateY(-3deg);
      border-color: rgba(124,58,237,.7);
      box-shadow: 0 30px 70px rgba(0,0,0,.3);
    }

    .project-number {
      color: #22d3ee;
      font-weight: 800;
      font-size: 14px;
    }

    .project h3 {
      font-size: 27px;
      margin: 40px 0 15px;
    }

    .project p {
      color: var(--muted);
      line-height: 1.7;
      font-size: 14px;
    }

    .tags {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin-top: 25px;
    }

    .tag {
      font-size: 11px;
      padding: 7px 10px;
      border-radius: 20px;
      background: rgba(124,58,237,.12);
      border: 1px solid rgba(124,58,237,.25);
      color: #c4b5fd;
    }

    /* CONTACT */
    .contact-box {
      max-width: 900px;
      margin: auto;
      padding: 60px;
      text-align: center;
      border: 1px solid var(--border);
      border-radius: 30px;
      background:
        radial-gradient(circle at 50% 0%, rgba(124,58,237,.18), transparent 45%),
        rgba(255,255,255,.03);
    }

    .contact-box h2 {
      font-family: Poppins;
      font-size: clamp(35px, 6vw, 65px);
      margin-bottom: 20px;
    }

    .contact-box p {
      color: var(--muted);
      margin-bottom: 30px;
    }

    .socials {
      display: flex;
      justify-content: center;
      gap: 15px;
      margin-top: 25px;
      flex-wrap: wrap;
    }

    .social {
      padding: 12px 20px;
      border: 1px solid var(--border);
      border-radius: 30px;
      transition: .3s;
    }

    .social:hover {
      background: white;
      color: #050816;
      transform: translateY(-4px);
    }

    footer {
      padding: 40px;
      text-align: center;
      color: #687089;
      border-top: 1px solid var(--border);
    }

    /* REVEAL */
    .reveal {
      opacity: 0;
      transform: translateY(60px);
      transition: 1s cubic-bezier(.16,1,.3,1);
    }

    .reveal.active {
      opacity: 1;
      transform: translateY(0);
    }

    /* ANIMATIONS */
    @keyframes float {
      0%,100% { transform: translateY(0); }
      50% { transform: translateY(-10px); }
    }

    @keyframes gradient {
      0% { background-position: 0%; }
      100% { background-position: 300%; }
    }

    /* MOBILE */
    @media(max-width: 800px) {
      body {
        cursor: auto;
      }

      .cursor,
      .cursor-dot {
        display: none;
      }

      nav {
        width: 95%;
      }

      nav ul {
        display: none;
      }

      .about,
      .skills-container {
        grid-template-columns: 1fr;
      }

      .projects {
        grid-template-columns: 1fr;
      }

      .about-image {
        height: 350px;
      }

      section {
        padding: 80px 6%;
      }

      .contact-box {
        padding: 40px 20px;
      }
    }
  </style>
</head>

<body>

  <div class="background"></div>
  <div class="grid"></div>
  <canvas id="particles"></canvas>

  <div class="cursor"></div>
  <div class="cursor-dot"></div>

  <!-- NAVBAR -->
  <nav>
    <a href="#home" class="logo">MY.PORTFOLIO</a>

    <ul>
      <li><a href="#home">Home</a></li>
      <li><a href="#about">About</a></li>
      <li><a href="#skills">Skills</a></li>
      <li><a href="#projects">Projects</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>

    <a href="#contact" class="nav-btn">Let's Talk</a>
  </nav>

  <!-- HERO -->
  <section class="hero" id="home">
    <div class="hero-content reveal">

      <div class="badge">
        ✦ Available for new opportunities
      </div>

      <h1>
        I Build
        <br>
        <span class="gradient-text">Digital Experiences.</span>
      </h1>

      <p>
        Hello, I'm <strong>Your Name</strong>.
        I'm a <span class="typing" id="typing"></span>
        creating beautiful, fast and interactive digital experiences.
      </p>

      <div class="hero-buttons">
        <a href="#projects" class="btn btn-primary">
          View My Work →
        </a>

        <a href="#contact" class="btn btn-secondary">
          Contact Me
        </a>
      </div>

    </div>
  </section>

  <!-- ABOUT -->
  <section id="about">
    <div class="section-title reveal">
      <span>01 — About Me</span>
      <h2>Who I Am</h2>
    </div>

    <div class="about">

      <div class="about-image reveal"></div>

      <div class="about-content reveal">

        <h3>Turning ideas into reality.</h3>

        <p>
          I'm a passionate developer who loves creating modern,
          interactive and visually impressive websites and applications.
        </p>

        <p>
          I enjoy solving problems, learning new technologies and
          building experiences that people actually enjoy using.
        </p>

        <div class="stats">
          <div class="stat">
            <h3>20+</h3>
            <p>Projects</p>
          </div>

          <div class="stat">
            <h3>2+</h3>
            <p>Years Experience</p>
          </div>

          <div class="stat">
            <h3>15+</h3>
            <p>Technologies</p>
          </div>
        </div>

      </div>
    </div>
  </section>

  <!-- SKILLS -->
  <section id="skills">
    <div class="section-title reveal">
      <span>02 — Skills</span>
      <h2>What I Do</h2>
    </div>

    <div class="skills-container">

      <div class="skill reveal">
        <div class="skill-head">
          <span>HTML / CSS</span>
          <span>95%</span>
        </div>
        <div class="bar">
          <span data-width="95%"></span>
        </div>
      </div>

      <div class="skill reveal">
        <div class="skill-head">
          <span>JavaScript</span>
          <span>90%</span>
        </div>
        <div class="bar">
          <span data-width="90%"></span>
        </div>
      </div>

      <div class="skill reveal">
        <div class="skill-head">
          <span>React</span>
          <span>85%</span>
        </div>
        <div class="bar">
          <span data-width="85%"></span>
        </div>
      </div>

      <div class="skill reveal">
        <div class="skill-head">
          <span>Node.js</span>
          <span>80%</span>
        </div>
        <div class="bar">
          <span data-width="80%"></span>
        </div>
      </div>

      <div class="skill reveal">
        <div class="skill-head">
          <span>UI / UX</span>
          <span>88%</span>
        </div>
        <div class="bar">
          <span data-width="88%"></span>
        </div>
      </div>

      <div class="skill reveal">
        <div class="skill-head">
          <span>Git / GitHub</span>
          <span>85%</span>
        </div>
        <div class="bar">
          <span data-width="85%"></span>
        </div>
      </div>

    </div>
  </section>

  <!-- PROJECTS -->
  <section id="projects">

    <div class="section-title reveal">
      <span>03 — Projects</span>
      <h2>Featured Work</h2>
    </div>

    <div class="projects">

      <div class="project reveal">
        <div class="project-number">01 / PROJECT</div>
        <h3>AI Dashboard</h3>
        <p>
          A futuristic AI dashboard with analytics,
          interactive charts and beautiful animations.
        </p>

        <div class="tags">
          <span class="tag">React</span>
          <span class="tag">Node.js</span>
          <span class="tag">API</span>
        </div>
      </div>

      <div class="project reveal">
        <div class="project-number">02 / PROJECT</div>
        <h3>E-Commerce</h3>
        <p>
          Modern e-commerce experience with product
          browsing, cart functionality and responsive UI.
        </p>

        <div class="tags">
          <span class="tag">JavaScript</span>
          <span class="tag">CSS</span>
          <span class="tag">Firebase</span>
        </div>
      </div>

      <div class="project reveal">
        <div class="project-number">03 / PROJECT</div>
        <h3>Portfolio</h3>
        <p>
          Highly animated personal portfolio designed
          to showcase creative development work.
        </p>

        <div class="tags">
          <span class="tag">HTML</span>
          <span class="tag">CSS</span>
          <span class="tag">JavaScript</span>
        </div>
      </div>

    </div>
  </section>

  <!-- CONTACT -->
  <section id="contact">

    <div class="contact-box reveal">

      <h2>Let's create something amazing.</h2>

      <p>
        Have an idea, project or opportunity?
        Let's build something awesome together.
      </p>

      <a href="mailto:your@email.com" class="btn btn-primary">
        Get In Touch →
      </a>

      <div class="socials">
        <a href="#" class="social">GitHub</a>
        <a href="#" class="social">LinkedIn</a>
        <a href="#" class="social">Instagram</a>
      </div>

    </div>

  </section>

  <footer>
    © 2026 Your Name. Built with passion & code.
  </footer>


  <script>

    /* =========================
       TYPING ANIMATION
    ========================= */

    const words = [
      "Full Stack Developer",
      "Web Developer",
      "UI/UX Enthusiast",
      "Creative Coder"
    ];

    const typing = document.getElementById("typing");

    let wordIndex = 0;
    let charIndex = 0;
    let deleting = false;

    function typeEffect() {

      const currentWord = words[wordIndex];

      if (!deleting) {
        typing.textContent =
          currentWord.substring(0, charIndex + 1);

        charIndex++;

        if (charIndex === currentWord.length) {
          deleting = true;
          setTimeout(typeEffect, 1300);
          return;
        }

      } else {

        typing.textContent =
          currentWord.substring(0, charIndex - 1);

        charIndex--;

        if (charIndex === 0) {
          deleting = false;
          wordIndex = (wordIndex + 1) % words.length;
        }
      }

      setTimeout(typeEffect, deleting ? 45 : 90);
    }

    typeEffect();


    /* =========================
       SCROLL REVEAL
    ========================= */

    const reveals = document.querySelectorAll(".reveal");

    const observer = new IntersectionObserver(
      entries => {

        entries.forEach(entry => {

          if (entry.isIntersecting) {

            entry.target.classList.add("active");

            const bars =
              entry.target.querySelectorAll(".bar span");

            bars.forEach(bar => {
              bar.style.width = bar.dataset.width;
            });

          }

        });

      },
      {
        threshold: 0.15
      }
    );

    reveals.forEach(el => observer.observe(el));


    /* =========================
       CUSTOM CURSOR
    ========================= */

    const cursor = document.querySelector(".cursor");
    const dot = document.querySelector(".cursor-dot");

    document.addEventListener("mousemove", e => {

      cursor.style.left = e.clientX + "px";
      cursor.style.top = e.clientY + "px";

      dot.style.left = e.clientX + "px";
      dot.style.top = e.clientY + "px";

    });

    document.querySelectorAll("a, button").forEach(el => {

      el.addEventListener("mouseenter", () => {
        cursor.style.width = "45px";
        cursor.style.height = "45px";
        cursor.style.background = "rgba(255,255,255,.2)";
      });

      el.addEventListener("mouseleave", () => {
        cursor.style.width = "20px";
        cursor.style.height = "20px";
        cursor.style.background = "transparent";
      });

    });


    /* =========================
       3D ABOUT CARD
    ========================= */

    const aboutImage = document.querySelector(".about-image");

    aboutImage.addEventListener("mousemove", e => {

      const rect = aboutImage.getBoundingClientRect();

      const x = e.clientX - rect.left;
      const y = e.clientY - rect.top;

      const rotateX =
        ((y / rect.height) - .5) * -12;

      const rotateY =
        ((x / rect.width) - .5) * 12;

      aboutImage.style.transform =
        `perspective(800px)
         rotateX(${rotateX}deg)
         rotateY(${rotateY}deg)
         scale(1.02)`;

    });

    aboutImage.addEventListener("mouseleave", () => {
      aboutImage.style.transform =
        "perspective(800px) rotateX(0) rotateY(0)";
    });


    /* =========================
       PROJECT TILT
    ========================= */

    document.querySelectorAll(".project").forEach(card => {

      card.addEventListener("mousemove", e => {

        const rect = card.getBoundingClientRect();

        const x = e.clientX - rect.left;
        const y = e.clientY - rect.top;

        const rotateY =
          ((x / rect.width) - .5) * 8;

        const rotateX =
          ((y / rect.height) - .5) * -8;

        card.style.transform =
          `perspective(900px)
           rotateX(${rotateX}deg)
           rotateY(${rotateY}deg)
           translateY(-10px)`;

      });

      card.addEventListener("mouseleave", () => {
        card.style.transform = "";
      });

    });


    /* =========================
       PARTICLES
    ========================= */

    const canvas = document.getElementById("particles");
    const ctx = canvas.getContext("2d");

    let particles = [];

    function resizeCanvas() {

      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;

    }

    resizeCanvas();

    window.addEventListener("resize", resizeCanvas);

    for (let i = 0; i < 100; i++) {

      particles.push({
        x: Math.random() * window.innerWidth,
        y: Math.random() * window.innerHeight,
        size: Math.random() * 2 + .5,
        speedX: (Math.random() - .5) * .5,
        speedY: (Math.random() - .5) * .5
      });

    }

    function animateParticles() {

      ctx.clearRect(
        0,
        0,
        canvas.width,
        canvas.height
      );

      particles.forEach(p => {

        p.x += p.speedX;
        p.y += p.speedY;

        if (p.x < 0 || p.x > canvas.width)
          p.speedX *= -1;

        if (p.y < 0 || p.y > canvas.height)
          p.speedY *= -1;

        ctx.beginPath();

        ctx.arc(
          p.x,
          p.y,
          p.size,
          0,
          Math.PI * 2
        );

        ctx.fillStyle =
          "rgba(124, 58, 237, .7)";

        ctx.fill();

      });

      /* Connect nearby particles */

      for (let i = 0; i < particles.length; i++) {

        for (let j = i + 1; j < particles.length; j++) {

          const dx =
            particles[i].x - particles[j].x;

          const dy =
            particles[i].y - particles[j].y;

          const distance =
            Math.sqrt(dx * dx + dy * dy);

          if (distance < 120) {

            ctx.beginPath();

            ctx.moveTo(
              particles[i].x,
              particles[i].y
            );

            ctx.lineTo(
              particles[j].x,
              particles[j].y
            );

            ctx.strokeStyle =
              `rgba(124,58,237,
              ${.12 * (1 - distance / 120)})`;

            ctx.stroke();

          }

        }

      }

      requestAnimationFrame(animateParticles);
    }

    animateParticles();

  </script>

</body>
</html>
