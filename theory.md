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
*   **Function:** This is the most important part of the setup. The material of the cathode (e.g., Copper, Gold, Silver) determines what product you make. Researchers are working together to create better cathode which makes better product.
*   **Key Equation:** $$ CO_2 + 2H^+ + 2e^- \rightarrow CO + H_2O $$

### The Anode (The Oxidation Site)
The anode is the electrode connected to the positive terminal. This is where electrons leave the solution to return to the power supply.
*   **What happens here:** To balance the electrons used at the cathode, something must lose electrons (oxidize) at the anode. In most experiments, water is oxidized into oxygen gas.
*   **Function:** While we focus on what is happening on the cathode, the anode is necessary to complete the circuit.
*   **Key Equation:** $$ 2H_2O \rightarrow O_2 + 4H^+ + 4e^- $$

### The Electrolyte
This is the liquid solution between the two electrodes. Because pure water does not conduct electricity well, we dissolve salts, like $$KHCO_3$$, (which makes the solution more conductive) into it.
*   **Function:** It allows ions to move between the cathode and anode to balance the charge. Without an electrolyte, the circuit is broken, and no reaction happens.

---

## 3. Understanding the Variables
In an electrochemical experiment, there are two main parameters we can alter or measure: Potential and Current. It is vital to understand the difference between the driving force and the reaction rate.

### Potential (Voltage)
Potential is the energy or basically, the push applied to the system. Every chemical reaction has its own minimum energy requirement to proceed.
*   **Thermodynamic Potential:** This is the theoretical minimum voltage needed to start the reaction. For converting CO2 to Carbon Monoxide, this is approximately -0.11 Volts.
*   **Applied Potential:** This is the real potential applied in the real experiment, which is significantly more than the theoretical value. This is because real-world electrochemical reactions are hardly perfectly efficient and requires additional energy to overcome the theroretical minimum.

### Current (Amperage)
While voltage is the push, the current is the flow. Current measures the rate at which electrons are moving across the interface. Since the chemical reaction consumes electrons, the current tells you directly how fast the reaction is happening.
*   **High Current:** A fast reaction rate.
*   **Low Current:** A slow reaction rate.

### Surface Area and Normalization
A large piece of copper will naturally allow more current to pass than a thin copper wire, just because there is more space for the reaction to occur. This makes comparision unfair. So, to make fair comparisons between different experiments, we wil look at "Current Density" instead. This is the ratio of current by surface area of the electrode, telling us how active the material is regardless of its size.

---

## 4. Thermodynamics and Kinetics
A common questions from beginners is why the reaction does not start exactly at the theoretical voltage.

### The Energy Barrier
Even if you apply enough energy to make the reaction possible, the reaction might still be too slow to measure. This is because molecules need to rearrange themselves, bonds need to break, and intermediates need to form.

### Overpotential
To overcome this slowness, we apply extra voltage. This extra voltage is the **Overpotential**.
*   If a catalyst is "good," it requires very little overpotential to reach a high current.
*   If a catalyst is "bad," you must apply a massive voltage to get even a small current.

In research, the goal is often to find a setup that produces the most product with the least amount of overpotential.

---

## 5. Selectivity and The Main Challenge
The most difficult part of CO2 reduction is not breaking the CO2; it is avoiding the water.

### The Hydrogen Problem
Since our electrolyte is mostly water, there are billions of water molecules surrounding the electrode for every one CO2 molecule. Water can also accept electrons to form Hydrogen gas ($H_2$).
$$ 2H^+ + 2e^- \rightarrow H_2 $$

This is called the **Hydrogen Evolution Reaction (HER)**. It is a parasitic reaction that wastes your electricity.

### Selectivity (Faradaic Efficiency)
We measure success using **Faradaic Efficiency (FE)**. This represents the percentage of electrons that went into making the product you wanted (like CO) versus the product you didn't want (like Hydrogen).
*   **100% FE:** Every electron resulted in CO2 reduction.
*   **0% FE:** All electrons were wasted making Hydrogen gas.

The choice of metal for your cathode dictates this selectivity. Some metals (like Platinum) are excellent at making Hydrogen, which makes them terrible for CO2 reduction. Other metals (like Copper, Gold, or Silver) are poor at making Hydrogen, allowing the CO2 reduction to compete effectively.

---

## 6. Catalyst Materials: What determines the product?
Not all metals act the same. In the 1980s, Japanese researcher Yoshio Hori discovered that metals can be categorized into three distinct groups based on what they produce when you apply electricity in CO2-saturated water.

### Group 1: The Hydrogen Generators (Avoid these)
Metals like **Platinum (Pt), Nickel (Ni), Iron (Fe), and Titanium (Ti)**.
*   **Behavior:** These metals bind to Hydrogen atoms very strongly.
*   **Result:** If you use these as a cathode, you will produce almost exclusively Hydrogen gas. The CO2 will barely touch the surface.
*   **Verdict:** Do not use these for the working electrode.

### Group 2: The Two-Electron Pathway (CO / Formate)
Metals like **Silver (Ag), Gold (Au), Zinc (Zn), and Tin (Sn)**.
*   **Behavior:** These metals are poor at making hydrogen, allowing CO2 to react. However, they stop the reaction early.
*   **Result:** They produce Carbon Monoxide (CO) or Formate (HCOO-).
*   **Verdict:** Great for beginners. Zinc is cheap and makes Formate; Silver is expensive but makes CO efficiently.

### Group 3: The Hydrocarbon Pathway (Copper)
**Copper (Cu)** is unique in the periodic table.
*   **Behavior:** Copper has just the right binding energy to hold onto the Carbon atom, allowing it to bond with other Carbon atoms.
*   **Result:** It can produce Methane ($CH_4$), Ethylene ($C_2H_4$), and Ethanol ($C_2H_5OH$).
*   **Verdict:** The "Holy Grail" of research. However, it is complex because it produces a mix of many different liquids and gases at once.

---

## 7. The Physical Limit: Solubility
Finally, we must understand the environment. CO2 is a gas, but the reaction happens on the solid metal surface inside a liquid.

For the reaction to work, CO2 gas must dissolve into the water to reach the electrode.
1.  **Solubility:** CO2 does not dissolve well in water (approx. 33mM concentration at room temperature).
2.  **Mass Transport:** As you run the reaction, you use up the CO2 near the metal surface. If new CO2 cannot diffuse in fast enough, the reaction starves, and Hydrogen evolution takes over.

**Practical Implication:**
This is why you will see instructions to "bubble" CO2 gas continuously into the solution. It ensures the water stays saturated with CO2, giving the reaction the best chance to succeed.
