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

# Common Problems & Troubleshooting
*Part 4: A Diagnostic Approach to Unexpected Experimental Outcomes*

---

## Quick Check

| Symptom | Possible Cause | Go To Section |
| :--- | :--- | :--- |
| Current is 0.00 A | Broken circuit or loose cable | Section 2 |
| Current is fluctuating wildly | Trapped bubbles or loose connection | Section 3 |
| Liquid level is changing | Membrane leak | Section 4 |
| Data looks weird or drifted | Reference electrode issue | Section 3 |

<style>
  .wizard-container { max-width: 650px; margin: 40px auto; background: #e8eaf6; padding: 30px; border-radius: 8px; border: 2px solid #3f51b5; font-family: Arial, sans-serif; text-align: center; min-height: 250px; display: flex; flex-direction: column; justify-content: center;}
  .wizard-question { font-size: 20px; font-weight: bold; color: #1a237e; margin-bottom: 25px; }
  .wizard-options { display: flex; flex-direction: column; gap: 10px; max-width: 400px; margin: 0 auto; }
  .wizard-btn { background: #3f51b5; color: white; border: none; padding: 12px 20px; font-size: 16px; border-radius: 5px; cursor: pointer; transition: 0.2s; font-weight: bold; }
  .wizard-btn:hover { background: #303f9f; transform: translateY(-2px); }
  .wizard-result { background: #fff; padding: 20px; border-radius: 8px; border-left: 5px solid #4caf50; display: none; text-align: left; }
  .restart-btn { margin-top: 20px; background: #9e9e9e; color: white; border: none; padding: 8px 15px; border-radius: 4px; cursor: pointer; }
  .restart-btn:hover { background: #757575; }
</style>

<div class="wizard-container" id="wizard-box">
  <div id="wizard-content">
    <div class="wizard-question" id="q-text">What is the main issue you are experiencing?</div>
    <div class="wizard-options" id="options-box">
      <!-- Options injected by JS -->
    </div>
  </div>
  
  <div class="wizard-result" id="wizard-result">
    <h3 style="margin-top:0; color: #2e7d32;" id="res-title">Diagnosis</h3>
    <p id="res-text" style="font-size: 16px; line-height: 1.5;"></p>
    <button class="restart-btn" onclick="startWizard()">🔄 Start Over</button>
  </div>
</div>

<script>
  const wizardData = {
    start: {
      q: "What is the main issue you are experiencing right now?",
      options:[
        { text: "My Faradaic Efficiency (FE) is too low", next: "fe_issue" },
        { text: "My current is dropping over time", next: "decay_issue" },
        { text: "The Reference Electrode voltage looks weird", next: "re_issue" }
      ]
    },
    fe_issue: {
      q: "What is the main product replacing your CO₂ products?",
      options:[
        { text: "Mostly Hydrogen (H₂)", next: "res_h2" },
        { text: "I can't find the missing FE (Gas + Liquid don't add to 100%)", next: "res_missing" }
      ]
    },
    decay_issue: {
      q: "Look at your liquid electrolyte. Is it turning a different color?",
      options:[
        { text: "Yes, it's turning slightly blue/green", next: "res_dissolve" },
        { text: "No, it is perfectly clear", next: "res_poisoning" }
      ]
    },
    re_issue: {
      q: "Have you checked the glass tip of the Reference Electrode?",
      options:[
        { text: "Yes, there is a tiny bubble trapped inside the frit", next: "res_bubble" },
        { text: "The tip is clear, but the white wire inside looks black/brown", next: "res_re_dead" }
      ]
    }
  };

  const resultsData = {
    res_h2: { title: "Hydrogen Evolution Takeover", text: "<strong>Diagnosis:</strong> The Hydrogen Evolution Reaction (HER) is out-competing CO₂ reduction.<br><br><strong>Fix:</strong> Check your CO₂ flow rate (is it saturated?). Alternatively, your catalyst might be contaminated with a highly active HER metal like Pt or Ni. Try cleaning your cell in acid." },
    res_missing: { title: "Missing Products", text: "<strong>Diagnosis:</strong> You have unmeasured products, or a leak!<br><br><strong>Fix:</strong> 1. Run an NMR on the liquid to check for Formate or Acetate. 2. Use soapy water on your gas fittings to check for leaks. 3. Ensure your GC is calibrated properly." },
    res_dissolve: { title: "Anodic Dissolution", text: "<strong>Diagnosis:</strong> Your Copper/Metal catalyst is dissolving into the liquid!<br><br><strong>Fix:</strong> You might be applying a positive (oxidizing) potential by accident, or your counter electrode is leaking metal ions into the catholyte. Check your membrane!" },
    res_poisoning: { title: "Surface Poisoning", text: "<strong>Diagnosis:</strong> The surface of your catalyst is getting blocked.<br><br><strong>Fix:</strong> Carbon buildup or heavy metal trace impurities are sticking to the catalyst. Use a fresh, highly pure electrolyte and try running the experiment again." },
    res_bubble: { title: "Trapped Bubble", text: "<strong>Diagnosis:</strong> A gas bubble is blocking the ionic bridge in the reference electrode tip.<br><br><strong>Fix:</strong> This acts like a giant resistor! Gently flick the tip of the reference electrode to dislodge the bubble before inserting it into the cell." },
    res_re_dead: { title: "Dead Reference Electrode", text: "<strong>Diagnosis:</strong> The Ag/AgCl coating has degraded or reacted.<br><br><strong>Fix:</strong> Over time, reference electrodes degrade, especially if exposed to wrong chemicals. You need to re-chloridize the wire or buy a new Reference Electrode." }
  };

  function renderNode(nodeId) {
    const qText = document.getElementById('q-text');
    const optionsBox = document.getElementById('options-box');
    const resultBox = document.getElementById('wizard-result');
    const contentBox = document.getElementById('wizard-content');

    // If it's a result node
    if (nodeId.startsWith('res_')) {
      contentBox.style.display = 'none';
      resultBox.style.display = 'block';
      document.getElementById('res-title').innerHTML = resultsData[nodeId].title;
      document.getElementById('res-text').innerHTML = resultsData[nodeId].text;
      return;
    }

    // If it's a question node
    contentBox.style.display = 'block';
    resultBox.style.display = 'none';
    const node = wizardData[nodeId];
    qText.innerText = node.q;
    optionsBox.innerHTML = '';
    
    node.options.forEach(opt => {
      const btn = document.createElement('button');
      btn.className = 'wizard-btn';
      btn.innerText = opt.text;
      btn.onclick = () => renderNode(opt.next);
      optionsBox.appendChild(btn);
    });
  }

  function startWizard() {
    renderNode('start');
  }

  // Initialize
  startWizard();
</script>

<style>
  .noise-container { max-width: 650px; margin: 30px auto; background: #fff; border-radius: 8px; box-shadow: 0 4px 10px rgba(0,0,0,0.1); overflow: hidden; border: 1px solid #ddd; }
  .noise-tabs { display: flex; background: #f1f1f1; border-bottom: 2px solid #ccc; }
  .noise-tab { flex: 1; padding: 15px; text-align: center; cursor: pointer; font-weight: bold; color: #555; transition: 0.3s; border-bottom: 3px solid transparent; }
  .noise-tab:hover { background: #e9ecef; }
  .noise-tab.active { background: #fff; color: #d32f2f; border-bottom: 3px solid #d32f2f; }
  .noise-content { display: none; padding: 25px; text-align: center; }
  .noise-content.active { display: block; animation: fadeIn 0.4s; }
  .noise-svg { width: 100%; max-width: 400px; height: 120px; background: #fafafa; border: 1px solid #eee; margin-bottom: 15px; border-radius: 4px; }
  
  @keyframes fadeIn { from { opacity: 0; transform: translateY(5px); } to { opacity: 1; transform: translateY(0); } }
</style>

<div class="noise-container">
  <div class="noise-tabs">
    <div class="noise-tab active" onclick="openNoiseTab(event, 'jagged')">📈 The "Jagged" Line</div>
    <div class="noise-tab" onclick="openNoiseTab(event, 'decay')">📉 The Decaying Curve</div>
    <div class="noise-tab" onclick="openNoiseTab(event, 'flat')">➖ The Flat Line</div>
  </div>

  <!-- Tab 1: Jagged -->
  <div id="jagged" class="noise-content active">
    <svg class="noise-svg" viewBox="0 0 400 120">
      <polyline points="0,60 20,40 40,80 60,30 80,90 100,20 120,70 140,50 160,80 180,40 200,90 220,30 240,80 260,50 280,70 300,40 320,90 340,30 360,80 380,40 400,60" fill="none" stroke="#d32f2f" stroke-width="2"/>
    </svg>
    <h3 style="margin-top:0; color: #d32f2f;">Wild Fluctuations</h3>
    <p><strong>Diagnosis:</strong> Physical disruption in the circuit.</p>
    <p><strong>Physical Cause:</strong> Large CO₂ bubbles are forming and getting trapped on your Working Electrode, temporarily blocking the surface area before popping off. Alternatively, you have a loose alligator clip vibrating on the desk.</p>
    <p><strong>Fix:</strong> Increase the stirring speed, adjust electrode placement, or secure your cables with tape.</p>
  </div>

  <!-- Tab 2: Decaying -->
  <div id="decay" class="noise-content">
    <svg class="noise-svg" viewBox="0 0 400 120">
      <path d="M 0,20 Q 100,20 200,80 T 400,100" fill="none" stroke="#f57c00" stroke-width="3"/>
    </svg>
    <h3 style="margin-top:0; color: #f57c00;">Continuous Current Drop</h3>
    <p><strong>Diagnosis:</strong> Catalyst Deactivation.</p>
    <p><strong>Physical Cause:</strong> Your catalyst is dying. It might be getting poisoned by metal impurities in your electrolyte (like Iron or Zinc depositing on your Copper), or the surface is being covered by carbonaceous species.</p>
    <p><strong>Fix:</strong> Clean your electrolyte (use pre-electrolysis), use higher purity salts, or check if your catalyst is physically peeling off the substrate.</p>
  </div>

  <!-- Tab 3: Flat -->
  <div id="flat" class="noise-content">
    <svg class="noise-svg" viewBox="0 0 400 120">
      <line x1="0" y1="100" x2="400" y2="100" stroke="#1976d2" stroke-width="3"/>
    </svg>
    <h3 style="margin-top:0; color: #1976d2;">Absolutely Zero Current</h3>
    <p><strong>Diagnosis:</strong> Open Circuit.</p>
    <p><strong>Physical Cause:</strong> Electricity cannot flow. A cable is unplugged, the potentiostat output is turned off, or an electrode broke in half under the liquid.</p>
    <p><strong>Fix:</strong> Check all physical connections. Ensure the Potentiostat software actually says "Cell On".</p>
  </div>
</div>

<script>
  function openNoiseTab(evt, tabName) {
    var i, x, tablinks;
    x = document.getElementsByClassName("noise-content");
    for (i = 0; i < x.length; i++) { x[i].style.display = "none"; x[i].classList.remove("active"); }
    tablinks = document.getElementsByClassName("noise-tab");
    for (i = 0; i < x.length; i++) { tablinks[i].className = tablinks[i].className.replace(" active", ""); }
    document.getElementById(tabName).style.display = "block";
    document.getElementById(tabName).classList.add("active");
    evt.currentTarget.className += " active";
  }
</script>

---

## 1. The Diagnostic Philosophy
When an electrochemical experiment runs wild, it is rarely random: commonly associated with one or more uncontrolled factors. Successful troubleshooting depends on isolation and inspection of these variables.

The root of the problems often stems from these:
1.  **The Physics:** Is the electrical path complete?
2.  **The Chemistry:** Is the reaction environment proper?
3.  **The Analysis:** Is the math or calibration correct?

---

## 2. Category A: Electrical Anomalies
These issues pop up immediately upon starting the experiment and are generally related to charge movement.
### Issue: Incomplete Circuit
*   **Symptom:**
    The current remains only at 0.00 A or flucuate at noise level ($<1 \mu A$).
*   **Example of Potential Causes:**
    1.  Break or discontinuity in the wire path.
    2.  Connection of alligator clips to plastic insulation rather than metal.
    3.  Air bubble blocking the slat bridge or glass frit.
*   **Common Diagnosis:**
    Confirm the contunitity of the wire using device like ammeter or multimeter. If the wires are confirmed to connected, the issue may lie with an air bubble trapped inside a glass frit or a salt bridge acts. This bubble act as an electrical insulator, cutting of anode and cathode and rendering the circuit incomplete.
    
### Issue: High Impedance / Compliance Error
*   **Symptom:**
    The power supply or potentiostat hits its maximum voltage limit while not delivering the expected current.
*   **Potential Causes:**
    1.  Electrolyte concentration not appropriate, resulting in low conductivity.
    2.  Excessive distance between Working and Counter electrodes.
    3.  Membrane dehydration.
*   **Suggestion/Diagnosis:**
    This indicates High Cell Resistance (IR Drop). The electricity is struggling to push through the liquid. It is frequently observed when using ion-exchange membranes that were not properly soaked in water or activated before usage, as dry membranes are highly resistive.

---

## 3. Category B: Electrochemical Performance
The chemical reaction is not behaving as predicted.

![Stability Troubleshooting](./assets/images/stability_troubleshooting.png)
*Figure : Diagnostic Stability Plots. Green = Healthy. Orange = Poisoned (decaying). Red = Noise (bubbles/loose wire).*

### Issue: Catalyst Deactivation
*   **Symptom:**
    The current starts high and promising, but then decays rapidly (e.g. dropping by 50% within the first 20 minutes) without stabilizing.
*   **Potential Causes:**
    1.  Adsorption of impurities (Poisoning).
    2.  Surface oxidation.
    3.  Bubble accumulation masking the surface.
*   **Suggestion/Diagnosis:**
    Most often, this indicates electrolyte contamination. Trace organic compounds from plastic tubing or unwashed glassware may clog the active sites of the catalyst. If the decay is erratic, gas bubbles may be sticking to the electrode surface, thereby, blocking the liquid from touching the metal.

![Pourbaix Diagram](./assets/images/pourbaix_diagram.png)
*Figure : Simplified Pourbaix Diagram for Copper. To prevent your electrode from dissolving (Corrosion), you must keep your voltage and pH in the yellow "Immunity" region.*

### Issue: Selectivity Loss
*   **Symptom:**
    The current is stable and high, but the Faradaic Efficiency shows low carbon-based fuels and high Hydrogen.
*   **Potential Causes:**
    1.  Trace metal contamination (Iron/Zinc/Nickel).
    2.  Depletion of local $CO_2$.
*   **Suggestion/Diagnosis:**
    This is frequently caused by Underpotential Deposition. If low-purity salts are used, trace amounts of Iron ($Fe$) can dissolve into the liquid and plate onto the Copper cathode. Since Iron is an excellent catalyst for Hydrogen evolution, the reaction could shifts to making Hydrogen, ignoring the $CO_2$.

### Issue: Signal Instability (Noise)
*   **Symptom:**
    The Current vs. Time plot appears jagged or oscillates rather than forming a smooth line.
*   **Potential Causes:**
    1.  Reference Electrode instability.
    2.  Hydrodynamic turbulence.
    3.  Loose connections.
*   **Suggestion/Diagnosis:**
    If the oscillation is rhythmic, it often suggests bubble dynamics: bubbles growing and detaching from the electrode surface, changing the effective surface area; this is actually normal and okay to continue. But, if the noise is random and sharp, it typically points to an air bubble trapped in the tip of the Reference Electrode, causing the potentiostat to lose its suppposedly constant reference voltage.

---

## 4. Category C: Physical & Mechanical Failures
Invalidation cause by failure in the H-Cell setup that alters the chemical environment.

### Issue: Electrolyte Crossover
*   **Symptom:**
    The liquid level in one chamber rises while the other drops over the course of experiment.
*   **Potential Causes:**
    1.  Tear in the membrane.
    2.  Osmotic pressure imbalance.
*   **Common Diagnosis:**
    If the membrane is intact, this is often a result of Osmotic Drag. If the concentration of ions is significantly different between the anode and cathode chambers, water might migrate through the membrane to balance the concentration, diluting the electrolyte and altering the pH.

### Issue: Gas Leak
*   **Symptom:**
    The Current is stable, but the Calculated Efficiency is anomally low (e.g. the sum of all products is only 30% instead of near 100%).
*   **Potential Causes:**
    1.  Worn-out rubber septa.
    2.  Loose fittings on the gas exhaust line.
    3.  Poor seal between the glass chambers and the clamp.
*   **Common Diagnosis:**
    If the electricity passed suggests you made 10 moles of gas, but you only collected 3 moles, the gas didn't disappearit, it leaked. A simple Soap Bubble Test often reveals leaks in the headspace.
