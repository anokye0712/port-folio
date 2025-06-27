<template>
     <section id="projects" class="projects-section">
    <div class="container">
      <h2 class="section-title">Projects & Research</h2>

      <div class="filters">
        <button
          @click="setActiveFilter('all')"
          :class="{ active: activeFilter === 'all' }"
          class="filter-button"
        >
          All
        </button>
        <button
          @click="setActiveFilter('published')"
          :class="{ active: activeFilter === 'published' }"
          class="filter-button"
        >
          Published
        </button>
        <button
          @click="setActiveFilter('under review')"
          :class="{ active: activeFilter === 'under review' }"
          class="filter-button"
        >
          Under Review
        </button>
        <button
          @click="setActiveFilter('thesis')"
          :class="{ active: activeFilter === 'thesis' }"
          class="filter-button"
        >
          Master's Thesis
        </button>
      </div>

      <div class="projects-grid">
        <div class="project-card" v-for="project in filteredProjects" :key="project.id">
          <div class="project-image-container">
            <img
              :src= "project.imageUrl || getProjectImage(project.type)"
              :alt="project.title"
              class="project-image"
            />
          </div>
          <div class="project-info">
            <h3 class="project-title">{{ project.title }}</h3>
            <p class="project-description">{{ project.description }}</p>
            <a :href="project.url" target="_blank" class="project-link" v-if="project.url">
              View Publication
              <span class="arrow">→</span>
            </a>
            <span class="project-status" :class="project.status.toLowerCase()">
              {{ project.status }}
            </span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue';

// Dummy project data (will eventually come from FastAPI)
const projects = ref([
  {
    id: 1,
    title: "CNN multi-beam seabed sediment classification combined with novel feature optimization method",
    description: "Objective: Develop an improved method for seabed sediment classification using Convolutional Neural Networks (CNNs) by integrating a novel feature optimization technique. Methods: Utilized multibeam echosounder data, applied advanced signal processing for feature extraction, and optimized feature sets before feeding into a CNN model. Key Outcomes: Achieved higher accuracy in sediment type identification compared to traditional methods, demonstrating robustness in diverse marine environments.",
    url: "https://doi.org/10.1007/s11004-023-10079-5",
    imageUrl: "./images/Gemini_Generated_Image_zbbpk1zbbpk1zbbp.png",
    status: "Published",
    type: "Published"
  },
  {
    id: 2,
    title: "Characterization of terrain variations of an underwater ancient town in Qiandao Lake",
    description: "Objective: Map and characterize the submerged terrain of an ancient town in Qiandao Lake to understand its geological and historical significance. Methods: Employed high-resolution multibeam bathymetry and GIS analysis to create detailed 3D models and terrain profiles. Key Outcomes: Provided precise topographical data of the underwater structures, aiding in archaeological assessment and preservation efforts.",
    url: "https://doi.org/10.3390/rs12020268",
    imageUrl: "./images/remotesensing-12-00268-g008-550.jpg",
    status: "Published",
    type: "Published"
  },
  {
    id: 3,
    title: "High-resolution seafloor survey and applications.",
    description: "Objective: Contribute to a book on high-resolution seafloor survey techniques and their practical applications. Methods: Involved in the technical issue group, focusing on data acquisition, processing methodologies, and case studies related to detailed seafloor mapping for various marine engineering and environmental purposes. Key Outcomes: Provided expertise on cutting-edge survey technologies and their real-world impact.",
    url: "https://www.tandfonline.com/doi/abs/10.1080/01490419.2023.2185842",
    imageUrl: "./images/highres.png",
    status: "Published",
    type: "Published"
  },
  {
    id: 4,
    title: "Optimizing Multi-Classifier Fusion for Seabed Sediment Classification Using Machine Learning",
    description: "Objective: Enhance seabed sediment classification accuracy by developing an optimized multi-classifier fusion framework. Methods: Explored various machine learning algorithms (e.g., SVM, Random Forest, Neural Networks) and designed a fusion strategy that leverages the strengths of multiple models. Key Outcomes: Achieved significant improvements in classification performance, particularly for complex sediment types, through intelligent model combination.",
    url: "https://doi.org/10.1080/17538947.2023.2295988",
    status: "Published", // Changed to Under Review as per prompt
    imageUrl: "./images/SVM_new.png",
    type: "Under Review"
  },
  {
    id: 5,
    title: "Master's Thesis: Improving Seabed Sediment Classification from Multibeam Echosounders using Nonlinear Feature Optimization and Adaptive Model Fusion.",
    description: "Objective: My master's thesis focused on advancing seabed sediment classification from multibeam echosounder data. Methods: Investigated nonlinear feature optimization techniques to enhance the discriminatory power of acoustic features and developed an adaptive model fusion framework to combine the outputs of multiple machine learning classifiers. Key Outcomes: The research significantly improved classification accuracy and robustness, providing a more reliable methodology for marine habitat mapping and geological surveys.",
    url: null, // No specific DOI/URL provided in prompt for thesis
    imageUrl:'./images/fig4.svg',
    status: "Completed",
    type: "Master's Thesis"
  }
]);

const activeFilter = ref('all');

const setActiveFilter = (filterType) => {
  activeFilter.value = filterType;
};

const filteredProjects = computed(() => {
  if (activeFilter.value === 'all') {
    return projects.value;
  }
  if (activeFilter.value === 'published') {
    return projects.value.filter(project => project.type === 'Published');
  }
  if (activeFilter.value === 'under review') {
    return projects.value.filter(project => project.type === 'Under Review');
  }
  if (activeFilter.value === 'thesis') {
    return projects.value.filter(project => project.type === 'Master\'s Thesis');
  }
  return projects.value; // Fallback
});

// Function to determine placeholder image based on project type/status
const getProjectImage = (type) => {
  // You would replace these with actual image paths if you had them
  // For now, using generic icons or colored placeholders
  switch (type) {
    case 'Published':
      return '/images/pub-icon.svg'; // Or a generic map/chart icon
    case 'Under Review':
      return '/images/review-icon.svg'; // Or a generic document icon
    case 'Master\'s Thesis':
      return '/images/thesis-icon.svg'; // Or a generic book icon
    default:
      return '/images/default-project.svg'; // Generic fallback
  }
};
</script>

<style scoped>
/* Scoped styles for the ProjectsSection component */
.projects-section {
  padding: 80px 0;
  background-color: #f8f9fa; /* Light background for contrast */
  color: #333;
}

.container {
  max-width: 1200px; /* Wider container for projects */
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

.filters {
  text-align: center;
  margin-bottom: 50px;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 15px;
}

.filter-button {
  background-color: #e9ecef;
  color: var(--background-dark);
  border: 1px solid #ccc;
  padding: 12px 25px;
  border-radius: 30px;
  font-size: 1.1em;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

.filter-button:hover {
  background-color: #dee2e6;
  border-color: var(--primary-color);
}

.filter-button.active {
  background-color: var(--primary-color);
  color: var(--text-light);
  border-color: var(--primary-color);
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
  transform: translateY(-2px);
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 40px;
}

.project-card {
  background-color: #fff;
  border-radius: 12px;
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1);
  overflow: hidden;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  display: flex;
  flex-direction: column;
}

.project-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 12px 30px rgba(0, 0, 0, 0.15);
}

.project-image-container {
  width: 100%;
  height: 220px; /* Fixed height for image area */
  background-color: #e9ecef; /* Placeholder background */
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
  border-bottom: 1px solid #eee;
}

.project-image {
  max-width: 100%;
  max-height: 100%;
  object-fit: contain; /* Ensure image fits well */
  opacity: 0.8; /* Subtle transparency for placeholder */
  /* If you have actual detailed images, you might want object-fit: cover; and adjust height */
}

.project-info {
  padding: 25px;
  display: flex;
  flex-direction: column;
  flex-grow: 1; /* Allows info section to expand */
}

.project-title {
  font-family: var(--header-font);
  font-size: 1.6em;
  font-weight: 700;
  margin-bottom: 15px;
  color: var(--background-dark);
  line-height: 1.3;
}

.project-description {
  font-family: var(--body-font);
  font-size: 1em;
  line-height: 1.7;
  color: #555;
  margin-bottom: 20px;
  flex-grow: 1; /* Allows description to take up available space */
}

.project-link {
  display: inline-flex;
  align-items: center;
  margin-top: auto; /* Push link to the bottom */
  color: var(--primary-color);
  font-weight: 600;
  transition: color 0.3s ease;
}

.project-link:hover {
  color: var(--accent-color);
}

.project-link .arrow {
  margin-left: 8px;
  transition: margin-left 0.3s ease;
}

.project-link:hover .arrow {
  margin-left: 12px;
}

.project-status {
  display: inline-block;
  margin-top: 15px;
  padding: 6px 12px;
  border-radius: 20px;
  font-size: 0.85em;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  align-self: flex-start; /* Align status to the left */
}

.project-status.published {
  background-color: #d4edda;
  color: #155724;
}

.project-status.under.review { /* Note the two classes for "under review" */
  background-color: #fff3cd;
  color: #856404;
}

.project-status.completed {
  background-color: #d1ecf1;
  color: #0c5460;
}

/* Responsive adjustments */
@media (max-width: 1024px) {
  .projects-grid {
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 30px;
  }
  .project-title {
    font-size: 1.4em;
  }
}

@media (max-width: 768px) {
  .projects-section {
    padding: 60px 0;
  }
  .section-title {
    font-size: 2.5em;
    margin-bottom: 40px;
  }
  .filters {
    margin-bottom: 40px;
    gap: 10px;
  }
  .filter-button {
    padding: 10px 20px;
    font-size: 1em;
  }
  .projects-grid {
    grid-template-columns: 1fr; /* Stack cards on small screens */
    gap: 25px;
  }
  .project-image-container {
    height: 200px;
  }
  .project-info {
    padding: 20px;
  }
  .project-title {
    font-size: 1.3em;
    margin-bottom: 10px;
  }
  .project-description {
    font-size: 0.95em;
    margin-bottom: 15px;
  }
  .project-link {
    font-size: 0.95em;
  }
}

@media (max-width: 480px) {
  .projects-section {
    padding: 40px 0;
  }
  .section-title {
    font-size: 2em;
    margin-bottom: 30px;
  }
  .filter-button {
    padding: 8px 15px;
    font-size: 0.9em;
  }
  .project-image-container {
    height: 180px;
  }
  .project-info {
    padding: 15px;
  }
  .project-title {
    font-size: 1.2em;
  }
}
</style>