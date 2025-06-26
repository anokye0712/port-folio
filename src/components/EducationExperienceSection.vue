<template>
    <section id="education-experience" class="edu-exp-section">
      <div class="container">
        <h2 class="section-title">Education & Experience</h2>
  
        <div class="timeline">
          <h3 class="timeline-category-title">Education</h3>
          <div v-for="edu in education" :key="edu.id" class="timeline-item">
            <div class="timeline-dot"></div>
            <div class="timeline-content">
              <h4>{{ edu.degree }}</h4>
              <p class="institution">{{ edu.institution }}</p>
              <p class="dates">{{ edu.period }}</p>
              <p class="description" v-if="edu.researchFocus">
                Research Focus: {{ edu.researchFocus }}
              </p>
            </div>
          </div>
  
          <h3 class="timeline-category-title">Experience</h3>
          <div v-for="exp in experience" :key="exp.id" class="timeline-item">
            <div class="timeline-dot"></div>
            <div class="timeline-content">
              <h4>{{ exp.position }}</h4>
              <p class="institution">{{ exp.company }}</p>
              <p class="dates">{{ exp.period }}</p>
              <ul class="responsibilities" v-if="exp.responsibilities && exp.responsibilities.length">
                <li v-for="(res, index) in exp.responsibilities" :key="index">{{ res }}</li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </section>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  // Dummy data for Education (will come from FastAPI later)
  const education = ref([
    {
      id: 1,
      degree: "M.Phil. in Geomatics Engineering",
      institution: "College of Geodesy and Geomatic, Shandong University of Science and Technology",
      period: "September 2018 - June 2023",
      researchFocus: "Utilizing deep learning and machine learning methods for seabed sediment classification."
    },
    {
      id: 2,
      degree: "B.Sc. in Geomatic Engineering",
      institution: "Department of Geomatic Engineering, Kwame Nkrumah University of Science and Technology",
      period: "September 2013 - June 2017"
    }
  ]);
  
  // Dummy data for Experience (will come from FastAPI later)
  const experience = ref([
    {
      id: 1,
      position: "Geomatic Engineer (Internship)",
      company: "Ghana Highway Authority",
      period: "September 2017 - August 2018",
      responsibilities: [
        "Assisted in topographic surveys for road design and construction.",
        "Participated in data collection and processing using various survey instruments.",
        "Contributed to GIS mapping and analysis for infrastructure projects."
      ]
    }
  ]);
  </script>
  
<style scoped>
  /* Scoped styles for the EducationExperienceSection component */
  .edu-exp-section {
    padding: 80px 0;
    background-color: #f8f9fa; /* Light background for contrast */
    color: #333;
  }
  
  .container {
    max-width: 900px;
    margin: 0 auto;
    padding: 0 20px;
  }
  
  .section-title {
    font-family: var(--header-font);
    font-size: 3em;
    font-weight: 700;
    text-align: center;
    margin-bottom: 60px;
    color: var(--background-dark);
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
  
  .timeline {
    position: relative;
    padding: 20px 0;
  }
  
  .timeline::before {
    content: '';
    position: absolute;
    top: 0;
    left: 50%;
    width: 4px;
    height: 100%;
    background-color: #dee2e6;
    transform: translateX(-50%);
    z-index: 0;
  }
  
  .timeline-category-title {
    font-family: var(--header-font);
    font-size: 2.2em;
    font-weight: 600;
    text-align: center;
    margin-bottom: 40px;
    margin-top: 50px;
    color: var(--primary-color);
    position: relative;
    z-index: 1;
  }
  
  /* Remove margin-top for the first category title */
  .timeline-category-title:first-of-type {
      margin-top: 0;
  }
  
  
  .timeline-item {
    position: relative;
    margin-bottom: 60px;
    padding: 20px 40px;
    background-color: #fff;
    border-radius: 10px;
    box-shadow: 0 6px 20px rgba(0, 0, 0, 0.1);
    opacity: 0; /* For animation */
    transform: translateY(20px); /* For animation */
    animation: fadeInSlideUp 0.8s ease forwards;
    /* Stagger animation based on index (manual for now, could be dynamic with JS) */
  }
  
  /* Alternate positioning of timeline items */
  .timeline-item:nth-child(odd) {
    left: 50%;
    text-align: left;
    transform-origin: left center;
    animation-delay: 0.1s; /* Example for staggering */
  }
  
  .timeline-item:nth-child(even) {
    right: 50%;
    text-align: right;
    transform-origin: right center;
    animation-delay: 0.2s; /* Example for staggering */
  }
  
  .timeline-item:nth-child(3n) { animation-delay: 0.3s; }
  .timeline-item:nth-child(4n) { animation-delay: 0.4s; }
  .timeline-item:nth-child(5n) { animation-delay: 0.5s; }
  
  
  .timeline-dot {
    position: absolute;
    top: 50%;
    left: 50%;
    width: 18px;
    height: 18px;
    background-color: var(--accent-color);
    border: 4px solid #fff;
    border-radius: 50%;
    transform: translate(-50%, -50%);
    z-index: 1;
    box-shadow: 0 0 0 3px rgba(0, 123, 255, 0.3);
  }
  
  .timeline-content {
    padding: 10px; /* Internal padding for content */
  }
  
  .timeline-content h4 {
    font-family: var(--header-font);
    font-size: 1.6em;
    font-weight: 700;
    margin-bottom: 5px;
    color: var(--background-dark);
  }
  
  .timeline-content .institution {
    font-family: var(--body-font);
    font-size: 1.1em;
    font-weight: 600;
    color: var(--primary-color);
    margin-bottom: 5px;
  }
  
  .timeline-content .dates {
    font-family: var(--body-font);
    font-size: 0.95em;
    color: #777;
    margin-bottom: 15px;
  }
  
  .timeline-content .description {
    font-family: var(--body-font);
    font-size: 1em;
    line-height: 1.6;
    color: #555;
    margin-top: 10px;
  }
  
  .timeline-content .responsibilities {
      list-style: none; /* Remove default bullet points */
      padding-left: 0;
      margin-top: 10px;
  }
  
  .timeline-content .responsibilities li {
      font-family: var(--body-font);
      font-size: 0.95em;
      color: #555;
      margin-bottom: 8px;
      position: relative;
      padding-left: 20px; /* Space for custom bullet */
  }
  
  .timeline-content .responsibilities li::before {
      content: '•'; /* Custom bullet point */
      position: absolute;
      left: 0;
      color: var(--accent-color); /* Bullet color */
      font-size: 1.2em;
      line-height: 1;
      top: 2px;
  }
  
  
  /* Animation for timeline items */
  @keyframes fadeInSlideUp {
    from {
      opacity: 0;
      transform: translateY(20px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }
  
  
  /* Responsive adjustments for vertical timeline on small screens */
  @media (max-width: 768px) {
    .edu-exp-section {
      padding: 60px 0;
    }
    .section-title {
      font-size: 2.5em;
      margin-bottom: 40px;
    }
    .timeline::before {
      left: 20px; /* Move timeline line to the left */
      transform: translateX(0);
    }
    .timeline-item {
      width: auto; /* Remove fixed width */
      margin-left: 40px; /* Space for the line and dot */
      left: 0 !important; /* Override odd/even positioning */
      right: auto !important; /* Override odd/even positioning */
      text-align: left !important; /* Ensure content is left-aligned */
      transform-origin: left center;
    }
    .timeline-item:last-child {
      margin-bottom: 0;
    }
    .timeline-dot {
      left: 20px; /* Align dot with the line */
      transform: translate(-50%, -50%); /* Only translate Y for dot */
    }
    .timeline-category-title {
      font-size: 1.8em;
      margin-bottom: 30px;
    }
    .timeline-content h4 {
      font-size: 1.4em;
    }
    .timeline-content .institution {
      font-size: 1em;
    }
    .timeline-content .dates {
      font-size: 0.9em;
    }
    .timeline-content .description,
    .timeline-content .responsibilities li {
      font-size: 0.9em;
    }
  }
  
  @media (max-width: 480px) {
    .edu-exp-section {
      padding: 40px 0;
    }
    .section-title {
      font-size: 2em;
      margin-bottom: 30px;
    }
    .timeline-item {
      margin-bottom: 40px;
    }
    .timeline-category-title {
      font-size: 1.6em;
      margin-bottom: 25px;
      margin-top: 40px;
    }
    .timeline-item {
      padding: 15px 25px;
    }
    .timeline-content h4 {
      font-size: 1.2em;
    }
  }
  </style>