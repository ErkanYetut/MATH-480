# MATH-480 ODE Solver Project - Numerical Methods for Ordinary Differential Equations
## Numerical Methods for Ordinary Differential Equations

---

## 📌 Overview

This project implements and compares numerical methods for solving Ordinary Differential Equations (ODEs). Methods range from first-order to third-order accuracy, applied to linear test problems and nonlinear pendulum equation.

**Methods Implemented:**
- Forward Euler (1st order)
- RK2 / Euler's Halfstep (2nd order)
- RK3 (3rd order)
- AB2 / Adams-Bashforth (2nd order, multistep)

---

## 📁 Project Structure
---

## Exercise 1: Forward Euler Method

**What we did:** Implemented Euler's explicit method and solved `dy/dx = -y - 3x, y(0)=1` from x=0 to 2 with varying step sizes.

**Key Findings:**
- Error ratio ≈ 2 when step size is halved
- Estimated order p = 1
- Euler is **1st order accurate (O(h))**

**Observations:**
- Small step sizes needed for reasonable accuracy
- Error accumulates linearly with step size
- Simple but inefficient for high accuracy requirements

---

## Exercise 2: RK2 Method (Euler's Halfstep)

**What we did:** Implemented 2nd order Runge-Kutta method and compared with Euler.

**Key Findings:**
- Error ratio ≈ 4 when step size is halved
- Estimated order p = 2
- RK2 is **2nd order accurate (O(h²))**

**Comparison with Euler:**
- RK2 achieves same accuracy as Euler with 10× fewer steps
- Euler needs ~160 steps to match RK2 at 10 steps
- Euler needs ~125,000 steps to match RK2 at 320 steps (392× more)

**Observations:**
- Converges much faster than Euler
- Better energy preservation
- Single-step method (only needs current point)

---

## Exercise 3: RK3 Method

**What we did:** Implemented 3rd order Runge-Kutta method.

**Key Findings:**
- Error ratio ≈ 8 when step size is halved
- Estimated order p = 3
- RK3 is **3rd order accurate (O(h³))**

**Comparison with RK2:**
- RK3 needs only 10 steps to achieve what RK2 needs 80 steps for
- RK3 needs ~18,000 steps to match what RK2 needs 320 steps for

**Observations:**
- Extremely fast convergence
- Excellent for high-precision requirements
- More function evaluations per step (3 per step)

---

## Exercise 4: System of ODEs

**What we did:** Extended RK3 to solve systems of ODEs.

**Problem:** 
- `dy0/dx = -y0 - 3x, y0(0)=5`
- `dy1/dx = -y1 - 3x, y1(0)=6`

**Key Findings:**
- System solution matched two independent scalar solutions exactly
- Norm of differences was near zero

**Observations:**
- System solver works identically to scalar solver
- Each equation evolves independently
- Matrix/vector implementation works seamlessly

---

## Exercise 5: Pendulum ODE

**What we did:** Solved nonlinear pendulum equation `d²θ/dx² + 3·sin(θ)=0`, `θ(0)=1`, `θ'(0)=0` using Euler (1000, 10000 steps) and RK3 (100 steps).

**Key Findings:**
- **Euler (1000 steps):** Amplitude grows beyond ±1, unstable, energy increases
- **Euler (10000 steps):** Better amplitude preservation, still small energy drift
- **RK3 (100 steps):** Perfect amplitude within [-1,1], excellent energy conservation

**Observations:**
- Euler fails to conserve energy for long-time integration
- Higher-order methods essential for oscillatory systems
- RK3 with 100 steps outperforms Euler with 10000 steps

---

## Exercise 6: Step Size Comparison

**What we did:** Solved `dy/dx = -y - 3x, y(0)=20` from x=0 to 20 using Euler with different step sizes (n = 40, 30, 20, 15, 12, 10).

**Key Findings:**
- Smaller step size (more steps) → more accurate solution
- Larger step size (fewer steps) → larger error accumulation
- All solutions plotted on same figure with exact solution

**Observations:**
- Error accumulates over long integration intervals
- Step size choice critically affects accuracy
- Trade-off between computational cost and accuracy

---

## Exercise 7: Adams-Bashforth 2nd Order (AB2)

**What we did:** Implemented AB2 multistep method and compared with RK2.

**Key Findings:**
- Error ratio ≈ 4 when step size is halved → 2nd order accurate (p=2)
- Same order as RK2 but more efficient

**Efficiency Comparison:**
- For 100 steps, AB2 needs 101 function evaluations
- RK2 would need 200 evaluations for same steps
- AB2 is about twice as efficient (same accuracy, half the cost)

**Observations:**
- AB2 is a multistep method (needs previous derivative values)
- `fValue` and `fValueold` store current and previous derivatives
- First step uses RK2 for initialization
- More efficient than RK2 for long-time integration

---

## 📊 Overall Conclusions

| Method | Order | Accuracy | Efficiency | Best For |
|--------|-------|----------|------------|----------|
| Euler | 1 | Low | High (1 eval/step) | Quick estimates, small intervals |
| RK2 | 2 | Medium | Medium (2 evals/step) | General purpose, moderate accuracy |
| RK3 | 3 | High | Low (3 evals/step) | High precision, short intervals |
| AB2 | 2 | Medium | High (1 eval/step after first) | Long-time integration, efficiency |

---

## 🔑 Key Takeaways

1. **Higher order means faster convergence.** RK3 needs far fewer steps than Euler for same accuracy.

2. **Energy conservation matters.** For pendulum problem, Euler fails physically while RK3 succeeds.

3. **Multistep methods (AB2) are more efficient** than single-step methods of same order.

4. **Step size choice is critical.** Too large → inaccurate; too small → expensive.

5. **No single best method.** Choice depends on accuracy requirements, problem stiffness, and available computational resources.

---

## 🚀 How to Run

```bash
python exercise1.py
python exercise2.py
python exercise3.py
python exercise4.py
python exercise5.py
python exercise6.py
python exercise7.py
