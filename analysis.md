<script type="text/javascript" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>

# Data Collection, Analysis & Interpretation
*Part 3: From Raw Data to Chemical Insight*

---

## 1. The Analytical Ch
In Electrochemical CO2 Reduction, the analysis that researchers mostly do involves around the speed of the reaction, the selectivity of the product and the stability of the catalyst.

---

## 2. Phase 1: Data Collection
A valid dataset requires the collection of three distinct metrics.

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

