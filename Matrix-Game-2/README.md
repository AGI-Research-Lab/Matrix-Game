<p align="center">
<h1 align="center">Matrix-Game 2.0</h1>
<h3 align="center">An Open-Source, Real-Time, and Streaming Interactive World Model</h3>
</p>

<font size=7><div align='center' >  [[🤗 HuggingFace](https://huggingface.co/Skywork/Matrix-Game-2.0)] [[📖 Technical Report](assets/pdf/report.pdf)] [[🚀 Project Website](https://matrix-game-v2.github.io/)] </div></font>


<div align="center">
  <img src="assets/images/cover.png" alt="teaser" />
</div>

## 📝 Overview
**Matrix-Game-2.0** is an interactive world foundation model for real-time long video generation.  Built upon an auto-regressive diffusion-based image-to-world framework, it can generate real-time[25fps] long videos conditioned on keyboard and mouse inputs, enabling fine-grained control and dynamic scene evolution.

## 🤗 Matrix-Game-2.0 Model
we provide three pretrained model weights including universal scenes, GTA driving scene and TempleRun game scene. Please refer to our HuggingFace page to reach these resources.

## Requirements
We tested this repo on the following setup:
* Nvidia GPU with at least 24 GB memory (A100, and H100 are tested).
* Linux operating system.
* 64 GB RAM.

## Installation
Create a conda environment and install dependencies:
```
conda create -n matrix-game-2.0 python=3.10 -y
conda activate matrix-game-2.0
pip install -r requirements.txt
# install apex and FlashAttention
# Our project also depends on [FlashAttention](https://github.com/Dao-AILab/flash-attention)
git clone https://github.com/SkyworkAI/Matrix-Game.git
cd Matrix-Game-2
python setup.py develop
```


## Quick Start
### Download checkpoints
```
huggingface-cli download Matrix-Game-2.0 --local-dir Matrix-Game-2.0
```

### Inference
After downloading pretrained models, you can use the following command to generate an interactive video with random action trajectories:
```
python inference.py \
    --config_path configs/inference_yaml/{your-config}.yaml \
    --checkpoint_path {path-to-the-checkpoint} \
    --img_path {path-to-the-input-image} \
    --output_folder outputs \
    --num_output_frames 150 \
    --seed 42 \
    --pretrained_model_path {path-to-the-vae-folder}
```
Or, you can use the script `inference_streaming.py` for generating the interactive videos with your own input actions and images:
```
python inference_streaming.py \
    --config_path configs/inference_yaml/{your-config}.yaml \
    --checkpoint_path {path-to-the-checkpoint} \
    --output_folder outputs \
    --seed 42 \
    --pretrained_model_path {path-to-the-vae-folder}
```
## ⭐ Acknowledgements

We would like to express our gratitude to:

- [Diffusers](https://github.com/huggingface/diffusers) for their excellent diffusion model framework
- [SkyReels-V2](https://github.com/SkyworkAI/SkyReels-V2) for their strong base model
- [Self-Forcing](https://github.com/guandeh17/Self-Forcing) for their excellent work
- [GameFactory](https://github.com/KwaiVGI/GameFactory) for their idea of action control module
- [MineRL](https://github.com/minerllabs/minerl) for their excellent gym framework
- [Video-Pre-Training](https://github.com/openai/Video-Pre-Training) for their accurate Inverse Dynamics Model
- [TAEHV-VAE](https://github.com/madebyollin/taehv/) for their excellent work for accelerating VAE decoding

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Citation
If you find this codebase useful for your research, please kindly cite our paper:
```
```
