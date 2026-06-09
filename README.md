# Honeycomb-Serpentine Moiré Polarization Interferometer
### Axion-like Phase Field Dynamics under Current-Induced Symmetry Breaking

**Author:** Chur Chin, MD  
**Affiliation:** Department of Family Medicine, Dong-eui Medical Center, Busan, Republic of Korea  
**Repository type:** DIY experimental optics / independent research  

---

## Overview

This repository documents an ongoing experimental series investigating coupled optical mode dynamics in a **honeycomb-serpentine Moiré polarization interferometer** driven by a rotating polarizer and a DC-biased copper wire channel. The central observation is that the introduction of current-carrying copper wire into the optical path produces reproducible, symmetry-broken mode structures that are interpreted within an **axion-like effective phase field** framework.

---

## Experimental Setup

| Component | Description |
|-----------|-------------|
| Optical structure | Honeycomb-serpentine Moiré film stack |
| Light source | Red laser (~650 nm) |
| Polarizer | Rotating input privacy film (manual / motor-driven) |
| Motor | N20 DC micro-motor |
| Electrical channel | Copper wire inserted into serpentine channel |
| Power supply | DC voltage sweep (0 V → variable); battery holder |
| Camera | Smartphone (1280×720, ~30 fps) |
| Projection screen | Diffuse screen; dots observed in far field |

---

## Key Observables

### 1. Dot Pattern Morphology
- **Baseline (no wire):** Diffuse, symmetric dot distribution; low spatial spread
- **Wire-present condition:** Emergence of a bright **central mode** (fundamental) surrounded by **satellite modes** (higher-order); 4–5× increase in dot count and spatial spread
- **Voltage sweep:** Monotonic and non-monotonic changes in mode structure depending on contact resistance stability

### 2. ON/OFF Oscillation Cycle
Video analysis of the 8–9 minute recording revealed a strikingly regular modulation:

| Parameter | Value |
|-----------|-------|
| Mean ON/OFF period | **2.28 s ± 0.01 s** |
| Frequency | **0.439 Hz** |
| Temporal jitter (σ) | < 10 ms |

The sub-10 ms jitter rules out a simple electrical harmonic artifact. The periodicity is locked to the polarizer rotation cadence, with the copper wire current providing phase stabilization.

### 3. Radial Dynamics ("Rocket" and Satellite Ejection)
- **Minutes 0–3:** Dot cluster concentrated near center
- **Minutes 3–5:** Central mode brightens sharply; intensity increase ~ ×2–3
- **Minutes 5+:** Streak-like radial emission ("rocket") from central mode; satellite dots displaced outward in discrete jumps; pattern repeats

This radial expansion sequence — **central brightening → streak emission → satellite redistribution** — recurs with the 2.28 s periodicity and is interpreted as periodic energy transfer between coupled optical modes.

### 4. Symmetry Breaking and Mode Coexistence
The copper wire current breaks the rotational symmetry of the Moiré lattice, enabling simultaneous occupation of:
- A **strong-coupling-like regime** (central fundamental mode, high intensity, narrow spatial extent)
- A **weak-coupling-like regime** (peripheral satellite modes, lower intensity, broader distribution)

The two regimes exchange energy via the symmetry-broken channel, producing the observed discrete jumps analogous to mode hopping in coupled resonator systems.

---

## Theoretical Framework

### Axion-like Effective Phase Field

The optical-electrical state of the system is modeled as an effective phase field:

$$\theta_{\text{eff}}(\mathbf{r}, V) = \theta_{\text{opt}}(\mathbf{r}) + \theta_{\text{elec}}(\mathbf{r}, V)$$

where:
- $\theta_{\text{opt}}$ encodes the Moiré superlattice interference phase (twist-angle dependent)
- $\theta_{\text{elec}}$ is the electrically-induced phase modulation from the current-carrying wire

The current $I$ in the copper wire acts as a **symmetry-breaking bias** that shifts the system from a $C_6$-symmetric Moiré ground state into a lower-symmetry configuration. The resulting dynamics are analogous to an axion field responding to a background electromagnetic potential.

### Mode Coupling Analogy

The central mode and satellite modes are treated as coupled oscillators with effective coupling strength $g_{\text{eff}}(V)$:

$$H_{\text{eff}} = \omega_0 a^\dagger a + \sum_k \omega_k b_k^\dagger b_k + g_{\text{eff}}(V)(a^\dagger b_k + \text{h.c.})$$

- When $g_{\text{eff}} \gg |\omega_0 - \omega_k|$: strong-coupling-like energy localization at center
- When $g_{\text{eff}} \lesssim |\omega_0 - \omega_k|$: weak-coupling-like satellite population

The voltage-dependent crossover between these regimes produces the observed radial redistribution events.

### Tunneling-like Mode Hopping

The discrete, abrupt radial jumps of satellite dots — appearing suddenly rather than drifting continuously — are consistent with a **classical analog of quantum tunneling**: mode energy overcomes an effective potential barrier set by the interference landscape, producing sudden reconfiguration of the far-field dot pattern. This is macroscopic mode hopping, not true quantum tunneling, but the visual and dynamical analogy is striking and scientifically meaningful as a classical-quantum correspondence.

---

## Artifact Exclusion

A critical re-evaluation of earlier results identified a potential **contact resistance artifact** at the battery holder–copper wire junction, which may have contributed to FFT doublet features previously interpreted as Rabi-like mode splitting. Subsequent steps:

- [x] Identified unstable contact as source of spurious FFT doublet
- [x] Battery stabilization confirmed: harmonic-like oscillation persists after voltage stabilization → not a simple electrical harmonic
- [ ] Proper soldering of copper wire to aluminum tape (in progress)
- [ ] 0 V control recording (wire present, no current) — planned next session

---

## Experimental Conditions Comparison

| Condition | Dot Count | Spatial Spread | FFT Modes | Notes |
|-----------|-----------|----------------|-----------|-------|
| No wire, film OFF | Low | Narrow | Baseline | Reference |
| No wire, film ON | Low–Med | Moderate | Baseline | Polarizer effect only |
| Wire present, 0 V | TBD | TBD | TBD | **Planned** |
| Wire present, DC on | High (~4–5×) | Wide | New modes appear | Main experimental condition |
| Voltage sweep | Variable | Variable | Mode-dependent | Ongoing |

---

## Video Analysis Summary

Raw footage (~8–9 min total) was compressed with FFmpeg (H.264, CRF 28) for archiving. Frame-by-frame analysis was performed with OpenCV (Python). Key metrics extracted per frame:

- Bright pixel count (threshold = 160)
- Connected component detection (min area = 3 px)
- Radial distance of each dot from pattern center
- ON/OFF transition timestamps (Δ > 50 px threshold)

FFT of the ON/OFF time series confirms a dominant frequency at **0.439 Hz** with harmonic content, distinct from the electrical supply frequency.

---

## Repository Structure

```
/
├── README.md                  # This file
├── videos/
│   ├── raw/                   # Original recordings (compressed)
│   └── annotated/             # Labeled key frames
├── analysis/
│   ├── frame_analysis.py      # OpenCV dot detection script
│   ├── fft_analysis.py        # Spectral analysis
│   └── results/               # CSV outputs, plots
└── notes/
    └── experimental_log.md    # Session-by-session observations
```

---

## Status & Next Steps

- [x] Reproducible coupled-mode dynamics confirmed across multiple sessions
- [x] 2.28 s periodicity identified and quantified
- [x] Axion-like phase field framework developed
- [x] Contact resistance artifact identified and flagged
- [ ] Soldering fix → repeat voltage sweep
- [ ] 0 V control video (no current, wire present)
- [ ] Systematic dot-count vs. voltage curve
- [ ] Manuscript preparation (target: *Results in Physics* or *Optics Letters*)

---

## Notes on Terminology

Following reviewer guidance and internal discussion, the term **"strong coupling"** is avoided in its strict cavity-QED sense. Instead, this work uses:
- *"strong-coupling-like regime"* or *"high-coupling regime"* for the central mode behavior
- *"coherent cavity-mediated mode exchange"* for the inter-mode energy transfer
- *"classical analog of tunneling-like mode hopping"* for the discrete radial jump events

---

## License

CC BY 4.0 — Free to use with attribution.

---

*Last updated: June 2026*
