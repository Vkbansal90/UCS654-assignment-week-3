# Learning Probability Density Function using Roll-Number Based Transformation

## Overview

This assignment focuses on learning a probability density function (PDF) from real air quality data after applying a non-linear transformation that depends on my university roll number. The idea is to see how a small personalized transformation affects the distribution of data and then estimate a suitable PDF for it.

I used NO₂ (Nitrogen Dioxide) values from an air quality dataset as the main variable.

---

## Dataset

Dataset used: India Air Quality Data (Kaggle)

Feature selected: **NO₂ concentration**

### Preprocessing steps

- Removed rows where NO₂ values were missing  
- Converted values to float for calculation  
- Used only the NO₂ column as required  

---

## Step 1 – Transformation

Each NO₂ value \(x\) was transformed using:

z = x + aᵣ sin(bᵣx)

where:

aᵣ = 0.05 × (r mod 7)  
bᵣ = 0.3 × (r mod 5 + 1)

My roll number:

r = **102316085**

After calculation:

aᵣ = **0.2**  
bᵣ = **0.3**

So the final formula became:

z = x + 0.2 sin(0.3x)

This transformation slightly perturbs the original data but keeps the overall trend.

---

## Step 2 – Learning the PDF

We assume the transformed data follows:

p(z) = c · e^(−λ(z−μ)²)

This is similar to a Gaussian distribution.

### How parameters were estimated

- μ (mean) → average of transformed values  
- Variance → computed from z values  
- λ = 1 / (2 × variance)  
- c = √(λ / π)

---

## Final Results

μ (mean) = **25.8028**  
λ (lambda) = **0.001460**  
c (constant) = **0.021559**

---

## Observations

- The distribution of transformed values still looks roughly bell-shaped  
- Small λ suggests data is quite spread out  
 

---

## Tools Used
- NumPy  
- Pandas  


---

## Conclusion

This experiment helped me understand how transformations can change data distributions and how PDFs can be estimated from real data. Using the roll number
