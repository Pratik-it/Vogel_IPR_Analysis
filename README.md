# Well Performance & Nodal Analysis Toolkit

A robust Python implementation for comprehensive reservoir and production engineering analysis. This tool generates Vogel's Inflow Performance Relationship (IPR) curves and couples them with Vertical Lift Performance (VLP) profiles using the Poettmann and Carpenter multiphase flow method to perform full Nodal Analysis. It is designed to evaluate bottomhole flowing pressures, predict production rates, and optimize artificial lift or tubing string selection.

## Features

*   **Dual Reservoir Support**: Rigorously handles both saturated ($P \le P_b$) and undersaturated ($P > P_b$) reservoir conditions.
*   **Multiphase VLP Calculation**: Implements the Poettmann and Carpenter correlation to estimate pressure traverses and fluid lifting capacity within the production tubing.
*   **Automated Nodal Analysis**: Utilizes `scipy.optimize.fsolve` to programmatically calculate the exact intersection (operating point) between the IPR and VLP curves.
*   **Tubing Sensitivity**: Evaluates and plots Tubing Performance Relationship (TPR) curves for multiple tubing sizes (e.g., 1.90-inch, 2.375-inch, and 2.875-inch) to aid in production equipment optimization.
*   **Skin Effect Simulation**: Dynamic visualization of how changes in the skin factor (formation damage or well stimulation) impact the IPR curve and shift the operating conditions.

## Theoretical Background

Standard well performance evaluation requires balancing the reservoir's ability to deliver fluid (IPR) with the piping system's lifting capacity (VLP/TPR). This toolkit integrates Vogel's empirical IPR equation for solution-gas drive reservoirs with robust vertical lift multiphase flow calculations. This comprehensive approach is crucial for:
*   Production optimization and debottlenecking
*   Tubing size and completion equipment selection
*   Reservoir surveillance and dynamic performance prediction
*   Well productivity and drawdown analysis

## Key Equations

**Productivity Index (Steady-State Radial Flow):**
$$J = \frac{k h}{141.2 B_o \mu (\ln(r_e/r_w) - 0.75 + S)}$$

**Vogel's Equation for Saturated Reservoirs ($P \le P_b$):**
$$q = q_{max} \left[ 1 - 0.2 \left( \frac{P_{wf}}{P_r} \right) - 0.8 \left( \frac{P_{wf}}{P_r} \right)^2 \right]$$

**Undersaturated Reservoirs ($P > P_b$):**
Linear flow above the bubble point:
$$q = J (P_r - P_{wf}) \quad \text{for} \quad P_{wf} \ge P_b$$
Vogel flow below the bubble point:
$$q = q_b + \frac{J P_b}{1.8} \left[ 1 - 0.2 \left( \frac{P_{wf}}{P_b} \right) - 0.8 \left( \frac{P_{wf}}{P_b} \right)^2 \right] \quad \text{for} \quad P_{wf} < P_b$$

## Input Parameters

### Reservoir & IPR Parameters
*   Porosity
*   Permeability ($K$) in mD
*   Pay zone thickness ($h$) in ft
*   Reservoir Pressure ($P_r$) in psi
*   Bubble Point Pressure ($P_b$) in psi
*   Formation Volume Factor ($B_o$) in RB/STB
*   Fluid viscosity ($\mu$) in cP
*   Drainage Area ($A$) in Acres
*   Wellbore radius ($r_w$) in ft
*   Skin Factor ($S$)

### VLP & Wellbore Parameters
*   Wellhead Pressure ($P_{wh}$) in psi
*   Well Depth in ft
*   Tubing Inner Diameter ($d$) in inches
*   Oil API Gravity
*   Gas-Liquid Ratio (GLR) in scf/STB
*   Specific Gravities for Gas, Oil, and Water ($\gamma_g$, $\gamma_o$, $\gamma_w$)
*   Fractional cuts of oil and water ($f_o$, $f_w$)
