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
- **PARI-1581** : Download PRAI-1581 dataset from this link.
- **Occluded Duke** : Download the dataset from Baidu disk or from the original dataset link.


### Usage

2.Inference.

   * Evaulations on PRAI-1581 Dataset. The results are as follows:
\begin{table}[ht]
\centering
\caption{Comparison with the state-of-the-arts on Occluded-Duke dataset.} 
\renewcommand{\arraystretch}{1.2}
\setlength{\tabcolsep}{6pt}
\begin{tabular}{c c| c c c c c}
\Xhline{1pt}
\multicolumn{2}{c|}{\multirow{2}{*}{\textbf{Methods}}} & \multicolumn{5}{c}{Occluded-Duke (\%)} \\ \cline{3-7}
\multicolumn{2}{c|}{} & R-1 & R-5 & R-10 & R-20 & mAP \\
\Xhline{0.75pt}
BiCNet-TKS \cite{RN8} & CVPR'21 & 33.6 & 49.5 & 56.2  & 63.3 & 33.4 \\
STMN \cite{RN2}       & ICCV'21 & 42.2 & \underline{62.7} & 69.2  & \underline{77.6}  & \underline{43.7} \\
GRL \cite{RN9}        & CVPR'21 & \underline{43.2} & 57.3 & 60.6 & 64.1 & 43.4 \\
PSTA \cite{RN6}      & ICCV'21 & 42.9 & \underline{62.7} & 68.8 & 75.6 & 43.4 \\
SiNet \cite{RN7}      & CVPR'22 & 40.0 & 58.0 & 65.7 & 73.7 & 40.0 \\
PPCL \cite{RN14}      & TCSVT'23& 40.7 & 60.5 & 66.2 & 73.2 & 42.2 \\
MSINet \cite{RN16}    & CVPR'23 & 40.3 & 62.4 & \underline{69.7} & 74.7 & 42.8 \\
MDPR \cite{RN15}      & TMM'24  & 22.0 & 38.6 & 45.8 & 53.7 & 21.7 \\
DCCT \cite{RN35}      & TNNLS'24& 21.2 & 39.3 & 48.8 & 56.5 & 23.0 \\
\rowcolor{mybest}
Ours           & -       & \textbf{54.0} & \textbf{72.1} & \textbf{78.7} & \textbf{83.2} & \textbf{53.9} \\
\Xhline{1pt}
\end{tabular}

\justifying
\vspace{4pt}
\noindent The best results are shown in \textbf{bold}; 
the second best are \underline{underlined}; 
the results of our method are highlighted in \colorbox{mybest}{blue}.
\label{tab:OccludedDuke}
\end{table}

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

## Demo

Our model processes video inputs to predict individual counts, operating over 3-second intervals.

| ![GIF 1](https://github.com/learnsharing/STICC/blob/master/scene1.gif?raw=true) | ![GIF 2](https://github.com/learnsharing/STICC/blob/master/scene2.gif?raw=true) |
| :---: | :---: |
| ![GIF 3](https://github.com/learnsharing/STICC/blob/master/scene3.gif?raw=true) | ![GIF 4](https://github.com/learnsharing/STICC/blob/master/scene4.gif?raw=true) |


# Acknowledgement

We thank the authors of [PAT](https://arxiv.org/pdf/2106.04095) and [STMN](https://cvlab-yonsei.github.io/projects/STMN) for their excellent work.
