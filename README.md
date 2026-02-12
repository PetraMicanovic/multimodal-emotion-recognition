# Multimodal Emotion Recognition

This repository contains experiments for emotion recognition using
multimodal and unimodal models.

## Environment Notes
Experiments were conducted in Google Colab using a CUDA-enabled PyTorch setup. Specific package versions may vary depending on the execution environment.


## Datasets

- **MELD**  
  [Multimodal EmotionLines Dataset](https://affective-meld.github.io/) used for training and evaluation of multimodal emotion recognition models (audio, text, video).

- **SEAC**  
  [Serbian Emotional Amateur Cellphone Speech Corpus (SEAC)](https://www.ktios.ftn.uns.ac.rs/sadapt/SADAPT_publications.html) used for audio-only emotion recognition experiments. Models trained on MELD audio are used for initialization.

  ## Dataset Licenses
  All datasets used in this repository are subject to their original licenses and are not distributed here.

## Experiments

### MELD
- Baseline multimodal model (no temporal pooling)
- Multimodal model with temporal pooling

### SR
- Audio-only model initialized from the MELD audio baseline

## Structure
- `notebooks/` – experiment notebooks
- `models/` – documentation of trained models (no weights)

### Pretrained Models
| Dataset | Modality       | Architecture                   | Class Weights | HF Model |
|--------|----------------|---------------------------------|---------------|----------|
| MELD   | Audio          | Baseline                        | ❌            | 🔗 https://huggingface.co/PetraMicanovic/meld-audio-baseline |
| MELD   | Text           | Baseline                        | ❌            | 🔗 https://huggingface.co/PetraMicanovic/meld-text-baseline |
| MELD   | Early Fusion   | Baseline                        | ❌            | 🔗 https://huggingface.co/PetraMicanovic/meld-early-fusion-baseline |
| MELD   | Audio          | Temporal Pooling                | ✅            | 🔗 https://huggingface.co/PetraMicanovic/meld-audio-temporal |
| MELD   | Text           | Baseline                        | ✅            | 🔗 https://huggingface.co/PetraMicanovic/meld-text-class-weights |
| MELD   | Early Fusion   | Temporal Pooling                | ✅            | 🔗 https://huggingface.co/PetraMicanovic/meld-early-fusion-temporal |
| SEAC   | Audio          | Baseline                        | ❌            | 🔗 https://huggingface.co/PetraMicanovic/audio_meld_seac_finetuned |
| SEAC   | Early Fusion   | Temporal Pooling                | ❌            | 🔗 https://huggingface.co/PetraMicanovic/meld-to-seac-audio-emotion-recognition-temporal-pooling-class-weights |

## Versions
 
- **v0.1-baseline-meld**
  - Audio baseline model (no temporal pooling)
  - Text baseline model (BERT embeddings)
  - Early fusion baseline model (feature-level fusion)

No class weighting, encoder fine-tuning, or advanced fusion strategies are included.

- **v0.2 – meld-temporal-pooling**
  - Temporal pooling over audio features (mean + std)
  - Class-weighted CrossEntropy loss
  - Improved robustness to class imbalance

- **v0.3 – cross-dataset-evaluation**
  - Audio model evaluated on **unseen SEAC dataset** (cross-dataset generalization test)
  - Evaluation performed on **two unseen speakers** (male + female)
  - Extended confusion matrix and F1-score visualizations for:
    - Audio model
    - Text model
  - Provides baseline before **speaker fine-tuning / domain adaptation**

## Notes
Datasets and trained model weights are not included in this repository.

