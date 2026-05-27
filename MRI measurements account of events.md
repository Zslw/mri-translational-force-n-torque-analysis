MRI Measurement Session — Dec 20, 2025 — 3T — Translational Force Pilot

We had multiple goals for the session during the day as we were clear to experiment while no patient was being scanned. We used the 3T.
First, getting the map for the magnetic field along the z-axis or patient couch. For that, we positioned the **circular grid fixture** in the patient table. We learned the controls to the couch and how to read the position in mm on 4 digits. We checked for clearance of the fixture to the bore entrance to find out our fixture was a little too big. 

Then, we set up the **computer**, **gaussmeter**, and **gaussmeter probe** in the desk at the control room. For the last one, we pass it through the wall into the MR room. For that we needed the probe cable unentangled  (little waste of time, easily fix by storing the probe in a 8 figure-rope like storage). There we decided on the range we were gonna cover from the maximum point into the bore where the probe could read and about a meter away. There we took several measurements in sets of 2 (1 going into the bore, 1 going out from the bore) for different coordinates on the grid, which were 00, A3, A6, G6, G3 along the vertical, noting the height of G6 and G3 to match with translational. Then we checked for uniformity by taking the right side D3. For all that, before measurements, we made sure that the fixture was aligned with iso-center using the scanner laser crosshair and a **ruler**. We marked down on the table the position of the fixture. We ended the measurements with 15 tables. 2 for each letter, 4 for center, 1 repeated because of a Labview crash.

Later, we set up the **translational fixture**, we noted some slow-downs. First, the string is kind of hard to knot properly to the baskets or different baskets, so an easy fix is to have a set of strings with baskets and subjects ready to add to the pole. So next steps should include printing more **baskets** and cutting about **1.3 meters of string** for each basket. All which should be already weighted and labeled. Then for the procedure, we aligned the translational fixture and the small basket to iso-center, using the lasers and marking with tape its position, we also measured the distance from the couch edge to the start of our fixture base. so we can locate the basket at equilibrium. The magnetic force was more visible than expected which meant the 0 position was only found outside the MR room or without the subject (only basket on string). That added some time to our measurements by moving the fixture around and trying to "zero it out". 

For translational also, we used a **Ti sample** for **positive control,** we did 3 trials and noted both distance from iso and the displacement on our fixture. The fixture on the couch was moved in increments of 50 mm close the bore and 100 mm on the further edge. Then we did the same thing for the **epicardial lead.** It is important to note that the Ti was coiled intro a spring like shaped (not to packed) and was position in horizontal so its length was along the z axis of the MRI and its diameter perpendicular to the field. The lead, in contrast, was coiled tight vertical to the field, because of its thickness it was easier this way and more packed. Because of the particular shapes in these configurations, we decided to try with straight pieces of both Ti and **316L stainless steel** and followed the same procedure. We have 8 tables for this experiment, 3 for Ti, 3 for epicardial lead, 1 for Ti straight, 1 for 316L.

While that was going on, we set up the extra equipment for the torque experiment, that is ensemble the **torque fixture** with the **sensor**
the **lever arm**, which serves as “baskets” and apply the same criteria that we should make more of the same size lever arms with samples of metals attached to them beforehand. The **circuit and DAQ** were set up and connected to the side of the computer in the MRI control room. Connections include **power to DAQ**, **5V from DAQ to circuit**, **signal reading** (plus and minus), **DAQ to USB** and a **10m cable from sensor to circuit**. The 10m cable was extended through the wall in the same way the probe was. Once everything was connected, we tested the sensor input by gently pushing against it. From there, we positioned the fixture and aligned it to iso-center, marking its position with tape. We tried using rod samples of non-magnetic stainless steel and titanium without readings. The 316L was too short or thin to feel torque on it. So, more of this material is needed to further test. At the end, we couldn't measure for torque.

Another thing to note is that we could measure all 3 things at the same time. By putting the torque first then the translational then the grid in the MRI couch, we can potentially take all measurements in a single couch run. However, there are some issues with that, first we needed to make sure the field mapping reaches the same points the torque does. Second, a single computer with Labview running will stall by receiving the inputs from both the Gaussmeter and the DAQ since both are set to read from USB. 


---
Packing list as we go

We packed for 3 experiments, Magnetic field mapping, Translational Force Assessment, Torque Test.

We needed the 3 main fixtures along with the recording computational set. For each experiment, we set 3 plastic boxes with things we could have needed.

For recording, a laptop for mapping and torque, a DAQ for torque, and a notebook and paper for translational and notes on the rest.

For mapping, the main fixture was a single piece. Its box included, gaussmeter and probe with its cable. Cable from gaussmeter to USB, calibration record and info from the manufacturer along with a couple replacement batteries.

For translational, main fixture, a couple of pieces for that. Base and pole is one, set of 2 adjustable rings one for string on top one for ruler on bottom, with their respective nylon screws. Additionally, 2 kydex rulers for translational displacement measure. string. And basket. We brought all basket attempts but only the last one was used (it was the best). We also brought tape, duct tape, masking tape, all surface tape (painter tape), double-sided tape. Materials to test, Ti and 316L, the epicardial lead, a baseball with a staple inside of it (it didn't do anything sadly) 

For torque, the main fixture includes, a base, a nylon screw that attaches base to pole, pole, ring to attach sensor to pole. A ceramic bearing with plastic piece to hold a lever arm with sample and the built Aluminum sensor. Along with fixture, from the sensor, a 10m cable a circuit in an antistatic bag, a DAQ with its connections. A set of 16 rods, Ti and Stainless steel to test. Some tweezers to bend wire if needed. A set of different lengths of lever arms. A small blue screwdriver for adjusting circuit potentiometers. Having an extra ceramic bearing with base would be good as well.

---

# Master Packing List — MRI Measurement Session (3T)

## A. Shared / General Items (All Experiments)
- [ ] Laptop (LabVIEW installed)
- [ ] Power supply / charger for laptop
- [ ] Notebook + loose paper (manual logging, sketches, backup)
- [ ] Pens / pencils
- [ ] Ruler (for laser alignment & couch referencing)
- [ ] Painter’s tape (surface marking)
- [ ] Masking tape
- [ ] Duct tape
- [ ] Double-sided tape
- [ ] USB cables (spares recommended)
- [ ] Labels + marker (for baskets, strings, samples)


---

## B. Magnetic Field Mapping (Gauss Mapping)

### Primary Fixture
- [ ] Circular grid fixture (single-piece)

### Instrumentation
- [ ] Gaussmeter
- [ ] Gaussmeter probe
- [ ] Probe cable (sufficient length for wall pass-through)
- [ ] USB cable (gaussmeter → laptop)

### Accessories & Documentation
- [ ] Manufacturer calibration certificate / records
- [ ] Replacement batteries for gaussmeter
- [ ] Cable storage solution (figure-8 rope wrap)


---

## C. Translational Force Assessment

### Primary Fixture
- [ ] Translational force base
- [ ] Vertical pole
- [ ] Adjustable ring (top) — string attachment
- [ ] Adjustable ring (bottom) — ruler attachment
- [ ] Nylon screws (for both rings)

### Measurement Tools
- [ ] Kydex rulers ×2 (displacement measurement)
- [ ] Measuring tape or ruler (couch edge → fixture base distance)

### Suspension System
- [ ] Pre-cut strings (~1.3 m each)
- [ ] Printed baskets (multiple, identical)
- [ ] Baskets pre-weighted and labeled
- [ ] Extra strings pre-knotted to baskets (preferred)

### Test Articles
- [ ] Titanium sample (coiled)
- [ ] Titanium sample (straight)
- [ ] Epicardial lead
- [ ] 316L stainless steel (straight)
- [ ] Additional test objects (optional)


---

## D. Torque Test Setup

### Primary Fixture
- [ ] Base
- [ ] Pole
- [ ] Nylon screw (base ↔ pole)
- [ ] Ring (sensor attachment)
- [ ] Ceramic bearing
- [ ] Plastic bearing holder
- [ ] Lever arm(s)

### Sensor & Electronics
- [ ] Torque sensor
- [ ] 10 m sensor cable (wall pass-through)
- [ ] Circuit board (antistatic bag)
- [ ] DAQ
- [ ] DAQ power supply
- [ ] USB cable (DAQ → laptop)

### Connections Checklist
- [ ] Power → DAQ
- [ ] 5 V from DAQ → circuit
- [ ] Signal ± from circuit → DAQ
- [ ] Sensor → 10 m cable → circuit

### Samples
- [ ] Titanium rods (various lengths)
- [ ] Stainless steel rods (various lengths)
- [ ] 316L stainless steel (larger / thicker pieces)
- [ ] Epicardial leads

### Tools & Extras
- [ ] Tweezers (wire/sample adjustment)
- [ ] Small screwdriver (potentiometer tuning)
- [ ] Multiple lever arms (different lengths)
- [ ] Multiple lever arms (idential)
- [ ] Spare ceramic bearing + base

