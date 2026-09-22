# tkt-stable-diffusion

A Thinkube app template: image generation with Stable Diffusion models and a
Gradio page.

## What it does

- `server.py` loads the model named by `MODEL_ID` with Hugging Face
  diffusers, in float16 on the GPU. A model id containing `xl` loads the
  Stable Diffusion XL pipeline; any other loads the standard pipeline. It
  uses the DPM-Solver multistep scheduler, with attention and VAE slicing to
  lower memory use.
- A Gradio page at `/gradio` (`/` redirects there) takes a prompt, a
  negative prompt, inference steps (10 to 100), guidance scale (1 to 20),
  width and height (512 to 1536 px) and a seed (-1 for random). It shows the
  image and the seed used.
- `/health` reports the model and the GPU memory in use.
- `thinkube.yaml` deploys one container on port 7860 with one GPU.

## How it reaches a user

A person deploys it from the Templates page in thinkube-control, part of
[Thinkube](https://github.com/thinkube/thinkube). The deploy creates the
person's own repository from this template, then builds and deploys the app.
It is not installed on its own.

## Configuration

| Variable | Description |
|----------|-------------|
| `MODEL_ID` | Hugging Face model ID (default: stabilityai/stable-diffusion-xl-base-1.0). Set from the `model_id` parameter at deploy time |
| `APP_NAME` | Application name. The platform sets it to the name given at deploy time |
| `HF_TOKEN` | Hugging Face token for gated models. Optional: add it on the Secrets page of thinkube-control |

## Features

- Text-to-image generation
- Gradio web interface
- GPU-accelerated inference (RTX 3090+)
- Prompt and negative prompt support
- Image size customization (512-1536px)
- Seed control for reproducible results

## Working on it

| File | What it is |
|---|---|
| `server.py` | the diffusers pipeline, the Gradio page, `/health` |
| `Containerfile` | the image, on the platform's `ai-inference-base` image |
| `requirements.txt` | Python packages; PyTorch comes from the base image |
| `thinkube.yaml` | the deployment: one GPU, port 7860 |
| `manifest.yaml` | the template metadata, the `model_id` parameter and the `HF_TOKEN` secret |
| `docs/deploy.html` | a form that sends you to the Templates page of your thinkube-control with this template and a `model_id` filled in |

## License

MIT. Code generated from this template is yours: no attribution required, and you may license the app you build however you choose. See [LICENSE](LICENSE).

Copyright Alejandro Martínez Corriá and the Thinkube contributors
