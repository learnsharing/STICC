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
