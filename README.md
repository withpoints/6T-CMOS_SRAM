# 6T CMOS SRAM Bitcell Design and Verification

This repository documents the **design, layout, and post-layout verification of a 6T CMOS SRAM bitcell** implemented using **Cadence Virtuoso**. The project follows a standard full-custom memory design flow and focuses on correctness, verification, and clarity rather than foundry-specific optimization.

---

## 📌 Project Overview

* Full-custom **6T SRAM bitcell** design
* Symmetric, **array-ready layout**
* **DRC clean** and **LVS clean**
* **RCX-based parasitic extraction**
* Functional verification of **hold, write, and read** operations using transient simulation

This project is intended to demonstrate understanding of SRAM fundamentals and physical design verification flow.

---

## 🛠 Tools Used

* Cadence Virtuoso (Schematic & Layout)
* Assura (DRC, LVS, RCX)
* ADE / ViVA (Transient Simulation)

---

## 📐 Design Description

The 6T SRAM bitcell consists of:

* Two cross-coupled CMOS inverters for data storage
* Two NMOS access transistors controlled by the wordline (WL)
* Differential bitlines (BL, BLB) for read and write operations

The layout is designed with left–right symmetry and shared diffusion to ensure matching and enable easy tiling in an SRAM array.

---

## 🔍 Physical Verification

### DRC (Design Rule Check)

* Layout verified against technology rules
* **0 DRC violations**
* Result available in: `verification/drc/drc_clean.png`

### LVS (Layout Versus Schematic)

* Schematic and layout connectivity matched
* **0 net, device, pin, or parameter mismatches**
* Assura-generated VNL netlist included for reference
* Results available in: `verification/lvs/`

### Static Noise Margin (SNM)
- Hold SNM evaluated using butterfly curve analysis (`verification/snm/`)
---

## 🧪 Post-Layout Verification (RCX)

* RCX-based parasitic extraction performed to include interconnect resistance and capacitance
* Extracted view used for simulation via switch-view list

### Functional Verification

The following operating modes were verified using transient simulation:

* **Hold**: With WL = 0, stored data remains stable over time
* **Write**: Correct overwrite of stored data when WL is asserted
* **Read**: Differential bitline behavior observed without disturbing stored data

  * Read ‘1’: BL > BLB
  * Read ‘0’: BLB > BL

Waveforms are available in the `simulation/` directory.

---

## 📂 Repository Structure

```
6T-CMOS-SRAM/
│
├── README.md
├── schematic/
│   └── 6t_sram_schematic.png
├── layout/
│   └── 6t_sram_layout.png
├── verification/
│   ├── drc/
│      └── drc_clean.png
│   └── lvs/
│       ├── lvs_clean.png
│       └── 6t_sram_assura_lvs.vnl
│   ├── snm/
│       └── hold_snm_butterfly.png
├── simulation/
│   ├── hold_waveform.png
│   ├── write_waveform.png
│   ├── read_0_waveform.png
│   └── read_1_waveform.png
└── notes/
    └── design_notes.md
```

---

## 📌 Disclaimer

* This project is for **academic and learning purposes only**
* No foundry PDKs, rule decks, or proprietary files are included
* Technology parameters are based on an educational CMOS setup

---

## 🚀 Future Work (Optional)

* SRAM array construction and tiling
* Sense amplifier and precharge circuit integration
* Write/read margin analysis under PVT corners

---

## 👤 Author

Rohit Kumar Maurya

---

*This repository is intended to showcase full-custom VLSI design and verification skills relevant to SRAM and memory-oriented roles.*
