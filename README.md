# Assignment 3 – Learn Probability Density Functions using Roll-Number-Parameterized Non-Linear Model
# Submitted To: Dr. Suresh Raikwar

## Objective
To transform NO2 concentration values using the given nonlinear transformation and estimate values for parameters mu and lambda of a probability density function on the transformed data.

---

## Dataset
- Dataset: India Air Quality Data
- Source: https://www.kaggle.com/datasets/shrutibhargava94/india-air-quality-data
- Feature used: **NO2**
- NA values were removed before processing.

---

## Methodology

### Step 1: Data Transformation
NO2 feature (x) is transformed using:

z = x + a_r sin(b_r x)

where:
- a_r = 0.05 × (r mod 7)
- b_r = 0.3 × (r mod 5 + 1)
- r is Thapar University issued roll number

This introduces a nonlinear sin variation to the original NO2 values.

---

### Step 2: Probability Density Function Estimation
The transformed variable z is modeled using the following pdf:

p̂(z) = c · exp(−λ(z − μ)²)

The parameters are estimated using **Maximum Likelihood Estimation** assuming a Gaussian distribution:
#### Note: Although the transformed data shows slight right skewness, a Gaussian distribution was assumed. The estimated PDF represents the best Gaussian fit to the transformed NO₂ values using Maximum Likelihood Estimation.

- μ is estimated mean of z
- σ² is estimated variance of z
- λ = 1 / (2σ²)
- c = √(λ / π)

---

## Results

| Parameter | Value |
|---------|------|
| μ | 25.81266175882587 |
| λ | 0.0014605774203603466 |
| c | 0.021561916251518938 |

---

## Result Visualization
- Histogram of transformed variable z
- Estimated probability density function plotted over the histogram
- <img width="584" height="455" alt="image" src="https://github.com/user-attachments/assets/d05bfb06-84a7-4225-9e33-5b536863a360" />


This visualization confirms that the estimated PDF follows the distribution of the transformed data.

---

## Conclusion
The NO2 data was successfully transformed using the given function, and the parameters of the probability density function were estimated using Maximum Likelihood Estimation. The resulting distribution resembles a Gaussian distribution, validating the chosen modeling approach.
