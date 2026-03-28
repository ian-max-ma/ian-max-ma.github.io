[index.html](https://github.com/user-attachments/files/26322185/index.html)
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Yihao (Ian) Ma 马邑昊</title>

  <!-- Google Fonts: Raleway (headings) + Inter (body) -->
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link href="https://fonts.googleapis.com/css2?family=Raleway:wght@300;400;600;700&family=Inter:wght@300;400;500;600&display=swap" rel="stylesheet" />
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.2/css/all.min.css" />
  <!-- FullCalendar v6 -->
  <link href="https://cdn.jsdelivr.net/npm/fullcalendar@6.1.11/index.global.min.css" rel="stylesheet" />
  <script src="https://cdn.jsdelivr.net/npm/fullcalendar@6.1.11/index.global.min.js"></script>
  <!-- ical.js for ICS parsing -->
  <script src="https://cdn.jsdelivr.net/npm/ical.js@2.0.0/build/ical.min.js"></script>
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --link:   #1772d0;
      --link-h: #0f5ab0;
      --text:   #333;
      --muted:  #888;
      --dark:   #111;
      --border: #e5e5e5;
      --nav-h:  70px;
      --max:    1100px;   /* wider — removes the side gap */
    }

    html { scroll-behavior: smooth; }

    body {
      font-family: 'Inter', 'Helvetica Neue', sans-serif;
      font-size: 19px;        /* noticeably larger base */
      line-height: 1.8;
      color: var(--text);
      background: #fff;
    }

    a { color: var(--link); text-decoration: none; }
    a:hover { color: var(--link-h); text-decoration: underline; }
    strong { font-weight: 600; }

    /* ══════════════════════
       NAVBAR
       ══════════════════════ */
    #navbar {
      position: fixed; top: 0; left: 0; right: 0;
      height: var(--nav-h);
      background: #fff;
      border-bottom: 1px solid var(--border);
      z-index: 1000;
    }
    .nav-inner {
      max-width: var(--max);
      margin: 0 auto;
      height: 100%;
      padding: 0 1.25rem;
      display: flex; align-items: center; justify-content: space-between;
    }
    .nav-brand {
      font-family: 'Raleway', sans-serif;
      font-size: 1.4rem;
      font-weight: 700;
      color: var(--dark);
      letter-spacing: -.01em;
    }
    .nav-brand:hover { color: var(--dark); text-decoration: none; }

    .nav-links { display: flex; list-style: none; }
    .nav-links a {
      display: block;
      padding: .3rem .9rem;
      font-family: 'Inter', sans-serif;
      font-size: .88rem;
      font-weight: 400;
      color: var(--text);
      transition: color .15s;
    }
    .nav-links a:hover,
    .nav-links a.active { color: var(--link); text-decoration: none; }

    .nav-icons { display: flex; gap: .4rem; align-items: center; }
    .nav-icon-btn {
      background: none; border: none; cursor: pointer;
      color: #bbb; font-size: 1rem; padding: .3rem; line-height: 1;
      transition: color .15s;
    }
    .nav-icon-btn:hover { color: var(--link); }

    .nav-toggle { display: none; background: none; border: none; cursor: pointer; padding: .4rem; }
    .nav-toggle span { display: block; width: 22px; height: 2px; background: var(--text); margin: 5px 0; }

    /* ══════════════════════
       PAGE / SECTION
       ══════════════════════ */
    #about { padding: calc(var(--nav-h) + 52px) 0 80px; }

    .container {
      max-width: var(--max);
      margin: 0 auto;
      padding: 0 1.25rem;    /* minimal side padding — content fills width */
    }

    /* Two-column grid */
    .about-grid {
      display: grid;
      grid-template-columns: 290px 1fr;
      gap: 3rem;
      align-items: flex-start;
    }

    /* ─── LEFT ─── */
    .portrait-col { text-align: center; }

    .portrait-photo {
      width: 250px; height: 250px;
      border-radius: 50%;
      object-fit: cover;
      display: block;
      margin: 0 auto 1.3rem;
      border: 3px solid #ddd;
    }
    .portrait-fallback {
      width: 250px; height: 250px;
      border-radius: 50%;
      background: #e0e0e0;
      margin: 0 auto 1.3rem;
      display: flex; align-items: center; justify-content: center;
      font-size: 5.5rem; color: #aaa;
    }

    .portrait-name {
      font-family: 'Raleway', sans-serif;
      font-size: 1.9rem;
      font-weight: 700;
      color: var(--dark);
      line-height: 1.2;
      margin-bottom: .3rem;
    }
    .portrait-role {
      font-size: 1.05rem;
      color: var(--muted);
      margin-bottom: .15rem;
    }
    .portrait-org {
      font-size: 1.05rem;
      margin-bottom: 1.3rem;
    }
    .portrait-org a { color: var(--link); font-weight: 400; }
    .portrait-org a:hover { text-decoration: underline; }

    /* ── Social icons: NO background, plain colored symbols ──
       Matching exactly what's on xinjie-shen.com:
       just large blue icon glyphs, no box/square behind them  */
    .social-row {
      display: flex;
      justify-content: center;
      align-items: center;
      flex-wrap: wrap;
      gap: .75rem;
    }

    /* Each icon: just the symbol, blue, large */
    .sicon {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      color: var(--link);
      font-size: 1.7rem;   /* large, prominent */
      transition: color .15s, transform .15s;
      text-decoration: none;
      line-height: 1;
    }
    .sicon:hover {
      color: var(--link-h);
      transform: translateY(-2px);
      text-decoration: none;
    }

    /* CV is text, same size and color */
    .sicon.cv {
      font-family: 'Raleway', sans-serif;
      font-size: 1.35rem;
      font-weight: 700;
      letter-spacing: .04em;
    }

    /* ─── RIGHT ─── */
    .bio-col {}

    .bio-heading {
      font-family: 'Raleway', sans-serif;
      font-size: 2.8rem;
      font-weight: 300;     /* light weight — exactly like Xinjie's */
      color: var(--dark);
      margin-bottom: 1.25rem;
      letter-spacing: -.02em;
      line-height: 1.15;
    }

    .bio-para {
      font-size: 1rem;
      line-height: 1.85;
      color: var(--text);
      margin-bottom: 1rem;
    }

    /* Interests + Education */
    .bio-two-col {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 1rem 3rem;
      margin-top: 2rem;
    }

    .bio-subcol-title {
      font-family: 'Raleway', sans-serif;
      font-size: 1.2rem;
      font-weight: 700;
      color: var(--dark);
      margin-bottom: 1rem;
    }

    /* Interest list — each item gets a DIFFERENT icon (dark, not blue) */
    .int-list { list-style: none; }
    .int-list li {
      display: flex;
      align-items: flex-start;
      gap: .7rem;
      font-size: .97rem;
      margin-bottom: .55rem;
      color: var(--text);
    }
    .int-list li i {
      color: #555;       /* dark gray icons, like on Xinjie's site */
      margin-top: .28rem;
      font-size: .95rem;
      flex-shrink: 0;
      width: 1.1rem;
      text-align: center;
    }

    /* Education list */
    .edu-list { list-style: none; }
    .edu-list li {
      display: flex;
      align-items: flex-start;
      gap: .7rem;
      margin-bottom: 1rem;
    }
    .edu-list li i {
      color: #555;
      font-size: 1.1rem;
      margin-top: .22rem;
      flex-shrink: 0;
    }
    .edu-degree {
      font-size: .97rem;
      font-weight: 600;
      color: var(--dark);
      line-height: 1.35;
    }
    .edu-school {
      font-size: .87rem;
      color: var(--muted);
      margin-top: .06rem;
    }

    /* ══════════════════════
       FOOTER
       ══════════════════════ */
    /* ══════════════════════
       SCHEDULE SECTION
       ══════════════════════ */
    #schedule { padding: 72px 0 80px; background: #fff; }

    .schedule-heading {
      font-family: 'Raleway', sans-serif;
      font-size: 2.8rem;
      font-weight: 300;
      color: var(--dark);
      margin-bottom: .4rem;
      letter-spacing: -.02em;
    }
    .schedule-subtext {
      font-size: .97rem;
      color: var(--muted);
      margin-bottom: 2.5rem;
    }

    /* Full-width calendar (read-only mode) */
    .schedule-grid {
      display: block;
    }

    /* ── FullCalendar wrapper ── */
    .cal-wrap {
      background: #fff;
      border: 1px solid var(--border);
      border-radius: 8px;
      padding: 1.25rem;
      box-shadow: 0 2px 12px rgba(0,0,0,.05);
    }

    /* FullCalendar style overrides */
    .fc { font-family: 'Inter', sans-serif; font-size: .87rem; }
    .fc .fc-toolbar-title { font-family: 'Raleway', sans-serif; font-size: 1.15rem; font-weight: 700; color: var(--dark); }
    .fc .fc-button { background: var(--link) !important; border-color: var(--link) !important; font-size: .8rem !important; padding: .28rem .65rem !important; border-radius: 4px !important; font-family: 'Inter', sans-serif !important; }
    .fc .fc-button:hover { background: var(--link-h) !important; }
    .fc .fc-button-active { background: var(--link-h) !important; }
    .fc .fc-col-header-cell-cushion { font-weight: 600; color: var(--dark); text-decoration: none; }
    .fc .fc-daygrid-day-number { color: var(--text); text-decoration: none; }
    .fc .fc-event { background: var(--link) !important; border-color: var(--link) !important; font-size: .76rem !important; border-radius: 3px !important; }
    .fc .fc-day-today { background: #eef4ff !important; }
    .fc-theme-standard td, .fc-theme-standard th { border-color: #eee !important; }

    /* ICS status badge */
    .cal-sources {
      display: flex; gap: .6rem; flex-wrap: wrap;
      margin-bottom: 1rem;
    }
    .cal-source-badge {
      display: inline-flex; align-items: center; gap: .4rem;
      padding: .25rem .7rem;
      border-radius: 20px;
      font-size: .78rem; font-weight: 600;
      border: 1.5px solid;
    }
    .cal-source-badge.icloud  { color: #555; border-color: #aaa; background: #f5f5f5; }
    .cal-source-badge.outlook { color: #0078d4; border-color: #0078d4; background: #e8f4ff; }
    .cal-source-badge.loaded  { color: #22863a; border-color: #34d058; background: #e6ffed; }
    .cal-source-badge i { font-size: .8rem; }

    @media (max-width: 900px) {
      .schedule-grid { grid-template-columns: 1fr; }
    }

    /* ══════════════════════
       EXPERIENCE SECTION
       ══════════════════════ */
    #experience { padding: 72px 0 80px; background: #fff; }

    .section-heading {
      font-family: 'Raleway', sans-serif;
      font-size: 2.8rem;
      font-weight: 300;
      color: var(--dark);
      margin-bottom: 2.5rem;
      letter-spacing: -.02em;
    }

    /* Timeline */
    .timeline { position: relative; padding-left: 0; }

    .tl-item {
      display: grid;
      grid-template-columns: 160px 1fr;
      gap: 0 2.2rem;
      margin-bottom: 2.5rem;
      position: relative;
    }
    .tl-item::before {
      /* vertical connector line */
      content: '';
      position: absolute;
      left: 160px;
      top: 12px;
      bottom: -2.5rem;
      width: 2px;
      background: var(--border);
      transform: translateX(-50%);
    }
    .tl-item:last-child::before { display: none; }

    .tl-date {
      text-align: right;
      padding-top: .1rem;
      font-size: .84rem;
      color: var(--muted);
      line-height: 1.5;
      padding-right: 1rem;
    }

    .tl-body {
      padding-left: 1.4rem;
      border-left: 2px solid var(--border);
      position: relative;
    }
    .tl-body::before {
      /* dot on the timeline */
      content: '';
      position: absolute;
      left: -6px; top: 8px;
      width: 10px; height: 10px;
      border-radius: 50%;
      background: var(--link);
      border: 2px solid #fff;
      box-shadow: 0 0 0 2px var(--link);
    }

    .tl-role {
      font-family: 'Raleway', sans-serif;
      font-size: 1.15rem;
      font-weight: 700;
      color: var(--dark);
      margin-bottom: .1rem;
    }
    .tl-company {
      font-size: .95rem;
      color: var(--link);
      font-weight: 500;
      margin-bottom: .5rem;
    }
    .tl-company a { color: var(--link); }
    .tl-company a:hover { color: var(--link-h); }
    .tl-loc {
      font-size: .83rem;
      color: var(--muted);
      margin-bottom: .6rem;
    }
    .tl-desc {
      font-size: .95rem;
      color: var(--text);
      line-height: 1.75;
    }
    .tl-desc ul { padding-left: 1.3rem; margin: 0; }
    .tl-desc li { margin-bottom: .3rem; }
    .tl-tags {
      margin-top: .7rem;
      display: flex; gap: .4rem; flex-wrap: wrap;
    }
    .tl-tag {
      display: inline-block;
      padding: .15rem .65rem;
      border-radius: 20px;
      background: #eef4ff;
      color: var(--link);
      font-size: .75rem;
      font-weight: 600;
    }

    /* ══════════════════════
       PROJECTS SECTION
       ══════════════════════ */
    #projects { padding: 72px 0 80px; background: #f9f9f9; }

    .proj-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
      gap: 1.5rem;
    }

    .proj-card {
      background: #fff;
      border: 1px solid var(--border);
      border-radius: 8px;
      overflow: hidden;
      transition: box-shadow .2s, transform .2s;
      display: flex; flex-direction: column;
    }
    .proj-card:hover {
      box-shadow: 0 6px 24px rgba(0,0,0,.09);
      transform: translateY(-3px);
    }

    .proj-img {
      width: 100%; height: 170px;
      background: linear-gradient(135deg, #1772d0 0%, #0f3f8c 100%);
      display: flex; align-items: center; justify-content: center;
      font-size: 3.5rem; color: rgba(255,255,255,.55);
    }

    .proj-body { padding: 1.2rem 1.3rem 1.4rem; flex: 1; display: flex; flex-direction: column; }

    .proj-title {
      font-family: 'Raleway', sans-serif;
      font-size: 1.1rem;
      font-weight: 700;
      color: var(--dark);
      margin-bottom: .5rem;
      line-height: 1.3;
    }
    .proj-meta {
      font-size: .8rem;
      color: var(--muted);
      margin-bottom: .6rem;
    }
    .proj-desc {
      font-size: .9rem;
      color: var(--text);
      line-height: 1.7;
      flex: 1;
      margin-bottom: .9rem;
    }
    .proj-tags { display: flex; gap: .4rem; flex-wrap: wrap; }
    .proj-tag {
      display: inline-block;
      padding: .12rem .55rem;
      border-radius: 20px;
      background: #eef4ff;
      color: var(--link);
      font-size: .73rem;
      font-weight: 600;
    }
    .proj-links {
      margin-top: .9rem;
      display: flex; gap: .6rem; flex-wrap: wrap;
    }
    .proj-link {
      display: inline-flex; align-items: center; gap: .35rem;
      padding: .3rem .8rem;
      border: 1.5px solid var(--link);
      border-radius: 4px;
      font-size: .8rem;
      font-weight: 600;
      color: var(--link);
      transition: background .15s, color .15s;
    }
    .proj-link:hover {
      background: var(--link); color: #fff; text-decoration: none;
    }

    /* ══════════════════════
       AWARDS SECTION
       ══════════════════════ */
    #awards { padding: 72px 0 80px; background: #fff; }

    .awards-list { list-style: none; }
    .award-item {
      display: flex;
      align-items: flex-start;
      gap: 1.2rem;
      padding: 1.2rem 0;
      border-bottom: 1px solid var(--border);
    }
    .award-item:last-child { border-bottom: none; }

    .award-icon {
      width: 44px; height: 44px;
      border-radius: 50%;
      background: #fff7e0;
      border: 1.5px solid #f6c800;
      display: flex; align-items: center; justify-content: center;
      flex-shrink: 0;
      font-size: 1.2rem; color: #d4a017;
    }
    .award-body {}
    .award-title {
      font-family: 'Raleway', sans-serif;
      font-size: 1.05rem;
      font-weight: 700;
      color: var(--dark);
      margin-bottom: .15rem;
      line-height: 1.3;
    }
    .award-org {
      font-size: .88rem;
      color: var(--muted);
    }
    .award-year {
      font-size: .78rem;
      color: var(--link);
      font-weight: 600;
      margin-top: .18rem;
    }

    /* ══════════════════════
       CONTACT SECTION
       ══════════════════════ */
    #contact { padding: 72px 0 80px; background: #f9f9f9; }

    .contact-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 3rem;
      align-items: flex-start;
    }

    .contact-intro {
      font-size: 1rem;
      color: var(--text);
      line-height: 1.8;
      margin-bottom: 2rem;
    }

    .contact-items { list-style: none; }
    .contact-item {
      display: flex;
      align-items: center;
      gap: 1rem;
      margin-bottom: 1.1rem;
    }
    .contact-item-icon {
      width: 42px; height: 42px;
      border-radius: 50%;
      background: #eef4ff;
      display: flex; align-items: center; justify-content: center;
      color: var(--link);
      font-size: 1.1rem;
      flex-shrink: 0;
    }
    .contact-item-text {}
    .contact-item-label {
      font-size: .78rem;
      color: var(--muted);
      text-transform: uppercase;
      letter-spacing: .05em;
      margin-bottom: .05rem;
    }
    .contact-item-value {
      font-size: .95rem;
      color: var(--text);
      font-weight: 500;
    }
    .contact-item-value a { color: var(--link); }
    .contact-item-value a:hover { color: var(--link-h); }

    /* Simple contact form */
    .contact-form {}
    .form-group { margin-bottom: 1.1rem; }
    .form-group label {
      display: block;
      font-size: .82rem;
      font-weight: 600;
      color: var(--dark);
      margin-bottom: .35rem;
      text-transform: uppercase;
      letter-spacing: .04em;
    }
    .form-group input,
    .form-group textarea {
      width: 100%;
      padding: .7rem .9rem;
      border: 1.5px solid var(--border);
      border-radius: 5px;
      font-family: 'Inter', sans-serif;
      font-size: .93rem;
      color: var(--text);
      background: #fff;
      outline: none;
      transition: border-color .15s;
      resize: vertical;
    }
    .form-group input:focus,
    .form-group textarea:focus { border-color: var(--link); }
    .form-group textarea { min-height: 120px; }

    .form-submit {
      display: inline-flex; align-items: center; gap: .5rem;
      padding: .65rem 1.8rem;
      background: var(--link);
      color: #fff;
      border: none;
      border-radius: 5px;
      font-family: 'Raleway', sans-serif;
      font-size: 1rem;
      font-weight: 700;
      cursor: pointer;
      transition: background .15s;
    }
    .form-submit:hover { background: var(--link-h); }

    @media (max-width: 760px) {
      .tl-item { grid-template-columns: 1fr; }
      .tl-item::before { display: none; }
      .tl-date { text-align: left; padding-right: 0; margin-bottom: .2rem; }
      .tl-body { border-left: 3px solid var(--link); }
      .proj-grid { grid-template-columns: 1fr; }
      .contact-grid { grid-template-columns: 1fr; }
    }

    /* ══════════════════════
       FOOTER
       ══════════════════════ */
    footer {
      text-align: center;
      padding: 1.8rem 1rem;
      font-size: .82rem;
      color: #bbb;
      border-top: 1px solid var(--border);
      margin-top: 5rem;
    }
    footer a { color: #bbb; }

    /* ══════════════════════
       RESPONSIVE
       ══════════════════════ */
    @media (max-width: 760px) {
      body { font-size: 17px; }
      .about-grid    { grid-template-columns: 1fr; gap: 2rem; }
      .bio-two-col   { grid-template-columns: 1fr; }
      .nav-links     { display: none; }
      .nav-toggle    { display: block; }
      .nav-links.open {
        display: flex; flex-direction: column;
        position: absolute; top: var(--nav-h); left: 0; right: 0;
        background: #fff; border-bottom: 1px solid var(--border);
        padding: .5rem 0; box-shadow: 0 4px 10px rgba(0,0,0,.06);
      }
    }
  </style>
</head>
<body>

<!-- ══════════════════════
     NAVBAR
     ══════════════════════ -->
<nav id="navbar">
  <div class="nav-inner">
    <a class="nav-brand" href="#about">Academic</a>

    <button class="nav-toggle"
            onclick="this.nextElementSibling.classList.toggle('open')"
            aria-label="Menu">
      <span></span><span></span><span></span>
    </button>

    <ul class="nav-links">
      <li><a href="#about" class="active">Home</a></li>
      <li><a href="#schedule">Schedule</a></li>
      <li><a href="#experience">Experience</a></li>
      <li><a href="#projects">Projects</a></li>
      <li><a href="#awards">Awards</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>

    <div class="nav-icons">
      <button class="nav-icon-btn" title="Search" aria-label="Search">
        <i class="fas fa-search"></i>
      </button>
      <button class="nav-icon-btn" title="Toggle dark mode" aria-label="Dark mode">
        <i class="fas fa-moon"></i>
      </button>
    </div>
  </div>
</nav>

<!-- ══════════════════════
     ABOUT ME
     ══════════════════════ -->
<section id="about">
    <div class="container">
      <div class="about-grid">

        <!-- ── LEFT ── -->
        <div class="portrait-col">

          <img class="portrait-photo"
               src="photo.jpg"
               alt="Yihao Ma 马邑昊"
               onerror="this.outerHTML='<div class=\'portrait-fallback\'>👤</div>'" />

          <div class="portrait-name">Yihao Ma 马邑昊</div>
          <div class="portrait-role">MSc Student @ Imperial College London</div>
          <div class="portrait-org">
            <a href="https://www.imperial.ac.uk/business-school/programmes/msc-risk-management-financial-engineering/"
               target="_blank">Imperial College London</a>
          </div>

          <!-- Plain blue icon links — no background box -->
          <div class="social-row">

            <!-- Email -->
            <a href="mailto:ianyihaoma@163.com" class="sicon" title="Email">
              <i class="fas fa-envelope"></i>
            </a>

            <!-- WhatsApp -->
            <a href="https://wa.me/447350116442" target="_blank" class="sicon" title="WhatsApp">
              <i class="fab fa-whatsapp"></i>
            </a>

            <!-- LinkedIn -->
            <a href="https://www.linkedin.com/in/yihao-ma-9297a42b6/" target="_blank"
               class="sicon" title="LinkedIn">
              <i class="fab fa-linkedin"></i>
            </a>

            <!-- CV -->
            <a href="Yihao Ma - resume.pdf" target="_blank" class="sicon cv" title="Download CV">
              CV
            </a>

          </div>
        </div>

        <!-- ── RIGHT ── -->
        <div class="bio-col">
          <h1 class="bio-heading">About Me</h1>

          <p class="bio-para">
            Hi, I'm Yihao (Ian) Ma, currently an MSc student in
            <strong>Risk Management &amp; Financial Engineering</strong> at
            <a href="https://www.imperial.ac.uk/" target="_blank">Imperial College London</a>.
            My research interests lie at the intersection of
            <strong>quantitative finance</strong>, <strong>data science</strong>,
            and <strong>financial engineering</strong> — building rigorous,
            data-driven tools that bridge academic theory and real-world market dynamics.
          </p>

          <p class="bio-para">
            Previously, I interned as a Data Science Intern at
            <a href="https://www.tiktok.com/" target="_blank"><strong>TikTok UK</strong></a>
            and <a href="https://www.bytedance.com/" target="_blank"><strong>ByteDance</strong></a>,
            and as a Derivative Trading Research Intern at
            <strong>Industrial Securities</strong>, where I developed options pricing models
            and backtested delta-hedging strategies. I hold a
            <strong>First Class BBA in Finance (GPA 3.99/4, Rank 1)</strong>
            from <a href="https://www.uic.edu.hk/" target="_blank">Beijing Normal Hong Kong Baptist University</a>.
          </p>

          <p class="bio-para">
            I am a <strong>2025 CFA Research Challenge Local Final Champion</strong> and
            National Grand Prize winner at the CMAU Market Research Competition.
            I am always open to new challenges — if you are looking for someone rigorous,
            curious and driven, <a href="mailto:ianyihaoma@163.com">find me</a>.
          </p>

          <!-- Interests + Education two columns -->
          <div class="bio-two-col">

            <div>
              <div class="bio-subcol-title">Interests</div>
              <ul class="int-list">
                <li>
                  <i class="fas fa-chart-line"></i>
                  Quantitative Trading &amp; Derivatives
                </li>
                <li>
                  <i class="fas fa-brain"></i>
                  Machine Learning in Finance
                </li>
                <li>
                  <i class="fas fa-shield-halved"></i>
                  Risk Modelling &amp; Valuation
                </li>
                <li>
                  <i class="fas fa-database"></i>
                  Data Science &amp; Business Intelligence
                </li>
                <li>
                  <i class="fas fa-gears"></i>
                  Financial Engineering
                </li>
              </ul>
            </div>

            <div>
              <div class="bio-subcol-title">Education</div>
              <ul class="edu-list">
                <li>
                  <i class="fas fa-graduation-cap"></i>
                  <div>
                    <div class="edu-degree">MSc Risk Mgmt &amp; Financial Engineering, 25.08 – 26.08</div>
                    <div class="edu-school">Imperial College London</div>
                  </div>
                </li>
                <li>
                  <i class="fas fa-graduation-cap"></i>
                  <div>
                    <div class="edu-degree">BBA Finance (First Class), 21.09 – 25.06</div>
                    <div class="edu-school">Beijing Normal Hong Kong Baptist University</div>
                  </div>
                </li>
              </ul>
            </div>

          </div>
        </div><!-- /bio-col -->

      </div><!-- /about-grid -->
    </div>
  </section>

<!-- ══════════════════════════════════════
     SCHEDULE SECTION
     ══════════════════════════════════════ -->
<section id="schedule">
  <div class="container">
    <h2 class="schedule-heading">Schedule</h2>
    <p class="schedule-subtext">
      View my availability — synced live from Outlook (Imperial College London).
    </p>

    <div class="schedule-grid">
      <div class="cal-sources">
        <span class="cal-source-badge outlook" id="cal-status">
          <i class="fab fa-microsoft"></i> Outlook · 加载中…
        </span>
      </div>

      <div class="cal-wrap">
        <div id="cal-error" style="display:none; padding:1.5rem; text-align:center; color:#888; font-size:.9rem;">
          <i class="fas fa-calendar-xmark" style="font-size:2rem; display:block; margin-bottom:.7rem; color:#ddd;"></i>
          日历暂时无法加载。请稍后刷新，或直接
          <a href="mailto:ianyihaoma@163.com">发邮件</a>联系我。
        </div>
        <div id="calendar"></div>
      </div>
    </div>
  </div>
</section>

<!-- ══════════════════════════════════════
     EXPERIENCE SECTION
     ══════════════════════════════════════ -->
<section id="experience">
  <div class="container">
    <h2 class="section-heading">Experience</h2>

    <div class="timeline">

      <!-- TikTok UK -->
      <div class="tl-item">
        <div class="tl-date">Jun 2024 – Sep 2024</div>
        <div class="tl-body">
          <div class="tl-role">Data Science Intern</div>
          <div class="tl-company">
            <a href="https://www.tiktok.com/" target="_blank">TikTok UK</a>
          </div>
          <div class="tl-loc"><i class="fas fa-location-dot"></i>&nbsp; London, United Kingdom</div>
          <div class="tl-desc">
            <ul>
              <li>Built and deployed machine-learning models to optimise content recommendation and creator growth, directly impacting platform engagement metrics.</li>
              <li>Designed A/B testing frameworks and conducted statistical analysis on large-scale user behaviour datasets to validate product hypotheses.</li>
              <li>Collaborated cross-functionally with product and engineering teams to translate analytical insights into actionable roadmap items.</li>
            </ul>
          </div>
          <div class="tl-tags">
            <span class="tl-tag">Python</span>
            <span class="tl-tag">Machine Learning</span>
            <span class="tl-tag">A/B Testing</span>
            <span class="tl-tag">SQL</span>
            <span class="tl-tag">Data Science</span>
          </div>
        </div>
      </div>

      <!-- ByteDance -->
      <div class="tl-item">
        <div class="tl-date">Jun 2023 – Sep 2023</div>
        <div class="tl-body">
          <div class="tl-role">Data Science Intern</div>
          <div class="tl-company">
            <a href="https://www.bytedance.com/" target="_blank">ByteDance</a>
          </div>
          <div class="tl-loc"><i class="fas fa-location-dot"></i>&nbsp; Beijing, China</div>
          <div class="tl-desc">
            <ul>
              <li>Developed data pipelines and dashboards for real-time monitoring of core business KPIs across multiple product lines.</li>
              <li>Applied NLP and clustering techniques to extract insights from user-generated content, informing strategy for international markets.</li>
              <li>Wrote production-grade Python scripts for ETL workflows processing billions of daily events.</li>
            </ul>
          </div>
          <div class="tl-tags">
            <span class="tl-tag">Python</span>
            <span class="tl-tag">NLP</span>
            <span class="tl-tag">ETL</span>
            <span class="tl-tag">Data Pipelines</span>
            <span class="tl-tag">Spark</span>
          </div>
        </div>
      </div>

      <!-- Industrial Securities -->
      <div class="tl-item">
        <div class="tl-date">Dec 2022 – Feb 2023</div>
        <div class="tl-body">
          <div class="tl-role">Derivative Trading Research Intern</div>
          <div class="tl-company">Industrial Securities</div>
          <div class="tl-loc"><i class="fas fa-location-dot"></i>&nbsp; Shanghai, China</div>
          <div class="tl-desc">
            <ul>
              <li>Developed options pricing models using Black-Scholes and Heston frameworks; backtested delta-hedging strategies on CSI 300 index options.</li>
              <li>Conducted volatility surface construction and Greeks analysis to support trading desk decision-making.</li>
              <li>Produced weekly research reports on equity derivatives market conditions for institutional clients.</li>
            </ul>
          </div>
          <div class="tl-tags">
            <span class="tl-tag">Derivatives</span>
            <span class="tl-tag">Options Pricing</span>
            <span class="tl-tag">Python</span>
            <span class="tl-tag">Backtesting</span>
            <span class="tl-tag">Quantitative Finance</span>
          </div>
        </div>
      </div>

      <!-- KPMG -->
      <div class="tl-item">
        <div class="tl-date">Jun 2022 – Aug 2022</div>
        <div class="tl-body">
          <div class="tl-role">Audit Intern</div>
          <div class="tl-company">
            <a href="https://home.kpmg/cn/en/home.html" target="_blank">KPMG</a>
          </div>
          <div class="tl-loc"><i class="fas fa-location-dot"></i>&nbsp; Beijing, China</div>
          <div class="tl-desc">
            <ul>
              <li>Assisted senior auditors in financial statement review and internal control testing for listed companies across the retail and technology sectors.</li>
              <li>Prepared working papers and reconciliation schedules; identified discrepancies and escalated findings to the engagement manager.</li>
            </ul>
          </div>
          <div class="tl-tags">
            <span class="tl-tag">Audit</span>
            <span class="tl-tag">Financial Analysis</span>
            <span class="tl-tag">Excel</span>
            <span class="tl-tag">Internal Controls</span>
          </div>
        </div>
      </div>

    </div><!-- /timeline -->
  </div>
</section>


<!-- ══════════════════════════════════════
     PROJECTS SECTION
     ══════════════════════════════════════ -->
<section id="projects">
  <div class="container">
    <h2 class="section-heading">Projects</h2>

    <div class="proj-grid">

      <!-- Project 1 -->
      <div class="proj-card">
        <div class="proj-img"><i class="fas fa-chart-line"></i></div>
        <div class="proj-body">
          <div class="proj-title">Volatility Surface Construction &amp; Options Pricing</div>
          <div class="proj-meta">Quantitative Finance · 2023</div>
          <div class="proj-desc">
            Built an end-to-end pipeline to construct implied volatility surfaces from market quotes for CSI 300 index options. Implemented local volatility (Dupire) and Heston stochastic volatility models, and compared pricing accuracy against the Black-Scholes benchmark.
          </div>
          <div class="proj-tags">
            <span class="proj-tag">Python</span>
            <span class="proj-tag">QuantLib</span>
            <span class="proj-tag">Scipy</span>
            <span class="proj-tag">Options</span>
          </div>
        </div>
      </div>

      <!-- Project 2 -->
      <div class="proj-card">
        <div class="proj-img" style="background: linear-gradient(135deg, #00875a 0%, #006644 100%);">
          <i class="fas fa-brain"></i>
        </div>
        <div class="proj-body">
          <div class="proj-title">ML-Driven Alpha Factor Research</div>
          <div class="proj-meta">Machine Learning · 2024</div>
          <div class="proj-desc">
            Designed and backtested a systematic alpha factor library using gradient boosting (XGBoost, LightGBM) on A-share market data. Achieved statistically significant IC scores through rigorous walk-forward validation and transaction-cost-aware portfolio construction.
          </div>
          <div class="proj-tags">
            <span class="proj-tag">XGBoost</span>
            <span class="proj-tag">LightGBM</span>
            <span class="proj-tag">Backtesting</span>
            <span class="proj-tag">Factor Investing</span>
          </div>
        </div>
      </div>

      <!-- Project 3 -->
      <div class="proj-card">
        <div class="proj-img" style="background: linear-gradient(135deg, #744fc6 0%, #4a2d8a 100%);">
          <i class="fas fa-shield-halved"></i>
        </div>
        <div class="proj-body">
          <div class="proj-title">Credit Risk Modelling — PD Estimation</div>
          <div class="proj-meta">Risk Management · 2025</div>
          <div class="proj-desc">
            Developed a Probability of Default (PD) model for a corporate loan portfolio using logistic regression and survival analysis. Calibrated the model against through-the-cycle (TTC) benchmarks and stress-tested under adverse macroeconomic scenarios.
          </div>
          <div class="proj-tags">
            <span class="proj-tag">Credit Risk</span>
            <span class="proj-tag">Survival Analysis</span>
            <span class="proj-tag">Python</span>
            <span class="proj-tag">Statsmodels</span>
          </div>
        </div>
      </div>

      <!-- Project 4 -->
      <div class="proj-card">
        <div class="proj-img" style="background: linear-gradient(135deg, #e05a00 0%, #a03600 100%);">
          <i class="fas fa-database"></i>
        </div>
        <div class="proj-body">
          <div class="proj-title">NLP Sentiment Analysis for Market Signals</div>
          <div class="proj-meta">NLP · Data Science · 2023</div>
          <div class="proj-desc">
            Fine-tuned a FinBERT model on Chinese financial news to generate daily sentiment scores for A-share listed companies. Integrated sentiment signals with technical factors in a long-short portfolio and demonstrated improved Sharpe ratio versus a pure factor baseline.
          </div>
          <div class="proj-tags">
            <span class="proj-tag">FinBERT</span>
            <span class="proj-tag">NLP</span>
            <span class="proj-tag">PyTorch</span>
            <span class="proj-tag">Sentiment</span>
          </div>
        </div>
      </div>

    </div><!-- /proj-grid -->
  </div>
</section>


<!-- ══════════════════════════════════════
     AWARDS SECTION
     ══════════════════════════════════════ -->
<section id="awards">
  <div class="container">
    <h2 class="section-heading">Awards &amp; Honors</h2>

    <ul class="awards-list">

      <li class="award-item">
        <div class="award-icon"><i class="fas fa-trophy"></i></div>
        <div class="award-body">
          <div class="award-title">CFA Research Challenge — Local Final Champion</div>
          <div class="award-org">CFA Society United Kingdom</div>
          <div class="award-year">2025</div>
        </div>
      </li>

      <li class="award-item">
        <div class="award-icon"><i class="fas fa-medal"></i></div>
        <div class="award-body">
          <div class="award-title">National Grand Prize — CMAU Market Research Competition</div>
          <div class="award-org">China Market Research Association (CMAU)</div>
          <div class="award-year">2024</div>
        </div>
      </li>

      <li class="award-item">
        <div class="award-icon"><i class="fas fa-star"></i></div>
        <div class="award-body">
          <div class="award-title">First Class BBA — GPA 3.99 / 4.0, Rank 1 in Cohort</div>
          <div class="award-org">Beijing Normal Hong Kong Baptist University</div>
          <div class="award-year">2021 – 2025</div>
        </div>
      </li>

      <li class="award-item">
        <div class="award-icon"><i class="fas fa-award"></i></div>
        <div class="award-body">
          <div class="award-title">Dean's List — Excellence Scholarship (×3)</div>
          <div class="award-org">Beijing Normal Hong Kong Baptist University</div>
          <div class="award-year">2021 – 2024</div>
        </div>
      </li>

    </ul>
  </div>
</section>


<!-- ══════════════════════════════════════
     CONTACT SECTION
     ══════════════════════════════════════ -->
<section id="contact">
  <div class="container">
    <h2 class="section-heading">Contact</h2>

    <div class="contact-grid">

      <!-- Left: contact info -->
      <div>
        <p class="contact-intro">
          Feel free to reach out if you'd like to discuss research opportunities,
          internships, or anything at the intersection of quantitative finance and data science.
          I typically reply within one business day.
        </p>

        <ul class="contact-items">
          <li class="contact-item">
            <div class="contact-item-icon"><i class="fas fa-envelope"></i></div>
            <div class="contact-item-text">
              <div class="contact-item-label">Email</div>
              <div class="contact-item-value">
                <a href="mailto:ianyihaoma@163.com">ianyihaoma@163.com</a>
              </div>
            </div>
          </li>
          <li class="contact-item">
            <div class="contact-item-icon"><i class="fab fa-whatsapp"></i></div>
            <div class="contact-item-text">
              <div class="contact-item-label">WhatsApp</div>
              <div class="contact-item-value">
                <a href="https://wa.me/447350116442" target="_blank">+44 0735 0116442</a>
              </div>
            </div>
          </li>
          <li class="contact-item">
            <div class="contact-item-icon"><i class="fab fa-linkedin"></i></div>
            <div class="contact-item-text">
              <div class="contact-item-label">LinkedIn</div>
              <div class="contact-item-value">
                <a href="https://www.linkedin.com/in/yihao-ma-9297a42b6/" target="_blank">Yihao Ma</a>
              </div>
            </div>
          </li>
          <li class="contact-item">
            <div class="contact-item-icon"><i class="fas fa-map-marker-alt"></i></div>
            <div class="contact-item-text">
              <div class="contact-item-label">Location</div>
              <div class="contact-item-value">London, United Kingdom</div>
            </div>
          </li>
        </ul>
      </div>

      <!-- Right: contact form (mailto-based) -->
      <div class="contact-form">
        <form action="mailto:ianyihaoma@163.com" method="get" enctype="text/plain">
          <div class="form-group">
            <label for="cf-name">Your Name</label>
            <input type="text" id="cf-name" name="name" placeholder="Jane Smith" required />
          </div>
          <div class="form-group">
            <label for="cf-email">Your Email</label>
            <input type="email" id="cf-email" name="email" placeholder="jane@example.com" required />
          </div>
          <div class="form-group">
            <label for="cf-subject">Subject</label>
            <input type="text" id="cf-subject" name="subject" placeholder="Research collaboration" />
          </div>
          <div class="form-group">
            <label for="cf-msg">Message</label>
            <textarea id="cf-msg" name="body" placeholder="Hi Yihao, I'd love to…"></textarea>
          </div>
          <button type="submit" class="form-submit">
            <i class="fas fa-paper-plane"></i> Send Message
          </button>
        </form>
      </div>

    </div><!-- /contact-grid -->
  </div>
</section>


<footer>
  © 2026 Yihao (Ian) Ma 马邑昊 &nbsp;·&nbsp;
  Powered by <a href="https://hugoblox.com" target="_blank">Wowchemy</a>
</footer>

<script>
/* ── Nav active highlight on scroll ── */
const navLinks = document.querySelectorAll('.nav-links a[href^="#"]');
const sections = document.querySelectorAll('section[id]');
window.addEventListener('scroll', () => {
  let cur = '';
  sections.forEach(s => { if (window.scrollY >= s.offsetTop - 90) cur = s.id; });
  navLinks.forEach(l => l.classList.toggle('active', l.getAttribute('href') === '#' + cur));
});

/* ── FullCalendar + ICS sync from Outlook ── */
const ICS_URL = 'https://outlook.office365.com/owa/calendar/23cc44178634439a98f6378410b27018@imperial.ac.uk/5199c2df17c54c69979c1aa4d3befa68587884087647201419/calendar.ics';

// Manual timeout wrapper (AbortSignal.timeout not available in all browsers)
function fetchWithTimeout(url, ms) {
  const ctrl = new AbortController();
  const tid  = setTimeout(() => ctrl.abort(), ms);
  return fetch(url, { signal: ctrl.signal })
    .finally(() => clearTimeout(tid));
}

// CORS proxies tried in order; first one to return valid ICS wins
const PROXIES = [
  url => `https://corsproxy.io/?url=${encodeURIComponent(url)}`,
  url => `https://api.allorigins.win/raw?url=${encodeURIComponent(url)}`,
  url => `https://api.codetabs.com/v1/proxy?quest=${encodeURIComponent(url)}`,
  url => `https://corsproxy.io/?${encodeURIComponent(url)}`,
];

async function fetchICS() {
  for (let i = 0; i < PROXIES.length; i++) {
    const proxyUrl = PROXIES[i](ICS_URL);
    try {
      console.log('[Cal] Trying proxy', i + 1, ':', proxyUrl);
      const res  = await fetchWithTimeout(proxyUrl, 12000);
      const text = await res.text();
      console.log('[Cal] Proxy', i + 1, 'status:', res.status, '| starts with:', text.slice(0, 80));
      if (text.includes('BEGIN:VCALENDAR')) {
        console.log('[Cal] ✓ Proxy', i + 1, 'returned valid ICS');
        return text;
      }
    } catch (e) {
      console.warn('[Cal] Proxy', i + 1, 'failed:', e.message);
    }
  }
  console.error('[Cal] All proxies failed for URL:', ICS_URL);
  return null;
}

function parseICS(icsText) {
  const jcal   = ICAL.parse(icsText);
  const comp   = new ICAL.Component(jcal);
  const vevs   = comp.getAllSubcomponents('vevent');
  return vevs.map(ev => {
    const e = new ICAL.Event(ev);
    return {
      title:  e.summary || '(busy)',
      start:  e.startDate.toJSDate(),
      end:    e.endDate ? e.endDate.toJSDate() : undefined,
      allDay: e.startDate.isDate,
    };
  });
}

document.addEventListener('DOMContentLoaded', async () => {
  const calEl    = document.getElementById('calendar');
  const errEl    = document.getElementById('cal-error');
  const statusEl = document.getElementById('cal-status');

  // Render calendar grid immediately (empty)
  const calendar = new FullCalendar.Calendar(calEl, {
    initialView: 'dayGridMonth',
    headerToolbar: {
      left:   'prev,next today',
      center: 'title',
      right:  'dayGridMonth,timeGridWeek,listWeek',
    },
    height:         660,
    firstDay:       1,
    eventColor:     '#1772d0',
    eventTextColor: '#fff',
    nowIndicator:   true,
    editable:       false,
    selectable:     false,
  });
  calendar.render();

  // Load ICS in background
  const icsText = await fetchICS();
  if (!icsText) {
    errEl.style.display  = 'block';
    calEl.style.display  = 'none';
    statusEl.innerHTML   = '<i class="fab fa-microsoft"></i> Outlook · 加载失败';
    statusEl.style.color = '#c00';
    statusEl.style.borderColor = '#c00';
    return;
  }

  try {
    const events = parseICS(icsText);
    events.forEach(ev => calendar.addEvent(ev));
    statusEl.innerHTML = `<i class="fab fa-microsoft"></i> Outlook · ${events.length} 个事件已同步`;
    statusEl.classList.add('loaded');
  } catch (e) {
    console.error('[Cal] Parse error:', e);
    errEl.style.display = 'block';
    calEl.style.display = 'none';
  }
});
</script>

</body>
</html>
