<template>
    <section id="contact" class="contact-section">
      <div class="container">
        <h2 class="section-title">Get in Touch</h2>
  
        <div class="contact-grid">
          <div class="contact-info">
            <h3>Contact Details</h3>
            <p class="contact-detail">
              <span class="icon">📱</span> Mobile: (+86) 19963864349
            </p>
            <p class="contact-detail">
              <span class="icon">✉️</span> E-mail: anokye561@outlook.com
            </p>
  
            <div class="social-links">
              <a href="https://linkedin.com/in/michaelanokye" target="_blank" class="social-icon">
                <img src="/icons/linkedin.svg" alt="LinkedIn" />
              </a>
              <a href="https://www.researchgate.net/profile/Michael-Anokye" target="_blank" class="social-icon">
                <img src="/icons/researchgate.svg" alt="ResearchGate" />
              </a>
              </div>
          </div>
  
          <div class="contact-form-container">
            <h3>Send a Message</h3>
            <form class="contact-form" @submit.prevent="submitForm">
              <div class="form-group">
                <label for="name">Name</label>
                <input type="text" id="name" name="name" placeholder="Your Name" required />
              </div>
              <div class="form-group">
                <label for="email">Email</label>
                <input type="email" id="email" name="email" placeholder="Your Email" required />
              </div>
              <div class="form-group">
                <label for="message">Message</label>
                <textarea id="message" name="message" rows="6" placeholder="Your Message" required></textarea>
              </div>
              <button type="submit" class="submit-button">Send Message</button>
              <p class="form-note">
              </p>
            </form>
          </div>
        </div>
      </div>
    </section>
  </template>
  
  <script setup>
  // This form is intentionally non-functional as per the prompt.
  // The submitForm function will just log a message.
  const submitForm = () => {
    alert('Thank you for your message! This form is currently non-functional. Please use the email/mobile provided.');
    // In a real application, you would send this data to your backend
  };
  </script>
  
  <style scoped>
  /* Scoped styles for the ContactSection component */
  .contact-section {
    padding: 80px 0;
    background-color: var(--background-dark); /* Dark background for the footer/contact */
    color: var(--text-light);
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
    color: var(--text-light);
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
  
  .contact-grid {
    display: grid;
    grid-template-columns: 1fr 1.5fr; /* Info on left, form on right */
    gap: 50px;
    background-color: #2a2a40; /* Slightly lighter dark for content area */
    border-radius: 15px;
    padding: 40px;
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
  }
  
  .contact-info,
  .contact-form-container {
    padding: 20px;
  }
  
  .contact-info h3,
  .contact-form-container h3 {
    font-family: var(--header-font);
    font-size: 2.2em;
    font-weight: 600;
    margin-bottom: 30px;
    color: var(--primary-color);
    text-align: center;
  }
  
  .contact-detail {
    display: flex;
    align-items: center;
    font-family: var(--body-font);
    font-size: 1.2em;
    margin-bottom: 20px;
    color: rgba(255, 255, 255, 0.9);
  }
  
  .contact-detail .icon {
    font-size: 1.5em;
    margin-right: 15px;
    color: var(--accent-color);
  }
  
  .social-links {
    margin-top: 40px;
    display: flex;
    justify-content: center; /* Center icons */
    gap: 25px;
  }
  
  .social-icon {
    display: inline-block;
    width: 50px;
    height: 50px;
    border-radius: 50%;
    background-color: #3e3e5c; /* Darker background for icons */
    display: flex;
    justify-content: center;
    align-items: center;
    transition: transform 0.3s ease, background-color 0.3s ease, box-shadow 0.3s ease;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
  }
  
  .social-icon img {
    width: 60%;
    height: 60%;
    filter: invert(1); /* Make SVGs white on dark background */
    opacity: 0.8;
  }
  
  .social-icon:hover {
    transform: translateY(-5px) scale(1.05);
    background-color: var(--primary-color);
    box-shadow: 0 6px 15px rgba(0, 0, 0, 0.3);
  }
  
  /* Contact Form Styles */
  .contact-form {
    display: flex;
    flex-direction: column;
  }
  
  .form-group {
    margin-bottom: 20px;
  }
  
  .form-group label {
    display: block;
    font-family: var(--body-font);
    font-size: 1.1em;
    margin-bottom: 8px;
    color: rgba(255, 255, 255, 0.9);
  }
  
  .form-group input,
  .form-group textarea {
    width: 100%;
    padding: 15px;
    border: 1px solid #555;
    border-radius: 8px;
    background-color: #3e3e5c;
    color: var(--text-light);
    font-family: var(--body-font);
    font-size: 1em;
    transition: border-color 0.3s ease, box-shadow 0.3s ease;
  }
  
  .form-group input::placeholder,
  .form-group textarea::placeholder {
    color: rgba(255, 255, 255, 0.5);
  }
  
  .form-group input:focus,
  .form-group textarea:focus {
    outline: none;
    border-color: var(--primary-color);
    box-shadow: 0 0 0 3px rgba(0, 123, 255, 0.3);
  }
  
  .submit-button {
    display: inline-block;
    padding: 18px 35px;
    background-color: var(--accent-color);
    color: var(--text-light);
    border: none;
    border-radius: 50px;
    font-size: 1.2em;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.3s ease;
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
    align-self: flex-start; /* Align button to the left */
    margin-top: 10px;
  }
  
  .submit-button:hover {
    background-color: #218838;
    transform: translateY(-3px);
    box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3);
  }
  
  .form-note {
    font-family: var(--body-font);
    font-size: 0.9em;
    color: rgba(255, 255, 255, 0.7);
    margin-top: 25px;
    text-align: center;
  }
  
  
  /* Responsive adjustments */
  @media (max-width: 900px) {
    .contact-grid {
      grid-template-columns: 1fr; /* Stack columns on smaller screens */
      gap: 30px;
      padding: 30px;
    }
    .contact-info, .contact-form-container {
      padding: 0; /* Remove inner padding as grid provides it */
    }
    .contact-info h3, .contact-form-container h3 {
      margin-bottom: 25px;
    }
    .social-links {
      margin-top: 30px;
    }
    .contact-detail {
      font-size: 1.1em;
      justify-content: center; /* Center contact details when stacked */
    }
    .form-group label {
      font-size: 1em;
    }
    .submit-button {
      align-self: center; /* Center button when stacked */
      padding: 15px 30px;
      font-size: 1.1em;
    }
  }
  
  @media (max-width: 480px) {
    .contact-section {
      padding: 40px 0;
    }
    .section-title {
      font-size: 2em;
      margin-bottom: 30px;
    }
    .contact-grid {
      padding: 20px;
    }
    .contact-info h3, .contact-form-container h3 {
      font-size: 1.8em;
      margin-bottom: 20px;
    }
    .contact-detail {
      font-size: 1em;
      margin-bottom: 15px;
    }
    .social-icon {
      width: 40px;
      height: 40px;
    }
    .form-group input,
    .form-group textarea {
      padding: 12px;
      font-size: 0.95em;
    }
    .submit-button {
      padding: 12px 25px;
      font-size: 1em;
    }
    .form-note {
      font-size: 0.85em;
    }
  }
  </style>