# DLA · TP5 — Foundation models for robotics

Practical session for the **DLA (Deep Learning)** course, Sorbonne Université, M2.
Tuesday 17 November 2026, 13:45–15:45. Instructor: Silvia Tulli (ISIR, Sorbonne Université).

It follows lecture **C5 “Foundation models for robotics”**. You rebuild, on small 2D problems that train in seconds, the three design choices shared by modern vision-language-action models (VLAs) such as π0, SmolVLA and GR00T N1:

1. a **generative action head** (flow matching) instead of mean-squared-error regression,
2. **action chunking**: predicting several future actions at once,
3. **language conditioning** of the policy (FiLM).

In the last part you load a real open VLA (SmolVLA) and a real robot dataset with 🤗 LeRobot.

| Part | Topic | Time | Runtime |
|---|---|---|---|
| 0 | Setup | 5 min | CPU |
| 1 | MSE regression vs flow matching on multimodal demonstrations | 35 min | CPU |
| 2 | Closed loop and action chunking under partial observation | 30 min | CPU |
| 3 | Language-conditioned policy (FiLM) and grounding tests | 30 min | CPU |
| 4 | A real VLA: SmolVLA on a LeRobot dataset | 15 min | GPU + internet |
| 5 | Wrap-up questions | 5 min | — |

## Getting started

**Google Colab (recommended).**
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Silviatulli/DLA-TP5-foundation-models-robotics/blob/main/DLA_TP5_Foundation_models_for_robotics_STUDENT.ipynb)
For Part 4 choose *Runtime → Change runtime type → T4 GPU*.

**Locally.**
```bash
git clone https://github.com/Silviatulli/DLA-TP5-foundation-models-robotics.git
cd DLA-TP5-foundation-models-robotics
pip install -r requirements.txt
jupyter notebook DLA_TP5_Foundation_models_for_robotics_STUDENT.ipynb
```
Part 4 additionally needs `pip install "lerobot[smolvla]"` and downloads about 2 GB. The LeRobot API changes between versions; the notebook tries the current and the older import paths.

## How to work
Cells marked `# TODO` are for you to complete; questions marked **Q** are answered in a markdown cell. Run the notebook top to bottom.

## Credits and references

The 2D environments, demonstrations, exercises and questions were written for this course. The following material was used to build the TP, and the notebook downloads or reimplements parts of it. Please see each source for its licence.

**Software, models and datasets used by the notebook**
- **PyTorch**, **NumPy**, **Matplotlib**: core libraries.
- **🤗 LeRobot**, Hugging Face (Apache-2.0): dataset loader and SmolVLA implementation used in Part 4. R. Cadène et al., *LeRobot: State-of-the-art Machine Learning for Real-World Robotics in PyTorch*, 2024. https://github.com/huggingface/lerobot
- **SmolVLA** pretrained model `lerobot/smolvla_base`, Hugging Face Hub. M. Shukor et al., *SmolVLA: A Vision-Language-Action Model for Affordable and Efficient Robotics*, arXiv:2506.01844, 2025. https://huggingface.co/lerobot/smolvla_base
- **Dataset** `lerobot/svla_so100_pickplace` (SO-100 pick-and-place, community data recorded for SmolVLA), fallback `lerobot/pusht`. See the dataset cards on https://huggingface.co/lerobot for licence and authors.
- **Sentence encoder** `sentence-transformers/all-MiniLM-L6-v2` (Apache-2.0), used in Part 3. N. Reimers & I. Gurevych, *Sentence-BERT*, EMNLP 2019. https://huggingface.co/sentence-transformers/all-MiniLM-L6-v2

**Methods reimplemented in simplified form**
- Flow matching (Parts 1–2): Y. Lipman et al., *Flow Matching for Generative Modeling*, ICLR 2023, arXiv:2210.02747; and X. Liu et al., *Flow Straight and Fast: Rectified Flow*, ICLR 2023, arXiv:2209.03003.
- Generative action heads for multimodal demonstrations: C. Chi et al., *Diffusion Policy: Visuomotor Policy Learning via Action Diffusion*, RSS 2023, arXiv:2303.04137.
- Action chunking and temporal ensembling (Part 2): T. Z. Zhao et al., *Learning Fine-Grained Bimanual Manipulation with Low-Cost Hardware* (ACT), RSS 2023, arXiv:2304.13705.
- FiLM conditioning (Part 3): E. Perez et al., *FiLM: Visual Reasoning with a General Conditioning Layer*, AAAI 2018, arXiv:1709.07871.
- VLA with flow-matching action expert: K. Black et al., *π0: A Vision-Language-Action Flow Model for General Robot Control*, arXiv:2410.24164, 2024.
- NVIDIA, *GR00T N1: An Open Foundation Model for Generalist Humanoid Robots*, arXiv:2503.14734, 2025.

**Course material**
- S. Tulli, DLA lecture C5 *Foundation models for robotics*, Sorbonne Université, 2026.
- H. Rahimi, *Multimodal Foundation Models*, lecture slides, Sorbonne Université, 12 November 2026 (background on vision-language models).

