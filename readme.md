# Azure OPENAI GPT Model + Query Enterprise data with Azure OpenAI and Cognitive Search
## Introduction
This program utilizes Azure Cognitive Search and Azure OpenAI to answer questions from uploaded PDF documents in Azure Blob Storage. It leverages Python virtual environment for development.

## Prerequisites
Before running the program, ensure that you have the following:

1. Azure Cognitive Search service and its admin/query key. Index needs to be created on Blob Container.
2. Azure Blob Storage account details, where you will upload files. Sample files present in data folder.
3. Azure OpenAI service and its API key.
4. Python virtual environment.
5. Installation
6. Clone the repository or download the program files to your local machine.

## Virtual Encironment
Create and activate a Python virtual environment using the virtual environment manager of your choice.
`pip install virtualenv`
`python<version> -m venv <virtual-environment-name>`
`source env/bin/activate`

## Install Dependencies
- [Azure Developer CLI](https://aka.ms/azure-dev/install)
- [Node.js](https://nodejs.org/en/download/)
- [Git](https://git-scm.com/downloads)
- [Powershell 7+ (pwsh)](https://github.com/powershell/powershell) - For Windows users only.
* Install the required dependencies by running the following command:
`pip install -r requirements.txt`

Set the necessary environment variables or update the code with your own values. Replace the placeholders in the code sample provided with your own values. The variables that need to be updated are marked with "YOUR VALUE HERE" comments.

## Usage
To use the program, follow these steps:

Ensure that your Azure Blob Storage contains the PDF documents you want to search.

### Run the program using the following command:
`python main.py`

The program will search for the specified question in the PDF documents stored in Azure Blob Storage.

It will retrieve relevant information from the documents and generate a prompt for the Azure OpenAI model.

The program will make a call to the OpenAI GPT model to get the answer to the question.

The answer, along with the retrieved data points and the prompt, will be printed to the console.

## Configuration
The program uses environment variables to store sensitive information. You can set these variables directly in your environment or use a .env file in the root directory of the project. Here are the variables that need to be set:

* `AZURE_STORAGE_ACCOUNT`: The name of your Azure Blob Storage account.
* `AZURE_STORAGE_CONTAINER`: The name of the container in your Azure Blob Storage where the PDF documents are stored.
* `AZURE_SEARCH_SERVICE`: The name of your Azure Cognitive Search service.
* `AZURE_SEARCH_INDEX`: The name of the search index in your Azure Cognitive Search service.
* `AZURE_OPENAI_SERVICE`: The name of your Azure OpenAI service.
* `AZURE_OPENAI_GPT_DEPLOYMENT`: The name of the OpenAI GPT model deployment.
* `AZURE_OPENAI_CHATGPT_DEPLOYMENT`: The name of the OpenAI ChatGPT deployment.
* `KB_FIELDS_CONTENT`: The field name for the content of the documents in the search index.
* `KB_FIELDS_CATEGORY`: The field name for the category of the documents in the search index.
* `KB_FIELDS_SOURCEPAGE`: The field name for the source page of the documents in the search index.
* Make sure to set the `OPENAI_API_KEY` environment variable or update the openai.api_key line in the code with your OpenAI API key.

## Limitations
The program assumes that the PDF documents in Azure Blob Storage are already processed and indexed in Azure Cognitive Search. If the documents are not indexed, you need to set up the indexing process separately.
The program currently uses a fixed template to generate the prompt for the OpenAI model. If you want to modify the prompt structure or add more sources, you can update the template variable in the code.
The program retrieves the top 3 search results from Azure Cognitive Search. You can adjust the top parameter in the search_client.search method to retrieve more or fewer results.
## License
This project is licensed under the MIT License.