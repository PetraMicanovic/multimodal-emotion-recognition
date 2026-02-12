# Multimodal Emotion Recognition

This repository contains experiments for emotion recognition using
multimodal and unimodal models.

## Environment Notes
Experiments were conducted in **Google Colab** using a CUDA-enabled PyTorch setup. Specific package versions may vary depending on the execution environment.


## Datasets

- **MELD**  
  [Multimodal EmotionLines Dataset](https://affective-meld.github.io/) Used for training and evaluation of multimodal emotion recognition models (audio + text).

- **SEAC**  
  [Serbian Emotional Amateur Cellphone Speech Corpus (SEAC)](https://www.ktios.ftn.uns.ac.rs/sadapt/SADAPT_publications.html) 
  Used for **audio-only cross-dataset and domain adaptation experiments**. Audio models trained on MELD are used for initialization.

  ## Dataset Licenses
  All datasets used in this repository are subject to their original licenses and are not distributed here.

## Experiments

### MELD
- Baseline multimodal model (no temporal pooling)
- Audio model with temporal pooling (mean + std)
- Class-weighted training
- Text and Early Fusion baselines

### SEAC (Cross-Dataset + Domain Adaptation)
- Audio-only model initialized from the MELD audio baseline
- Speaker-split evaluation setup
    - Two unseen speakers (one male, one female) used for **zero-shot evaluation**
    - Remaining speakers used for **fine-tuning**
- Fine-tuned audio model evaluation
    - Tested again on the two held-out Serbian speakers(**cross-speaker evaluation**)
    - Tested on the original MELD test set (**cross-dataset back-transfer**)

## Structure
- `notebooks/` – experiment notebooks
- `models/` – trained model files (PyTorch weights and configuration)


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
  - No class weighting, encoder fine-tuning, or advanced fusion strategies are included.

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

- **v0.4 – seac-finetuning-and-domain-adaptation**
  - Audio model fine-tuned on the **SEAC dataset using remaining speakers** (domain adaptation)
  - Evaluated on:
    - SEAC speakers used for testing (**cross-speaker evaluation**)
    - Original MELD test set (**cross-dataset back-transfer**)
  - Added detailed evaluation visualizations:
    - Confusion matrix 
    - Per-class F1-score plots
  - Provides comparison between:
    - MELD-trained audio models (**with and without temporal pooling and class weighting**)
    - SEAC fine-tuned audio models (**with and without temporal pooling and class weighting**)

## Notes

- Encoder: **Wav2Vec2 (frozen)**
- Temporal pooling = mean + standard deviation
- Sampling rate: **16 kHz**
- Evaluation metrics: Accuracy + Weighted F1
- Confusion matrix includes counts and row-normalized percentages

---

## License

MIT