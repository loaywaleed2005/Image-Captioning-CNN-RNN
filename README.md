# Image Captioning using CNN-RNN

A deep learning project that automatically generates natural-language captions for images using a CNN-RNN architecture trained on the MS COCO dataset.

## Project Overview

The system combines computer vision and natural language processing:

- ResNet50 extracts visual features from images.
- An LSTM processes partial caption sequences.
- The image and text representations are merged.
- The model predicts the next word until a complete caption is generated.

## Dataset

The project uses the MS COCO 2014 training dataset.

- More than 118,000 training images
- Five human-written captions per image
- A subset of approximately 59,000 images was used for training

## Data Preparation

The workflow includes:

- Loading image-caption annotations
- Mapping each image to multiple captions
- Converting captions to lowercase
- Removing punctuation
- Adding `startseq` and `endseq` tokens
- Tokenizing words
- Padding caption sequences
- Building the vocabulary

## Model Architecture

### Image Branch

- Pretrained ResNet50
- Final classification layer removed
- 2048-dimensional image feature vector
- Dense layer with 256 units
- Dropout regularization

### Text Branch

- Word embedding layer
- Dropout regularization
- LSTM with 256 units

### Caption Decoder

The image and text branches are combined using element-wise addition, followed by dense layers that predict the next word.

The model also includes an auxiliary image-classification output for additional supervision.

## Training

- Batch size: 64
- Epochs: 10
- Optimizer: Adam
- Main loss: Categorical cross-entropy
- Custom data generator for memory-efficient training

## Caption Generation

Captions are generated using greedy decoding:

1. Begin with `startseq`
2. Predict the next word
3. Add the predicted word to the sequence
4. Continue until `endseq` or maximum caption length

## Evaluation

The project includes:

- Qualitative visualization of generated captions
- BLEU-1
- BLEU-2
- BLEU-3
- BLEU-4

The generated captions are compared with multiple human reference captions.

## Technologies

- Python
- TensorFlow
- Keras
- ResNet50
- LSTM
- NumPy
- Matplotlib
- NLTK
- MS COCO
- Kaggle

## Project File

Open `Image_Captioning_CNN_RNN.ipynb` to view the complete preprocessing, model architecture, training, caption generation, and BLEU evaluation workflow.

## Team

- Omar Samer
- Marawan Deif
- Loay Waleed
