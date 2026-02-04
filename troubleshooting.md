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
*A Diagnostic Approach to Experimental Anomalies*

---

## 1. The Diagnostic Philosophy
In electrochemical research, failure is rarely random. When an experiment goes unexpected, it is usually an effect from specific uncontrol factor. Successful troubleshooting depends on isolation and inspection of these variables rather than random fix.

The root of issue met often stems from these:
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
    Confirm the contunitity of the wire using device like ammeter or multimeter. If the wires are confirmed to connected, the issue may lie with an air bubble trapped inside a glass frit or a salt bridge acts. This bubble act as an electrical insulator, cutting of anode and cathode and redering the circuit incomplete.
    
### Issue: High Impedance / Compliance Error
*   **Symptom:**
    The power supply or potentiostat hits its maximum voltage limit while not delivering the expected current.
*   **Potential Causes:**
    1.  Electrolyte concentration is too low, resulting in too low conductivity.
    2.  Excessive distance between Working and Counter electrodes.
    3.  Membrane dehydration.
*   **Common Diagnosis:**
    This indicates High Cell Resistance (IR Drop). The electricity is struggling to push through the liquid. This is frequently observed when using ion-exchange membranes (like Nafion) that were not properly soaked in water for 24 hours prior to use, as dry membranes are highly resistive.
