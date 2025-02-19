# Extract PDF Images That Span Across Multiple Pages

This notebook contains a series of cells to process generate synthetic data from different models to be later be evaluated by Azure OpenAI Service Evaluation in Azure AI Foundry. 

## Requirements
- Python 3.8
- PyMuPDF (`fitz`)
- Azure OpenAI SDK
- `json` and `re` libraries (standard Python libraries)

## Setup
1. Clone the repository.
2. Navigate to the project directory.
3. You may run this notebook on Fabric Notebooks or AzureML.
4. Run the notebook cells in order.

## Notes
- Ensure you have the necessary permissions to access Azure Key Vault and Storage account.
- Modify the paths and storage account details as needed.


## Cells Overview

### Installing Dependencies

The following code cell will use `pip` to install all the necessary dependencies listed in the `requirements.txt` file. This ensures that all the required packages are available for the project to run correctly.

### Code Description

The following code snippet demonstrates how to configure and initialize the Azure OpenAI client for extracting text from PDFs using PyMuPDF (`fitz`).

1. **Importing Libraries**:
   - `fitz`: PyMuPDF library for extracting text from PDF files.
   - `AzureOpenAI`: Library for interacting with Azure OpenAI services.
   - `json` and `re`: Standard Python libraries for handling JSON data and regular expressions, respectively.

2. **Azure OpenAI Configuration**:
   - `AZURE_OPENAI_API_KEY`: Your Azure OpenAI API key.
   - `AZURE_OPENAI_ENDPOINT`: Your Azure OpenAI endpoint URL.
   - `DEPLOYMENT_NAME`: The name of your Azure OpenAI deployment.
   - `AZURE_OPENAI_VERSION`: The version of the Azure OpenAI API you are using.

3. **Initializing the Azure OpenAI Client**:
   - The `AzureOpenAI` client is initialized with the provided API key, API version, and endpoint URL.

### Extract Text from PDF and Generating Synthetic Data

The following code snippet demonstrates how to extract text from a PDF file, clean JSON responses, generate synthetic data using Azure OpenAI, and save the data to a JSONL file.

### 4. Extract and Combine Images from Azure Storage
This cell performs the same tasks as Cell 2 but reads and writes files to an Azure storage account container. The storage account name is `aoaisplit98bd0002`, and the code connects to this storage account using a connection string stored as a secret in Azure Key Vault. Ensure the Azure resource running the notebook has Key Vault Contributor access.

### Execute Synthetic Data Generation

The following code snippet demonstrates how to extract text from a PDF file, generate synthetic data using Azure OpenAI, and save the data to a JSONL file.

1. **File Paths**:
   - `pdf_path`: Specifies the path to the PDF file from which text will be extracted. Change this to your PDF file path.
   - `output_file`: Specifies the path to the output JSONL file where the synthetic data will be saved.

2. **Extracting Text from PDF**:
   - The `extract_text_from_pdf` function is called with `pdf_path` as the argument to extract text from the specified PDF file.

3. **Generating Synthetic Data**:
   - If text is successfully extracted from the PDF, the `generate_synthetic_data` function is called with the extracted text to generate synthetic data.

4. **Saving Synthetic Data**:
   - The generated synthetic data is saved to the specified `output_file` using the `save_to_jsonl` function.
   - A message is printed to indicate that the synthetic dataset has been saved to the output file.

5. **Handling No Text Extraction**:
   - If no text is extracted from the PDF, a message is printed to indicate that no text was extracted.
