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

/* ------------------------------ ANIMATIONS ------------------------------ */
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(40px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.hero h2,
.hero p,
.btn {
  animation: fadeInUp 1s ease forwards;
}

/* ------------------------------ RESPONSIVE ------------------------------ */
@media (max-width: 1024px) {
  .hero h2 {
    font-size: 52px;
  }

  .gallery-grid {
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  }
}

@media (max-width: 768px) {
  header {
    flex-direction: column;
    gap: 10px;
  }

  .hero {
    padding: 60px 20px;
  }

  .hero h2 {
    font-size: 42px;
  }

  .hero p {
    font-size: 16px;
  }

  .about h2,
  .gallery h2,
  .tournament h2,
  .video-section h2 {
    font-size: 32px;
  }
}

@media (max-width: 480px) {
  nav {
    flex-wrap: wrap;
    justify-content: center;
    gap: 10px;
  }

  .hero h2 {
    font-size: 34px;
  }

  .hero p {
    font-size: 14px;
  }

  .btn {
    padding: 10px 24px;
  }

  .gallery-grid {
    grid-template-columns: 1fr;
  }

  input,
  textarea {
    font-size: 14px;
  }
}
