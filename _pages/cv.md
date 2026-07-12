---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

<a href="{{ base_path }}/files/cv-vignesh-sitaraman.pdf" class="btn btn--primary">Download CV as PDF</a>

Education
======
* Ph.D. in Nuclear Astrophysics, Florida State University, Tallahassee, FL, Present
* M.S. in Physics, Florida State University, Tallahassee, FL, 2020
* M.Sc. in Physics, BITS Pilani - Hyderabad Campus, India, 2018
  * Thesis: Digital Signal Processing for the Charged Particle Detector Array at INGA
* B.E. in Chemical Engineering, BITS Pilani - Hyderabad Campus, India, 2018
  * Thesis: Desalination of Water using Nano-Photonics

Research Experience
======
* **Graduate Research Assistant** | May 2020 – Present
  * John D. Fox Superconducting Linear Accelerator Laboratory, FSU
  * Supervisor: Prof. Ingo Wiedenhöver
  * Conceptualized and implemented a novel design upgrade to the internal tracking proportional counter, demonstrating an order-of-magnitude improvement in position resolution during preliminary alpha-source calibration.
  * Deployed the upgraded detector in three experimental campaigns measuring the $$^{27}Al(\alpha,p)$$, $$^{24}Mg(\alpha,p)$$, and $$^{17}F(\alpha,p)$$ reactions.
  * Assisted in developing a simulation of the electric fields in the ANASEN detector; efforts on a particle Monte Carlo simulation are ongoing.
  * Upgraded the digital Data Acquisition (DAQ) system by integrating CAEN 1740 & 1725 digitizers alongside QDC/PHA firmware for coincident data readout using FSUDAQ.
  * Assisted in setting up the digital electronics and trigger logic for operating the SABRE array in conjunction with the SE-SPS (Super-Enge Split-Pole Spectrograph) using CoMPASS.

* **Junior Research Fellow** | Aug 2018 – July 2019
  * Tata Institute of Fundamental Research (TIFR), Mumbai
  * Supervisors: Prof. Rudrajyoti Palit and Prof. S.N. Mishra
  * Evaluated timing and energy response of $$LaBr_3(Ce)$$ detectors to augment the INGA array with fast-timing capabilities for precision nuclear lifetime measurements.
  * Investigated structural properties of neutron-deficient nuclei in the mass-130 region, far from the line of stability.

* **Project: Desalination of Water using Nano-Photonics** | Jan 2018 – May 2018
  * BITS Pilani - Hyderabad Campus
  * Supervisors: Prof. Kannan Ramaswamy and Dr. Vikranth K. Surasani
  * Simulated a novel Nano-Photonics Enabled Solar Membrane Distillation (NESMD) plant using a bilayer membrane architecture, and evaluated its geographic viability for Hyderabad to guide construction of a prototype plant.

* **Project: Digital Signal Processing for the Indian National Gamma Array** | Aug 2017 – Dec 2017
  * Tata Institute of Fundamental Research (TIFR), Mumbai
  * Supervisors: Prof. Rudrajyoti Palit and Dr. Sarmistha Banik
  * Participated in experimental campaigns at the BARC-TIFR Pelletron LINAC Facility; implemented and compared digital signal processing algorithms to analyze high-volume data from INGA and the Charged Particle Detector Array (CPDA).

Publications
======
{% for post in site.publications reversed %}
  * {{ post.date | date: "%Y" }} — [{{ post.title }}]({{ base_path }}{{ post.url }}), *{{ post.venue }}*
{% endfor %}

Talks & Presentations
======
{% for post in site.talks reversed %}
  * {{ post.date | date: "%Y" }} — [{{ post.title }}]({{ base_path }}{{ post.url }}), {{ post.venue }}{% if post.location %}, {{ post.location }}{% endif %}
{% endfor %}

Teaching
======
* **PHY 2054 (College Physics B):** Instructed undergraduate lab sessions on electromagnetism, circuits, and optics (Summer/Fall 2020).
* **PHY 2053 (College Physics A):** Facilitated hands-on experiments covering classical mechanics, kinematics, and thermodynamics (Fall 2019, Spring 2020).
* Conducted pre-lab lectures, graded technical reports, and hosted weekly office hours to assist students with problem-solving and data analysis.

Mentorship & Service
======
* Mentored junior students and undergraduates in experimental nuclear physics techniques, including hands-on training with vacuum systems, digital electronics, and detector testing/assembly, as well as data analysis and simulation fundamentals using C++ and ROOT.
* **Tandem Maintenance Coordinator**, John D. Fox Laboratory — trained incoming graduate students to conduct lab safety and maintenance checks and organized the maintenance schedule.

Technical Skills
======
* **Detector Instrumentation:** Detector design and fabrication; gas-filled proportional counters, silicon strip detectors, and High-Purity Germanium (HPGe) detectors; high-vacuum environments; analog/digital data acquisition.
* **Data Acquisition (DAQ):** Integration of digital electronics (CAEN 1740/1725 digitizers), digital DAQ firmware configuration (PHA/QDC), FSUDAQ, CoMPASS, hardware troubleshooting.
* **Data Analysis & Simulation:** ROOT, Garfield++, Gmsh, Elmer, ParaView, pycatima, SRIM, LISE++, MATLAB, Octave.
* **Programming Languages:** C++, Python, $$\LaTeX$$.
* **Engineering & Modeling:** SolidWorks, COMSOL.
* **Accelerator Operations:** Operational proficiency with superconducting LINAC and Tandem Van de Graaff accelerators.
* **Languages:** English, Hindi, Tamil, Spanish (B1).

Awards & Memberships
======
* John D. Fox Award, Department of Physics, Florida State University, 2025
* Evelyn and John Baugh Scholarship, Department of Physics, Florida State University, 2024
* Dean's Fellowship, Florida State University, 2019
* Junior Research Fellow, Tata Institute of Fundamental Research, 2018
* Member, American Physical Society, Present
* AAAS Scholarship, Member, American Association for the Advancement of Science, 2020–2021
