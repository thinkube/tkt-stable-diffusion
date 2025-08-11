# Stable Diffusion Image Generator Template for Thinkube

A GPU-accelerated Stable Diffusion image generation template for the [Thinkube](https://github.com/thinkube/thinkube) platform, providing high-quality image generation with a Gradio UI.

## 🚀 Quick Start

[![Deploy to Thinkube](https://img.shields.io/badge/Deploy%20to-Thinkube-blue?style=for-the-badge&logo=kubernetes)](https://thinkube.github.io/tkt-stable-diffusion/deploy.html)

Click the button above to deploy this template to your Thinkube instance!

## ✨ Features

- 🎨 **Stable Diffusion**: High-quality text-to-image generation
- 🚀 **Optimized Performance**: Memory efficient attention, VAE slicing, and fp16 precision
- 🖼️ **Gradio UI**: Interactive web interface for image generation
- 🖥️ **GPU Required**: Designed for Ampere+ GPUs (RTX 3090, A100, etc.)
- 📦 **Multiple Models**: Support for SDXL, SD 1.5, SD 2.1, and custom models

## ⚠️ Hardware Requirements

**This template requires an Ampere or newer GPU architecture:**
- ✅ NVIDIA RTX 3090 (24GB VRAM) - Recommended
- ✅ NVIDIA RTX 4090 (24GB VRAM) - Recommended
- ✅ NVIDIA A100, A40, H100
- ⚠️ NVIDIA RTX 3080 (10GB VRAM) - Limited to SD 1.5 models
- ❌ NVIDIA GTX 1080 (Pascal - NOT supported)
- ❌ NVIDIA RTX 2080 (Turing - NOT supported)

## 📋 Supported Models

### Stable Diffusion XL (Requires 20GB+ VRAM)
- `stabilityai/stable-diffusion-xl-base-1.0` (default)
- `stabilityai/stable-diffusion-xl-refiner-1.0`
- `segmind/SSD-1B` (smaller SDXL variant)

### Stable Diffusion 1.5/2.1 (Requires 8GB+ VRAM)
- `runwayml/stable-diffusion-v1-5`
- `stabilityai/stable-diffusion-2-1`
- `dreamlike-art/dreamlike-diffusion-1.0`
- `prompthero/openjourney-v4`

### Custom Fine-tuned Models
- `SG161222/Realistic_Vision_V6.0_B1_noVAE`
- `darkstorm2150/Protogen_x5.8_Official_Release`
- Any Hugging Face compatible model

## 🔧 Configuration

When deploying through Thinkube Control:

| Parameter | Description | Default | Example |
|-----------|-------------|---------|---------|
| `model_id` | Hugging Face model ID | `stabilityai/stable-diffusion-xl-base-1.0` | `runwayml/stable-diffusion-v1-5` |

## 📁 Template Structure

```
tkt-stable-diffusion/
├── manifest.yaml          # Template configuration
├── thinkube.yaml          # Deployment specification
├── Dockerfile.jinja       # Container definition
├── server.py.jinja        # Stable Diffusion server with Gradio
├── requirements.txt       # Python dependencies
└── README.md              # This file
```

## 🎮 Usage

Once deployed, access the Gradio interface through your browser:

1. **Enter a prompt**: Describe what you want to generate
2. **Adjust settings**:
   - **Negative Prompt**: What to avoid in the image
   - **Inference Steps**: More steps = higher quality (slower)
   - **Guidance Scale**: How closely to follow the prompt
   - **Image Size**: Resolution of the output image
   - **Seed**: For reproducible results
3. **Click Generate**: Wait for your image to be created

### Example Prompts

- "A majestic mountain landscape at sunset, highly detailed, 8k, photorealistic"
- "A futuristic city with flying cars, cyberpunk style, neon lights"
- "Portrait of a wizard, digital art, fantasy, detailed, artstation"
- "A cozy coffee shop interior, warm lighting, watercolor style"

## ⚡ Performance Tips

1. **Model Selection**:
   - Use SD 1.5 models for faster generation
   - SDXL provides higher quality but is slower

2. **Optimization Settings**:
   - Lower inference steps (20-30) for faster generation
   - Reduce image size for quicker results
   - Use fixed seeds for consistent testing

3. **Memory Management**:
   - The template automatically enables memory optimizations
   - VAE slicing and attention slicing are enabled by default

## 🔑 Environment Variables

- `HF_TOKEN`: Optional Hugging Face token for accessing gated models

## 📊 Resource Usage

- **GPU Memory**: 8-20GB depending on model and settings
- **CPU**: 4+ cores recommended
- **RAM**: 16GB+ recommended
- **Storage**: 20GB+ for model cache

## 🐛 Troubleshooting

### Out of Memory Errors
- Reduce image resolution
- Use SD 1.5 instead of SDXL
- Lower batch size to 1

### Slow Generation
- Reduce inference steps
- Use smaller image dimensions
- Ensure GPU is properly utilized

### Model Loading Issues
- Check HF_TOKEN for gated models
- Verify model ID is correct
- Ensure sufficient disk space for model cache

## 📚 Learn More

- [Stable Diffusion Documentation](https://huggingface.co/docs/diffusers/using-diffusers/sdxl)
- [Diffusers Library](https://github.com/huggingface/diffusers)
- [Hugging Face Models](https://huggingface.co/models?library=diffusers)
- [Thinkube Documentation](https://github.com/thinkube/thinkube)

## 📄 License

This template is part of the Thinkube project and follows the same licensing terms.