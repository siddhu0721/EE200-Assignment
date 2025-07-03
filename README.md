# EE200 Home Assignment - IIT Kanpur

---

## 📌 Problem 1: Frequency Mixer (Hybrid Image)

### 🎯 Objective
Create a **hybrid image** by combining:
- **Low-pass** filtered version of one image
- **High-pass** filtered version of another image

### ⚙️ Approach

- **Image Preprocessing:**
  - Images are loaded using Python libraries: `NumPy`, `Matplotlib`, `Pillow`, and `SciPy`
  - Converted to grayscale
  - Resized using Lanczos interpolation for consistency

- **Filtering Strategy:**
  - **Low-pass Filter:** Apply Gaussian filter → retains overall structure  
    `Low_Pass = G(image)`
  - **High-pass Filter:** Subtract Gaussian-filtered image from original  
    `High_Pass = image - G(image)`
  - **Hybrid Image:**  
    `Hybrid = Low_Pass_Image + High_Pass_Image`

### 🧠 Insight
- From **far distance**, low-pass features dominate.
- From **close distance**, high-pass details emerge.

---

## 📌 Problem 2: Frequency de-Mixer (Audio Denoising)

### 🎯 Objective
Filter out **unwanted sounds** like flute and beats from an audio file, retaining only **human voice**.

### ⚙️ Approach

- **Fourier Transform:**
  - Normalize the audio to avoid clipping
  - Use **Fast Fourier Transform (FFT)** for spectral analysis
  - Focus on frequencies up to the **Nyquist limit**

- **Observation:**
  - Human voice: 50 Hz – 1000 Hz  
  - Flute: 1200 Hz – 1750 Hz  
  - Beats: > 2100 Hz  
  - Flute and beats form distinct peaks in FFT plot

- **Filtering:**
  - Use **Band-pass filter (50 Hz – 1000 Hz)** to retain only human voice
  - Discard other frequency bands

### ✅ Result
Cleaned audio retaining only human vocal frequencies, effectively removing flute and beat components.

---

## 🛠️ Technologies Used
- Python
- NumPy
- SciPy
- Pillow
- Matplotlib
- Audio libraries for FFT and signal processing

---

## 📁 File Structure (Assumed)
```bash
.
├── images/
│   ├── input1.jpg
│   ├── input2.jpg
│   └── hybrid_output.jpg
├── audio/
│   ├── original.wav
│   └── filtered_output.wav
├── mixer.py
├── demixer.py
└── README.md
