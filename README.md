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

## Environment
```
python >=3.6 
pytorch >=1.4
opencv-python >=4.0
scipy >=1.4.0
h5py >=2.10
pillow >=7.0.0
imageio >=1.18
nni >=2.0 (python3 -m pip install --upgrade nni)
```
