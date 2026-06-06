<!-- 🌓 PocketPython Core UI Engine (Favicon + Dark Mode + Footer Remover + Gravity Easter Egg) -->
<link rel="icon" href="data:image/svg+xml,<svg xmlns=%22http://w3.org viewBox=%220 0 100 100%22><rect width=%22100%22 height=%22100%22 rx=%2225%22 fill=%22%23161b22%22/><text x=%2250%%22 y=%2272%%22 font-size=%2265%22 font-family=%22sans-serif%22 font-weight=%22900%22 fill=%22%2339d353%22 text-anchor=%22middle%22>P</text></svg>">

<div style="text-align: right; margin: 15px 0;">
  <button id="theme-toggle-btn" style="padding: 8px 16px; border-radius: 20px; border: 1px solid #ccc; background: #ffffff; color: #24292e; cursor: pointer; font-weight: bold; font-family: sans-serif; transition: all 0.2s ease;">🌙 Dark Mode</button>
</div>

<style>
  /* 🚫 Completely delete the footer */
  footer, .site-footer, .footer {
    display: none !important;
  }

  /* 🌓 Dark Mode configurations */
  body.dark-mode-active {
    background-color: #0d1117 !important;
    color: #c9d1d9 !important;
  }
  body.dark-mode-active h1, body.dark-mode-active h2, body.dark-mode-active h3, body.dark-mode-active h4 {
    color: #f0f6fc !important;
    border-bottom-color: #21262d !important;
  }
  body.dark-mode-active a {
    color: #58a6ff !important;
  }
  body.dark-mode-active code {
    background-color: #161b22 !important;
    color: #ff7b72 !important;
  }
  body.dark-mode-active pre {
    background-color: #161b22 !important;
    border: 1px solid #21262d !important;
  }
  body.dark-mode-active hr {
    background-color: #21262d !important;
    border: none !important;
    height: 1px !important;
  }
  body.dark-mode-active #theme-toggle-btn {
    background: #21262d !important;
    color: #f0f6fc !important;
    border-color: #30363d !important;
  }
</style>

<script>
  // ==========================================
  // 1. DARK MODE TOGGLE LOGIC
  // ==========================================
  const themeButton = document.getElementById('theme-toggle-btn');
  const userSystemDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
  const currentSavedTheme = localStorage.getItem('site-theme');

  if (currentSavedTheme === 'dark' || (!currentSavedTheme && userSystemDark)) {
    document.body.classList.add('dark-mode-active');
    themeButton.textContent = '☀️ Light Mode';
  }

  themeButton.addEventListener('click', () => {
    document.body.classList.toggle('dark-mode-active');
    const isNowDark = document.body.classList.contains('dark-mode-active');
    localStorage.setItem('site-theme', isNowDark ? 'dark' : 'light');
    themeButton.textContent = isNowDark ? '☀️ Light Mode' : '🌙 Dark Mode';
  });

  // ==========================================
  // 2. GRAVITY PHYSICS ENGINE LOGIC
  // ==========================================
  let secretKeyBuffer = "";
  let physicsActive = false;
  let animationFrameId = null;
  let itemsArray = [];

  document.addEventListener("keydown", (e) => {
    if (e.key === "Escape" && physicsActive) {
      resetWebpageGravity();
      return;
    }

    secretKeyBuffer += e.key.toLowerCase();
    if (secretKeyBuffer.length > 6) {
      secretKeyBuffer = secretKeyBuffer.slice(-6);
    }
    if (secretKeyBuffer === "python") {
      if (!physicsActive) activateWebpageGravity();
      secretKeyBuffer = "";
    }
  });

  function activateWebpageGravity() {
    physicsActive = true;
    const components = document.querySelectorAll('h1, h2, h3, h4, p, li, a, hr, footer, span, button, .site-footer');
    itemsArray = [];

    components.forEach((element) => {
      element.style.position = 'relative';
      element.style.display = 'inline-block';
      element.style.transformOrigin = 'center';
      element.style.transition = 'none';

      itemsArray.push({
        domNode: element,
        posY: 0,
        posX: 0,
        velY: 1 + Math.random() * 2,
        velX: (Math.random() - 0.5) * 4,
        degRot: 0,
        velRot: (Math.random() - 0.5) * 6,
        bounceCount: 0
      });
    });

    const gravityForce = 0.35;
    const bounceAbsorption = -0.55;

    function runPhysicsLoop() {
      if (!physicsActive) return;
      const windowFloor = window.innerHeight;

      itemsArray.forEach((item) => {
        const bounds = item.domNode.getBoundingClientRect();
        item.velY += gravityForce;
        item.posY += item.velY;
        item.posX += item.velX;
        item.degRot += item.velRot;

        if (bounds.bottom + item.velY > windowFloor) {
          if (item.bounceCount < 3) {
            item.velY *= bounceAbsorption;
            item.bounceCount++;
          } else {
            item.velY = 0;
            item.velX = 0;
            item.velRot = 0;
          }
        }

        item.domNode.style.transform = `translate(${item.posX}px, ${item.posY}px) rotate(${item.degRot}deg)`;
      });

      animationFrameId = requestAnimationFrame(runPhysicsLoop);
    }

    runPhysicsLoop();
  }

  function resetWebpageGravity() {
    physicsActive = false;
    cancelAnimationFrame(animationFrameId);
    itemsArray.forEach((item) => {
      item.domNode.style.transform = '';
      item.domNode.style.position = '';
      item.domNode.style.display = '';
      item.domNode.style.transformOrigin = '';
      item.domNode.style.transition = '';
    });
  }
</script>

A portable, zero-installation Python development environment.

⚠️ **Notice:** This project exclusively supports **Python 3.14.0+**.

---

### 📥 Available Packages

* 📦 **[Download Standard Archive (ZIP)](https://github.com/m97493578-ops/PocketPython/releases/)**
  * Optimized for restricted school environments.
  * Requires manual folder extraction.
* 🚀 **[Download Self-Extractor (EXE SFX)](https://github.com/m97493578-ops/PocketPython/releases/)**
  * Automatically unpacks without third-party tools.
  * Ideal for quick local deployments.

---

## ✨ Features

* **No Admin Rights:** Runs entirely in user folders.
* **Fully Portable:** Carry it on a USB drive.
* **Latest Runtime:** Pre-configured for upcoming Python 3.14 features.

---

## 🚀 Quick Start Guide

1. Download the latest version from the **[Releases Page](https://github.com/m97493578-ops/PocketPython/releases/)**.
2. Unpack or extract the file into your local folder (e.g., Documents or USB).
3. Open the folder and run `python.exe` to start coding.

---

## ❓ Q&A (Frequently Asked Questions)

#### Q: Do I need admin rights to install this on school computers?
**A:** No. PocketPython is completely portable and executes safely from user directories.

#### Q: Why does this project only support Python 3.14.0 and up?
**A:** It utilizes modern core optimizations and new interpreter features unique to Python 3.14.

#### Q: Can I run third-party libraries (like NumPy or Requests)?
**A:** Yes. You can install packages locally using the built-in package manager included in the archive.

#### Q: How do I remove PocketPython from a computer?
**A:** Simply delete the extracted folder. It leaves zero traces or registry keys behind.

---

## ⚖️ License

This project is open-source software licensed under the **MIT License**. Feel free to use, modify, and distribute it.
