<script setup>
</script>

<template>
    <section class="hero-section">
        <div class="hero-background"></div>
        <div class="hero-content">
            <h1 class="hero-name">Michael Anokye</h1>
            <p class="hero-tagline">Geomatic Engineer Professional | Geospatial AI & Seabed Modeling Expert</p>
            <a href="#about" class="cta-about">Explore My Work</a>
        </div>
    </section>
</template>

<style scoped>

/* Scoped styles for the HeroSection component */
.hero-section {
  position: relative;
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
  color: var(--text-light); /* Use a light text color from our variables */
  text-align: center;
  /* background-color: var(--background-dark); */ /* A fallback dark background */
}

.hero-background {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(135deg, var(--background-dark) 0%, #3e0b57 100%); /* Abstract gradient */
  /* Or a subtle pattern/image: */
  /* background-image: url('../assets/images/abstract-geo-pattern.svg'); */ /* You'd create this SVG */
  /* background-size: cover; */
  /* background-position: center; */
  /* filter: brightness(0.7); Adjust brightness if using an image */
  z-index: 0;

  /* Subtle animation for the background */
  animation: gradient-shift 15s ease infinite alternate;
}

@keyframes gradient-shift {
  0% {
    background-position: 0% 50%;
  }
  100% {
    background-position: 100% 50%;
  }
}

.hero-content {
  position: relative;
  z-index: 1;
  max-width: 900px;
  padding: 20px;
  opacity: 0; /* Will animate in with JS later */
  transform: translateY(20px); /* Will animate in with JS later */
  animation: fade-in-up 1s ease-out forwards;
  animation-delay: 0.5s;
}

@keyframes fade-in-up {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.hero-name {
  font-family: var(--header-font);
  font-size: 4.5em; /* Large font size */
  font-weight: 700;
  margin-bottom: 15px;
  letter-spacing: 2px;
  text-shadow: 2px 2px 8px rgba(0, 0, 0, 0.3); /* Subtle text shadow */
}

.hero-tagline {
  font-family: var(--body-font);
  font-size: 1.8em;
  font-weight: 400;
  margin-bottom: 40px;
  color: rgba(255, 255, 255, 0.85);
}

.cta-button {
  display: inline-block;
  padding: 18px 35px;
  background-color: var(--accent-color);
  color: var(--text-light);
  border: none;
  border-radius: 50px; /* Pill shape */
  font-size: 1.2em;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
}

.cta-button:hover {
  background-color: #218838; /* Slightly darker green on hover */
  transform: translateY(-3px);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3);
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .hero-name {
    font-size: 3em;
  }
  .hero-tagline {
    font-size: 1.4em;
  }
  .cta-button {
    padding: 15px 30px;
    font-size: 1em;
  }
}

@media (max-width: 480px) {
  .hero-name {
    font-size: 2.2em;
  }
  .hero-tagline {
    font-size: 1.1em;
    margin-bottom: 30px;
  }
  .cta-button {
    padding: 12px 25px;
    font-size: 0.9em;
  }
}

</style>
