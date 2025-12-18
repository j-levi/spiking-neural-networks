# Spiking Neural Networks (SNN) — Mathematical Notes

## Overview
This project explores spiking neuron models, dynamics, and training approaches for Spiking Neural Networks (SNNs). Emphasis is on the mathematical models: Leaky Integrate-and-Fire (LIF), spike generation, synaptic dynamics, and learning rules.

## Leaky Integrate-and-Fire (LIF) Neuron
The LIF neuron models membrane potential V(t) with a first-order RC circuit:
$$
C_m \frac{dV}{dt} = -g_L (V(t) - E_L) + I(t),
$$
where C_m is membrane capacitance, g_L leak conductance, E_L resting potential, and I(t) synaptic/current input. When V(t) reaches threshold V_{th} the neuron emits a spike and V is reset to V_{reset} (and possibly held during a refractory period).

Discrete-time Euler approximation (Δt step):
$$
V_{t+1} = V_t + \frac{\Delta t}{C_m} [-g_L (V_t - E_L) + I_t].
$$
A common normalized form uses a decay factor α ∈ (0,1):
$$
V_{t+1} = α V_t + (1-α) I_t, \quad \text{emit spike if } V_{t+1} \ge V_{th}.
$$

## Synaptic Currents and Filtering
Synaptic currents are often modeled with exponential kernels:
$$
I(t) = \sum_{f} w_f \cdot \exp\left(-\frac{t - t_f}{\tau_s}\right) H(t - t_f),
$$
where t_f are presynaptic spike times, w_f synaptic weights, τ_s synaptic time constant, and H is the Heaviside step.

## Learning in SNNs
Training SNNs is more challenging due to non-differentiable spike events. Approaches include:
- Spike-Timing-Dependent Plasticity (STDP): a local unsupervised rule where synaptic change depends on relative spike timing Δt = t_post - t_pre; typical update:
$$
\Delta w = \begin{cases} A_+ e^{-\Delta t/\tau_+}, & \Delta t > 0 \\ -A_- e^{\Delta t/\tau_-}, & \Delta t < 0 \end{cases}
$$
- Surrogate gradients: approximate the nondifferentiable spike function with a smooth surrogate during backpropagation-through-time (BPTT).
- Tempotron, SpikeProp: task-specific supervised rules adapting weights based on spike timings.

## Rate vs. Temporal Coding
- Rate coding: firing rate over a window carries information; SNN can be approximated by rate-based networks for analysis.
- Temporal coding: precise spike times encode information; requires timing-sensitive learning rules like STDP or temporal surrogates.

## Analysis Tools
- Mean-field approximations and population dynamics for large networks.
- Fokker–Planck and diffusion approximations for stochastic inputs.

## References
- Dayan & Abbott, "Theoretical Neuroscience." 
- Gerstner & Kistler, "Spiking Neuron Models." 
- Bellec et al., surrogate gradient methods for SNNs.

## Files
See notebooks final.ipynb and final copy.ipynb for simulations and experiments.
