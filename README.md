# Self-Supervised Retinal Image Registration

Official implementation of the paper:

**[Paper Title Here]**
[Authors]
[Conference / Journal Name], [Year]

---

## Overview

Retinal image registration is an important step in longitudinal disease monitoring, multimodal retinal analysis, image fusion, and clinical decision support. However, accurate registration remains challenging when retinal images contain large deformation, appearance changes, low overlap, or different acquisition conditions.

This repository provides the implementation of our self-supervised retinal image registration framework. The method is designed to learn robust spatial alignment between retinal images without relying on dense ground-truth deformation fields. It supports training, inference, and evaluation of registration performance using standard retinal image registration metrics.

---

## Main Contributions

* A self-supervised learning framework for retinal image registration.
* Robust alignment under challenging conditions such as large deformation and limited overlap.
* Evaluation against classical and learning-based registration baselines.
* Quantitative assessment using metrics such as AUC and MLE.
* Reproducible training and testing pipeline for retinal registration experiments.

---

## Repository Structure

```text
.
├── configs/                 # Configuration files for training and evaluation
├── data/                    # Dataset preparation scripts
├── datasets/                # Dataset loading utilities
├── models/                  # Model architecture definitions
├── losses/                  # Self-supervised loss functions
├── scripts/                 # Training, inference, and evaluation scripts
├── utils/                   # Helper functions and visualization tools
├── checkpoints/             # Pretrained weights or saved models
├── results/                 # Output registration results
├── requirements.txt         # Python dependencies
└── README.md
```

---

## Installation

Clone the repository:

```bash
git clone (https://github.com/Ahmedsalah882/SSLRetinaReg.git)
cd SSLRetinaReg
```

Create a virtual environment:

```bash
conda create -n retinal-reg python=3.10
conda activate retinal-reg
```

Install the required packages:

```bash
pip install -r requirements.txt
```

---

## Dataset Preparation

Place the retinal image dataset inside the `data/` directory or update the dataset path in the configuration file.

Expected structure:

```text
data/
└── dataset_name/
    ├── images/
    ├── train.csv
    ├── val.csv
    └── test.csv
```

Each CSV file should contain the image pairs used for registration, for example:

```text
fixed_image,moving_image
image_001_a.png,image_001_b.png
image_002_a.png,image_002_b.png
```

Update the dataset paths in:

```text
configs/default.yaml
```

---

## Training

To train the model:

```bash
python scripts/train.py --config configs/default.yaml
```

Training outputs, logs, and checkpoints will be saved under:

```text
results/
```

---

## Inference

To register a pair of retinal images using a trained checkpoint:

```bash
python scripts/inference.py \
    --fixed path/to/fixed_image.png \
    --moving path/to/moving_image.png \
    --checkpoint path/to/checkpoint.pth \
    --output results/registered_output.png
```

---

## Evaluation

To evaluate the model on the test set:

```bash
python scripts/evaluate.py \
    --config configs/default.yaml \
    --checkpoint path/to/checkpoint.pth
```

The evaluation script reports registration performance using metrics such as:

* AUC
* Mean Landmark Error, MLE
* Success rate under different error thresholds
* Failure cases under low-overlap or large-deformation settings

---

## Pretrained Models

Pretrained weights will be released here:

```text
checkpoints/
```

| Model                              | Dataset        | Download    |
| ---------------------------------- | -------------- | ----------- |
| Self-supervised registration model | [Dataset Name] | Coming soon |

---

## Example Results

Example qualitative registration results:

```text
results/examples/
```

The visualizations include:

* Fixed image
* Moving image
* Registered image
* Overlay before registration
* Overlay after registration
* Estimated deformation field, if applicable

---

## Citation

If you find this work useful, please cite:

```bibtex
@article{ paper_key,
  title   = {Paper Title},
  author  = {..., ... and Others},
  journal = {Journal or Conference Name},
  year    = {2026}
}
```

---

## License

This project is released under the [MIT License](LICENSE).

---

## Acknowledgements

This work builds on prior research in retinal image registration, self-supervised medical image analysis, and deformable image alignment. We thank the authors of the baseline methods and public retinal datasets used in this study.
