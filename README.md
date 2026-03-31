# LIGO-Data-Analysis
Gemini said
Here is a high-quality, professional README.md tailored for your GitHub repository. It highlights the intersection of Deep Learning, Signal Processing, and Astrophysics.

Gravitational Wave Parameter Estimation using CNNs
Project Overview
This project implements a Deep Learning pipeline to perform Parameter Estimation on synthetic Gravitational Wave (GW) signals. By converting 1D strain data into 2D Time-Frequency Spectrograms, the model utilizes a Convolutional Neural Network (CNN) to "reverse-engineer" the physical characteristics (Chirp Parameters) of a binary merger event.

The core challenge addressed is the Signal-to-Noise (SNR) problem: identifying and measuring a faint frequency "sweep" embedded within stochastic Gaussian noise, similar to the data processed by LIGO/Virgo detectors.

Technical Stack
Language: Python 3.x

Signal Generation: NumPy, SciPy.signal (Linear Chirp synthesis, Phase integration)

Feature Engineering: Short-Time Fourier Transform (STFT) for Spectrogram generation

Deep Learning: TensorFlow / Keras (Sequential CNN architecture)

Visualization: Matplotlib

Methodology
1. Synthetic Data Generation
We generate synthetic "chirp" signals where a single hidden parameter (the Label, range 0.1 to 1.0) controls the instantaneous frequency evolution:

Initial Frequency: 30+70×label

Final Frequency: 150+100×label

Noise Injection: Realistic background noise is added using np.random.normal to simulate detector strain.

2. Time-Frequency Analysis (Spectrograms)
The raw 1D time-series data is transformed into 2D Spectrograms using a Hanning window. This allows the CNN to treat the physics problem as a Visual Pattern Recognition task, identifying the slope and intensity of the frequency sweep over time.

3. Model Architecture & Training
The model is a Regressor that takes a (Frequency×Time×1) input and outputs a continuous value representing the predicted physical label.

Loss Function: Mean Absolute Error (MAE)

Optimizer: Adam

Early Stopping: Implemented to prevent overfitting and monitor validation loss.

Key Results
Loss Convergence: Achieved a significant reduction in training loss (from 0.83 to 0.06).

High Precision: The model demonstrates strong predictive capabilities, successfully estimating labels with minimal error (e.g., Actual: 0.5988, Predicted: 0.6188) even in noisy environments.

Inverse Problem Mastery: Proves that CNNs can effectively map observed data back to its source parameters without manual feature extraction.

Future Scope
Real-World Integration: Testing the model against real data from the LIGO Open Science Center (GWOSC).

Whiten & Scale: Implementing frequency-domain whitening to improve the signal-to-noise ratio.

Acoustic Analogues: Exploring the sonification of model outputs to simulate Acoustic Black Hole (Dumb Hole) conditions in fluid dynamics experiments.
