# Spatiotemporal Information Complementary Condensation for Video-based Person Re-identification
Official PyTorch implementation of "Spatiotemporal Information Complementary Condensation for Video-based Person Re-identification". 

## Overview
Video-based person re-IDentification (re-ID) focuses on retrieving videos of the same individual across different time periods and camera viewpoints. In contrast to image-based re-ID, video-based re-ID approaches can leverage Spatiotemporal (ST) Information (Info); however, it still grapples with key challenges, such as occlusion, inter-frame body misalignment, and background interference. A widely adopted strategy involves integrating attention mechanisms, which guide the model to focus on salient foreground regions. Yet, these attention regions, often overly localized and highly similar, tend to be unstable or susceptible to disturbance. Current methods attempt to expand the receptive field by shifting attention regions across frames, which heavily depends on an impractical assumption that body parts are spatially aligned. To address these issues, we propose the Spatiotemporal Information Complementary Condensation (STICC) model, which consists of an ST Info encoder and decoder.

## Inference Pipeline

![Inference Pipeline](./figures/STICC.png)

The STICC architecture include:
- **Identity-Discriminative Feature Encoding**: Extracts identity-discriminative features for each individual.
- **Individual-Specific Feature Encoding**: Emphasizes the extraction of shared identity-discriminative features among multiple individuals.
- **Relevance-Guided Decoder**: Employs relevance scores as weights to perform weighted condensation of the embeddings.
- **Memory-Guided Decoder**: Leverages dual memory modules to construct an attention mechanism for condensing the encoded embeddings. 

The encoder first uses self-attention to extract common features of foreground pedestrians. It then constructs a cross-attention via a memory module that integrates and stores individual-specific features, enabling different frames to complement each other at corresponding body parts without requiring precise body alignment. The decoder condenses the encoded embeddings into two complementary representation vectors via two sub-decoders: a relevance-guided decoder generates a fine-grained representation vector to preserve local details, while a memory-guided decoder extracts an abstract semantic representation vector that strengthens identity-related cues.  

## Demo

Our model processes video inputs to predict individual counts, operating over 3-second intervals.

| ![GIF 1](https://github.com/learnsharing/STICC/blob/master/scene1.gif?raw=true) | ![GIF 2](https://github.com/learnsharing/STICC/blob/master/scene2.gif?raw=true) |
| :---: | :---: |
| ![GIF 3](https://github.com/learnsharing/STICC/blob/master/scene3.gif?raw=true) | ![GIF 4](https://github.com/learnsharing/STICC/blob/master/scene4.gif?raw=true) |

## Setup

### Installation

Clone and set up the STICC repository

```
git clone https://github.com/learning/STICC/main
cd STICC
conda create -n STICC python=3.7
conda activate STICC
pip install -r requirements.txt
```

Data Preparation
- **PARI-1581** : Download PRAI-1581 dataset from Baidu disk or from the original dataset link.
- **Occluded Duke** : Download the dataset from Baidu disk or from the original dataset link.
- **PETS2009** : Download the dataset from Baidu disk or from the original dataset link.


### Usage
1.Training
  * For training, you need to prepare the dataset and prepreocess the relevant data. The data format follows:
   ```
   x y
   x y
   ```
   * The training script is as follows:
   ``` bash
   python train.py
   ```
2.Inference.

   * Evaulations on PRAI-1581 Dataset. The results are as follows:
  

   * Evaulations on Occluded Duke Dataset. The results are as follows:

| Dataset | Rank-1 | Rank-5 | mAP|
| ------ | --- | --- | --- |
| BiCNet-TKS | 33.6 | 49.5| 33.4|
| PSTA | 42.9 | 62.7| 43.4|
| STMN | 42.2 | 62.7| 43.7|
| GRL | 43.2 | 57.3| 43.4|
| SiNet  | 40.0 | 58.0| 40.0|
| MSINet | 40.3 | 62.4| 42.8|
| Ours | 57.1 | 75.6| 56.6|
||


# Acknowledgement

We thank the authors of [PAT](https://arxiv.org/pdf/2106.04095) and [STMN](https://cvlab-yonsei.github.io/projects/STMN) for their excellent work.
