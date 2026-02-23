This repository contains the code for my M.Sc. thesis, Comparative Evaluation of Drift Detection Methods for Incremental Fine-Tuning in Heat Load Forecasting (BTU Cottbus–Senftenberg, 2026). The project studies short-term heat-load forecasting for district heating systems under concept drift (e.g., retrofits, operational changes, evolving consumption patterns) and how to keep forecasting models reliable over time.

Project idea (detect-then-adapt)
I implement a closed-loop detect-then-adapt pipeline:

Train a baseline LSTM forecaster on an approximately stationary (“no-drift”) period.

During deployment, compute a univariate forecast-error stream (per-window MAE aggregated over a multi-step horizon).

Run a drift detector on the error stream.

If drift is detected, trigger incremental fine-tuning of the LSTM using a unified update protocol with a cooldown constraint (to avoid excessive updates).

Drift detectors compared
This repo evaluates three error-stream drift detectors as adaptation triggers:

DDM (Drift Detection Method)

Page-Hinkley (PH)

ADWIN

Evaluation setup
Detectors are assessed:

As alarm systems (false alarms, detection delay, alarm load).

End-to-end (forecast accuracy, post-drift recovery, and generalization when adaptation is frozen).

Experiments cover both abrupt retrofit-driven drift (with an annotated change point) and a controlled gradual-drift scenario constructed via probabilistic mixing over a transition window.

High-level takeaway
Drift-triggered fine-tuning can significantly reduce performance loss after drift, but the real-world value depends strongly on trigger quality (especially false alarms and delay). In these experiments, Page-Hinkley is the most consistently reliable trigger under abrupt drift, while ADWIN shows strong longer-term benefits under gradual drift.

Citation
If you use this code, please cite the thesis.
