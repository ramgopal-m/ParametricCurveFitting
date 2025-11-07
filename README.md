# 📘 Parametric Curve Fitting – Research & Development Assignment

## 🧩 Problem Statement

Find the unknown parameters \( \theta, M, X \) in the given **parametric equations** of a curve:

\[
x(t) = t\cos(\theta) - e^{M|t|}\sin(0.3t)\sin(\theta) + X
\]
\[
y(t) = 42 + t\sin(\theta) + e^{M|t|}\sin(0.3t)\cos(\theta)
\]

### Unknowns
\[
\theta, \; M, \; X
\]

### Parameter Ranges
\[
0° < \theta < 50°, \quad -0.05 < M < 0.05, \quad 0 < X < 100
\]

### Parameter ‘t’
\[
6 < t < 60
\]

---

## 📊 Given Data

The file **`xy_data.csv`** contains 1500 points \((x, y)\) that lie on the curve for \( 6 < t < 60 \).

Example rows:
| x | y |
|---|---|
| 88.364456 | 57.784378 |
| 74.283936 | 54.406780 |
| 60.256474 | 46.311462 |
| 82.134370 | 57.717567 |
| 101.036390 | 67.849340 |

---

## 🧮 Methodology

1. **Loaded dataset** using `pandas` and confirmed dimensions (1500 × 2).  
2. **Assumed** \( t \) values uniformly spaced between 6 and 60.  
3. **Defined** the parametric equations for \(x(t)\) and \(y(t)\).  
4. **Computed L1 loss** between actual and predicted points:
   \[
   L = \frac{1}{N}\sum_i \left( |x_i - \hat{x}_i| + |y_i - \hat{y}_i| \right)
   \]
5. **Optimized parameters**:
   - Performed a **coarse-to-fine grid search** for \( \theta, M \)
   - Chose optimal \( X \) as the **median** of \( x_{\text{data}} - x_{\text{model}} \)
6. **Validated visually** using Matplotlib and Desmos.

---

## 🧾 Results

| Parameter | Symbol | Final Value |
|------------|---------|-------------|
| Rotation angle | \( \theta \) | 28.10° (0.4904 rad) |
| Exponential factor | \( M \) | 0.02125 |
| X offset | \( X \) | 54.89815 |
| L1 Mean Error | — | 25.243 |

---

## 🧠 Final Parametric Equation (LaTeX Format)

\[
\left(
t\cos(0.490438)
- e^{0.021250|t|}\sin(0.3t)\sin(0.490438)
+ 54.898154,\;
42 + t\sin(0.490438)
+ e^{0.021250|t|}\sin(0.3t)\cos(0.490438)
\right)
\]

---

## 🧭 Desmos Verification

**Desmos Expression (copy-paste directly):**
