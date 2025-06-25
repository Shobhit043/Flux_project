# 🌌 GenFillX

**GenFillX** is a Gradio-based web application that provides a user-friendly interface for:
- 🎨 **Prompt-based Image Generation**
- 🩹 **Inpainting** (filling missing or corrupted parts of an image)
- 🌄 **Outpainting** (extending the image beyond its borders)

This project uses **quantized** versions of large diffusion models to enable efficient inference even on limited hardware.

---

## 🚀 Features

- Utilizes **Black Forest Labs** models:
  - `black-forest-labs/FLUX.1-schnell` for image generation
  - `black-forest-labs/FLUX.1-Fill-dev` for inpainting and outpainting
- 🧠 Powered by **FastAPI** for backend API model hosting
- 🌐 **Multilingual prompt support** via `deep_translator` and `GoogleTranslator`
- 🧪 Includes evaluation with **CLIP score** to assess image–prompt alignment
- 💾 Uses **4-bit and double quantized models** for reduced memory usage and faster loading

---


## 🔁 Workflow

1. **Model Hosting:**
   - Run `flux_4bit_api.ipynb` and `flux_fill_4bit_api.ipynb` in **Google Colab**.
   - Each notebook starts a **FastAPI server** and returns an API URL (using `ngrok` or similar).

2. **API Integration:**
   - Paste the generated API URLs into `gradio_app.ipynb`.
   - The Gradio app uses these endpoints to send requests and receive generated images.

3. **Image Handling:**
   - Input images are encoded as **UTF-8 base64 strings** and sent to the FastAPI model.
   - The models return output images, which are rendered in the Gradio UI.

4. **Quantized Models:**
   - Original FLUX models (~50 GB) are **quantized to 4-bit** using `bitsandbytes` with **double quantization**.
   - These quantized models are hosted on your **Hugging Face account** and used in API notebooks to minimize RAM/VRAM usage.

5. **Evaluation:**
   - `clip_score.ipynb` evaluates model performance.
   - Around 10 prompt–image pairs were tested for prompt-image adherence using the CLIP score.

---

