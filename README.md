# MusicScore-Inference

Official inference script for text-driven Music Score Generation experiment of [paper](https://arxiv.org/abs/2406.11462):

**MusicScore: A Dataset for Music Score Modeling and Generation**.

> [Yuheng Lin](https://rozenthegoat.github.io), [Zheqi Dai](https://github.com/dzq84) and [Qiuqiang Kong](https://github.com/qiuqiangkong)

## Setup

This codebase is under Python 3.11. To setup a conda environment, run the following:

```
conda create -n ScoreGen python=3.11
conda activate ScoreGen
```

```
pip install -r requirement.yaml
```

### Prepare the checkpoint

The global step of 78000 has been released on Huggingface, [portal here](https://huggingface.co/RozenWhite/ScoreDiffusion/tree/main).
Download it, and make sure you place it correctly.

## Run

An example shell script to run the inference is provided `inference.sh`.

```
bash inference.sh
```

It is also encouraged to make your own attempt by modifying the arguments:

```
CUDA_VISIBLE_DEVICES=0 \
python main.py \
  --prompt "a music score of piano" \
  --ckpt_path "./ckpt/global_step_78000.pt" \
  --config "config.yaml" \
  --outpath "result.jpg" \
  --n_sample 5 \
  --resolution 512 \
  --cfg_scale 4.0 \
  --ddim_steps 10 \
```

## Gradio Demo

We also support a simple Gradio web interface for easier inference.

```
python gradio_demo.py
```

By testing, inferencing 512 resolution of 9 images at one time consumes 23.58G GPU memory, within the capacity of one RTX 4090.


## error fixing
- attn-mask: [77,77] 
  - I have solved this problem by link
    pip install open-clip-torch==2.24.0

## scripts
- python main.py   --prompt "the theme of a Mozart-style piano sonata"   --ckpt_path "./ckpt/global_step_78000.pt"   --config "config.yaml"   --outpath "result.jpg"   --n_sample 1   --resolution 512   --cfg_scale 4.0   --ddim_steps 250
- python main.py   --prompt "cadenza of a Liszt-style rhapsody"   --ckpt_path "./ckpt/global_step_78000.pt"   --config "config.yaml"   --outpath "result.jpg"   --n_sample 1   --resolution 512   --cfg_scale 4.0   --ddim_steps 250
- python main.py   --prompt "chopin-style piano etude"   --ckpt_path "./ckpt/global_step_78000.pt"   --config "config.yaml"   --outpath "result.jpg"   --n_sample 1   --resolution 512   --cfg_scale 4.0   --ddim_steps 250