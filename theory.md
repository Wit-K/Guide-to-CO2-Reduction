---
layout: default
title: "CO2RR Theory: The Fundamentals of CO2 Reduction"
description: "Learn the foundational theory of CO2RR, including the CO2 reduction reaction pathways, the volcano plot, and choosing the right metal catalyst."
---

<script>
  MathJax = {
    tex: {
      inlineMath: [['$', '$'],['\\(', '\\)']],
      displayMath: [['$$', '$$'], ['\\[', '\\]']],
      processEscapes: true
    }
  };
</script>
<script id="MathJax-script" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>

<style>
  .toc-box {
    background: #f8fafc;
    border: 1px solid #e2e8f0;
    border-left: 5px solid #3b82f6;
    border-radius: 8px;
    padding: 20px 25px;
    margin: 30px 0;
    box-shadow: 0 4px 6px rgba(0,0,0,0.05);
    font-family: system-ui, -apple-system, sans-serif;
  }
  .toc-box h4 {
    margin-top: 0;
    color: #1e3a8a;
    font-size: 1.2rem;
    margin-bottom: 15px;
  }
  .toc-box ul {
    list-style-type: none;
    padding-left: 0;
    margin: 0;
  }
  .toc-box li {
    margin-bottom: 8px;
  }
  .toc-box a {
    text-decoration: none;
    color: #3b82f6;
    font-weight: 600;
    transition: all 0.2s;
  }
  .toc-box a:hover {
    color: #1e40af;
    text-decoration: underline;
  }

/* Style the ## headings (Second Level) so they look nice */
  .toc-box ul ul {
    display: block; /* Make sure these are visible! */
    padding-left: 20px;
    font-size: 0.95em;
    margin-top: 5px;
    border-left: 2px solid #e2e8f0;
    margin-left: 5px;
  }
  .toc-box ul ul a {
    color: #475569;
    font-weight: normal;
  }
  .toc-box ul ul a:hover {
    color: #3b82f6;
  }

  /* Completely hide the ### headings (Third Level) and deeper */
  .toc-box ul ul ul {
    display: none;
  }
</style>

<!-- Paste this part exactly where you want the Table of Contents to appear! -->
<div class="toc-box" markdown="1">
<h4>Table of Contents</h4>

* TOC
{:toc}

</div>

# Foundations & Theory
*Part 1: The Electrochemical Basics*

---

## 1. The Big Picture
To understand this project, we must first know what electrochemical reduction is. In chemistry, "reduction" simply means gaining electrons.

Most people are familiar with combustion, where we burn a fuel with oxygen to release energy. This process produces carbon dioxide ($$CO_2$$) and water.

$$ Fuel + Oxygen \rightarrow CO_2 + H_2O + Energy $$

We can actually reverse that process and that is essentially what "$$CO_2$$ Reduction ($$CO_2$$R)" is. We use energy from different sources (like heat or light) to complete this process, but electrical energy is what we will be focusing on as it is the most efficient yet. Using energy to force electrons back into carbon dioxide, we can convert it from a waste product back into a useful fuel or chemical feedstock, naming it the process of "electrochemical CO2 reduction".

$$ CO_2 + H_2O + Energy (Electricity) \rightarrow Fuel + Oxygen $$

Because $$CO_2$$ is an extremely stable molecule, it does not want to react. It requires a significant amount of energy and a specific environment to break its bonds and form new ones. This is why we need an electrochemical cell.

<style>
  .tree-container {
    display: flex;
    flex-direction: row; /* Horizontal flow */
    align-items: center;
    justify-content: center;
    gap: 20px;
    margin: 40px 0;
    font-family: system-ui, -apple-system, sans-serif;
  }
  
  /* Replaced tree-row with tree-column to stack the products vertically in each phase */
  .tree-column {
    display: flex;
    flex-direction: column;
    gap: 20px;
    justify-content: center;
  }

  .tree-node {
    position: relative;
    padding: 15px 25px;
    background: #f8fafc;
    border: 2px solid #3b82f6;
    border-radius: 8px;
    font-weight: 600;
    color: #1e3a8a;
    cursor: default;
    text-align: center;
    transition: all 0.2s ease;
    box-shadow: 0 2px 4px rgba(0,0,0,0.05);
    min-width: 140px; /* Keeps nodes looking uniform */
  }

  .tree-node:hover {
    background: #3b82f6;
    color: white;
    transform: translateY(-2px);
    box-shadow: 0 4px 6px rgba(0,0,0,0.1);
  }

  .node-tooltip {
    visibility: hidden;
    width: 240px;
    background-color: #1f2937;
    color: #f3f4f6;
    text-align: left;
    border-radius: 8px;
    padding: 15px;
    position: absolute;
    z-index: 10;
    bottom: 130%;
    left: 50%;
    transform: translateX(-50%);
    opacity: 0;
    transition: opacity 0.3s, bottom 0.3s;
    font-size: 0.85rem;
    font-weight: normal;
    line-height: 1.5;
    box-shadow: 0 10px 15px -3px rgba(0,0,0,0.2);
  }

  .node-tooltip::after {
    content: "";
    position: absolute;
    top: 100%;
    left: 50%;
    margin-left: -8px;
    border-width: 8px;
    border-style: solid;
    border-color: #1f2937 transparent transparent transparent;
  }

  .tree-node:hover .node-tooltip {
    visibility: visible;
    opacity: 1;
    bottom: 140%;
  }

  .tooltip-title {
    font-weight: bold;
    font-size: 1rem;
    border-bottom: 1px solid #4b5563;
    padding-bottom: 6px;
    margin-bottom: 8px;
    display: block;
    color: #60a5fa;
  }

  .tree-arrow {
    font-size: 45px; /* Much larger arrow */
    color: #94a3b8;  /* Professional blue-gray tint */
    font-weight: bold;
    display: flex;
    align-items: center;
    transition: transform 0.3s ease;
  }

  /* Automatically adjust for mobile phones so it doesn't break off the screen */
  @media (max-width: 768px) {
    .tree-container {
      flex-direction: column;
    }
    .tree-arrow {
      transform: rotate(90deg); /* Turn horizontal arrows downward on mobile */
      margin: 10px 0;
    }
  }
</style>

<div class="tree-container">
  <!-- First Stage: Starting Material -->
  <div class="tree-column">
    <div class="tree-node">CO₂ (Carbon Dioxide)
      <div class="node-tooltip">
        <span class="tooltip-title">Carbon Dioxide (CO₂)</span>
        Our highly stable starting material. Requires significant energy and a catalyst to break its C=O double bonds.
      </div>
    </div>
  </div>
  
  <!-- Massive Right Arrow -->
  <div class="tree-arrow">➔</div>
  
  <!-- Second Stage: 2-Electron Products -->
  <div class="tree-column">
    <div class="tree-node">CO (Carbon Monoxide)
      <div class="node-tooltip">
        <span class="tooltip-title">Carbon Monoxide (CO)</span>
        <strong>Electrons:</strong> 2e⁻<br>
        <strong>Phase:</strong> Gas<br>
        <strong>Use:</strong> Essential precursor for "syngas" to manufacture synthetic industrial chemicals.
      </div>
    </div>
    <div class="tree-node">HCOO⁻ (Formate)
      <div class="node-tooltip">
        <span class="tooltip-title">Formate (HCOO⁻)</span>
        <strong>Electrons:</strong> 2e⁻<br>
        <strong>Phase:</strong> Liquid<br>
        <strong>Use:</strong> Utilized in direct liquid fuel cells, agriculture, and the chemical industry.
      </div>
    </div>
  </div>
  
  <!-- Massive Right Arrow -->
  <div class="tree-arrow">➔</div>
  
  <!-- Third Stage: >2 Electron Products -->
  <div class="tree-column">
    <div class="tree-node">CH₄ (Methane)
      <div class="node-tooltip">
        <span class="tooltip-title">Methane (CH₄)</span>
        <strong>Electrons:</strong> 8e⁻<br>
        <strong>Phase:</strong> Gas<br>
        <strong>Use:</strong> Direct, drop-in substitute for natural gas in heating and electricity generation.
      </div>
    </div>
    <div class="tree-node">C₂H₄ (Ethylene)
      <div class="node-tooltip">
        <span class="tooltip-title">Ethylene (C₂H₄)</span>
        <strong>Electrons:</strong> 12e⁻<br>
        <strong>Phase:</strong> Gas<br>
        <strong>Use:</strong> The world's most important precursor for creating plastics (polyethylene).
      </div>
    </div>
    <div class="tree-node">C₂H₅OH (Ethanol)
      <div class="node-tooltip">
        <span class="tooltip-title">Ethanol (C₂H₅OH)</span>
        <strong>Electrons:</strong> 12e⁻<br>
        <strong>Phase:</strong> Liquid<br>
        <strong>Use:</strong> High-density liquid fuel, fuel additive, and universal solvent.
      </div>
    </div>
  </div>
</div>
*Interactive Figure : The "Family Tree" of CO2 reduction products.*

---

## 2. Basic Electrochemistry
Experiments in this field take place inside an "electrolytic cell". An electrolytic cell uses an external power source to force non-spontaneous chemical reactions to happen. Think of it as charging a battery, but instead of storing the energy inside the battery itself, we are storing the energy in the liquid fuel we create. The 'Cathode' is where we shove electrons in to build these fuel molecules.

There are two sides of the reaction which can happen in electrochemstry:

### The Cathode (The Reduction Site)
The cathode is the "electrode" connected to the negative terminal of the power supply. This is where electrons enter the solution.
*   **What happens here:** Positive ions or neutral molecules (like $$CO_2$$) are attracted to the surface. They accept electrons and undergo reduction.
*   **Function:** This is the most important part of the setup. The material of the cathode determines what product you make. Researchers are working together to create better cathode which makes better product.
*   **Key Equation:** $$ CO_2 + 2H^+ + 2e^- \rightarrow CO + H_2O $$

### The Anode (The Oxidation Site)
The anode is the "electrode" connected to the positive terminal. This is where electrons leave the solution to return to the power supply.
*   **What happens here:** To balance the electrons used at the cathode, something must lose electrons (oxidize) at the anode. In most experiments, water is oxidized into oxygen gas.
*   **Function:** While we focus on what is happening on the cathode, the anode is necessary to complete the circuit.
*   **Key Equation:** $$ 2H_2O \rightarrow O_2 + 4H^+ + 4e^- $$

---

## 3. The Core Idea
If we are applying electricity, why doesn't the CO2 just break apart on its own?

### The Stability Problem
Carbon Dioxide is an incredibly stable molecule: it has a linear shape ($$O=C=O$$) with strong double bonds. It is already happy as is and resist changes coming in its way. So if you just stick a wire in water and apply voltage, don't expect long chain carbon compound to form; the electricity will ignore $$CO_2$$ and just split water, which is easy to break apart, instead.

### What the Catalyst Does
This is where the metal electrode comes into play. The reaction does not happen in the liquid; it happens on the surface of the metal.
1.  **Adsorption:** The $$CO_2$$ molecule lands on the metal surface.
2.  **Activation:** The metal atoms grab the Carbon and Oxygen, physically bending the molecule. This bending weakens the bonds, making it easier for electrons to attack.
3.  **Formation:** The electron attack the reactants, breaking them apart. The atoms then combine with each other, forming new molecules which is our product.
4.  **Desorption:** Once the fuel is made, the metal must let go so the product can float away and make room for more $$CO_2$$.

### The "Goldilocks" Zone
The metal must bind to the $$CO$$ (the intermediate) with just the right amount of force for it to create products efficeintly. Scientists are trying to find or design a material that is just right.
*   **Too Weak:** If the metal doesn't hold onto the $$CO$$ strongly enough, they will just fly away and the main product will be $$CO$$.
*   **Too Strong:** If the metal grabs too tight, the $$CO$$ gets stuck. The surface gets clogged by all the $$CO$$, preventing new $$CO_2$$ from entering. The reaction stops. This is the term define as "surface poisoning".
*   **Just Right:** The metal holds onto $$CO$$ long enough to transform it into hydrocarbon, but lets go of after the product form.

The goal of the research is to find a catalyst surface that has this perfect balance.

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<div style="width: 100%; max-width: 650px; margin: 30px auto;">
  <canvas id="volcanoPlot"></canvas>
</div>

<script>
document.addEventListener("DOMContentLoaded", function() {
  const ctx = document.getElementById('volcanoPlot').getContext('2d');
  
  const dataPoints =[
    {x: -0.2, y: 30, label: 'Au (Gold)', product: 'CO'},
    {x: -0.4, y: 50, label: 'Ag (Silver)', product: 'CO'},
    {x: -0.8, y: 95, label: 'Cu (Copper)', product: 'Hydrocarbons'},
    {x: -1.4, y: 20, label: 'Ni (Nickel)', product: 'H₂ (Poisoned)'},
    {x: -1.7, y: 10, label: 'Pt (Platinum)', product: 'H₂ (Poisoned)'}
  ];

  new Chart(ctx, {
    data: {
      datasets:[
        {
          type: 'scatter',
          label: 'Catalyst Metals',
          data: dataPoints,
          backgroundColor: function(context) {
            const lbl = context.raw?.label;
            if(lbl?.includes('Cu')) return '#4caf50'; // Green for Cu
            if(lbl?.includes('Au') || lbl?.includes('Ag')) return '#2196f3'; // Blue for CO
            return '#f44336'; // Red for H2
          },
          pointRadius: 8,
          pointHoverRadius: 11,
          order: 1
        },
        {
          type: 'line',
          label: 'Theoretical Volcano Curve',
          data:[
            {x: -0.1, y: 15}, {x: -0.4, y: 50}, {x: -0.8, y: 100}, {x: -1.4, y: 25}, {x: -1.9, y: 5}
          ],
          borderColor: 'rgba(0,0,0,0.3)',
          borderDash: [5, 5],
          fill: false,
          pointRadius: 0,
          tension: 0.4,
          order: 2
        }
      ]
    },
    options: {
      plugins: {
        tooltip: {
          callbacks: {
            label: function(context) {
              if (context.datasetIndex === 1) return null; // Hide tooltip for the curve
              const pt = context.raw;
              return `${pt.label} | Primary Product: ${pt.product} | Binding Energy: ${pt.x} eV`;
            }
          }
        },
        title: {
          display: true,
          text: 'Interactive Volcano Plot for CO₂ Reduction',
          font: { size: 16 }
        }
      },
      scales: {
        x: { title: { display: true, text: 'CO Binding Energy (eV) [Weak ➔ Strong]' } },
        y: { title: { display: true, text: 'Catalytic Activity' }, beginAtZero: true }
      }
    }
  });
});
</script>
<p align="center"><em>Hover over the data points to see the exact binding energy and the resulting primary product.</em></p>

<div style="border: 1px solid #ccc; padding: 20px; border-radius: 8px; text-align: center; margin: 30px 0; background-color: #f9f9f9; box-shadow: 0 4px 6px rgba(0,0,0,0.1);">
    <h4 style="margin-top: 0;">Interactive Binding Energy: The "Goldilocks" Principle</h4>
    <div style="height: 180px; position: relative; background: #e0f7fa; border-radius: 8px; overflow: hidden; margin-bottom: 20px;" id="animation-box">
        <!-- Metal Surface -->
        <div style="position: absolute; bottom: 0; width: 100%; height: 40px; background: #9e9e9e; display: flex; align-items: center; justify-content: center; color: white; font-weight: bold;">Metal Catalyst Surface</div>
        
        <!-- Molecules -->
        <div id="co-molecule-1" style="position: absolute; top: 10px; left: 45%; width: 40px; height: 40px; background: #ff5722; color: white; border-radius: 50%; line-height: 40px; font-size: 14px; font-weight: bold; transition: all 0.6s ease;">CO</div>
        <div id="co-molecule-2" style="position: absolute; top: 10px; left: 55%; width: 40px; height: 40px; background: #ff5722; color: white; border-radius: 50%; line-height: 40px; font-size: 14px; font-weight: bold; transition: all 0.6s ease; opacity: 0;">CO</div>
    </div>
    
    <input type="range" id="binding-slider" min="1" max="3" value="2" style="width: 80%; cursor: pointer;">
    <div style="display: flex; justify-content: space-between; width: 80%; margin: 5px auto 15px auto; font-weight: bold; font-size: 14px;">
        <span style="color: #2196f3;">Weak</span>
        <span style="color: #4caf50;">Just Right</span>
        <span style="color: #f44336;">Strong</span>
    </div>
    <div id="slider-description" style="font-size: 16px; min-height: 50px; background: white; padding: 10px; border-radius: 5px; border: 1px solid #ddd;"></div>
</div>

<script>
    const slider = document.getElementById('binding-slider');
    const mol1 = document.getElementById('co-molecule-1');
    const mol2 = document.getElementById('co-molecule-2');
    const desc = document.getElementById('slider-description');

    function updateAnimation() {
        const val = slider.value;
        if (val == 1) { 
            // Weak
            mol1.style.top = '20px'; mol1.style.left = '80%'; mol1.style.transform = 'rotate(45deg)';
            mol1.innerHTML = 'CO'; mol1.style.background = '#2196f3';
            mol2.style.opacity = '0';
            desc.innerHTML = "<strong>Too Weak:</strong> CO lands but immediately flies away. The main product is simply <strong>CO gas</strong>.";
        } else if (val == 2) { 
            // Just right
            mol1.style.top = '100px'; mol1.style.left = '42%'; mol1.style.transform = 'rotate(0deg)';
            mol1.innerHTML = 'C'; mol1.style.background = '#4caf50';
            mol2.style.top = '100px'; mol2.style.left = '52%'; mol2.style.opacity = '1';
            mol2.innerHTML = 'C'; mol2.style.background = '#4caf50';
            desc.innerHTML = "<strong>Just Right:</strong> CO sticks long enough to bond with another Carbon. The metal lets go once formed. Result: <strong>Ethylene (C₂H₄)</strong>.";
        } else if (val == 3) { 
            // Strong
            mol1.style.top = '105px'; mol1.style.left = '35%'; mol1.style.transform = 'rotate(0deg)';
            mol1.innerHTML = 'CO'; mol1.style.background = '#f44336';
            mol2.style.top = '105px'; mol2.style.left = '55%'; mol2.style.opacity = '1';
            mol2.innerHTML = 'CO'; mol2.style.background = '#f44336';
            desc.innerHTML = "<strong>Too Strong:</strong> CO gets permanently stuck. New CO₂ is blocked from entering. Result: <strong>Catalyst Poisoning / Hydrogen Evolution</strong>.";
        }
    }
    slider.addEventListener('input', updateAnimation);
    updateAnimation(); // trigger on load
</script>

---

## 4.1 Understanding Measurements and Variable
In an electrochemical experiment, there are two main parameters we can alter or measure: Potential and Current. It is vital to understand the difference between the driving force and the reaction rate.

### Potential (Voltage)
Potential is the energy or basically, the push applied to the system. Every chemical reaction has its own minimum energy requirement to proceed.
*   **Thermodynamic Potential:** This is the theoretical minimum voltage needed to start the reaction. For converting $$CO_2$$ to Carbon Monoxide, this is approximately -0.11 Volts.
*   **Applied Potential:** This is the real potential applied in the real experiment, which is significantly more than the theoretical value. This is because real-world electrochemical reactions are hardly perfectly efficient and requires additional energy to overcome the theroretical minimum.

### Current (Amperage)
While voltage is the push, the current is the flow. Current measures the rate at which electrons are moving across the interface. Since the chemical reaction consumes electrons, the current tells you directly how fast the reaction is happening.
*   **High Current:** A fast reaction rate.
*   **Low Current:** A slow reaction rate.

### Surface Area and Normalization
A large piece of copper will naturally allow more current to pass than a thin copper wire, just because there is more space for the reaction to occur. This makes comparision unfair. So, to make fair comparisons between different experiments, we wil look at "Current Density" instead. This is the ratio of current by surface area of the electrode, telling us how active the material is regardless of its size.

## 4.2 Thermodynamics and Kinetics
Why does the reaction does not start exactly at the theoretical voltage?

### The Energy Barrier
Even if you apply enough energy to make the reaction possible, the reaction might still be too slow to measure. This is because molecules need to rearrange themselves, bonds need to break, and intermediates need to form.

### Overpotential
To overcome this slowness, we apply extra voltage. This extra voltage is the "Overpotential".
*   If a catalyst is "good," it requires very little overpotential to reach a high current.
*   If a catalyst is "bad," you must apply a massive voltage to get even a small current.

In research, the goal is often to find a setup that produces the most product with the least amount of overpotential.

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<style>
  .energy-container {
    max-width: 800px;
    margin: 40px auto;
    background: #ffffff;
    border: 1px solid #e2e8f0;
    border-radius: 12px;
    box-shadow: 0 10px 15px -3px rgba(0,0,0,0.1);
    overflow: hidden;
    font-family: system-ui, -apple-system, sans-serif;
  }
  .energy-header {
    background: #1e293b;
    color: white;
    padding: 15px 20px;
    text-align: center;
  }
  .energy-header h3 { margin: 0; font-size: 1.25rem; color: #f8fafc; }
  .chart-wrapper {
    padding: 20px;
    height: 350px;
    position: relative;
  }
  .stepper-panel {
    background: #f8fafc;
    border-top: 2px solid #e2e8f0;
    padding: 20px;
    display: flex;
    flex-direction: column;
    gap: 15px;
  }
  .stepper-controls {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .step-btn {
    background: #3b82f6;
    color: white;
    border: none;
    padding: 10px 20px;
    border-radius: 6px;
    font-weight: bold;
    cursor: pointer;
    transition: background 0.2s;
  }
  .step-btn:hover { background: #2563eb; }
  .step-btn:disabled { background: #cbd5e1; cursor: not-allowed; }
  .step-indicator {
    font-weight: bold;
    color: #475569;
  }
  .explanation-box {
    background: white;
    border-left: 4px solid #3b82f6;
    padding: 15px;
    border-radius: 0 6px 6px 0;
    font-size: 0.95rem;
    line-height: 1.5;
    color: #334155;
    min-height: 80px;
  }
  .highlight-gold { color: #d97706; font-weight: bold; }
  .highlight-copper { color: #dc2626; font-weight: bold; }
</style>

<div class="energy-container">
  <div class="energy-header">
    <h3>Interactive Energy Landscape: Why Copper Works and Gold Gets Stuck</h3>
  </div>
  
  <div class="chart-wrapper">
    <canvas id="energyChart"></canvas>
  </div>
  
  <div class="stepper-panel">
    <div class="explanation-box" id="step-explanation">
      <strong>Start:</strong> We begin with CO₂ gas. We set this energy level to 0.0 eV as our baseline starting line. Click "Next Step" to apply voltage and start the reaction!
    </div>
    
    <div class="stepper-controls">
      <button class="step-btn" id="btn-prev" onclick="changeStep(-1)" disabled>Previous Step</button>
      <div class="step-indicator" id="step-counter">Step 0 of 4</div>
      <button class="step-btn" id="btn-next" onclick="changeStep(1)">Next Step</button>
    </div>
  </div>
</div>

<script>
document.addEventListener("DOMContentLoaded", function() {
  const ctx = document.getElementById('energyChart').getContext('2d');
  
  // Full DFT Data from your image
  const labels =['CO₂', '*COOH', '*CO', '*CHO', 'CH₄'];
  const dataGold =[0, 1.2, -0.1, 2.5, 2.0];
  const dataCopper =[0, 0.5, -0.2, 0.3, -0.8];
  
  let currentStep = 0;
  
  // Explanations for each step
  const explanations =[
    "<strong>Start (CO₂):</strong> We begin with CO₂ gas. We set this energy level to 0.0 eV as our baseline starting line.",
    "<strong>Step 1 (*COOH):</strong> The first electron and proton are added. <span class='highlight-copper'>Copper</span> forms this intermediate easily (+0.5 eV). <span class='highlight-gold'>Gold</span> requires a much higher energy (+1.2 eV). Higher energy means more <em>Overpotential</em> is needed.",
    "<strong>Step 2 (*CO):</strong> Water leaves, leaving Carbon Monoxide (*CO) attached to the metal. Both metals drop in energy here. For <span class='highlight-gold'>Gold</span>, it is highly likely the CO just detaches floats away as a final gas product.",
    "<strong>Step 3 (*CHO):</strong> To continue toward Methane, we must add another hydrogen. <span class='highlight-copper'>Copper</span> needs a tiny bump to +0.3 eV. <span class='highlight-gold'>Gold</span> faces a large energy barrier up to +2.5 eV. To force Gold over this, you would need an absurdly high Overpotential that water will likely be split into H₂ gas instead. This is why Gold gets stuck.",
    "<strong>Step 4 (CH₄):</strong> Once <span class='highlight-copper'>Copper</span> gets past the *CHO barrier, the reaction easily adds the remaining protons and electrons until Methane (CH₄) is formed and releases from the surface."
  ];

  // Initialize Chart
  const energyChart = new Chart(ctx, {
    type: 'line',
    data: {
      labels: labels,
      datasets:[
        {
          label: 'Gold (Stuck at CO)',
          data:[0, null, null, null, null], // Starts at step 0
          borderColor: '#f59e0b',
          backgroundColor: '#f59e0b',
          borderWidth: 4,
          pointRadius: 6,
          pointHoverRadius: 8,
          tension: 0.1 // Slight curve for aesthetics
        },
        {
          label: 'Copper (Makes Methane)',
          data: [0, null, null, null, null], // Starts at step 0
          borderColor: '#ef4444',
          backgroundColor: '#ef4444',
          borderWidth: 4,
          pointRadius: 6,
          pointHoverRadius: 8,
          tension: 0.1
        },
        {
          label: 'Baseline (0 eV)',
          data: [0, 0, 0, 0, 0],
          borderColor: '#94a3b8',
          borderWidth: 2,
          borderDash: [5, 5],
          pointRadius: 0,
          fill: false
        }
      ]
    },
    options: {
      responsive: true,
      maintainAspectRatio: false,
      plugins: {
        tooltip: {
          callbacks: { label: (ctx) => `${ctx.dataset.label}: ${ctx.raw} eV` }
        }
      },
      scales: {
        y: {
          title: { display: true, text: 'Free Energy (ΔG) in eV', font: { weight: 'bold' } },
          min: -1.0,
          max: 3.0
        },
        x: {
          title: { display: true, text: 'Reaction Intermediates', font: { weight: 'bold' } }
        }
      }
    }
  });

  // Expose function to global scope for buttons
  window.changeStep = function(direction) {
    currentStep += direction;
    
    // Bounds checking
    if(currentStep < 0) currentStep = 0;
    if(currentStep > 4) currentStep = 4;
    
    // Update Button States
    document.getElementById('btn-prev').disabled = (currentStep === 0);
    document.getElementById('btn-next').disabled = (currentStep === 4);
    
    // Update Text
    document.getElementById('step-counter').innerText = `Step ${currentStep} of 4`;
    
    // Animate text change
    const textBox = document.getElementById('step-explanation');
    textBox.style.opacity = 0;
    setTimeout(() => {
      textBox.innerHTML = explanations[currentStep];
      textBox.style.opacity = 1;
    }, 200);

    // Update Chart Data (Slices array up to current step)
    const newGoldData = dataGold.map((val, idx) => idx <= currentStep ? val : null);
    const newCopperData = dataCopper.map((val, idx) => idx <= currentStep ? val : null);
    
    energyChart.data.datasets[0].data = newGoldData;
    energyChart.data.datasets[1].data = newCopperData;
    energyChart.update();
  };
});
</script>

---

## 5. Selectivity and the Competing Reaction
The most difficult part of $$CO_2$$ reduction is not breaking the $$CO_2$$; it is avoiding the water.

### The Hydrogen Problem
Since our electrolyte is mostly water, there are billions of water molecules surrounding the electrode for every one CO2 molecule. Water can also accept electrons to form Hydrogen gas ($$H_2$$).

$$ 2H^+ + 2e^- \rightarrow H_2 $$

This is called the "Hydrogen Evolution Reaction (HER)". It is an annoying competing reaction that wastes electricity and hinders reactions that we actually want.
And, where does the hydrogen comes from then? You might wonder: if we only pump in CO2 gas, where does the Hydrogen come from? It comes from the water itself.

$$ H_2O ⇌ H^+ + OH^- $$

### Selectivity (Faradaic Efficiency)
We measure the efficiency using "Faradaic Efficiency (FE)". It represents the percentage of electrons that went into making the product you want against all the products produced (including Hydrogen).
**Example:**
*   **100% FE:** Every electron resulted in $$CO_2$$ reduction.
*   **50% FE:** Half of the electron resulted in $$CO_2$$ reduction.
*   **0% FE:** All electrons were wasted making Hydrogen gas.

---

## 6. Catalyst materials
When we say we are making fuel, don't expect liquid gasoline to drip off the catalyst. For example, group 1 & 2 metals make gas (CO/Hydrogen) that float away and Copper makes liquid alcohols that dissolve invisibly into the water. So, because they don't act the same, they are often be categorized into groups based on what they produce:

### Group 1: Hydrogen Producers
**Metals:** Platinum (Pt), Nickel (Ni), Iron (Fe), Titanium (Ti) and more.
Do not use these metals if you are aiming for $$CO_2$$ reduction.
*   **Behavior:** These metals bind to Hydrogen atoms very strongly.
*   **Typical Products:** Mostly Hydrogen gas. The CO2 will barely touch the surface.

### Group 2: Two-Electron Pathway (CO / Formate)
**Metals:** Silver ($$Ag$$), Gold ($$Au$$), Zinc ($$Zn$$), Tin ($$Sn$$) and more.
They are great for beginners; however, different metals are specialized in making different product, so research first on what products you are looking for. For example, Zinc makes Formate and Silver makes $$CO$$ efficiently.
*   **Behavior:** These metals are poor at making hydrogen, allowing CO2 to react. However, they stop the reaction early and separate from the reaction site.
*   **Typical Products:** Carbon Monoxide ($$CO$$) or Formate ($$HCOO-$$).

### Group 3: Hydrocarbon Pathway
**Metal:** Copper ($$Cu$$)
It is unique in the periodic table and the only metal known to make multi-carbon products (very valuable). However, it is complex as it produces a mix of different products' state at once and can be somewhat unpredictable. Scientist are trying to tune the metal and understand mechanism of how each product forms in different environment.
*   **Behavior:** Copper has just the right binding energy with the Carbon atom. This allows the carbon atoms to bond with other Carbon atoms without dettaching from the surface of the metal first.
*   **Typical Products:** Methane ($$CH_4$$), Ethylene ($$C_2H_4$$), and Ethanol ($$C_2H_5OH$$).

<style>
  .ptable-container { text-align: center; margin: 30px 0; font-family: Arial, sans-serif; background: #f8f9fa; padding: 20px; border-radius: 8px; border: 1px solid #e9ecef;}
  .ptable-buttons button { padding: 10px 15px; margin: 5px; border: none; border-radius: 5px; cursor: pointer; font-weight: bold; color: white; transition: 0.2s;}
  .ptable-buttons button:hover { opacity: 0.8; }
  .btn-h2 { background-color: #f44336; }
  .btn-co { background-color: #2196f3; }
  .btn-hc { background-color: #4caf50; }
  .btn-reset { background-color: #6c757d; }
  
  .ptable-grid {
    display: grid;
    grid-template-columns: repeat(12, 1fr);
    gap: 5px;
    max-width: 600px;
    margin: 20px auto 0 auto;
  }
  .ptable-element {
    aspect-ratio: 1;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: #e0e0e0;
    border: 1px solid #ccc;
    border-radius: 4px;
    font-weight: bold;
    font-size: 14px;
    transition: all 0.3s ease;
    cursor: help;
  }
  /* Element Categories */
  .cat-h2 { background-color: #ffcdd2; border: 2px solid #f44336; }
  .cat-co { background-color: #bbdefb; border: 2px solid #2196f3; }
  .cat-hc { background-color: #c8e6c9; border: 2px solid #4caf50; }
  
  /* Dimmed state for non-highlighted */
  .dimmed { opacity: 0.15; filter: grayscale(100%); }
</style>

<div class="ptable-container">
  <h4 style="margin-top: 0;">Interactive Periodic Table of CO₂ Reduction</h4>
  <p style="font-size: 14px; margin-bottom: 15px;">Click a group below to highlight the respective metals.</p>
  
  <div class="ptable-buttons">
    <button class="btn-h2" onclick="highlightGroup('h2')">Group 1 (H₂ Producers)</button>
    <button class="btn-co" onclick="highlightGroup('co')">Group 2 (CO / Formate)</button>
    <button class="btn-hc" onclick="highlightGroup('hc')">Group 3 (Hydrocarbons)</button>
    <button class="btn-reset" onclick="highlightGroup('all')">Show All</button>
  </div>
  
  <!-- Simplified d-block & p-block Grid -->
  <div class="ptable-grid" id="ptable">
    <!-- Row 1 -->
    <div class="ptable-element cat-h2" title="Titanium (Hydrogen)">Ti</div>
    <div class="ptable-element">V</div><div class="ptable-element">Cr</div><div class="ptable-element">Mn</div>
    <div class="ptable-element cat-h2" title="Iron (Hydrogen)">Fe</div>
    <div class="ptable-element cat-h2" title="Cobalt (Hydrogen)">Co</div>
    <div class="ptable-element cat-h2" title="Nickel (Hydrogen)">Ni</div>
    <div class="ptable-element cat-hc" title="Copper (Hydrocarbons!)">Cu</div>
    <div class="ptable-element cat-co" title="Zinc (CO/Formate)">Zn</div>
    <div class="ptable-element cat-co" title="Gallium (CO/Formate)">Ga</div>
    <div class="ptable-element">Ge</div><div class="ptable-element">As</div>
    <!-- Row 2 -->
    <div class="ptable-element">Zr</div><div class="ptable-element">Nb</div><div class="ptable-element">Mo</div><div class="ptable-element">Tc</div>
    <div class="ptable-element cat-h2" title="Ruthenium (Hydrogen)">Ru</div>
    <div class="ptable-element cat-h2" title="Rhodium (Hydrogen)">Rh</div>
    <div class="ptable-element cat-h2" title="Palladium (Hydrogen)">Pd</div>
    <div class="ptable-element cat-co" title="Silver (CO)">Ag</div>
    <div class="ptable-element cat-co" title="Cadmium (CO/Formate)">Cd</div>
    <div class="ptable-element cat-co" title="Indium (Formate)">In</div>
    <div class="ptable-element cat-co" title="Tin (Formate)">Sn</div>
    <div class="ptable-element">Sb</div>
    <!-- Row 3 -->
    <div class="ptable-element">Hf</div><div class="ptable-element">Ta</div><div class="ptable-element">W</div><div class="ptable-element">Re</div>
    <div class="ptable-element cat-h2" title="Osmium (Hydrogen)">Os</div>
    <div class="ptable-element cat-h2" title="Iridium (Hydrogen)">Ir</div>
    <div class="ptable-element cat-h2" title="Platinum (Hydrogen)">Pt</div>
    <div class="ptable-element cat-co" title="Gold (CO)">Au</div>
    <div class="ptable-element cat-co" title="Mercury (CO/Formate)">Hg</div>
    <div class="ptable-element cat-co" title="Thallium (CO/Formate)">Tl</div>
    <div class="ptable-element cat-co" title="Lead (Formate)">Pb</div>
    <div class="ptable-element cat-co" title="Bismuth (Formate)">Bi</div>
  </div>
</div>

<script>
  function highlightGroup(group) {
    const elements = document.querySelectorAll('.ptable-element');
    elements.forEach(el => {
      el.classList.remove('dimmed'); 
      if (group === 'all') return;
      if (!el.classList.contains('cat-' + group)) {
        el.classList.add('dimmed');
      }
    });
  }
</script>

---

## 7. The Physical Limit
We must understand the environment and its limit in real-world. $$CO_2$$ is a gas, but the reaction happens on the solid metal surface inside a liquid. For the reaction to work, $$CO_2$$ gas must dissolve into the water to reach the electrode.
Some of the limits are:
1.  **Solubility:** $CO_2$ does not dissolve well in water: just around 33mM concentration at room temperature.
2.  **Mass Transport:** As you run the reaction, you use up the CO2 near the metal surface. If new $CO_2$ cannot diffuse in fast enough, the reaction stops and Hydrogen evolution takes over instead.

This is why you will see instructions to bubble $CO_2$ gas continuously into the solution. It keeps the water saturated with $CO_2$, giving enough room for valuable reactions to happen. 

<style>
  .page-nav { display: flex; justify-content: space-between; align-items: center; margin-top: 50px; padding-top: 20px; border-top: 2px solid #e2e8f0; font-family: system-ui, -apple-system, sans-serif; }
  .nav-btn { display: inline-block; padding: 10px 20px; background: #ffffff; color: #3b82f6; text-decoration: none; border: 1px solid #cbd5e1; border-radius: 6px; font-weight: 600; transition: all 0.2s; }
  .nav-btn:hover { background: #3b82f6; color: #ffffff; border-color: #3b82f6; text-decoration: none; }
  .nav-home { color: #64748b; font-weight: bold; text-decoration: none; transition: color 0.2s; }
  .nav-home:hover { color: #0f172a; text-decoration: underline; }
</style>

<div class="page-nav">
  <a href="./" class="nav-btn">← Home</a>
  <a href="./" class="nav-home">Back to Directory</a>
  <a href="./experiment" class="nav-btn">Next: Experimental Setup →</a>
</div>
