This script interacts with the Ollama framework to generate book information using the DeepSeek-R1, a thinking model designed for logical reasoning and structured responses. It pulls the deepseek-r1:7b model, queries it for ten books in JSON format, and processes the AI-generated response. DeepSeek-R1 excels in accuracy, structured output, and maintaining context-rich, coherent replies.
***

### **1.1 Pulling the DeepSeek-R1 Model**

```sh
!ollama pull deepseek-r1:7b
```

-   This command pulls (downloads) the `deepseek-r1:7b` model from Ollama's registry.
-   `deepseek-r1:7b` refers to the **7-billion-parameter version** of the DeepSeek-R1 model.
-   If the model is already downloaded, this command ensures it's up to date.
* * *

### **1.2 Defining the Prompt Message**

```python
messages = [{
    'role': 'user',
    'content': """
                return info about ten different books. \
                # return output in JSON format: \
                # {{
                # 'title': 'string', \
                # 'description': 'string', \
                # 'key_points': 'string' \
                #     }}
                """
}]
```

-   This defines a **list of messages** to send to the AI.
-   It mimics a conversational structure where the **user** sends a request.
-   The prompt asks the model to return **information about ten different books** in **JSON format**.
-   The `\` at the end of lines allows multi-line formatting while avoiding indentation issues.
-   The JSON structure inside comments (`# ...`) is likely intended as a guide for the model.
* * *

### **1.3 Importing Required Libraries**

```python
import ollama
import json
```

-   `ollama`: Used to interact with the locally running Ollama LLM.
-   `json`: Used for handling JSON data.
* * *

### **1.4 Sending the Request to Ollama**

```python
response = ollama.chat(
    model='deepseek-r1:1.5b',
    messages=messages,
    # format='json'
)
```

-   **`ollama.chat()`** is used to send a
