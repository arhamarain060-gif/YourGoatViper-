<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>YourGoatViper — Official</title>

  <style>
    /* ------------------------------ RESET ------------------------------ */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Poppins', sans-serif;
      background: #000;
      color: #fff;
      scroll-behavior: smooth;
    }

    /* ------------------------------ HEADER ------------------------------ */
    header {
      position: fixed;
      width: 100%;
      top: 0;
      left: 0;
      background: rgba(0, 0, 0, 0.6);
      backdrop-filter: blur(10px);
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 15px 30px;
      z-index: 100;
    }

    header h1 {
      font-size: 20px;
      color: #ff6600;
      font-weight: 700;
    }

    nav {
      display: flex;
      gap: 20px;
    }

    nav a {
      color: #fff;
      text-decoration: none;
      font-weight: 600;
      transition: 0.3s;
    }

    nav a:hover {
      color: #ff6600;
    }

    /* ------------------------------ HERO ------------------------------ */
    .hero {
      height: 100vh;
      background: url('IMG_1703.jpeg') center/cover no-repeat;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      text-align: center;
      padding: 20px;
    }

    .hero h2 {
      font-size: 64px;
      color: #ff6600;
      margin-bottom: 15px;
      font-weight: 900;
      text-transform: uppercase;
      text-shadow: 0 5px 20px rgba(0, 0, 0, 0.6);
    }

    .hero p {
      font-size: 18px;
      max-width: 650px;
      color: #ddd;
      margin-bottom: 30px;
      line-height: 1.6;
    }

    .btn {
      background: linear-gradient(90deg, #ff6600, #ff3300);
      color: #fff;
      padding: 14px 34px;
      border: none;
      border-radius: 8px;
      font-weight: bold;
      cursor: pointer;
      transition: 0.3s ease;
      box-shadow: 0 6px 20px rgba(255, 102, 0, 0.3);
    }

    .btn:hover {
      transform: scale(1.08);
      box-shadow: 0 10px 30px rgba(255, 102, 0, 0.4);
    }

    /* ------------------------------ ABOUT ------------------------------ */
    .about {
      padding: 120px 20px;
      background: #0a0a0a;
      text-align: center;
    }

    .about h2 {
      color: #ff6600;
      font-size: 40px;
      margin-bottom: 25px;
      font-weight: 800;
    }

    .about p {
      color: #ccc;
      line-height: 1.6;
      max-width: 800px;
      margin: 0 auto;
      font-size: 16px;
    }

    /* ------------------------------ GALLERY ------------------------------ */
    .gallery {
      background: #111;
      padding: 100px 20px;
      text-align: center;
    }

    .gallery h2 {
      color: #ff6600;
      font-size: 38px;
      margin-bottom: 30px;
      font-weight: 700;
    }

    .gallery-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
      gap: 20px;
      max-width: 1100px;
      margin: 0 auto;
    }

    .gallery-grid img {
      width: 100%;
      border-radius: 12px;
      transition: transform 0.3s ease, box-shadow 0.3s ease;
    }

    .gallery-grid img:hover {
      transform: scale(1.05);
      box-shadow: 0 10px 40px rgba(255, 102, 0, 0.3);
    }

    /* ------------------------------ TOURNAMENT ------------------------------ */
    .tournament {
      background: #0a0a0a;
      padding: 100px 20px;
      text-align: center;
    }

    .tournament h2 {
      color: #ff6600;
      font-size: 38px;
      margin-bottom: 20px;
      font-weight: 700;
    }

    .tournament .info {
      color: #ccc;
      margin-bottom: 30px;
      font-size: 16px;
    }

    form {
      display: flex;
      flex-direction: column;
      gap: 15px;
      max-width: 500px;
      margin: 0 auto;
    }

    input,
    textarea {
      padding: 14px;
      border: none;
      border-radius: 8px;
      outline: none;
      font-size: 15px;
      background: #1a1a1a;
      color: #fff;
      transition: border 0.3s ease;
    }

    input:focus,
    textarea:focus {
      border: 1px solid #ff6600;
    }

    .submit-btn {
      background: linear-gradient(90deg, #ff6600, #ff3300);
      color: #fff;
      padding: 14px;
      border: none;
      border-radius: 8px;
      font-weight: bold;
      cursor: pointer;
      transition: 0.3s ease;
      box-shadow: 0 6px 20px rgba(255, 102, 0, 0.3);
    }

    .submit-btn:hover {
      transform: scale(1.05);
      box-shadow: 0 10px 30px rgba(255, 102, 0, 0.4);
    }

    /* ------------------------------ VIDEO SECTION ------------------------------ */
    .video-section {
      background: #111;
      padding: 100px 20px;
      text-align: center;
    }

    .video-section h2 {
      color: #ff6600;
      font-size: 38px;
      margin-bottom: 30px;
      font-weight: 700;
    }

    .video-section iframe {
      width: 100%;
      max-width: 720px;
      height: 405px;
      border-radius: 10px;
      border: none;
      box-shadow: 0 10px 40px rgba(0, 0, 0, 0.5);
    }

    /* ------------------------------ FOOTER ------------------------------ */
    footer {
      background: #000;
      text-align: center;
      padding: 30px 20px;
      color: #777;
      font-size: 15px;
      border-top: 1px solid #111;
    }

    /* ------------------------------ WHATSAPP BUTTON ------------------------------ */
    .whatsapp-btn {
      position: fixed;
      bottom: 20px;
      right: 20px;
      background: #25D366;
      color: #fff;
      border-radius: 50%;
      width: 60px;
      height: 60px;
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 30px;
      text-decoration: none;
      box-shadow: 0 6px 20px rgba(37, 211, 102, 0.4);
      transition: 0.3s;
      z-index: 999;
    }

    .whatsapp-btn:hover {
      transform: scale(1.1);
      background: #1ebe5d;
    }

    /* ------------------------------ RESPONSIVE ------------------------------ */
    @media (max-width: 768px) {
      header {
        flex-direction: column;
        gap: 10px;
      }

      .hero h2 {
        font-size: 42px;
      }

      .hero p {
        font-size: 16px;
      }
    }

  </style>
</head>

<body>

  <!-- HEADER -->
  <header>
    <h1>YourGoatViper — Official</h1>
    <nav>
      <a href="#about">About</a>
      <a href="#gallery">Gallery</a>
      <a href="#tournament">Tournament</a>
      <a href="#videos">Videos</a>
    </nav>
  </header>

  <!-- HERO SECTION -->
  <section class="hero">
    <h2>Welcome to YourGoatViper</h2>
    <p>The official gaming hub of Viper — tournaments, highlights, and everything esports!</p>
    <button class="btn" onclick="document.getElementById('tournament').scrollIntoView({behavior: 'smooth'})">
      Join Tournament
    </button>
  </section>

  <!-- ABOUT SECTION -->
  <section id="about" class="about">
    <h2>About Me</h2>
    <p>
      I’m <strong>YourGoatViper</strong> — a passionate gamer, content creator, and tournament host.
      My mission is to bring gamers together from around the world to compete, grow, and showcase their talent.
      Whether you’re a beginner or a pro, this is your space to shine.
    </p>
  </section>

  <!-- GALLERY SECTION -->
  <section id="gallery" class="gallery">
    <h2>Gallery</h2>
    <div class="gallery-grid">
      <img src="https://via.placeholder.com/300x200?text=Game+1" alt="Gallery image 1">
      <img src="https://via.placeholder.com/300x200?text=Game+2" alt="Gallery image 2">
      <img src="https://via.placeholder.com/300x200?text=Game+3" alt="Gallery image 3">
      <img src="https://via.placeholder.com/300x200?text=Game+4" alt="Gallery image 4">
    </div>
  </section>

  <!-- TOURNAMENT SECTION -->
  <section id="tournament" class="tournament">
    <h2>Join the Tournament</h2>
    <p class="info">Register now and compete for prizes and glory!</p>
    <form onsubmit="alert('Your registration has been submitted!'); return false;">
      <input type="text" placeholder="Your Name" required />
      <input type="email" placeholder="Your Email" required />
      <input type="text" placeholder="Game ID" required />
      <textarea placeholder="Your Message (optional)" rows="4"></textarea>
      <button type="submit" class="submit-btn">Register</button>
    </form>
  </section>

  <!-- VIDEO SECTION -->
  <section id="videos" class="video-section">
    <h2>Featured Video</h2>
    <iframe
      src="https://www.youtube.com/embed/dQw4w9WgXcQ"
      title="Featured Video"
      allowfullscreen>
    </iframe>
  </section>

  <!-- FOOTER -->
  <footer>
    <p>© 2025 YourGoatViper. All rights reserved.</p>
  </footer>

  <!-- WHATSAPP BUTTON -->
  <a class="whatsapp-btn" href="https://wa.me/923348666640" target="_blank" title="Chat on WhatsApp">
    💬
  </a>

</body>
</html>
