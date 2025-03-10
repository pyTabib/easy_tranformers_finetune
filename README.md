
# Easy Transformers Fine-Tune

**Easy Transformers Fine-Tune** is a Python library that simplifies the process of fine-tuning pretrained transformer models (like BERT, GPT-2, and T5) for various natural language processing (NLP) tasks such as text classification, named entity recognition (NER), and question answering. The library provides a high-level interface for training these models, evaluation tools, and integration features to make it easier for users to fine-tune state-of-the-art models with minimal effort.

## Key Features

- **Pretrained Model Support**: Fine-tune popular transformer models like `BERT`, `GPT-2`, `T5`, and others.
- **Simple Fine-Tuning API**: Easily fine-tune models for a wide range of NLP tasks.
- **Data Preprocessing**: Automatic tokenization and preprocessing of text data.
- **Customizable Training Loop**: A flexible training loop that can be adapted for various tasks.
- **Evaluation Metrics**: Built-in evaluation functions to track model performance, such as accuracy and F1 score.
- **Model Saving and Loading**: Save your fine-tuned models and load them for inference later.
- **Compatibility with Hugging Face**: Leverages the powerful Hugging Face `transformers` library to access and fine-tune models.
- **Easy Integration**: Integrate fine-tuned models into production pipelines with ease.

## Installation

You can install the library directly from PyPI using `pip`:

```bash
pip install easy-transformers-finetune
```

Alternatively, if you want to install the package locally, clone this repository and run the following:

```bash
git clone https://github.com/yourusername/easy-transformers-finetune.git
cd easy-transformers-finetune
pip install .
```

Make sure you have `Python 3.6` or later installed.

## Requirements

- Python 3.6+
- PyTorch >= 1.7.0
- Hugging Face Transformers >= 4.0.0
- Datasets >= 1.0.0
- Scikit-learn >= 0.24.0

The required dependencies will be automatically installed when you install the package.

## Usage

### Fine-Tuning a Model

Fine-tuning a pretrained transformer model like BERT for text classification is simple. Here's an example:

```python
from easy_transformers_finetune import fine_tune_model, setup_tokenizer, save_model

# Load the tokenizer for BERT
tokenizer = setup_tokenizer('bert-base-uncased')

# Fine-tune the model on the 'imdb' dataset (sentiment analysis)
model = fine_tune_model('bert-base-uncased', 'text-classification', dataset_name='imdb')

# Save the fine-tuned model
save_model(model, model_name='fine_tuned_bert')
```

### Evaluation

Once the model is fine-tuned, you can evaluate its performance using built-in metrics like accuracy and F1 score. Here’s how to evaluate a model:

```python
from easy_transformers_finetune import evaluate_model

# Example predictions and true labels
predictions = [0, 1, 0, 1]  # Model predictions
labels = [0, 1, 0, 0]  # Ground truth labels

# Evaluate the model
accuracy, f1_score = evaluate_model(predictions, labels)

print(f"Accuracy: {accuracy}")
print(f"F1 Score: {f1_score}")
```

### Preprocessing and Data Loading

You can use the `load_data()` function to load and preprocess datasets. It automatically tokenizes the text data for use with transformers:

```python
from easy_transformers_finetune import load_data, setup_tokenizer

# Setup tokenizer
tokenizer = setup_tokenizer('bert-base-uncased')

# Load and preprocess the IMDB dataset
train_data, test_data = load_data(dataset_name='imdb', tokenizer=tokenizer)

# Now you can pass the tokenized data to your model for training
```

### Saving and Loading Models

After fine-tuning a model, you can save it for future use, or load it again to make predictions:

```python
from easy_transformers_finetune import save_model, load_model

# Save the model
save_model(model, model_name='fine_tuned_bert')

# Load the model later
loaded_model = load_model('fine_tuned_bert')
```

## Example Notebooks

We provide Jupyter notebooks with examples to help you get started quickly:

- **[Text Classification Example](examples/text_classification_example.py)**
- **[Question Answering Example](examples/question_answering_example.py)**

These notebooks show how to fine-tune models on datasets like IMDb, SQuAD, etc., and how to use your fine-tuned models for inference.

## Contributing

We welcome contributions! To get started:

1. Fork the repository.
2. Create a new branch for your feature or bug fix.
3. Make your changes and add tests if necessary.
4. Submit a pull request.

Please follow the PEP-8 style guide and ensure that your code is well-tested.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

### **Contact**

If you have any questions or need further assistance, feel free to open an issue or contact the project maintainers.
