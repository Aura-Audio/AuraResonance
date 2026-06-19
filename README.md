# 🌊 AuraResonance
**Transform Chaos into Harmony: A Real-Time Resonance Lab for Web Audio**

[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/yourusername/AuraResonance/blob/main/LICENSE)
[![GitHub stars](https://img.shields.io/github/stars/yourusername/AuraResonance?style=social)](https://github.com/yourusername/AuraResonance/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/yourusername/AuraResonance?style=social)](https://github.com/yourusername/AuraResonance/network/members)
[![Twitter Follow](https://img.shields.io/twitter/follow/yourhandle?style=social)](https://twitter.com/yourhandle)

---

## **📌 Overview**
**AuraResonance** is a **single-page web app** that lets you **experiment with resonance in real-time**. It transforms chaotic, unpitched sounds (like white noise, water, or fabric rustling) into **musical, resonant tones** using **filters, feedback, and convolution**.

### **🎯 Core Concept**
Resonance is the process of **selectively amplifying specific frequencies** within a sound while attenuating others. By applying **high-Q filters, comb filters, feedback loops, or convolution**, you can turn **noise into music**, **water into chimes**, or **friction into singing bowls**.

> *"Think of white noise or water as a block of marble. The musical tones you want to hear are already inside—you just need to carve away the rest."*

---

---

## **🎨 Features**

### **🔊 Sound Sources**
| Source          | Description                                                                                     |
|-----------------|-------------------------------------------------------------------------------------------------|
| **🎤 Live Mic** | Real-time audio input from your microphone.                                                     |
| **White Noise** | Broadband noise with equal energy across all frequencies.                                       |
| **Pink Noise**  | Noise with equal energy per octave (softer highs).                                            |
| **Brown Noise** | Noise with more low-end energy (like a rumbling river).                                       |
| **🎵 Tone**      | Pure sine wave (default: 220Hz).                                                                |
| **💧 Water**     | Procedural water sound (Brown Noise + random "bubbles").                                       |
| **🌧️ Rain**      | High-frequency noise + random "raindrops."                                                     |
| **🔥 Fire**       | Bandpass-filtered noise + LFO modulation (crackling effect).                                   |

---

### **✨ Resonance Methods**
Below is a **complete table of all resonance methods** supported by AuraResonance, including their **mechanism, use cases, and resonance control**.

| **Method**               | **Category**               | **Mechanism**                                                                                     | **Resonance Control**               | **Best For**                          | **Example Sounds**                          | **Resonance % Estimation**                     |
|--------------------------|----------------------------|---------------------------------------------------------------------------------------------------|------------------------------------|---------------------------------------|--------------------------------------------|-----------------------------------------------|
| **High-Q Bandpass**      | Filter-Based              | Isolates a narrow frequency band, amplifying it while attenuating others.                        | Q factor, Frequency               | White/pink/brown noise, water, cuddles | River → cello note, static → howling wind    | Energy ratio, Q factor, spectral flatness     |
| **Low-Q Bandpass**       | Filter-Based              | Broadly boosts a frequency range.                                                                | Q factor, Frequency               | Subtle warmth, ambient textures       | Water rumble, wind                          | Energy ratio                                 |
| **Lowpass Filter**       | Filter-Based              | Attenuates high frequencies, allowing lows to dominate.                                          | Cutoff frequency, Q factor        | Warmth, muffling                      | Underwater sounds, distant noise            | Energy ratio (low-frequency focus)          |
| **Highpass Filter**      | Filter-Based              | Attenuates low frequencies, allowing highs to dominate.                                          | Cutoff frequency, Q factor        | Brightness, air                       | Hiss, airy textures                         | Energy ratio (high-frequency focus)         |
| **Peaking EQ**           | Filter-Based              | Boosts/cuts a specific frequency range.                                                          | Gain, Q factor, Center frequency  | Tone shaping                          | Enhancing specific harmonics in noise       | Energy ratio                                 |
| **Comb Filter**          | Feedback/Delay-Based       | Creates peaks and notches via **short delays + feedback**.                                       | Delay time, Feedback               | Metallic, robotic, glassy textures     | Fabric rustling → robotic choir             | Spectral flatness, crest factor              |
| **Sympathetic Feedback** | Feedback-Based             | Routes output back into input, creating **self-oscillation**.                                   | Frequency, Q, Feedback             | Sustained, singing tones              | Water → bell strikes, noise → Aeolian harp   | Dry/wet mix, energy ratio                    |
| **Allpass Filter**       | Filter-Based              | Shifts phase without affecting amplitude.                                                      | Frequency, Q factor                | Phasing, subtle resonance              | Swirling, spatial effects                   | Spectral flatness                            |
| **LFO-Modulated Filter** | Modulation-Based           | Sweeps a filter’s frequency/cutoff with an **LFO**.                                              | LFO rate, Depth, Filter Q          | Dynamic, evolving resonance           | Ghostly howls, sci-fi engines                | Energy ratio (time-averaged)                 |
| **Dynamic Filter Sweep** | Modulation-Based           | Manually or algorithmically sweeps filter parameters.                                           | Sweep rate, Range                 | Expressive, interactive resonance     | Rising/falling tones, waterfalls            | Energy ratio (real-time)                    |
| **Convolution Reverb**   | Physical Modeling          | Applies the **impulse response** of a physical space/object to a sound.                        | Impulse response (IR), Wet/Dry mix | Realistic acoustic resonance          | Water → bronze bell, noise → cathedral reverb | Energy ratio, spectral flatness             |
| **Waveguide**            | Physical Modeling          | Models the **vibrations of strings/tubes** using delay lines.                                  | Delay length, Feedback, Damping    | String-like, tubular resonance        | Water → plucked strings, noise → wind chimes | Energy ratio, Q factor                      |
| **Modal Synthesis**      | Physical Modeling          | Simulates **resonant modes** of objects (e.g., bells, plates).                                    | Modal frequencies, Decay times     | Complex, harmonic resonance           | Water → church bells, noise → metallic drones | Energy ratio, spectral flatness             |
| **Formant Filtering**    | Filter-Based              | Mimics the **resonant cavities** of the human vocal tract.                                        | Formant frequencies, Bandwidths    | Vocal-like resonance                  | Noise → vowel sounds, water → singing voices | Energy ratio                                 |
| **Granular + Resonance** | Granular-Based             | Applies resonance to **tiny grains** of sound.                                                  | Grain size, Filter Q, Pitch        | Textured, evolving resonance           | Water → shimmering clouds, noise → granular pads | Energy ratio, spectral flatness             |
| **Resonant Lowpass**     | Filter-Based              | Combines resonance (Q > 1) with lowpass filtering.                                              | Cutoff, Q factor                   | Warmth + resonance                    | Water → warm drones, noise → bright tones    | Energy ratio, Q factor                      |

---

---

## **🚀 How It Works**

### **1. Resonance Index Calculation**
AuraResonance calculates a **real-time resonance index (0–100%)** using a **weighted average** of three metrics:

| **Metric**            | **Weight** | **Description**                                                                                     | **Formula**                                                                                     |
|-----------------------|------------|-----------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------|
| **Energy Ratio**      | 40%        | % of energy in the resonant band (defined by filter frequency ± bandwidth).                          | `(Energy in Resonant Band / Total Energy) × 100`                                              |
| **Spectral Flatness** | 30%        | Measures how **peak-y** the spectrum is (lower = more resonant).                                    | `(1 - (Geometric Mean / Arithmetic Mean)) × 100`                                              |
| **Q Factor**          | 30%        | Normalized Q factor (higher Q = more selective = more resonant).                                  | `min(100, (Q / 100) × 100)`                                                                     |

**Example:**
If `Energy Ratio = 65%`, `Spectral Flatness = 80%`, and `Q Contribution = 70%`:
**Resonance Index = (65 × 0.4) + (80 × 0.3) + (70 × 0.3) = 71%**

---

### **2. Sound Source Generation**
| **Source**       | **Implementation**                                                                                     | **Key Features**                          |
|------------------|-------------------------------------------------------------------------------------------------------|-------------------------------------------|
| **Live Mic**     | `MediaStreamAudioSourceNode` + `getUserMedia`                                                        | Real-time audio input.                   |
| **White Noise**  | `ScriptProcessorNode` with random values.                                                             | Flat spectrum.                           |
| **Pink Noise**   | `ScriptProcessorNode` with 1/f filtering (6-pole filter).                                            | Equal energy per octave.                 |
| **Brown Noise**  | `ScriptProcessorNode` with integrated white noise.                                                   | More low-end energy.                     |
| **Tone**         | `OscillatorNode` (sine wave).                                                                        | Pure reference tone.                     |
| **Water**        | Brown Noise + random sine wave "bubbles" with frequency sweeps.                                      | Procedural, dynamic.                      |
| **Rain**         | White Noise + highpass filter + random high-frequency "raindrops."                                  | High-frequency texture.                  |
| **Fire**         | Bandpass-filtered noise + LFO modulation.                                                             | Crackling, dynamic.                       |

---

### **3. Resonance Methods in Depth**
#### **🔹 High-Q Bandpass Filter (The Magnifying Glass)**
- **How it works:** Isolates a **narrow frequency band** and amplifies it.
- **Effect:** Turns noise into a **pure tone** (e.g., water → cello note).
- **Parameters:** Frequency, Q (1–100).

#### **🔹 Comb Filter (The Infinite Mirror)**
- **How it works:** Uses **short delays + feedback** to create peaks and notches in the spectrum.
- **Effect:** Metallic, robotic, or glassy tones (e.g., fabric rustling → robotic choir).
- **Parameters:** Delay time (1–100ms), Feedback (0–100%).

#### **🔹 Sympathetic Feedback (The Endless Ring)**
- **How it works:** Routes the **filtered output back into the input**, creating self-oscillation.
- **Effect:** Sustained, singing tones (e.g., water → bell strikes).
- **Parameters:** Frequency, Q, Feedback.

#### **🔹 Convolution Reverb (The Ultimate Resonance)**
- **How it works:** Applies the **impulse response (IR)** of a physical object (e.g., church bell) to the sound.
- **Effect:** Imprints the **acoustic fingerprint** of the object (e.g., water → bronze bell).
- **Parameters:** IR file, Wet/Dry mix.

#### **🔹 LFO-Modulated Filter (Dynamic Resonance)**
- **How it works:** Sweeps a filter’s frequency with an **LFO (Low-Frequency Oscillator)**.
- **Effect:** Ghostly howls, sci-fi engines, or sweeping water tones.
- **Parameters:** LFO rate, Depth, Filter Q.

#### **🔹 Waveguide (String/Tube Simulation)**
- **How it works:** Uses **delay lines + filters** to model vibrating strings or tubes.
- **Effect:** String-like or tubular resonance (e.g., water → plucked strings).
- **Parameters:** Delay time, Filter frequency, Feedback.

---

---

## **📥 Installation & Usage**

### **1. Quick Start**
1. **Clone the repository:**
   ```bash
   git clone https://github.com/yourusername/AuraResonance.git
   cd AuraResonance
   ```
2. **Open `index.html` in a browser:**
   - Simply double-click the file or open it with a modern browser (Chrome, Firefox, Edge).
   - For **live mic input**, allow microphone access when prompted.

3. **Alternative: Host on GitHub Pages**
   - Push the code to a GitHub repository.
   - Enable **GitHub Pages** in the repo settings (serves `index.html` by default).

### **2. Using the App**
1. **Select a Sound Source:**
   - Choose from **Live Mic, White/Pink/Brown Noise, Tone, Water, Rain, or Fire**.
2. **Pick a Resonance Method:**
   - Try **Bandpass, Comb, Feedback, Convolution, LFO, or Waveguide**.
3. **Adjust Parameters:**
   - Use sliders to tweak **Q, Frequency, Feedback, Delay, and Wet/Dry Mix**.
4. **Monitor Resonance:**
   - Watch the **FFT Spectrum**, **Oscilloscope**, and **Resonance Index** update in real-time.
5. **Save/Load Presets:**
   - Save your favorite configurations and reload them later.

---

---

## **🛠️ Built With**
- **Vanilla JavaScript** (No frameworks)
- **Web Audio API** (For real-time audio processing)
- **HTML5 Canvas** (For visualizers)
- **CSS3** (For styling)

---

---

## **📂 Project Structure**
```
AuraResonance/
├── index.html          # Main app file
├── README.md           # This file
├── LICENSE             # MIT License
└── assets/             # (Optional) For impulse responses or other static files
```

---

---

## **🚀 Roadmap**
Here’s what’s **planned for future updates** to AuraResonance:

| **Feature**               | **Description**                                                                                     | **Priority** | **Status**      |
|---------------------------|-------------------------------------------------------------------------------------------------|--------------|-----------------|
| **Custom Impulse Responses** | Allow users to **upload their own IR files** for convolution reverb.                          | High         | ❌ Not Started   |
| **MIDI Control**          | Map sliders/buttons to **MIDI controllers** (e.g., knobs, faders).                             | High         | ❌ Not Started   |
| **Audio Recording**       | Add **recording functionality** to capture and export the processed audio.                   | High         | ❌ Not Started   |
| **More Sound Sources**    | Add **Wind, Thunder, Ocean Waves, Crackling Fire, ASMR (Cuddles, Breathing)**.                 | Medium       | ❌ Not Started   |
| **More Resonance Methods** | Add **Formant Filtering, Modal Synthesis, Granular Synthesis, FDN (Feedback Delay Network)**. | Medium       | ❌ Not Started   |
| **Preset Library**        | A **library of pre-configured presets** (e.g., "Church Bell," "Glassy Water," "Sci-Fi Drone"). | Medium       | ❌ Not Started   |
| **Mobile Optimization**  | Improve **touch support**, UI scaling, and performance for mobile devices.                   | Medium       | ❌ Not Started   |
| **Keyboard Shortcuts**    | Add **keyboard shortcuts** for quick access to sound sources/methods.                        | Low          | ❌ Not Started   |
| **Dark/Light Mode**       | Toggle between **dark and light themes**.                                                        | Low          | ❌ Not Started   |
| **Tooltips & Documentation** | Add **tooltips** and **in-app documentation** for each parameter/method.                     | Low          | ❌ Not Started   |
| **Web MIDI Integration**  | Enable **real-time MIDI control** for parameters.                                                | Low          | ❌ Not Started   |
| **Collaborative Mode**    | Allow **multiple users to connect** and control the app simultaneously (WebSocket).      | Low          | ❌ Not Started   |
| **Offline Support**       | Enable **service workers** for offline use (PWA).                                               | Low          | ❌ Not Started   |

---

---

## **🤝 Contributing**
Contributions are **welcome and encouraged**! Here’s how you can help:

### **1. Reporting Issues**
- Open an issue on GitHub with:
  - A **clear description** of the problem.
  - **Steps to reproduce**.
  - **Browser/OS** you’re using.

### **2. Suggesting Features**
- Open an issue with your **feature request** and a **detailed description**.

### **3. Pull Requests**
1. **Fork** the repository.
2. Create a **new branch** (`git checkout -b feature/your-feature`).
3. Commit your changes (`git commit -m "Add your feature"`).
4. Push to the branch (`git push origin feature/your-feature`).
5. Open a **Pull Request** on GitHub.

### **4. Development Setup**
- No build process required! Just edit `index.html` and test in a browser.
- For **advanced features** (e.g., MIDI, WebSockets), you may need to:
  - Run a local server (e.g., `python -m http.server`).
  - Use HTTPS for mic access (e.g., `ngrok` for local testing).

---

---

## **📜 License**
This project is **open-source** and licensed under the **[MIT License](https://github.com/yourusername/AuraResonance/blob/main/LICENSE)**.

---

---

## **🙏 Acknowledgments**
- **Web Audio API**: The backbone of this project.
- **MDN Web Docs**: For [Web Audio API documentation](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API).
- **GitHub Community**: For inspiration and support.

---
---

## **📢 Contact**
- **GitHub**: [@yourusername](https://github.com/yourusername)
- **Twitter**: [@yourhandle](https://twitter.com/yourhandle)
- **Email**: your.email@example.com

---
---
## **🌟 Support the Project**
If you find **AuraResonance** useful, consider:
- **⭐ Starring** the repository on GitHub.
- **🐛 Reporting issues** or **🚀 contributing** new features.
- **💬 Sharing** it with others who might find it interesting!

---
---
**🎶 Happy Resonating!**
*Turn chaos into harmony, one frequency at a time.*
