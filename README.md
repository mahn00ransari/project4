
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="IRON HOUSE — a modern gym website demo project.">
  <title>IRON HOUSE | Train With Purpose</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link href="https://fonts.googleapis.com/css2?family=Barlow+Condensed:wght@500;600;700;800&family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.2/css/all.min.css">
  <style>
    :root {
      --bg: #101110;
      --panel: #191b19;
      --panel-2: #222522;
      --lime: #c8ff39;
      --white: #f6f7f2;
      --muted: #a4aaa0;
      --line: rgba(255,255,255,.12);
      --max: 1160px;
    }
    * { box-sizing: border-box; margin: 0; padding: 0; }
    html { scroll-behavior: smooth; scroll-padding-top: 82px; }
    body { font-family: Inter, sans-serif; background: var(--bg); color: var(--white); line-height: 1.65; }
    a { color: inherit; }
    .wrap { width: min(var(--max), calc(100% - 44px)); margin-inline: auto; }
    .topbar { position: sticky; top: 0; z-index: 50; background: rgba(16,17,16,.95); backdrop-filter: blur(12px); border-bottom: 1px solid var(--line); }
    .nav { min-height: 76px; display: flex; align-items: center; justify-content: space-between; gap: 24px; }
    .brand { text-decoration: none; font: 800 1.65rem "Barlow Condensed", sans-serif; letter-spacing: 1.4px; }
    .brand span { color: var(--lime); }
    .nav-links { display: flex; align-items: center; gap: 30px; list-style: none; }
    .nav-links a { text-decoration: none; color: #e5e7e1; font-size: .9rem; font-weight: 600; }
    .nav-links a:hover { color: var(--lime); }
    .menu-toggle { display: none; color: var(--white); background: transparent; border: 0; font-size: 1.5rem; cursor: pointer; }
    .button { display: inline-flex; align-items: center; justify-content: center; gap: 10px; padding: 13px 22px; border: 1px solid var(--lime); background: var(--lime); color: #151711; font-weight: 800; text-decoration: none; text-transform: uppercase; letter-spacing: .6px; font-size: .78rem; transition: transform .2s, background .2s; cursor: pointer; }
    .button:hover { transform: translateY(-2px); background: #d8ff72; }
    .button.outline { background: transparent; color: var(--white); border-color: var(--line); }
    .button.outline:hover { border-color: var(--lime); color: var(--lime); }
    .hero { min-height: 650px; display: grid; align-items: center; position: relative; overflow: hidden; background: linear-gradient(90deg, rgba(13,15,13,.96) 0%, rgba(13,15,13,.84) 48%, rgba(13,15,13,.2) 100%), url("https://images.unsplash.com/photo-1534438327276-14e5300c3a48?auto=format&fit=crop&w=1800&q=85") center/cover; }
    .hero-content { max-width: 720px; padding: 92px 0; position: relative; }
    .eyebrow { display: inline-flex; gap: 10px; align-items: center; color: var(--lime); text-transform: uppercase; letter-spacing: 2px; font-size: .73rem; font-weight: 800; margin-bottom: 18px; }
    .eyebrow::before { content: ""; width: 28px; height: 2px; background: var(--lime); }
    h1, h2, h3 { font-family: "Barlow Condensed", sans-serif; text-transform: uppercase; line-height: .98; }
    h1 { font-size: clamp(3.6rem, 8vw, 7.1rem); letter-spacing: -1px; max-width: 740px; }
    h1 em { color: var(--lime); font-style: normal; }
    .hero p { max-width: 540px; color: #c4c8c0; margin: 24px 0 30px; }
    .hero-actions { display: flex; flex-wrap: wrap; gap: 12px; }
    .hero-stats { display: flex; flex-wrap: wrap; gap: 34px; margin-top: 54px; }
    .stat strong { display: block; font: 700 2rem "Barlow Condensed", sans-serif; color: var(--lime); }
    .stat span { color: #c1c6bd; text-transform: uppercase; font-size: .68rem; letter-spacing: 1px; }
    section { padding: 88px 0; }
    .section-head { display: flex; align-items: end; justify-content: space-between; gap: 22px; margin-bottom: 34px; }
    .section-head h2 { font-size: clamp(2.8rem, 5vw, 4.2rem); }
    .section-head h2 span { color: var(--lime); }
    .section-head p { max-width: 440px; color: var(--muted); font-size: .92rem; }
    .programs { background: #151715; }
    .cards { display: grid; grid-template-columns: repeat(3, 1fr); gap: 18px; }
    .program-card { background: var(--panel); border: 1px solid var(--line); overflow: hidden; transition: transform .22s, border-color .22s; }
    .program-card:hover { transform: translateY(-5px); border-color: rgba(200,255,57,.6); }
    .program-card img { width: 100%; height: 220px; object-fit: cover; display: block; filter: saturate(.78); }
    .card-body { padding: 24px; }
    .card-body .tag { color: var(--lime); font-size: .68rem; font-weight: 800; letter-spacing: 1.3px; text-transform: uppercase; }
    .card-body h3 { font-size: 2rem; margin: 10px 0; }
    .card-body p { color: var(--muted); font-size: .88rem; min-height: 72px; }
    .text-link { display: inline-flex; align-items: center; gap: 9px; color: var(--lime); text-decoration: none; text-transform: uppercase; font-size: .73rem; font-weight: 800; margin-top: 20px; }
    .about-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 58px; align-items: center; }
    .about-photo { position: relative; }
    .about-photo img { display: block; width: 100%; min-height: 380px; object-fit: cover; }
    .photo-note { position: absolute; right: -14px; bottom: 22px; background: var(--lime); color: #171a13; padding: 17px 22px; font: 700 1.3rem "Barlow Condensed", sans-serif; text-transform: uppercase; }
    .about-copy h2 { font-size: clamp(2.8rem, 5vw, 4.4rem); margin-bottom: 22px; }
    .about-copy h2 span { color: var(--lime); }
    .about-copy p { color: var(--muted); margin-bottom: 22px; }
    .benefits { list-style: none; display: grid; gap: 13px; margin: 24px 0 28px; }
    .benefits li { display: flex; gap: 12px; align-items: center; font-size: .92rem; }
    .benefits i { color: var(--lime); }
    .plans { background: var(--panel); }
    .plan-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 18px; align-items: stretch; }
    .plan { padding: 30px; background: #111310; border: 1px solid var(--line); }
    .plan.featured { border: 1px solid var(--lime); box-shadow: inset 0 3px var(--lime); }
    .plan-label { color: var(--lime); font-size: .68rem; text-transform: uppercase; letter-spacing: 1.5px; font-weight: 800; }
    .plan h3 { font-size: 2.1rem; margin: 12px 0; }
    .price { font: 700 3rem "Barlow Condensed", sans-serif; margin-bottom: 5px; }
    .price small { font: 500 .78rem Inter,sans-serif; color: var(--muted); }
    .plan > p { color: var(--muted); font-size: .86rem; min-height: 48px; }
    .plan ul { list-style: none; margin: 22px 0 26px; display: grid; gap: 11px; color: #d9ddd5; font-size: .84rem; }
    .plan li i { color: var(--lime); margin-right: 9px; }
    .plan .button { width: 100%; }
    .contact-grid { display: grid; grid-template-columns: .85fr 1.15fr; gap: 46px; }
    .contact-copy h2 { font-size: clamp(2.8rem, 5vw, 4rem); margin-bottom: 18px; }
    .contact-copy h2 span { color: var(--lime); }
    .contact-copy p { color: var(--muted); margin-bottom: 22px; }
    .contact-detail { display: flex; gap: 13px; align-items: flex-start; margin: 17px 0; color: #dce0d8; font-size: .9rem; }
    .contact-detail i { color: var(--lime); margin-top: 5px; width: 18px; }
    .contact-form { background: var(--panel); border: 1px solid var(--line); padding: 30px; }
    .field-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 15px; }
    .field { display: flex; flex-direction: column; gap: 7px; margin-bottom: 15px; }
    .field.full { grid-column: 1/-1; }
    .field label { color: #dfe2dc; font-size: .78rem; font-weight: 700; }
    .field input, .field select, .field textarea { width: 100%; padding: 12px 13px; background: #101210; color: var(--white); border: 1px solid #383d37; border-radius: 0; font: inherit; font-size: .88rem; }
    .field input:focus, .field select:focus, .field textarea:focus { outline: 2px solid var(--lime); outline-offset: 1px; }
    .form-message { display: none; margin-top: 15px; padding: 12px; color: #10140a; background: var(--lime); font-size: .84rem; font-weight: 700; }
    footer { border-top: 1px solid var(--line); padding: 26px 0; color: var(--muted); font-size: .8rem; }
    .footer-row { display: flex; justify-content: space-between; gap: 16px; flex-wrap: wrap; }
    .footer-brand { color: var(--white); font: 800 1.3rem "Barlow Condensed", sans-serif; letter-spacing: 1px; }
    .footer-brand span { color: var(--lime); }
    @media (max-width: 820px) {
      .menu-toggle { display: block; }
      .nav-links { display: none; position: absolute; top: 75px; left: 0; width: 100%; padding: 24px; background: #171917; border-bottom: 1px solid var(--line); flex-direction: column; align-items: flex-start; }
      .nav-links.active { display: flex; }
      .hero { min-height: auto; background-position: 60% center; }
      .cards, .plan-grid { grid-template-columns: 1fr 1fr; }
      .about-grid, .contact-grid { grid-template-columns: 1fr; }
      .about-grid { gap: 36px; }
      .photo-note { right: 10px; }
      .section-head { align-items: flex-start; flex-direction: column; }
    }
    @media (max-width: 560px) {
      .wrap { width: min(100% - 30px, var(--max)); }
      section { padding: 65px 0; }
      .nav { min-height: 68px; }
      .nav-links { top: 67px; }
      .hero-content { padding: 75px 0; }
      .hero-stats { gap: 22px; }
      .cards, .plan-grid, .field-grid { grid-template-columns: 1fr; }
      .field.full { grid-column: auto; }
      .contact-form { padding: 20px; }
      .about-photo img { min-height: 270px; }
      .stat strong { font-size: 1.7rem; }
    }
  </style>
</head>
<body>
  <header class="topbar">
    <nav class="nav wrap" aria-label="Main navigation">
      <a class="brand" href="#home">IRON <span>HOUSE</span></a>
      <button class="menu-toggle" type="button" aria-label="Toggle navigation" aria-expanded="false"><i class="fa-solid fa-bars"></i></button>
      <ul class="nav-links">
        <li><a href="#home">Home</a></li>
        <li><a href="#programs">Programs</a></li>
        <li><a href="#about">Our Story</a></li>
        <li><a href="#plans">Membership</a></li>
        <li><a class="button" href="#contact">Join Us <i class="fa-solid fa-arrow-right"></i></a></li>
      </ul>
    </nav>
  </header>

  <main>
    <section class="hero" id="home">
      <div class="wrap">
        <div class="hero-content">
          <div class="eyebrow">Your work. Your strength.</div>
          <h1>BUILD YOUR<br><em>STRONGER</em><br>SELF.</h1>
          <p>A welcoming training space for every level. Move with purpose, build steady habits, and celebrate progress on your own terms.</p>
          <div class="hero-actions">
            <a class="button" href="#plans">Explore Membership <i class="fa-solid fa-arrow-right"></i></a>
            <a class="button outline" href="#programs">Explore Programs</a>
          </div>
          <div class="hero-stats">
            <div class="stat"><strong>24/7*</strong><span>Flexible access</span></div>
            <div class="stat"><strong>12+</strong><span>Training formats</span></div>
            <div class="stat"><strong>ALL</strong><span>Experience levels</span></div>
          </div>
          <p style="font-size:.72rem;color:#969d91;margin-top:12px">*Demo website detail; actual hours and services may vary.</p>
        </div>
      </div>
    </section>

    <section class="programs" id="programs">
      <div class="wrap">
        <div class="section-head">
          <div><div class="eyebrow">Find your rhythm</div><h2>TRAINING <span>PROGRAMS</span></h2></div>
          <p>Choose a style that fits your goals, schedule, and comfort level. Start where you are and build consistency.</p>
        </div>
        <div class="cards">
          <article class="program-card">
            <img src="https://images.unsplash.com/photo-1583454110551-21f2fa2afe61?auto=format&fit=crop&w=900&q=80" alt="Strength training equipment">
            <div class="card-body"><div class="tag">01 / Strength</div><h3>Strength Lab</h3><p>Learn foundational movement patterns with a thoughtful, progressive training approach.</p><a class="text-link" href="#contact">Ask about sessions <i class="fa-solid fa-arrow-right"></i></a></div>
          </article>
          <article class="program-card">
            <img src="https://images.unsplash.com/photo-1534258936925-c58bed479fcb?auto=format&fit=crop&w=900&q=80" alt="Fitness class training">
            <div class="card-body"><div class="tag">02 / Group</div><h3>Team Circuit</h3><p>Coach-guided circuits that mix movement, teamwork, and options for different abilities.</p><a class="text-link" href="#contact">Ask about sessions <i class="fa-solid fa-arrow-right"></i></a></div>
          </article>
          <article class="program-card">
            <img src="https://images.unsplash.com/photo-1518611012118-696072aa579a?auto=format&fit=crop&w=900&q=80" alt="Stretching and mobility practice">
            <div class="card-body"><div class="tag">03 / Mobility</div><h3>Move Better</h3><p>Mobility and recovery sessions focused on comfortable range of motion and body awareness.</p><a class="text-link" href="#contact">Ask about sessions <i class="fa-solid fa-arrow-right"></i></a></div>
          </article>
        </div>
      </div>
    </section>

    <section id="about">
      <div class="wrap about-grid">
        <div class="about-photo">
          <img src="https://images.unsplash.com/photo-1534438327276-14e5300c3a48?auto=format&fit=crop&w=1000&q=80" alt="Modern gym training floor">
          <div class="photo-note">Show up. Start small.</div>
        </div>
        <div class="about-copy">
          <div class="eyebrow">The Iron House mindset</div>
          <h2>MORE THAN<br>A <span>WORKOUT.</span></h2>
          <p>IRON HOUSE is a fictional gym brand concept built around a simple idea: fitness should feel supportive, practical, and sustainable—not intimidating.</p>
          <ul class="benefits">
            <li><i class="fa-solid fa-circle-check"></i> Friendly, beginner-conscious environment</li>
            <li><i class="fa-solid fa-circle-check"></i> Clear coaching and movement options</li>
            <li><i class="fa-solid fa-circle-check"></i> Strength, conditioning, and mobility</li>
            <li><i class="fa-solid fa-circle-check"></i> Progress measured beyond appearance</li>
          </ul>
          <a href="#contact" class="button">Meet Your Next Goal <i class="fa-solid fa-arrow-right"></i></a>
        </div>
      </div>
    </section>

    <section class="plans" id="plans">
      <div class="wrap">
        <div class="section-head">
          <div><div class="eyebrow">Simple membership concepts</div><h2>CHOOSE YOUR <span>PLAN</span></h2></div>
          <p>Sample prices below are placeholders for this portfolio project, not real offers.</p>
        </div>
        <div class="plan-grid">
          <article class="plan">
            <div class="plan-label">Flexible</div><h3>Starter</h3><div class="price">$19 <small>/ month*</small></div><p>For exploring the gym and building a routine.</p>
            <ul><li><i class="fa-solid fa-check"></i> Gym floor access</li><li><i class="fa-solid fa-check"></i> Intro orientation</li><li><i class="fa-solid fa-check"></i> Basic progress guide</li></ul>
            <a class="button outline" href="#contact" data-plan="Starter">Select Starter</a>
          </article>
          <article class="plan featured">
            <div class="plan-label">Popular concept</div><h3>Momentum</h3><div class="price">$39 <small>/ month*</small></div><p>A balanced option for steady training.</p>
            <ul><li><i class="fa-solid fa-check"></i> Everything in Starter</li><li><i class="fa-solid fa-check"></i> Group class access</li><li><i class="fa-solid fa-check"></i> Monthly check-in</li></ul>
            <a class="button" href="#contact" data-plan="Momentum">Select Momentum</a>
          </article>
          <article class="plan">
            <div class="plan-label">Coach support</div><h3>Focused</h3><div class="price">$69 <small>/ month*</small></div><p>Extra structure with coaching touchpoints.</p>
            <ul><li><i class="fa-solid fa-check"></i> Everything in Momentum</li><li><i class="fa-solid fa-check"></i> Coaching consultation</li><li><i class="fa-solid fa-check"></i> Personal plan review</li></ul>
            <a class="button outline" href="#contact" data-plan="Focused">Select Focused</a>
          </article>
        </div>
        <p style="color:var(--muted);font-size:.72rem;margin-top:14px">*Fictional demonstration pricing. No purchase or membership is offered.</p>
      </div>
    </section>

    <section id="contact">
      <div class="wrap contact-grid">
        <div class="contact-copy">
          <div class="eyebrow">Start a conversation</div>
          <h2>LET'S GET<br><span>YOU MOVING.</span></h2>
          <p>Curious about the programs or membership concepts? Send a demo inquiry using the form. This static sample does not transmit your information.</p>
          <div class="contact-detail"><i class="fa-solid fa-location-dot"></i><div><strong>Visit us</strong><br>123 Training Avenue, Your City (sample address)</div></div>
          <div class="contact-detail"><i class="fa-solid fa-clock"></i><div><strong>Hours</strong><br>Sample hours: Mon–Sat, 6 AM–10 PM</div></div>
          <div class="contact-detail"><i class="fa-solid fa-envelope"></i><div><strong>Email</strong><br>hello@example.com (sample)</div></div>
        </div>
        <form class="contact-form" id="inquiryForm">
          <div class="field-grid">
            <div class="field"><label for="name">Your name</label><input id="name" name="name" autocomplete="name" required placeholder="Name"></div>
            <div class="field"><label for="email">Email address</label><input id="email" name="email" type="email" autocomplete="email" required placeholder="you@example.com"></div>
            <div class="field full"><label for="interest">I'm interested in</label><select id="interest" name="interest" required><option value="">Choose an option</option><option>Starter membership</option><option>Momentum membership</option><option>Focused membership</option><option>Training programs</option><option>General question</option></select></div>
            <div class="field full"><label for="message">Message (optional)</label><textarea id="message" name="message" rows="4" placeholder="What would you like to know?"></textarea></div>
          </div>
          <button class="button" type="submit">Send Demo Inquiry <i class="fa-solid fa-arrow-right"></i></button>
          <p class="form-message" id="formMessage" role="status">Demo submitted! No information was sent or stored.</p>
        </form>
      </div>
    </section>
  </main>

  <footer><div class="wrap footer-row"><div class="footer-brand">IRON <span>HOUSE</span></div><p>© <span id="year"></span> IRON HOUSE — fictional portfolio project.</p><p>Built with HTML, CSS & JavaScript.</p></div></footer>

  <script>
    // Mobile navigation
    const menuToggle = document.querySelector('.menu-toggle');
    const navLinks = document.querySelector('.nav-links');
    menuToggle.addEventListener('click', () => {
      const opened = navLinks.classList.toggle('active');
      menuToggle.setAttribute('aria-expanded', String(opened));
      menuToggle.innerHTML = opened
        ? '<i class="fa-solid fa-xmark"></i>'
        : '<i class="fa-solid fa-bars"></i>';
    });

    document.querySelectorAll('.nav-links a').forEach(link => {
      link.addEventListener('click', () => {
        navLinks.classList.remove('active');
        menuToggle.setAttribute('aria-expanded', 'false');
        menuToggle.innerHTML = '<i class="fa-solid fa-bars"></i>';
      });
    });

    // Preselect a membership when its CTA is clicked
    document.querySelectorAll('[data-plan]').forEach(button => {
      button.addEventListener('click', () => {
        const selectedPlan = button.dataset.plan;
        const interest = document.getElementById('interest');
        const matchingOption = [...interest.options].find(option => option.text.includes(selectedPlan));
        if (matchingOption) interest.value = matchingPlanValue(matchingOption);
      });
    });
    function matchingPlanValue(option) { return option.value || option.text; }

    // Demo inquiry: browser-only feedback, no backend or email delivery
    const inquiryForm = document.getElementById('inquiryForm');
    const formMessage = document.getElementById('formMessage');
    inquiryForm.addEventListener('submit', event => {
      event.preventDefault();
      formMessage.style.display = 'block';
      inquiryForm.reset();
      window.setTimeout(() => { formMessage.style.display = 'none'; }, 5500);
    });

    document.getElementById('year').textContent = new Date().getFullYear();
  </script>
</body>
</html>
