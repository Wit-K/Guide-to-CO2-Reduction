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

# Data Collection, Analysis & Interpretation
*Part 3: From Raw Data to Chemical Insight*

---

## 1. The Three Pillars of Analysis
To evaluate the success of a CO2 reduction experiment, researchers focus on three primary performance metrics. Data collection is designed to answer these three questions:

1.  **Activity (Speed):** *How fast is the reaction occurring?*
    *   In chemistry, we usually measure reaction rates in Moles/Second. In electrochemistry, we measure this from the Current. Higher current equals faster fuel production.

2.  **Selectivity (Purity):** *What product are we making?*
    *   Electricity can create many different things, so we need to determine what percentage of the electrons actually went into the desired target product.

3.  **Stability (Durability):** *How long does the catalyst last?*
    *   A catalyst works very fast for the first 10 seconds but dies out afterward is useless. We analyze stability by monitoring how the Activity and Selectivity change over time.
  
These 3 pillars will be expanded later, but for now just keep in mind that we need these three things from the data that you will be collecting.

---

## 2. Phase 1: Data Collection
A dataset typically requires the collection of three distinct metrics.

### A. Electrical Data
These data are usually automatically provided by the potentiostat or multimeter.
*   **Current ($I$):** The rate of electron flow, measured in Amperes (A) or Milliamperes (mA).
*   **Voltage ($V$):** The driving force, measured in Volts (V).
*   **Time ($t$):** The duration of the electrolysis (Seconds).
*   **Total Charge ($Q$):** The total electron count ($Q = I \times t$).

### B. Physical Data
*   **Electrode Surface Area ($A$):** The geometric area of the catalyst submerged in the electrolyte ($cm^2$).
*   This allows for the calculation of current density, enabling comparisons between different sized electrodes.

### C. Chemical Data
*   **Product Amount ($n$):** The actual quantity of fuel produced, measured in Moles.
*   This requires external detection methods which will be later discussed in Section 5.

---

## 3. Phase 2: Fundamental Constants & Stoichiometry
To convert electrical charge (Coulombs) into chemical mass (Moles), two constants are required.

### The Conversion Factor
**Faraday’s Constant ($F$)** represents the charge of one mole of electrons.
$$ F \approx 96,485 \ C/mol $$

### The Stoichiometric Constant ($z$)
Different products require different amounts of electrons to form. These values, denoted as $z$ (or $n$), will be used to calculate efficiency. Here are the table of some commonly found products from CO2 reduction reaction.

| Product | Chemical Formula | Electrons Required ($z$) | Phase |
| :--- | :--- | :---: | :--- |
| **Hydrogen** | $H_2$ | **2** | Gas |
| **Carbon Monoxide** | $CO$ | **2** | Gas |
| **Formate** | $HCOO^-$ | **2** | Liquid |
| **Methane** | $CH_4$ | **8** | Gas |
| **Ethylene** | $C_2H_4$ | **12** | Gas |
| **Ethanol** | $C_2H_5OH$ | **12** | Liquid |
| **Propanol** | $C_3H_7OH$ | **18** | Liquid |

The more electrons required, the more electricity used up per the same mole of product.

---

## 4. Phase 3: The Core Metrics
Once you have your raw data and your constants, you can calculate the two numbers that are actually report in a research paper.

### A. Measuring Activity: Current Density ($j$)
Raw current is misleading. Of course, a massive sheet of copper will pass more current than a tiny wire; therefore, to compare your catalyst fairly against other researchers, the surface area must be normallized.

**The Formula:**
$$ j = \frac{I}{A} $$

*   **$j$:** Current Density ($mA/cm^2$)
*   **$I$:** Current (mA)
*   **$A$:** Surface Area of the electrode ($cm^2$)

**Interpretation:**
*   **High $j$:** The material is highly active; the reaction is fast.
*   **Low $j$:** The material is sluggish; the reaction is slow.
The number will further depends on type and category of catalyst which can be further compare with other work of same kind or the control

### B. Measuring Selectivity: Faradaic Efficiency (FE)
This is one of the critical if not the most critical calculation in $CO_2$ reduction. It tells you the percentage of electrons that were successfully used to create your desired product, versus those wasted on unwanted side reactions.

**The Formula:**
$$ FE = \frac{n \times z \times F}{Q} \times 100 $$

*   **$n$:** Moles of product produced.
*   **$z$:** Electrons required per molecule (from the Reference Table).
*   **$F$:** Faraday’s Constant ($96,485 \ C/mol$).
*   **$Q$:** Total Charge passed ($Current \times Time$).

**Example:**
If you ran 100 Coulombs of charge ($Q$) and produced a small amount of Methane, you plug the moles of Methane into $n$, use 8 for $z$, and calculate.
*   **FE = 80%:** The catalyst is excellent.
*   **FE = 1%:** The catalyst is mostly just making waste.

---

## 5. Phase 4: Visualizing the Data in Graph
Countless of numbers collected from the instrument don't tell us the whole story; we need to connect the dots and interpret the whole reaction. To understand how a catalyst behaves, we plot current, voltage and time.

### A. The Sweep Techniques: LSV and CV
These are the first experiments you run to see if your catalyst is working. You vary the voltage and measure the current output.

**1. Linear Sweep Voltammetry (LSV)**
*   **The Action:** The potentiostat scans the voltage in one direction (e.g., from 0V down to -2.0V).
*   **The Result:** A graph where the current stays near zero until a specific voltage, then drastically shoots down. This is because a reaction has its own specific minimum for the reaction to proceed.
*   **Onset Potential:** This is the voltage where the current starts to rise meaning the reaction turns on. A more positive onset potential is better as it can be inferred the reaction needs less energy to start. (Note that positive is less energy as we are considering the reduction reaction where we look at negative potentials)

**2. Cyclic Voltammetry (CV)**
*   **The Action:** The potentiostat scans the voltage down and then back up in a loop (0V $\rightarrow$ -2.0V $\rightarrow$ 0V).
*   **The Result:** A supposedly Duck-shaped loop, but the shape can varies with the experiments and conditions.
*   **The Difference:** While LSV just shows performance, CV is a diagnostic tool. The shape tells you about the capacitance (surface area) and reversibility. If the graph looks totally different in a few loop, the catalyst might be unstable. This is why in research, they often run the loop many times to ensure stability and reproducibility.

So while CV offer more data to interpret, LSV maybe suited to some experiment such as experiment focusing on steady state behavior.

### B. Chronoamperometry (CA)
LSV and CV only last a few seconds. To measure products, you need to run the reaction for a longer period.

*   **The Action:** Hold the voltage constant (e.g. -1.0V) and record current over time.
*   **The Graph:**
    *   **X-Axis:** Time (Seconds)
    *   **Y-Axis:** Current Density ($mA/cm^2$)
*   **Interpretation:**
    *   **Flat Line:** Stable catalyst.
    *   **Declining Line:** The catalyst is unstable (e.g. being poisoned or falling off).

---
