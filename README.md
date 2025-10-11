<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>YourGoatViper — Official</title>
  <style>
    /* Reset */
    *{box-sizing:border-box;margin:0;padding:0}
    html,body{height:100%;font-family:Inter, "Segoe UI", Roboto, Arial, sans-serif;color:#fff}
    a{color:inherit;text-decoration:none}

    /* Background poster */
    .bg{
      position:fixed;inset:0;background-image:url('IMG_1703.jpeg');
      background-size:cover;background-position:center center;filter:brightness(.45);
      z-index:-2;
    }

    /* subtle overlay for readability */
    .overlay{
      position:fixed;inset:0;background:linear-gradient(90deg, rgba(0,0,0,.65) 0%, rgba(0,0,0,.6) 60%, rgba(10,10,10,.35) 100%);
      z-index:-1;
    }

    /* Nav */
    header{
      position:fixed;left:0;right:0;top:22px;padding:18px 36px;display:flex;align-items:center;justify-content:space-between;
      z-index:40;
    }
    .brand{font-weight:700;color:#ff6a2b;letter-spacing:1px}
    nav{display:flex;gap:22px;align-items:center}
    nav a{color:#fff;opacity:.95}
    nav a:hover{opacity:1;text-decoration:underline}

    /* Center hero area - keep design consistent with poster: large typographic block left, basketball/flame on right */
    .hero{
      min-height:100vh;display:flex;align-items:center;padding:8vh 6vw;
      gap:3rem;
    }

    .left{
      max-width:760px;
      transform-origin:left center;
      animation:fadeUp .9s ease both;
    }

    .subtitle{
      font-size:13px;letter-spacing:6px;color:rgba(255,255,255,.8);
      margin-bottom:14px;text-transform:uppercase
    }

    .title{
      font-size:78px;line-height:.9;font-weight:900;color:#e35a23;
      text-shadow: 0 6px 18px rgba(0,0,0,.6);
      margin-bottom:22px;
      font-family: "Bebas Neue", "Arial Black", sans-serif;
    }

    .cta-row{
      display:flex;gap:18px;align-items:center;margin-top:10px;
    }
    .btn{
      background:linear-gradient(180deg,#bf4a1d,#e36b2b);
      color:#fff;padding:12px 26px;border-radius:6px;border:none;cursor:pointer;font-weight:700;
      box-shadow:0 8px 30px rgba(227,107,43,.12);
      transform:translateZ(0);transition:transform .22s ease,box-shadow .22s;
    }
    .btn:hover{transform:translateY(-4px);box-shadow:0 18px 40px rgba(227,107,43,.18)}
    .btn:active{transform:translateY(-1px)}

    /* small floating info card with animated boxes */
    .info-card{
      margin-top:30px;background:rgba(255,255,255,.04);backdrop-filter: blur(4px);
      padding:16px;border-radius:12px;display:inline-flex;gap:14px;align-items:center;
      animation:float 4s ease-in-out infinite;
      border:1px solid rgba(255,255,255,.05)
    }
    .price-box{
      background:linear-gradient(180deg, rgba(255,255,255,.03), rgba(255,255,255,.02));
      padding:10px 14px;border-radius:8px;text-align:center;min-width:110px;
      box-shadow: 0 6px 22px rgba(0,0,0,.45);
      transition:transform .2s ease,box-shadow .2s;
    }
    .price-box:hover{transform:translateY(-6px);box-shadow:0 18px 40px rgba(0,0,0,.55)}
    .price-title{font-size:13px;color:rgba(255,255,255,.8);margin-bottom:6px}
    .price-value{font-size:20px;font-weight:800;color:#fff}

    /* right area reserved but we won't change poster elements (keeps poster unchanged) */
    .right{flex:1;min-height:360px;display:flex;align-items:center;justify-content:center;padding-right:4vw}

    /* Modal for social links (Continue) */
    .modal{
      position:fixed;inset:0;display:flex;align-items:center;justify-content:center;padding:28px;
      visibility:hidden;opacity:0;transition:opacity .25s ease,visibility .25s .25s;
      z-index:80;
    }
    .modal.visible{visibility:visible;opacity:1;transition:opacity .25s ease}
    .modal-backdrop{
      position:absolute;inset:0;background:rgba(0,0,0,.6);backdrop-filter: blur(2px)
    }
    .modal-card{
      position:relative;max-width:920px;width:100%;background:linear-gradient(180deg,#0b0b0b,#0f0f0f);
      border-radius:14px;padding:28px;box-shadow:0 20px 60px rgba(0,0,0,.6);transform:translateY(18px);
      animation:cardIn .4s cubic-bezier(.2,.9,.18,1) both;
      display:grid;grid-template-columns:1fr 340px;gap:18px;overflow:hidden;border:1px solid rgba(255,255,255,.04)
    }

    .modal-left h2{font-size:24px;margin-bottom:8px}
    .meta-line{color:rgba(255,255,255,.7);margin-bottom:14px}

    .social-grid{display:flex;flex-wrap:wrap;gap:12px}
    .social{
      display:flex;align-items:center;gap:12px;padding:12px 14px;border-radius:10px;background:linear-gradient(180deg, rgba(255,255,255,.02), rgba(255,255,255,.01));
      min-width:180px;cursor:pointer;border:1px solid rgba(255,255,255,.03);transition:transform .18s,box-shadow .18s;
    }
    .social:hover{transform:translateY(-6px);box-shadow:0 14px 40px rgba(0,0,0,.6)}

    .social svg{width:26px;height:26px;flex-shrink:0}
    .social span{font-weight:700}

    /* right column with QR & entry / prize boxes */
    .modal-right{display:flex;flex-direction:column;align-items:center;gap:12px}
    .qr-wrap{background:#fff;padding:10px;border-radius:10px}
    .qr-wrap img{width:220px;height:220px;display:block}

    .small-note{font-size:13px;color:rgba(255,255,255,.75);text-align:center;margin-top:8px}

    /* About/Contact sections - slide panels */
    .panel{
      position:fixed;top:0;right:-100%;height:100vh;width:420px;background:linear-gradient(180deg,#071017,#0f1a1f);
      z-index:70;padding:28px;box-shadow:-14px 0 40px rgba(0,0,0,.6);transition:right .36s cubic-bezier(.2,.9,.18,1)
    }
    .panel.open{right:0}
    .panel h3{margin-bottom:8px}
    .panel p{color:rgba(255,255,255,.8);line-height:1.35;margin-bottom:14px}
    .panel .links{display:flex;flex-direction:column;gap:8px}
    .panel a{background:rgba(255,255,255,.03);padding:10px;border-radius:8px;color:#fff;border:1px solid rgba(255,255,255,.03)}

    /* small footer hint */
    .footer-hint{position:fixed;left:18px;bottom:18px;color:rgba(255,255,255,.8);font-size:13px}

    /* Animations */
    @keyframes fadeUp{from{opacity:0;transform:translateY(12px)}to{opacity:1;transform:translateY(0)}}
    @keyframes float{0%{transform:translateY(0)}50%{transform:translateY(-8px)}100%{transform:translateY(0)}}
    @keyframes cardIn{from{opacity:0;transform:translateY(18px) scale(.995)}to{opacity:1;transform:translateY(0) scale(1)}}

    /* Responsive */
    @media (max-width:980px){
      .title{font-size:48px}
      .hero{padding:8vh 5vw}
      .modal-card{grid-template-columns:1fr;max-width:640px}
      .modal-right{order:-1}
    }
    @media (max-width:520px){
      .title{font-size:36px}
      header{padding:12px 18px}
      nav{gap:12px}
      .brand{font-size:14px}
      .price-box{min-width:86px}
      .modal-card{padding:18px}
      .qr-wrap img{width:160px;height:160px}
    }

  </style>
</head>
<body>

  <div class="bg" aria-hidden="true"></div>
  <div class="overlay" aria-hidden="true"></div>

  <header>
    <div class="brand">ARHAM ARAIN</div>
    <nav>
      <a href="#" id="nav-home">Home</a>
      <a href="#" id="nav-about">About</a>
      <a href="#" id="nav-contact">Contact</a>
    </nav>
  </header>

  <main>
    <section class="hero">
      <div class="left">
        <div class="subtitle">YOU GOAT VIPER OFFICIAL WEBSITE</div>
        <h1 class="title">YOURGOAT<br>VIPER</h1>

        <div class="cta-row">
          <button class="btn" id="continueBtn">Continue</button>
        </div>

        <!-- the details text you asked for (kept visually on left) -->
        <div class="info-card" aria-hidden="false" style="margin-top:26px;">
          <div>
            <div style="font-weight:800;font-size:17px">YourGoatViper</div>
            <div style="font-size:13px;color:rgba(255,255,255,.8);margin-top:6px;max-width:480px">
              Pubg content creator 🔥 34 tournament winner 🥇, Tdm player, Pakistan #3 player, Account seller,
              GFX designer, editor.
              <div style="margin-top:8px;color:rgba(255,255,255,.65);font-size:13px">
                <strong>International tournament:</strong> YourGoatViper is organising an international tournament — many international players are coming and all matches will be live-streamed with commentary.
              </div>
            </div>
          </div>

          <div style="display:flex;flex-direction:column;align-items:center;justify-content:center;margin-left:18px">
            <div class="price-box">
              <div class="price-title">Entry Fee</div>
              <div class="price-value">200</div>
            </div>
            <div class="price-box" style="margin-top:10px">
              <div class="price-title">Prize Pool</div>
              <div class="price-value">5K + Intl entry free</div>
            </div>
          </div>
        </div>
      </div>

      <div class="right" aria-hidden="true">
        <!-- intentionally empty so poster's right visuals remain untouched -->
      </div>

    </section>
  </main>

  <div class="footer-hint">Tap "Continue" to message me or open my channels</div>

  <!-- Modal with socials & QR -->
  <div class="modal" id="modal">
    <div class="modal-backdrop" id="modalBackdrop"></div>

    <div class="modal-card" role="dialog" aria-modal="true" aria-labelledby="modalTitle">
      <div class="modal-left">
        <h2 id="modalTitle">Connect with YourGoatViper</h2>
        <div class="meta-line">Direct links to WhatsApp, Instagram, Snapchat, YouTube, TikTok — tap any to open</div>

        <div class="social-grid">
          <!-- WhatsApp -->
          <a class="social" href="https://wa.me/923348666640" target="_blank" rel="noopener noreferrer">
            <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M20.52 3.48A11.88 11.88 0 0 0 12 0C5.372 0 .03 5.342.03 12c0 2.116.552 4.19 1.6 6.02L0 24l6.2-1.61A11.94 11.94 0 0 0 12 24c6.628 0 12-5.372 12-12 0-1.98-.48-3.86-1.48-5.52z" fill="#25D366"/></svg>
            <span>WhatsApp</span>
          </a>

          <!-- Instagram -->
          <a class="social" href="https://www.instagram.com/arham_arain333?igsh=NGhobDk1c29rd3oy&utm_source=qr" target="_blank" rel="noopener noreferrer">
            <svg viewBox="0 0 24 24"><rect width="24" height="24" rx="6" fill="url(#g)"/><defs><linearGradient id="g" x1="0" x2="1"><stop offset="0" stop-color="#feda75"/><stop offset="1" stop-color="#d62976"/></linearGradient></defs></svg>
            <span>Instagram</span>
          </a>

          <!-- Snapchat -->
          <a class="social" href="https://snapchat.com/t/pJwMTBOf" target="_blank" rel="noopener noreferrer">
            <svg viewBox="0 0 24 24"><path d="M12 2C8.7 2 6 4.7 6 8.1c0 3.4 2.7 6.2 6 6.2s6-2.8 6-6.2C18 4.7 15.3 2 12 2z" fill="#FFFC00"/></svg>
            <span>Snapchat</span>
          </a>

          <!-- YouTube -->
          <a class="social" href="https://www.youtube.com/@YourGoatViper" target="_blank" rel="noopener noreferrer">
            <svg viewBox="0 0 24 24"><path d="M23 7.2s-.2-1.6-.8-2.3c-.8-.9-1.7-.9-2.1-1C16.6 3.5 12 3.5 12 3.5s-4.6 0-7.9.5c-.4.1-1.3.1-2.1 1C1.2 5.6 1 7.2 1 7.2S.8 9 .8 10.8v2.4C.8 15 1 16.6 1 16.6s.2 1.6.8 2.3c.8.9 1.8.9 2.3 1 2.2.3 7.9.5 7.9.5s4.6 0 7.9-.5c.4-.1 1.3-.1 2.1-1 .6-.7.8-2.3.8-2.3s.2-1.6.2-3.4v-2.4C23.2 9 23 7.2 23 7.2z" fill="#FF0000"/></svg>
            <span>YouTube</span>
          </a>

          <!-- TikTok -->
          <a class="social" href="https://www.tiktok.com/@yourgoatviper?_t=ZS-90S6zQCiZwS&_r=1" target="_blank" rel="noopener noreferrer">
            <svg viewBox="0 0 24 24"><path d="M9 2v12.6c0 2.3-1.9 4.1-4.2 4.1-2 0-3.7-1.4-4.1-3.3A4.4 4.4 0 0 0 1 14.6c.5 0 1 .1 1.6.1 1.9 0 3.9-.8 5.4-2.2V2h4z" fill="#69C9D0"/></svg>
            <span>TikTok</span>
          </a>
        </div>

        <div style="margin-top:14px;color:rgba(255,255,255,.65);font-size:13px">
          <strong>WhatsApp number:</strong> +92 334 8666640
        </div>
      </div>

      <div class="modal-right">
        <div class="qr-wrap" title="WhatsApp QR">
          <img src="IMG_1698.jpeg" alt="WhatsApp QR code">
        </div>

        <div class="small-note">Scan or tap WhatsApp to message me directly.</div>

        <div style="display:flex;gap:10px;margin-top:6px">
          <div style="padding:10px;border-radius:8px;background:linear-gradient(180deg,#151515,#0b0b0b);text-align:center">
            <div style="font-size:12px;color:rgba(255,255,255,.7)">Entry Fee</div>
            <div style="font-weight:900;font-size:18px">200</div>
          </div>
          <div style="padding:10px;border-radius:8px;background:linear-gradient(180deg,#151515,#0b0b0b);text-align:center">
            <div style="font-size:12px;color:rgba(255,255,255,.7)">Prize Pool</div>
            <div style="font-weight:900;font-size:18px">5K + Int'l entry free</div>
          </div>
        </div>

        <div style="display:flex;gap:8px;margin-top:10px">
          <button class="btn" onclick="window.open('https://wa.me/923348666640','_blank')">WhatsApp</button>
          <button class="btn" onclick="closeModal()" style="background:linear-gradient(180deg,#333,#222)">Close</button>
        </div>
      </div>
    </div>
  </div>

  <!-- About & Contact slide panels -->
  <aside class="panel" id="aboutPanel" aria-hidden="true">
    <h3>About</h3>
    <p>Owner of this website is <strong>YourGoatViper</strong>. This is the official page for tournament info, content announcements, and direct contact.</p>
    <div class="links">
      <a href="https://wa.me/923348666640" target="_blank" rel="noopener noreferrer">WhatsApp — +92 334 8666640</a>
      <a href="https://www.instagram.com/arham_arain333?igsh=NGhobDk1c29rd3oy&utm_source=qr" target="_blank" rel="noopener noreferrer">Instagram — arham_arain333</a>
      <a href="https://snapchat.com/t/pJwMTBOf" target="_blank" rel="noopener noreferrer">Snapchat — Aarain21553</a>
      <a href="https://www.tiktok.com/@yourgoatviper?_t=ZS-90S6zQCiZwS&_r=1" target="_blank" rel="noopener noreferrer">TikTok — yourgoatviper</a>
      <a href="https://www.youtube.com/@YourGoatViper" target="_blank" rel="noopener noreferrer">YouTube — YourGoatViper</a>
    </div>
  </aside>

  <aside class="panel" id="contactPanel" aria-hidden="true">
    <h3>Contact</h3>
    <p>Direct message me on WhatsApp or follow my social channels below.</p>

    <div class="links">
      <a href="https://wa.me/923348666640" target="_blank" rel="noopener noreferrer">WhatsApp: +92 334 8666640</a>
      <a href="https://www.instagram.com/arham_arain333?igsh=NGhobDk1c29rd3oy&utm_source=qr" target="_blank" rel="noopener noreferrer">Instagram: arham_arain333</a>
      <a href="https://snapchat.com/t/pJwMTBOf" target="_blank" rel="noopener noreferrer">Snapchat: Aarain21553</a>
      <a href="https://www.tiktok.com/@yourgoatviper?_t=ZS-90S6zQCiZwS&_r=1" target="_blank" rel="noopener noreferrer">TikTok</a>
      <a href="https://www.youtube.com/@YourGoatViper" target="_blank" rel="noopener noreferrer">YouTube</a>
    </div>
  </aside>

<script>
  // Modal open/close
  const continueBtn = document.getElementById('continueBtn');
  const modal = document.getElementById('modal');
  const modalBackdrop = document.getElementById('modalBackdrop');

  continueBtn.addEventListener('click', () => {
    modal.classList.add('visible');
  });

  function closeModal(){
    modal.classList.remove('visible');
  }

  modalBackdrop.addEventListener('click', closeModal);
  document.addEventListener('keydown', (e) => {
    if(e.key === 'Escape') closeModal();
  });

  // Panels for About and Contact
  const aboutPanel = document.getElementById('aboutPanel');
  const contactPanel = document.getElementById('contactPanel');
  const navAbout = document.getElementById('nav-about');
  const navContact = document.getElementById('nav-contact');
  const navHome = document.getElementById('nav-home');

  navAbout.addEventListener('click', (e) => {
    e.preventDefault();
    aboutPanel.classList.add('open');
    contactPanel.classList.remove('open');
  });

  navContact.addEventListener('click', (e) => {
    e.preventDefault();
    contactPanel.classList.add('open');
    aboutPanel.classList.remove('open');
  });

  navHome.addEventListener('click', (e) => {
    e.preventDefault();
    aboutPanel.classList.remove('open');
    contactPanel.classList.remove('open');
    closeModal();
    // scroll to top (visual return to poster/home)
    window.scrollTo({top:0,behavior:'smooth'});
  });

  // Close panels when clicking outside (on Escape)
  document.addEventListener('keydown', (e) => {
    if (e.key === 'Escape') {
      aboutPanel.classList.remove('open');
      contactPanel.classList.remove('open');
    }
  });

  // small accessibility: open WhatsApp QR image in new tab when clicked
  document.querySelectorAll('.qr-wrap img').forEach(img => {
    img.style.cursor = 'pointer';
    img.addEventListener('click', () => {
      window.open(img.src, '_blank');
    });
  });
</script>

</body>
</html>
