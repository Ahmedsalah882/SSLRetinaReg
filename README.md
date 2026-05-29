# SSLRetinaReg

This code repository is directly related to the manuscript currently under consideration:
> **Title**: SSLRetinaReg: Lightweight Self-Supervised Technique for Retinal Image Registration
> 
> **Authors**: Ahmed Shamsia, Tapio Seppänen, and Md Ziaul Hoque
> 
> **Journal**: The Visual Computer (Under Consideration)
> 
> **Year**: 2026

---

## Abstract

Retinal image registration is essential for longitudinal analysis, yet it remains challenging due to large spatial displacement, limited overlap, and appearance variation. Recent work has shown that diffusion-based feature representations, combined with correspondence filtering and multi-stage transformation estimation, can achieve strong registration performance. However, diffusion-based feature extraction carries substantial computational cost, and it remains unclear whether such heavyweight representations are necessary for accurate retinal registration. In this work, we investigate whether a lightweight self-supervised convolutional encoder can serve as an effective alternative to diffusion-based features within a correspondence-driven registration pipeline. We propose SSLRetinaReg, which replaces diffusion feature extraction with a DenseNet-121 backbone trained through a masked image reconstruction objective. This self-supervised strategy enables the encoder to learn structurally informative retinal representations without requiring task-specific annotations or large-scale pretrained generative models. The learned features are integrated into a registration pipeline that combines SIFT and random point sampling for spatial coverage, with correspondence refinement achieved through inverse-consistency and transformation-based filtering. Coarse-to-fine alignment is then performed using homography followed by a third-order polynomial transformation. We conducted experiments on the FIRE benchmark dataset to show that the proposed approach achieves state-of-the-art results, with an AUC of 0.903 and a mean landmark error of 2.898. These results suggest that effective retinal image registration does not require computationally expensive generative representations, and that a lightweight self-supervised encoder, when paired with appropriate correspondence filtering and staged transformation estimation, provides a practical and competitive alternative. The code will be available at [https://github.com/Ahmedsalah882/SSLRetinaReg](https://github.com/Ahmedsalah882/SSLRetinaReg).

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

Acknowledgments} This research was conducted with the Center for Machine Vision and Signal Analysis in the Faculty of Information Technology and Electrical Engineering at University of Oulu, Finland. 
