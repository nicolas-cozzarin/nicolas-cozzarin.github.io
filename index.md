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
    padding-top: 40px;
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

  /* Resume Items (Experience & Education) */
  .resume-item {
    margin-bottom: 30px;
  }
  .resume-header {
    display: flex;
    justify-content: space-between;
    align-items: baseline;
    margin-bottom: 5px;
  }
  .resume-header h3 {
    margin: 0;
    font-size: 1.2em;
    color: #111;
  }
  .resume-date {
    font-size: 0.9em;
    color: #666;
    font-family: monospace, sans-serif;
  }
  .resume-company {
    font-weight: bold;
    color: #444;
    margin-bottom: 10px;
    font-size: 0.95em;
  }
  .resume-item ul {
    margin-top: 0;
    padding-left: 20px;
    font-size: 0.95em;
    color: #333;
  }

  /* Courses List */
  .course-list {
    list-style-type: none;
    padding: 0;
  }
  .course-list li {
    margin-bottom: 15px;
    font-size: 0.95em;
    border-left: 3px solid #eee;
    padding-left: 15px;
  }
  .course-title {
    font-weight: bold;
    color: #222;
  }
  .course-meta {
    font-size: 0.85em;
    color: #666;
    font-family: monospace, sans-serif;
    margin-bottom: 3px;
    display: block;
  }

  /* Skills Stars (Two Columns) */
  .skills-container { margin-bottom: 40px; }
  .skill-category { 
    margin-top: 35px; 
    font-weight: bold; 
    border-bottom: 1px solid #333; 
    padding-bottom: 5px; 
    margin-bottom: 15px; 
    font-size: 1.1em;
  }
  .skills-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    column-gap: 50px;
  }
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
    .resume-header { flex-direction: column; }
    .resume-date { margin-top: 5px; }
    .skills-grid { grid-template-columns: 1fr; }
  }
</style>

<script>
  function setLanguage(lang) {
    document.getElementById('lang-en').style.display = lang === 'en' ? 'block' : 'none';
    document.getElementById('lang-fr').style.display = lang === 'fr' ? 'block' : 'none';
    
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
    
    <div class="top-section">
      <aside class="sidebar">
        <h2>Nicolas Cozzarin</h2>
        <img src="docs/assets/ppicture.jpeg" alt="Nicolas Cozzarin" class="profile-pic">
        <hr>
        <ul class="sidebar-links">
          <li><a href="https://www.linkedin.com/in/ncozzarin/?skipRedirect=true" target="_blank">Find me on LinkedIn</a></li>
          <li><a href="docs/assets/CV_COZZARIN_EN.pdf" download>Download my CV</a></li>
          <li><a href="https://www.linkedin.com/in/ncozzarin/?skipRedirect=true" target="_blank">Check out my GitHub profile</a></li>
          <li><a href="mailto:nicolasjcozzarin@gmail.com">E-mail me</a></li>
        </ul>
      </aside>

      <div class="about-content">
        <h2 id="about-me">about me</h2>
        <p>I am an IT Project Manager and Product Owner with 10 years of experience. I specialize in Agile methodologies (Scrum/Kanban) and Software Development Life Cycle (SDLC) management. My technical focus is on AI and Data, allowing me to translate user needs into practical, effective technical solutions.</p>
        <p>Currently, I am completing a BSc in Artificial Intelligence & Robotics at Universidad Siglo XXI, focusing on machine learning and generative AI.</p>
      </div>
    </div>

    <div class="full-width-section">
      <hr class="section-divider">

      <h2 id="professional-experience">professional experience</h2>
      
      <div class="resume-item">
        <div class="resume-header">
          <h3>AI Product Owner</h3>
          <span class="resume-date">Nov 2025 – Present</span>
        </div>
        <div class="resume-company">Security Forces Disciplinary Control System | Cordoba, Argentina</div>
        <ul>
          <li>Managing the implementation of an NLP model for automated text classification of legal cases.</li>
          <li>Defining and enforcing strict data anonymization protocols to ensure privacy and compliance.</li>
          <li>Bridging the gap between the technical data science team and legal stakeholders to align product development with operational needs.</li>
        </ul>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Product Owner / IT Project Manager</h3>
          <span class="resume-date">Oct 2022 – Oct 2025</span>
        </div>
        <div class="resume-company">Union of Financial Corners | Geneva, Switzerland</div>
        <ul>
          <li>Managed the full Software Development Life Cycle (SDLC) for robust cryptocurrency exchange platforms.</li>
          <li>Optimized Agile workflows (Scrum/Kanban), resulting in a 20% increase in the development team's velocity.</li>
          <li>Translated complex business requirements into technical roadmaps, ensuring alignment with financial industry standards.</li>
        </ul>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Functional Analyst</h3>
          <span class="resume-date">Feb 2019 – Oct 2022</span>
        </div>
        <div class="resume-company">FlyDevs | USA</div>
        <ul>
          <li>Gathered business needs and translated them into actionable, detailed functional specifications for engineering teams.</li>
          <li>Facilitated stakeholder communication to ensure technical deliverables consistently met business objectives.</li>
        </ul>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>QA Lead</h3>
          <span class="resume-date">2017 – Feb 2019</span>
        </div>
        <div class="resume-company">Charly Inc | Canada</div>
        <ul>
          <li>Designed and led comprehensive testing strategies, coordinating effectively with remote software development teams.</li>
          <li>Streamlined delivery processes, significantly reducing post-release bugs and improving overall product stability.</li>
        </ul>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Backend Python Developer</h3>
          <span class="resume-date">Feb 2015 – 2017</span>
        </div>
        <div class="resume-company">E-MIPS | Buenos Aires, Argentina</div>
        <ul>
          <li>Developed, customized, and maintained ERP modules using Python, kicking off my technical career.</li>
          <li>Collaborated closely with cross-functional teams to deliver scalable backend solutions tailored to client needs.</li>
        </ul>
      </div>

      <hr class="section-divider">

      <h2 id="education">education</h2>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Bachelor in Artificial Intelligence & Robotics</h3>
          <span class="resume-date">2021 – 2025</span>
        </div>
        <div class="resume-company">Universidad Siglo XXI (R.M. n° 1142/2021)</div>
        <ul>
          <li><strong>Specialization:</strong> Artificial Intelligence, Data Science, and Robotics.</li>
          <li><strong>Relevant Coursework:</strong> Machine Learning, Deep Learning, and Generative AI.</li>
        </ul>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>AI & Robotics Exchange Laboratory</h3>
          <span class="resume-date">Nov 2024 – Nov 2025</span>
        </div>
        <div class="resume-company">Hochschule Furtwangen | Germany (Remote)</div>
        <ul>
          <li>Completed coursework in Machine Learning, Deep Generative Models, Computer Vision, Robotics, and Microcontroller Systems.</li>
          <li>Maintained a strong focus on AI model development, data processing, and hands-on experimentation in Jupyter-based environments.</li>
          <li>Collaborated in a multicultural academic setting, strengthening analytical research and cross-cultural communication skills.</li>
        </ul>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Electronics Technician Diploma</h3>
          <span class="resume-date">2009 – 2015</span>
        </div>
        <div class="resume-company">Instituto Técnico Industrial San Judas Tadeo</div>
        <ul>
          <li>Gained a solid foundation in electronics, applied systems, and hardware technologies.</li>
          <li>Developed analytical, project-oriented problem-solving skills that easily transfer to software engineering and IT.</li>
        </ul>
      </div>

      <hr class="section-divider">

      <h2 id="courses">courses & certifications</h2>
      <ul class="course-list">
        <li>
          <span class="course-meta">2026 • Altruisme Efficace France</span>
          <span class="course-title">Introductory Workshops to Effective Altruism</span><br>
          Exploring high-impact strategies and evidence-based approaches to global problem-solving.
        </li>
        <li>
          <span class="course-meta">Apr 2025 • Mendix (Credential ID 90924)</span>
          <span class="course-title">Mendix Developer Certificate</span><br>
          Certification in rapid, scalable low-code application development.
        </li>
        <li>
          <span class="course-meta">Semrush</span>
          <span class="course-title">Backlink Management Course with Greg Gifford</span><br>
          Advanced strategies for SEO, link-building, and digital presence optimization.
        </li>
        <li>
          <span class="course-meta">Swiss Financial Compliance</span>
          <span class="course-title">MLA Training Module</span><br>
          Training in anti-money laundering regulations and strict financial compliance.
        </li>
        <li>
          <span class="course-meta">Udemy</span>
          <span class="course-title">Build ReactJS Applications</span><br>
          Practical development of dynamic, component-based frontend web applications.
        </li>
        <li>
          <span class="course-meta">Jun 2020 • Coderhouse</span>
          <span class="course-title">Web Development (Desarrollo Web)</span><br>
          Fundamentals of modern web architecture, responsive design, and deployment.
        </li>
        <li>
          <span class="course-meta">2017</span>
          <span class="course-title">Hardware Descriptive Language for VHDL Development</span><br>
          Programming and logic design for complex digital circuits and FPGA integration.
        </li>
        <li>
          <span class="course-meta">Programming</span>
          <span class="course-title">Advanced C++ Programming and Modern Practices</span><br>
          Deep dive into memory management, object-oriented design, and high-performance coding.
        </li>
        <li>
          <span class="course-meta">2016</span>
          <span class="course-title">University Course in Microelectronics</span><br>
          Design, fabrication principles, and practical applications of microelectronic systems.
        </li>
      </ul>

      <hr class="section-divider">

      <h2 id="skills">skills</h2>
      <div class="skills-container">
        
        <div class="skill-category">Tech, Data & AI</div>
        <div class="skills-grid">
          <div class="skill-row"><span class="skill-name">Python</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Pandas</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Scikit-learn</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">PyTorch</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">NLP</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">NER</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">SQL</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">React.js</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">TypeScript</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">Git</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Docker</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">CI/CD</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">REST APIs</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
        </div>

        <div class="skill-category">Product & Management</div>
        <div class="skills-grid">
          <div class="skill-row"><span class="skill-name">Agile (Scrum/Kanban)</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">SDLC</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Backlog Management</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">User Stories</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Jira</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Confluence</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Azure DevOps</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Figma</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">Miro</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">Balsamiq</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
        </div>
        
        <div class="skill-category">Languages</div>
        <div class="skills-grid">
          <div class="skill-row"><span class="skill-name">Spanish (Native)</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">English (C1)</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">French (C1)</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">German (B2)</span> <span class="skill-stars"><span class="filled">★★★</span>★★</span></div>
        </div>

      </div>
      
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
    
    <div class="top-section">
      <aside class="sidebar">
        <h2>Nicolas Cozzarin</h2>
        <img src="docs/assets/ppicture.jpeg" alt="Nicolas Cozzarin" class="profile-pic">
        <hr>
        <ul class="sidebar-links">
          <li><a href="#" target="_blank">Me retrouver sur LinkedIn</a></li>
          <li><a href="docs/assets/CV_COZZARIN_FR.pdf" download>Télécharger mon CV</a></li>
          <li><a href="https://github.com/nicolas-cozzarin" target="_blank">Mon profil GitHub</a></li>
          <li><a href="mailto:nicolasjcozzarin@gmail.com">M'envoyer un e-mail</a></li>
        </ul>
      </aside>

      <div class="about-content">
        <h2 id="a-propos">à propos</h2>
        <p>Product Owner et Chef de Projet IT avec 10 ans d'expérience. Je suis spécialiste des méthodologies Agiles (Scrum/Kanban) et du pilotage du cycle de vie des logiciels (SDLC). Fort d'une spécialisation en IA et Data, je traduis les besoins utilisateurs en solutions techniques concrètes et performantes.</p>
        <p>Je termine actuellement un Bachelor en Intelligence Artificielle et Robotique à l'Universidad Siglo XXI, avec un accent sur le machine learning et l'IA générative.</p>
      </div>
    </div>

    <div class="full-width-section">
      <hr class="section-divider">

      <h2 id="experiences-professionnelles">expérience professionnelle</h2>
      
      <div class="resume-item">
        <div class="resume-header">
          <h3>AI Product Owner</h3>
          <span class="resume-date">Nov 2025 – Présent</span>
        </div>
        <div class="resume-company">Système de Contrôle Disciplinaire des Forces de Sécurité | Cordoba, Argentine</div>
        <ul>
          <li>Pilotage de l'implémentation d'un modèle NLP pour la classification automatisée de textes juridiques.</li>
          <li>Définition et application de protocoles stricts d'anonymisation des données pour garantir la confidentialité et la conformité légale.</li>
          <li>Gestion du backlog produit, servant de pont entre l'équipe technique de data science et les experts juridiques.</li>
        </ul>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Product Owner / Chef de Projet IT</h3>
          <span class="resume-date">Oct 2022 – Oct 2025</span>
        </div>
        <div class="resume-company">Union of Financial Corners | Genève, Suisse</div>
        <ul>
          <li>Gestion complète du cycle de vie du développement (SDLC) de plateformes d'échange de cryptomonnaies à haute performance.</li>
          <li>Optimisation des processus Agiles (Scrum/Kanban), entraînant une augmentation de 20% de la vélocité de l'équipe de développement.</li>
          <li>Traduction des exigences commerciales en spécifications techniques, en garantissant l'alignement avec les normes du secteur financier.</li>
        </ul>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Analyste Fonctionnel</h3>
          <span class="resume-date">Fév 2019 – Oct 2022</span>
        </div>
        <div class="resume-company">FlyDevs | USA</div>
        <ul>
          <li>Recueil des besoins métiers et traduction en spécifications fonctionnelles claires pour les équipes d'ingénierie.</li>
          <li>Facilitation de la communication entre les parties prenantes pour assurer que les livrables techniques répondent aux objectifs commerciaux.</li>
        </ul>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>QA Lead</h3>
          <span class="resume-date">2017 – Fév 2019</span>
        </div>
        <div class="resume-company">Charly Inc | Canada</div>
        <ul>
          <li>Conception et direction des stratégies de tests globaux, en coordination avec des équipes de développement à distance.</li>
          <li>Amélioration des processus de livraison, réduisant considérablement les bugs post-lancement et renforçant la stabilité des produits.</li>
        </ul>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Développeur Backend Python</h3>
          <span class="resume-date">Fév 2015 – 2017</span>
        </div>
        <div class="resume-company">E-MIPS | Buenos Aires, Argentine</div>
        <ul>
          <li>Développement et maintenance de modules ERP en Python.</li>
          <li>Collaboration étroite avec des équipes pluridisciplinaires pour livrer des solutions backend scalables et adaptées aux clients.</li>
        </ul>
      </div>

      <hr class="section-divider">

      <h2 id="education-fr">éducation</h2>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Bachelor en Intelligence Artificielle et Robotique</h3>
          <span class="resume-date">2021 – 2025</span>
        </div>
        <div class="resume-company">Universidad Siglo XXI (R.M. n° 1142/2021)</div>
        <ul>
          <li><strong>Spécialisation :</strong> Intelligence Artificielle, Data Science, Robotique.</li>
          <li><strong>Cours pertinents :</strong> Machine Learning, Deep Learning, IA Générative.</li>
        </ul>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Échange Laboratoire IA & Robotique</h3>
          <span class="resume-date">Nov 2024 – Nov 2025</span>
        </div>
        <div class="resume-company">Hochschule Furtwangen | Allemagne (À distance)</div>
        <ul>
          <li>Modules suivis en Machine Learning, Modèles Génératifs Profonds, Vision par Ordinateur, Robotique et Systèmes Microcontrôleurs.</li>
          <li>Fort accent sur le développement de modèles d'IA, le traitement des données et l'expérimentation pratique via des environnements Jupyter.</li>
          <li>Collaboration dans un cadre académique multiculturel, renforçant les capacités d'analyse, de recherche et de communication.</li>
        </ul>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Diplôme de Technicien Électronicien</h3>
          <span class="resume-date">2009 – 2015</span>
        </div>
        <div class="resume-company">Instituto Técnico Industrial San Judas Tadeo</div>
        <ul>
          <li>Bases solides en électronique, systèmes appliqués et technologies matérielles.</li>
          <li>Développement de compétences analytiques et orientées projet, facilement transférables à l'ingénierie logicielle et à l'IT.</li>
        </ul>
      </div>

      <hr class="section-divider">

      <h2 id="cours">cours & certifications</h2>
      <ul class="course-list">
        <li>
          <span class="course-meta">2026 • Altruisme Efficace France</span>
          <span class="course-title">Ateliers d’introduction à l’altruisme efficace</span><br>
          Exploration de stratégies à fort impact et basées sur les preuves pour la résolution de problèmes globaux.
        </li>
        <li>
          <span class="course-meta">Avr 2025 • Mendix (ID 90924)</span>
          <span class="course-title">Mendix Developer Certificate</span><br>
          Certification en développement rapide d'applications scalables "low-code".
        </li>
        <li>
          <span class="course-meta">Semrush</span>
          <span class="course-title">Backlink Management Course avec Greg Gifford</span><br>
          Stratégies avancées pour le SEO, le link-building et l'optimisation de la présence numérique.
        </li>
        <li>
          <span class="course-meta">Swiss Financial Compliance</span>
          <span class="course-title">MLA Training Module</span><br>
          Formation sur la réglementation anti-blanchiment d'argent et la stricte conformité financière.
        </li>
        <li>
          <span class="course-meta">Udemy</span>
          <span class="course-title">Build ReactJS Applications</span><br>
          Développement pratique d'applications web frontend dynamiques basées sur des composants.
        </li>
        <li>
          <span class="course-meta">Juin 2020 • Coderhouse</span>
          <span class="course-title">Développement Web (Desarrollo Web)</span><br>
          Principes fondamentaux de l'architecture web moderne, du design responsive et du déploiement.
        </li>
        <li>
          <span class="course-meta">2017</span>
          <span class="course-title">Hardware Descriptive Language for VHDL Development</span><br>
          Programmation et conception logique pour circuits numériques complexes et intégration FPGA.
        </li>
        <li>
          <span class="course-meta">Programmation</span>
          <span class="course-title">Advanced C++ Programming and Modern Practices</span><br>
          Plongée dans la gestion de la mémoire, la conception orientée objet et le code haute performance.
        </li>
        <li>
          <span class="course-meta">2016</span>
          <span class="course-title">Cours Universitaire en Microélectronique</span><br>
          Conception, principes de fabrication et applications pratiques des systèmes microélectroniques.
        </li>
      </ul>

      <hr class="section-divider">

      <h2 id="competences">compétences</h2>
      <div class="skills-container">
        
        <div class="skill-category">Tech, Data & IA</div>
        <div class="skills-grid">
          <div class="skill-row"><span class="skill-name">Python</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">Pandas</span> <span class="skill-stars"><span class="filled">★★★</span>★★</span></div>
          <div class="skill-row"><span class="skill-name">Scikit-learn</span> <span class="skill-stars"><span class="filled">★★★</span>★★</span></div>
          <div class="skill-row"><span class="skill-name">PyTorch</span> <span class="skill-stars"><span class="filled">★★★</span>★★</span></div>
          <div class="skill-row"><span class="skill-name">NLP</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">NER</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">SQL</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">React.js</span> <span class="skill-stars"><span class="filled">★★★</span>★★</span></div>
          <div class="skill-row"><span class="skill-name">TypeScript</span> <span class="skill-stars"><span class="filled">★★</span>★★★</span></div>
          <div class="skill-row"><span class="skill-name">Git</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Docker</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">CI/CD</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">API REST</span> <span class="skill-stars"><span class="filled">★★★</span>★★</span></div>
        </div>

        <div class="skill-category">Produit & Management</div>
        <div class="skills-grid">
          <div class="skill-row"><span class="skill-name">Agile (Scrum/Kanban)</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">SDLC</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Backlog Management</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">User Stories</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Jira</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Confluence</span> <span class="skill-stars"><span class="filled">★★</span></span>★★★</div>
          <div class="skill-row"><span class="skill-name">Azure DevOps</span> <span class="skill-stars"><span class="filled">★★★</span></span>★★</div>
          <div class="skill-row"><span class="skill-name">Figma</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">Miro</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">Balsamiq</span> <span class="skill-stars"><span class="filled">★★★</span>★★</span></div>
        </div>
        
        <div class="skill-category">Langues</div>
        <div class="skills-grid">
          <div class="skill-row"><span class="skill-name">Espagnol (Natif)</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Anglais (everyday working language)</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">Français (working language)</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">Allemand (B2)</span> <span class="skill-stars"><span class="filled">★★★</span>★★</span></div>
          <div class="skill-row"><span class="skill-name">Chinois (HSK3)</span> <span class="skill-stars"><span class="filled">★★</span>★★★</span></div>
        </div>

      </div>
      
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
