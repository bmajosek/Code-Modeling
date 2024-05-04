# Code Completion Project

## Overview
This project focuses on creating and fine-tuning a model for code completion tasks on Kotlin and Python datasets. It involves extracting code from large open-source projects, fine-tuning a pre-trained transformer model (Phi-1.5), and evaluating the model's performance on both Kotlin and Python code completion tasks.

## Project Structure

- `train_model.ipynb`: Notebook for training the model on the Kotlin dataset.
- `evaluate_model.ipynb`: Notebook for evaluating the model on both the Kotlin and Python datasets.

## Usage

This project includes several Jupyter notebooks and Python scripts which are designed to be run in sequence. Below are step-by-step instructions on how to use each component of the project:

### 1. Extracting Code Files

Navigate to the `train_model.ipynb` Jupyter notebook to begin the process of extracting Kotlin code from your designated project directory. Here's how to proceed:

- **Set Source Directory**:
  Replace the `source_dir` variable's value with the path to the directory containing the Kotlin project from which you want to extract code.

  ```python
  source_dir = "../path/to/kotlin/project"
- **Run the Notebook**:
Execute all cells in the notebook to extract all Kotlin code, remove comments, and save the cleaned code into structured files.

### 2. Training the Model
Once you have your dataset ready, use the `train_model.ipynb` to fine-tune the pre-trained Phi-1.5 model:

- **Load Data**:
  Ensure your dataset paths are correctly set up to load the training and validation sets.
- **Execute Training**:
  Run all the cells in the notebook to start the training process. The model and tokenizer will be fine-tuned based on the provided Kotlin dataset.
- **Save Model and Tokenizer**:
  The fine-tuned model and tokenizer are automatically saved to the specified paths. Ensure you have write permissions to the target directory.

### 3. Evaluating the Model
To evaluate the performance of your trained model, use the `evaluate_model.ipynb` notebook:

- **Load Model and Tokenizer**:
  Make sure the paths to the saved model and tokenizer are correctly specified to load them successfully.
  ```python
  model, tokenizer = load_model_and_tokenizer(model_path="path/to/saved/model", tokenizer_path="path/to/saved/tokenizer")
  ```
- **Generate Test Prompts and Completions**:
  Use the generate_prompts_and_completions function to create test data from your saved code files.
  ```python
  test_files_splited = generate_prompts_and_completions(test_files)
  python_files_splited = generate_prompts_and_completions(python_files)
  ```
- **Run the Evaluation**:
  Execute the cells to assess the model using the generated prompts and completions. The notebook will compute accuracy metrics and generate code completions which you can review.

### 4. Visualizing Results
After evaluation, visualize the model's accuracy using the plotting functions provided in the notebook:

- **Plot Boxplots**:
  Use the plot_boxplot function to compare the accuracies obtained from Kotlin and Python code completions.
  ```python
  plot_boxplot(accuracies_kt, accuracies_py)
  ```
  
