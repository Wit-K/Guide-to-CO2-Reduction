<script type="text/javascript" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>

# Data Collection, Analysis & Interpretation
*From Raw Numbers to Chemical Insight*

---

## 1. The Analysis Pipeline
In scientific research, running the experiment is only half the battle. The goal is to translate raw electrical signals into meaningful chemical data. The workflow generally follows this pipeline:
1.  **Collect Raw Data:** Gather electrical readings and physical measurements.
2.  **Apply Constants:** Use standard physical constants to bridge physics and chemistry.
3.  **Calculate Metrics:** Convert raw numbers into standard units (Current Density, Efficiency).
4.  **Visualize:** Plot graphs (Voltammetry) to identify trends.

---

## 2. Phase 1: Data Collection (The Raw Inputs)
Before doing any calculations, a researcher must aggregate three specific types of data.

### A. Electrical Data (The "Easy" Part)
If you are using a potentiostat or a multimeter, these numbers are provided automatically.
*   **Current ($I$):** The rate of electron flow, measured in Amperes (A) or Milliamperes (mA).
*   **Voltage ($V$):** The potential difference applied, measured in Volts (V).
*   **Time ($t$):** The duration of the electrolysis, measured in Seconds (s).
*   **Charge ($Q$):** The total number of electrons passed. Calculated as $Q = I \times t$.

### B. Physical Data (The Normalization Factor)
*   **Electrode Surface Area ($A$):** The geometric area of the Working Electrode dipped in the solution.
*   *Why it measures:* You cannot compare a giant industrial plate to a tiny laboratory wire using raw current. You must measure the area (in $cm^2$) to calculate density later.

### C. Chemical Data (The "Hard" Part)
*   **Product Yield ($n$):** The physical amount of fuel produced, measured in **Moles**.
*   *The Challenge:* The potentiostat does **not** tell you this. It only tells you how many electrons passed. It does not tell you if those electrons made Methane, Carbon Monoxide, or just Hydrogen. You must determine this using separate detection methods (discussed in Section 5).

---

## 3. Phase 2: The Reference Cheat Sheet
To perform any analysis, you need specific physical constants. These values are the "Key" to converting electricity (Coulombs) into Chemistry (Moles).

### The Universal Constant
**Faraday’s Constant ($F$)** represents the total electric charge carried by one mole of electrons.
$$ F \approx 96,485 \ C/mol $$
*   *Usage:* This number allows you to convert the "Total Charge" from your machine into "Moles of Electrons."

### The Electron Reference Table ($z$ or $n$)
Not all products are created equal. Making a complex molecule requires more electrons than making a simple one. You must know the **electron requirement ($z$)** for the specific product you are detecting.

| Product | Chemical Formula | Electrons Required ($z$) | Product State |
| :--- | :--- | :---: | :--- |
| **Hydrogen** | $H_2$ | **2** | Gas |
| **Carbon Monoxide** | $CO$ | **2** | Gas |
| **Formate** | $HCOO^-$ | **2** | Liquid |
| **Methane** | $CH_4$ | **8** | Gas |
| **Ethylene** | $C_2H_4$ | **12** | Gas |
| **Ethanol** | $C_2H_5OH$ | **12** | Liquid |
| **Propanol** | $C_3H_7OH$ | **18** | Liquid |

*   **Key Insight:** Notice that Methane requires 4 times as much electricity to create as Carbon Monoxide. This is why "High Current" doesn't always mean "More Moles"—it might just mean you are making a more electron-hungry product.
