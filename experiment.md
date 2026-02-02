<script type="text/javascript" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>

# Experimental Design & Set Up
Part2: Analysis and Break Down of each Critical Component in Common Design.

---

## 1. The Big Picture
For 90% of high school and undergraduate research, the standard design is the "H-Type Electrolytic Cell".

H-Type Electrolytic Cell or commonly called "H-cell" gets its name from its iconic look, two container and a bridge, thus calling it H-Cell.
Imagine two separate building connected by a bridge.
*   **Cathodic Chamber:** This is where the CO2 reduction happens. It contains the Working Electrode and the CO2 gas.
*   **Anodic Chamber:** This contains the Counter Electrode. Its job is just to complete the electrical circuit.
*   **The Membrane/Bridge:** This allows ions to flow between the chambers but stops the liquids and gases from mixing.

**Why separate them?**
If you put everything in one beaker, the oxygen produced in Anodic Chamber would float over to Chamber 1 and ruin your sensitive CO2 reaction. The "H" shape physically isolates these compounds while allowing electricity to flow and reactions to happen.

*(Note: There are also other types of Cells including Flow Cells and Single Cell. But, because Flow Cells are too advance and require expensive pumps and Single Cell will get all the liquid mixed up, we will left them out and focus on H-Cell. If you are interested, you can research further by looking into scientific papers regarding the Flow Cell pros, cons, and set up)*

---

## 2. Anatomy of an H-Cell System
Even though there are many different H-Cells from various manufacturer, most of them consists of 5 main components. Understanding their roles are necessary for designing a valid experiment.

### The Core Components in Simple Term
1.  **The Working Electrode (WE):** The catalyst material where the CO2 reduction reaction occurs.
2.  **The Counter Electrode (CE):** An inert and electrically conductive material that completes the electrical circuit.
3.  **The Reference Electrode (RE):** A specialized and stable probe with known constant potential for benchmarking.
4.  **The Membrane:** A selective barrier that isolates the two chambers.
5.  **The Electrolyte:** The ionic solution that allows charge transfer.

### System Configuration: 2-Electrode vs. 3-Electrode
One of the first design choices a researcher makes is how to control the voltage.

**A. The 2-Electrode Configuration**
In this setup, a potential difference is applied directly between the Anode and Cathode.
*   **Measurement:** Measures the total cell voltage.
*   **Limitation:** It measures the sum of all resistance in the cell (wires, electrolyte, membrane). It is difficult to distinguish how much energy is being used for the reaction versus how much is lost to resistance.
*   **Context:** Common in industrial bulk electrolysis where precision regarding specific surface potentials is less critical than total power consumption.

**B. The 3-Electrode Configuration (The Academic Standard)**
This setup introduces a Reference Electrode placed near the Working Electrode.
*   **Measurement:** The potentiostat measures the voltage difference between the *Working Electrode* and the *Reference Electrode*, while passing current between the *Working* and *Counter* electrodes.
*   **Advantage:** This isolates the Working Electrode, essentially ignoring the resistance of the rest of the cell.
*   **Context:** This is the standard for published research as it allows for precise reporting of thermodynamic data ($V$ vs. $RHE$).

---

## 3. The Working Electrode (WE)
The Working Electrode (Cathode) is the centerpiece of the experiment. It is the only component where the specific material selection dictates the chemical product.

### Function
The WE acts as the electron donor. In an H-Cell, it is submerged in the cathodic chamber, which is continuously purged with CO2 gas.

### Material Selection Criteria
Researchers select materials based on the "Product Selectivity" map established in literature:
*   **Copper (Cu):** Currently the only bulk metal capable of catalyzing substantial Carbon-Carbon coupling to form hydrocarbons (Ethylene, Ethanol, Methane).
*   **Au, Ag, Zn (Gold, Silver, Zinc):** These metals typically terminate the reaction early, producing Carbon Monoxide (CO) or Formate.
*   **Carbon/Graphite:** often used as a baseline or support structure, but generally poor for direct CO2 reduction activity.

### Surface Pretreatment Principles
The surface state of the metal significantly impacts data reproducibility. A "fresh" sample from a supplier often contains surface oxides or organic contaminants that can block active sites. Standard laboratory protocols usually involve a pretreatment phase:
*   **Mechanical Polishing:** Using successively finer abrasives to create a uniform surface area.
*   **Chemical Etching:** Using dilute acids to strip native oxide layers immediately prior to testing.
*   **Electropolishing:** Using a high current in a specific solution to microscopically smooth the surface.

*Note: The specific pretreatment method is often detailed in the "Experimental Methods" section of the papers you choose to reference.*
