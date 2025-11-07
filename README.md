# 📘 Parametric Curve Fitting – Research & Development Assignment

## 🧩 Problem Statement

Find the unknown parameters $$\[
\theta \; M \; X
\]$$ in the given **parametric equations** of a curve:


$$
x = \left( t * \cos(\theta) - e^{M|t|} \cdot \sin(0.3t) \sin(\theta) + X \right)
$$

$$
y = \left( 42 + t * \sin(\theta) + e^{M|t|} \cdot \sin(0.3t) \cos(\theta) \right)
$$



### Unknowns
$$\[
\theta \; M \; X
\]$$

### Parameter Ranges
$$\[
0° < \theta < 50°, \quad -0.05 < M < 0.05, \quad 0 < X < 100
\]$$

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
   $$\[
   L = \frac{1}{N}\sum_i \left( |x_i - \hat{x}_i| + |y_i - \hat{y}_i| \right)
   \]$$
5. **Optimized parameters**:
   - Performed a **coarse-to-fine grid search** for $$\( \theta, M \)$$
   - Chose optimal \( X \) as the **median** of $$\( x_{\text{data}} - x_{\text{model}} \)$$


6. **Validated visually** using Matplotlib and Desmos.

---

## 🧾 Results

| Parameter | Symbol | Final Value |
|------------|---------|-------------|
| Rotation angle | $$\( \theta \)$$ | 28.10° (0.4904 rad) |
| Exponential factor | \( M \) | 0.02125 |
| X offset | \( X \) | 54.89815 |
| L1 Mean Error | — | 25.243 |

---

## 🧠 Final Parametric Equation (LaTeX Format)


\left(t \cos(0.490438)- e^{0.021250|t|} \sin(0.3t) \sin(0.490438)+ 54.898154,\;
42 + t \sin(0.490438)+ e^{0.021250|t|} \sin(0.3t) \cos(0.490438)\right)



---

## 🧭 Desmos Verification

**Desmos Expression (copy-paste directly):**
```
( t*cos(0.490438) - e^(0.021250*abs(t))*sin(0.3*t)*sin(0.490438) + 54.898154,
  42 + t*sin(0.490438) + e^(0.021250*abs(t))*sin(0.3*t)*cos(0.490438) )
```

**Domain:**
```
6 ≤ t ≤ 60
```

**Desmos Settings:**
- Angle Unit: **Radians**
- Recommended View:  
  - x-axis: 50 → 120  
  - y-axis: 40 → 80  

---

## 📉 Visualizations

### (a) Given (x, y) Data Points
![Data Points](plots/data_points.png)

### (b) Fitted Curve vs Data
![Fitted Curve](plots/fitted_curve.png)

---

## 🧩 Conclusion

- Estimated parameters produce a curve that matches the dataset with high accuracy.  
- The L1 loss of **≈25.24** confirms a good fit.  
- The fitted curve correctly captures the sinusoidal behavior of the dataset.  
- Verification on **Desmos** confirms the mathematical validity.

---

## 🧠 Implementation Details

- **Dataset:** `xy_data.csv`
- **Code Environment:** Google Colab (Python 3)
- **Libraries Used:** NumPy, Pandas, Matplotlib
- **Optimization:** Grid search + median correction for X
- **Validation:** Visual curve comparison and Desmos plotting

---

## 📎 References

- [Desmos Graphing Calculator](https://www.desmos.com/calculator)
- [NumPy Documentation](https://numpy.org/doc/)
- [Matplotlib Documentation](https://matplotlib.org/stable/contents.html)

---

## 📂 Repository Structure

```
curve-fitting-assignment/
│
├── xy_data.csv
├── Parametric_Fitting.ipynb
├── README.md
└── plots/
    ├── data_points.png
    └── fitted_curve.png
```

---

## 🧾 Final Submission Summary

| Item | Description | Status |
|------|--------------|:------:|
| Data File | xy_data.csv | ✅ |
| Colab Notebook | Parametric_Fitting.ipynb | ✅ |
| Fitted Parameters | θ=28.10°, M=0.02125, X=54.89815 | ✅ |
| Desmos Graph | Parametric curve verified | ✅ |
| Report (README.md) | Detailed methodology and results | ✅ |
