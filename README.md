# GenFillX
GenFillX is a gradio app which provides 3 ai features
1. Image generateion
2. Image Inpainting
3. Image Oupainting

Original size of both the models is aroung **50gb** which is way more than the Vram provided in free instances of google colab and kaggle(around 15gb). So in order to use these models I performed 4bit quantization on both the models using the BitandBytes module and stored the 4bit quantized models in my own huggingface account. You can see the code in the quantization directory.

## Tech Stack Used

### Frontend / Interface
- [Gradio](https://gradio.app/) – Web interface for interacting with the models
- Google Colab – Used to run notebooks and host the FastAPI servers
- Kaggle - Used to run notebooks and host the FastAPI servers

### Models & ML Frameworks
- [FLUX.1-schnell](https://huggingface.co/black-forest-labs/FLUX.1-schnell) – Image generation model
- [FLUX.1-Fill-dev](https://huggingface.co/black-forest-labs/FLUX.1-Fill-dev) – Inpainting and outpainting model
- [Hugging Face Transformers](https://huggingface.co/transformers/) – Transformer-based model loading and inference
- [bitsandbytes](https://github.com/TimDettmers/bitsandbytes) – 4-bit and double quantization of models

### Evaluation
- [CLIP (OpenAI)](https://github.com/openai/CLIP) – Used to compute similarity between prompts and generated images (CLIP score)

### API & Backend
- [FastAPI](https://fastapi.tiangolo.com/) – High-performance API framework for serving models
- [Uvicorn](https://www.uvicorn.org/) – ASGI server for running FastAPI applications
- [Ngrok](https://ngrok.com/) (optional) – Tunnels Colab-hosted APIs to public URLs

### Multilingual Support
- [deep-translator](https://github.com/nidhaloff/deep-translator) – Prompt translation using Google Translate API

### Model Hosting
- [Hugging Face Hub](https://huggingface.co/) – For hosting quantized model weights

### Utilities
- NumPy, Pillow (PIL), Base64 – For image preprocessing, encoding, and decoding
- Jupyter / Google Colab Notebooks – Interactive environment for development and deployment



# How to run the app
1. Run flux_api.ipynb and flux_fill_api.ipynb.<br>
Note - **Its recommended to run one notebook on google colab and another on kaggle**  as we can only have one gpu enbaled notebook on both platform. make sure **gpu is ebabled** in both the notebooks.

2. After both the notebooks run successfully they both will generate an fastapi link which you should paste in the gradio_app.ipynb
3. Run the gradio_app.ipynb. you can run this notebook in google colab as this notebook does not require gpu to be enabled and run on cpu only
4. Click on the gradio app link generated after successfull execution and use the app.

 ![can't display screenshot](https://github.com/Shobhit043/Flux_project/blob/main/images/screenshots/Screenshot%202025-06-25%20155318.png)<br>

 # Features

 ### Image generation
 Enter Input prompt and click  on generate to start the image generation.

#### Inpainting
Upload the image you want to perform inpainting on and use the marker to highlight the image section where you want to perform inpainting and enter the prompt to guide the model for inpainting like "generate a glass".

#### Outpainting
Upload the image and select the expantion percentage and enter prompt which gives a brief summary of the image so that model can understand what is in the image and it can outpainting the image.

# Sample Outputs
 ### Image generation
 ![can't display screenshot](https://github.com/Shobhit043/Flux_project/blob/main/images/model_outputs/Screenshot%202025-06-25%20153509.png)<br>
 prompt - Generate image of a realistic dog
<br>
<br>
 ![can't display screenshot](https://github.com/Shobhit043/Flux_project/blob/main/images/model_outputs/Screenshot%202025-06-25%20153519.png)<br>
 prompt - Generate image of a frog holding a whiteboard with "bye" written on it.

#### Inpainting
 ![can't display screenshot](https://github.com/Shobhit043/Flux_project/blob/main/images/model_outputs/Screenshot%202025-06-25%20160724.png)<br>
 prompt - Write "hi" on the board
<br>
<br>
 ![can't display screenshot](https://github.com/Shobhit043/Flux_project/blob/main/images/model_outputs/Screenshot%202025-06-25%20160731.png)<br>
 prompt - Man wearing a grey jacket with white t-shirt
 
#### Outpainting
 ![can't display screenshot](https://github.com/Shobhit043/Flux_project/blob/main/images/model_outputs/Screenshot%202025-06-25%20160806.png)<br>
 Expantion percentage - 25% <br>
 prompt - A Calm lake reflecting green lush green hills and distant hizy mountains under soft overcast sky.
<br>
<br>
 ![can't display screenshot](https://github.com/Shobhit043/Flux_project/blob/main/images/model_outputs/Screenshot%202025-06-25%20160753.png)<br>
 Expantion percentage - 25% <br>
 prompt - A winding dirt path disappears into a dense, sun-dappled jungle.
