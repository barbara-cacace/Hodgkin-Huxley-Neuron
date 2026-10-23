# Hodgkin–Huxley Neuron Model — Brain Modelling

This project implements a **single-compartment Hodgkin–Huxley (HH) neuron model** and uses computational experiments to investigate how voltage-gated sodium and potassium channels generate action potentials and shape neuronal excitability.

The model follows the classical squid giant axon formulation. The notebook implements the membrane equations and gating dynamics in Python, simulates them using the **forward Euler method**, and visualizes the effects of different stimulation protocols and model parameters.

## Model

The membrane is represented as a capacitor coupled to sodium (Na⁺), potassium (K⁺), and leak currents:

\[
C_m \frac{dV}{dt} = I_{\mathrm{ext}} - I_{\mathrm{Na}} - I_{\mathrm{K}} - I_{\mathrm{L}}.
\]

Voltage-dependent gating variables describe sodium activation (`m`), sodium inactivation (`h`), and potassium activation (`n`). Their kinetics determine spike initiation, repolarization, and recovery after an action potential.

## Experiments

The notebook explores:

1. **Current-clamp stimulation:** brief pulses, sustained current steps, and slowly increasing ramps to study individual spikes, repetitive firing, and accommodation.
2. **Firing rate versus injected current (f–I):** estimation of the current threshold for sustained firing and characterization of neuronal excitability.
3. **Refractory periods:** paired-pulse stimulation to investigate recovery after a spike.
4. **Strength–duration relationship:** estimation of pulse thresholds and fitting of the Weiss–Lapicque relation to obtain rheobase and chronaxie.
5. **Voltage clamp:** separation of fast inward sodium and delayed outward potassium currents.
6. **Steady-state I–V relationship:** investigation of ionic-current balance and the resting membrane potential.
7. **Pharmacological channel block:** simulation of sodium-channel inhibition (TTX) and potassium-channel inhibition (TEA).
8. **Temperature scaling:** use of a Q10 factor to examine the effects of faster gating kinetics on spike shape and firing rate.
9. **Phase-plane analysis:** visualization of the voltage–potassium-gate (`V`–`n`) dynamics and their nullclines.

## Main Findings

The simulations reproduce key behaviors of the classical HH neuron. Brief depolarizing pulses can trigger single action potentials, whereas sustained stimulation produces repetitive firing. Slowly rising inputs can lead to **accommodation**, even when their final current exceeds a step stimulus that causes spiking.

The model also shows a finite-frequency onset of sustained firing, refractory recovery between closely spaced pulses, and decreasing threshold current as pulse duration increases. Voltage-clamp experiments distinguish the transient inward Na⁺ current from the delayed outward K⁺ current. Blocking sodium conductance prevents action potentials, while blocking potassium conductance disrupts repolarization and repetitive firing.

With Q10 temperature scaling, faster channel kinetics produce narrower spikes and higher firing rates. Phase-plane analysis connects spike generation and recovery to the interaction between membrane voltage and the slower potassium gating variable.

## How to Run

1. Open `HH_Neuron_BarbaraCacace_Brain_Modelling.ipynb` in Google Colab or Jupyter Notebook.
2. Run the cells in order to define the model, simulate the experiments, and generate the figures.
3. Read the accompanying `BarbaraCacaceHHNeuron_Brain_Modelling.pdf` for a written explanation of the equations, experiments, and findings.

The notebook generates its simulation data directly; **no external dataset is required**. It uses Python with NumPy, Matplotlib, tqdm, and ipywidgets, together with standard-library modules.

## Limitations

This is a deterministic, single-compartment model. It does not include neuronal morphology, synaptic input, stochastic channel behavior, or additional adaptation currents. Temperature effects are represented by uniform Q10 scaling of gating rates. The forward Euler method also requires a sufficiently small time step for numerical accuracy.

## Project Files

- `HH_Neuron_BarbaraCacace_Brain_Modelling.ipynb` — Python implementation, experiments, and visualizations.
- `BarbaraCacaceHHNeuron_Brain_Modelling.pdf` — accompanying project report.

## Technologies

Python · NumPy · Matplotlib · Jupyter Notebook / Google Colab · tqdm · ipywidgets
