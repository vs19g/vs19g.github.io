---
title: "Digital Data Acquisition Systems at the John D. Fox Laboratory"
excerpt: "Upgrading the ANASEN active target's DAQ with CAEN digitizers and FSUDAQ, and supporting digital electronics for the SABRE array with CoMPASS."
collection: portfolio
---
{% include base_path %}

Every detector upgrade is only as good as the electronics chain reading it out. Alongside the mechanical rebuild of the ANASEN proportional counter, I led the transition of its data acquisition system from legacy analog electronics to a digital, trigger-flexible pipeline, and separately supported digital DAQ setup for the SABRE array.

### ANASEN: CAEN Digitizers and FSUDAQ
The upgraded proportional counter and silicon array produce many more channels than the original analog chain could cleanly handle, and active-target experiments demand tight timing correlations between the gas detector, the silicon wall, and the beam-line diagnostics.
* **Digitizer Integration:** Integrated CAEN 1740 & 1725 digitizers alongside QDC/PHA firmware to replace the legacy analog readout.
* **DAQ Software:** Configured **FSUDAQ**, the Fox Lab's in-house acquisition framework, to achieve reliable coincident data readout across the upgraded detector.

This digital chain was in place for the experimental campaigns measuring the $$^{27}Al(\alpha,p)$$, $$^{24}Mg(\alpha,p)$$, and $$^{17}F(\alpha,p)$$ reactions.

### SABRE / SE-SPS: CoMPASS
To broaden my experimental electronics expertise beyond ANASEN, I assisted in setting up the digital electronics and trigger logic for operating the **SABRE** array in conjunction with the **SE-SPS** (Super-Enge Split-Pole Spectrograph), using **CoMPASS** for digital pulse processing.

### Impact
Working across both systems gave me hands-on experience with two different digital DAQ stacks (FSUDAQ and CoMPASS) and digitizer families, and with the trigger logic design that coincident, multi-detector nuclear astrophysics experiments depend on.
