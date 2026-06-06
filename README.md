# Stochastic Interest Rate Modelling and Yield Curve Reconstruction

## Overview
This repository contains the solution for the IIT Roorkee Finance Club Open Project: *Implementing, Calibrating, and Extending the Cox-Ingersoll-Ross (CIR) Model on Real Yield Curve Data*. 

The objective is to reconstruct the entire yield curve utilizing only the 3-Month (3M) instantaneous short rate as an observable input. The project utilizes a single-factor stochastic differential equation (SDE) calibrated to historical yield data and extended to improve out-of-sample predictive accuracy.

## Project Structure
- **`src.ipynb`**: The primary Google Colab Notebook containing all data preprocessing, mathematical calibration, yield curve prediction, and critical analysis.
- **`cir_predictions.csv`**: The reconstructed yield curve containing the baseline CIR and CIR++ predictions.
- **`cir_metrics.csv`**: The out-of-sample evaluation metrics ($R^2$ and RMSE) for the tested maturities.

## Methodology
1. **Base CIR Calibration**: Ordinary Least Squares (OLS) discretization is used to calibrate the mean-reverting square-root diffusion process ($\kappa, \theta, \sigma$).
2. **Yield Curve Reconstruction**: Using the analytical zero-coupon bond pricing formula to map the 3M rate to 6M-30Y tenors.
3. **CIR++ Extension**: A deterministic residual shift is introduced across time and log-maturity basis functions to accurately fit the initial yield curve and correct structural single-factor constraints.

## Performance
- **Baseline Out-of-Sample $R^2$**: ~0.803
- **CIR++ Out-of-Sample $R^2$**: ~0.871 (> 0.85)

## Dependencies
- `numpy`
- `pandas`
