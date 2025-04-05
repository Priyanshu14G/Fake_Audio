# 🎧 Audio Deepfake Detection using RawNet2

This repository presents a practical solution to detecting AI-generated speech, addressing the growing threat of **audio deepfakes**. Built as part of Momenta's take-home technical assessment, the project explores cutting-edge techniques, implements a working pipeline, and reflects on real-world applicability.

---

## 🔍 Objective

Design and implement a lightweight audio deepfake detection system that:
- Differentiates between **bonafide** (real human speech) and **spoofed** (AI-generated) audio
- Can scale to analyze real-time conversations
- Demonstrates a deep understanding of existing research and deployment considerations

---

## 🧠 Approach Summary

### ✅ Selected Model: `RawNet2`

- **Reason for Selection**: Operates directly on raw waveforms, eliminating the need for heavy preprocessing like spectrogram generation.
- **Core Strengths**:
  - Residual CNN blocks effectively learn temporal audio features
  - Fast and efficient — promising for real-time deployment
  - Proven success in ASVspoof 2021 and similar challenges

---

## 📁 Folder Structure

- `RawNet2_Audio_Deepfake.ipynb`: Main notebook with model training and evaluation
- `data/train/bonafide` and `data/train/spoof`: Real and fake training audio
- `data/test/bonafide` and `data/test/spoof`: Real and fake testing audio

## 🧪 How to Run

1. Clone this repo
2. Place audio files under `data/` in correct format
3. Run the Jupyter notebook

```bash
pip install -r requirements.txt
jupyter notebook RawNet2_Audio_Deepfake.ipynb


