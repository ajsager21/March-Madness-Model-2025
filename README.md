# March Madness Model 2025

**An XGBoost-based prediction model for the 2024–25 Men's College Basketball season — including a full tournament bracket simulator.**

[![Model](https://img.shields.io/badge/model-XGBoost-green.svg)]()
[![Accuracy](https://img.shields.io/badge/game%20accuracy-79.4%25-blue.svg)]()
[![vs. Vegas](https://img.shields.io/badge/beat%20spread-76.2%25-orange.svg)]()

---

## Overview

This repository holds the model code and data used to predict outcomes across the 2024–25 Men's College Basketball season, including the NCAA Tournament. The model was built on XGBoost and evaluated both on straight win/loss accuracy and against Las Vegas point-spread odds — a materially harder benchmark, since it requires not just picking the right winner but beating the market's own calibration.

## Key Results

| Metric | Result |
|---|---|
| Game outcome prediction accuracy | **79.4%** of games predicted correctly |
| Performance vs. Las Vegas spread | Would have **beaten the spread in 76.2%** of games |
| Model type | XGBoost (gradient-boosted trees) |
| Feature set | "Minus L10 Games" variant (excludes last-10-games rolling form features — see Methodology) |
| Tournament simulation | Full bracket simulated using model win probabilities |

## What's in this repo

| File | Description |
|---|---|
| `2025 March Madness XGBoost Model (Minus L10 Games)-Copy1.ipynb` | Core model: data prep, feature engineering, XGBoost training and evaluation |
| `Bracket Using XGBoost (Minus L10)-Copy1.ipynb` | Uses the trained model's win probabilities to simulate the full NCAA Tournament bracket, including quadrant/path-of-least-resistance analysis |
| `game_results_2025.csv` | Game-level results data for the 2024–25 season used for training/evaluation |

## Methodology

The model predicts the winner of individual college basketball matchups using team-level statistical features, trained via XGBoost. The **"Minus L10 Games"** naming indicates this version of the model excludes last-10-games rolling-form features from the input set — a deliberate variant, likely tested against a version that includes recent-form features, to assess whether recency signal helps or introduces noise/overfitting risk this close to tournament time.

The **bracket simulator** takes the trained model's per-matchup win probabilities and propagates them through the full 68-team NCAA Tournament structure, allowing exploration of how bracket seeding and quadrant placement (i.e., which teams a given team would need to beat en route to the championship) affects a team's realistic path to a title — distinct from just picking the "best" team in isolation.

## Running the notebooks

```bash
git clone https://github.com/ajsager21/March-Madness-Model-2025.git
cd March-Madness-Model-2025
pip install xgboost pandas numpy scikit-learn jupyter
jupyter notebook
```

Open `2025 March Madness XGBoost Model (Minus L10 Games)-Copy1.ipynb` first to train/evaluate the model, then `Bracket Using XGBoost (Minus L10)-Copy1.ipynb` to run the tournament simulation using the trained model's outputs.

## Notes

- Filenames retain their original `-Copy1` suffixes from the working environment; functionality is unaffected, but a cleanup/rename pass (e.g. `model_training.ipynb`, `bracket_simulation.ipynb`) would improve repo polish if revisited.
- No `requirements.txt` is currently included — the core dependencies are `xgboost`, `pandas`, `numpy`, and `scikit-learn`.

## Author

**A.J. Sager** 
Data science · sports analytics
