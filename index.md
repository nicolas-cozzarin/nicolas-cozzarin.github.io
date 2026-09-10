<style>
  /* Layout Structure */
  .portfolio-wrapper {
    position: relative;
    max-width: min(1200px, 92vw);
    margin: 0 auto;
    padding: 0 clamp(16px, 4vw, 48px) 50px;
    box-sizing: border-box;
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
    flex: 0 0 300px;
  }
  .sidebar h2 { 
    margin-top: 0; 
    font-size: 1.5em;
    margin-bottom: 15px;
  }
  .profile-pic {
    width: 100%;
    max-width: 300px;
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
    margin-bottom: 8px;
    font-size: 0.95em;
  }
  .resume-summary {
    margin-top: 0;
    margin-bottom: 12px;
    font-size: 0.95em;
    color: #555;
    line-height: 1.5;
    max-width: 70ch;
  }
  .resume-item ul {
    margin-top: 0;
    padding-left: 20px;
    font-size: 0.95em;
    color: #333;
    max-width: 70ch;
  }
  .resume-item ul li {
    margin-bottom: 8px;
  }
  .about-content p {
    max-width: 85ch;
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

  /* Skills (Compact) */
  .skills-compact { margin-bottom: 10px; }
  .skill-line {
    margin-bottom: 16px;
    font-size: 0.95em;
    color: #333;
    line-height: 1.6;
    border-left: 3px solid #eee;
    padding-left: 15px;
    max-width: 70ch;
  }
  .skill-label {
    font-weight: bold;
    color: #222;
  }
  
  /* Tables */
  table { width: 100%; border-collapse: collapse; margin-bottom: 30px; font-size: 0.95em; }
  th, td { border: 1px solid #eee; padding: 10px; text-align: left; vertical-align: top; }
  th { background-color: #fafafa; font-weight: normal; color: #555; }
  
  /* Responsive */
  @media (max-width: 768px) {
    .top-section { flex-direction: column; gap: 30px; }
    .sidebar { flex: 1 1 auto; }
    .profile-pic { max-width: 240px; }
    .lang-toggle-container { position: relative; text-align: right; margin-bottom: 20px; top: 0; }
    .resume-header { flex-direction: column; }
    .resume-date { margin-top: 5px; }
  }
</style>

<script>
  function setLanguage(lang) {
    document.getElementById('lang-en').style.display = lang === 'en' ? 'block' : 'none';
    document.getElementById('lang-fr').style.display = lang === 'fr' ? 'block' : 'none';
    document.getElementById('lang-es').style.display = lang === 'es' ? 'block' : 'none';
    
    document.getElementById('btn-en').className = lang === 'en' ? 'lang-btn active' : 'lang-btn';
    document.getElementById('btn-fr').className = lang === 'fr' ? 'lang-btn active' : 'lang-btn';
    document.getElementById('btn-es').className = lang === 'es' ? 'lang-btn active' : 'lang-btn';
  }
</script>

<div class="portfolio-wrapper">
  
  <!-- Minimalist Language Toggle -->
  <div class="lang-toggle-container">
    <button id="btn-en" class="lang-btn active" onclick="setLanguage('en')">EN</button> | 
    <button id="btn-fr" class="lang-btn" onclick="setLanguage('fr')">FR</button> | 
    <button id="btn-es" class="lang-btn" onclick="setLanguage('es')">ES</button>
  </div>

  <!-- ================= ENGLISH SECTION ================= -->
  <div id="lang-en">
    
    <div class="top-section">
      <aside class="sidebar">
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
        <h2 id="about-me"><strong>About me</strong></h2>
        <p>I'm a Product Owner and IT Project Manager with 10 years of experience across product management, QA, and backend development, now specialised in AI and data products.</p>
        <p>Having successfully completed my BSc in Artificial Intelligence & Robotics, my current focus is on AI compliance, AI ethics and alignment, and seamlessly integrating AI and automations into companies to make their processes significantly more effective.</p>
        <p>Alongside my professional work, I have volunteered extensively in animal welfare and animal rights, and I am now exploring the potential impact of artificial intelligence on the situation of animals, a crucial topic that remains largely undiscussed. This includes examining the present and potential use of AI in factory farming and, conversely, in reducing wild animal suffering, as well as how reducing speciesist attitudes in frontier AI systems could shape outcomes for animals now and in the future. Finally, I consider how AI tools could help boost our efforts in animal advocacy.</p>
        <p>EU citizen with a Swiss work permit, based near Geneva and immediately available to relocate.</p>
      </div>
    </div>

    <div class="full-width-section">
      <hr class="section-divider">

      <h2 id="professional-experience"><strong>Professional experience</strong></h2>
      
      <div class="resume-item">
        <div class="resume-header">
          <h3>IT Project Manager / Product Owner</h3>
          <span class="resume-date">Oct 2022 – Oct 2025</span>
        </div>
        <div class="resume-company">Union of Financial Corners | Geneva, Switzerland</div>
        <p class="resume-summary">Led the end-to-end development of digital financial products, from business planning and product definition to delivery, launch, and post-launch optimization, while ensuring alignment between business objectives, technology, and compliance requirements. Managed the product backlog and distributed engineering teams, translated business needs into actionable user stories, and used sprint planning and performance metrics to improve delivery efficiency.</p>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>AI Product Owner & ML Developer (Internship)</h3>
          <span class="resume-date">Nov 2025 – Jun 2026</span>
        </div>
        <div class="resume-company">Security Forces Disciplinary Control System | Córdoba, Argentina</div>
        <ul>
          <li>Owned end-to-end delivery of an NLP text-classification system automating the triage of legal case files: scoped requirements with legal staff, defined the roadmap, and built the model myself.</li>
          <li>Developed the classification pipeline in Python, PyTorch, and Scikit-learn: data preparation, model training, and evaluation.</li>
          <li>Designed and implemented an anonymisation pipeline (NER + pseudonymisation) so sensitive personal data never entered training or inference, meeting GDPR/LPD requirements.</li>
        </ul>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Functional Analyst</h3>
          <span class="resume-date">Feb 2019 – Dec 2022</span>
        </div>
        <div class="resume-company">FlyDevs | USA (Remote)</div>
        <p class="resume-summary">Translated business requirements into functional specifications and user stories, while acting as the link between stakeholders, UI/UX, QA, and engineering teams throughout product delivery. Facilitated Agile ceremonies, resolved delivery blockers, and helped streamline release processes by aligning technical delivery and CI/CD practices with business priorities.</p>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Lead Quality Assurance Analyst</h3>
          <span class="resume-date">Mar 2017 – Dec 2019</span>
        </div>
        <div class="resume-company">Charly Inc. | Canada (Remote)</div>
        <p class="resume-summary">Led quality assurance activities across several software projects, defining test strategies and coordinating a distributed QA team to ensure functional and technical requirements were met. Established processes for functional, integration, and regression testing, maintained test documentation and defect tracking, and improved the defect detection.</p>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Python Backend Developer - Odoo</h3>
          <span class="resume-date">Feb 2015 – Jun 2016</span>
        </div>
        <div class="resume-company">E-MIPS | Buenos Aires, Argentina</div>
        <p class="resume-summary">Developed and customized Odoo modules in Python to automate business processes including CRM, inventory, and accounting, and integrated the platform with external applications and APIs. Documented the solutions, used Git and Docker throughout development, and worked within Agile delivery cycles to maintain and evolve the applications.</p>
      </div>

      <hr class="section-divider">

      <h2 id="education"><strong>Education</strong></h2>

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
        <div class="resume-company">Hochschule Furtwangen | Germany</div>
        <ul>
          <li>Completed coursework in Machine Learning, Deep Generative Models, Computer Vision, Robotics, and Microcontroller Systems.</li>
          <li>Maintained a strong focus on AI model development, data processing, and hands-on experimentation in Jupyter-based environments.</li>
          <li>Collaborated in a multicultural academic setting, strengthening analytical research and cross-cultural communication skills.</li>
          <li>Passed the German B2 language exam and built connections with professionals and organizations active in Germany's AI ecosystem.</li>
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

      <h2 id="animal-advocacy"><strong>Animal Advocacy Experience</strong></h2>

      <div class="resume-item">
        <div class="resume-header">
          <h3>AI Enabler</h3>
          <span class="resume-date">2026 – Present</span>
        </div>
        <div class="resume-company">Hack the Fork | Paris, France</div>
        <p class="resume-summary">Designed the AI framework for the hackathon and helped explore and test the AWS environment; will mentor participating teams on AI scoping during the event.</p>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>DevOps Volunteer</h3>
          <span class="resume-date">2019 – 2022</span>
        </div>
        <div class="resume-company">Difusión V | Voicot</div>
        <p class="resume-summary">Set up and maintained hosting and CI/CD for the organisation's websites: <a href="http://difuv.com" target="_blank">difuv.com</a>, <a href="http://voicot.com" target="_blank">voicot.com</a>, and <a href="http://difusionv.com" target="_blank">difusionv.com</a>.</p>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Founder & Organiser</h3>
          <span class="resume-date">2026 – Present</span>
        </div>
        <div class="resume-company">We The Free | Angoulême, France</div>
        <p class="resume-summary">Founded and run the local chapter: manage the materials budget and purchasing, organise outreach and social events, and recruit activists from the surrounding area.</p>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Logistics</h3>
          <span class="resume-date">2021 – 2022</span>
        </div>
        <div class="resume-company">Vegan Campout Argentina</div>
        <p class="resume-summary">Coordinated stall logistics and supplier needs for a 2,000-attendee event, contributed to the programme, and managed a team of 20 volunteers on the day.</p>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Organiser</h3>
          <span class="resume-date">2019 – 2022</span>
        </div>
        <div class="resume-company">Buenos Aires Animal Save</div>
        <p class="resume-summary">Co-organised slaughterhouse vigils: opened events by briefing attendees, liaised with slaughterhouse workers, supported participants during vigils, and produced footage for social media.</p>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Organiser</h3>
          <span class="resume-date">2018 – 2020</span>
        </div>
        <div class="resume-company">Anonymous for the Voiceless | Buenos Aires, Argentina</div>
        <p class="resume-summary">Created and ran Cube of Truth events with 20–60 activists: coordinated teams and materials, and welcomed and briefed new members.</p>
      </div>

      <hr class="section-divider">

      <h2 id="courses"><strong>Courses & certifications</strong></h2>
      <ul class="course-list">
        <li>
          <span class="course-meta">Sep 2026 • BlueDot Impact</span>
          <span class="course-title">Future of AI</span><br>
          An introduction to what AI can do today, where it's going over the next decade, and how you can start contributing to a better future.
        </li>
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

      <h2 id="skills"><strong>Skills</strong></h2>
      <div class="skills-compact">
        <p class="skill-line"><span class="skill-label">Product:</span> Agile (Scrum/Kanban), backlog management, product roadmapping, user research, A/B testing, stakeholder management, Jira, Confluence, Figma</p>
        <p class="skill-line"><span class="skill-label">AI & Data:</span> Python (Pandas, Scikit-learn, PyTorch), NLP/NER, SQL, RAG, LLM APIs (OpenAI, Anthropic), AI agent building, local LLM deployment</p>
        <p class="skill-line"><span class="skill-label">Engineering:</span> Docker, CI/CD, Git, React.js, TypeScript, REST APIs</p>
        <p class="skill-line"><span class="skill-label">Languages:</span> Spanish (native), English (C1), French (C1), German (B2), Chinese (HSK3)</p>
      </div>
      
      <hr class="section-divider">

      <h2 id="references"><strong>References</strong></h2>
      <table>
        <thead>
          <tr><th>Name</th><th>Role</th><th>Contact</th></tr>
        </thead>
        <tbody>
          <tr>
            <td>Andi Gjonej</td>
            <td>CEO, Union Financial Corners | Geneva, Switzerland</td>
            <td>Available on request<br><a href="docs/assets/Certificat_de_travail.pdf" download>Download Employment Certificate</a></td>
          </tr>
          <tr>
            <td>Franco Cellone</td>
            <td><a href="https://www.linkedin.com/company/15223804/" target="_blank">Coordinador de Registro y Análisis de la Información</a><br><a href="https://www.linkedin.com/company/15223804/" target="_blank">Gobierno de Córdoba</a></td>
            <td>Available on request</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>

  <!-- ================= FRENCH SECTION ================= -->
  <div id="lang-fr" style="display:none;">
    
    <div class="top-section">
      <aside class="sidebar">
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
        <h2 id="a-propos"><strong>À propos</strong></h2>
        <p>Je suis Product Owner et Chef de Projet IT, avec 10 ans d'expérience en gestion de produit, QA et développement backend, aujourd'hui spécialisé dans les produits IA et data.</p>
        <p>Ayant obtenu mon Bachelor en Intelligence Artificielle et Robotique, je me concentre actuellement sur l'intégration de l'IA et de l'automatisation en entreprise pour rendre les processus significativement plus efficaces, la conformité de l'IA, l'éthique et l'alignement des modèles.</p>
        <p>En parallèle de mon parcours professionnel, je me suis beaucoup investi dans le bénévolat pour le bien-être et les droits des animaux, et j'explore aujourd'hui l'impact potentiel de l'intelligence artificielle sur la situation des animaux, un sujet crucial qui reste largement absent du débat. Cela inclut l'examen de l'utilisation actuelle et potentielle de l'IA dans les élevages industriels et, à l'inverse, dans la réduction de la souffrance des animaux sauvages, ainsi que la manière dont la réduction des attitudes spécistes dans les systèmes d'IA de pointe peut avoir un impact présent et futur. Enfin, je m'intéresse à la façon dont les outils d'IA pourraient renforcer nos actions de plaidoyer pour les animaux.</p>
        <p>Citoyen de l'UE titulaire d'un permis de travail suisse, basé près de Genève et disponible immédiatement pour une relocalisation.</p>
      </div>
    </div>

    <div class="full-width-section">
      <hr class="section-divider">

      <h2 id="experiences-professionnelles"><strong>Expérience professionnelle</strong></h2>
      
      <div class="resume-item">
        <div class="resume-header">
          <h3>Chef de Projet IT / Product Owner</h3>
          <span class="resume-date">Oct 2022 – Oct 2025</span>
        </div>
        <div class="resume-company">Union of Financial Corners | Genève, Suisse</div>
        <p class="resume-summary">Pilotage de bout en bout du développement de produits financiers numériques, de la définition du produit et des business plans jusqu'au déploiement, au lancement et à l'optimisation post-lancement, en assurant l'alignement entre les enjeux métier, la technologie et les exigences de conformité. Gestion du backlog produit et d'équipes d'ingénierie réparties en Europe et en Amérique, traduction des besoins métier en user stories et pilotage des sprints et des indicateurs de performance.</p>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>AI Product Owner & Développeur ML (stage)</h3>
          <span class="resume-date">Nov 2025 – Juin 2026</span>
        </div>
        <div class="resume-company">Système de Contrôle Disciplinaire des Forces de Sécurité | Córdoba, Argentine</div>
        <ul>
          <li>Prise en charge de bout en bout d'un système de classification de texte NLP automatisant le tri des dossiers juridiques : cadrage des besoins avec les équipes juridiques, définition de la feuille de route, et développement du modèle.</li>
          <li>Développement du pipeline de classification en Python, PyTorch et Scikit-learn : préparation des données, entraînement et évaluation du modèle.</li>
          <li>Conception et mise en œuvre d'un pipeline d'anonymisation (NER + pseudonymisation) garantissant qu'aucune donnée personnelle sensible n'entre dans l'entraînement ou l'inférence, conformément au RGPD et à la LPD.</li>
        </ul>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Analyste fonctionnel</h3>
          <span class="resume-date">Fév 2019 – Déc 2022</span>
        </div>
        <div class="resume-company">FlyDevs | USA (À distance)</div>
        <p class="resume-summary">Traduction des besoins métier en spécifications fonctionnelles et en user stories, avec un rôle d'interface entre les parties prenantes, les équipes UI/UX, QA et engineering tout au long de la réalisation des produits. Animation des cérémonies Agile, résolution des blocages et amélioration des cycles de livraison en veillant à aligner les pratiques de développement et de CI/CD sur les priorités métier.</p>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Lead QA Analyst</h3>
          <span class="resume-date">Mar 2017 – Déc 2019</span>
        </div>
        <div class="resume-company">Charly Inc. | Canada (À distance)</div>
        <p class="resume-summary">Pilotage de l'assurance qualité sur plusieurs projets logiciels, avec définition des stratégies de test et coordination d'une équipe QA distribuée afin de garantir le respect des exigences fonctionnelles et techniques. Mise en place des processus de tests fonctionnels, d'intégration et de régression, maintenance de la documentation et du suivi des anomalies.</p>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Développeur Backend Python - Odoo</h3>
          <span class="resume-date">Fév 2015 – Juin 2016</span>
        </div>
        <div class="resume-company">E-MIPS | Buenos Aires, Argentine</div>
        <p class="resume-summary">Développement et personnalisation de modules Odoo en Python pour automatiser des processus métier tels que le CRM, la gestion des stocks et la comptabilité, ainsi qu'intégration d'applications et d'API externes. Documentation des solutions développées et utilisation de Git et Docker dans le cadre de cycles de développement Agile pour assurer la maintenance et l'évolution des applications.</p>
      </div>

      <hr class="section-divider">

      <h2 id="education-fr"><strong>Éducation</strong></h2>

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
        <div class="resume-company">Hochschule Furtwangen | Allemagne</div>
        <ul>
          <li>Modules suivis en Machine Learning, Modèles Génératifs Profonds, Vision par Ordinateur, Robotique et Systèmes Microcontrôleurs.</li>
          <li>Fort accent sur le développement de modèles d'IA, le traitement des données et l'expérimentation pratique via des environnements Jupyter.</li>
          <li>Collaboration dans un cadre académique multiculturel, renforçant les capacités d'analyse, de recherche et de communication.</li>
          <li>Obtention de la certification B2 en allemand et développement de contacts avec des acteurs de l'écosystème de l'IA en Allemagne.</li>
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

      <h2 id="plaidoyer-fr"><strong>Expérience en plaidoyer animal</strong></h2>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Référent IA</h3>
          <span class="resume-date">2026 – Aujourd'hui</span>
        </div>
        <div class="resume-company">Hack the Fork | Paris, France</div>
        <p class="resume-summary">Conception du cadre IA du hackathon et participation à l'exploration et aux tests de l'environnement AWS ; accompagnement des équipes participantes sur le cadrage IA pendant l'événement.</p>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Bénévole DevOps</h3>
          <span class="resume-date">2019 – 2022</span>
        </div>
        <div class="resume-company">Difusión V | Voicot</div>
        <p class="resume-summary">Mise en place et maintenance de l'hébergement et du CI/CD pour les sites de l'organisation : <a href="http://difuv.com" target="_blank">difuv.com</a>, <a href="http://voicot.com" target="_blank">voicot.com</a> et <a href="http://difusionv.com" target="_blank">difusionv.com</a>.</p>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Fondateur et organisateur</h3>
          <span class="resume-date">2026 – Aujourd'hui</span>
        </div>
        <div class="resume-company">We The Free | Angoulême, France</div>
        <p class="resume-summary">Fondation et gestion de l'antenne locale : gestion du budget matériel et des achats, organisation d'actions de sensibilisation et d'événements sociaux, et recrutement de militants dans la région.</p>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Logistique</h3>
          <span class="resume-date">2021 – 2022</span>
        </div>
        <div class="resume-company">Vegan Campout Argentina</div>
        <p class="resume-summary">Coordination de la logistique des stands et des besoins fournisseurs pour un événement de 2 000 participants, contribution au programme, et encadrement d'une équipe de 20 bénévoles le jour J.</p>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Organisateur</h3>
          <span class="resume-date">2019 – 2022</span>
        </div>
        <div class="resume-company">Buenos Aires Animal Save</div>
        <p class="resume-summary">Co-organisation de veillées devant des abattoirs : ouverture des événements par un briefing des participants, liaison avec les employés des abattoirs, accompagnement des participants pendant les veillées, et production de contenus vidéo pour les réseaux sociaux.</p>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Organisateur</h3>
          <span class="resume-date">2018 – 2020</span>
        </div>
        <div class="resume-company">Anonymous for the Voiceless | Buenos Aires, Argentine</div>
        <p class="resume-summary">Création et animation d'événements Cube of Truth avec 20 à 60 militants : coordination des équipes et du matériel, et accueil et briefing des nouveaux membres.</p>
      </div>

      <hr class="section-divider">

      <h2 id="cours"><strong>Cours & certifications</strong></h2>
      <ul class="course-list">
        <li>
          <span class="course-meta">Sep 2026 • BlueDot Impact</span>
          <span class="course-title">Future of AI</span><br>
          Une introduction à ce que l'IA peut faire aujourd'hui, à son évolution au cours de la prochaine décennie, et à la manière de contribuer dès à présent à un avenir meilleur.
        </li>
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

      <h2 id="competences"><strong>Compétences</strong></h2>
      <div class="skills-compact">
        <p class="skill-line"><span class="skill-label">Produit :</span> Agile (Scrum/Kanban), gestion du backlog, roadmap produit, recherche utilisateur, A/B testing, gestion des parties prenantes, Jira, Confluence, Figma</p>
        <p class="skill-line"><span class="skill-label">IA & Data :</span> Python (Pandas, Scikit-learn, PyTorch), NLP/NER, SQL, RAG, API LLM (OpenAI, Anthropic), création d'agents IA, déploiement de LLM en local</p>
        <p class="skill-line"><span class="skill-label">Ingénierie :</span> Docker, CI/CD, Git, React.js, TypeScript, REST APIs</p>
        <p class="skill-line"><span class="skill-label">Langues :</span> Espagnol (natif), Anglais (C1), Français (C1), Allemand (B2), Chinois (HSK3)</p>
      </div>
      
      <hr class="section-divider">

      <h2 id="references-fr"><strong>Références</strong></h2>
      <table>
        <thead>
          <tr><th>Nom</th><th>Rôle</th><th>Contact</th></tr>
        </thead>
        <tbody>
          <tr>
            <td>Andi Gjonej</td>
            <td>PDG, Union Financial Corners | Genève, Suisse</td>
            <td>Disponible sur demande<br><a href="docs/assets/Certificat_de_travail.pdf" download>Télécharger le Certificat de travail</a></td>
          </tr>
          <tr>
            <td>Franco Cellone</td>
            <td><a href="https://www.linkedin.com/company/15223804/" target="_blank">Coordinador de Registro y Análisis de la Información</a><br><a href="https://www.linkedin.com/company/15223804/" target="_blank">Gobierno de Córdoba</a></td>
            <td>Disponible sur demande</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>

  <!-- ================= SPANISH SECTION ================= -->
  <div id="lang-es" style="display:none;">
    
    <div class="top-section">
      <aside class="sidebar">
        <img src="docs/assets/ppicture.jpeg" alt="Nicolas Cozzarin" class="profile-pic">
        <hr>
        <ul class="sidebar-links">
          <li><a href="https://www.linkedin.com/in/ncozzarin/?skipRedirect=true" target="_blank">Ver mi perfil de LinkedIn</a></li>
          <li><a href="docs/assets/CV_COZZARIN_ES.pdf" download>Descargar mi CV</a></li>
          <li><a href="https://github.com/nicolas-cozzarin" target="_blank">Ver mi perfil de GitHub</a></li>
          <li><a href="mailto:nicolasjcozzarin@gmail.com">Enviarme un correo</a></li>
        </ul>
      </aside>

      <div class="about-content">
        <h2 id="sobre-mi"><strong>Sobre mí</strong></h2>
        <p>Soy Product Owner y IT Project Manager, con 10 años de experiencia en gestión de producto, QA y desarrollo backend, actualmente especializado en productos de IA y datos.</p>
        <p>Habiendo completado con éxito mi Licenciatura en Inteligencia Artificial y Robótica, mi enfoque actual está puesto en el cumplimiento normativo de la IA, la ética y el alineamiento de los modelos de IA, así como en la integración fluida de la IA y la automatización en las empresas para hacer sus procesos significativamente más eficientes.</p>
        <p>Además de mi trabajo profesional, he participado activamente como voluntario en causas de bienestar y derechos animales, y actualmente estoy explorando el impacto potencial de la inteligencia artificial en la situación de los animales, un tema crucial que sigue siendo poco discutido. Esto incluye analizar el uso actual y potencial de la IA en la ganadería industrial y, por el contrario, en la reducción del sufrimiento de los animales silvestres, así como la manera en que reducir las actitudes especistas en los sistemas de IA de vanguardia puede tener un impacto en el presente y en el futuro. Finalmente, considero de qué manera las herramientas de IA podrían potenciar nuestros esfuerzos de activismo por los animales.</p>
        <p>Ciudadano de la UE con permiso de trabajo suizo, radicado cerca de Ginebra y disponible de forma inmediata para reubicarse.</p>
      </div>
    </div>

    <div class="full-width-section">
      <hr class="section-divider">

      <h2 id="experiencia-profesional"><strong>Experiencia profesional</strong></h2>
      
      <div class="resume-item">
        <div class="resume-header">
          <h3>Gerente de Proyectos IT / Product Owner</h3>
          <span class="resume-date">Oct 2022 – Oct 2025</span>
        </div>
        <div class="resume-company">Union of Financial Corners | Ginebra, Suiza</div>
        <p class="resume-summary">Lideré el desarrollo integral de productos financieros digitales, desde la planificación de negocio y la definición del producto hasta la entrega, el lanzamiento y la optimización post-lanzamiento, asegurando la alineación entre los objetivos de negocio, la tecnología y los requisitos de cumplimiento normativo. Gestioné el backlog de producto y equipos de ingeniería distribuidos, traduje las necesidades del negocio en user stories accionables, y utilicé la planificación de sprints y métricas de desempeño para mejorar la eficiencia en la entrega.</p>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>AI Product Owner y Desarrollador ML (pasantía)</h3>
          <span class="resume-date">Nov 2025 – Jun 2026</span>
        </div>
        <div class="resume-company">Sistema de Control Disciplinario de las Fuerzas de Seguridad | Córdoba, Argentina</div>
        <ul>
          <li>Lideré de punta a punta un sistema de clasificación de texto con NLP para automatizar el triage de expedientes legales: relevé los requerimientos junto con el equipo legal, definí el roadmap, y desarrollé el modelo.</li>
          <li>Desarrollé el pipeline de clasificación en Python, PyTorch y Scikit-learn: preparación de datos, entrenamiento y evaluación del modelo.</li>
          <li>Diseñé e implementé un pipeline de anonimización (NER + pseudonimización) para que ningún dato personal sensible ingresara al entrenamiento o la inferencia, cumpliendo con el RGPD y la LPD.</li>
        </ul>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Analista Funcional</h3>
          <span class="resume-date">Feb 2019 – Dic 2022</span>
        </div>
        <div class="resume-company">FlyDevs | EE. UU. (Remoto)</div>
        <p class="resume-summary">Traduje los requerimientos de negocio en especificaciones funcionales y user stories, actuando como nexo entre las partes interesadas, los equipos de UI/UX, QA e ingeniería a lo largo de la entrega del producto. Facilité las ceremonias Ágiles, resolví bloqueos en la entrega y contribuí a optimizar los procesos de lanzamiento alineando las prácticas de desarrollo y CI/CD con las prioridades del negocio.</p>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Analista Líder de QA</h3>
          <span class="resume-date">Mar 2017 – Dic 2019</span>
        </div>
        <div class="resume-company">Charly Inc. | Canadá (Remoto)</div>
        <p class="resume-summary">Lideré las actividades de aseguramiento de calidad en varios proyectos de software, definiendo estrategias de testing y coordinando un equipo de QA distribuido para garantizar el cumplimiento de los requisitos funcionales y técnicos. Establecí procesos de testing funcional, de integración y de regresión, mantuve la documentación de pruebas y el seguimiento de defectos, y mejoré la detección de errores.</p>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Desarrollador Backend Python - Odoo</h3>
          <span class="resume-date">Feb 2015 – Jun 2016</span>
        </div>
        <div class="resume-company">E-MIPS | Buenos Aires, Argentina</div>
        <p class="resume-summary">Desarrollé y personalicé módulos de Odoo en Python para automatizar procesos de negocio como CRM, inventario y contabilidad, e integré la plataforma con aplicaciones y APIs externas. Documenté las soluciones desarrolladas, utilicé Git y Docker a lo largo del desarrollo, y trabajé dentro de ciclos de entrega Ágiles para mantener y evolucionar las aplicaciones.</p>
      </div>

      <hr class="section-divider">

      <h2 id="educacion"><strong>Educación</strong></h2>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Licenciatura en Inteligencia Artificial y Robótica</h3>
          <span class="resume-date">2021 – 2025</span>
        </div>
        <div class="resume-company">Universidad Siglo XXI (R.M. n° 1142/2021)</div>
        <ul>
          <li><strong>Especialización:</strong> Inteligencia Artificial, Ciencia de Datos y Robótica.</li>
          <li><strong>Cursos relevantes:</strong> Machine Learning, Deep Learning e IA Generativa.</li>
        </ul>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Laboratorio de Intercambio en IA y Robótica</h3>
          <span class="resume-date">Nov 2024 – Nov 2025</span>
        </div>
        <div class="resume-company">Hochschule Furtwangen | Alemania</div>
        <ul>
          <li>Completé cursos de Machine Learning, Modelos Generativos Profundos, Visión por Computadora, Robótica y Sistemas de Microcontroladores.</li>
          <li>Mantuve un fuerte enfoque en el desarrollo de modelos de IA, el procesamiento de datos y la experimentación práctica en entornos basados en Jupyter.</li>
          <li>Colaboré en un entorno académico multicultural, fortaleciendo mis capacidades de investigación analítica y comunicación intercultural.</li>
          <li>Aprobé el examen de alemán nivel B2 y establecí contactos con profesionales y organizaciones activas en el ecosistema de IA de Alemania.</li>
        </ul>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Diploma de Técnico Electrónico</h3>
          <span class="resume-date">2009 – 2015</span>
        </div>
        <div class="resume-company">Instituto Técnico Industrial San Judas Tadeo</div>
        <ul>
          <li>Adquirí una base sólida en electrónica, sistemas aplicados y tecnologías de hardware.</li>
          <li>Desarrollé habilidades analíticas y de resolución de problemas orientadas a proyectos, fácilmente transferibles a la ingeniería de software y a la IT.</li>
        </ul>
      </div>

      <hr class="section-divider">

      <h2 id="activismo-es"><strong>Experiencia en Activismo Animal</strong></h2>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Referente de IA</h3>
          <span class="resume-date">2026 – Actualidad</span>
        </div>
        <div class="resume-company">Hack the Fork | París, Francia</div>
        <p class="resume-summary">Diseñé el marco de IA del hackathon y participé en la exploración y prueba del entorno de AWS; seré mentor de los equipos participantes en la definición del alcance de IA durante el evento.</p>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Voluntario DevOps</h3>
          <span class="resume-date">2019 – 2022</span>
        </div>
        <div class="resume-company">Difusión V | Voicot</div>
        <p class="resume-summary">Configuré y mantuve el hosting y el CI/CD de los sitios de la organización: <a href="http://difuv.com" target="_blank">difuv.com</a>, <a href="http://voicot.com" target="_blank">voicot.com</a> y <a href="http://difusionv.com" target="_blank">difusionv.com</a>.</p>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Fundador y organizador</h3>
          <span class="resume-date">2026 – Actualidad</span>
        </div>
        <div class="resume-company">We The Free | Angoulême, Francia</div>
        <p class="resume-summary">Fundé y dirijo la sede local: gestiono el presupuesto de materiales y las compras, organizo actividades de difusión y eventos sociales, y recluto activistas en la zona.</p>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Logística</h3>
          <span class="resume-date">2021 – 2022</span>
        </div>
        <div class="resume-company">Vegan Campout Argentina</div>
        <p class="resume-summary">Coordiné la logística de stands y las necesidades de proveedores para un evento de 2.000 asistentes, contribuí al programa, y gestioné un equipo de 20 voluntarios durante la jornada.</p>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Organizador</h3>
          <span class="resume-date">2019 – 2022</span>
        </div>
        <div class="resume-company">Buenos Aires Animal Save</div>
        <p class="resume-summary">Coorganicé vigilias frente a mataderos: abrí los eventos con una charla informativa a los asistentes, mantuve contacto con trabajadores de los mataderos, acompañé a los participantes durante las vigilias, y produje material audiovisual para redes sociales.</p>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Organizador</h3>
          <span class="resume-date">2018 – 2020</span>
        </div>
        <div class="resume-company">Anonymous for the Voiceless | Buenos Aires, Argentina</div>
        <p class="resume-summary">Creé y coordiné eventos Cube of Truth con entre 20 y 60 activistas: organicé equipos y materiales, y recibí y capacité a nuevos miembros.</p>
      </div>

      <hr class="section-divider">

      <h2 id="cursos-es"><strong>Cursos y certificaciones</strong></h2>
      <ul class="course-list">
        <li>
          <span class="course-meta">Sep 2026 • BlueDot Impact</span>
          <span class="course-title">Future of AI</span><br>
          Una introducción a lo que la IA puede hacer hoy, hacia dónde se dirige en la próxima década, y cómo empezar a contribuir a un futuro mejor.
        </li>
        <li>
          <span class="course-meta">2026 • Altruisme Efficace France</span>
          <span class="course-title">Talleres introductorios de Altruismo Eficaz</span><br>
          Exploración de estrategias de alto impacto y enfoques basados en evidencia para la resolución de problemas globales.
        </li>
        <li>
          <span class="course-meta">Abr 2025 • Mendix (ID de credencial 90924)</span>
          <span class="course-title">Mendix Developer Certificate</span><br>
          Certificación en desarrollo rápido de aplicaciones escalables low-code.
        </li>
        <li>
          <span class="course-meta">Semrush</span>
          <span class="course-title">Backlink Management Course con Greg Gifford</span><br>
          Estrategias avanzadas de SEO, construcción de enlaces y optimización de la presencia digital.
        </li>
        <li>
          <span class="course-meta">Swiss Financial Compliance</span>
          <span class="course-title">MLA Training Module</span><br>
          Formación en regulaciones de prevención de lavado de dinero y estricto cumplimiento financiero.
        </li>
        <li>
          <span class="course-meta">Udemy</span>
          <span class="course-title">Build ReactJS Applications</span><br>
          Desarrollo práctico de aplicaciones web frontend dinámicas basadas en componentes.
        </li>
        <li>
          <span class="course-meta">Jun 2020 • Coderhouse</span>
          <span class="course-title">Desarrollo Web</span><br>
          Fundamentos de arquitectura web moderna, diseño responsivo y despliegue.
        </li>
        <li>
          <span class="course-meta">2017</span>
          <span class="course-title">Hardware Descriptive Language for VHDL Development</span><br>
          Programación y diseño lógico para circuitos digitales complejos e integración FPGA.
        </li>
        <li>
          <span class="course-meta">Programación</span>
          <span class="course-title">Advanced C++ Programming and Modern Practices</span><br>
          Profundización en gestión de memoria, diseño orientado a objetos y programación de alto rendimiento.
        </li>
        <li>
          <span class="course-meta">2016</span>
          <span class="course-title">Curso Universitario en Microelectrónica</span><br>
          Diseño, principios de fabricación y aplicaciones prácticas de sistemas microelectrónicos.
        </li>
      </ul>

      <hr class="section-divider">

      <h2 id="habilidades"><strong>Habilidades</strong></h2>
      <div class="skills-compact">
        <p class="skill-line"><span class="skill-label">Producto:</span> Agile (Scrum/Kanban), gestión del backlog, roadmap de producto, investigación de usuarios, A/B testing, gestión de stakeholders, Jira, Confluence, Figma</p>
        <p class="skill-line"><span class="skill-label">IA y Datos:</span> Python (Pandas, Scikit-learn, PyTorch), NLP/NER, SQL, RAG, APIs de LLM (OpenAI, Anthropic), creación de agentes de IA, despliegue de LLM local</p>
        <p class="skill-line"><span class="skill-label">Ingeniería:</span> Docker, CI/CD, Git, React.js, TypeScript, REST APIs</p>
        <p class="skill-line"><span class="skill-label">Idiomas:</span> Español (nativo), Inglés (C1), Francés (C1), Alemán (B2), Chino (HSK3)</p>
      </div>

      <hr class="section-divider">

      <h2 id="referencias"><strong>Referencias</strong></h2>
      <table>
        <thead>
          <tr><th>Nombre</th><th>Rol</th><th>Contacto</th></tr>
        </thead>
        <tbody>
          <tr>
            <td>Andi Gjonej</td>
            <td>CEO, Union Financial Corners | Ginebra, Suiza</td>
            <td>Disponible a solicitud<br><a href="docs/assets/Certificat_de_travail.pdf" download>Descargar Certificado de trabajo</a></td>
          </tr>
          <tr>
            <td>Franco Cellone</td>
            <td><a href="https://www.linkedin.com/company/15223804/" target="_blank">Coordinador de Registro y Análisis de la Información</a><br><a href="https://www.linkedin.com/company/15223804/" target="_blank">Gobierno de Córdoba</a></td>
            <td>Disponible a solicitud</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</div>
