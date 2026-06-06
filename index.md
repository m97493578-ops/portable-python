<!-- 🌓 PocketPython Theme Toggle Component -->
<div style="text-align: right; margin: 15px 0;">
  <button id="theme-toggle-btn" style="padding: 8px 16px; border-radius: 20px; border: 1px solid #ccc; background: #ffffff; color: #24292e; cursor: pointer; font-weight: bold; font-family: sans-serif; transition: all 0.2s ease;">🌙 Dark Mode</button>
</div>

<style>
  /* Explicit overrides for default GitHub Pages themes */
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
  const themeButton = document.getElementById('theme-toggle-btn');
  const userSystemDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
  const currentSavedTheme = localStorage.getItem('site-theme');

  // Apply dark mode if preferred or previously saved
  if (currentSavedTheme === 'dark' || (!currentSavedTheme && userSystemDark)) {
    document.body.classList.add('dark-mode-active');
    themeButton.textContent = '☀️ Light Mode';
  }

  // Handle active click events
  themeButton.addEventListener('click', () => {
    document.body.classList.toggle('dark-mode-active');
    const isNowDark = document.body.classList.contains('dark-mode-active');
    localStorage.setItem('site-theme', isNowDark ? 'dark' : 'light');
    themeButton.textContent = isNowDark ? '☀️ Light Mode' : '🌙 Dark Mode';
  });
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
