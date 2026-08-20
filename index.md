---
layout: default
---

<style>
  /* Layout Structure */
  .portfolio-wrapper {
    position: relative;
    max-width: 1100px;
    margin: 0 auto;
    padding-bottom: 50px;
  }

  /* Minimalist Language Toggle (Top Right) */
  .lang-toggle-container {
    position: absolute;
    top: 10px;
    right: 0;
    font-family: monospace, sans-serif;
    font-size: 0.95em;
    z-index: 10;
  }
  .lang-btn {
    background: transparent;
    border: none;
    color: #999;
    cursor: pointer;
    padding: 0 4px;
    font-size: 1em;
    transition: color 0.2s;
  }
  .lang-btn:hover { color: #555; }
  .lang-btn.active {
    color: #000;
    font-weight: bold;
    text-decoration: underline;
  }

  /* Top Section: Two-Column Grid */
  .top-section {
    display: flex;
    gap: 50px;
    padding-top: 40px; /* Space for the toggle */
    margin-bottom: 30px;
  }
  
  /* Left Sidebar */
  .sidebar {
    flex: 0 0 240px;
  }
  .sidebar h2 { 
    margin-top: 0; 
    font-size: 1.5em;
    margin-bottom: 15px;
  }
  .profile-pic {
    width: 100%;
    max-width: 240px;
    border-radius: 4px; 
    display: block;
    margin-bottom: 20px;
    object-fit: cover;
  }
  .sidebar hr {
    margin: 20px 0;
    border: 0;
    border-top: 1px solid #ddd;
  }
  .sidebar-links {
    list-style-type: none;
    padding: 0;
    margin: 0;
    font-size: 0.95em;
  }
  .sidebar-links li {
    margin-bottom: 12px;
  }
  
  /* Right Content (About Me) */
  .about-content {
    flex: 1;
    min-width: 300px;
  }
  .about-content h2 {
    margin-top: 0;
  }

  /* Full Width Section */
  .full-width-section {
    width: 100%;
  }
  hr.section-divider {
    border: 0;
    border-top: 1px solid #eee;
    margin: 40px 0;
  }

  /* Skills Stars */
  .skills-container { margin-bottom: 40px; }
  .skill-category { margin-top: 25px; font-weight: bold; border-bottom: 1px solid #333; padding-bottom: 5px; margin-bottom: 10px; }
  .skill-row {
    display: flex;
    justify-content: space-between;
    padding: 8px 10px;
    margin: 0 -10px;
    border-bottom: 1px solid #eee;
    transition: background-color 0.3s;
    font-size: 0.95em;
  }
  .skill-row:hover { background-color: #f9f9f9; }
  .skill-name { color: #333; }
  .skill-stars { color: #ddd; letter-spacing: 2px; }
  .skill-stars .filled { color: #888; transition: color 0.3s; }
  .skill-row:hover .skill-stars .filled { color: #f39c12; }
  
  /* Tables */
  table { width: 100%; border-collapse: collapse; margin-bottom: 30px; font-size: 0.95em; }
  th, td { border: 1px solid #eee; padding: 10px; text-align: left; vertical-align: top; }
  th { background-color: #fafafa; font-weight: normal; color: #555; }
  
  /* Responsive */
  @media (max-width: 768px) {
    .top-section { flex-direction: column; gap: 30px; }
    .sidebar { flex: 1 1 auto; }
    .lang-toggle-container { position: relative; text-align: right; margin-bottom: 20px; top: 0; }
  }
</style>

<script>
  function setLanguage(lang) {
    // Toggle content visibility (using block instead of flex now)
    document.getElementById('lang-en').style.display = lang === 'en' ? 'block' : 'none';
    document.getElementById('lang-fr').style.display = lang === 'fr' ? 'block' : 'none';
    
    // Toggle button active states
    document.getElementById('btn-en').className = lang === 'en' ? 'lang-btn active' : 'lang-btn';
    document.getElementById('btn-fr').className = lang === 'fr' ? 'lang-btn active' : 'lang-btn';
  }
</script>

<div class="portfolio-wrapper">
  
  <!-- Minimalist Language Toggle -->
  <div class="lang-toggle-container">
    <button id="btn-en" class="lang-btn active" onclick="setLanguage('en')">EN</button> | 
    <button id="btn-fr" class="lang-btn" onclick="setLanguage('fr')">FR</button>
  </div>

  <!-- ================= ENGLISH SECTION ================= -->
  <div id="lang-en">
    
    <!-- Top Section: Two Columns -->
    <div class="top-section">
      <aside class="sidebar">
        <h2>Nicolas Cozzarin</h2>
        <img src="docs/assets/ppicture.jpeg" alt="Nicolas Cozzarin" class="profile-pic">
        <hr>
        <ul class="sidebar-links">
          <li><a href="#" target="_blank">Find me on LinkedIn</a></li>
          <li><a href="#" target="_blank">Download my CV</a></li>
          <li><a href="#" target="_blank">Follow me on Twitter</a></li>
          <li><a href="#" target="_blank">Check out my GitHub profile</a></li>
          <li><a href="mailto:nicolasjcozzarin@gmail.com">E-mail me at nicolasjcozzarin@gmail.com</a></li>
        </ul>
      </aside>

      <div class="about-content">
        <h2 id="about-me">about me</h2>
        <p>I am an IT Project Manager and Product Owner with 10 years of experience. I specialize in Agile methodologies (Scrum/Kanban) and Software Development Life Cycle (SDLC) management. My technical focus is on AI and Data, allowing me to translate user needs into practical, effective technical solutions.</p>
        <p>Currently, I am completing a BSc in Artificial Intelligence & Robotics at Universidad Siglo XXI, focusing on machine learning and generative AI.</p>
      </div>
    </div>

    <!-- Bottom Section: Full Width -->
    <div class="full-width-section">
      <hr class="section-divider">

      <h2 id="things-i-am-doing">things I am doing at the moment</h2>
      <ul>
        <li>I am an <strong>AI Product Owner</strong> for the Security Forces Disciplinary Control System in Cordoba, Argentina, managing an NLP model for text classification and implementing data anonymization protocols.</li>
        <li>Finishing my <strong>BSc in Artificial Intelligence & Robotics</strong>.</li>
      </ul>
      
      <hr class="section-divider">

      <h2 id="things-i-have-done">links to things I have done in the past</h2>
      <ul>
        <li>Managed full SDLC for crypto exchange platforms as a <strong>Product Owner / IT Project Manager</strong> at Union of Financial Corners (Geneva), increasing development team velocity by 20%.</li>
        <li>Translated business needs into functional specifications as a <strong>Functional Analyst</strong> at FlyDevs (USA).</li>
        <li>Optimized delivery processes and led test strategies as a <strong>QA Lead</strong> at Charly Inc (Canada).</li>
        <li>Developed ERP modules in Python as a <strong>Backend Developer</strong> at E-MIPS (Buenos Aires).</li>
      </ul>
      
      <hr class="section-divider">

      <h2 id="updates">updates</h2>
      <table>
        <thead>
          <tr><th>date</th><th>news</th></tr>
        </thead>
        <tbody>
          <tr><td>11/2025</td><td>Started AI Product Owner role for Security Forces in Cordoba, Argentina</td></tr>
          <tr><td>10/2022</td><td>Started as Product Owner/IT Project Manager at Union of Financial Corners, Geneva</td></tr>
          <tr><td>02/2019</td><td>Began working as a Functional Analyst for FlyDevs</td></tr>
          <tr><td>2017</td><td>Took on the QA Lead role at Charly Inc</td></tr>
          <tr><td>02/2015</td><td>Started my tech career as a Backend Python Developer at E-MIPS</td></tr>
        </tbody>
      </table>
      
      <hr class="section-divider">

      <h2 id="skills">skills</h2>
      <div class="skills-container">
        <div class="skill-category">Tech, Data & AI</div>
        <div class="skill-row"><span class="skill-name">Python (Pandas, Scikit-learn), PyTorch</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
        <div class="skill-row"><span class="skill-name">NLP, NER</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
        <div class="skill-row"><span class="skill-name">SQL, React.js, TypeScript</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
        <div class="skill-row"><span class="skill-name">Git, Docker, CI/CD, REST APIs</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>

        <div class="skill-category">Product & Management</div>
        <div class="skill-row"><span class="skill-name">Agile (Scrum/Kanban), SDLC</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
        <div class="skill-row"><span class="skill-name">Backlog Management, User Stories</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
        <div class="skill-row"><span class="skill-name">Jira, Confluence, Azure DevOps</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
        <div class="skill-row"><span class="skill-name">Figma, Miro, Balsamiq</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
        
        <div class="skill-category">Languages</div>
        <div class="skill-row"><span class="skill-name">Spanish (Native)</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
        <div class="skill-row"><span class="skill-name">English (C1)</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
        <div class="skill-row"><span class="skill-name">French (C1)</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
        <div class="skill-row"><span class="skill-name">German (B2)</span> <span class="skill-stars"><span class="filled">★★★</span>★★</span></div>
      </div>
      
      <hr class="section-divider">
      
      <h2>projects & insights</h2>
      <ul class="post-list">
        {%- for post in site.posts -%}
        <li>
          <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>
          <h3>
            <a class="post-link" href="{{ post.url | relative_url }}">
              {{ post.title | escape }}
            </a>
          </h3>
        </li>
        {%- endfor -%}
      </ul>
    </div>
  </div>

  <!-- ================= FRENCH SECTION ================= -->
  <div id="lang-fr" style="display:none;">
    
    <!-- Top Section: Two Columns -->
    <div class="top-section">
      <aside class="sidebar">
        <h2>Nicolas Cozzarin</h2>
        <img src="docs/assets/ppicture.jpeg" alt="Nicolas Cozzarin" class="profile-pic">
        <hr>
        <ul class="sidebar-links">
          <li><a href="#" target="_blank">Me retrouver sur LinkedIn</a></li>
          <li><a href="#" target="_blank">Télécharger mon CV</a></li>
          <li><a href="#" target="_blank">Me suivre sur Twitter</a></li>
          <li><a href="#" target="_blank">Découvrir mon profil GitHub</a></li>
          <li><a href="mailto:nicolasjcozzarin@gmail.com">M'envoyer un e-mail à nicolasjcozzarin@gmail.com</a></li>
        </ul>
      </aside>

      <div class="about-content">
        <h2 id="a-propos">à propos</h2>
        <p>Product Owner et Chef de Projet IT avec 10 ans d'expérience. Je suis spécialiste des méthodologies Agiles (Scrum/Kanban) et du pilotage SDLC. Fort d'une spécialisation en IA et Data, je traduis les besoins utilisateurs en solutions techniques concrètes et performantes.</p>
        <p>Je termine actuellement un Bachelor en Intelligence Artificielle et Robotique à l'Universidad Siglo XXI, avec un accent sur le machine learning et l'IA générative.</p>
      </div>
    </div>

    <!-- Bottom Section: Full Width -->
    <div class="full-width-section">
      <hr class="section-divider">

      <h2 id="en-ce-moment">ce que je fais en ce moment</h2>
      <ul>
        <li>Je suis <strong>AI Product Owner</strong> pour le Système de Contrôle Disciplinaire des Forces de Sécurité à Cordoba, Argentine, où je gère un modèle NLP pour l'automatisation de l'analyse de dossiers légaux.</li>
        <li>Je finalise mon <strong>Bachelor en Intelligence Artificielle et Robotique</strong>.</li>
      </ul>
      
      <hr class="section-divider">

      <h2 id="experiences-passees">liens vers mes expériences passées</h2>
      <ul>
        <li>Pilotage SDLC complet pour des plateformes d'échange crypto en tant que <strong>Product Owner / IT Project Manager</strong> chez Union of Financial Corners (Genève).</li>
        <li>Traduction des besoins commerciaux en spécifications en tant qu'<strong>Analyste fonctionnel</strong> chez FlyDevs (USA).</li>
        <li>Définition des stratégies de tests pour des équipes distantes en tant que <strong>QA Lead</strong> chez Charly Inc (Canada).</li>
        <li>Développement de modules ERP en Python en tant que <strong>Développeur Backend</strong> chez E-MIPS (Buenos Aires).</li>
      </ul>
      
      <hr class="section-divider">

      <h2 id="mises-a-jour">mises à jour</h2>
      <table>
        <thead>
          <tr><th>date</th><th>nouvelle</th></tr>
        </thead>
        <tbody>
          <tr><td>11/2025</td><td>Début de ma mission d'AI Product Owner pour les Forces de Sécurité de Cordoba</td></tr>
          <tr><td>10/2022</td><td>Arrivée chez Union of Financial Corners à Genève en tant que Product Owner</td></tr>
          <tr><td>02/2019</td><td>Début en tant qu'Analyste fonctionnel pour FlyDevs</td></tr>
          <tr><td>2017</td><td>Prise de poste en tant que QA Lead chez Charly Inc</td></tr>
          <tr><td>02/2015</td><td>Début de carrière technique comme Développeur Backend Python chez E-MIPS</td></tr>
        </tbody>
      </table>
      
      <hr class="section-divider">

      <h2 id="competences">compétences</h2>
      <div class="skills-container">
        <div class="skill-category">Tech, Data & IA</div>
        <div class="skill-row"><span class="skill-name">Python (Pandas, Scikit-learn), PyTorch</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
        <div class="skill-row"><span class="skill-name">NLP, NER</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
        <div class="skill-row"><span class="skill-name">SQL, React.js, TypeScript</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
        <div class="skill-row"><span class="skill-name">Git, Docker, CI/CD, API REST</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>

        <div class="skill-category">Produit & Management</div>
        <div class="skill-row"><span class="skill-name">Agile (Scrum/Kanban), SDLC</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
        <div class="skill-row"><span class="skill-name">Backlog Management, User Stories</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
        <div class="skill-row"><span class="skill-name">Jira, Confluence, Azure DevOps</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
        <div class="skill-row"><span class="skill-name">Figma, Miro, Balsamiq</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
        
        <div class="skill-category">Langues</div>
        <div class="skill-row"><span class="skill-name">Espagnol (Natif)</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
        <div class="skill-row"><span class="skill-name">Anglais (C1)</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
        <div class="skill-row"><span class="skill-name">Français (C1)</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
        <div class="skill-row"><span class="skill-name">Allemand (B2)</span> <span class="skill-stars"><span class="filled">★★★</span>★★</span></div>
      </div>
      
      <hr class="section-divider">

      <h2>projets & réflexions</h2>
      <ul class="post-list">
        {%- for post in site.posts -%}
        <li>
          <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>
          <h3>
            <a class="post-link" href="{{ post.url | relative_url }}">
              {{ post.title | escape }}
            </a>
          </h3>
        </li>
        {%- endfor -%}
      </ul>
    </div>
  </div>
</div>
