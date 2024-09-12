# OllamaFlask
 
To add a model to your Ollama local setup and call it using Python, follow these general steps:

1. Install Ollama
Ensure you have the Ollama CLI installed on your system. If you haven't done this yet, download and install it from the [Ollama website](https://ollama.com/).

2. Add a Model to Ollama
Ollama has a built-in command to download and add models. To add a model, open your terminal and use the following command:

```bash
ollama pull llama3.1:8b
```

3. Ensure Ollama is Running
Make sure your Ollama instance is up and running locally. You can use:

```bash
ollama serve
```

# Instructions for Running Flask API in Jupyter Notebook

This guide will walk you through setting up a local Flask API that mimics LMStudio's `/v1/chat/completions` endpoint using the Ollama model or another local language model.

## Prerequisites

Ensure the following are installed:
- **Flask**: Python web framework.
- **Ollama**: This guide assumes you're using Ollama.

You can install them by running the following commands in a cell:

```bash
!pip install flask ollama
```
Steps to Set Up and Run the Flask App
Write the Flask App:

Copy the Flask app code provided below into a code cell and execute it.
Run the Flask Server:

You can run the Flask server directly from within a Jupyter Notebook. The server will be accessible at http://localhost:1234/v1/chat/completions.
Send Requests to the API:

After the server is running, you can make POST requests to http://localhost:1234/v1/chat/completions using tools like curl, Postman, or Python code within the notebook.
Example Request:

To test the API, you can use the following code inside the notebook:
```python
import requests

url = "http://localhost:1234/v1/chat/completions"
data = { 
  "messages": [ 
    { "role": "system", "content": "You are a helpful coding assistant." },
    { "role": "user", "content": "How do I init and update a git submodule?" }
  ], 
  "temperature": 0.7, 
  "max_tokens": 150
}

response = requests.post(url, json=data)
print(response.json())
```
Or you can test it with a tool like curl or Postman:

```bash
curl --location 'http://localhost:1234/v1/chat/completions' \
--header 'Content-Type: application/json' \
--data '{ 
  "messages": [ 
    { "role": "system", "content": "You are a helpful coding assistant." },
    { "role": "user", "content": "How do I init and update a git submodule?" }
  ], 
  "temperature": 0.7, 
  "max_tokens": 150
}'
```
Stop the Server:
When you're done, stop the Flask server by interrupting the kernel in the Jupyter Notebook.