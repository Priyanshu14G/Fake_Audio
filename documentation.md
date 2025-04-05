# 📝 Documentation – Audio Deepfake Detection

This documentation provides an overview of the research insights, technical implementation, and reflective analysis conducted during the development of a lightweight audio deepfake detection system using **RawNet2**.

---

## 🔬 Research Summary & Model Selection

After surveying recent advancements from the [Audio Deepfake Detection GitHub repo](https://github.com/media-sec-lab/Audio-Deepfake-Detection), I shortlisted the following three promising approaches:

| Model         | Key Innovation                                                   | Performance            | Reason for Selection                                          |
|---------------|------------------------------------------------------------------|-------------------------|----------------------------------------------------------------|
| **RawNet2**   | Operates on raw waveforms using residual CNN blocks and GRUs     | ~96% EER (ASVspoof 2019) | No feature extraction, real-time inference, clean architecture |
| **LCNN**      | Squeeze-and-Excitation blocks with spectrogram input             | ~95% on multiple datasets | Lightweight, interpretable, widely-used                        |
| **Spec-ResNet** | Spectrogram-based deep residual CNN                           | ~90–95% (with augmentation) | Good accuracy, extensible with attention modules               |

### ✅ Chosen for implementation: **RawNet2**

- Direct input of raw audio
- Simpler pipeline (no spectrogram generation)
- Efficient training and generalization

---

## ⚙️ Implementation Insights

### ✅ What Worked Well

- **RawNet2** offered a clean and modular design.
- Used `torchaudio` for waveform loading and transformation.
- Training/inference worked on mid-range hardware.
- Dataset organized into `bonafide/` and `spoof/` folders for quick setup.

---

## 🚧 Key Challenges

| Challenge                 | Resolution |
|---------------------------|------------|
| 📉 **Dataset Size**       | Used a subset of ASVspoof; applied class weights |
| 🌀 **Varying Lengths**     | Used zero-padding and fixed-size chunking |
| 🔊 **Background Noise**    | Noted issues with low-quality spoof clips |
| 💻 **Hardware Limits**     | Kept small batch size and epochs for demonstration |

---

## 💡 Potential Improvements

### 🔁 Model Enhancements

- Add attention (e.g., SE blocks or transformers)
- Combine raw and spectrogram features (hybrid model)
- Denoising pre-processing layer

### 🧪 Training Improvements

- Data augmentation (pitch shift, time masking, noise)
- Hard negative mining
- Domain-specific fine-tuning

### ☁️ Deployment Ideas

- Convert to **ONNX**/**TorchScript**
- Use sliding window inference for streaming detection
- Wrap in **REST API** with real-time capture (Flask/FastAPI)
- Containerize for cloud or edge deployment

---

## 🧠 Reflections

### 1. **What were the most significant challenges?**
- Stabilizing training with raw audio input
- Avoiding overfitting with a small dataset

### 2. **How might this approach perform in real-world conditions?**
- May struggle with noisy, unseen spoofing methods
- Needs robust pre-processing and model tuning

### 3. **What additional data or resources would improve performance?**
- Diverse spoof audio (TTS, VC, adversarial)
- Domain-specific noise samples
- Pretrained anti-spoofing models (LA, PA datasets)

### 4. **How would you deploy this model in production?**
- Use Flask/FastAPI to expose API
- Apply streaming window inference for long audio
- Monitor performance over time
- Manual override for high-risk contexts

---

## 📌 Summary

- ✅ **RawNet2** provides a solid and efficient baseline
- 💡 Implementation demonstrated on custom dataset
- 🚀 Pipeline is production-adaptable with minor extensions
