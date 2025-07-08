# DLMC Dataset Backup (Deep Learning Matrix Collection)

This repository hosts a **backup copy** of the Deep Learning Matrix Collection (DLMC) dataset, originally provided by Google Research. The purpose is to ensure long-term accessibility and reproducibility, in case the original source becomes unavailable.

---

## 📦 Dataset Overview

DLMC is a collection of sparse matrices derived from intermediate computations in deep neural networks. It is widely used in research related to sparse matrix multiplication (SpMM), sparse training, and GPU kernel optimization.

This dataset was introduced and analyzed in the following two papers:

> **1. [Sparse GPU Kernels for Deep Learning](https://arxiv.org/abs/2006.10901)**  
> Trevor Gale, Matei Zaharia, Erich Elsen  
> *arXiv:2006.10901*

> **2. [The State of Sparsity in Deep Neural Networks](https://arxiv.org/abs/1902.09574)**  
> Trevor Gale, Erich Elsen, Sara Hooker  
> *arXiv:1902.09574*

---

## 🧾 Dataset Description

Dataset of sparse matrices from [arXiv:2006.10901](https://arxiv.org/abs/2006.10901).  
Matrices were collected from models studied in [arXiv:1902.09574](https://arxiv.org/abs/1902.09574).

- Sparse matrices for each model are stored in separate directories:
  - `transformer/` for the Transformer model
  - `rn50/` for the ResNet-50 model

- The matrices are organized by sparsification method and final sparsity level.

- Lists of all matrices for each model are included in:
  - `transformer_matrices.txt`
  - `rn50_matrices.txt`

- Summary statistics for all matrices are included in:
  - `dlmc.csv`

- For convolutional layers in ResNet-50, the product of the output spatial dimensions (i.e., the `n` in MxKxN) is included in:
  - `rn50_batchsizes.txt`

### 📐 Matrix File Format

Each matrix is stored in its own file using the following format:

- The first line contains 3 integers: nrows ncols nnz
    which represent the number of rows, columns, and non-zero entries.

- Each subsequent line contains the **column indices of non-zero elements in a single row**, space-separated.

- All matrices are structured such that the forward pass corresponds to left multiplication: A * B = C
    where A is sparse, B is dense, and C is dense.

- Convolutional weight matrices are represented as 2D matrices suitable for an explicit GEMM-style convolution (i.e., im2col + matmul).

---

## 📂 Original Source

- Official dataset and implementation repository:  
👉 https://github.com/google-research/google-research/tree/master/sgk

- Dataset location: `sgk/data/`

---

## 🛡️ License and Attribution

- The DLMC dataset is created and owned by **Google Research**.
- This repository is **for academic backup purposes only** and does **not claim any ownership** of the dataset.
- If you are the dataset author or a Google representative and wish to have this mirror removed, please open an issue or contact the repository maintainer.

---

## 📁 Repository Structure

---
.
├── transformer/
├── rn50/
├── transformer_matrices.txt
├── rn50_matrices.txt
├── rn50_batchsizes.txt
├── dlmc.csv
└── README.md
---

## 🧪 Usage

You may clone this repository and use the dataset for academic purposes:

```bash
git clone https://github.com/CX9898/dlmc-dataset.git

## 🔍 Citation

If you use the DLMC dataset in your research, please cite the following works:

---
@article{gale2020sparse,
  title={Sparse GPU Kernels for Deep Learning},
  author={Gale, Trevor and Zaharia, Matei and Elsen, Erich},
  journal={arXiv preprint arXiv:2006.10901},
  year={2020}
}

@article{gale2019state,
  title={The State of Sparsity in Deep Neural Networks},
  author={Gale, Trevor and Elsen, Erich and Hooker, Sara},
  journal={arXiv preprint arXiv:1902.09574},
  year={2019}
}
---

## 🙏 Acknowledgements

Thanks to the Google Research team for releasing the DLMC dataset and enabling research in sparse neural networks and GPU kernel optimization.
