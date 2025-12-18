# Spiking Neural Networks (SNN) — Project Notes

## Overview
This project explores how spiking neurons communicate with short electrical pulses instead of continuous activations. It focuses on core building blocks (neuron models, synapses, spike trains) and what that means for learning, simulation, and representation.

## What you can learn
- How simple leaky integrate-and-fire neurons turn input current into spikes.
- How synapses filter spikes over time, creating richer temporal dynamics.
- How information can be encoded either in firing rates or precise spike timing.
- Why training SNNs is harder than standard neural nets and which workarounds exist.

## Training approaches (high level)
- Local plasticity rules such as spike-timing–dependent plasticity (STDP).
- Surrogate-gradient methods that let you backpropagate through spike events.
- Task-specific rules (e.g., Tempotron/SpikeProp) that emphasize spike timing.

## Using the notebooks
- `final.ipynb` and `final copy.ipynb` simulate different neuron/synapse settings, visualize spike trains, and compare simple training strategies.
- Try changing thresholds, decay constants, or input spike patterns to see how coding style (rate vs. timing) affects behavior.

## References
- Dayan & Abbott, "Theoretical Neuroscience"
- Gerstner & Kistler, "Spiking Neuron Models"
- Bellec et al., surrogate gradient methods for SNNs
