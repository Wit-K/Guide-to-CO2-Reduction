---
layout: default
title: "CO2RR Experimental Setup: H-Cells & Electrodes"
description: "A step-by-step beginner guide to setting up a CO2 reduction experiment. Learn how to wire a potentiostat and build an H-cell."
---

<script>
  MathJax = {
    tex: {
      inlineMath: [['$', '$'], ['\\(', '\\)']],
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

# Experimental Design & Set Up
Part2: Analysis and Break Down of each Critical Component in Common Design.

---

## Safety & Operational Hazards
*Common protocols for handling gases and electricity.*

*   **Carbon Monoxide (CO) Toxicity:**
    *   *Risk:* The primary product of this reaction is CO, an odorless, colorless, and deadly gas.
    *   *Protocol:* Experiments should be conducted in a fume hood or a well-ventilated space equipped with CO detector.
*   **High-Pressure Cylinders:**
    *   *Risk:* $CO_2$ tanks contain massive pressure. If it leaked or valve tear, it becomes a big projectile
    *   *Protocol:* Cylinders should be chained/strapped to a wall or stable bench at all times. Not moving a tank without the safety cap screwed on.
*   **Alkaline Electrolytes:**
    *   *Risk:* Potassium Hydroxide ($KOH$) and Bicarbonate solutions can cause eye damage and skin irritation.
    *   *Protocol:* Chemical goggles and nitrile gloves to prevent any accidents.
*   **Electrical Safety in Wet Environments:**
    *   *Risk:* Saltwater is highly conductive. Spills near the power supply can cause short circuits.
    *   *Protocol:* Power supplies should be kept above the bench surface and ensure that all alligator clips are dry before turning on the voltage.
 
Note that these are just some common safety and protocal when working with CO2 reduction. There are other several guidlines which should always be looked up and followed for each chemical and instruments.

---

## 1. The Big Picture
For 90% of high school and undergraduate research, the standard design is the "H-Type Electrolytic Cell".

H-Type Electrolytic Cell or commonly called "H-cell" gets its name from its iconic look, two container and a bridge, thus calling it H-Cell.
Imagine two separate building connected by a bridge.
*   **Cathodic Chamber:** This is where the $$CO_2$$ reduction happens. It contains the Working Electrode and the $$CO_2$$ gas.
*   **Anodic Chamber:** This contains the Counter Electrode. Its job is just to complete the electrical circuit.
*   **The Membrane/Bridge:** This allows ions to flow between the chambers but stops the liquids and gases from mixing.

**Why separate them?**
If you put everything in one beaker, the oxygen produced in Anodic Chamber would float over to Chamber 1 and ruin your sensitive CO2 reaction. The "H" shape physically isolates these compounds while allowing electricity to flow and reactions to happen.

*(Note: There are also other types of Cells including Flow Cells and Single Cell. But, because Flow Cells are too advance and require expensive pumps and Single Cell will get all the liquid mixed up, we will left them out and focus on H-Cell. If you are interested, you can research further by looking into scientific papers regarding the Flow Cell pros, cons, and set up)*

---

## 2. The Hardware Setup
To perform CO2 reduction, you need a specific set of components arranged in a standard 3-Electrode System. This setup ensures we can control the voltage precisely while keeping the fuel products separate from the waste oxygen.

<style>
  .hcell-container {
    display: flex; flex-wrap: wrap; gap: 20px; margin: 30px 0;
    background: #f8f9fa; padding: 20px; border-radius: 8px; border: 1px solid #e9ecef;
    align-items: center; /* Keeps everything vertically centered */
  }
  .hcell-svg { flex: 1.8; min-width: 350px; } /* Makes the SVG take up more room */
  .hcell-info {
    flex: 1; min-width: 220px; background: white; padding: 15px 20px;
    border-radius: 8px; border: 1px solid #ccc; box-shadow: 0 4px 6px rgba(0,0,0,0.05);
    transition: opacity 0.2s ease;
  }
  .hotspot { cursor: pointer; transition: 0.2s; }
  .hotspot:hover { opacity: 0.6; filter: drop-shadow(0 0 5px rgba(0,0,0,0.4)); }
</style>

<div class="hcell-container">
  <div class="hcell-svg">
    <!-- Viewbox adjusted to give more breathing room on all sides -->
    <svg viewBox="0 -10 420 330" width="100%" height="100%">
      
      <!-- Liquid -->
      <path d="M 30 160 L 30 260 A 20 20 0 0 0 50 280 L 150 280 A 20 20 0 0 0 170 260 L 170 210 L 250 210 L 250 260 A 20 20 0 0 0 270 280 L 370 280 A 20 20 0 0 0 390 260 L 390 160 Z" fill="#e3f2fd" stroke="#2196f3" stroke-width="2"/>
      
      <!-- Glassware (H-Cell) -->
      <path d="M 30 90 L 30 260 A 20 20 0 0 0 50 280 L 150 280 A 20 20 0 0 0 170 260 L 170 210 L 250 210 L 250 260 A 20 20 0 0 0 270 280 L 370 280 A 20 20 0 0 0 390 260 L 390 90 M 170 160 L 170 90 M 250 160 L 250 90" fill="none" stroke="#9e9e9e" stroke-width="4" stroke-linecap="round"/>
      
      <!-- Bridge / Membrane -->
      <line class="hotspot" x1="210" y1="160" x2="210" y2="210" stroke="#ff9800" stroke-width="8" onclick="showInfo('membrane')"/>
      <text x="210" y="235" font-size="12" fill="#ff9800" font-weight="bold" text-anchor="middle" pointer-events="none">Membrane</text>

      <!-- Working Electrode (WE) -->
      <rect class="hotspot" x="55" y="70" width="15" height="150" fill="#795548" stroke="#5d4037" stroke-width="2" onclick="showInfo('we')"/>
      <text x="62.5" y="40" font-size="12" fill="#795548" font-weight="bold" text-anchor="middle">
        <tspan x="62.5" dy="0">WE</tspan>
        <tspan x="62.5" dy="14">(Cathode)</tspan>
      </text>

      <!-- Reference Electrode (RE) -->
      <rect class="hotspot" x="140" y="70" width="10" height="120" fill="#e0e0e0" stroke="#9e9e9e" stroke-width="2" onclick="showInfo('re')"/>
      <text x="145" y="40" font-size="12" fill="#616161" font-weight="bold" text-anchor="middle">
        <tspan x="145" dy="0">RE</tspan>
        <tspan x="145" dy="14">(Ag/AgCl)</tspan>
      </text>

      <!-- Bubbler -->
      <path class="hotspot" d="M 95 70 L 95 250 L 115 250 L 115 230 L 105 230 L 105 70 Z" fill="#b3e5fc" stroke="#0288d1" stroke-width="2" onclick="showInfo('bubbler')"/>
      <circle cx="102" cy="260" r="3" fill="#0288d1"/><circle cx="95" cy="270" r="4" fill="#0288d1"/><circle cx="110" cy="265" r="2.5" fill="#0288d1"/>
      <text x="105" y="20" font-size="12" fill="#0288d1" font-weight="bold" text-anchor="middle">
        <tspan x="105" dy="0">CO₂</tspan>
        <tspan x="105" dy="14">Gas</tspan>
      </text>

      <!-- Counter Electrode (CE) -->
      <rect class="hotspot" x="315" y="70" width="10" height="150" fill="#9e9e9e" stroke="#616161" stroke-width="2" onclick="showInfo('ce')"/>
      <line class="hotspot" x1="305" y1="190" x2="335" y2="190" stroke="#616161" stroke-width="2" onclick="showInfo('ce')"/>
      <line class="hotspot" x1="305" y1="200" x2="335" y2="200" stroke="#616161" stroke-width="2" onclick="showInfo('ce')"/>
      <line class="hotspot" x1="305" y1="210" x2="335" y2="210" stroke="#616161" stroke-width="2" onclick="showInfo('ce')"/>
      <text x="320" y="40" font-size="12" fill="#424242" font-weight="bold" text-anchor="middle">
        <tspan x="320" dy="0">CE</tspan>
        <tspan x="320" dy="14">(Anode - Pt)</tspan>
      </text>
      
      <!-- Instructions -->
      <text x="210" y="310" font-size="14" fill="#d32f2f" font-style="italic" text-anchor="middle" font-weight="bold">👆 Click the components above!</text>
    </svg>
  </div>
  
  <div class="hcell-info" id="hcell-info-panel">
    <h3 style="margin-top:0; font-size: 1.1rem; color: #1976d2;">Interactive H-Cell</h3>
    <p style="font-size: 13px; line-height: 1.5; color: #444;">Welcome to the standard H-Type Electrolytic Cell. This is the workhorse of CO₂ reduction research.</p>
    <p style="font-size: 13px; line-height: 1.5; color: #444;"><strong>👈 Click on any part of the diagram</strong> (electrodes, membrane, bubbler) to learn its role.</p>
  </div>
</div>

<script>
  const infoPanel = document.getElementById('hcell-info-panel');
  const hcellData = {
    we: { title: "Working Electrode (WE)", text: "<strong>Role:</strong> The Cathode. This is where the magic happens! CO₂ is reduced here. Connected to the negative terminal.<br><br><strong>Materials:</strong> Usually a catalyst like Copper (Cu), Gold (Au), or Silver (Ag)." },
    ce: { title: "Counter Electrode (CE)", text: "<strong>Role:</strong> The Anode. It completes the electrical circuit. Water is oxidized to Oxygen gas (O₂) here.<br><br><strong>Materials:</strong> Needs to be highly stable so it doesn't dissolve. Platinum (Pt) mesh or wire is the standard." },
    re: { title: "Reference Electrode (RE)", text: "<strong>Role:</strong> Voltage Sensor. It measures the potential applied to the Working Electrode without passing current itself.<br><br><strong>Materials:</strong> Silver/Silver Chloride (Ag/AgCl) is standard for water-based electrolytes." },
    membrane: { title: "Ion Exchange Membrane", text: "<strong>Role:</strong> Traffic Controller. Allows positive ions (like H⁺ or K⁺) to cross the bridge but blocks gases.<br><br><strong>Why?</strong> If oxygen from the anode crossed over, it would ruin the reaction. Nafion 117 is standard." },
    bubbler: { title: "CO₂ Gas Bubbler", text: "<strong>Role:</strong> Reactant Supply. Delivers a constant flow of CO₂ gas into the liquid.<br><br><strong>Pro-Tip:</strong> You must bubble the gas for 20-30 minutes <em>before</em> turning on electricity to purge out ambient oxygen." }
  };

  function showInfo(part) {
    infoPanel.style.opacity = 0;
    setTimeout(() => {
      infoPanel.innerHTML = `<h3 style="margin-top:0; font-size: 1.15rem; color: #1976d2; margin-bottom: 10px;">${hcellData[part].title}</h3><p style="font-size: 13px; line-height: 1.5; color: #444;">${hcellData[part].text}</p>`;
      infoPanel.style.opacity = 1;
    }, 150);
  }
</script>

<style>
  .inspector-container {
    display: flex;
    max-width: 850px;
    margin: 40px auto;
    background: #ffffff;
    border: 1px solid #e2e8f0;
    border-radius: 8px;
    box-shadow: 0 4px 6px rgba(0,0,0,0.05);
    overflow: hidden;
    font-family: system-ui, -apple-system, sans-serif;
    min-height: 550px;
  }
  .inspector-sidebar {
    width: 32%;
    background: #f8fafc;
    border-right: 1px solid #e2e8f0;
    display: flex;
    flex-direction: column;
  }
  .inspector-menu-header {
    padding: 20px;
    background: #1e293b;
    color: #f8fafc;
    font-weight: bold;
    font-size: 1.05rem;
    letter-spacing: 0.5px;
    text-transform: uppercase;
  }
  .inspector-tab {
    padding: 16px 20px;
    cursor: pointer;
    border-bottom: 1px solid #e2e8f0;
    color: #475569;
    font-weight: 500;
    font-size: 0.95rem;
    transition: all 0.2s;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .inspector-tab:hover {
    background: #f1f5f9;
    color: #0f172a;
  }
  .inspector-tab.active {
    background: #ffffff;
    color: #3b82f6;
    border-left: 4px solid #3b82f6;
    font-weight: 600;
  }
  .tab-arrow {
    color: #cbd5e1;
    font-weight: bold;
  }
  .inspector-tab.active .tab-arrow {
    color: #3b82f6;
  }
  .inspector-content {
    width: 68%;
    padding: 35px;
    overflow-y: auto;
    background: #ffffff;
    transition: opacity 0.2s ease-in-out;
  }
  .content-title {
    font-size: 1.5rem;
    color: #0f172a;
    margin-bottom: 25px;
    padding-bottom: 15px;
    border-bottom: 2px solid #f1f5f9;
    font-weight: bold;
  }
  .content-section {
    margin-bottom: 30px;
  }
  .section-heading {
    font-size: 1.1rem;
    color: #1e293b;
    margin-bottom: 12px;
    font-weight: 600;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  /* Uses a standard unicode square instead of an emoji */
  .section-heading::before {
    content: "■"; 
    color: #3b82f6;
    font-size: 0.7rem;
  }
  .section-text {
    font-size: 0.95rem;
    color: #475569;
    line-height: 1.6;
  }
  .section-list {
    margin-top: 10px;
    padding-left: 20px;
    color: #475569;
    font-size: 0.95rem;
    line-height: 1.6;
  }
  .section-list li {
    margin-bottom: 10px;
  }
  .section-list strong {
    color: #1e293b;
  }

  /* Mobile responsiveness */
  @media (max-width: 768px) {
    .inspector-container { flex-direction: column; }
    .inspector-sidebar { width: 100%; border-right: none; border-bottom: 2px solid #e2e8f0; }
    .inspector-content { width: 100%; padding: 20px; }
  }
</style>

<div class="inspector-container">
  <div class="inspector-sidebar">
    <div class="inspector-menu-header">Hardware Modules</div>
    <div class="inspector-tab active" onclick="loadComponent('we', this)">Working Electrode (WE) <span class="tab-arrow">›</span></div>
    <div class="inspector-tab" onclick="loadComponent('ce', this)">Counter Electrode (CE) <span class="tab-arrow">›</span></div>
    <div class="inspector-tab" onclick="loadComponent('re', this)">Reference Electrode (RE) <span class="tab-arrow">›</span></div>
    <div class="inspector-tab" onclick="loadComponent('membrane', this)">Ion Exchange Membrane <span class="tab-arrow">›</span></div>
    <div class="inspector-tab" onclick="loadComponent('electrolyte', this)">Electrolyte Solution <span class="tab-arrow">›</span></div>
    <div class="inspector-tab" onclick="loadComponent('external', this)">External Systems <span class="tab-arrow">›</span></div>
  </div>
  
  <div class="inspector-content" id="inspector-display">
    <!-- Dynamic content renders here via JavaScript -->
  </div>
</div>

<script>
  const componentData = {
    we: {
      title: "Working Electrode (WE)",
      role: "The Working Electrode (Cathode) is the centerpiece of the experiment. It serves as the electron donor and the active site where the reduction reaction occurs. Connected to the negative terminal, the Working Electrode is usually the catalyst itself. In electrochemistry, the material of the electrode dictates the entire reaction pathway. The specific atomic arrangement on the surface determines whether CO₂ is converted into Carbon Monoxide, Methane, or Hydrogen gas. Therefore, the choice of the Working Electrode is the primary variable in any CO₂ reduction study.",
      properties:[
        "<strong>Surface Morphology and Composition:</strong> The roughness or nano-structure of the surface changes the local environment and the availability of reaction sites, often influencing the efficiency of the reaction. The purity of the metal is also critical, as even trace impurities can alter the product distribution.",
        "<strong>Pretreatment and Modification:</strong> There are multiple available modifications for the metal before running the experiment. These affect the reaction widely and change the specific products that are synthesized."
      ],
      choices:[
        "<strong>Copper (Cu):</strong> The most significant material in the field, as it is the only bulk metal capable of efficiently producing hydrocarbons (Ethylene, Ethanol).",
        "<strong>Other Transition Metals:</strong> Au, Zn, and Ag are commonly used to produce CO. Sn and Bi are commonly used to produce Formate.",
        "<em>Note:</em> These metals undergo several tuning modifications, such as oxidizing the metals to increase surface area, replacing bulk metals with nanoparticles, and supporting metals with structures like carbon to aid in mass transport."
      ]
    },
    ce: {
      title: "Counter Electrode (CE)",
      role: "The Counter Electrode (Anode) completes the electrical circuit. While the focus of the experiment is on the cathode side, the anode is necessary for the system to fully function. Connected to the positive terminal, the Counter Electrode balances the reaction. For every electron consumed by the CO₂ reduction at the cathode, an oxidation reaction must occur here (typically splitting water into Oxygen gas).",
      properties:[
        "<strong>Chemical Inertness:</strong> The material must withstand high oxidation potentials without corroding. If it degrades or dissolves during the experiment, metal ions can cross the cell and contaminate the Working Electrode, rendering the data invalid.",
        "<strong>Surface Area:</strong> To ensure the Counter Electrode does not become a bottleneck, researchers verify that its surface area is significantly larger than that of the Working Electrode. This establishes a fair test when comparing between different catalysts."
      ],
      choices:[
        "<strong>Platinum (Pt):</strong> The academic standard due to its exceptional stability and conductivity. It usually comes in the form of a wire or mesh.",
        "<strong>Graphite/Carbon:</strong> A cost-effective alternative often used in educational settings, though it requires constant monitoring for degradation over long-term experiments.",
        "<strong>Dimensionally Stable Anodes (DSA):</strong> Industrial-grade oxides (such as Iridium Oxide) designed specifically for high-current durability."
      ]
    },
    re: {
      title: "Reference Electrode (RE)",
      role: "The Reference Electrode provides a stable, known voltage against which the Working Electrode is measured. In a standard 3-electrode setup, the Reference Electrode does not carry current. Its sole purpose is to sense the potential at the Working Electrode without interference from the Anode. Without a Reference Electrode, the recorded voltage reflects the entire cell, which includes wire and solution resistance, making it impossible to determine the true energy applied to the reaction.",
      properties:[
        "<strong>Stability:</strong> The potential of the reference must not change over time. If the reference shifts by even 0.1V, the data becomes invalid because the true energy applied to the CO₂ is no longer known.",
        "<strong>Impedance:</strong> It requires a low-resistance connection to the electrolyte to ensure fast and accurate reading by the potentiostat."
      ],
      choices:[
        "<strong>Silver/Silver Chloride (Ag/AgCl):</strong> The most common reference electrode for aqueous (water-based) experiments due to its stability and non-toxicity.",
        "<strong>Saturated Calomel Electrode (SCE):</strong> An older standard utilizing Mercury, which has largely been phased out due to toxicity concerns.",
        "<strong>Reversible Hydrogen Electrode (RHE):</strong> The standard reference in theoretical literature. While researchers report data vs. RHE, they physically use an Ag/AgCl electrode in the lab and convert the figures later using the Nernst equation: <em>E(RHE) = E(Ag/AgCl) + 0.197 V + (0.0591 V × pH)</em>."
      ]
    },
    membrane: {
      title: "Ion Exchange Membrane",
      role: "The Membrane is the physical barrier located inside the bridge of the H-Cell, separating the Cathodic chamber from the Anodic chamber. The membrane serves two key functions: it must block chemicals while simultaneously allowing electricity to flow. It prevents gases produced at the Anode from migrating to the Cathode, while allowing ions to pass through freely to complete the electrical circuit.",
      properties:[
        "<strong>Ionic Conductivity:</strong> Dictates how easily ions flow through the material. High resistance leads to a large voltage drop across the cell, referred to as the IR drop.",
        "<strong>Gas Crossover:</strong> The capacity to halt gas bubbles. If O₂ crosses the membrane, it can re-oxidize the products, creating invalid experimental results."
      ],
      choices:[
        "<strong>Nafion (Cation Exchange Membrane):</strong> The industry standard, specifically Nafion 117 or 212. It allows positive ions (H⁺) to pass but strictly blocks negative ions and gases.",
        "<strong>Anion Exchange Membranes (AEM):</strong> Membranes designed to allow negative ions (OH⁻ or HCO₃⁻) to pass. These are frequently utilized in alkaline electrolytes.",
        "<strong>Salt Bridges / Glass Frits:</strong> The classic laboratory alternative. While they exhibit higher electrical resistance than Nafion, they are cost-effective and sufficient for fundamental studies where high current density is not the objective."
      ]
    },
    electrolyte: {
      title: "Electrolyte Solution",
      role: "The electrolyte is the conductive liquid that fills the cell chambers. It serves three main functions: closing the circuit between the Anode and Cathode, providing the protons (H⁺) or water molecules (H₂O) required to bond with the Carbon, and acting as a pH buffer to keep the reaction environment stable as carbonic acid forms in the solution.",
      properties:[
        "<strong>Conductivity:</strong> Higher salt concentrations reduce electrical resistance, ensuring less energy is wasted as heat.",
        "<strong>Buffering Capacity:</strong> If the local pH at the electrode surface fluctuates too drastically, the reaction may switch from producing CO to producing Hydrogen gas.",
        "<strong>Purity:</strong> This is a highly common source of error. Low-grade salts often contain trace amounts of Iron or Zinc, which will deposit onto the electrode and compromise the experiment."
      ],
      choices:[
        "<strong>0.1M Potassium Bicarbonate (KHCO₃):</strong> The standard for H-Cell experiments. Because it is chemically similar to dissolved CO₂, it naturally maintains a slightly-acidic pH which is optimal for a variety of catalysts.",
        "<strong>Potassium Hydroxide (KOH):</strong> An alkaline electrolyte used in specific Flow Cell reactors. It is rarely used in standard H-Cells due to the availability of better alternatives.",
        "<strong>Potassium Chloride (KCl):</strong> A basic salt sometimes used for preliminary testing, though it lacks the buffering capacity of bicarbonate."
      ]
    },
    external: {
      title: "External Control & Supply Systems",
      role: "The cell alone cannot operate independently. The experiment requires external hardware to deliver reactants, control the energy input, and collect analytical data. This category involves two distinct components: the Gas Feed (delivering the CO₂ reactant) and the Electronic Feed (delivering and measuring electricity). Absolute stability in these external systems is mandatory for generating consistent data.",
      properties:[
        "<strong>Mass Transport:</strong> The CO₂ must be delivered at a constant rate. In professional laboratories, this flow is regulated down to the standard cubic centimeter per minute (sccm).",
        "<strong>Voltage Compliance:</strong> The power source must possess the capacity to maintain the set voltage even as the internal resistance of the cell fluctuates during the experiment."
      ],
      choices:[
        "<strong>Gas Supply:</strong> A standard CO₂ cylinder is used to supply gas to the system. Researchers must ensure high-purity grades are used, as lower grades contain harmful impurities.",
        "<strong>Electrical Control:</strong> The standard device is the Potentiostat. This computer-controlled instrument acts as both the power supply and the multimeter, executing automated data logging."
      ]
    }
  };

  function loadComponent(key, element) {
    // Update menu styling
    document.querySelectorAll('.inspector-tab').forEach(tab => tab.classList.remove('active'));
    element.classList.add('active');

    const data = componentData[key];
    const display = document.getElementById('inspector-display');
    
    // Construct HTML lists
    let propHtml = '';
    data.properties.forEach(p => { propHtml += `<li>${p}</li>`; });

    let choiceHtml = '';
    data.choices.forEach(c => { choiceHtml += `<li>${c}</li>`; });

    // Fade animation
    display.style.opacity = 0;
    setTimeout(() => {
      display.innerHTML = `
        <div class="content-title">${data.title}</div>
        
        <div class="content-section">
          <div class="section-heading">Role & Significance</div>
          <div class="section-text">${data.role}</div>
        </div>

        <div class="content-section">
          <div class="section-heading">Key Properties</div>
          <ul class="section-list">${propHtml}</ul>
        </div>

        <div class="content-section">
          <div class="section-heading">Common Choices in Research</div>
          <ul class="section-list">${choiceHtml}</ul>
        </div>
      `;
      display.style.opacity = 1;
    }, 200);
  }

  // Initialize the first tab on load
  document.addEventListener("DOMContentLoaded", () => {
    loadComponent('we', document.querySelector('.inspector-tab'));
  });
</script>

### Component Table

| **Component** | **Role** | **Standard Materials** |
| :--- | :--- | :--- |
| **Working Electrode (WE)** | This is the Cathode where CO2 reduction happens. | Copper Foil (Cu), Gold (Au), or Silver (Ag) |
| **Counter Electrode (CE)** | This is the Anode that completes the circuit (usually making Oxygen). | Platinum (Pt) Mesh or Wire |
| **Reference Electrode (RE)** | Measures the voltage accurately without passing current. | Ag/AgCl (Silver/Silver Chloride) |
| **H-Cells and External Supplies** | A two-chamber glass vessel and essential $CO_2$ and electricity sources. | Potentiostat, $CO_2$ Gas Tank |
| **Nafion Membrane** | Allows protons ($H^+$) to cross but stops fuel from mixing with oxygen. | Nafion 117 or 115 |
| **Electrolyte** | Conducts ions and holds the dissolved CO2. | 0.1M $KHCO_3$ (Potassium Bicarbonate) |

---

### 2.1 The Three Electrodes

#### 2.1.1 The Working Electrode (WE)

##### Role & Significance
The Working Electrode (Cathode) is the centerpiece of the experiment. It serves as the electron donor and the active site where the reduction reaction occurs. Connected to the negative terminal, most of the time, the Working Electrode is the catalyst. In electrochemistry, the material of the electrode dictates the entire reaction pathway. The specific atomic arrangement on the surface determines whether $CO_2$ is converted into Carbon Monoxide, Methane, or just Hydrogen gas. Therefore, the choice of the Working Electrode is the primary variable in any $$CO_2$$ reduction study.

##### Key Properties
1.  **Surface Morphology and Composition:** The roughness or nano-structure of the surface changes the local environment and the availability of reaction sites, often influencing the efficiency of the reaction. The purity of the metal is also critcal, and even trace of impurities can alter the product distribution.
2.  **Pretreatment and Modification:** There are multiples available modification of the metal before running the experiment. This affects the reaction widely and often change what product are produced.

##### Common Choices in Research
In this field, the WE varies by a lot to each researchers analyzing different materials. However, the most common working electrode are metals:
*   **Copper (Cu):** The most significant material in the field, as it is the only bulk metal capable of efficiently producing hydrocarbons (Ethylene, Ethanol).
*   **Other Transition Metals:** Au, Zn and Ag are commonly used to produce CO. And Sn and Bi are commonly used to produce Formate
These metals can undergoes several tuning and modifying as stated. The common example are: oxidizing metals to help increase its surface area and change the product distribution, replacing chunks of metal by their nano particles might improve their faradaic efficiency and supporting metals with structures like carbon could help in mass transport of $$CO_2$$.

---

#### 2.1.2 The Counter Electrode (CE)

##### Role & Significance
The Counter Electrode (Anode) completes the electrical circuit. While the focus of the experiment is on the cathode side, the anode is necessary for the system to fully function. Connected to the positive terminal, the Counter Electrode balances the reaction. For every electron consumed by the $CO_2$ reduction at the cathode, an oxidation reaction must occur here (typically splitting water into Oxygen).

##### Key Properties
1.  **Chemical Inertness:** The material must withstand high oxidation potentials without corroding. If it degrades or dissolves during the experiment, metal ions can cross the cell and contaminate the Working Electrode, making the data invalid.
2.  **Surface Area:** To ensure the Counter Electrode does not become a bottleneck, researchers ensure its surface area is significantly larger than that of the Working Electrode. This makes the test fair when compairing between Catalysts.

##### Common Choices in Research
*   **Platinum (Pt):** The academic standard due to its exceptional stability and conductivity, usually comes in form of wire or mesh.
*   **Graphite/Carbon:** A cost-effective alternative often used in educational settings, though it requires monitoring for degradation over long-term experiments.
*   **Dimensionally Stable Anodes (DSA):** Industrial-grade oxides (like Iridium Oxide) designed specifically for high-current durability.

---

#### 2.1.3 The Reference Electrode (RE)

##### Role & Significance
The Reference Electrode provides a stable, known voltage against which the Working Electrode is measured. In a standard 3-electrode setup, the Reference Electrode does not carry current. Its sole purpose is to sense the potential at the Working Electrode without interference from the Anode. Without a Reference Electrode, you will be measuring the voltage across the entire cell, which includes the wires and solution resistance, making it impossible to know exactly how much energy is being applied to the reaction itself.

##### Key Properties
1.  **Stability:** The potential of the reference must not change over time. If the reference move up or down by even 0.1V, the data becomes useless because you no longer know the true energy applied to the $CO_2$.
2.  **Impedance:** It must have a low-resistance connection to the electrolyte to ensure fast and accurate reading by the potentiostat.

##### Common Choices in Research
*   **Silver/Silver Chloride (Ag/AgCl):** The most common reference electrode for aqueous (water-based) experiments due to its stability and non-toxicity.
*   **Saturated Calomel Electrode (SCE):** An older standard using Mercury, but now has largely phased out due to toxicity concerns.
*   **Reversible Hydrogen Electrode (RHE):** This is the reference in theoryx. While researchers normally report data vs. RHE, they physically use an Ag/AgCl electrode in the lab and convert the numbers later through the equation below.

$$ E(RHE) = E(Ag/AgCl) + 0.197 V + (0.0591 V × pH) $$

*  **E(Ag/AgCl):** The raw voltage number vs Ag/AgCl.
*  **0.197 V:** The standard constant for a standard Ag/AgCl electrode at room temperature.
*  **0.0591 V × pH:** Nernst equation factor: adjusts the voltage based on environment acidity.
          
---

### 2.2 The Reaction Vessel

#### 2.2.1 The Membrane

##### Role & Significance
The Membrane is the physical barrier located inside the bridge of the H-Cell, separating the Cathodic chamber from the Anodic chamber. The membrane serves two key functions: it must block chemicals while allowing electricity to flow.
1.  **Isolation:** It prevents gases produced at the Anode from migrating to the Cathode which, otherwise, would have ruined the reaction.
2.  **Conduction:** It must allow ions to pass through freely to complete the circuit. If the membrane is restrictive, the electrical resistance increases, and the cell heats up.

##### Key Properties
1.  **Ionic Conductivity:** How easily ions flow through. High resistance leads to a large voltage drop, called "IR drop", across the cell.
2.  **Gas Crossover:** The ability to stop gas bubbles. If $O_2$ crosses over, it can re-oxidize your products, making it look like your experiment failed.

##### Common Choices in Research
*   **Nafion (Cation Exchange Membrane):** The industry standard specifically Nafion 117 or 212. It allows positive ions ($H^+$) to pass but blocks negative ions and gases.
*   **Anion Exchange Membranes (AEM):** Membranes that allow negative ions ($OH^-$ or $HCO_3^-$) to pass. These are often used in alkaline electrolytes.
*   **Salt Bridges / Glass Frits:** The classic laboratory alternative. While they have higher electrical resistance than Nafion, they are cost-effective and sufficient for fundamental studies where high current density is not the primary goal.

---

#### 2.2.2 The Electrolyte

##### Role & Significance
The electrolyte is the conductive liquid that fills the cell.
It serves three main functions:
1.  **Ionic Conduction:** It closes the circuit between the Anode and Cathode acting like a wire in a circuit.
2.  **Reactant Source:** It provides the protons ($H^+$) or water molecules ($H_2O$) required to bond with the Carbon.
3.  **pH Buffer:** $CO_2$ is an acidic gas. When bubbled into water, it forms carbonic acid. The electrolyte buffer (retain the same pH) to keep the reaction environment stable.

##### Key Properties
1.  **Conductivity:** Higher salt concentrations reduce electrical resistance, wasting less energy as heat.
2.  **Buffering Capacity:** If the local pH at the electrode surface changes too drastically, the reaction can switch from making $CO$ to making Hydrogen.
3.  **Purity:** This is the most common source of error. Low-grade salts often contain trace amounts of Iron or Zinc, which will plate onto the electrode and ruining experiment.

##### Common Choices in Research
*   **0.1M Potassium Bicarbonate ($KHCO_3$):** The standard for H-Cell experiments. Because it is chemically similar to dissolved $CO_2$, it naturally maintains a slightly-acidic pH which is ideal for many catalysts. It is recommended for beginners to use $KHCO_3$ first before considering changing to other advance electrolytes.
*   **Potassium Hydroxide ($KOH$):** A alkaline electrolyte used in some Flow Cell reactors. It is not commonly used in H-Cell due to other better options.
*   **Potassium Chloride ($KCl$):** A simple salt sometimes used for testing, though it lacks the buffering ability of bicarbonate.

---

#### 2.2.3 External Control & Supply Systems

##### Role & Significance
Only the cell alone cannot operate. The experiment requires external hardware to deliver reactants, control the energy input and collect the data.
This category involves two distinct feeds:
1.  **The Gas Feed:** Delivers the $CO_2$ reactant to the cell.
2.  **The Electronic Feed:** Delivers and measures the electricity.
If the gas flow fluctuates, the concentration of $CO_2$ at the electrode changes. If the voltage fluctuates, the reaction rate changes. Stability in these external systems is required for consistent data.

##### Key Properties
1.  **Mass Transport:** The $CO_2$ must be delivered at a constant rate. In professional labs, this is controlled to the milliliter per minute (sccm).
2.  **Voltage Compliance:** The power source must be able to maintain the set voltage even if the resistance of the cell changes during the experiment.

##### Common Choices in Research
*   **Gas Supply:** Mostly used CO2 tank to supply gas in the system; however, user must be aware of its grade as lower grade can comes with impurities.
*   **Electrical Control:** The most common device is the Potentiostat. It is a computer-controlled device that acts as both the power supply and the multimeter, automatically logging data.

---

## 3. Pre-Experiment Preparation
Before you assemble the cell, you must prepare the materials.

### 3.1 Polishing the Electrode
The electrode surface must first be atomically clean.
1.  **Sand:** Use fine-grit sandpaper to remove visible oxidation.
2.  **Polish:** Place a polishing cloth on a flat surface. Add Alumina slurry ($0.05 \mu m$).
3.  **The Figure-8:** Move the electrode in a "Figure-8" motion.
4.  **Clean:** Rinse with Distilled Water.
5.  **Sonicate:** Place the electrode in a beaker of water/acetone and put it in an ultrasonic bath for 5 minutes. This vibrates off the microscopic dust left by the polishing.

![Polishing Motion](./assets/images/polishing.png){: style="display:block; margin-left:auto; margin-right:auto; width:75%;" }

*Figure : The correct "Figure-8" motion for polishing electrodes to ensure an even surface.*

### 3.2 Membrane Hydration
The Nafion membrane acts like a sponge. If it is dry, it is brittle and non-conductive.
*   **The Rule:** Never let the membrane dry out.
*   **Activation:** Soak the membrane in your electrolyte or deionized water for at least 24 hours before use.
*   **Storage:** Keep it in a sealed jar of water when not in use.

---

## 4. Assembly & Wiring
Once the parts are clean, assemble the H-Cell. Ensure the membrane is sandwiched tightly between the two chambers to prevent leaks.

### 4.1 The Wiring
Connecting the Potentiostat can be confusing because cable colors vary by brand; however, the logic is always the same:

| **Cable Role** | **Common Color** | **Connects To** |
| :--- | :--- | :--- |
| **Working (WE)** | Red | The Working Electrode. This is where we measure the reaction. |
| **Counter (CE)** | Black | Platinum Wire. This completes the circuit. |
| **Reference (RE)** | Blue | The Ag/AgCl. This measures the voltage. |
| **Sense (S)** | Often attached to WE | Connect this to Working Electrode as well to improve accuracy. |

> *Warning: If you swap the Counter and Reference cables, you can instantly destroy your Reference Electrode by forcing high current through it.**

<style>
  .wiring-container {
    background: #ffffff;
    padding: 25px;
    border-radius: 8px;
    font-family: system-ui, -apple-system, sans-serif;
    max-width: 700px;
    margin: 30px auto;
    border: 1px solid #e2e8f0;
    box-shadow: 0 4px 6px rgba(0,0,0,0.05);
    text-align: center;
  }
  .wiring-header {
    color: #1e293b;
    margin-bottom: 10px;
    font-size: 1.25rem;
    font-weight: bold;
  }
  .wiring-instructions {
    color: #475569;
    font-size: 0.95rem;
    margin-bottom: 20px;
  }
  .wiring-svg {
    background: #f8fafc;
    border: 1px solid #cbd5e1;
    border-radius: 6px;
    width: 100%;
    max-width: 600px;
    height: auto;
    user-select: none;
  }
  .node {
    cursor: pointer;
    transition: filter 0.2s;
  }
  .node:hover {
    filter: brightness(0.85);
  }
  .node-active {
    stroke: #eab308; /* Yellow highlight when selected */
    stroke-width: 4px;
  }
  .wire-line {
    stroke-width: 4px;
    stroke-linecap: round;
    pointer-events: none;
  }
  .verify-btn {
    background: #334155;
    color: white;
    border: none;
    padding: 12px 24px;
    font-size: 1rem;
    font-weight: bold;
    border-radius: 4px;
    cursor: pointer;
    margin-top: 20px;
    transition: background 0.2s;
  }
  .verify-btn:hover { background: #1e293b; }
  .reset-btn {
    background: #e2e8f0;
    color: #334155;
    border: none;
    padding: 12px 24px;
    font-size: 1rem;
    font-weight: bold;
    border-radius: 4px;
    cursor: pointer;
    margin-top: 20px;
    margin-left: 10px;
    transition: background 0.2s;
  }
  .reset-btn:hover { background: #cbd5e1; }
  #wiring-feedback {
    margin-top: 20px;
    padding: 15px;
    border-radius: 4px;
    display: none;
    font-size: 0.95rem;
    font-weight: 500;
    text-align: left;
    line-height: 1.5;
  }
  .feedback-success { background: #dcfce7; color: #166534; border: 1px solid #bbf7d0; }
  .feedback-error { background: #fee2e2; color: #991b1b; border: 1px solid #fecaca; }
</style>

<div class="wiring-container">
  <div class="wiring-header">Potentiostat Wiring Configuration</div>
  <div class="wiring-instructions">Click a colored potentiostat terminal, then click the corresponding electrode below to establish a connection.</div>
  
  <svg class="wiring-svg" viewBox="0 0 600 400" id="wiring-canvas">
    <!-- Dynamic Wires will be injected here -->
    <g id="wire-layer"></g>

    <!-- Potentiostat Box -->
    <rect x="150" y="20" width="300" height="80" rx="8" fill="#475569" />
    <text x="300" y="50" font-size="16" fill="white" font-weight="bold" text-anchor="middle" pointer-events="none">Potentiostat Output</text>
    
    <!-- Potentiostat Terminals -->
    <!-- Red (WE) -->
    <circle cx="200" cy="100" r="15" fill="#ef4444" class="node terminal" id="term-red" onclick="selectTerminal('red', 200, 100)" />
    <text x="200" y="80" font-size="12" fill="white" text-anchor="middle" pointer-events="none">Red</text>
    
    <!-- Black (CE) -->
    <circle cx="300" cy="100" r="15" fill="#1e293b" class="node terminal" id="term-black" onclick="selectTerminal('black', 300, 100)" />
    <text x="300" y="80" font-size="12" fill="white" text-anchor="middle" pointer-events="none">Black</text>
    
    <!-- Blue (RE) -->
    <circle cx="400" cy="100" r="15" fill="#3b82f6" class="node terminal" id="term-blue" onclick="selectTerminal('blue', 400, 100)" />
    <text x="400" y="80" font-size="12" fill="white" text-anchor="middle" pointer-events="none">Blue</text>

    <!-- Electrodes -->
    <!-- Ag/AgCl (RE) -->
    <rect x="50" y="300" width="120" height="60" rx="4" fill="#e2e8f0" stroke="#94a3b8" stroke-width="2" class="node electrode" id="elec-re" onclick="selectElectrode('re', 110, 300)" />
    <text x="110" y="325" font-size="14" fill="#334155" font-weight="bold" text-anchor="middle" pointer-events="none">Ag/AgCl Sensor</text>
    <text x="110" y="345" font-size="12" fill="#64748b" text-anchor="middle" pointer-events="none">Reference</text>

    <!-- Copper Foil (WE) -->
    <rect x="240" y="300" width="120" height="60" rx="4" fill="#b45309" stroke="#78350f" stroke-width="2" class="node electrode" id="elec-we" onclick="selectElectrode('we', 300, 300)" />
    <text x="300" y="325" font-size="14" fill="white" font-weight="bold" text-anchor="middle" pointer-events="none">Copper Foil</text>
    <text x="300" y="345" font-size="12" fill="#fde68a" text-anchor="middle" pointer-events="none">Cathode</text>

    <!-- Platinum Mesh (CE) -->
    <rect x="430" y="300" width="120" height="60" rx="4" fill="#94a3b8" stroke="#475569" stroke-width="2" class="node electrode" id="elec-ce" onclick="selectElectrode('ce', 490, 300)" />
    <text x="490" y="325" font-size="14" fill="white" font-weight="bold" text-anchor="middle" pointer-events="none">Platinum Mesh</text>
    <text x="490" y="345" font-size="12" fill="#e2e8f0" text-anchor="middle" pointer-events="none">Anode</text>
  </svg>

  <div>
    <button class="verify-btn" onclick="verifyCircuit()">Verify Circuit</button>
    <button class="reset-btn" onclick="resetWiring()">Reset</button>
  </div>
  
  <div id="wiring-feedback"></div>
</div>

<script>
  let activeTerminal = null;
  const connections = { red: null, black: null, blue: null };
  const wireColors = { red: '#ef4444', black: '#1e293b', blue: '#3b82f6' };
  
  function selectTerminal(color, x, y) {
    // Clear previous active state
    document.querySelectorAll('.terminal').forEach(el => el.classList.remove('node-active'));
    
    activeTerminal = { color: color, x: x, y: y };
    document.getElementById('term-' + color).classList.add('node-active');
  }

  function selectElectrode(elecId, x, y) {
    if (!activeTerminal) return;

    const color = activeTerminal.color;
    connections[color] = elecId;

    renderWires();
    
    // Reset active terminal
    document.querySelectorAll('.terminal').forEach(el => el.classList.remove('node-active'));
    activeTerminal = null;
  }

  function renderWires() {
    const layer = document.getElementById('wire-layer');
    layer.innerHTML = ''; // Clear existing wires

    // Terminal coords
    const tCoords = { red: [200, 100], black:[300, 100], blue: [400, 100] };
    // Electrode coords
    const eCoords = { re: [110, 300], we:[300, 300], ce: [490, 300] };

    for (const[color, elecId] of Object.entries(connections)) {
      if (elecId) {
        const x1 = tCoords[color][0];
        const y1 = tCoords[color][1];
        const x2 = eCoords[elecId][0];
        const y2 = eCoords[elecId][1];

        const line = document.createElementNS('http://www.w3.org/2000/svg', 'line');
        line.setAttribute('x1', x1);
        line.setAttribute('y1', y1);
        line.setAttribute('x2', x2);
        line.setAttribute('y2', y2);
        line.setAttribute('stroke', wireColors[color]);
        line.setAttribute('class', 'wire-line');
        layer.appendChild(line);
      }
    }
  }

  function resetWiring() {
    connections.red = null;
    connections.black = null;
    connections.blue = null;
    activeTerminal = null;
    document.querySelectorAll('.terminal').forEach(el => el.classList.remove('node-active'));
    renderWires();
    const feedback = document.getElementById('wiring-feedback');
    feedback.style.display = 'none';
    feedback.className = '';
  }

  function verifyCircuit() {
    const feedback = document.getElementById('wiring-feedback');
    feedback.style.display = 'block';
    feedback.className = '';

    // Correct mapping: Red = WE, Black = CE, Blue = RE
    const we = connections.red;
    const ce = connections.black;
    const re = connections.blue;

    if (!we || !ce || !re) {
      feedback.classList.add('feedback-error');
      feedback.innerHTML = "Incomplete circuit. Please ensure all three cables are connected to an electrode.";
      return;
    }

    if (we === 'we' && ce === 'ce' && re === 're') {
      feedback.classList.add('feedback-success');
      feedback.innerHTML = "Circuit verified. The wiring configuration is correct. The potentiostat is ready for operation.";
    } else if (ce === 're' || re === 'ce') {
      feedback.classList.add('feedback-error');
      feedback.innerHTML = "Critical error. The Counter and Reference cables are inverted. This configuration forces high current through the sensitive Ag/AgCl sensor, resulting in permanent damage to the electrode.";
    } else {
      feedback.classList.add('feedback-error');
      feedback.innerHTML = "Incorrect configuration. The current setup will not yield valid electrochemical data. Please review the standard 3-electrode wiring protocol and try again.";
    }
  }
</script>

---

## 5. The Start-Up Protocol
You cannot simply turn on the voltage. You must first create the right environment.

### 5.1 Purging
Air contains gases other than $CO_2$ that aren't inert. They can react and steal the electricity from your CO2RR, so we need to remove them first.

1.  **Insert the Gas Tube:** Place the CO2 gas tube directly into the liquid at the bottom of the cell.
2.  **Bubble:** Let the $CO_2$ bubble vigorously for 20-30 minutes before running the experiment. This ensures that the solutionus is saturated with $CO_2$ and every experiment is valid.
3.  **Check:** Ensure that the gas isn't blanketting in the headspace and is sparging in the solution. Blanketting could starve your catalyst from receiving sufficient $CO_2$.
4.  **Measure:** Measure the flow rate of the $CO_2$ for each test typically by using mass flow controller. This is crucial for further calculation for accurate result.

![Sparging vs Blanketing](./assets/images/sparging.png){: style="display:block; margin-left:auto; margin-right:auto; width:75%;" }

*Figure : Ensure the gas tube goes into the liquid to fully saturate the electrolyte.*

### 5.2 The Leak Check
Before starting the electricity:
1.  Close the cell outlet.
2.  Apply soapy water to the joints.
3.  If you see bubbles growing on the outside, you have a gas leak. Tighten the clamps.

---

## Conclusion
There is no universally "correct" $CO_2$ electrochemical setup. Valid designs are chosen based on research goals, constraints, and trade-offs. The best equipment is simply the setup that allows you to isolate the variable you are trying to study while minimizing sources of error like contamination or instability. Further information on the exact set up each experiment should be obtain from literature reviews and each consequence should be carefully considered before adjusting.

<style>
  .page-nav { display: flex; justify-content: space-between; align-items: center; margin-top: 50px; padding-top: 20px; border-top: 2px solid #e2e8f0; font-family: system-ui, -apple-system, sans-serif; }
  .nav-btn { display: inline-block; padding: 10px 20px; background: #ffffff; color: #3b82f6; text-decoration: none; border: 1px solid #cbd5e1; border-radius: 6px; font-weight: 600; transition: all 0.2s; }
  .nav-btn:hover { background: #3b82f6; color: #ffffff; border-color: #3b82f6; text-decoration: none; }
  .nav-home { color: #64748b; font-weight: bold; text-decoration: none; transition: color 0.2s; }
  .nav-home:hover { color: #0f172a; text-decoration: underline; }
</style>

<div class="page-nav">
  <a href="./theory" class="nav-btn">← Previous: Theory</a>
  <a href="./" class="nav-home">Back to Directory</a>
  <a href="./analysis" class="nav-btn">Next: Data Analysis →</a>
</div>
