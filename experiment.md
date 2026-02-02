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

## 2. Simple Anatomy of an H-Cell System
Even though there are many different H-Cells from various manufacturer, most of them consists of 5 main components. Understanding their roles are necessary for designing a valid experiment.

### The Core Components in Simple Term
1.  **The Working Electrode (WE):** The catalyst material where the CO2 reduction reaction occurs.
2.  **The Counter Electrode (CE):** An inert and electrically conductive material that completes the electrical circuit.
3.  **The Reference Electrode (RE):** A specialized and stable probe with known constant potential for benchmarking.
4.  **The Membrane:** A selective barrier that isolates the two chambers.
5.  **The Electrolyte:** The ionic solution that allows charge transfer.

All of these are crucial components in "three electrode system" commonly used in H-cell electrochemical experiments. It is called three electrode system as to its three electrode, which includes reference electrode that distinguishes it from the normal two electrode system studied in high school. 

---

## 3. The Working Electrode (WE)
Core Research.

### Role & Significance
The Working Electrode (Cathode) is the centerpiece of the experiment. It serves as the electron donor and the active site where the reduction reaction occurs. Connected to the negative terminal, most of the time, the Working Electrode is the catalyst. In electrochemistry, the material of the electrode dictates the entire reaction pathway. The specific atomic arrangement on the surface determines whether $CO_2$ is converted into Carbon Monoxide, Methane, or just Hydrogen gas. Therefore, the choice of the Working Electrode is the primary variable in any CO2 reduction study.

### Key Properties That Affect Results
1.  **Surface Morphology and Composition:** The roughness or nano-structure of the surface changes the local environment and the availability of reaction sites, often influencing the efficiency of the reaction. The purity of the metal is also critcal, and even trace of impurities can alter the product distribution.
2.  **Pretreatment and Modification:** There are multiples available modification of the metal before running the experiment. This affects the reaction widely and often change what product are produced.

### Common Choices in Research
In this field, the WE varies by a lot to each researchers analyzing different materials. However, the most common working electrode are metals:
*   **Copper (Cu):** The most significant material in the field, as it is the only bulk metal capable of efficiently producing hydrocarbons (Ethylene, Ethanol).
*   **Other Transition Metals:** Au, Zn and Ag are commonly used to produce CO. And Sn and Bi are commonly used to produce Formate
These metals can undergoes several tuning and modifying as stated. The common example are: oxidizing metals to help increase its surface area and change the product distribution, replacing chunks of metal by their nano particles might improve their faradaic efficiency and supporting metals with structures like carbon could help in mass transport of CO2.
---

## 4. The Counter Electrode (CE)
Complete the Circuit.

### Role & Significance
The Counter Electrode (Anode) completes the electrical circuit. While the focus of the experiment is on the cathode side, the anode is necessary for the system to fully function. Connected to the positive terminal, the Counter Electrode balances the reaction. For every electron consumed by the $CO_2$ reduction at the cathode, an oxidation reaction must occur here (typically splitting water into Oxygen).

### Key Properties That Affect Results
1.  **Chemical Inertness:** The material must withstand high oxidation potentials without corroding. If it degrades or dissolves during the experiment, metal ions can cross the cell and contaminate the Working Electrode, making the data invalid.
2.  **Surface Area:** To ensure the Counter Electrode does not become a bottleneck, researchers ensure its surface area is significantly larger than that of the Working Electrode. This makes the test fair when compairing between Catalysts.

### Common Choices in Research
*   **Platinum (Pt):** The academic standard due to its exceptional stability and conductivity, usually comes in form of wire or mesh.
*   **Graphite/Carbon:** A cost-effective alternative often used in educational settings, though it requires monitoring for degradation over long-term experiments.
*   **Dimensionally Stable Anodes (DSA):** Industrial-grade oxides (like Iridium Oxide) designed specifically for high-current durability.
