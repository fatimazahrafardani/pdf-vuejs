<template>
    <header class="header">
      <nav class="nav-container">
        <div class="logo">LUXE</div>
        <div class="nav-links">
          <a href="#menu">Menu</a>
          <a href="#about">About</a>
          <a href="#reservations">Reservations</a>
          <a href="#contact">Contact</a>
        </div>
      </nav>
    </header>
  </template>
  
  <style scoped>
  .header {
    padding: 1.5rem 2rem;
    position: fixed;
    width: 100%;
    top: 0;
    z-index: 1000;
    background: rgba(0, 0, 0, 0.8);
    backdrop-filter: blur(8px);
  }
  
  .nav-container {
    max-width: 1200px;
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  
  .logo {
    font-size: 2rem;
    font-weight: 700;
    color: #ffffff;
    letter-spacing: 3px;
  }
  
  .nav-links {
    display: flex;
    gap: 2rem;
  }
  
  .nav-links a {
    color: #ffffff;
    text-decoration: none;
    font-size: 1.1rem;
    transition: color 0.3s ease;
  }
  
  .nav-links a:hover {
    color: #d4af37;
  }
  </style>