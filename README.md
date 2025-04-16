<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <title>Paranoico Site</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="preload" href="https://fonts.googleapis.com/css2?family=Orbitron:wght@700&family=Roboto+Mono:wght@500;700&display=swap" as="style">
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@700&family=Roboto+Mono:wght@500;700&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" crossorigin="anonymous">
  <style>
    :root {
      --primary-color: #0f0f0f;
      --secondary-color: #1a1a1a;
      --accent-color: #ff007f;
      --accent-hover: #ff4d94;
      --light-color: #ffffff;
      --text-color: #e0e0e0;
      --shadow-color: rgba(0, 0, 0, 0.7);
      --border-radius: 20px;
      --transition-speed: 0.3s;
      --gradient-start: #ff007f;
      --gradient-end: #ff4d94;
    }
    * { margin: 0; padding: 0; box-sizing: border-box; }
    html { scroll-behavior: smooth; }
    body {
      background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
      font-family: 'Roboto Mono', monospace;
      color: var(--text-color);
      min-height: 100vh;
      overflow-x: hidden;
      position: relative;
      padding: 30px 10px;
    }
    .container { width: 100%; max-width: 1400px; margin: 0 auto; }
    header {
      text-align: center;
      padding: 80px 30px;
      background: var(--secondary-color);
      border-radius: var(--border-radius);
      box-shadow: 0 10px 40px var(--shadow-color);
      margin-bottom: 60px;
      position: relative;
      overflow: hidden;
      animation: neonBorder 3s ease-in-out infinite;
    }
    @keyframes neonBorder {
      0%,100% { box-shadow: 0 0 20px var(--accent-color); }
      50% { box-shadow: 0 0 40px var(--accent-hover); }
    }
    header h1 {
      font-family: 'Orbitron', sans-serif;
      font-size: 80px;
      color: var(--light-color);
      text-shadow: 0 0 30px var(--accent-color);
      margin-bottom: 30px;
      opacity: 0;
      animation: fadeInUp 1s 0.5s forwards;
    }
    header p {
      font-size: 28px;
      color: #ccc;
      max-width: 800px;
      margin: 0 auto 50px auto;
      opacity: 0;
      animation: fadeInUp 1s 1s forwards;
    }
    nav {
      display: flex;
      justify-content: center;
      gap: 30px;
      opacity: 0;
      animation: fadeInUp 1s 1.5s forwards;
    }
    nav a {
      font-size: 22px;
      text-decoration: none;
      color: var(--light-color);
      transition: var(--transition-speed);
      position: relative;
    }
    nav a::after {
      content: '';
      position: absolute;
      bottom: -5px; left: 0;
      width: 0; height: 2px;
      background: var(--accent-color);
      transition: var(--transition-speed);
    }
    nav a:hover::after { width: 100%; }
    section {
      margin-bottom: 80px;
      opacity: 0;
      transform: translateY(20px);
    }
    section.visible { opacity: 1; transform: translateY(0); transition: opacity 0.8s ease-out, transform 0.8s ease-out; }
    section h2 {
      font-family: 'Orbitron', sans-serif;
      font-size: 56px;
      text-align: center;
      margin-bottom: 50px;
      text-shadow: 0 0 15px var(--accent-color);
    }
    .card-container {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 50px;
    }
    .card {
      background: var(--secondary-color);
      border-radius: var(--border-radius);
      padding: 50px;
      max-width: 450px;
      width: 100%;
      text-align: center;
      box-shadow: 0 8px 25px var(--shadow-color);
      transition: transform var(--transition-speed), box-shadow var(--transition-speed);
      position: relative;
      overflow: hidden;
    }
    .card::before {
      content: '';
      position: absolute;
      top: -50%; left: -50%;
      width: 200%; height: 200%;
      background: conic-gradient(from 0deg, var(--gradient-start), var(--gradient-end));
      animation: rotate 4s linear infinite;
      z-index: 0;
      opacity: 0.2;
    }
    @keyframes rotate { to { transform: rotate(360deg); } }
    .card:hover { transform: translateY(-10px); box-shadow: 0 10px 30px var(--accent-color); }
    .card img {
      width: 100%;
      border-radius: 12px;
      margin-bottom: 25px;
      display: block;
      loading: lazy;
      position: relative;
      z-index: 1;
    }
    .card h3 {
      font-size: 32px;
      margin-bottom: 15px;
      color: var(--light-color);
      position: relative;
      z-index: 1;
    }
    .card p {
      font-size: 20px;
      color: #bbb;
      position: relative;
      z-index: 1;
    }
    .btn {
      display: inline-block;
      margin-top: 30px;
      padding: 18px 40px;
      font-size: 20px;
      border: none;
      border-radius: 40px;
      background: linear-gradient(45deg, var(--gradient-start), var(--gradient-end));
      color: var(--primary-color);
      cursor: pointer;
      transition: var(--transition-speed);
      text-decoration: none;
      position: relative;
      z-index: 1;
    }
    .btn:hover { transform: scale(1.07); box-shadow: 0 0 20px var(--accent-color); }
    footer {
      text-align: center;
      font-size: 18px;
      color: #aaa;
      padding: 40px 20px;
    }
    footer i {
      margin: 0 10px;
      color: var(--accent-color);
      transition: var(--transition-speed);
      font-size: 28px;
    }
    footer i:hover { color: var(--accent-hover); transform: scale(1.2); }
    @media (max-width: 768px) {
      header h1 { font-size: 60px; }
      header p { font-size: 22px; }
      section h2 { font-size: 42px; }
      .btn { font-size: 18px; padding: 15px 30px; }
      nav { display: none; }
      .menu-toggle { display: block; position: absolute; top: 30px; right: 30px; font-size: 28px; color: var(--light-color); cursor: pointer; }
      nav.mobile { display: flex; flex-direction: column; gap: 20px; background: var(--secondary-color); position: absolute; top: 70px; right: 30px; padding: 20px; border-radius: var(--border-radius); box-shadow: 0 8px 25px var(--shadow-color); }
    }
    @keyframes fadeInUp { to { opacity: 1; transform: translateY(0); } }

    /* Modal Style */
    #modal {
      position: fixed;
      top: 0; left: 0;
      width: 100vw; height: 100vh;
      background: rgba(0, 0, 0, 0.8);
      display: none;
      align-items: center;
      justify-content: center;
      z-index: 1000;
    }
    .modal-content {
      background: var(--secondary-color);
      padding: 40px;
      border-radius: var(--border-radius);
      box-shadow: 0 0 30px var(--accent-color);
      text-align: center;
      max-width: 400px;
      width: 90%;
      color: var(--text-color);
      position: relative;
    }
    .modal-content .close {
      position: absolute;
      top: 15px; right: 20px;
      font-size: 28px;
      cursor: pointer;
      color: var(--accent-color);
    }
  </style>
</head>
<body>
  <div class="container">
    <header>
      <div class="menu-toggle" aria-label="Abrir menu"><i class="fas fa-bars"></i></div>
      <h1>Bem-vindo ao Paranoico</h1>
      <p>Seu destino para uma experiência épica no GTA SAMP e MTA</p>
      <nav role="navigation">
        <a href="#produtos">Produtos</a>
        <a href="#planos">Planos</a>
      </nav>
    </header>

    <section id="produtos">
      <h2>Produtos</h2>
      <div class="card-container">
  <div class="card">
    <img src="https://media.moddb.com/images/downloads/1/47/46326/mtasa.png" alt="MTA" loading="lazy">
    <h3>MTA</h3>
    <p>Bypass real é com os Paranoicos no MTA.</p>
    <a href="#" class="btn" role="button">Saiba Mais</a>
  </div>
  <div class="card">
    <img src="https://cdn2.steamgriddb.com/icon/cfd66e741860718ddecf1f6eabd05fc6.ico" alt="SAMP" loading="lazy">
    <h3>SAMP</h3>
    <p>Bypass real é com os Paranoicos no SAMP.</p>
    <a href="#" class="btn" role="button">Saiba Mais</a>
  </div>
  <div class="card">
    <img src="https://upload.wikimedia.org/wikipedia/commons/9/9a/FiveM_Logo.png" alt="FiveM" loading="lazy">
    <h3>FiveM</h3>
    <p>BY PARA OS FIVEMZUDO TBM PORRA.</p>
    <a href="#" class="btn" role="button">Saiba Mais</a>
  </div>
</div>
    </section>

    <section id="planos">
      <h2>Planos</h2>
      <div class="card-container">
        <div class="card">
          <h3>Plano Básico</h3>
          <p>É mais simples e não muito recomendado.</p>
          <p><strong>Preço:</strong> R$ 25</p>
          <a href="https://discord.gg/paranoicosbypass" target="_blank" class="btn">Em breve</a>
        </div>
        <div class="card">
          <h3>Plano Avançado</h3>
          <p>Métodos Exclusivos o bypass.</p>
          <p><strong>Preço:</strong> R$ 295</p>
          <a href="https://discord.gg/paranoicosbypass" target="_blank" class="btn">Em breve</a>
        </div>
      </div>
    </section>

    <footer>
      <p>© 2025 Paranoico. Todos os direitos reservados.</p>
      
      
      
      <p>
        <a href="#" aria-label="WhatsApp"><i class="fab fa-whatsapp"></i></a>
        <a href="#" aria-label="Instagram"><i class="fab fa-instagram"></i></a>
        <a href="https://discord.gg/paranoicos" target="_blank" aria-label="Discord"><i class="fab fa-discord"></i></a>
      </p>
    </footer>
  </div>

  <!-- Modal -->
  <div id="modal">
    <div class="modal-content">
      <span class="close">&times;</span>
      <h3>Segura aí...</h3>
      <p>Em breve você vai dar bypass, calma!</p>
    </div>
  </div>

  <script>
    const sections = document.querySelectorAll('section');
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) entry.target.classList.add('visible');
      });
    }, { threshold: 0.2 });
    sections.forEach(sec => observer.observe(sec));

    const toggle = document.querySelector('.menu-toggle');
    const nav = document.querySelector('nav');
    toggle.addEventListener('click', () => nav.classList.toggle('mobile'));

    // Modal logic
    const modal = document.getElementById('modal');
    const closeBtn = modal.querySelector('.close');
    const infoBtns = document.querySelectorAll('.btn[href="#"]');

    infoBtns.forEach(btn => {
      btn.addEventListener('click', e => {
        e.preventDefault();
        modal.style.display = 'flex';
      });
    });

    closeBtn.addEventListener('click', () => {
      modal.style.display = 'none';
    });

    window.addEventListener('click', e => {
      if (e.target === modal) modal.style.display = 'none';
    });
  </script>
</body>
</html>
