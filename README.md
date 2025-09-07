# Vogel's Inflow Performance Relationship (IPR) Analysis

A Python implementation of Vogel's Inflow Performance Relationship (IPR) curve generator for reservoir engineering analysis. This tool calculates and visualizes the relationship between bottomhole flowing pressure and production rate for oil wells.

## Features

- **Dual Reservoir Support**: Handles both saturated (P ≤ Pb) and undersaturated (P > Pb) reservoirs
- **Productivity Index Calculation**: Computes the productivity index (J) using steady-state radial flow equations
- **Interactive Visualization**: Generates professional IPR curves with clear bubble point indication
- **Industry-Standard Formulas**: Implements Vogel's empirical equation and proper reservoir engineering principles
- **User-Friendly Interface**: Simple input format with clear visual outputs

## Theoretical Background

Vogel's IPR method is widely used in petroleum engineering to predict well performance, particularly for solution-gas drive reservoirs. The method provides a relationship between flowing bottomhole pressure (Pwf) and production rate (q), which is crucial for:

- Production optimization
- Equipment selection
- Reservoir performance prediction
- Well productivity analysis

### Key Equations

- **Productivity Index**: J = (kh) / (141.2Bμ(ln(re/rw) - 0.75 + S))
- **Saturated Reservoirs (P ≤ Pb)**: q = Qmax * [1 - 0.2(Pwf/P) - 0.8(Pwf/P)²]
- **Undersaturated Reservoirs (P > Pb)**: 
  - Linear flow: q = J(P - Pwf) for Pwf ≥ Pb
  - Vogel flow: q = Qb + (JPb/1.8) * [1 - 0.2(Pwf/Pb) - 0.8(Pwf/Pb)²] for Pwf < Pb
- **Maximum Flow Rate**: Qmax = (JP)/1.8 (saturated reservoirs)

### Input Parameters
- Porosity
- Permeability (K) mD
- Pay zone thickness (h) Feet
- Reservoir Pressure (P)	psi
- Bubble Point Pressure (Pb)	psi
- Formation Volume Factor (Bo)	RB/STB
- Fluid viscosity (μ)	cP
- Drainage Area (A)	Acres
- Wellbore radius (rw)ft
- Skin Factor (S)
