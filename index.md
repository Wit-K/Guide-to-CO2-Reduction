<script type="text/javascript" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>

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

## Main Index Sections

### [1. Foundations & Theory](./theory)
Key electrochemical concepts explained from the root with intuition and context. Connecting equations to real-world experiments and understanding its reaction mechanisms.

### [2. Experimental Design](./experiment)
A guide to the hardware. Identifying the correct electrochemical cell, electrode and electrolyte for different experiments.

### [3. Data Collection, Analysis & Interpretation](./analysis)
How to read typical results, avoid common mistakes, and understand what conclusions can be made.

### [4. Common Problems & Troubleshooting](./troubleshooting)
Conceptual and experimental issues beginners frequently encounter, and how to reason through them.

### [5. Curated Resources](./resources)
Papers, textbooks, and reviews annotated with guidance on how to approach them as a beginner.

<style>
  .tree-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 20px;
    margin: 40px 0;
    font-family: system-ui, -apple-system, sans-serif;
  }
  .tree-row {
    display: flex;
    gap: 20px;
    justify-content: center;
    width: 100%;
    flex-wrap: wrap;
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
  /* Little triangle pointer for tooltip */
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
    font-size: 24px;
    color: #9ca3af;
  }
</style>

<div class="tree-container">
  <div class="tree-row">
    <div class="tree-node">CO₂ (Carbon Dioxide)
      <div class="node-tooltip">
        <span class="tooltip-title">Carbon Dioxide (CO₂)</span>
        Our highly stable starting material. Requires significant energy and a catalyst to break its C=O double bonds.
      </div>
    </div>
  </div>
  
  <div class="tree-arrow">⬇️</div>
  
  <div class="tree-row">
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
  
  <div class="tree-arrow">⬇️</div>
  
  <div class="tree-row">
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
<p align="center"><em>Interactive Figure: Hover over any product to view its properties and real-world value.</em></p>

---
*Created by [Wit Kulvutiroj]*
