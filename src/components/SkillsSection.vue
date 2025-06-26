<script setup>
</script>

<template>
  <section id="skills" class="skills-section">
    <div class="container">
      <h2 class="section-title">Technical Skills</h2>

      <div class="skills-grid">
        <div class="skill-category">
          <h3 class="category-title">Programming Languages</h3>
          <div class="category-items">
            <div class="skill-card">
              <span class="skill-icon">🐍</span>
              <p class="skill-name">Python</p>
            </div>
            <div class="skill-card">
              <span class="skill-icon">⚛️</span>
              <p class="skill-name">Julia</p>
            </div>
            <div class="skill-card">
              <span class="skill-icon">📊</span>
              <p class="skill-name">MATLAB</p>
            </div>
            <div class="skill-card">
              <span class="skill-icon">📄</span>
              <p class="skill-name">JavaScript</p>
            </div>
          </div>
        </div>

        <div class="skill-category">
          <h3 class="category-title">GIS Software</h3>
          <div class="category-items">
            <div class="skill-card">
              <span class="skill-icon">🌐</span>
              <p class="skill-name">QGIS</p>
            </div>
            <div class="skill-card">
              <span class="skill-icon">⛰️</span>
              <p class="skill-name">SAGA GIS</p>
            </div>
          </div>
        </div>

        <div class="skill-category">
          <h3 class="category-title">Other Tools</h3>
          <div class="category-items">
            <div class="skill-card">
              <span class="skill-icon">🌿</span>
              <p class="skill-name">Leaflet</p>
            </div>
            <div class="skill-card">
              <span class="skill-icon">📏</span>
              <p class="skill-name">RESTful API (FastAPI)</p>
            </div>
            <div class="skill-card">
              <span class="skill-icon">✍️</span>
              <p class="skill-name">VUE</p>
            </div>
            <div class="skill-card">
              <span class="skill-icon">🌎</span>
              <p class="skill-name">Mapbox</p>
            </div>
            <div class="skill-card">
              <span class="skill-icon">🌆</span>
              <p class="skill-name">Giro 3D</p>
            </div>
            <div class="skill-card">
              <span class="skill-icon">💻</span>
              <p class="skill-name">Geoapify</p>
            </div>
            <div class="skill-card">
              <span class="skill-icon">🧠</span>
              <p class="skill-name">FastAI</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* Scoped styles for the SkillsSection component */
.skills-section {
  padding: 80px 0;
  background-color: var(--background-dark); /* Dark background for contrast */
  color: var(--text-light); /* Light text for dark background */
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
  color: var(--text-light); /* Title color for dark background */
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

.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 40px;
}

.skill-category {
  background-color: #2a2a40; /* Slightly lighter dark background for categories */
  border-radius: 12px;
  padding: 30px;
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.4);
  transition: transform 0.3s ease;
}

.skill-category:hover {
  transform: translateY(-8px);
}

.category-title {
  font-family: var(--header-font);
  font-size: 2em;
  font-weight: 600;
  text-align: center;
  margin-bottom: 30px;
  color: var(--primary-color); /* Highlight category titles */
}

.category-items {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(120px, 1fr)); /* Adjust for smaller cards */
  gap: 20px;
  justify-content: center; /* Center items if they don't fill the grid */
}

.skill-card {
  background-color: #3e3e5c; /* Darker background for individual skill cards */
  border-radius: 10px;
  padding: 20px 15px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  transition: transform 0.3s ease, background-color 0.3s ease, box-shadow 0.3s ease;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
  cursor: default; /* Not interactive, but indicates a discrete element */
}

.skill-card:hover {
  transform: translateY(-5px) scale(1.03);
  background-color: #4a4a70;
  box-shadow: 0 6px 15px rgba(0, 0, 0, 0.3);
}

.skill-icon {
  font-size: 3em; /* Larger icons */
  margin-bottom: 10px;
  line-height: 1; /* Ensures proper vertical alignment */
}

.skill-name {
  font-family: var(--body-font);
  font-size: 1.1em;
  font-weight: 600;
  color: var(--text-light);
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .skills-section {
    padding: 60px 0;
  }
  .section-title {
    font-size: 2.5em;
    margin-bottom: 40px;
  }
  .skills-grid {
    grid-template-columns: 1fr; /* Stack categories on smaller screens */
    gap: 30px;
  }
  .category-title {
    font-size: 1.8em;
    margin-bottom: 25px;
  }
  .category-items {
    grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
    gap: 15px;
  }
  .skill-card {
    padding: 15px 10px;
  }
  .skill-icon {
    font-size: 2.5em;
  }
  .skill-name {
    font-size: 1em;
  }
}

@media (max-width: 480px) {
  .skills-section {
    padding: 40px 0;
  }
  .section-title {
    font-size: 2em;
    margin-bottom: 30px;
  }
  .skill-category {
    padding: 20px;
  }
  .category-title {
    font-size: 1.5em;
    margin-bottom: 20px;
  }
  .category-items {
    gap: 10px;
  }
  .skill-icon {
    font-size: 2em;
  }
  .skill-name {
    font-size: 0.9em;
  }
}
</style>
