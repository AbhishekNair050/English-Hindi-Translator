# easyAnuvad

`easyAnuvad` is a neural machine translation (NMT) model designed to perform English-to-Hindi translation. This project applies various data preprocessing, tokenization, and padding techniques to build and train an LSTM-based translation model with attention mechanisms. 

## Table of Contents
- [Project Overview](#project-overview)
- [Data Processing](#data-processing)
- [Model Architecture](#model-architecture)
- [Installation](#installation)
- [Usage](#usage)

## Project Overview
`easyAnuvad` uses an LSTM-based sequence-to-sequence model with an attention layer to enhance the translation process. The project aims to achieve accurate English-to-Hindi translations using custom preprocessing and tokenization techniques. 

## Data Processing

### Loading Data
The dataset used in this project, `eng_hin_data.csv`, contains English-Hindi sentence pairs. Basic data cleaning operations such as removing HTML tags, URLs, contractions, and special characters are performed.

### Preprocessing
We use the following functions for text preprocessing:
- **`remove_html_tags`**: Strips HTML tags from text.
- **`remove_url`**: Removes any URLs present in the text.
- **`expand_contractions`**: Expands contractions in English text.
- **`preprocess_text`**: Standardizes text for tokenization.

### Tokenization and Padding
Tokenization is performed to convert sentences into sequences, and padding ensures that input and output sentences are of fixed length.

## Model Architecture

The model architecture consists of:
- **Embedding layers**: Converts tokens into dense vectors.
- **LSTM layers**: Encodes and decodes sequences.
- **Attention layer**: Provides focus on important words, improving translation quality.
- **Concatenation**: Merges encoder and attention outputs to generate translated sentences.

```python
easyAnuvad = build_model(input_vocab_size, output_vocab_size, max_length_input, max_length_output)
easyAnuvad.summary()
```

## Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/your_username/easyAnuvad.git
   cd easyAnuvad
   ```

2. **Set up environment**:
   ```bash
   conda create -n easyAnuvad python=3.11
   conda activate easyAnuvad
   ```

3. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

## Usage

1. **Data Preparation**:
   Ensure your dataset `eng_hin_data.csv` is in the project directory. Run the following command to preprocess and load data:
   ```python
   python data_preprocessing.py
   ```

2. **Model Training**:
   Train the model using:
   ```python
   python train.py
   ```

3. **Translation**:
   To translate an English sentence to Hindi, use the `predict` function:
   ```python
   from eval_predict import translate_sentence
   hindi_translation = translate_sentence("Hello, how are you?", easyAnuvad)
   print(hindi_translation)
   ```
