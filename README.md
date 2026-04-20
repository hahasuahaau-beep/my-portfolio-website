# my-portfolio-website
my intro (bio or technical


<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Dhannaram | AI & Data Science</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:ital,wght@0,300;0,400;0,500;1,300&display=swap" rel="stylesheet"/>
<style>
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

:root {
  --navy:    #0d1b2e;
  --navy2:   #122240;
  --accent:  #2d6cdf;
  --accent2: #4e8ef7;
  --gold:    #f0a500;
  --text:    #e8edf8;
  --muted:   #7a8eae;
  --card:    rgba(255,255,255,0.04);
  --border:  rgba(255,255,255,0.08);
  --ff-head: 'Syne', sans-serif;
  --ff-body: 'DM Sans', sans-serif;
}

html { scroll-behavior: smooth; }

body {
  font-family: var(--ff-body);
  background: var(--navy);
  color: var(--text);
  overflow-x: hidden;
  cursor: none;
}

.cursor {
  width: 12px; height: 12px;
  background: var(--accent2);
  border-radius: 50%;
  position: fixed; top: 0; left: 0;
  pointer-events: none;
  z-index: 9999;
  transition: transform 0.15s ease, background 0.2s;
  transform: translate(-50%,-50%);
}
.cursor-ring {
  width: 36px; height: 36px;
  border: 1.5px solid var(--accent2);
  border-radius: 50%;
  position: fixed; top: 0; left: 0;
  pointer-events: none;
  z-index: 9998;
  transition: transform 0.35s cubic-bezier(.25,.46,.45,.94), opacity 0.3s;
  transform: translate(-50%,-50%);
  opacity: 0.5;
}
body:hover .cursor { opacity: 1; }

body::before {
  content: '';
  position: fixed; inset: 0;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
  pointer-events: none;
  z-index: 0;
}

body::after {
  content: '';
  position: fixed; inset: 0;
  background-image:
    linear-gradient(rgba(45,108,223,0.04) 1px, transparent 1px),
    linear-gradient(90deg, rgba(45,108,223,0.04) 1px, transparent 1px);
  background-size: 60px 60px;
  pointer-events: none;
  z-index: 0;
}

nav {
  position: fixed; top: 0; left: 0; right: 0;
  z-index: 100;
  padding: 20px 48px;
  display: flex; align-items: center; justify-content: space-between;
  transition: background 0.4s, backdrop-filter 0.4s;
}
nav.scrolled {
  background: rgba(13,27,46,0.85);
  backdrop-filter: blur(16px);
  border-bottom: 1px solid var(--border);
}
.nav-logo {
  font-family: var(--ff-head);
  font-size: 22px; font-weight: 800;
  color: var(--text); text-decoration: none; letter-spacing: -0.5px;
}
.nav-logo span { color: var(--accent2); }
.nav-links { display: flex; gap: 36px; list-style: none; }
.nav-links a {
  font-size: 13px; font-weight: 500; letter-spacing: 1.2px;
  text-transform: uppercase; color: var(--muted);
  text-decoration: none; transition: color 0.2s; position: relative;
}
.nav-links a::after {
  content: ''; position: absolute; bottom: -4px; left: 0;
  width: 0; height: 1.5px; background: var(--accent2); transition: width 0.3s ease;
}
.nav-links a:hover { color: var(--text); }
.nav-links a:hover::after { width: 100%; }

.hamburger { display: none; flex-direction: column; gap: 5px; cursor: pointer; z-index: 200; }
.hamburger span { width: 24px; height: 2px; background: var(--text); border-radius: 2px; transition: all 0.3s; }
.hamburger.open span:nth-child(1) { transform: rotate(45deg) translate(5px,5px); }
.hamburger.open span:nth-child(2) { opacity: 0; }
.hamburger.open span:nth-child(3) { transform: rotate(-45deg) translate(5px,-5px); }

.mobile-menu {
  display: none; position: fixed; inset: 0;
  background: var(--navy); z-index: 150;
  flex-direction: column; align-items: center; justify-content: center; gap: 36px;
}
.mobile-menu.open { display: flex; }
.mobile-menu a {
  font-family: var(--ff-head); font-size: 32px; font-weight: 700;
  color: var(--text); text-decoration: none; transition: color 0.2s;
}
.mobile-menu a:hover { color: var(--accent2); }

#hero {
  min-height: 100vh; display: flex; align-items: center;
  padding: 120px 48px 80px; position: relative; z-index: 1;
}
.hero-inner {
  max-width: 1100px; margin: 0 auto; width: 100%;
  display: grid; grid-template-columns: 1fr 380px; gap: 60px; align-items: center;
}
.hero-tag {
  display: inline-flex; align-items: center; gap: 8px;
  font-size: 11px; font-weight: 500; letter-spacing: 2px;
  text-transform: uppercase; color: var(--accent2);
  border: 1px solid rgba(78,142,247,0.3);
  padding: 6px 14px; border-radius: 20px; margin-bottom: 28px;
  animation: fadeUp 0.7s ease both;
}
.hero-tag::before {
  content: ''; width: 6px; height: 6px;
  border-radius: 50%; background: var(--accent2); animation: pulse 2s infinite;
}
@keyframes pulse {
  0%,100% { opacity:1; transform:scale(1); }
  50% { opacity:0.4; transform:scale(0.8); }
}
.hero-name {
  font-family: var(--ff-head); font-size: clamp(52px, 7vw, 88px);
  font-weight: 800; line-height: 0.95; letter-spacing: -3px;
  color: var(--text); animation: fadeUp 0.7s 0.1s ease both;
}
.hero-name .highlight { color: transparent; -webkit-text-stroke: 1.5px var(--accent2); }
.hero-role {
  font-size: 18px; font-weight: 300; color: var(--muted);
  margin: 20px 0 32px; line-height: 1.6; animation: fadeUp 0.7s 0.2s ease both;
}
.hero-role strong { color: var(--text); font-weight: 500; }
.hero-btns { display: flex; gap: 16px; flex-wrap: wrap; animation: fadeUp 0.7s 0.3s ease both; }

.btn-primary {
  padding: 14px 32px; background: var(--accent); color: #fff;
  border: none; border-radius: 6px; font-family: var(--ff-body);
  font-size: 14px; font-weight: 500; cursor: pointer; text-decoration: none;
  display: inline-flex; align-items: center; gap: 8px;
  transition: transform 0.2s, box-shadow 0.2s;
}
.btn-primary:hover { transform: translateY(-2px); box-shadow: 0 8px 30px rgba(45,108,223,0.45); }
.btn-outline {
  padding: 14px 32px; background: transparent; color: var(--text);
  border: 1.5px solid var(--border); border-radius: 6px;
  font-family: var(--ff-body); font-size: 14px; font-weight: 500;
  cursor: pointer; text-decoration: none; transition: border-color 0.2s, background 0.2s;
}
.btn-outline:hover { border-color: var(--accent2); background: rgba(78,142,247,0.07); }

.hero-card {
  background: var(--card); border: 1px solid var(--border); border-radius: 20px;
  padding: 36px; backdrop-filter: blur(10px);
  animation: fadeUp 0.7s 0.4s ease both; position: relative; overflow: hidden;
}
.hero-card::before {
  content: ''; position: absolute; top: -60px; right: -60px;
  width: 180px; height: 180px; border-radius: 50%;
  background: radial-gradient(circle, rgba(45,108,223,0.2), transparent 70%);
}
.hero-avatar {
  width: 80px; height: 80px; border-radius: 50%;
  background: linear-gradient(135deg,#4e8ef7,#1a4fa0);
  display: flex; align-items: center; justify-content: center;
  font-family: var(--ff-head); font-size: 32px; font-weight: 800;
  color: #fff; margin-bottom: 20px; border: 3px solid rgba(255,255,255,0.15);
}
.hero-card h3 { font-family: var(--ff-head); font-size: 22px; font-weight: 700; margin-bottom: 4px; }
.hero-card p { font-size: 13px; color: var(--muted); margin-bottom: 20px; }
.hero-stats { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
.stat { background: rgba(255,255,255,0.04); border: 1px solid var(--border); border-radius: 10px; padding: 12px; }
.stat-num { font-family: var(--ff-head); font-size: 24px; font-weight: 800; color: var(--accent2); }
.stat-label { font-size: 11px; color: var(--muted); margin-top: 2px; }

.hero-scroll {
  position: absolute; bottom: 40px; left: 50%; transform: translateX(-50%);
  display: flex; flex-direction: column; align-items: center; gap: 8px;
  animation: fadeUp 0.7s 0.6s ease both;
}
.hero-scroll span { font-size: 10px; letter-spacing: 2px; text-transform: uppercase; color: var(--muted); }
.scroll-line {
  width: 1px; height: 40px;
  background: linear-gradient(to bottom, var(--accent2), transparent);
  animation: scrollPulse 2s infinite;
}
@keyframes scrollPulse { 0%,100% { opacity:0.3; } 50% { opacity:1; } }

section { position: relative; z-index: 1; }
.container { max-width: 1100px; margin: 0 auto; padding: 100px 48px; }

.section-label {
  font-size: 11px; font-weight: 500; letter-spacing: 2.5px;
  text-transform: uppercase; color: var(--accent2); margin-bottom: 12px;
  display: flex; align-items: center; gap: 12px;
}
.section-label::before { content: ''; width: 30px; height: 1.5px; background: var(--accent2); }
.section-title {
  font-family: var(--ff-head); font-size: clamp(32px, 4vw, 48px);
  font-weight: 800; letter-spacing: -1.5px; line-height: 1.1;
  margin-bottom: 56px; color: var(--text);
}

.reveal { opacity: 0; transform: translateY(32px); transition: opacity 0.7s ease, transform 0.7s ease; }
.reveal.visible { opacity: 1; transform: translateY(0); }

#about { background: linear-gradient(to bottom, var(--navy), var(--navy2)); }
.about-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 60px; align-items: start; }
.about-text p { font-size: 16px; line-height: 1.85; color: #b0bdda; margin-bottom: 20px; }
.about-text p strong { color: var(--text); font-weight: 500; }
.about-info { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; margin-top: 32px; }
.info-item { padding: 14px 16px; background: var(--card); border: 1px solid var(--border); border-radius: 10px; }
.info-label { font-size: 10px; letter-spacing: 1.5px; text-transform: uppercase; color: var(--muted); margin-bottom: 4px; }
.info-value { font-size: 13px; font-weight: 500; color: var(--text); }

.skills-wrap { display: flex; flex-direction: column; gap: 18px; }
.skill-group-title {
  font-family: var(--ff-head); font-size: 13px; font-weight: 700;
  letter-spacing: 1px; text-transform: uppercase; color: var(--muted); margin-bottom: 16px;
}
.skill-bar-item { margin-bottom: 14px; }
.skill-bar-top { display: flex; justify-content: space-between; font-size: 13px; margin-bottom: 6px; }
.skill-bar-name { color: var(--text); font-weight: 500; }
.skill-bar-pct  { color: var(--accent2); font-weight: 600; font-size: 12px; }
.skill-bar-bg   { height: 6px; background: rgba(255,255,255,0.07); border-radius: 6px; overflow: hidden; }
.skill-bar-fill {
  height: 100%; border-radius: 6px;
  background: linear-gradient(90deg, var(--accent), var(--accent2));
  width: 0; transition: width 1.2s cubic-bezier(0.4, 0, 0.2, 1);
}
.tool-tags { display: flex; flex-wrap: wrap; gap: 8px; margin-top: 8px; }
.tool-tag {
  font-size: 12px; padding: 5px 12px;
  background: rgba(45,108,223,0.1); border: 1px solid rgba(45,108,223,0.2);
  border-radius: 20px; color: var(--accent2); transition: background 0.2s;
}
.tool-tag:hover { background: rgba(45,108,223,0.2); }

#education { background: var(--navy); }
.edu-timeline { position: relative; padding-left: 30px; }
.edu-timeline::before {
  content: ''; position: absolute; left: 5px; top: 6px; bottom: 6px;
  width: 2px; background: linear-gradient(to bottom, var(--accent), transparent);
}
.edu-item { position: relative; margin-bottom: 48px; padding-left: 30px; }
.edu-item::before {
  content: ''; position: absolute; left: -30px; top: 5px;
  width: 12px; height: 12px; border-radius: 50%;
  background: var(--accent); border: 2px solid var(--navy);
  box-shadow: 0 0 0 3px rgba(45,108,223,0.3);
}
.edu-badge {
  display: inline-block; font-size: 10px; font-weight: 600;
  letter-spacing: 1px; text-transform: uppercase;
  padding: 3px 10px; border-radius: 20px;
  background: rgba(45,108,223,0.15); color: var(--accent2);
  border: 1px solid rgba(45,108,223,0.2); margin-bottom: 10px;
}
.edu-title { font-family: var(--ff-head); font-size: 20px; font-weight: 700; color: var(--text); margin-bottom: 4px; }
.edu-school { font-size: 14px; color: var(--muted); margin-bottom: 10px; }
.edu-desc { font-size: 13.5px; color: #7a8eae; line-height: 1.7; }
.edu-subjects { display: flex; flex-wrap: wrap; gap: 6px; margin-top: 12px; }
.subject-tag { font-size: 11px; padding: 3px 10px; background: var(--card); border: 1px solid var(--border); border-radius: 4px; color: var(--muted); }

#projects { background: var(--navy2); }
.projects-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 24px; }
.proj-card {
  background: var(--card); border: 1px solid var(--border); border-radius: 16px;
  padding: 28px; position: relative; overflow: hidden;
  transition: transform 0.3s ease, border-color 0.3s, box-shadow 0.3s; cursor: pointer;
}
.proj-card:hover {
  transform: translateY(-6px); border-color: rgba(78,142,247,0.3);
  box-shadow: 0 20px 60px rgba(0,0,0,0.3), 0 0 0 1px rgba(78,142,247,0.1);
}
.proj-card::before {
  content: ''; position: absolute; top: 0; left: 0; right: 0; height: 3px;
  background: linear-gradient(90deg, var(--accent), var(--accent2));
  transform: scaleX(0); transform-origin: left; transition: transform 0.4s ease;
}
.proj-card:hover::before { transform: scaleX(1); }
.proj-card.featured { grid-column: span 2; display: grid; grid-template-columns: 1fr 1fr; gap: 32px; align-items: center; }
.proj-card.featured::before { transform: scaleX(1); }
.proj-num { font-family: var(--ff-head); font-size: 11px; font-weight: 700; color: var(--accent2); letter-spacing: 1.5px; margin-bottom: 16px; opacity: 0.6; }
.proj-title { font-family: var(--ff-head); font-size: 20px; font-weight: 700; color: var(--text); margin-bottom: 10px; }
.proj-desc { font-size: 13.5px; color: #7a8eae; line-height: 1.7; margin-bottom: 20px; }
.proj-techs { display: flex; flex-wrap: wrap; gap: 6px; }
.tech-badge {
  font-size: 11px; font-weight: 600; padding: 4px 10px; border-radius: 4px;
  background: rgba(45,108,223,0.12); color: var(--accent2); border: 1px solid rgba(45,108,223,0.2);
}
.proj-status {
  font-size: 10px; font-weight: 600; letter-spacing: 1px; text-transform: uppercase;
  display: inline-flex; align-items: center; gap: 5px; margin-top: 12px; color: var(--muted);
}
.proj-status.progress { color: var(--gold); }
.proj-status.planned  { color: var(--muted); }
.proj-status::before  { content: ''; width: 5px; height: 5px; border-radius: 50%; background: currentColor; }
.proj-visual {
  background: linear-gradient(135deg, rgba(45,108,223,0.15), rgba(78,142,247,0.05));
  border: 1px solid rgba(45,108,223,0.15); border-radius: 12px; height: 180px;
  display: flex; align-items: center; justify-content: center;
}
.proj-icon { font-size: 52px; opacity: 0.6; filter: drop-shadow(0 0 20px rgba(78,142,247,0.5)); }

#certifications { background: var(--navy); }
.cert-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 20px; }
.cert-card {
  background: var(--card); border: 1px solid var(--border); border-radius: 14px;
  padding: 24px; display: flex; align-items: flex-start; gap: 16px;
  transition: transform 0.3s, border-color 0.3s;
}
.cert-card:hover { transform: translateY(-4px); border-color: rgba(78,142,247,0.25); }
.cert-icon {
  width: 42px; height: 42px; border-radius: 10px; flex-shrink: 0;
  background: linear-gradient(135deg, rgba(45,108,223,0.25), rgba(78,142,247,0.1));
  display: flex; align-items: center; justify-content: center;
  font-size: 20px; border: 1px solid rgba(45,108,223,0.2);
}
.cert-title  { font-size: 14px; font-weight: 600; color: var(--text); margin-bottom: 4px; }
.cert-source { font-size: 12px; color: var(--muted); }
.cert-status { font-size: 10px; font-weight: 600; letter-spacing: 0.8px; text-transform: uppercase; color: #4caf50; margin-top: 6px; }
.cert-status.ongoing { color: var(--gold); }

#contact { background: var(--navy2); }
.contact-inner { display: grid; grid-template-columns: 1fr 1fr; gap: 80px; align-items: start; }
.contact-left h2 {
  font-family: var(--ff-head); font-size: clamp(32px, 4vw, 52px);
  font-weight: 800; letter-spacing: -2px; line-height: 1.1; color: var(--text); margin-bottom: 20px;
}
.contact-left p { font-size: 15px; color: var(--muted); line-height: 1.8; margin-bottom: 36px; }
.contact-links { display: flex; flex-direction: column; gap: 14px; }
.contact-link {
  display: flex; align-items: center; gap: 14px; padding: 16px 20px;
  background: var(--card); border: 1px solid var(--border); border-radius: 12px;
  text-decoration: none; color: var(--text); font-size: 14px;
  transition: border-color 0.2s, transform 0.2s;
}
.contact-link:hover { border-color: rgba(78,142,247,0.3); transform: translateX(4px); }
.contact-link-icon {
  width: 36px; height: 36px; border-radius: 8px; background: rgba(45,108,223,0.15);
  display: flex; align-items: center; justify-content: center; font-size: 16px; flex-shrink: 0;
}
.contact-link-label { font-size: 11px; color: var(--muted); margin-bottom: 1px; text-transform: uppercase; letter-spacing: 0.8px; }
.contact-link-val   { font-size: 13px; font-weight: 500; }

.contact-form { display: flex; flex-direction: column; gap: 16px; }
.form-group { display: flex; flex-direction: column; gap: 7px; }
.form-group label { font-size: 11px; font-weight: 600; letter-spacing: 1px; text-transform: uppercase; color: var(--muted); }
.form-group input,
.form-group textarea {
  background: var(--card); border: 1px solid var(--border); border-radius: 10px;
  padding: 14px 16px; color: var(--text); font-family: var(--ff-body);
  font-size: 14px; outline: none; transition: border-color 0.2s; resize: none;
}
.form-group input:focus,
.form-group textarea:focus { border-color: var(--accent2); }
.form-group input::placeholder,
.form-group textarea::placeholder { color: var(--muted); }
.form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; }
.btn-send {
  padding: 15px 36px; background: linear-gradient(135deg, var(--accent), #1f5bbf);
  color: #fff; border: none; border-radius: 10px; font-family: var(--ff-body);
  font-size: 14px; font-weight: 600; cursor: pointer;
  display: flex; align-items: center; justify-content: center; gap: 8px;
  transition: transform 0.2s, box-shadow 0.2s; box-shadow: 0 4px 20px rgba(45,108,223,0.3);
}
.btn-send:hover { transform: translateY(-2px); box-shadow: 0 8px 30px rgba(45,108,223,0.5); }

footer {
  position: relative; z-index: 1; border-top: 1px solid var(--border);
  padding: 32px 48px; display: flex; align-items: center; justify-content: space-between;
  background: var(--navy);
}
footer p { font-size: 13px; color: var(--muted); }
.footer-logo { font-family: var(--ff-head); font-size: 18px; font-weight: 800; color: var(--text); }
.footer-logo span { color: var(--accent2); }

@keyframes fadeUp {
  from { opacity:0; transform:translateY(24px); }
  to   { opacity:1; transform:translateY(0); }
}

@media (max-width: 900px) {
  nav { padding: 18px 24px; }
  .nav-links { display: none; }
  .hamburger { display: flex; }
  #hero { padding: 100px 24px 60px; }
  .hero-inner { grid-template-columns: 1fr; }
  .hero-card  { display: none; }
  .container  { padding: 70px 24px; }
  .about-grid, .contact-inner { grid-template-columns: 1fr; gap: 40px; }
  .projects-grid { grid-template-columns: 1fr; }
  .proj-card.featured { grid-column: span 1; grid-template-columns: 1fr; }
  .proj-visual { display: none; }
  .cert-grid  { grid-template-columns: 1fr 1fr; }
  footer { flex-direction: column; gap: 12px; text-align: center; padding: 24px; }
}
@media (max-width: 600px) {
  .cert-grid  { grid-template-columns: 1fr; }
  .hero-btns  { flex-direction: column; }
  .btn-primary, .btn-outline { text-align: center; justify-content: center; }
  .form-row   { grid-template-columns: 1fr; }
  .about-info { grid-template-columns: 1fr; }
}
</style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<nav id="navbar">
  <a href="#hero" class="nav-logo">D<span>.</span></a>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#education">Education</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#certifications">Certs</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
  <div class="hamburger" id="hamburger">
    <span></span><span></span><span></span>
  </div>
</nav>

<div class="mobile-menu" id="mobileMenu">
  <a href="#about"          class="mobile-link">About</a>
  <a href="#education"      class="mobile-link">Education</a>
  <a href="#projects"       class="mobile-link">Projects</a>
  <a href="#certifications" class="mobile-link">Certs</a>
  <a href="#contact"        class="mobile-link">Contact</a>
</div>

<!-- HERO -->
<section id="hero">
  <div class="hero-inner">
    <div class="hero-left">
      <div class="hero-tag">Available for Internships</div>
      <h1 class="hero-name">Dhan<br><span class="highlight">naram</span></h1>
      <p class="hero-role">
        B.E. Student in <strong>Artificial Intelligence</strong><br>
        &amp; <strong>Data Science</strong> · MBM University, Jodhpur
      </p>
      <div class="hero-btns">
        <a href="#projects" class="btn-primary"><span>View Projects</span><span>&#8594;</span></a>
        <a href="#contact"  class="btn-outline">Get in Touch</a>
      </div>
    </div>
    <div class="hero-card">
      <div class="hero-avatar">D</div>
      <h3>Dhannaram</h3>
      <p>Jodhpur, Rajasthan, India</p>
      <div class="hero-stats">
        <div class="stat"><div class="stat-num">4+</div><div class="stat-label">Projects Built</div></div>
        <div class="stat"><div class="stat-num">6+</div><div class="stat-label">Certifications</div></div>
        <div class="stat"><div class="stat-num">5</div><div class="stat-label">Languages</div></div>
        <div class="stat"><div class="stat-num">2024</div><div class="stat-label">Batch</div></div>
      </div>
    </div>
  </div>
  <div class="hero-scroll">
    <span>Scroll</span>
    <div class="scroll-line"></div>
  </div>
</section>

<!-- ABOUT -->
<section id="about">
  <div class="container">
    <div class="section-label reveal">About Me</div>
    <h2 class="section-title reveal">Passionate about AI<br>&amp; Building Things</h2>
    <div class="about-grid">
      <div class="about
