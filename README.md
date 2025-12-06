# Image Captioning with CNN-LSTM and Attention (Flickr8k)

This project implements an image caption generator using a CNN encoder and an LSTM decoder on the Flickr8k dataset. The goal is to generate natural language descriptions for images and to study whether adding an attention mechanism to the baseline model can improve caption quality.

## Dataset

The model is trained and evaluated on the Flickr8k dataset, a public benchmark for image-to-sentence description. It consists of 8,000 images, each paired with five human-written captions, covering a variety of everyday scenes without focusing on specific famous people or places.

## Model Overview

1. **Baseline model (Encoder–Decoder):**
   - CNN encoder: VGG16 pre-trained on ImageNet is used to extract a fixed-length feature vector from each image.
   - Text processing: captions are tokenized and converted to integer sequences, then padded to a fixed length.
   - LSTM decoder: an embedding layer and an LSTM generate the caption word by word, conditioned on the image features and previous words.
   - Output: a dense layer with softmax predicts the next word in the sequence.

2. **Attention-based extension:**
   - Attention scores are computed between the image features and the LSTM hidden state.
   - The attention context vector is concatenated with the LSTM output before the final dense layers.
   - The aim is to allow the model to focus on different parts of the image as each word is generated.

## Motivation and Findings

The main objective of this project was to investigate whether adding an attention mechanism to a standard CNN–LSTM captioning model could improve performance on Flickr8k.

In practice, the attention-based model did not outperform the simpler encoder–decoder baseline. Likely reasons include:
- Increased model complexity and number of parameters.
- The relatively small and simple Flickr8k dataset, which may not benefit as much from attention as larger, more diverse datasets.
- A higher risk of overfitting without strong regularization.

These observations suggest that attention is not always guaranteed to improve results, especially when the dataset size and complexity are limited.

## Requirements

Install the Python dependencies with:

```bash
pip install -r requirements.txt
```

(Use the `requirements.txt` file created from this project, or adapt it based on your environment.)

## How to Run

1. Download the Flickr8k dataset and place the images and captions in the paths expected by the notebook.
2. Open the notebook:

```bash
jupyter notebook Image_Caption_Generator_Flickr_Dataset_CNN_LSTM_Attention_FINAL.ipynb
```

3. Run the cells in order to:
   - Extract image features with VGG16.
   - Prepare the caption sequences and vocabulary.
   - Train the baseline CNN–LSTM model.
   - Train and evaluate the attention-based model.


