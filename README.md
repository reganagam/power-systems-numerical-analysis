# ⚡ Numerical Analysis of ODEs: Voltage Modeling on Lossless Transmission Lines

**Author:** Regan Agam (NIM: 24/PTK/552177/16439)  
**Program:** Master's in Electrical Engineering, Universitas Gadjah Mada (UGM)  
**Course:** Komputasi Numeris

## 📌 Project Overview
Electrical transmission lines are vital infrastructure for transferring power over long distances. Uncontrolled voltage fluctuations along these lines can lead to equipment damage, power inefficiencies, and total system failures. 

This project models the voltage profile along a lossless transmission line (ignoring resistance and conductance) using Ordinary Differential Equations (ODEs). It implements and compares multiple numerical methods to predict voltage behavior, solving both Initial Value Problems (IVP) and Boundary Value Problems (BVP).

## 🧮 Mathematical Formulation
Starting from the Telegrapher's Equations for a lossless line under steady-state AC conditions, the voltage $V(x)$ and current $I(x)$ are defined as:

$$\frac{dV(x)}{dx}=-j\omega L\cdot I(x)$$
$$\frac{dI(x)}{dx}=-j\omega C\cdot V(x)$$

By differentiating and substituting, the model is simplified into a second-order harmonic oscillation ODE:

$$\frac{d^{2}V(x)}{dx^{2}}+\beta^{2}V(x)=0$$

Where $\beta=\omega\sqrt{LC}$ acts as the propagation constant.

## 🛠️ Tech Stack & Methods
* **Language:** Python (`numpy`, `matplotlib`)
* **IVP Solvers:** Euler Method, Midpoint Method, Runge-Kutta 4th Order (RK4)
* **BVP Solvers:** Finite Difference Method (Matrix Discretization)

## 📊 Results & Performance Analysis
The simulation was run with a propagation constant $\beta=2.0$ over a domain $x\in[0,\pi/4]$, testing step sizes ($h$) of 0.1, 0.05, and 0.01.

### 1. Initial Value Problem (IVP) Evaluation
| Step Size ($h$) | Euler Error | Midpoint Error | RK4 Error |
| :---: | :---: | :---: | :---: |
| **0.1** | 0.0970504 | 0.0529708 | 0.000105618 |
| **0.05** | 0.0165971 | 0.0133189 | 0.000006656 |
| **0.01** | 0.0003371 | 0.0005267 | 0.000000011 |

*(Data extracted from simulation at $x=\pi/4$)*

### 2. Boundary Value Problem (BVP) Evaluation
| Step Size ($h$) | Finite Difference Max Error |
| :---: | :---: |
| **0.1** | 0.1459976 |
| **0.05** | 0.1029988 |
| **0.01** | 0.0460187 |

*(Data extracted from maximum absolute error across the domain)*

## 💡 Key Engineering Insights
* **RK4 is the Gold Standard for IVP:** The Runge-Kutta 4th Order method demonstrated vastly superior accuracy. At a step size of $h=0.1$, RK4 produced an error of ~0.0001, making it approximately 900 times more accurate than the Euler method.
* **Impact of Step Size ($h$):** Halving the step size in RK4 (from 0.1 to 0.05) reduced the computational error by a factor of 15.8, strictly following $O(h^{4})$ theoretical expectations.
* **BVP Discretization Stability:** The Finite Difference method effectively approximated the boundary constraints, with error scaling proportionally to $h^{2}$ as the step size decreased.

## 🚀 How to Run
1. Clone this repository.
2. Install required packages: 
   ```bash
   pip install numpy matplotlib
