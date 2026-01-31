<script type="text/javascript" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>

# Foundations & Theory
*Part 1: The Electrochemical Basics*

---

## 1. The Big Picture
To understand this project, we must first know what electrochemical reduction is. In chemistry, "reduction" simply means gaining electrons.

Most people are familiar with combustion, where we burn a fuel with oxygen to release energy. This process produces carbon dioxide ($$CO_2$$) and water.
$$ Fuel + Oxygen \rightarrow CO_2 + H_2O + Energy $$

We can actually reverse that process and that is essentially what "CO2 Reduction (CO2R)" is. We use energy from different sources (like heat or light) to complete this process, but electrical energy is what we will be focusing on as it is the most efficient yet. Using energy to force electrons back into carbon dioxide, we can convert it from a waste product back into a useful fuel or chemical feedstock, naming it the process of "electrochemical CO2 redcution".

$$ CO_2 + H_2O + Energy (Electricity) \rightarrow Fuel + Oxygen $$

Because $$CO_2$$ is an extremely stable molecule, it does not want to react. It requires a significant amount of energy and a specific environment to break its bonds and form new ones. This is why we need an electrochemical cell.

---

## 2. Basic Electrochemistry
Experiments in this field take place inside an "electrolytic cell". Unlike a battery (which creates electricity from chemicals), an electrolytic cell uses an external power source to force non-spontaneous chemical reactions to happen.

Here are the three critical components of the system:

### The Cathode (The Reduction Site)
The cathode is the electrode connected to the negative terminal of your power supply. This is where the electrons enter the solution.
*   **What happens here:** Positive ions or neutral molecules (like $$CO_2$$) are attracted to the surface. They accept electrons and undergo reduction.
*   **Function:** This is the most important part of the setup. The material of the cathode (e.g., Copper, Gold, Silver) determines what product you make. Researchers are working on creating better cathode which makes better product.
*   **Key Equation:** $$ CO_2 + 2H^+ + 2e^- \rightarrow CO + H_2O $$

### The Anode (The Oxidation Site)
The anode is the electrode connected to the positive terminal. This is where electrons leave the solution to return to the power supply.
*   **What happens here:** To balance the electrons used at the cathode, something must lose electrons (oxidize) at the anode. In most experiments, water is oxidized into oxygen gas.
*   **Function:** While we focus on what is happening on the cathode, the anode is necessary to complete the circuit.
*   **Key Equation:** $$ 2H_2O \rightarrow O_2 + 4H^+ + 4e^- $$

### The Electrolyte
This is the liquid solution between the two electrodes. Because pure water does not conduct electricity well, we dissolve salts like $$KHCO_3$$ (whcich makes the solution more conductive) into it.
*   **Function:** It allows ions to move between the cathode and anode to balance the charge. Without an electrolyte, the circuit is broken, and no reaction happens.

---

## 3. The Metrics: Potential, Current, and Density
In a physics class, you learn $V=IR$. In electrochemistry, these terms have specific physical meanings regarding the reaction.

### Potential (Voltage) = The "Push"
Potential, measured in Volts (V), is the driving force you apply to the system.
*   Every reaction requires a minimum voltage to start (Thermodynamic Potential).
*   If you apply -0.5V, the electrons might not have enough energy to break the $CO_2$ molecule.
*   If you apply -2.0V, you are pushing harder, which usually makes the reaction faster but might also trigger unwanted side reactions (like splitting water into hydrogen).

### Current (Amperage) = The "Rate"
Current, measured in Amperes (A), counts how many electrons are flowing through the wire per second.
*   Since the chemical reaction requires electrons (e.g., 2 electrons to convert one $CO_2$ to $CO$), the current tells you exactly how fast the reaction is occurring.
*   **High Current = High Reaction Rate.**

### Current Density (The Standard Metric)
This is the most important concept for comparing results.
If Researcher A uses a massive sheet of copper, they will get a high current just because the surface is big. If Researcher B uses a tiny wire, they get a low current.

To compare them fairly, we divide the current by the surface area of the electrode.
$$ Current Density (j) = \frac{Current (mA)}{Area (cm^2)} $$
*   **Unit:** $mA/cm^2$
*   **Usage:** In your experiments, you will always report current density, not just raw current. This allows you to compare your efficiency directly with papers published by universities.
