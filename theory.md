---
layout: guide
nav_id: theory
title: "CO2RR Theory: Foundations of CO2 Electroreduction"
description: "Core concepts for aqueous CO2 electroreduction: electrode potential, current, selectivity, catalysis, and mass transport."
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
<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
<script defer src="https://cdn.jsdelivr.net/npm/chart.js@4.5.1/dist/chart.umd.js"></script>

<style>
  .guide-page--theory mjx-container[display="true"] {
    max-width: 100%;
    overflow-x: auto;
    overflow-y: hidden;
    padding: 0.25rem 0;
  }
  .theory-figure {
    margin: 2rem 0;
    padding: 1.25rem;
    border: 1px solid #cbd5e1;
    border-radius: 8px;
    background: #f8fafc;
  }
  .theory-figure h4 { margin: 0 0 1rem; color: #1e3a8a; }
  .theory-figure figcaption { margin-top: 1rem; font-size: 0.9rem; }
  .theory-figure .chart-wrapper { position: relative; height: 320px; min-width: 0; }
  .theory-figure .widget-controls {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    gap: 0.75rem;
    margin: 1rem 0;
  }
  .theory-figure button {
    min-height: 44px;
    padding: 0.5rem 0.8rem;
    border: 2px solid #1e40af;
    border-radius: 6px;
    background: #fff;
    color: #1e40af;
    font: inherit;
    cursor: pointer;
  }
  .theory-figure button:hover { background: #eff6ff; }
  .theory-figure button[aria-pressed="true"] { background: #1e40af; color: #fff; }
  .theory-figure button:disabled { border-color: #64748b; color: #475569; cursor: default; }
  .theory-figure button:focus-visible,
  .theory-figure input:focus-visible { outline: 3px solid #1e40af; outline-offset: 3px; }
  .theory-figure .widget-feedback { padding: 1rem; border-left: 4px solid #1e40af; background: #fff; }
  .product-map,
  .catalyst-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(min(100%, 150px), 1fr));
    gap: 0.75rem;
    padding: 0;
    margin: 1rem 0;
    list-style: none;
  }
  .product-map li,
  .catalyst-card { padding: 0.9rem; border: 1px solid #94a3b8; border-radius: 6px; background: #fff; }
  .product-map strong,
  .catalyst-card strong { display: block; color: #1e3a8a; }
  .product-map span,
  .catalyst-card span { display: block; margin-top: 0.4rem; font-size: 0.9rem; }
  .catalyst-card.is-highlighted { border: 3px solid #1e40af; padding: calc(0.9rem - 2px); background: #eff6ff; }
  #binding-slider { width: 100%; min-height: 44px; accent-color: #1e40af; }
  .binding-labels { display: flex; justify-content: space-between; gap: 0.5rem; font-size: 0.9rem; }
  #animation-box { height: 160px; position: relative; overflow: hidden; background: #e0f2fe; margin: 1rem 0; }
  .catalyst-surface {
    position: absolute;
    bottom: 0;
    width: 100%;
    height: 40px;
    background: #475569;
    color: #fff;
    text-align: center;
    line-height: 40px;
    font-size: 0.9rem;
  }
  .co-molecule {
    position: absolute;
    width: 40px;
    height: 40px;
    border-radius: 50%;
    background: #1e40af;
    color: #fff;
    text-align: center;
    line-height: 40px;
    transition: top 0.4s, left 0.4s, opacity 0.4s;
  }
  #step-counter { flex: 1 1 6rem; text-align: center; }
  @media (max-width: 30rem) {
    .theory-figure { padding: 0.75rem; }
    .theory-figure .chart-wrapper { height: 300px; }
    .theory-figure .widget-controls button { flex: 1 1 8rem; }
    #step-counter { flex-basis: 100%; order: -1; }
  }
  @media (prefers-reduced-motion: reduce) {
    .theory-figure * { transition: none !important; }
  }
</style>

<div id="foundations--theory"></div>

This chapter introduces the concepts needed to understand aqueous CO₂ electroreduction experiments: electrode potential, current, product selectivity, catalysis, and reactant transport. It assumes basic chemistry and introduces research-specific terminology as it appears. The examples focus on aqueous H-cells. Practical experimental work requires laboratory supervision and validated procedures appropriate to the equipment and materials.

{% include page-toc.html %}

<div id="1-the-big-picture"></div>

## 1. What CO₂ electroreduction produces
{: #products}

Electrochemical CO₂ reduction, abbreviated **CO₂RR**, uses electrical energy to convert CO₂ into products such as carbon monoxide, formate, hydrocarbons, and oxygenated compounds. Reduction involves electron transfer to the reacting species. In aqueous systems, water or other proton donors also participate in forming many products. Comparisons with reversed combustion provide a broad energy-storage analogy; the actual reaction pathways depend on the catalyst, potential, electrolyte, and CO₂ supply.

**Hydrocarbons** contain carbon and hydrogen, as in methane and ethylene. **Oxygenated products** also contain oxygen, as in ethanol and formate. Different products require different numbers of electrons, which becomes important when calculating Faradaic efficiency.

<figure class="theory-figure" aria-labelledby="product-map-title">
  <h4 id="product-map-title">Representative products from CO₂</h4>
  <p>Starting reactant: CO₂. These are alternative products, not successive stages.</p>
  <ul class="product-map">
    <li><strong>CO: carbon monoxide</strong><span>2 electrons per molecule</span><span>Typically measured in outlet gas; a chemical feedstock.</span></li>
    <li><strong>HCOO⁻: formate</strong><span>2 electrons per ion</span><span>Typically measured as a dissolved ion in the electrolyte.</span></li>
    <li><strong>CH₄: methane</strong><span>8 electrons per molecule</span><span>Typically measured in outlet gas; a hydrocarbon.</span></li>
    <li><strong>C₂H₄: ethylene</strong><span>12 electrons per molecule</span><span>Typically measured in outlet gas; a hydrocarbon.</span></li>
    <li><strong>C₂H₅OH: ethanol</strong><span>12 electrons per molecule</span><span>Typically measured as a dissolved product; an oxygenated compound.</span></li>
  </ul>
  <figcaption>Representative CO₂RR products. Electron requirements are given per product molecule or ion. Each C₂ product consumes two CO₂ molecules. This map shows possible products and does not represent a universal sequence of reaction intermediates. Phase descriptions indicate typical analysis locations; recovery can also be affected by dissolution, volatility, and crossover.</figcaption>
</figure>

<div id="2-basic-electrochemistry"></div>

## 2. The electrochemical cell and interface
{: #electrochemical-cell}

An **electrolytic cell** uses an external power source to drive electrochemical reactions. Reduction occurs at the cathode, and oxidation occurs at the anode. Electrons move through the electrodes and external circuit, while ions carry current through the electrolyte. In many aqueous CO₂RR experiments, CO₂ reduction and hydrogen evolution occur at the cathode, and water oxidation produces oxygen at the anode. Depending on the cathodic reaction, the products may be gases or dissolved species.

### 2.1 Cathode, anode, and charge transport
{: #electrodes-and-charge-transport}

<div id="the-cathode-the-reduction-site"></div>

At the **cathode**, reactants exchange electrons with the electrode at the electrode–electrolyte interface. Dissolved, electrically neutral CO₂ reaches this region mainly through diffusion and convection. **Diffusion** transports molecules down a concentration gradient; **convection** transports them with moving liquid. The catalyst surface, applied potential, electrolyte, and local reactant concentrations together influence the reaction rate and product distribution.

<div id="the-anode-the-oxidation-site"></div>

At the **anode**, oxidation releases electrons into the external circuit. Oxygen evolution is a common anodic reaction in aqueous CO₂RR, although other anodic reactions are possible. An H-cell usually separates the electrode compartments while maintaining an ionic connection. A membrane can limit mixing, but gas and product crossover may still occur.

For CO formation coupled to oxygen evolution, acidic bookkeeping gives:

$$\mathrm{CO_2 + 2H^+ + 2e^- \rightarrow CO + H_2O}$$

$$\mathrm{2H_2O \rightarrow O_2 + 4H^+ + 4e^-}$$

Corresponding neutral/alkaline forms are:

$$\mathrm{CO_2 + H_2O + 2e^- \rightarrow CO + 2OH^-}$$

$$\mathrm{4OH^- \rightarrow O_2 + 2H_2O + 4e^-}$$

These equations use different bookkeeping forms for different electrolyte conditions. They represent net reactions and do not specify an elementary reaction mechanism. Combining CO formation with oxygen evolution gives this balanced net example, driven by electrical energy:

$$\mathrm{2CO_2 \rightarrow 2CO + O_2}$$

### 2.2 Three-electrode measurement
{: #three-electrode-measurement}

A **potentiostat** controls the working-electrode potential relative to a reference electrode while current flows between the working and counter electrodes. During CO₂RR, the **working electrode** normally acts as the cathode and the **counter electrode** supports oxidation. The **reference electrode** ideally carries negligible current and provides a stable potential reference. The working-electrode potential and the voltage across the complete cell are different measurements.

The **electrochemical interface** is the region where the electrode and electrolyte meet. Surface charge, nearby ions, and solvent molecules form an interfacial arrangement often called the electric double layer. This local environment influences reactions and can differ from the bulk solution.

See [the hardware setup]({{ '/experiment.html' | relative_url }}#2-the-hardware-setup) for the experimental components.

<div id="41-understanding-measurements-and-variable"></div>
<div id="potential-voltage"></div>

## 3. Electrode potential, thermodynamics, and kinetics
{: #electrode-potential}

Electrode potential expresses electrical energy per unit charge relative to a stated reference: one volt is one joule per coulomb. It describes the electrical conditions at an electrode. To interpret a potential, first identify the reference scale and the relevant chemical conditions.

### 3.1 Reference scales and conversions
{: #reference-scales}

The **standard hydrogen electrode (SHE)** provides a conventional reference scale. The **reversible hydrogen electrode (RHE)** references the hydrogen reaction at the solution pH. Converting a measurement from another reference electrode to RHE requires that electrode's potential relative to SHE and the solution pH at the stated temperature. For Ag/AgCl electrodes, the conversion also depends on the filling solution.

At 25 °C, with hydrogen at its standard pressure:

$$E_{\mathrm{vs\,RHE}} = E_{\mathrm{vs\,ref}} + E_{\mathrm{ref\,vs\,SHE}} + (0.05916\,\mathrm{V})\,\mathrm{pH}$$

Report the temperature, reference electrode and filling solution, and pH used for conversion. The coefficient changes with temperature. A conversion based on bulk pH does not establish the pH immediately next to an operating electrode.

### 3.2 Equilibrium and applied potential
{: #equilibrium-and-applied-potential}

An **equilibrium potential** describes the thermodynamic balance of a specified reaction under specified conditions, including temperature and chemical activities. Activity is an effective concentration used to describe chemical behavior. The **applied potential** is the potential imposed experimentally. An observable reaction onset also depends on kinetics, transport, background current, and the measurement threshold. Every reported potential should identify its reference scale and relevant experimental conditions.

Different product reactions have different equilibrium potentials. A single numerical potential cannot describe the onset of all CO₂RR pathways.

<div id="42-thermodynamics-and-kinetics"></div>
<div id="the-stability-problem"></div>
<div id="the-energy-barrier"></div>

### 3.3 Thermodynamics and activation barriers
{: #thermodynamics-and-kinetics}

A reaction can be thermodynamically favorable and still proceed slowly. Its rate depends on **activation barriers** for processes such as electron transfer, proton transfer, and intermediate conversion. A transition state is a high-energy configuration crossed during a reaction step; an intermediate is a species formed between steps. An activation barrier is measured from the preceding state to the transition state, not simply from an arbitrary zero of energy.

For the same net reaction and chemical conditions, a catalyst changes the reaction pathway and barriers without changing the overall equilibrium free-energy difference. **Free-energy changes** describe the thermodynamic driving force under specified conditions; they are distinct from kinetic barriers.

<figure class="theory-figure" aria-labelledby="energy-title">
  <h4 id="energy-title">Reaction free energy and activation barriers</h4>
  <p id="energy-summary">Both illustrative pathways start and end at the same free energies. Each transition state lies above the preceding state, and the lower-barrier pathway has smaller rises. Use the stepper to reveal reactants, a transition state, an intermediate, a second transition state, and products.</p>
  <div class="chart-wrapper"><canvas id="energyChart" role="img" aria-labelledby="energy-title" aria-describedby="energy-summary energy-caption">A schematic of two pathways with identical endpoints and different activation barriers.</canvas></div>
  <div class="widget-controls">
    <button type="button" id="btn-prev" disabled>Previous step</button>
    <span id="step-counter">Step 0 of 4</span>
    <button type="button" id="btn-next">Next step</button>
  </div>
  <p id="step-explanation" class="widget-feedback" role="status" aria-live="polite" aria-atomic="true">Reactants: both pathways begin at the same free energy under the specified conditions. Advancing the stepper reveals an explanation, not a simulated experiment.</p>
  <figcaption id="energy-caption">Schematic pathways for the same net reaction under fixed conditions. Both pathways have the same overall free-energy change, but different activation barriers. Heights and shapes are illustrative; they are not calculated CO₂RR energies.</figcaption>
</figure>

<div id="overpotential"></div>

### 3.4 Overpotential and uncompensated resistance
{: #overpotential-and-resistance}

The **overpotential** is the difference between the interfacial electrode potential and the equilibrium potential of the specified reaction on the same reference scale:

$$\eta_p = E_{\mathrm{interface}} - E_{\mathrm{eq},p}$$

Here $p$ identifies the product reaction. Under the signed convention used here, cathodic overpotential is negative. Publications may instead report its magnitude. Catalyst comparisons should specify the target product, product formation rate, selectivity, and experimental conditions. High total current alone does not demonstrate effective production of the desired product.

Resistance between the working electrode and the reference-electrode sensing location causes an ohmic potential drop. Consequently, the measured potential can differ from the potential experienced at the reacting interface. With anodic current positive and cathodic current negative, a lumped-resistance correction is:

$$E_{\mathrm{interface}} \approx E_{\mathrm{measured}} - I R_u$$

Here $I$ is signed current in amperes and $R_u$ is uncompensated resistance in ohms. For negative current, the correction makes the interfacial potential less negative than the uncorrected measured potential. Report the resistance and how compensation or correction was applied; do not correct an already compensated value twice. Overpotential and ohmic loss are different contributions.

<div id="5-selectivity-and-the-competing-reaction"></div>

## 4. Current, charge, and product selectivity
{: #current-and-selectivity}

Potential establishes electrical conditions; current describes charge flow. Product measurements establish how much of that charge is associated with each reaction.

<div id="current-amperage"></div>

### 4.1 Current sign and accumulated charge
{: #current-and-charge}

**Current** is the rate of charge flow. Measured current can include charge transferred in chemical reactions, called Faradaic current, and transient charging of the electrode interface. Its magnitude therefore describes total charge flow, while the formation rate of an individual product requires product-specific information. In this chapter, anodic current is positive and cathodic current is negative; some instruments and publications use different plotting conventions.

**Charge** is obtained by integrating current over the measurement interval. For an interval that remains cathodic under this sign convention, define a positive charge magnitude:

$$Q_c = -\int_{t_0}^{t_1} I(t)\,dt$$

Here $t_0$ and $t_1$ are the start and end times. Current in amperes integrated over seconds gives charge in coulombs. For constant cathodic current, $Q_c = \lvert I\rvert(t_1-t_0)$. An absolute-current integral should not be applied indiscriminately to measurements containing both anodic and cathodic periods.

<div id="surface-area-and-normalization"></div>

### 4.2 Geometric current density
{: #current-density}

**Geometric current density** is current divided by the exposed geometric electrode area:

$$j_{\mathrm{geo}} = \frac{I}{A_{\mathrm{geo}}}$$

It helps compare electrodes of different sizes, but it also depends on roughness, wetting, transport, and experimental conditions. State the area definition and whether signed current density or its magnitude is plotted. Normalization by electrochemically active surface area answers a different question and requires an appropriate area measurement.

<div id="the-hydrogen-problem"></div>

### 4.3 Competing hydrogen evolution
{: #hydrogen-evolution}

**Hydrogen evolution (HER)** competes with CO₂RR in aqueous electrolytes. In acidic conditions, protons can be reduced to H₂:

$$\mathrm{2H^+ + 2e^- \rightarrow H_2}$$

In neutral or alkaline conditions, water can supply hydrogen:

$$\mathrm{2H_2O + 2e^- \rightarrow H_2 + 2OH^-}$$

The competing rates depend on the catalyst, electrode potential, and local chemical environment, including available proton donors. Hydrogen formation lowers the charge fraction assigned to a chosen CO₂RR product, although hydrogen may itself be useful in other applications.

<div id="selectivity-faradaic-efficiency"></div>

### 4.4 Faradaic efficiency and partial current
{: #faradaic-efficiency}

**Faradaic efficiency (FE)** is the fraction of measured charge associated with formation of a specified product over a specified interval:

$$\mathrm{FE}_p(\%) = 100\,\frac{z_p F N_p}{Q_c}$$

Here $N_p$ is the number of moles of product formed over the interval, $z_p$ is the number of electrons required per product molecule or ion, and $F$ is the Faraday constant, approximately 96,485 C mol⁻¹. The electron requirements are 2 for CO and formate, 8 for methane, and 12 for ethylene and ethanol.

For example, an FE for CO of 50% means that half of the charge is assigned to CO formation; the remaining charge may form hydrogen or other products. Zero FE for CO does not imply that all charge forms hydrogen. FE expresses **charge-based selectivity**. It does not directly describe product purity, the mole fraction in a product mixture, or energy efficiency, which also depends on the electrical energy consumed.

The average **partial current** associated with product $p$ is:

$$|\overline{I}_p| = \frac{z_p F N_p}{t_1-t_0}$$

$$|\overline{I}_p| = \frac{\mathrm{FE}_p}{100}\,|\overline{I}|$$

These relationships use the same interval for product amount, charge, and average current. Gas and liquid product measurements must cover compatible intervals. Charging/background contributions, dissolved or crossed-over products, and incomplete recovery can affect interpretation of the charge balance. If all Faradaic products are quantified and other contributions are negligible, their FEs should sum to approximately 100%.

**Worked example — hypothetical inputs:** A constant current of −10 mA for 100 s gives $Q_c=1$ C. If the FE for CO is 60%, 0.6 C is assigned to CO formation. With two electrons per CO molecule, this corresponds to approximately 3.11 µmol of CO and an average partial-current magnitude of 6 mA. These values illustrate the calculation and are not experimental measurements.

See [electrical measurements]({{ '/analysis.html' | relative_url }}#3-electrical-data) and [performance calculations]({{ '/analysis.html' | relative_url }}#5-calculating-performance) for how these quantities are used.

<div id="3-the-core-idea"></div>

## 5. Catalysts and reaction pathways
{: #catalysts-and-pathways}

Converting CO₂ to useful products involves competing reaction steps. A catalyst changes how readily those steps occur; its effect must be considered together with potential, electrolyte, and transport.

<div id="what-the-catalyst-does"></div>

### 5.1 Adsorption and intermediates
{: #adsorption-and-intermediates}

Catalysis occurs at the electrode–electrolyte interface, where the surface can stabilize reactants and reaction intermediates. **Adsorption** means binding to the surface; **desorption** means leaving it. An asterisk denotes an adsorbed species, so \*CO means CO bound to the surface. Representative pathways to CO can involve \*COOH and \*CO, while pathways to other products involve different intermediates and competing steps. The preferred pathway depends on the catalyst and reaction conditions.

<div id="6-catalyst-materials"></div>
<div id="group-1-hydrogen-producers"></div>
<div id="group-2-two-electron-pathway-co--formate"></div>
<div id="group-3-hydrocarbon-pathway"></div>

### 5.2 Representative catalyst families
{: #catalyst-families}

Representative metal catalysts show different product preferences under aqueous CO₂RR conditions. Gold and silver are commonly studied for CO production, while tin, indium, and bismuth are commonly studied for formate production. Platinum and nickel often favor hydrogen evolution in these conditions. These examples describe characteristic behavior rather than fixed classifications: potential, surface structure, electrolyte, and local conditions can change the observed product distribution.

Among commonly studied monometallic electrodes, copper is notable for producing both hydrocarbons and oxygenated products from CO₂. Examples include methane, ethylene, and ethanol. **C₂+** denotes products containing two or more carbon atoms. Their formation can involve reactions between adsorbed CO-derived intermediates. Copper's product distribution is sensitive to its surface and operating environment, so these pathways should be presented as copper-specific examples.

<figure class="theory-figure" aria-labelledby="catalyst-title">
  <h4 id="catalyst-title">Representative metal catalysts in aqueous CO₂RR</h4>
  <p>Highlight a group to compare the examples. All cards remain visible, and the labels state their characteristic behavior.</p>
  <div class="widget-controls" role="group" aria-label="Highlight catalyst examples">
    <button type="button" data-catalyst-group="co" aria-pressed="false">CO examples</button>
    <button type="button" data-catalyst-group="formate" aria-pressed="false">Formate examples</button>
    <button type="button" data-catalyst-group="copper" aria-pressed="false">Copper products</button>
    <button type="button" data-catalyst-group="her" aria-pressed="false">HER examples</button>
    <button type="button" data-catalyst-group="all" aria-pressed="true">Show all</button>
  </div>
  <p id="catalyst-status" role="status" aria-live="polite" aria-atomic="true">All eight examples are shown.</p>
  <ul class="catalyst-grid" id="ptable">
    <li class="catalyst-card" data-group="co"><strong>Au: gold</strong><span>CO production</span></li>
    <li class="catalyst-card" data-group="co"><strong>Ag: silver</strong><span>CO production</span></li>
    <li class="catalyst-card" data-group="formate"><strong>Sn: tin</strong><span>Formate production</span></li>
    <li class="catalyst-card" data-group="formate"><strong>In: indium</strong><span>Formate production</span></li>
    <li class="catalyst-card" data-group="formate"><strong>Bi: bismuth</strong><span>Formate production</span></li>
    <li class="catalyst-card" data-group="copper"><strong>Cu: copper</strong><span>Hydrocarbons and oxygenated products; a condition-dependent mixture</span></li>
    <li class="catalyst-card" data-group="her"><strong>Pt: platinum</strong><span>Often favors hydrogen evolution</span></li>
    <li class="catalyst-card" data-group="her"><strong>Ni: nickel</strong><span>Often favors hydrogen evolution</span></li>
  </ul>
  <figcaption>Selected examples of characteristic behavior in aqueous CO₂RR. Product preferences depend on surface structure and operating conditions; these categories are not fixed properties of the elements.</figcaption>
</figure>

<div id="the-goldilocks-zone"></div>

### 5.3 What binding strength can explain
{: #binding-strength}

Adsorption strength can influence surface coverage, intermediate conversion, and product release. For CO production, forming CO and allowing it to desorb are useful outcomes. Further conversion on copper can require retention of CO-derived intermediates and subsequent reaction steps. Strongly adsorbed species can block sites under some conditions. A single CO-binding descriptor cannot determine the optimum catalyst for every CO₂RR product.

Adsorption-energy conventions must be checked before reading a numerical plot. For the common definition that subtracts the energies of the separate surface and adsorbate from the combined system, more negative values mean stronger adsorption. The schematic below instead uses an explicitly qualitative weak-to-strong direction and assigns no energies to metals.

<figure class="theory-figure" aria-labelledby="adsorption-title">
  <h4 id="adsorption-title">A conceptual relationship between adsorption and reaction rate</h4>
  <p id="adsorption-summary">For a chosen reaction, weak adsorption may limit intermediate formation, whereas strong adsorption may limit further reaction or release. The schematic has an intermediate maximum. Select a region for its explanation.</p>
  <div class="chart-wrapper"><canvas id="volcanoPlot" role="img" aria-labelledby="adsorption-title" aria-describedby="adsorption-summary adsorption-caption">A qualitative curve rising from weak adsorption to an intermediate maximum and falling toward strong adsorption.</canvas></div>
  <div class="widget-controls" role="group" aria-label="Select an adsorption region">
    <button type="button" data-adsorption-region="0" aria-pressed="false">Weak adsorption</button>
    <button type="button" data-adsorption-region="1" aria-pressed="true">Intermediate adsorption</button>
    <button type="button" data-adsorption-region="2" aria-pressed="false">Strong adsorption</button>
  </div>
  <p id="adsorption-description" class="widget-feedback" role="status" aria-live="polite" aria-atomic="true">Intermediate adsorption: formation and subsequent reaction or release can be balanced for a particular reaction. Its optimum depends on the target reaction and conditions.</p>
  <figcaption id="adsorption-caption">Some catalytic reactions exhibit a trade-off between intermediate formation and subsequent reaction or release. This schematic illustrates that idea without ranking CO₂RR catalysts. The shape and optimum depend on the target reaction and conditions; CO adsorption alone does not predict product selectivity.</figcaption>
</figure>

<figure class="theory-figure" aria-labelledby="binding-title">
  <h4 id="binding-title">How adsorption can affect a surface reaction</h4>
  <label for="binding-slider">Select a schematic adsorption regime</label>
  <input type="range" id="binding-slider" min="1" max="3" step="1" value="2" aria-valuetext="Intermediate" aria-describedby="binding-caption">
  <div class="binding-labels"><span>Weak</span><span>Intermediate</span><span>Strong</span></div>
  <div id="animation-box" aria-hidden="true">
    <div class="catalyst-surface">Catalyst surface</div>
    <div class="co-molecule" id="co-molecule-1" style="top: 80px; left: 45%;">*CO</div>
    <div class="co-molecule" id="co-molecule-2" style="top: 80px; left: 55%; opacity: 0;">*CO</div>
  </div>
  <p id="slider-description" class="widget-feedback" role="status" aria-live="polite" aria-atomic="true">Intermediate adsorption: retained intermediates can undergo further reactions when suitable pathways are available. On copper, CO-derived intermediates can participate in formation of more reduced and multicarbon products.</p>
  <figcaption id="binding-caption">Qualitative adsorption regimes. The control does not predict a catalyst's binding energy, activity, or products. The animation only indicates release or retention of CO-derived species.</figcaption>
</figure>

<div id="7-the-physical-limit"></div>

## 6. CO₂ supply and the local reaction environment
{: #local-environment}

### 6.1 Dissolution and mass transport
{: #co2-supply}

In an aqueous H-cell, CO₂ must dissolve and reach the electrode interface before it can react. The equilibrium concentration of dissolved CO₂ depends on temperature, CO₂ partial pressure, and electrolyte composition. Diffusion and convection replenish CO₂ consumed near the electrode. Bubbling replenishes the bulk solution, but the interfacial concentration can still decrease when consumption outpaces supply. This **mass-transport limitation** can reduce CO₂RR rates and change the balance between CO₂RR and hydrogen evolution.

Gas-diffusion electrodes and flow cells provide other ways to deliver reactants, but their operation is outside this H-cell introduction. See [further reading on these configurations]({{ '/resources.html' | relative_url }}#4-scaling-up-flow-cells--gdes).

### 6.2 Local pH, buffering, and carbonate species
{: #local-ph}

The chemical environment immediately next to the electrode can differ from the bulk electrolyte. Cathodic reactions often increase local pH, while buffering and transport oppose these changes. A **buffer** resists pH changes through acid–base reactions, but its capacity and transport are finite.

CO₂ also participates in acid–base equilibria with bicarbonate and carbonate. Consequently, **total dissolved inorganic carbon** and **molecular CO₂ concentration** are different quantities. Changes in local pH, reactant availability, and electrolyte composition can affect both reaction rates and selectivity. A bulk pH measurement alone does not describe the operating interface.

## 7. Connecting theory to a first H-cell experiment
{: #preparing-for-an-experiment}

Before planning an H-cell experiment, identify the target products, potential reference, current convention, electrode area definition, CO₂ supply, and product-analysis methods. The key distinctions are:

- Electrode potential establishes electrical conditions relative to a reference; full-cell voltage is a separate measurement.
- Total current measures charge flow; partial current describes an individual product's formation rate.
- FE is product-specific charge selectivity; energy efficiency also depends on energy input.
- Catalyst behavior depends on the target reaction and operating environment.
- Bulk CO₂ supply and pH do not completely describe the reacting interface.

The [Experiment chapter]({{ '/experiment.html' | relative_url }}) explains cell components and preparation considerations, including [safety and operational hazards]({{ '/experiment.html' | relative_url }}#safety--operational-hazards). The [Analysis chapter]({{ '/analysis.html' | relative_url }}) connects electrical measurements and quantified products to performance metrics. Use supervised, validated laboratory procedures when moving from this conceptual preparation to practical work.

For deeper study, Resources contains [fundamentals and reviews]({{ '/resources.html' | relative_url }}#1-the-essentials-fundamentals--reviews), [measurement methodology]({{ '/resources.html' | relative_url }}#2-how-to-measure-methodology-standards--reference), and [catalyst examples]({{ '/resources.html' | relative_url }}#3-catalyst-library-materials--design-strategies).

<script>
document.addEventListener('DOMContentLoaded', function () {
  const reduceMotion = window.matchMedia('(prefers-reduced-motion: reduce)').matches;
  const adsorptionStates = [
    'Weak adsorption: intermediate formation can be limited if relevant species do not bind sufficiently for the chosen reaction.',
    'Intermediate adsorption: formation and subsequent reaction or release can be balanced for a particular reaction. Its optimum depends on the target reaction and conditions.',
    'Strong adsorption: retained intermediates can occupy sites or be difficult to convert or release, limiting turnover for the chosen reaction.'
  ];
  const energyStates = [
    'Reactants: both pathways begin at the same free energy under the specified conditions. Advancing the stepper reveals an explanation, not a simulated experiment.',
    'First transition state: the activation barrier is the rise from the reactants to this high-energy configuration. The lower-barrier pathway has a smaller rise.',
    'Intermediate: this state lies between reaction steps. Its free energy is not itself an activation barrier.',
    'Second transition state: this barrier is measured from the intermediate, not from the initial reactants or an arbitrary zero.',
    'Products: both pathways end at the same free energy. The overall reaction free-energy change is identical, while the activation barriers differ.'
  ];
  let volcanoChart;
  let energyChart;
  let currentStep = 0;

  // These dimensionless coordinates only draw schematic shapes. They are not
  // measured rates, adsorption energies, simulated data, or calculated energies.
  const higherBarriers = [2, 6, 1.5, 5, 0];
  const lowerBarriers = [2, 4, 1.5, 3, 0];

  if (typeof Chart !== 'undefined') {
    volcanoChart = new Chart(document.getElementById('volcanoPlot'), {
      type: 'line',
      data: {
        labels: ['Weak', 'Intermediate', 'Strong'],
        datasets: [{ data: [1, 3, 1], borderColor: '#1e40af', backgroundColor: '#1e40af', pointRadius: [6, 9, 6], tension: 0.25 }]
      },
      options: {
        responsive: true,
        maintainAspectRatio: false,
        animation: reduceMotion ? false : { duration: 250 },
        plugins: {
          legend: { display: false },
          tooltip: { callbacks: { label: context => adsorptionStates[context.dataIndex] } }
        },
        scales: {
          x: { title: { display: true, text: 'Adsorption strength — schematic' }, ticks: { autoSkip: false, maxRotation: 0, font: { size: 11 } } },
          y: { min: 0, max: 3.5, ticks: { display: false }, title: { display: true, text: ['Rate of a chosen reaction', '— schematic'] } }
        }
      }
    });
    energyChart = new Chart(document.getElementById('energyChart'), {
      type: 'line',
      data: {
        labels: ['Reactants', ['Transition', 'state 1'], 'Intermediate', ['Transition', 'state 2'], 'Products'],
        datasets: [
          { label: 'Higher barriers', data: [higherBarriers[0], null, null, null, null], borderColor: '#92400e', backgroundColor: '#92400e', borderDash: [6, 4], pointStyle: 'triangle', pointRadius: 5, tension: 0.15 },
          { label: 'Lower barriers', data: [lowerBarriers[0], null, null, null, null], borderColor: '#1e40af', backgroundColor: '#1e40af', pointRadius: 5, tension: 0.15 }
        ]
      },
      options: {
        responsive: true,
        maintainAspectRatio: false,
        animation: reduceMotion ? false : { duration: 250 },
        plugins: { tooltip: { enabled: false }, legend: { labels: { usePointStyle: true } } },
        scales: {
          x: { title: { display: true, text: 'Reaction progress — schematic' }, ticks: { autoSkip: false, maxRotation: 0, font: { size: 10 } } },
          y: { min: -0.5, max: 6.5, ticks: { display: false }, title: { display: true, text: ['Relative free energy', '— schematic'] } }
        }
      }
    });
  }

  document.querySelectorAll('[data-adsorption-region]').forEach(button => {
    button.addEventListener('click', function () {
      const selected = Number(button.dataset.adsorptionRegion);
      document.querySelectorAll('[data-adsorption-region]').forEach(control => {
        control.setAttribute('aria-pressed', String(Number(control.dataset.adsorptionRegion) === selected));
      });
      document.getElementById('adsorption-description').textContent = adsorptionStates[selected];
      if (volcanoChart) {
        volcanoChart.data.datasets[0].pointRadius = adsorptionStates.map((_, index) => index === selected ? 9 : 6);
        volcanoChart.update();
      }
    });
  });

  function changeStep(direction) {
    currentStep = Math.max(0, Math.min(4, currentStep + direction));
    document.getElementById('btn-prev').disabled = currentStep === 0;
    document.getElementById('btn-next').disabled = currentStep === 4;
    document.getElementById('step-counter').textContent = 'Step ' + currentStep + ' of 4';
    document.getElementById('step-explanation').textContent = energyStates[currentStep];
    if (energyChart) {
      energyChart.data.datasets[0].data = higherBarriers.map((value, index) => index <= currentStep ? value : null);
      energyChart.data.datasets[1].data = lowerBarriers.map((value, index) => index <= currentStep ? value : null);
      energyChart.update();
    }
  }
  document.getElementById('btn-prev').addEventListener('click', () => changeStep(-1));
  document.getElementById('btn-next').addEventListener('click', () => changeStep(1));

  const bindingStates = [
    { name: 'Weak', text: 'Weak adsorption: if CO forms but desorbs readily, it may leave as a product. Weak adsorption can also limit other surface steps, depending on the reaction.' },
    { name: 'Intermediate', text: 'Intermediate adsorption: retained intermediates can undergo further reactions when suitable pathways are available. On copper, CO-derived intermediates can participate in formation of more reduced and multicarbon products.' },
    { name: 'Strong', text: 'Strong adsorption: strongly adsorbed species can occupy sites and slow turnover. The resulting activity and product distribution depend on the surface and reaction conditions.' }
  ];
  const slider = document.getElementById('binding-slider');
  function updateBinding() {
    const selected = Number(slider.value) - 1;
    const state = bindingStates[selected];
    slider.setAttribute('aria-valuetext', state.name);
    document.getElementById('slider-description').textContent = state.text;
    const first = document.getElementById('co-molecule-1');
    const second = document.getElementById('co-molecule-2');
    first.textContent = selected === 0 ? 'CO' : '*CO';
    first.style.top = selected === 0 ? '20px' : '80px';
    first.style.left = selected === 0 ? '70%' : selected === 1 ? '45%' : '35%';
    second.style.opacity = selected === 2 ? '1' : '0';
  }
  slider.addEventListener('input', updateBinding);
  updateBinding();

  document.querySelectorAll('[data-catalyst-group]').forEach(button => {
    button.addEventListener('click', function () {
      const group = button.dataset.catalystGroup;
      const selectedNames = [];
      document.querySelectorAll('[data-catalyst-group]').forEach(control => {
        control.setAttribute('aria-pressed', String(control.dataset.catalystGroup === group));
      });
      document.querySelectorAll('.catalyst-card').forEach(card => {
        const selected = group !== 'all' && card.dataset.group === group;
        card.classList.toggle('is-highlighted', selected);
        if (selected) selectedNames.push(card.querySelector('strong').textContent);
      });
      document.getElementById('catalyst-status').textContent = group === 'all'
        ? 'All eight examples are shown.'
        : 'Highlighted: ' + selectedNames.join('; ') + '. All other examples remain visible.';
    });
  });
});
</script>
