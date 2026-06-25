---
layout: page
icon: fas fa-folder-open
order: 4
title: Blog
---

<link rel="stylesheet" href="{{ '/assets/css/custom-theme.css' | relative_url }}">

<div class="folder-intro">
~/anas-portfolio/blog — click a folder to open it and see the articles inside.
</div>

<div class="folder-grid">

  <div class="folder-card" style="--card-accent: var(--accent-featured);">
    <span class="folder-path">~/featured</span>
    <h3>Portfolio Purpose</h3>
    <p>Why this portfolio exists, and how it tracks my Computer Engineering journey one semester at a time.</p>
    <div class="folder-meta">
      <span class="folder-pill">1 Article</span>
      <span class="folder-pill">Featured</span>
    </div>
    <div class="folder-articles">
      <a href="{{ '/posts/introduction/' | relative_url }}">About Me</a>
    </div>
  </div>

  <div class="folder-card" style="--card-accent: var(--accent-pf);">
    <span class="folder-path">~/programming-fundamentals</span>
    <h3>Programming Fundamentals</h3>
    <p>Where it all started — Python basics, problem solving, and my first steps into C# and OOP.</p>
    <div class="folder-meta">
      <span class="folder-pill">3 Articles</span>
      <span class="folder-pill">Python · C#</span>
    </div>
    <div class="folder-articles">
      <a href="{{ '/posts/programming_fundamentals/' | relative_url }}">Programming Fundamentals</a>
      <a href="{{ '/posts/problem_solving_through_programming/' | relative_url }}">Problem Solving Through Programming</a>
      <a href="{{ '/posts/oop/' | relative_url }}">Object-Oriented Programming</a>
    </div>
  </div>

  <div class="folder-card" style="--card-accent: var(--accent-db);">
    <span class="folder-path">~/database-systems</span>
    <h3>Database Systems</h3>
    <p>Designing schemas, writing SQL, and learning to think in ER diagrams before touching a single table.</p>
    <div class="folder-meta">
      <span class="folder-pill">3 Articles</span>
      <span class="folder-pill">MySQL</span>
    </div>
    <div class="folder-articles">
      <a href="{{ '/posts/database_systems/' | relative_url }}">Database Systems</a>
      <a href="{{ '/posts/sql/' | relative_url }}">SQL</a>
      <a href="{{ '/posts/er_diagram/' | relative_url }}">ER Diagrams</a>
    </div>
  </div>

  <div class="folder-card" style="--card-accent: var(--accent-ml);">
    <span class="folder-path">~/machine-learning</span>
    <h3>Machine Learning &amp; AI</h3>
    <p>My first real models — from a Walmart sales predictor to an insurance claim classifier.</p>
    <div class="folder-meta">
      <span class="folder-pill">2 Articles</span>
      <span class="folder-pill">Python · sklearn</span>
    </div>
    <div class="folder-articles">
      <a href="{{ '/posts/machine_learning_experience/' | relative_url }}">My Machine Learning Experience</a>
      <a href="{{ '/posts/insurance_claim_prediction/' | relative_url }}">Insurance Claim Prediction</a>
    </div>
  </div>

  <div class="folder-card" style="--card-accent: var(--accent-dld);">
    <span class="folder-path">~/digital-logic-design</span>
    <h3>Digital Logic Design</h3>
    <p>Where software stops and hardware begins — gates, circuits, and Microwind simulations.</p>
    <div class="folder-meta">
      <span class="folder-pill">1 Article</span>
      <span class="folder-pill">Microwind</span>
    </div>
    <div class="folder-articles">
      <a href="{{ '/posts/digital_logic_design/' | relative_url }}">Digital Logic Design</a>
    </div>
  </div>

  <div class="folder-card" style="--card-accent: var(--accent-journey);">
    <span class="folder-path">~/my-journey</span>
    <h3>My Journey &amp; Reflection</h3>
    <p>The non-technical side of the semester — challenges, labs, exams, and what comes next.</p>
    <div class="folder-meta">
      <span class="folder-pill">6 Articles</span>
      <span class="folder-pill">Reflection</span>
    </div>
    <div class="folder-articles">
      <a href="{{ '/posts/my_university_journey/' | relative_url }}">My University Journey</a>
      <a href="{{ '/posts/semester_challenges/' | relative_url }}">Semester Challenges</a>
      <a href="{{ '/posts/practical_labs/' | relative_url }}">Practical Labs</a>
      <a href="{{ '/posts/exams_and_assignments/' | relative_url }}">Exams &amp; Assignments</a>
      <a href="{{ '/posts/github_digital_footprint/' | relative_url }}">Building My GitHub Digital Footprint</a>
      <a href="{{ '/posts/future_goals/' | relative_url }}">Future Goals</a>
    </div>
  </div>

</div>

<script>
document.addEventListener('DOMContentLoaded', function () {
  document.querySelectorAll('.folder-card').forEach(function (card) {
    card.style.cursor = 'pointer';
    card.addEventListener('click', function (e) {
      if (e.target.tagName.toLowerCase() === 'a') return; // let article links navigate normally
      document.querySelectorAll('.folder-card').forEach(function (c) {
        if (c !== card) c.classList.remove('is-open');
      });
      card.classList.toggle('is-open');
    });
  });
});
</script>
