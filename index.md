<script type="text/javascript" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
  
# Electrochemical CO2 Reduction
**A practical, beginner-friendly guide for starting research**

---

## The Motivation
Electrochemical CO₂ reduction is widely discussed in research papers, but difficult to approach as a beginner. Most available resources either focus on abstract theory or assume prior experience and complete equipments. As a result, newcomers often struggle to picture and understand how experiments are designed, how data are interpreted and what it actually means.

This guide aims to bridge that gap. Its goal is to organize concepts, design logic, and data interpretation in a way that is easy to comprehend as beginners, while keeping standard of how the field is in real research.

## Who is this for?
*   **Student Researchers:** Students looking to conduct independent research projects or transitioning from theory to experiment.
*   **Beginners:** Anyone with a basic chemistry background attempting their first electrolysis experiments.
*   **Readers:** Readers who want clear concept map before diving into literature.

---
<!-- CO2RR CSS Animation -->
<style>
  .reactor-container {
    width: 100%; max-width: 600px; height: 160px; margin: 30px auto;
    background: #f8f9fa; border: 2px solid #e1e4e8; border-radius: 12px;
    position: relative; overflow: hidden; display: flex; align-items: center;
    box-shadow: inset 0 0 10px rgba(0,0,0,0.05); font-family: sans-serif;
  }
  .electrode {
    width: 12px; height: 120px; background: #4a5568; position: absolute;
    left: 50%; transform: translateX(-50%); border-radius: 6px;
    box-shadow: 0 0 15px rgba(74, 85, 104, 0.4);
  }
  .molecule {
    padding: 10px 15px; border-radius: 20px; position: absolute;
    font-weight: bold; font-size: 14px; box-shadow: 0 4px 6px rgba(0,0,0,0.1);
  }
  .co2 {
    background: #fed7d7; color: #c53030;
    animation: flowIn 4s infinite ease-in;
  }
  .electron {
    width: 12px; height: 12px; background: #ecc94b; border-radius: 50%;
    position: absolute; left: 50%; transform: translateX(-50%);
    box-shadow: 0 0 10px #ecc94b; animation: zap 4s infinite ease-in;
  }
  .product {
    background: #c6f6d5; color: #276749;
    animation: flowOut 4s infinite ease-out;
  }

  /* Animation Timelines */
  @keyframes flowIn {
    0% { left: 5%; opacity: 0; }
    10% { opacity: 1; }
    45% { left: calc(50% - 60px); opacity: 1; }
    50% { left: calc(50% - 60px); opacity: 0; }
    100% { opacity: 0; }
  }
  @keyframes zap {
    0%, 40% { top: -20px; opacity: 0; }
    45% { top: 70px; opacity: 1; }
    50%, 100% { top: 70px; opacity: 0; }
  }
  @keyframes flowOut {
    0%, 50% { left: calc(50% + 20px); opacity: 0; }
    55% { opacity: 1; left: calc(50% + 20px); }
    90% { opacity: 1; }
    100% { left: 80%; opacity: 0; }
  }
</style>

<div class="reactor-container">
  <div class="molecule co2">CO₂ + H₂O</div>
  <div class="electron"></div>
  <div class="electrode"></div>
  <div class="molecule product">CO / CH₄ / C₂H₄</div>
</div>
<!-- End Animation -->

## Main Index Sections

<style>.card-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:20px;margin:40px 0}.nav-card{background:white;border:1px solid #e1e4e8;border-radius:10px;padding:25px;text-decoration:none;color:inherit;transition:all 0.3s ease;display:flex;flex-direction:column;box-shadow:0 2px 5px rgba(0,0,0,0.05);cursor:pointer}.nav-card:hover{transform:translateY(-5px);border-color:#0366d6;box-shadow:0 8px 15px rgba(3,102,214,0.15);text-decoration:none}.card-icon{font-size:2.5em;margin-bottom:15px}.card-title{font-size:1.25em;font-weight:bold;margin-bottom:10px;color:#24292e}.nav-card:hover .card-title{color:#0366d6}.card-desc{font-size:0.95em;color:#586069;line-height:1.4}</style>
<div class="card-grid">
<a href="./theory" class="nav-card"><div class="card-icon">⚛️</div><div class="card-title">1. Theory</div><div class="card-desc">Master the basics of electrochemistry, binding energies, and the Volcano Plot.</div></a>
<a href="./experiment" class="nav-card"><div class="card-icon">🧪</div><div class="card-title">2. Experiment</div><div class="card-desc">Learn how to set up an H-cell, polish electrodes, and run the reaction safely.</div></a>
<a href="./analysis" class="nav-card"><div class="card-icon">📊</div><div class="card-title">3. Analysis</div><div class="card-desc">Interpret CV/LSV graphs and calculate Faradaic Efficiency step-by-step.</div></a>
<a href="./troubleshooting" class="nav-card"><div class="card-icon">🔧</div><div class="card-title">4. Troubleshooting</div><div class="card-desc">Diagnose 0mA current, membrane leaks, and erratic graphs like a pro.</div></a>
<a href="./resources" class="nav-card"><div class="card-icon">📚</div><div class="card-title">5. Resources</div><div class="card-desc">A curated library of essential papers, methodology standards, and reviews.</div></a>
</div>

---
*Created by [Wit Kulvutiroj]*
