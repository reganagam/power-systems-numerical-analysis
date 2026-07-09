# ⚡ Numerical Analysis of ODEs: Voltage Modeling on Lossless Transmission Lines

[cite_start]**Author:** Regan Agam (NIM: 24/PTK/552177/16439) [cite: 349, 743]  
[cite_start]**Program:** Master's in Electrical Engineering, Universitas Gadjah Mada (UGM) [cite: 746]  
[cite_start]**Course:** Komputasi Numeris [cite: 350, 742]

## 📌 Project Overview
[cite_start]Electrical transmission lines are vital infrastructure for transferring power over long distances[cite: 354, 755]. [cite_start]Uncontrolled voltage fluctuations along these lines can lead to equipment damage, power inefficiencies, and total system failures [cite: 357, 751-754]. 

[cite_start]This project models the voltage profile along a lossless transmission line (ignoring resistance and conductance) using Ordinary Differential Equations (ODEs)[cite: 358, 757]. [cite_start]It implements and compares multiple numerical methods to predict voltage behavior, solving both Initial Value Problems (IVP) and Boundary Value Problems (BVP)[cite: 386, 407, 771, 778].

## 🧮 Mathematical Formulation
[cite_start]Starting from the Telegrapher's Equations for a lossless line under steady-state AC conditions, the voltage $V(x)$ and current $I(x)$ are defined as[cite: 362, 763]:

$$\frac{dV(x)}{dx} = -j\omega L \cdot I(x)$$
$$\frac{dI(x)}{dx} = -j\omega C \cdot V(x)$$

[cite_start]By differentiating and substituting, the model is simplified into a second-order harmonic oscillation ODE [cite: 370-376, 766]:

$$\frac{d^{2}V(x)}{dx^{2}} + \beta^{2}V(x) = 0$$

[cite_start]Where $\beta = \omega\sqrt{LC}$ acts as the propagation constant[cite: 377, 765].

## 🛠️ Tech Stack & Methods
* [cite_start]**Language:** Python (`numpy`, `matplotlib`) [cite: 572, 573]
* [cite_start]**IVP Solvers:** Euler Method, Midpoint Method, Runge-Kutta 4th Order (RK4) [cite: 397, 399, 403, 774-776]
* [cite_start]**BVP Solvers:** Finite Difference Method (Matrix Discretization) [cite: 415, 781]

## 📊 Results & Performance Analysis
[cite_start]The simulation was run with a propagation constant $\beta = 2.0$ over a domain $x \in [0, \pi/4]$, testing step sizes ($h$) of 0.1, 0.05, and 0.01 [cite: 424, 784-786].

### 1. Initial Value Problem (IVP) Evaluation
| Step Size ($h$) | Euler Error | Midpoint Error | RK4 Error |
| :---: | :---: | :---: | :---: |
| **0.1** | 0.0970504 | 0.0529708 | 0.000105618 |
| **0.05** | 0.0165971 | 0.0133189 | 0.000006656 |
| **0.01** | 0.0003371 | 0.0005267 | 0.000000011 |

[cite_start]*(Data extracted from simulation at $x = \pi/4$)* [cite: 489, 490, 800-811]

### 2. Boundary Value Problem (BVP) Evaluation
| Step Size ($h$) | Finite Difference Max Error |
| :---: | :---: |
| **0.1** | 0.1459976 |
| **0.05** | 0.1029988 |
| **0.01** | 0.0460187 |

[cite_start]*(Data extracted from maximum absolute error across the domain)* [cite: 557, 558, 830-835]

## 💡 Key Engineering Insights
* [cite_start]**RK4 is the Gold Standard for IVP:** The Runge-Kutta 4th Order method demonstrated vastly superior accuracy[cite: 495, 569, 821]. [cite_start]At a step size of $h = 0.1$, RK4 produced an error of ~0.0001, making it approximately 900 times more accurate than the Euler method[cite: 496, 497, 822, 823].
* [cite_start]**Impact of Step Size ($h$):** Halving the step size in RK4 (from 0.1 to 0.05) reduced the computational error by a factor of 15.8, strictly following $O(h^4)$ theoretical expectations[cite: 497, 500, 819, 823].
* [cite_start]**BVP Discretization Stability:** The Finite Difference method effectively approximated the boundary constraints, with error scaling proportionally to $h^2$ as the step size decreased[cite: 561, 827, 841].

## 🚀 How to Run
1. Clone this repository.
2. Install required packages: `pip install numpy matplotlib`
3. Execute the simulation to generate the comparison plots:
   ```bash
   python main.py
