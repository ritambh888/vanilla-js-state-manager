# vanilla-js-state-manager
# Lightweight State Management System (Vanilla JS)

[![JavaScript](https://img.shields.io/badge/JavaScript-ES6%2B-yellow)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![Status](https://img.shields.io/badge/Status-Production%20Ready-green)]()

**Live Demo:** [View Application](https://ritambh888.github.io/vanilla-js-state-manager/)

## 📋 Overview
This project is a Proof of Concept (PoC) for a **dependency-free Single Page Application (SPA)** architecture. 

While modern frameworks like React or Vue are powerful, they often introduce unnecessary bloat for simple dashboards. This project demonstrates how to implement **centralized state management**, **authentication flows**, and **reactive DOM updates** using pure Vanilla JavaScript (ES6+).

## 🚀 Technical Highlights
* **Zero Dependencies:** No Node_modules, no Webpack, no build step. Extremely fast load times.
* **Custom State Machine:** Implements a localized `AppState` object to manage data flow and UI rendering.
* **SPA Architecture:** Handles view switching (Login vs. Dashboard) without browser refreshes.
* **Semantic HTML & CSS Variables:** Clean, maintainable styling structure.

## ⚙️ How It Works
The core logic relies on a centralized State Object that acts as the "Single Source of Truth." When the state changes (e.g., `isAuthenticated` becomes `true`), the `updateUI()` method automatically triggers the necessary DOM manipulations.

### The Core Logic (Snippet)
```javascript
const AppState = {
    isAuthenticated: false,
    
    // The "Reactor" that handles UI updates based on state
    updateUI: function() {
        if (this.isAuthenticated) {
            loginView.classList.add('hidden');
            dashboardView.classList.remove('hidden');
        } else {
            // Reset to safe state
            dashboardView.classList.add('hidden');
            loginView.classList.remove('hidden');
        }
    },

    // Actions
    login: function() {
        this.isAuthenticated = true;
        this.updateUI();
    }
};
