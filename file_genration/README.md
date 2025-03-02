# File Generation Module

This module is responsible for generating code based on user inputs and dataset samples. It uses the Google Generative AI model to generate code for backend, frontend, and evaluation purposes.

## Structure

- `main.py`: The main script that orchestrates the code generation process.
- `utils/`: Contains helper functions and configuration for logging and generation settings.
  - `helper.py`: Helper functions for extracting code cells, reading datasets, preparing the environment, executing Python files, and handling prompt execution and storage.
  - `config.py`: Configuration for logging and generation settings.
- `generate_code/`: Contains prompt and template files for code generation.
  - `backend/`: Prompts and templates for backend code generation.
  - `frontend/`: Prompts and templates for frontend code generation.
  - `eval/`: Prompts and templates for evaluation code generation.
  - `user_input/`: Directory where user input files are stored.

## Usage

1. Ensure that the required environment variables are set in a `.env` file.

### Required Environment Variables
- `API_KEY`: Your API key for the Google Generative AI model.
- `MODEL_NAME`: The name of the model to use for code generation.

2. Run the `main.py` script to start the code generation process.

## Program Flow and Execution Details in `main.py`

1. **Load Environment Variables**: The script first loads the environment variables and configures the Generative AI model using the provided API key and model name.
2. **Prepare the Environment**: It prepares the environment by copying user input files to the appropriate directories.
3. **Extract Code Cells**: The script extracts code cells from the `.ipynb` file and reads the dataset sample from the provided dataset file.
4. **Start Chat Session**: A chat session with the Generative AI model is started.
5. **Generate Evaluation Code**: The script generates evaluation code using the extracted data and dataset sample.
6. **Execute Evaluation Code**: The generated evaluation code is executed, and the output is read.
7. **Generate Backend Code**: The script generates backend code using the evaluation output, extracted data, and dataset sample.
8. **Generate Frontend Code**: The script generates frontend code using the evaluation output, extracted data, and dataset sample.
9. **Store Generated Code**: The generated code is stored in the respective output files and replaced in the appropriate directories.

## Summary of Prompts in `generate_code` Directory

### Backend
- `prompt.md`: Contains the prompt for generating backend code. This file includes specific instructions and requirements for the backend code generation process.
- `template_code.md`: Contains the template code for backend generation. This file provides a base structure and code snippets that the generated backend code will follow.

### Frontend
- `prompt.md`: Contains the prompt for generating frontend code. This file includes specific instructions and requirements for the frontend code generation process.
- `template_code.md`: Contains the template code for frontend generation. This file provides a base structure and code snippets that the generated frontend code will follow.

### Evaluation
- `prompt.md`: Contains the prompt for generating evaluation code. This file includes specific instructions and requirements for the evaluation code generation process.
- `template_code.md`: Contains the template code for evaluation generation. This file provides a base structure and code snippets that the generated evaluation code will follow.

### User Input
- Directory where user input files (e.g., `.ipynb`, `.csv`, `.json`, `.xl*`) are stored. These files are used as inputs for the code generation process.

## Example

```bash
python main.py
```

This will start the code generation process based on the user inputs and dataset samples provided in the `generate_code/user_input/` directory.