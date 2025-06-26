<template>
    <header class="main-header">
      <div class="container">
        <a href="#app" class="logo">MICHAEL ANOKYE</a>
        <nav :class="{ 'nav-open': isNavOpen }" class="main-nav">
          <ul>
            <li><a href="#about" @click="closeNav">About</a></li>
            <li><a href="#skills" @click="closeNav">Skills</a></li>
            <li><a href="#projects" @click="closeNav">Projects</a></li>
            <li><a href="#education-experience" @click="closeNav">Education & Experience</a></li>
            <li><a href="#contact" @click="closeNav">Contact</a></li>
          </ul>
        </nav>
        <button class="menu-toggle" @click="toggleNav">
          <span class="bar" :class="{ 'bar-top-open': isNavOpen }"></span>
          <span class="bar" :class="{ 'bar-middle-open': isNavOpen }"></span>
          <span class="bar" :class="{ 'bar-bottom-open': isNavOpen }"></span>
        </button>
      </div>
    </header>
  </template>
  
  <script setup>
import { ref, watch } from 'vue'; // Import watch

const isNavOpen = ref(false);
const emit = defineEmits(['nav-state-changed']); // Define emits

const toggleNav = () => {
  isNavOpen.value = !isNavOpen.value;
  emit('nav-state-changed', isNavOpen.value); // Emit event
};

const closeNav = () => {
  isNavOpen.value = false;
  emit('nav-state-changed', isNavOpen.value); // Emit event
};

// Add a watch to handle cases where external click might close it or initial load
// watch(isNavOpen, (newValue) => {
//   emit('nav-state-changed', newValue);
// });
  </script>
  
  <style scoped>
  /* Scoped styles for the Header component */
  .main-header {
    position: fixed; /* Makes the header stick to the top */
    top: 0;
    left: 0;
    width: 100%;
    background-color: rgba(26, 26, 46, 0.95); /* Slightly transparent dark background */
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
    z-index: 1000; /* Ensures it stays on top of other content */
    padding: 15px 0;
    transition: background-color 0.3s ease;
  }
  
  .main-header .container {
    display: flex;
    justify-content: space-between;
    align-items: center;
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 20px;
  }
  
  .logo {
    font-family: var(--header-font);
    font-size: 1.8em;
    font-weight: 700;
    color: var(--text-light);
    text-decoration: none;
    letter-spacing: 1px;
    transition: color 0.3s ease;
  }
  
  .logo:hover {
    color: var(--primary-color);
  }
  
  .main-nav ul {
    list-style: none;
    display: flex;
    margin: 0;
    padding: 0;
  }
  
  .main-nav li {
    margin-left: 40px;
  }
  
  .main-nav a {
    font-family: var(--body-font);
    font-size: 1.1em;
    color: rgba(255, 255, 255, 0.8);
    text-decoration: none;
    transition: color 0.3s ease, transform 0.3s ease;
    position: relative;
  }
  
  .main-nav a::after {
    content: '';
    position: absolute;
    left: 0;
    bottom: -5px;
    width: 0;
    height: 3px;
    background-color: var(--accent-color);
    transition: width 0.3s ease;
  }
  
  .main-nav a:hover {
    color: var(--text-light);
    transform: translateY(-2px);
  }
  
  .main-nav a:hover::after,
  .main-nav a.active::after { /* You could add an 'active' class based on scroll position */
    width: 100%;
  }
  
  /* Mobile Menu Toggle */
  .menu-toggle {
    display: none; /* Hidden on desktop */
    background: none;
    border: none;
    cursor: pointer;
    padding: 10px;
    z-index: 1001; /* Ensure button is above nav */
  }
  
  .bar {
    display: block;
    width: 30px;
    height: 3px;
    background-color: var(--text-light);
    margin: 6px 0;
    transition: all 0.3s ease;
    border-radius: 2px;
  }
  
  /* Hamburger to X animation */
  .bar-top-open {
    transform: rotate(45deg) translate(8px, 8px);
  }
  .bar-middle-open {
    opacity: 0;
  }
  .bar-bottom-open {
    transform: rotate(-45deg) translate(8px, -8px);
  }
  
  
  /* Responsive adjustments */
  @media (max-width: 900px) {
    .main-nav {
      position: fixed;
      top: 0;
      right: -280px; /* Hidden off-screen */
      width: 250px; /* Width of the sidebar menu */
      height: 100%;
      background-color: var(--background-dark);
      padding-top: 100px; /* Space for logo/toggle */
      box-shadow: -5px 0 15px rgba(0, 0, 0, 0.3);
      transition: right 0.4s ease-in-out;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: flex-start;
    }
  
    .main-nav.nav-open {
      right: 0; /* Slide in */
    }
  
    .main-nav ul {
      flex-direction: column;
      width: 100%;
      padding: 20px 0;
    }
  
    .main-nav li {
      margin: 0;
      width: 100%;
      text-align: center;
      border-bottom: 1px solid rgba(255, 255, 255, 0.1); /* Separator */
    }
  
    .main-nav li:last-child {
      border-bottom: none;
    }
  
    .main-nav a {
      display: block; /* Make links full width of li */
      padding: 15px 20px;
      font-size: 1.2em;
      color: var(--text-light);
      opacity: 0.9;
    }
  
    .main-nav a:hover {
      background-color: #3e3e5c;
      color: var(--accent-color);
    }
  
    .main-nav a::after {
      display: none; /* Hide underline on mobile */
    }
  
    .menu-toggle {
      display: block; /* Show hamburger on mobile */
    }
  
    /* When nav is open, darken content behind */
    #app::before {
      content: '';
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.5);
      z-index: 999; /* Below nav, above content */
      opacity: 0;
      visibility: hidden;
      transition: opacity 0.4s ease, visibility 0.4s ease;
    }
    .nav-open + #app::before { /* This selector is incorrect for sibling */
      /* This needs to be applied directly to #app or parent if nav is not sibling */
      /* For simplicity, we'll apply it globally to body if nav is open */
    }
  }
  
  /* Global body overlay when nav is open (needs to be outside scoped style) */
  /* This part will be added to main.css or App.vue's global style */
  </style>