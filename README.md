# Experimental verification of Signal sampling using various types
# Aim
Write a simple Python program for the construction and reconstruction of ideal, natural, and flattop sampling.
# Tools required
```
Google Collab
Python
NumPy Library
Matplotlib Library
Internet Connection
Computer / Laptop
```
## Theory

Sampling is the process of converting a continuous-time signal into a discrete-time signal by taking samples at regular time intervals.

According to the Nyquist Sampling Theorem, the sampling frequency must be at least twice the maximum frequency of the signal to avoid distortion.

---

### 1. Ideal Sampling

- In ideal sampling, the signal is sampled using instantaneous (zero-width) pulses.
- Each sample represents the exact value of the signal at that instant.
- It is a theoretical method and cannot be implemented practically.
- No distortion occurs.

---

### 2. Natural Sampling

- In natural sampling, the signal is multiplied with a train of pulses.
- The top of each pulse follows the shape of the input signal.
- It is practically possible.
- Small distortion may occur due to finite pulse width.

---

### 3. Flat-top Sampling

- In flat-top sampling, the sampled value is held constant for a short duration.
- The output consists of flat-topped pulses.
- It is widely used in digital systems.
- It introduces distortion called aperture effect.
  
# Program
```
import numpy as np
import matplotlib.pyplot as plt
# Continuous signal parameters
fm = 5                      # Message frequency 5hz
fs = 50                     # Sampling frequency 50hz
t = np.linspace(0, 1, 1000) # Continuous time axis
ts = np.arange(0, 1, 1/fs)  # Sampled time axis

# Original analog signal
x = np.sin(2 * np.pi * fm * t)#x=sin(2pifmt)

# Sampled values
xs = np.sin(2 * np.pi * fm * ts)

# Flat-top sampling generation
flat_top = np.zeros_like(t)

for i in range(len(ts)-1):
    idx = np.where((t >= ts[i]) & (t < ts[i+1]))
    flat_top[idx] = xs[i]

# Plotting
plt.figure(figsize=(12,8))

# Original signal
plt.subplot(4,1,1)
plt.plot(t, x)
plt.title("Original Analog Signal")
plt.grid()

# Ideal Sampling
plt.subplot(4,1,2)
plt.stem(ts, xs, basefmt=" ")
plt.title("Ideal Sampling")
plt.grid()

# Natural Sampling (approximated)
plt.subplot(4,1,3)
plt.plot(t, x)
plt.stem(ts, xs, linefmt='r', markerfmt='ro', basefmt=" ")
plt.title("Natural Sampling")
plt.grid()

# Flat-top Sampling
plt.subplot(4,1,4)
plt.plot(t, flat_top)
plt.title("Flat-top Sampling")
plt.grid()

plt.tight_layout()
plt.show()
```
# Output Waveform

<img width="1553" height="1026" alt="image" src="https://github.com/user-attachments/assets/f9ebe15a-50aa-4c0b-bdc1-8c29b6246a8b" />



# Result
Thus, the construction and reconstruction of Ideal, Natural, and Flat-top sampling were successfully implemented using Python, and the corresponding waveforms were obtained.
