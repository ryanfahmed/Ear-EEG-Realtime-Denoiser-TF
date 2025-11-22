# Ear-EEG-Realtime-Denoiser-TF
tensorflow lite project on trained data

---

# EEG Denoising Project

Improving the quality of EEG signals in real time using Niura’s in ear earbuds and a lightweight neural network.

---

## What this project is

This project takes noisy brainwave signals from the Niura earbuds and cleans them in real time. The goal is to remove motion noise and improve the clarity of the EEG so it can be used for focus tracking and other applications.

The system works end to end:

1. Collect EEG data from the earbuds
2. Train a small model to learn the difference between noisy and clean signals
3. Convert the model into a mobile friendly format
4. Run it inside an Android app that cleans the EEG as you are wearing the earbuds

---

## What the model does

The model looks at two seconds of EEG at a time and tries to produce a cleaner version of the same window. It is trained using pairs of recordings:

* Clean recordings
* Noisy recordings

Over time, it learns the pattern of noise and how to remove it.

---

## How the data is prepared

The data used in this project comes from real recordings made with Niura’s earbuds. Each recording is:

* Loaded from a text file
* Split into short windows
* Normalized so the model can learn consistently
* Paired as noisy and clean samples

---

## How the model is trained

The autoencoder model is trained using TensorFlow. The training script:

* Reads the prepared dataset
* Builds the denoising model
* Trains it until the validation score stops improving
* Saves checkpoints and plots of the training progress

The final model is small and runs efficiently.

---

## Mobile deployment

After training, the model is converted to TensorFlow Lite, which allows it to run directly on Android. Inside the app:

* The earbuds stream EEG over Bluetooth
* The app processes the signal
* The model cleans the EEG in real time
* The app displays both raw and denoised signals

The full process runs smoothly at about eight milliseconds per window.

---

## What the app shows

The Android interface visualizes:

* Raw EEG
* Cleaned EEG
* Measured improvement in signal quality
* Real time waveforms

This lets users see exactly how much noise is removed.

---

## Why this matters

Cleaner EEG makes it possible to:

* Track focus more accurately
* Reduce false readings from movement
* Build more reliable cognitive features
* Unlock better applications for wearable neurotechnology

This project shows that real time EEG denoising is possible on consumer hardware without heavy processing.

---

## How to try it

To reproduce the project:

```
1. Place the EEG text files in the data folders
2. Run the dataset preparation script
3. Train the model
4. Convert it to TFLite
5. Load the model in the Android app
```

All scripts in this repository support these steps.

---

## Credits

All EEG recordings were collected using Niura’s earbuds.
All data processing, model training, and mobile integration were created as part of this project.
