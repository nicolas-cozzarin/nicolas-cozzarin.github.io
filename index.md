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
    margin-bottom: 8px;
    font-size: 0.95em;
  }
  .resume-summary {
    margin-top: 0;
    margin-bottom: 12px;
    font-size: 0.95em;
    color: #555;
    line-height: 1.5;
  }
  .resume-item ul {
    margin-top: 0;
    padding-left: 20px;
    font-size: 0.95em;
    color: #333;
  }
  .resume-item ul li {
    margin-bottom: 8px;
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
    document.getElementById('btn-fr').className = lang === 'fr' ? 'lang-btn' : 'lang-btn';
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
        <h2 id="about-me"><strong>About me</strong></h2>
        <p>I am an IT Project Manager and Product Owner with 10 years of experience. I specialize in Agile methodologies (Scrum/Kanban) and Software Development Life Cycle (SDLC) management. I bridge the gap between complex technical models and practical, effective business solutions.</p>
        <p>Having successfully completed my BSc in Artificial Intelligence & Robotics, my current focus is on AI compliance, AI ethics and alignment, and seamlessly integrating AI and automations into companies to make their processes significantly more effective.</p>
      </div>
    </div>

    <div class="full-width-section">
      <hr class="section-divider">

      <h2 id="professional-experience"><strong>Professional experience</strong></h2>
      
      <div class="resume-item">
        <div class="resume-header">
          <h3>IT Project Manager / Product Owner</h3>
          <span class="resume-date">Oct 2022 – Present</span>
        </div>
        <div class="resume-company">Union of Financial Corners | Geneva, Switzerland</div>
        <p class="resume-summary">Directed the end-to-end delivery of software projects across Europe and Latin America, translating complex requirements into actionable tasks and managing agile workflows to ensure on-time, high-quality releases.</p>
        <ul>
          <li><strong>Problem:</strong> Fragmented development cycles and unclear requirements were delaying time-to-market for trading platforms.</li>
          <li><strong>Scope:</strong> Directed the full SDLC for high-performance cryptocurrency exchange platforms, translating complex business needs into clear, actionable technical roadmaps.</li>
          <li><strong>Result:</strong> Optimized Agile workflows (Scrum/Kanban), which successfully increased the development team's velocity by 20% and ensured zero-downtime releases fully compliant with financial industry standards.</li>
        </ul>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>AI Product Owner (Fixed-term contract)</h3>
          <span class="resume-date">2025</span>
        </div>
        <div class="resume-company">Security Forces Disciplinary Control System | Cordoba, Argentina</div>
        <p class="resume-summary">Led the implementation of an NLP-based automated text classification system to streamline legal case reviews while ensuring strict data privacy and security compliance.</p>
        <ul>
          <li><strong>Problem:</strong> An overwhelming volume of manual legal case reviews was causing severe operational bottlenecks.</li>
          <li><strong>Scope:</strong> Managed the full implementation of a robust NLP model for automated text classification and defined strict data anonymization protocols for compliance.</li>
          <li><strong>Result:</strong> Bridged the gap between data scientists and legal stakeholders, successfully accelerating case processing time by 40% while ensuring 100% privacy compliance.</li>
        </ul>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Front end Developer</h3>
          <span class="resume-date">Feb 2019 – Dec 2022</span>
        </div>
        <div class="resume-company">FlyDevs | USA (Remote)</div>
        <p class="resume-summary">Delivered high-quality web applications using React.js and TypeScript, working closely with stakeholders and design teams to align technical execution with client requirements in an agile environment.</p>
        <ul>
          <li><strong>Problem:</strong> Misalignment between client expectations and engineering outputs frequently led to costly feature rework.</li>
          <li><strong>Scope:</strong> Owned the requirements gathering process across multiple concurrent projects, translating ambiguous business needs into highly detailed functional specifications.</li>
          <li><strong>Result:</strong> Streamlined stakeholder communication, reducing feature rework by 30% and ensuring technical deliverables consistently met precise business objectives on schedule.</li>
        </ul>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Lead Quality Assurance Analyst</h3>
          <span class="resume-date">Mar 2017 – Dec 2019</span>
        </div>
        <div class="resume-company">Charly Inc. | Canada (Remote)</div>
        <p class="resume-summary">Managed QA processes and led a distributed remote team, designing comprehensive test strategies that significantly improved defect detection and overall software quality.</p>
        <ul>
          <li><strong>Problem:</strong> High rates of post-release defects were damaging user trust and increasing the product's technical debt.</li>
          <li><strong>Scope:</strong> Architected and spearheaded comprehensive end-to-end testing strategies, orchestrating efforts across global remote software development teams.</li>
          <li><strong>Result:</strong> Streamlined delivery pipelines and automated core test suites, successfully decreasing critical post-release bugs by 50% and vastly improving overall product stability.</li>
        </ul>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Python Backend Developer - Odoo</h3>
          <span class="resume-date">Feb 2015 – Jun 2016</span>
        </div>
        <div class="resume-company">E-MIPS | Buenos Aires, Argentina</div>
        <p class="resume-summary">Engineered and customized backend ERP modules using Python and Odoo, integrating third-party APIs to automate and optimize core business workflows for clients.</p>
        <ul>
          <li><strong>Problem:</strong> Legacy client systems lacked the custom integrations required for modern enterprise resource planning (ERP).</li>
          <li><strong>Scope:</strong> Engineered, customized, and maintained complex ERP modules using Python, working directly with cross-functional teams to modernize infrastructure.</li>
          <li><strong>Result:</strong> Delivered scalable, tailored backend solutions that automated key manual data entry tasks, saving clients an average of 15 hours per week in administrative overhead.</li>
        </ul>
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

      <h2 id="courses"><strong>Courses & certifications</strong></h2>
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

      <h2 id="skills"><strong>Skills</strong></h2>
      <div class="skills-container">

        <div class="skill-category">Product & Management</div>
        <div class="skills-grid">
          <div class="skill-row"><span class="skill-name">Agile (Scrum/Kanban)</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">SDLC</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Backlog Management</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">User Stories</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Jira</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Confluence</span> <span class="skill-stars"><span class="filled">★★★</span>★★</span></div>
          <div class="skill-row"><span class="skill-name">Azure DevOps</span> <span class="skill-stars"><span class="filled">★★</span>★★★</span></div>
          <div class="skill-row"><span class="skill-name">Figma</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">Miro</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">Balsamiq</span> <span class="skill-stars"><span class="filled">★★★</span>★★</span></div>
          <div class="skill-row"><span class="skill-name">Apple / MacOS</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Github / Gitlab</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Scrum / Agile</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">SEO</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">Product Roadmap</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">Backlog Refinement</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">User Research</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">A/B Testing</span> <span class="skill-stars"><span class="filled">★★★</span>★★</span></div>
          <div class="skill-row"><span class="skill-name">Stakeholder Management</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
        </div>

        <div class="skill-category">Languages</div>
        <div class="skills-grid">
          <div class="skill-row"><span class="skill-name">Spanish (Native)</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">English (C1)</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">French (C1)</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">German</span> <span class="skill-stars"><span class="filled">★★</span>★★★</span></div>
          <div class="skill-row"><span class="skill-name">Chinese (HSK3)</span> <span class="skill-stars"><span class="filled">★★</span>★★★</span></div>
        </div>
        
        <div class="skill-category">AI & Automation Tools</div>
        <div class="skills-grid">
          <div class="skill-row"><span class="skill-name">REST APIs</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">n8n</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Make.com</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Zapier</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Retrieval-Augmented Generation (RAG)</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">AI Agent Building</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">OpenAI API</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Anthropic Claude</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Local LLM Deployment</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">AI-Assisted Coding (Cursor, Replit)</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
        </div>

        <div class="skill-category">Technical & Data</div>
        <div class="skills-grid">
          <div class="skill-row"><span class="skill-name">Python</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Pandas</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">Scikit-learn</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">PyTorch</span> <span class="skill-stars"><span class="filled">★★★</span>★★</span></div>
          <div class="skill-row"><span class="skill-name">NLP</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">NER</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">SQL</span> <span class="skill-stars"><span class="filled">★★★</span>★★</span></div>
          <div class="skill-row"><span class="skill-name">React.js</span> <span class="skill-stars"><span class="filled">★★</span>★★★</span></div>
          <div class="skill-row"><span class="skill-name">TypeScript</span> <span class="skill-stars"><span class="filled">★★★</span>★★</span></div>
          <div class="skill-row"><span class="skill-name">Git</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">Docker</span> <span class="skill-stars"><span class="filled">★★★</span>★★</span></div>
          <div class="skill-row"><span class="skill-name">CI/CD</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
        </div>

      </div>
      
      <hr class="section-divider">

      <h2><strong>Projects & insights</strong></h2>
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

      <hr class="section-divider">

      <h2 id="volunteer"><strong>Volunteer Experience, Community Involvement</strong></h2>
      <table>
        <thead>
          <tr><th>Date</th><th>Role</th></tr>
        </thead>
        <tbody>
          <tr><td>2026 - Present</td><td>AI Representative: Supporting local teams on AI scoping for <strong>Hack the Fork</strong> hackathon (Paris)</td></tr>
          <tr><td>2026 - Current</td><td>Organizer for <strong>We The Free</strong> group in France</td></tr>
          <tr><td>2019 - 2022</td><td>Organizer of Buenos Aires <strong>Animal Save</strong></td></tr>
          <tr><td>2020 - 2022</td><td>Organizer of Buenos Aires <strong>Anonymous for the Voiceless</strong></td></tr>
          <tr><td>2021 - 2022</td><td>Organizer of Vegan Campout Argentina</td></tr>
        </tbody>
      </table>
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
        <h2 id="a-propos"><strong>À propos</strong></h2>
        <p>Product Owner et Chef de Projet IT avec 10 ans d'expérience. Je suis spécialiste des méthodologies Agiles (Scrum/Kanban) et du pilotage du cycle de vie des logiciels (SDLC). Je fais le pont entre les modèles techniques complexes et la création de solutions métiers concrètes et performantes.</p>
        <p>Ayant obtenu mon Bachelor en Intelligence Artificielle et Robotique, je me concentre actuellement sur la conformité de l'IA, l'éthique et l'alignement des modèles, ainsi que sur l'intégration de l'IA et de l'automatisation en entreprise pour rendre les processus significativement plus efficaces.</p>
      </div>
    </div>

    <div class="full-width-section">
      <hr class="section-divider">

      <h2 id="experiences-professionnelles"><strong>Expérience professionnelle</strong></h2>
      
      <div class="resume-item">
        <div class="resume-header">
          <h3>Chef de Projet IT / Product Owner</h3>
          <span class="resume-date">Oct 2022 – Aujourd'hui</span>
        </div>
        <div class="resume-company">Union of Financial Corners | Genève, Suisse</div>
        <p class="resume-summary">Direction complète de la livraison de projets logiciels à travers l'Europe et l'Amérique latine, traduisant des exigences complexes en tâches concrètes et gérant les flux de travail agiles pour assurer des lancements ponctuels et de haute qualité.</p>
        <ul>
          <li><strong>Problème :</strong> Des cycles de développement fragmentés et des exigences floues retardaient la mise sur le marché des plateformes de trading.</li>
          <li><strong>Périmètre :</strong> Direction complète du cycle de vie (SDLC) de plateformes d'échange de cryptomonnaies à haute performance, traduisant des besoins commerciaux complexes en feuilles de route techniques claires.</li>
          <li><strong>Résultat :</strong> Optimisation des processus Agiles (Scrum/Kanban), entraînant une augmentation de 20% de la vélocité de l'équipe de développement et assurant des déploiements sans interruption respectant les normes financières.</li>
        </ul>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>AI Product Owner (CDD)</h3>
          <span class="resume-date">2025</span>
        </div>
        <div class="resume-company">Système de Contrôle Disciplinaire des Forces de Sécurité | Cordoba, Argentine</div>
        <p class="resume-summary">Pilotage de la mise en œuvre d'un système de classification de texte automatisé basé sur le NLP pour optimiser l'examen des dossiers juridiques tout en garantissant la stricte confidentialité des données.</p>
        <ul>
          <li><strong>Problème :</strong> Un volume écrasant d'examens manuels de dossiers juridiques causait de graves goulots d'étranglement opérationnels.</li>
          <li><strong>Périmètre :</strong> Pilotage de l'implémentation complète d'un modèle NLP pour la classification automatisée et définition de protocoles stricts d'anonymisation des données.</li>
          <li><strong>Résultat :</strong> Alignement réussi entre data scientists et experts juridiques, accélérant le traitement des dossiers de 40% tout en garantissant une conformité totale à la vie privée.</li>
        </ul>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Développeur Front-End</h3>
          <span class="resume-date">Fév 2019 – Déc 2022</span>
        </div>
        <div class="resume-company">FlyDevs | USA (À distance)</div>
        <p class="resume-summary">Livraison d'applications web de haute qualité avec React.js et TypeScript, en étroite collaboration avec les parties prenantes et les équipes de conception pour aligner l'exécution technique sur les besoins des clients.</p>
        <ul>
          <li><strong>Problème :</strong> Le décalage entre les attentes des clients et les livrables d'ingénierie entraînait des retouches coûteuses de fonctionnalités.</li>
          <li><strong>Périmètre :</strong> Gestion du recueil des besoins métiers sur plusieurs projets simultanés, traduisant des demandes ambiguës en spécifications fonctionnelles hautement détaillées.</li>
          <li><strong>Résultat :</strong> Fluidification de la communication entre les parties prenantes, réduisant les retouches de 30% et garantissant que les livrables techniques atteignent systématiquement les objectifs commerciaux dans les délais.</li>
        </ul>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Lead QA Analyst</h3>
          <span class="resume-date">Mar 2017 – Déc 2019</span>
        </div>
        <div class="resume-company">Charly Inc. | Canada (À distance)</div>
        <p class="resume-summary">Gestion des processus d'assurance qualité et direction d'une équipe répartie à distance, en concevant des stratégies de test complètes qui ont considérablement amélioré la détection des anomalies et la qualité globale des logiciels.</p>
        <ul>
          <li><strong>Problème :</strong> Un taux élevé d'anomalies post-lancement affectait la confiance des utilisateurs et augmentait la dette technique du produit.</li>
          <li><strong>Périmètre :</strong> Conception et direction de stratégies complètes de tests de bout en bout, coordonnant efficacement des équipes de développement à distance réparties à l'international.</li>
          <li><strong>Résultat :</strong> Amélioration des pipelines de livraison et automatisation des tests clés, réduisant les bugs critiques post-lancement de 50% et renforçant massivement la stabilité globale du produit.</li>
        </ul>
      </div>

      <div class="resume-item">
        <div class="resume-header">
          <h3>Développeur Backend Python - Odoo</h3>
          <span class="resume-date">Fév 2015 – Juin 2016</span>
        </div>
        <div class="resume-company">E-MIPS | Buenos Aires, Argentine</div>
        <p class="resume-summary">Conception et personnalisation de modules ERP backend avec Python et Odoo, en intégrant des API tierces pour automatiser et optimiser les processus métiers clés des clients.</p>
        <ul>
          <li><strong>Problème :</strong> Les systèmes clients existants manquaient des intégrations personnalisées nécessaires à la gestion moderne des ressources de l'entreprise (ERP).</li>
          <li><strong>Périmètre :</strong> Développement, personnalisation et maintenance de modules ERP complexes en Python, en collaboration directe avec des équipes pluridisciplinaires pour moderniser l'infrastructure.</li>
          <li><strong>Résultat :</strong> Livraison de solutions backend scalables qui ont automatisé la saisie manuelle de données, faisant gagner aux clients en moyenne 15 heures par semaine de charge administrative.</li>
        </ul>
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

      <h2 id="cours"><strong>Cours & certifications</strong></h2>
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

      <h2 id="competences"><strong>Compétences</strong></h2>
      <div class="skills-container">

        <div class="skill-category">Produit & Management</div>
        <div class="skills-grid">
          <div class="skill-row"><span class="skill-name">Agile (Scrum/Kanban)</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">SDLC</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Gestion du Backlog</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">User Stories</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Jira</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Confluence</span> <span class="skill-stars"><span class="filled">★★★</span>★★</span></div>
          <div class="skill-row"><span class="skill-name">Azure DevOps</span> <span class="skill-stars"><span class="filled">★★</span>★★★</span></div>
          <div class="skill-row"><span class="skill-name">Figma</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">Miro</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">Balsamiq</span> <span class="skill-stars"><span class="filled">★★★</span>★★</span></div>
          <div class="skill-row"><span class="skill-name">Apple / MacOS</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Github / Gitlab</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Scrum / Agile</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">SEO</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">Roadmap Produit</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">Affinage du Backlog</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Recherche Utilisateur</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">A/B Testing</span> <span class="skill-stars"><span class="filled">★★★</span>★★</span></div>
          <div class="skill-row"><span class="skill-name">Gestion des Parties Prenantes</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
        </div>

        <div class="skill-category">Langues</div>
        <div class="skills-grid">
          <div class="skill-row"><span class="skill-name">Espagnol (Natif)</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Anglais (C1)</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">Français (C1)</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">Allemand</span> <span class="skill-stars"><span class="filled">★★</span>★★★</span></div>
          <div class="skill-row"><span class="skill-name">Chinois (HSK3)</span> <span class="skill-stars"><span class="filled">★★</span>★★★</span></div>
        </div>
        
        <div class="skill-category">Outils d'IA & Automatisation</div>
        <div class="skills-grid">
          <div class="skill-row"><span class="skill-name">REST APIs</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">n8n</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Make.com</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Zapier</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Retrieval-Augmented Generation (RAG)</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Création d'Agents IA</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">OpenAI API</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Anthropic Claude</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Déploiement LLM Local</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Code Assisté par IA (Cursor, Replit)</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
        </div>

        <div class="skill-category">Tech & Data</div>
        <div class="skills-grid">
          <div class="skill-row"><span class="skill-name">Python</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">Pandas</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">Scikit-learn</span> <span class="skill-stars"><span class="filled">★★★★★</span></span></div>
          <div class="skill-row"><span class="skill-name">PyTorch</span> <span class="skill-stars"><span class="filled">★★★</span>★★</span></div>
          <div class="skill-row"><span class="skill-name">NLP</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">NER</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">SQL</span> <span class="skill-stars"><span class="filled">★★★</span>★★</span></div>
          <div class="skill-row"><span class="skill-name">React.js</span> <span class="skill-stars"><span class="filled">★★</span>★★★</span></div>
          <div class="skill-row"><span class="skill-name">TypeScript</span> <span class="skill-stars"><span class="filled">★★★</span>★★</span></div>
          <div class="skill-row"><span class="skill-name">Git</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
          <div class="skill-row"><span class="skill-name">Docker</span> <span class="skill-stars"><span class="filled">★★★</span>★★</span></div>
          <div class="skill-row"><span class="skill-name">CI/CD</span> <span class="skill-stars"><span class="filled">★★★★</span>★</span></div>
        </div>

      </div>
      
      <hr class="section-divider">

      <h2><strong>Projets & insights</strong></h2>
      <ul class="post-list">
        {%- for post in site.posts -%}
        <li>
          <span class="post-meta">{{ post.date | date: "%-d %b %Y" }}</span>
          <h3>
            <a class="post-link" href="{{ post.url | relative_url }}">
              {{ post.title | escape }}
            </a>
          </h3>
        </li>
        {%- endfor -%}
      </ul>

      <hr class="section-divider">

      <h2 id="benevolat"><strong>Expérience de Bénévolat, Implication Communautaire</strong></h2>
      <table>
        <thead>
          <tr><th>Date</th><th>Rôle</th></tr>
        </thead>
        <tbody>
          <tr><td>2026 - en cours</td><td>Référent IA : accompagnement des équipes locales sur le cadrage IA de leur hackathon <strong>Hack the Fork</strong> (Paris)</td></tr>
          <tr><td>2026 - en cours</td><td>Organisateur pour le groupe <strong>We The Free</strong> en France</td></tr>
          <tr><td>2019 - 2022</td><td>Organisateur de Buenos Aires <strong>Animal Save</strong></td></tr>
          <tr><td>2020 - 2022</td><td>Organisateur de Buenos Aires <strong>Anonymous for the Voiceless</strong></td></tr>
          <tr><td>2021 - 2022</td><td>Organisateur de Vegan Campout Argentina</td></tr>
        </tbody>
      </table>
    </div>
  </div>
</div>
