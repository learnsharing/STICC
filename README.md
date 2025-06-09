# STICC for Video-based Person Re-identification
Official PyTorch implementation of "Spatiotemporal Information Complementary Condensation for Video-based Person Re-identification". 

## Overview

## Inference Pipeline

![Inference Pipeline](./figures/STICC.png)

The STICC architecture include:
- **Common Info Encoding**: Detects pedestrian coordinates.
- **Individual-Specific Info Encoding**: Detects pedestrian coordinates.
- **Relevance-Guided Detail Decoder**: Detects pedestrian coordinates.
- **Memory-Guided Abstraction Decoder**: Detects pedestrian coordinates.

The common Info encoding is collaboratively optimized together with the individual-specific Info encoding and the decoders. The fine-grained and semantic-aware representation vectors are concatenated to form a comprehensive representation for person re-ID inference. 

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
- **PARI-1581**:Download PRAI-1581 dataset from this link.
- **Occluded Duke**:Download the dataset from Baidu disk or from the original dataset link.

### Usage

2.Inference

   * For Rank-1、Rank-5、Rank-10、Rank-20 and mAP, The result are as follows:
   | Dataset | Rank-1 | Rank-5 | Rank-10 | Rank-20 | mAP | 
    | ----------- | --- | --- | --- | --- | --- |
    | PRAI-1581| 66.3 | 87.1| 91.4 | 94.2 | 2 |
    | Occluded-Duke| 57.1 | 75.6 | 2 | 2 | 56.6 |
    ||
