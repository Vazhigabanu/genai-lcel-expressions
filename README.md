## Design and Implementation of LangChain Expression Language (LCEL) Expressions

### AIM:
To design and implement a LangChain Expression Language (LCEL) expression that utilizes at least two prompt parameters and three key components (prompt, model, and output parser), and to evaluate its functionality by analyzing relevant examples of its application in real-world scenarios.

### PROBLEM STATEMENT:
   To develop a simple text generation application using LangChain Expression Language (LCEL) by integrating a prompt template, a language model, and an output parser. The application should accept user inputs such as topic and language as prompt parameters, generate relevant content using the language model, and display the output in a clear and structured format. The functionality of the application is tested using different inputs to verify the accuracy and consistency of the generated responses.
  

### DESIGN STEPS:

#### STEP 1:

Import the required LangChain libraries and create a prompt template with two parameters: topic and language.

#### STEP 2:

Initialize the language model and create an output parser to convert the generated response into a readable text format.

#### STEP 3:

Combine the prompt template, language model, and output parser using LCEL pipe (|) operator and invoke the chain with suitable input values to generate the output.

### PROGRAM:
```
import os
import openai

from dotenv import load_dotenv, find_dotenv
_ = load_dotenv(find_dotenv()) # read local .env file
openai.api_key = os.environ['OPENAI_API_KEY']
import sys
print(sys.executable)
import langchain_core
import langchain_openai
from langchain_core.prompts import ChatPromptTemplate
from langchain_openai import ChatOpenAI
from langchain_core.output_parsers import StrOutputParser
print("All libraries imported successfully!")
prompt = ChatPromptTemplate.from_template(
    "Explain {topic} briefly in {language}."
)model = ChatOpenAI(
    model="gpt-4o-mini",
    temperature=0
)
output_parser = StrOutputParser()
chain = prompt | model | output_parser
result = chain.invoke({
    "topic": "Artificial Intelligence",
    "language": "simple English"
})

print(result)

```

### OUTPUT:

<img width="1673" height="1032" alt="image" src="https://github.com/user-attachments/assets/41e82757-9588-4ff9-bb38-45fdf406e7e0" />


<img width="1891" height="1087" alt="image" src="https://github.com/user-attachments/assets/e9bc10f9-bb6b-47b8-937d-5f64d0747a0f" />


### RESULT:

Thus, the LangChain Expression Language (LCEL) expression was successfully designed and implemented using a prompt template, language model, and output parser with two prompt parameters. The generated output was verified successfully.
