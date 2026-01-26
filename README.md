# Multimodal Emotion Recognition

This repository contains experiments for emotion recognition using
multimodal and unimodal models.

## Datasets

- **MELD**  
  Multimodal EmotionLines Dataset used for training and evaluation of
  multimodal emotion recognition models (audio, text, video).

- **SEAC**  
  Serbian Emotional Audio Corpus used for audio-only emotion recognition
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

## Notes
Datasets and trained model weights are not included in this repository.

