# Multimodal Emotion Recognition

This repository contains experiments for emotion recognition using
multimodal and unimodal models.

## Environment Notes
Experiments were conducted in Google Colab using a CUDA-enabled PyTorch setup. Specific package versions may vary depending on the execution environment.


## Datasets

- **MELD**  
  [Multimodal EmotionLines Dataset](https://affective-meld.github.io/) used for training and evaluation of multimodal emotion recognition models (audio, text, video).

- **SEAC**  
  [Serbian Emotional Audio Corpus](https://www.ktios.ftn.uns.ac.rs/sadapt/SADAPT_publications.html) used for audio-only emotion recognition
  experiments. Models trained on MELD audio are used for initialization.

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
| Dataset | Modality       | Architecture                | Class Weights | HF Model |
|--------|----------------|-----------------------------|---------------|----------|
| MELD   | Audio          | Baseline (no pooling)       | ❌            | 🔗 https://huggingface.co/PetraMicanovic/meld-audio-baseline |


## Notes
Datasets and trained model weights are not included in this repository.

