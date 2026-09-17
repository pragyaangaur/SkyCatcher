# SkyCatcher

SkyCatcher is a catalytic oxidation reactor designed for industrial sulfur dioxide (SO₂) capture and conversion into sulfuric acid (H₂SO₄). The system is currently patent pending and has received external research grants. This repository focuses on modeling and analysis, not hardware implementation.

## Overview

This repository contains computational models used to analyze the kinetics and thermodynamic limits of SO₂ oxidation, and to identify optimal operating conditions for reactor performance.

## Models

### 1. SO₂ Conversion Efficiency

**What it does:**  
Models SO₂ conversion as a function of temperature by combining reaction kinetics with thermodynamic equilibrium limits.

**Core Idea:**  
Interplay between Arrhenius-driven reaction rates and equilibrium constraints in catalytic oxidation.

**Approach:**  
	•	First-order plug flow reaction model  
	•	Arrhenius-based rate dependence on temperature  
	•	Equilibrium ceiling imposed by reaction thermodynamics  
	•	Computation of effective conversion and H₂SO₄ yield  

**How it Works:**  
The model calculates kinetic conversion across a temperature range and overlays it with the thermodynamic equilibrium limit. The effective conversion is determined by the lower of the two, capturing the transition from kinetic control to equilibrium limitation.

**Key Result:**  
Maximum theoretical conversion: 88.6% at ~745 K  

**Stack:** Wolfram Mathematica

<p align="center">
<img src="Assets/Efficiency-Plot-1.jpeg" width="650">
<img src="Assets/Efficiency-Plot-2.jpeg" width="650"></p>

**Technical Note:** A formal write-up of the modeling assumptions, derivations, and results is available in Technical-Note.tex  
This document provides a deeper treatment of the reaction kinetics, thermodynamic constraints, and modeling framework used in this repository.

### 2. Temperature-Pressure Conversion Map

**What it does:**  
Extends the conversion model to map reactor performance across both temperature and pressure.

**Core Idea:**  
Optimal reactor performance exists as a region in temperature–pressure space, not a single point.

**Approach:**  
	•	Combine Arrhenius kinetics with pressure-dependent equilibrium  
	•	Evaluate conversion across a grid of temperature (400–900 K) and pressure (0.5–10 atm)  
	•	Generate a 2D phase map of conversion efficiency  

**How it Works:**  
For each (T, P) pair, the model computes kinetic and equilibrium limits and determines the achievable conversion. The resulting map highlights regions where performance is maximized and shows the shift from kinetic limitation to equilibrium control.

**Key Insight:**  
Reactor optimization requires navigating a trade-off surface rather than selecting a single operating condition.

**Stack:** Python, NumPy, Matplotlib

<p align="center">
<img src="Assets/Temperature-Pressure-Conversion-Map.png" width="650"></p>
