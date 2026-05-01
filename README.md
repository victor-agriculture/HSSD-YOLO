# Dataset Availability and Reproducibility Materials

This repository provides supplementary materials to support the reproducibility of our research, in response to reviewer requirements regarding dataset availability. Due to institutional and financial constraints, the full dataset cannot be publicly released, but is available upon reasonable request. The resources below are provided to maximize transparency and reproducibility.

---

## Repository Structure

```
dataset/
├── Sample annotations/         # Sample YOLO-format label files (illustrates annotation format)
│   ├── train/                  # 7 sample annotation files from the training set
│   │   ├── 1.txt ~ 7.txt
│   │   └── classes.txt         # Class name definitions
│   ├── val/                    # 2 sample annotation files from the validation set
│   │   ├── 1.txt, 2.txt
│   │   └── classes.txt
│   └── test/                   # 1 sample annotation file from the test set
│       ├── 1.txt
│       └── classes.txt
├── split files/                # Dataset split index files (lists which samples belong to each split)
│   ├── train/train.txt         # File IDs used for training (70%)
│   ├── val/val.txt             # File IDs used for validation (20%)
│   └── test/test.txt           # File IDs used for testing (10%)
├── Model configuration files/
│   └── hssd_yolo.yaml          # Full model architecture and hyperparameter configuration
└── Output scripts/
    └── test.py                 # Inference and evaluation script
```

---

## 1. Sample Annotations

Sample annotation files are provided in **YOLO format**. Each `.txt` file corresponds to one image and contains one row per annotated object:

```
<class_id> <x_center> <y_center> <width> <height>
```

- All coordinates are **normalized** to the range `[0, 1]` relative to image width and height.
- Class definitions are listed in `classes.txt` within each split folder.

**Example** (`val/1.txt`):
```
0 0.384028 0.408333 0.045833 0.024074
```

These sample files illustrate the data structure and annotation format used throughout the full dataset. They are not intended to represent the complete dataset.

---

## 2. Dataset Split Files

The full dataset was divided into training, validation, and test sets at a **7:2:1 ratio**:

| Split      | Proportion | File                        |
|------------|------------|-----------------------------|
| Training   | 70%        | `split files/train/train.txt` |
| Validation | 20%        | `split files/val/val.txt`     |
| Test       | 10%        | `split files/test/test.txt`   |

Each file lists the image file IDs belonging to that split. Researchers who obtain the full dataset via request can use these files to reproduce the exact same experimental split used in our study.

---

## 3. Model Configuration

The file `Model configuration files/hssd_yolo.yaml` contains the complete model architecture configuration, including:

- Number of object classes (`nc`)
- Model scaling parameters (`scales`: depth, width, max channels)
- Full `backbone` layer definitions
- Full `head` layer definitions with detection outputs at P3/P4/P5 scales

This configuration can be used directly with [Ultralytics YOLO](https://github.com/ultralytics/ultralytics) to reconstruct the model architecture used in our experiments.

---

## 4. Output / Inference Script

The file `Output scripts/test.py` provides the inference and evaluation script used to generate model outputs on the test set. It can be run as follows:

```bash
python test.py
```

> **Note:** A trained model weight file (`best.pt`) and the corresponding dataset are required. The weight file and full dataset are available upon request.

---

## Requesting the Full Dataset

The complete dataset is available to researchers upon reasonable request, subject to institutional review. Please contact the corresponding author via the email address listed in the paper.

When submitting a request, please briefly describe:
- Your research affiliation
- The intended use of the dataset

---

## Citation

If you use these materials, please cite our paper:

```
[Citation information will be added upon publication]
```

---

## License

The materials in this repository are released for academic research purposes only.
