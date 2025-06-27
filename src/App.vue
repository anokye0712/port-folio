<script setup>
import { ref , watch} from "vue"
import Header from './components/Header.vue'; // Import the new header
import HeroSection from "./components/HeroSection.vue"
import About from "./components/About.vue"
import SkillsSection from "./components/SkillsSection.vue"
import ProjectSection from "./components/ProjectSection.vue"
import EducationExperienceSection from './components/EducationExperienceSection.vue'; // Import the new component
import ContactSection from './components/ContactSection.vue'; // Import the new component

const isNavOpen = ref(false); // State to control body overflow and potential overlay

const handleNavStateChange = (status) => {
  isNavOpen.value = status;
};

// Watch isNavOpen and add/remove class to body
watch(isNavOpen, (newValue) => {
  if (newValue) {
    document.body.classList.add('nav-is-open');
  } else {
    document.body.classList.remove('nav-is-open');
  }
}, { immediate: true }); // Run immediately on component mount
</script>

<template>
  <div>
    <Header @nav-state-changed="handleNavStateChange" /> <div class="header-spacer"></div>

    <HeroSection></HeroSection>
    <About></About>
    <EducationExperienceSection></EducationExperienceSection>
    <ProjectSection></ProjectSection>
    <SkillsSection></SkillsSection>
    <ContactSection></ContactSection>
  </div>
  
</template>


<style scoped>
/* Global App.vue specific styles */
#app {
  /* No specific styles here yet, just ensuring global styles apply */
}

/* Class to prevent scrolling when mobile nav is open */
.overflow-hidden {
  overflow: hidden;
  height: 100vh; /* Prevent scroll on mobile when nav is open */
}

/* Spacer to prevent content from going under the fixed header */
.header-spacer {
  height: 80px; /* Adjust this value to match your header's actual height + padding */
  width: 100%;
}

/* Global overlay when mobile nav is open */
/* This works by modifying the body (or #app) directly, coupled with TheHeader's state */
body.nav-is-open::before { /* We'll toggle this class on <body> using JS in main.js */
  content: '';
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  z-index: 999; /* Below nav, above content */
  transition: opacity 0.4s ease;
  opacity: 1;
}

body.nav-is-open {
  overflow: hidden; /* Disable scrolling when overlay is active */
}
</style>
