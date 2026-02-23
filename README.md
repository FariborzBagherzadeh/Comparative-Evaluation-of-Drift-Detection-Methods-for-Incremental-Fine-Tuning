I’m an M.Sc. Artificial Intelligence student at BTU Cottbus–Senftenberg. My thesis explores how concept drift affects short-term heat-load forecasting in district heating / building-energy systems, where real-world changes (e.g., retrofits, control strategy updates, evolving user behavior) can degrade models trained only on past data.
​

In this project, I implement a detect-then-adapt forecasting pipeline: an LSTM baseline generates multi-step, 1-hour-ahead forecasts, a univariate forecast-error stream is monitored online, and the model is incrementally fine-tuned only when a drift detector raises an alarm (DDM, Page-Hinkley, ADWIN), with a cooldown to avoid excessive updates.
​

The work compares these detectors both as alarm mechanisms (false alarms, detection delay, alarm load) and by their downstream impact on forecasting accuracy, recovery after drift, and generalization after adaptation is frozen. Overall, drift-triggered fine-tuning can substantially reduce post-drift performance loss, but its practical value depends strongly on trigger reliability and update burden.
