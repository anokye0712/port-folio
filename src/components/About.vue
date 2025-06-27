<script setup>

</script>

<template>
  <section id="about" class="about-me-section">
    <div class="container">
      <h2 class="section-title">About Me</h2>
      <div class="about-content">
        <p class="summary-text">
          Highly accomplished and results-driven Geomatic Engineering professional with over five years of experience specializing in geospatial image processing, seabed modeling, computer vision, and geospatial AI. Proficient in MATLAB, Python, Julia, ArcGIS, QGIS, and SAGA GIS. Demonstrated research contributions include two published papers and one co-authored paper. Holds an MPhil in Marine Survey and Mapping from Shandong University of Science and Technology (June 2023), with research focused on applying deep learning and machine learning for advanced seabed sediment classification.
        </p>

        <div class="general-skills">
          <h3>General Skills</h3>
          <ul class="skills-list">
            <li class="skill-item">
              <span class="icon">✨</span> Target-setting and monitoring
            </li>
            <li class="skill-item">
              <span class="icon">🤝</span> Proven leadership and good human relations
            </li>
            <li class="skill-item">
              <span class="icon">🗣️</span> Excellent verbal communication skills
            </li>
            <li class="skill-item">
              <span class="icon">💡</span> Self-motivated and good team player
            </li>
            <li class="skill-item">
              <span class="icon">💪</span> Familiar with working under challenging situations and easily switch positions with little or no supervision
            </li>
          </ul>
        </div>
      </div>
    </div>
  </section>

</template>

<style scoped>
/* Scoped styles for the AboutMeSection component */
.about-me-section {
  padding: 80px 0;
  background-color: #f8f9fa; /* Light background for contrast */
  color: #333;
}

.container {
  max-width: 1000px;
  margin: 0 auto;
  padding: 0 20px;
}

.section-title {
  font-family: var(--header-font);
  font-size: 3em;
  font-weight: 700;
  text-align: center;
  margin-bottom: 60px;
  color: var(--background-dark); /* Darker color for titles */
  position: relative;
}

.section-title::after {
  content: '';
  display: block;
  width: 80px;
  height: 4px;
  background-color: var(--accent-color);
  margin: 20px auto 0;
  border-radius: 2px;
}

.about-content {
  display: flex;
  flex-direction: column;
  gap: 40px;
}

.summary-text {
  font-family: var(--body-font);
  font-size: 1.2em;
  line-height: 1.8;
  text-align: justify;
  background-color: #fff;
  padding: 30px;
  border-radius: 10px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
}

.general-skills {
  background-color: #fff;
  padding: 30px;
  border-radius: 10px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
}

.general-skills h3 {
  font-family: var(--header-font);
  font-size: 1.8em;
  margin-bottom: 25px;
  color: var(--primary-color);
  text-align: center;
}

.skills-list {
  list-style: none;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 20px;
}

.skill-item {
  font-family: var(--body-font);
  font-size: 1.1em;
  display: flex;
  align-items: center;
  padding: 15px 20px;
  background-color: #e9ecef;
  border-radius: 8px;
  transition: transform 0.3s ease, background-color 0.3s ease;
  cursor: default; /* Not clickable, but shows hover */
}

.skill-item:hover {
  transform: translateY(-5px);
  background-color: #dee2e6;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
}

.skill-item .icon {
  margin-right: 15px;
  font-size: 1.5em;
  line-height: 1; /* Align icon vertically */
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .about-me-section {
    padding: 60px 0;
  }
  .section-title {
    font-size: 2.5em;
    margin-bottom: 40px;
  }
  .summary-text {
    font-size: 1.1em;
    padding: 25px;
  }
  .general-skills h3 {
    font-size: 1.6em;
    margin-bottom: 20px;
  }
  .skills-list {
    grid-template-columns: 1fr; /* Stack skills on small screens */
  }
  .skill-item {
    font-size: 1em;
    padding: 12px 15px;
  }
}

@media (max-width: 480px) {
  .about-me-section {
    padding: 40px 0;
  }
  .section-title {
    font-size: 2em;
    margin-bottom: 30px;
  }
  .summary-text {
    font-size: 1em;
    padding: 20px;
  }
  .general-skills h3 {
    font-size: 1.4em;
  }
}
</style>
