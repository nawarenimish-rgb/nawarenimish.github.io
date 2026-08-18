<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>FresherConnect — Meet Your College Batch</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@500;600;700&family=IBM+Plex+Sans:wght@400;500;600&family=IBM+Plex+Mono:wght@400;500&family=Caveat:wght@500;600;700&display=swap" rel="stylesheet">
<style>
  :root{
    --primary: #FF6B6B;
    --primary-dark: #E63946;
    --secondary: #4ECDC4;
    --accent: #FFE66D;
    --dark: #2B2D42;
    --light: #F7F9FC;
    --gray: #95A5A6;
    --success: #2ECC71;
    --warning: #F39C12;
    --danger: #E74C3C;
    --font-display: 'Space Grotesk', sans-serif;
    --font-body: 'IBM Plex Sans', sans-serif;
    --font-mono: 'IBM Plex Mono', monospace;
    --font-hand: 'Caveat', cursive;
    --radius: 10px;
  }

  *{ box-sizing: border-box; }
  html{ scroll-behavior: smooth; }
  body{
    margin:0;
    font-family: var(--font-body);
    color: var(--dark);
    background: var(--light);
    -webkit-font-smoothing: antialiased;
  }

  a{ color: inherit; text-decoration: none; }
  h1,h2,h3,h4{ font-family: var(--font-display); margin:0; }
  button{ font-family: var(--font-body); cursor:pointer; border:none; }
  input, textarea{ font-family: var(--font-body); }

  :focus-visible{
    outline: 2.5px dashed var(--primary);
    outline-offset: 3px;
  }

  /* ---------- NAV ---------- */
  .nav{
    position: sticky; top:0; z-index: 40;
    background: rgba(255,255,255,0.95);
    backdrop-filter: blur(8px);
    border-bottom: 1px solid rgba(0,0,0,0.08);
    box-shadow: 0 2px 10px rgba(0,0,0,0.05);
  }
  .nav .wrap{ display:flex; align-items:center; justify-content:space-between; padding:16px 24px; }
  .brand{ display:flex; align-items:center; gap:12px; font-family: var(--font-display); font-weight:700; font-size:1.2rem; color: var(--primary); }
  .brand-icon{ font-size:1.5rem; }
  .nav-right{ display:flex; align-items:center; gap:16px; }
  .nav-link{ font-size:0.95rem; font-weight:500; color: var(--dark); transition: color 0.2s; }
  .nav-link:hover{ color: var(--primary); }
  .nav-btn{ background: var(--primary); color: white; padding:10px 18px; border-radius:20px; font-size:0.9rem; font-weight:600; transition: all 0.2s; }
  .nav-btn:hover{ background: var(--primary-dark); transform: translateY(-2px); }

  .wrap{ max-width: 1200px; margin: 0 auto; padding: 0 24px; }
  section{ padding: 80px 0; }

  /* ---------- HERO ---------- */
  .hero{
    background: linear-gradient(135deg, var(--primary) 0%, var(--secondary) 100%);
    color: white;
    padding: 120px 0;
    text-align: center;
    position: relative;
    overflow: hidden;
  }
  .hero::before{
    content: '';
    position: absolute;
    top: -50%;
    right: -10%;
    width: 500px;
    height: 500px;
    background: rgba(255,255,255,0.1);
    border-radius: 50%;
  }
  .hero::after{
    content: '';
    position: absolute;
    bottom: -30%;
    left: -5%;
    width: 300px;
    height: 300px;
    background: rgba(255,255,255,0.1);
    border-radius: 50%;
  }
  .hero .wrap{ position: relative; z-index: 2; }
  .hero h1{
    font-size: clamp(2.5rem, 6vw, 4rem);
    line-height: 1.1;
    margin-bottom: 16px;
    font-weight: 700;
  }
  .hero p{
    font-size: 1.2rem;
    max-width: 600px;
    margin: 0 auto 32px;
    opacity: 0.95;
    line-height: 1.6;
  }
  .hero-ctas{ display:flex; gap:16px; justify-content:center; flex-wrap:wrap; }
  .btn{
    font-family: var(--font-body);
    font-weight: 600;
    font-size: 1rem;
    padding: 14px 28px;
    border-radius: 8px;
    border: none;
    display: inline-flex;
    align-items: center;
    gap: 8px;
    transition: all 0.2s ease;
    cursor: pointer;
  }
  .btn-primary{ background: var(--primary); color: white; box-shadow: 0 4px 15px rgba(255,107,107,0.3); }
  .btn-primary:hover{ transform: translateY(-3px); box-shadow: 0 6px 20px rgba(255,107,107,0.4); }
  .btn-secondary{ background: white; color: var(--primary); }
  .btn-secondary:hover{ background: var(--light); }
  .btn-ghost{ background: transparent; border: 2px solid white; color: white; }
  .btn-ghost:hover{ background: rgba(255,255,255,0.1); }

  /* ---------- FEATURES ---------- */
  .features{ background: var(--light); }
  .sec-head{ margin-bottom: 48px; text-align: center; }
  .sec-head h2{ font-size: clamp(1.8rem, 4vw, 2.5rem); margin-bottom: 12px; }
  .sec-head p{ color: var(--gray); max-width: 600px; margin: 0 auto; line-height: 1.6; }

  .features-grid{
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 32px;
  }
  .feature-card{
    background: white;
    padding: 32px;
    border-radius: var(--radius);
    box-shadow: 0 4px 15px rgba(0,0,0,0.08);
    transition: all 0.3s;
    text-align: center;
  }
  .feature-card:hover{
    transform: translateY(-8px);
    box-shadow: 0 12px 30px rgba(0,0,0,0.15);
  }
  .feature-icon{
    font-size: 2.5rem;
    margin-bottom: 16px;
  }
  .feature-card h3{
    font-size: 1.3rem;
    margin-bottom: 12px;
    color: var(--dark);
  }
  .feature-card p{
    color: var(--gray);
    line-height: 1.6;
    margin: 0;
  }

  /* ---------- PROFILES SECTION ---------- */
  .profiles-section{ background: white; }
  .profile-filters{
    display: flex;
    gap: 12px;
    margin-bottom: 32px;
    flex-wrap: wrap;
  }
  .filter-btn{
    background: white;
    border: 2px solid var(--gray);
    padding: 10px 16px;
    border-radius: 20px;
    font-weight: 500;
    color: var(--dark);
    transition: all 0.2s;
  }
  .filter-btn:hover, .filter-btn.active{
    background: var(--primary);
    color: white;
    border-color: var(--primary);
  }

  .search-box{
    position: relative;
    margin-bottom: 32px;
  }
  .search-box input{
    width: 100%;
    padding: 14px 18px 14px 40px;
    border: 2px solid var(--gray);
    border-radius: 8px;
    font-size: 1rem;
    transition: all 0.2s;
  }
  .search-box input:focus{
    outline: none;
    border-color: var(--primary);
    box-shadow: 0 0 0 4px rgba(255,107,107,0.1);
  }
  .search-icon{
    position: absolute;
    left: 12px;
    top: 50%;
    transform: translateY(-50%);
    color: var(--gray);
  }

  .profiles-grid{
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 28px;
  }

  /* ---------- PROFILE CARD ---------- */
  .profile-card{
    background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
    border-radius: var(--radius);
    overflow: hidden;
    box-shadow: 0 4px 15px rgba(0,0,0,0.1);
    transition: all 0.3s;
    cursor: pointer;
  }
  .profile-card:hover{
    transform: translateY(-8px);
    box-shadow: 0 12px 30px rgba(0,0,0,0.2);
  }
  .profile-header{
    background: linear-gradient(135deg, var(--primary), var(--secondary));
    color: white;
    padding: 20px;
    text-align: center;
    position: relative;
  }
  .profile-avatar{
    width: 80px;
    height: 80px;
    background: white;
    border-radius: 50%;
    margin: 0 auto 12px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 2.5rem;
    font-weight: bold;
    color: var(--primary);
  }
  .profile-name{
    font-size: 1.3rem;
    font-weight: 700;
    margin-bottom: 4px;
  }
  .profile-branch{
    font-size: 0.9rem;
    opacity: 0.9;
  }
  .profile-body{
    padding: 20px;
  }
  .profile-info{
    display: flex;
    flex-direction: column;
    gap: 10px;
    margin-bottom: 16px;
  }
  .info-item{
    display: flex;
    align-items: center;
    gap: 8px;
    font-size: 0.95rem;
    color: var(--dark);
  }
  .info-label{
    font-weight: 600;
    color: var(--primary);
    min-width: 80px;
  }
  .interests{
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
    margin-top: 12px;
  }
  .interest-tag{
    background: var(--accent);
    color: var(--dark);
    padding: 4px 10px;
    border-radius: 15px;
    font-size: 0.8rem;
    font-weight: 500;
  }
  .profile-actions{
    display: flex;
    gap: 8px;
    margin-top: 16px;
  }
  .action-btn{
    flex: 1;
    padding: 10px;
    border: 2px solid var(--primary);
    background: white;
    color: var(--primary);
    border-radius: 6px;
    font-weight: 600;
    transition: all 0.2s;
  }
  .action-btn:hover{
    background: var(--primary);
    color: white;
  }

  /* ---------- MODAL ---------- */
  .modal{
    display: none;
    position: fixed;
    inset: 0;
    background: rgba(0,0,0,0.5);
    z-index: 50;
    align-items: center;
    justify-content: center;
  }
  .modal.active{
    display: flex;
  }
  .modal-content{
    background: white;
    border-radius: var(--radius);
    padding: 32px;
    max-width: 500px;
    width: 90%;
    max-height: 90vh;
    overflow-y: auto;
    box-shadow: 0 20px 60px rgba(0,0,0,0.3);
  }
  .modal-header{
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 24px;
  }
  .modal-header h2{
    margin: 0;
  }
  .close-btn{
    background: none;
    font-size: 1.5rem;
    color: var(--dark);
    cursor: pointer;
  }

  .form-group{
    margin-bottom: 24px;
  }
  .form-group label{
    display: block;
    font-weight: 600;
    margin-bottom: 8px;
    color: var(--dark);
  }
  .form-group input, .form-group textarea, .form-group select{
    width: 100%;
    padding: 12px;
    border: 2px solid var(--gray);
    border-radius: 6px;
    font-size: 1rem;
    transition: all 0.2s;
  }
  .form-group input:focus, .form-group textarea:focus, .form-group select:focus{
    outline: none;
    border-color: var(--primary);
    box-shadow: 0 0 0 4px rgba(255,107,107,0.1);
  }
  .form-group textarea{
    resize: vertical;
    min-height: 100px;
  }
  .chip-container{
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    margin-top: 10px;
  }
  .chip{
    background: var(--secondary);
    color: white;
    padding: 8px 12px;
    border-radius: 20px;
    font-size: 0.9rem;
    display: flex;
    align-items: center;
    gap: 6px;
  }
  .chip button{
    background: none;
    color: white;
    cursor: pointer;
    font-size: 1.2rem;
    line-height: 1;
  }

  /* ---------- TOAST ---------- */
  .toast{
    position: fixed;
    bottom: 24px;
    right: 24px;
    background: var(--dark);
    color: white;
    padding: 16px 24px;
    border-radius: 8px;
    box-shadow: 0 8px 20px rgba(0,0,0,0.2);
    opacity: 0;
    transform: translateY(20px);
    transition: all 0.3s;
    z-index: 100;
  }
  .toast.show{
    opacity: 1;
    transform: translateY(0);
  }

  .loading {
    text-align: center;
    padding: 40px;
    color: var(--gray);
  }

  /* ---------- FOOTER ---------- */
  footer{
    background: var(--dark);
    color: white;
    padding: 40px 0;
    text-align: center;
  }
  footer p{
    margin: 8px 0;
    opacity: 0.85;
  }

  @media (max-width: 768px){
    section{ padding: 60px 0; }
    .features-grid, .profiles-grid{
      grid-template-columns: 1fr;
    }
    .hero-ctas{
      flex-direction: column;
    }
    .btn{
      width: 100%;
      justify-content: center;
    }
  }
</style>
</head>
<body>

<!-- NAVIGATION -->
<nav class="nav">
  <div class="wrap">
    <div class="brand">
      <span class="brand-icon">👥</span>
      <span>FresherConnect</span>
    </div>
    <div class="nav-right">
      <a href="#discover" class="nav-link">Discover</a>
      <a href="#create" class="nav-link">Create Profile</a>
      <button class="nav-btn" id="shareNavBtn">Share</button>
    </div>
  </div>
</nav>

<!-- HERO SECTION -->
<section class="hero">
  <div class="wrap">
    <h1>Welcome to College 🎓</h1>
    <p>Meet your batch, make new friends, and start your college journey together. No awkward silences, just connections.</p>
    <div class="hero-ctas">
      <button class="btn btn-primary" id="createProfileBtn">🎉 Create Your Profile</button>
      <a href="#discover" class="btn btn-ghost">Browse Profiles</a>
    </div>
  </div>
</section>

<!-- FEATURES SECTION -->
<section class="features">
  <div class="wrap">
    <div class="sec-head">
      <h2>Why FresherConnect?</h2>
      <p>Everything you need to make your first week unforgettable</p>
    </div>
    <div class="features-grid">
      <div class="feature-card">
        <div class="feature-icon">🔍</div>
        <h3>Discover People</h3>
        <p>Find people from your branch, hometown, or with similar interests.</p>
      </div>
      <div class="feature-card">
        <div class="feature-icon">💬</div>
        <h3>Real Connections</h3>
        <p>See what makes each person unique and find common ground instantly.</p>
      </div>
      <div class="feature-card">
        <div class="feature-icon">🌍</div>
        <h3>Live Sync</h3>
        <p>All profiles sync instantly across everyone in your batch!</p>
      </div>
      <div class="feature-card">
        <div class="feature-icon">🏷️</div>
        <h3>Interest Matching</h3>
        <p>Connect over shared passions — sports, coding, music, gaming, and more.</p>
      </div>
      <div class="feature-card">
        <div class="feature-icon">📱</div>
        <h3>Easy to Share</h3>
        <p>One link to share with your entire batch — no login needed.</p>
      </div>
      <div class="feature-card">
        <div class="feature-icon">🚀</div>
        <h3>Quick Setup</h3>
        <p>Create a profile in 2 minutes and start making friends instantly.</p>
      </div>
    </div>
  </div>
</section>

<!-- PROFILES SECTION -->
<section class="profiles-section" id="discover">
  <div class="wrap">
    <div class="sec-head">
      <h2>Browse Your Batch</h2>
      <p>Click on any profile to learn more about your future friends</p>
    </div>

    <div class="search-box">
      <svg class="search-icon" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
        <circle cx="11" cy="11" r="8"></circle>
        <path d="m21 21-4.35-4.35"></path>
      </svg>
      <input type="text" id="searchInput" placeholder="Search by name, branch, hometown...">
    </div>

    <div class="profile-filters">
      <button class="filter-btn active" data-filter="all">All</button>
      <button class="filter-btn" data-filter="cse">CSE</button>
      <button class="filter-btn" data-filter="ece">ECE</button>
      <button class="filter-btn" data-filter="it">IT</button>
      <button class="filter-btn" data-filter="mechanical">Mechanical</button>
      <button class="filter-btn" data-filter="civil">Civil</button>
    </div>

    <div id="profilesContainer" class="profiles-grid">
      <div class="loading">Loading profiles...</div>
    </div>
  </div>
</section>

<!-- CREATE PROFILE MODAL -->
<div class="modal" id="createModal">
  <div class="modal-content">
    <div class="modal-header">
      <h2>Create Your Profile</h2>
      <button class="close-btn" id="closeModalBtn">&times;</button>
    </div>
    <form id="profileForm">
      <div class="form-group">
        <label for="name">Full Name *</label>
        <input type="text" id="name" required placeholder="What's your name?">
      </div>

      <div class="form-group">
        <label for="branch">Branch / Course *</label>
        <select id="branch" required>
          <option value="">Select your branch</option>
          <option value="cse">Computer Science (CSE)</option>
          <option value="ece">Electronics & Communication (ECE)</option>
          <option value="it">Information Technology (IT)</option>
          <option value="mechanical">Mechanical Engineering</option>
          <option value="civil">Civil Engineering</option>
          <option value="chemical">Chemical Engineering</option>
          <option value="aerospace">Aerospace Engineering</option>
          <option value="other">Other</option>
        </select>
      </div>

      <div class="form-group">
        <label for="hometown">Hometown *</label>
        <input type="text" id="hometown" required placeholder="Where are you from?">
      </div>

      <div class="form-group">
        <label for="bio">Tell us about yourself</label>
        <textarea id="bio" placeholder="Share something interesting about yourself in a few lines..."></textarea>
      </div>

      <div class="form-group">
        <label for="interests">Interests & Hobbies</label>
        <input type="text" id="interestInput" placeholder="Type and press Enter (e.g., Gaming, Music, Sports)">
        <div class="chip-container" id="interestsContainer"></div>
      </div>

      <div class="form-group">
        <label for="contact">Contact (Optional)</label>
        <input type="text" id="contact" placeholder="Instagram handle, email, or phone (optional)">
      </div>

      <div class="form-group">
        <label for="avatar">Emoji Avatar</label>
        <select id="avatar">
          <option value="😊">😊 Happy</option>
          <option value="😎">😎 Cool</option>
          <option value="🤓">🤓 Nerdy</option>
          <option value="😄">😄 Cheerful</option>
          <option value="🥳">🥳 Party</option>
          <option value="🤘">🤘 Rock</option>
          <option value="🧠">🧠 Brain</option>
          <option value="⚡">⚡ Energy</option>
        </select>
      </div>

      <button type="submit" class="btn btn-primary" style="width: 100%;">Create Profile</button>
    </form>
  </div>
</div>

<!-- PROFILE DETAIL MODAL -->
<div class="modal" id="detailModal">
  <div class="modal-content">
    <div class="modal-header">
      <h2>Profile Details</h2>
      <button class="close-btn" id="closeDetailBtn">&times;</button>
    </div>
    <div id="detailContent"></div>
  </div>
</div>

<!-- TOAST -->
<div class="toast" id="toast"></div>

<!-- FOOTER -->
<footer>
  <div class="wrap">
    <h3 style="margin-top: 0;">FresherConnect</h3>
    <p>Helping college freshers connect, make friends, and create lasting memories from day one.</p>
    <p>&copy; 2024 FresherConnect. Made with ❤️ for your batch.</p>
  </div>
</footer>

<script src="https://www.gstatic.com/firebasejs/10.7.0/firebase-app.js"></script>
<script src="https://www.gstatic.com/firebasejs/10.7.0/firebase-database.js"></script>
<script>
// Firebase Configuration - COEP FRESHERS 2030 PROJECT
const firebaseConfig = {
  apiKey: "AIzaSyDVNLKHsDRucDBRF2ThGJcLdOj7Y-0_70k",
  authDomain: "coep-freshers-2030.firebaseapp.com",
  databaseURL: "https://coep-freshers-2030-default-rtdb.firebaseio.com",
  projectId: "coep-freshers-2030",
  storageBucket: "coep-freshers-2030.firebasestorage.app",
  messagingSenderId: "645843889618",
  appId: "1:645843889618:web:c3ee7b3b218fbd7f7aac0b",
  measurementId: "G-69GCYF3C9L"
};

// Initialize Firebase
console.log("🚀 Initializing Firebase...");
firebase.initializeApp(firebaseConfig);
const db = firebase.database();
console.log("✅ Firebase initialized successfully");
console.log("📦 Project: coep-freshers-2030");

(function(){
  "use strict";

  const ICEBREAKERS = [
    "What's your go-to midnight snack?",
    "If you could learn any skill instantly, what would it be?",
    "What's the weirdest class you've taken?",
    "Favorite movie or show you'd binge?",
    "What's your hidden talent?",
    "Where do you see yourself after college?",
    "Morning person or night owl?",
    "What's your most embarrassing moment?",
    "If you could have dinner with anyone, who?",
    "What's your favorite type of cuisine?",
    "Most useless superpower you'd have?",
    "What would you name a pet robot?",
    "Best road trip story?",
    "What's your dream job?",
    "Most random thing in your room?",
  ];

  let profiles = [];
  let interests = [];
  let currentFilter = "all";
  let currentSearch = "";

  const modal = document.getElementById("createModal");
  const detailModal = document.getElementById("detailModal");
  const form = document.getElementById("profileForm");
  const interestInput = document.getElementById("interestInput");
  const interestsContainer = document.getElementById("interestsContainer");
  const profilesContainer = document.getElementById("profilesContainer");
  const searchInput = document.getElementById("searchInput");
  const filterBtns = document.querySelectorAll(".filter-btn");
  const toast = document.getElementById("toast");

  // Show toast message
  function showToast(message, duration = 3000) {
    toast.textContent = message;
    toast.classList.add("show");
    setTimeout(() => toast.classList.remove("show"), duration);
  }

  // Load profiles from Firebase in real-time
  function loadProfiles() {
    console.log("📥 Loading profiles from Firebase...");
    db.ref('profiles').on('value', (snapshot) => {
      const data = snapshot.val();
      profiles = data ? Object.values(data) : [];
      console.log("✅ Profiles loaded:", profiles.length, "profiles found");
      renderProfiles();
    }, (error) => {
      console.error("❌ Error loading profiles:", error);
      console.error("Error code:", error.code);
      console.error("Error message:", error.message);
      profilesContainer.innerHTML = `
        <div style="text-align: center; grid-column: 1/-1; padding: 40px; color: #95a5a6;">
          <p style="font-size: 1.1rem;">⚠️ Connection issue. Please refresh the page.</p>
          <p style="font-size: 0.9rem; color: #e74c3c;">Error: ${error.message}</p>
        </div>
      `;
    });
  }

  // Add interest
  function addInterest() {
    const value = interestInput.value.trim();
    if (value && interests.length < 6 && !interests.includes(value)) {
      interests.push(value);
      interestInput.value = "";
      renderInterests();
    }
  }

  // Render interests
  function renderInterests() {
    interestsContainer.innerHTML = interests.map((interest, idx) => `
      <div class="chip">
        ${interest}
        <button type="button" onclick="window.removeInterest(${idx})">×</button>
      </div>
    `).join("");
  }

  window.removeInterest = (idx) => {
    interests.splice(idx, 1);
    renderInterests();
  };

  // Interest input event
  interestInput.addEventListener("keypress", (e) => {
    if (e.key === "Enter") {
      e.preventDefault();
      addInterest();
    }
  });

  // Open create modal
  document.getElementById("createProfileBtn").addEventListener("click", () => {
    modal.classList.add("active");
    form.reset();
    interests = [];
    renderInterests();
  });

  document.getElementById("closeModalBtn").addEventListener("click", () => {
    modal.classList.remove("active");
  });

  document.getElementById("closeDetailBtn").addEventListener("click", () => {
    detailModal.classList.remove("active");
  });

  // Close modal on outside click
  modal.addEventListener("click", (e) => {
    if (e.target === modal) modal.classList.remove("active");
  });

  detailModal.addEventListener("click", (e) => {
    if (e.target === detailModal) detailModal.classList.remove("active");
  });

  // Form submission
  form.addEventListener("submit", (e) => {
    e.preventDefault();
    
    const profile = {
      id: Date.now(),
      name: document.getElementById("name").value,
      branch: document.getElementById("branch").value,
      hometown: document.getElementById("hometown").value,
      bio: document.getElementById("bio").value,
      interests: interests,
      contact: document.getElementById("contact").value,
      avatar: document.getElementById("avatar").value,
      createdAt: new Date().toLocaleDateString()
    };

    console.log("💾 Saving profile:", profile);
    // Save to Firebase
    db.ref('profiles/' + profile.id).set(profile, (error) => {
      if (error) {
        console.error("❌ Error saving profile:", error);
        showToast("❌ Failed to save profile. Try again.");
      } else {
        console.log("✅ Profile saved successfully");
        modal.classList.remove("active");
        form.reset();
        interests = [];
        renderInterests();
        showToast("✅ Profile created! Your batch can now see you.");
      }
    });
  });

  // Search functionality
  searchInput.addEventListener("input", (e) => {
    currentSearch = e.target.value.toLowerCase();
    renderProfiles();
  });

  // Filter functionality
  filterBtns.forEach(btn => {
    btn.addEventListener("click", () => {
      filterBtns.forEach(b => b.classList.remove("active"));
      btn.classList.add("active");
      currentFilter = btn.dataset.filter;
      renderProfiles();
    });
  });

  // Filter profiles
  function getFilteredProfiles() {
    return profiles.filter(profile => {
      const matchFilter = currentFilter === "all" || profile.branch === currentFilter;
      const matchSearch = currentSearch === "" || 
        profile.name.toLowerCase().includes(currentSearch) ||
        profile.hometown.toLowerCase().includes(currentSearch) ||
        (profile.interests && profile.interests.some(i => i.toLowerCase().includes(currentSearch)));
      return matchFilter && matchSearch;
    });
  }

  // Render profiles
  function renderProfiles() {
    const filtered = getFilteredProfiles();
    
    if (profiles.length === 0) {
      profilesContainer.innerHTML = `
        <div style="text-align: center; grid-column: 1/-1; padding: 40px; color: #95a5a6;">
          <p style="font-size: 1.1rem;">No profiles yet. Be the first to create one! 👇</p>
        </div>
      `;
      return;
    }

    if (filtered.length === 0) {
      profilesContainer.innerHTML = `
        <div style="text-align: center; grid-column: 1/-1; padding: 40px; color: #95a5a6;">
          <p style="font-size: 1.1rem;">No matches found. Try adjusting your search or filter.</p>
        </div>
      `;
      return;
    }

    profilesContainer.innerHTML = filtered.map(profile => `
      <div class="profile-card" onclick="window.showProfileDetail(${profile.id})">
        <div class="profile-header">
          <div class="profile-avatar">${profile.avatar}</div>
          <div class="profile-name">${profile.name}</div>
          <div class="profile-branch">${profile.branch.toUpperCase()}</div>
        </div>
        <div class="profile-body">
          <div class="profile-info">
            <div class="info-item">
              <span class="info-label">📍</span>
              <span>${profile.hometown}</span>
            </div>
            ${profile.bio ? `
              <div class="info-item">
                <span class="info-label">✍️</span>
                <span>${profile.bio.substring(0, 50)}${profile.bio.length > 50 ? '...' : ''}</span>
              </div>
            ` : ''}
          </div>
          ${profile.interests && profile.interests.length > 0 ? `
            <div class="interests">
              ${profile.interests.slice(0, 3).map(i => `<span class="interest-tag">${i}</span>`).join('')}
              ${profile.interests.length > 3 ? `<span class="interest-tag">+${profile.interests.length - 3}</span>` : ''}
            </div>
          ` : ''}
          <div class="profile-actions">
            <button class="action-btn">Connect</button>
            <button class="action-btn">Message</button>
          </div>
        </div>
      </div>
    `).join("");
  }

  // Show profile detail
  window.showProfileDetail = (id) => {
    const profile = profiles.find(p => p.id === id);
    if (!profile) return;

    const icebreaker = ICEBREAKERS[Math.floor(Math.random() * ICEBREAKERS.length)];

    document.getElementById("detailContent").innerHTML = `
      <div style="text-align: center;">
        <div class="profile-avatar" style="width: 120px; height: 120px; font-size: 4rem; margin: 0 auto 20px;">
          ${profile.avatar}
        </div>
        <h2>${profile.name}</h2>
        <p style="color: var(--primary); font-weight: 600; margin: 8px 0;">${profile.branch.toUpperCase()}</p>
        <p style="color: var(--gray); margin-bottom: 16px;">📍 From ${profile.hometown}</p>
      </div>

      ${profile.bio ? `
        <div style="margin: 24px 0; padding: 16px; background: #f5f7fa; border-radius: 8px;">
          <p style="margin: 0;">${profile.bio}</p>
        </div>
      ` : ''}

      ${profile.interests && profile.interests.length > 0 ? `
        <div style="margin: 20px 0;">
          <p style="font-weight: 600; margin-bottom: 12px;">Interests:</p>
          <div class="interests">
            ${profile.interests.map(i => `<span class="interest-tag">${i}</span>`).join('')}
          </div>
        </div>
      ` : ''}

      <div style="margin: 24px 0; padding: 16px; background: #ffe66d; border-radius: 8px; color: var(--dark);">
        <p style="font-weight: 600; margin: 0 0 8px 0;">🎲 Icebreaker:</p>
        <p style="margin: 0; font-style: italic;">"${icebreaker}"</p>
      </div>

      ${profile.contact ? `
        <div style="margin: 20px 0; padding: 12px; background: #f5f7fa; border-radius: 8px;">
          <p style="font-weight: 600; margin-bottom: 8px;">Contact:</p>
          <p style="margin: 0; word-break: break-all;">${profile.contact}</p>
        </div>
      ` : ''}

      <div style="margin-top: 24px; display: flex; gap: 12px;">
        <button class="btn btn-primary" style="flex: 1;" onclick="navigator.clipboard.writeText('Check out ${profile.name} on FresherConnect!'); window.showToast('Copied!')">📋 Copy</button>
        <button class="btn btn-secondary" style="flex: 1;" onclick="document.getElementById('detailModal').classList.remove('active')">Close</button>
      </div>
    `;

    detailModal.classList.add("active");
  };

  // Share functionality
  function shareBoard() {
    const url = window.location.href;
    if (navigator.share) {
      navigator.share({
        title: "FresherConnect",
        text: "Meet your college batch! Create your profile and connect with classmates.",
        url: url
      }).catch(err => console.log("Error sharing:", err));
    } else {
      navigator.clipboard.writeText(url).then(() => {
        showToast("🔗 Link copied! Share with your batch.");
      });
    }
  }

  document.getElementById("shareNavBtn").addEventListener("click", shareBoard);

  // Expose showToast globally
  window.showToast = showToast;

  // Initialize
  console.log("🎯 Application initializing...");
  loadProfiles();
})();
</script>
</body>
</html>
