---
title: "TWINE: Twisted-Wire Tracking and the Shockley–Ramo Signal"
excerpt: "How the twisted-wire proportional counter I built for ANASEN locates a track along the beam, and how a Shockley–Ramo weighting-field calculation predicts its cathode signal."
collection: portfolio
order: 2
header:
  teaser: "/twine-crossovers-3d.png"
---
{% include base_path %}

TWINE is the proportional counter I designed with Prof. Ingo Wiedenhöver and built for the [ANASEN active target](/portfolio/anasen-upgrade/). This page explains how its twisted wires locate a track along the beam, and how I used the Shockley–Ramo theorem to predict, and then test, the cathode signal that the position reconstruction depends on.

### The Idea
TWINE (Twisted Wire Instrument for Nuclear Experiments) replaces the straight resistive anodes of the original ANASEN counter with 24 twisted Au-W anodes (18 µm diameter) and 24 counter-twisted Au-W cathodes (76.2 µm diameter), each read out at one end, for a total of 48 channels. Inside the anode ring are 48 grounded guard wires, which shield the counter from the ion-chamber wires and the needle at smaller radii.

Because the anodes and cathodes twist in opposite directions, each anode crosses the cathodes at eight points along the 348.6 mm active length. The original counter had to locate an avalanche anywhere along the full wire from a resistive charge-division ratio. In TWINE the fired anode and cathodes identify the cell between two crossovers, 39 mm long at the center of the counter and 46 mm at the ends, and the position only has to be interpolated within that cell, from the way the induced signal is shared between the two cathodes that bracket the avalanche.

<img src="/images/twine-crossovers-3d.png" alt="Drawing of a tapered wire cage around a black beam line, with red anodes and blue cathodes twisting in opposite directions and one highlighted anode marked by eight dots where it crosses cathodes. An orange track runs from a starred vertex on the beam line through a circled point on that anode to a box labeled SX3 (silicon)." width="700" style="display: block; margin: 0 auto;">
<p align="center"><i>Anodes in red, cathodes in blue. One anode is highlighted with its eight crossovers (dots). A particle from a vertex on the beam axis fires the anode nearest its track on its way to the silicon.</i></p>

<img src="/images/twine-cell-readout.png" alt="Diagram along the beam axis of one cell: a horizontal anode line A j crossed at z i and z i plus 1 by two dashed diagonal cathode lines carrying charges Q i and Q i plus 1. A dotted charge-weighted line crosses the anode at z pc, closer to the midpoint z c i than the starred avalanche at z, with an arrow labeled divide by kappa from z pc to z." width="550" style="display: block; margin: 0 auto;">
<p align="center"><i>One cell, unrolled in azimuth. The avalanche on anode A<sub>j</sub> induces charges Q<sub>i</sub> and Q<sub>i+1</sub> on the two cathodes that bracket it, whose crossovers lie at z<sub>i</sub> and z<sub>i+1</sub>. The charge-weighted position is compressed toward the cell midpoint, and a correction factor &kappa; expands it back.</i></p>

<table style="width:100%; border: none;">
  <tr style="border: none;">
    <td style="width:55%; border: none; text-align: center;">
      <img src="/images/twine-pc-cad.png" alt="Computer rendering of two square green circuit boards, each with a round central hole, joined by a bundle of many thin wires that cross one another between the boards." style="width:100%;">
      <br><i>(a) CAD model: the wire bundle strung between the two mounting boards. The opposite handedness of the anodes and cathodes shows where the two sets cross.</i>
    </td>
    <td style="width:45%; border: none; text-align: center;">
      <img src="/images/twine-pc-as-built.jpg" alt="Photograph looking along the beam axis into the counter: a ring of fine wires and pins on a green board surrounds a central opening, with the silicon detectors visible around and behind it." style="width:100%;">
      <br><i>(b) The counter as built, photographed along the beam axis.</i>
    </td>
  </tr>
</table>

### Field Maps
The twist breaks the translational symmetry of an ordinary multi-wire counter, so the field near the crossovers can't be taken from an analytic formula. Every wire is inclined to the beam axis by only about 6° at the anode radius, so the transverse field changes slowly along the counter, and I modeled it as a stack of two-dimensional slices. At each slice I meshed the cross section with Gmsh, refined near the wires, and solved Laplace's equation with Elmer at the 660 V operating bias: anodes at 660 V, with the cathodes, guard wires, and chamber wall grounded.

Two slices bracket the cycle. At the cell midpoint (z = 0) each anode lies halfway between two cathodes, the "interspersed" configuration, and the equipotentials spread evenly around it. At the first crossover (z = 19.72 mm) a cathode sits at the same azimuth as each anode, the "stacked" configuration, and the equipotentials between the two crowd into a narrow bundle. No slice shows a distortion that would break proportionality or leave gas from which charge is not collected, and every anode stays enclosed in its own cell.

<table style="width:100%; border: none;">
  <tr style="border: none;">
    <td style="width:50%; border: none; text-align: center;">
      <img src="/images/twine-equipotential-midcell.webp" alt="Contour map on a dark background of one quarter of the counter cross section. A diagonal row of anodes, each a bright orange spot, is surrounded by closed equipotential lines; each anode lies midway between two dark outer cathode wires, with smaller grounded wires on the inner side and evenly spread contours." style="width:100%;">
      <br><i>(a) Cell midpoint, z = 0 mm (interspersed). Each anode lies halfway between two cathodes.</i>
    </td>
    <td style="width:50%; border: none; text-align: center;">
      <img src="/images/twine-equipotential-crossover.webp" alt="Contour map on a dark background of the same quarter cross section. Each anode, a bright orange spot, now has a dark cathode wire directly outside it; the contours between each pair crowd into a narrow bundle and open into a lobe beyond the cathode." style="width:100%;">
      <br><i>(b) Crossover, z = 19.72 mm (stacked). Each cathode has rotated to the azimuth of an anode.</i>
    </td>
  </tr>
</table>
<p align="center"><i>Equipotentials over one quadrant of the transverse section at the 660 V operating bias. The beam axis is at the bottom right of each panel.</i></p>

### The Shockley–Ramo Theorem
The cathodes don't collect the avalanche. They see a charge induced by the positive ions as those ions drift away from the anode, and the Shockley–Ramo theorem gives that signal. The weighting field $$\vec{E}_w$$ of an electrode is the Laplace solution with that electrode at unit potential, every other electrode grounded, and no charge in the volume. A charge $$q$$ moving with velocity $$\vec{v}$$ induces on that electrode the current

$$i = q\,\vec{v}\cdot\vec{E}_w ,$$

and moving from $$\vec{x}_1$$ to $$\vec{x}_2$$ it induces the net charge $$Q = -q\left[\varphi_w(\vec{x}_2) - \varphi_w(\vec{x}_1)\right]$$, where $$\varphi_w$$ is the weighting potential. The weighting field depends only on the electrode geometry, not on the voltages applied, and each readout wire has its own.

<table style="width:100%; border: none;">
  <tr style="border: none;">
    <td style="width:33%; border: none; text-align: center;">
      <img src="/images/twine-shockley-ramo-real.png" alt="Diagram of a positive charge q moving straight down with velocity v from a top plate at potential V0 toward three strips labeled k minus 1, k and k plus 1, along downward field arrows labeled E0. Shaded curves show the induced charge on the plate and on the strips, largest on strip k directly below the charge." style="width:100%;">
      <br><i>(a) Real configuration: q drifts along the operating field E<sub>0</sub> toward grounded strips.</i>
    </td>
    <td style="width:33%; border: none; text-align: center;">
      <img src="/images/twine-shockley-ramo-weighting.png" alt="Diagram of the same three strips with strip k at potential 1 and everything else at 0. Shaded nested arcs of the weighting potential, labeled 0.1 and 0.4, rise above strip k, small arrows show the weighting field, and a dashed line marks the path of the charge from x1 at the top plate to x2 at strip k." style="width:100%;">
      <br><i>(b) Weighting configuration of strip k: charge removed, strip k at unit potential, all else grounded.</i>
    </td>
    <td style="width:33%; border: none; text-align: center;">
      <img src="/images/twine-shockley-ramo-current.png" alt="Line graph of induced current, in units of q over T, against drift time from 0 to 1 T. The curve for strip k, which collects the charge, stays negative and falls to about minus 2.6; the curve for its neighbor k plus 1 starts slightly negative and turns positive to about 1.3, with shading marking equal areas." style="width:100%;">
      <br><i>(c) Induced current: strip k, which collects the charge, ends with &minus;q; on the neighbor the current reverses and its two lobes cancel.</i>
    </td>
  </tr>
</table>

### Applying It to TWINE
In TWINE the moving charge is an avalanche ion leaving an anode, and the electrodes of interest are the cathodes. The ions drift in the mobility regime, $$\vec{v} = \mu\vec{E}_0$$, so the current induced on a cathode is

$$i = q\mu\,\vec{E}_w\cdot\vec{E}_0 .$$

I computed both fields on the same mesh: the operating solution above, and a second solution with one cathode at 1 V and every other electrode grounded. Their dot product maps how strongly that cathode responds to an ion at each point.

* **The signal comes from a thin shell around the anode.** The product is concentrated within a short distance of each wire and falls by about two orders of magnitude across the rest of the cell, because near a thin wire both fields fall as 1/r.
* **The readout samples exactly that shell.** The ions take tens of microseconds to reach the cathodes, but the ~3 µs shaping returns the pulse to baseline long before then, and the PC hit must fall within a 650 ns coincidence window with the silicon. Together they select the first microseconds of the ion drift, which is where the cathode is most sensitive.
* **The signal is modulated along each cell.** At a crossover, the aligned cathode receives about 1.7 times the current that either cathode bracketing a mid-cell avalanche receives. The cathode share therefore peaks at the crossovers and dips midway between them, and that modulation is what places an event within its cell.

<table style="width:100%; border: none;">
  <tr style="border: none;">
    <td style="width:50%; border: none; text-align: center;">
      <img src="/images/twine-dotproduct-midcell.png" alt="Color map on a gray background around one cathode at the top of the frame. A purple region, for negative values, joins that cathode to the two anodes just below it in an inverted V; green spots surround the neighboring cathodes and the inner guard wires." style="width:100%;">
      <br><i>(a) Cell midpoint, z = 0 mm: the driven cathode (top) faces two anodes at &plusmn;7.5&deg;.</i>
    </td>
    <td style="width:50%; border: none; text-align: center;">
      <img src="/images/twine-dotproduct-crossover.png" alt="Color map on a gray background around one cathode at the top of the frame. A purple oval joins that cathode to the single anode directly below it, smaller purple lobes surround the next anode on each side, and green spots surround the neighboring cathodes and the inner guard wires." style="width:100%;">
      <br><i>(b) Crossover, z = 19.72 mm: the driven cathode faces one anode at its own azimuth.</i>
    </td>
  </tr>
</table>
<p align="center"><i>Dot product of one cathode's weighting field with the operating field, E<sub>w</sub>&middot;E<sub>0</sub>, on a signed logarithmic color scale. It is the current induced on that cathode by a positive ion at each point, divided by q&mu;. The rings run guard, anode, cathode from the inside outward.</i></p>

### Testing It Against Data
I extended the calculation from these two slices to seven, running from a crossover through the quarter, three-eighths, and three-quarter points of a cell to its midpoint. Plotted against the arc length $$s$$ between the fired anode and the driven cathode, the product at the anode surface from all seven slices falls on a single Lorentzian, $$\lvert\vec{E}_w\cdot\vec{E}_0\rvert = D_0/[1 + (s/h)^2]$$ with $$h$$ = 5.10 mm, which describes the solved values to 0.5%. One curve therefore serves every cell.

Taking the cathode-to-anode signal ratio $$Q_c/Q_a$$ to be proportional to this product, with one scale factor fixed at the crossover at z = +19.72 mm, the prediction runs from 0.906 at a crossover to 0.539 at mid-cell. I compared it with 9850 crossover events from α-source runs. The position of each event was projected to the anode radius from the silicon hit and the known source position, with no cell assignment or charge-sharing model applied to the data. The measured cathode charge fraction oscillates along z with the period and phase the weighting fields predict, in every cell the source illuminates, and the single scale factor is the only free parameter.

The measured modulation is shallower than predicted, and most of the difference comes from the reference position. The first harmonic of the data is 0.65 of the prediction, which a Gaussian smearing of σ = 5.9 mm in the projected position would fully account for. Using the crossover-reconstructed positions of the two-cathode events instead, the measured crossover-to-midpoint ratio in $$Q_c/Q_a$$ is 1.37, against a predicted 1.63. The remainder has not yet been separated among the residual position resolution, events assigned to the wrong cell, the cathode threshold, and the integration of the induced current along the ion drift, which this starting-current model leaves out.

<img src="/images/twine-cfrac-vs-z-pred.png" alt="Two-dimensional histogram of cathode charge fraction, 0 to 0.75, against PC z from minus 80 to 80 millimeters. An upper band near 0.45 dips toward 0.35 near minus 40, 0 and plus 40 millimeters and rises near minus 20, plus 20 and plus 60 millimeters, following a red line through open circles, with a separate short band near 0.1 and dotted vertical lines at the crossovers." width="650" style="display: block; margin: 0 auto;">
<p align="center"><i>Cathode charge fraction, Q<sub>c</sub>/(Q<sub>a</sub> + Q<sub>c</sub>), against position for 9850 crossover events from &alpha;-source runs in the SX3 barrel. Dotted lines mark the crossovers. Open circles are the weighting-field prediction at the solved slices, and the solid line is the Lorentzian through them, scaled to the data by one factor at the z = +19.72 mm crossover. The lower band near 0.1 is a partially integrated population from the <sup>17</sup>F source runs.</i></p>

<img src="/images/twine-charge-ratio-vs-z-pred.png" alt="Two-dimensional histogram of the cathode-to-anode signal ratio, 0 to 1.5, against PC z from minus 80 to 80 millimeters. An upper band near 0.8 dips toward 0.55 near minus 40, 0 and plus 40 millimeters and rises to about 0.9 near minus 20 and plus 20 millimeters, following a red line through open circles, with a separate low band near 0.1 and dotted vertical lines at the crossovers." width="650" style="display: block; margin: 0 auto;">
<p align="center"><i>The same comparison in the ratio Q<sub>c</sub>/Q<sub>a</sub>, the quantity the weighting field predicts directly.</i></p>

### What's Next
The calculation gives the induced current where the ions start their drift, not the integrated pulse amplitude. The next step is to couple these weighting fields to Garfield++ drift and avalanche simulation and integrate the induced current along the actual ion trajectories. That would predict the cathode amplitude and how it depends on the gas, the bias, and the shaping, so the operating point of the next campaign can be chosen by calculation and then confirmed with the source.

The field-solving pipeline itself is described on the [simulations page](/portfolio/detector-simulations/), and the detector's performance in beam on the [ANASEN upgrade page](/portfolio/anasen-upgrade/). The full account is in my [dissertation](/publication/2026-phd-dissertation).
