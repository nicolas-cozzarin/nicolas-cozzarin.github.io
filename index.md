---
layout: default
---

<style>
  /* Toggle Button Styles */
  .lang-toggle {
    background-color: #333;
    color: #fff;
    border: none;
    padding: 8px 16px;
    cursor: pointer;
    border-radius: 4px;
    font-size: 0.9em;
    margin-bottom: 20px;
    transition: background-color 0.2s;
  }
  .lang-toggle:hover { background-color: #555; }

  /* Profile Image Styles */
  .profile-pic {
    float: right;
    width: 150px;
    height: 150px;
    border-radius: 50%;
    object-fit: cover;
    margin-left: 20px;
    margin-bottom: 20px;
  }

  /* Skills Stars (Pascal van Gemert style) */
  .skills-container { margin-bottom: 40px; }
  .skill-category { margin-top: 20px; font-weight: bold; }
  .skill-row {
    display: flex;
    justify-content: space-between;
    padding: 8px 10px;
    border-bottom: 1px solid #eee;
    transition: background-color 0.3s;
    font-size: 0.95em;
  }
  .skill-row:hover { background-color: #f4f4f4; }
  .skill-name { color: #333; }
  
  /* Star colors: grey by default, highlight on row hover */
  .skill-stars { color: #ddd; letter-spacing: 2px; }
  .skill-stars .filled { color: #888; transition: color 0.3s; }
  .skill-row:hover .skill-stars .filled { color: #f39c12; /* highlights to gold/orange on hover */ }
  
  /* Clean up floats */
  .clearfix::after { content: ""; clear: both; display: table; }
  
  /* Table styling similar to Amanda's */
  table { width: 100%; border-collapse: collapse; margin-bottom: 30px; }
  th, td { border: 1px solid #ddd; padding: 8px; text-align: left; }
  th { background-color: #f9f9f9; }
</style>

<script>
  function toggleLanguage() {
    var enContent = document.getElementById("lang-en");
    var frContent = document.getElementById("lang-fr");
    if (enContent.style.display === "none") {
      enContent.style.display = "block";
      frContent.style.display = "none";
    } else {
      enContent.style.display = "none";
      frContent.style.display = "block";
    }
  }
</script>

<button class="lang-toggle" onclick="toggleLanguage()">Français / English</button>

<!-- ================= ENGLISH SECTION ================= -->
<div id="lang-en" class="clearfix">
  <img src="https://via.placeholder.com/150" alt="Nicolas Jose Cozzarin" class="profile-pic">
  
  <h2 id="about-me">about me</h2>
  <p>I am an IT Project Manager and Product Owner with 10 years of experience. I specialize in Agile methodologies (Scrum/Kanban) and Software Development Life Cycle (SDLC) management. My technical focus is on AI and Data, allowing me to translate user needs into practical, effective technical solutions.</p>
  <p>Currently, I am completing a BSc in Artificial Intelligence & Robotics at Universidad Siglo XXI, focusing on machine learning and generative AI.</p>
  <hr>

  <h2 id="things-i-am-doing">things I am doing at the moment</h2>
  <ul>
    <li>I am an <strong>AI Product Owner</strong> for the Security Forces Disciplinary Control System in Cordoba, Argentina, managing an NLP model for text classification and implementing data anonymization protocols.</li>
    <li>Finishing my <strong>BSc in Artificial Intelligence & Robotics</strong>.</li>
  </ul>
  <hr>

  <h2 id="things-i-have-done">links to things I have done in the past</h2>
  <ul>
    <li>Managed full SDLC for crypto exchange platforms as a <strong>Product Owner / IT Project Manager</strong> at Union of Financial Corners (Geneva), increasing development team velocity by 20%.</li>
    <li>Translated business needs into functional specifications as a <strong>Functional Analyst</strong> at FlyDevs (USA).</li>
    <li>Optimized delivery processes and led test strategies as a <strong>QA Lead</strong> at Charly Inc (Canada).</li>
    <li>Developed ERP modules in Python as a <strong>Backend Developer</strong> at E-MIPS (Buenos Aires).</li>
  </ul>
  <hr>

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
  <hr>

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
  <hr>
  
  <h2>projects & insights</h2>
  <p>Here is a collection of my latest projects, ideas, and posts.</p>
</div>


<!-- ================= FRENCH SECTION ================= -->
<div id="lang-fr" class="clearfix" style="display:none;">
  <img src="https://via.placeholder.com/150" alt="Nicolas Jose Cozzarin" class="profile-pic">
  
  <h2 id="a-propos">à propos</h2>
  <p>Product Owner et Chef de Projet IT avec 10 ans d'expérience. Je suis spécialiste des méthodologies Agiles (Scrum/Kanban) et du pilotage SDLC. Fort d'une spécialisation en IA et Data, je traduis les besoins utilisateurs en solutions techniques concrètes et performantes.</p>
  <p>Je termine actuellement un Bachelor en Intelligence Artificielle et Robotique à l'Universidad Siglo XXI, avec un accent sur le machine learning et l'IA générative.</p>
  <hr>

  <h2 id="en-ce-moment">ce que je fais en ce moment</h2>
  <ul>
    <li>Je suis <strong>AI Product Owner</strong> pour le Système de Contrôle Disciplinaire des Forces de Sécurité à Cordoba, Argentine, où je gère un modèle NLP pour l'automatisation de l'analyse de dossiers légaux.</li>
    <li>Je finalise mon <strong>Bachelor en Intelligence Artificielle et Robotique</strong>.</li>
  </ul>
  <hr>

  <h2 id="experiences-passees">liens vers mes expériences passées</h2>
  <ul>
    <li>Pilotage SDLC complet pour des plateformes d'échange crypto en tant que <strong>Product Owner / IT Project Manager</strong> chez Union of Financial Corners (Genève).</li>
    <li>Traduction des besoins commerciaux en spécifications en tant qu'<strong>Analyste fonctionnel</strong> chez FlyDevs (USA).</li>
    <li>Définition des stratégies de tests pour des équipes distantes en tant que <strong>QA Lead</strong> chez Charly Inc (Canada).</li>
    <li>Développement de modules ERP en Python en tant que <strong>Développeur Backend</strong> chez E-MIPS (Buenos Aires).</li>
  </ul>
  <hr>

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
  <hr>

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
  <hr>

  <h2>projets & réflexions</h2>
  <p>Voici une collection de mes derniers projets, idées et articles.</p>
</div>

<!-- ================= JEKYLL POSTS LOOP ================= -->
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
