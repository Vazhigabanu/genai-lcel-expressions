## Design and Implementation of LangChain Expression Language (LCEL) Expressions

### AIM:
To design and implement a LangChain Expression Language (LCEL) expression that utilizes at least two prompt parameters and three key components (prompt, model, and output parser), and to evaluate its functionality by analyzing relevant examples of its application in real-world scenarios.

### PROBLEM STATEMENT:

Traditional chains in LLM application frameworks often require verbose boilerplate code, making pipeline construction, streaming, asynchronous execution, and debugging complex. The objective is to design and implement a declarative, composable chain using LangChain Expression Language (LCEL) using the pipe operator (|). The chain must accept at least two prompt variables (e.g., topic and target_audience), process the input through a chat model, and parse the raw response into a structured format (such as plain text or JSON) using an output parser, demonstrating seamless execution in a real-world generation scenario.

### DESIGN STEPS:

#### STEP 1:Component Initialization and Parameter Setup

Import core LangChain primitives: ChatPromptTemplate, a chat model client (e.g., ChatOpenAI), and an output parser (such as StrOutputParser or JsonOutputParser).

Construct a parameterized prompt template defining at least two distinct input variables (e.g., {topic} and {target_audience}) to dynamically format the user instruction.

#### STEP 2: Composing the LCEL Chain
Assemble the components using the LCEL pipe syntax (chain = prompt | model | output_parser).

Ensure proper data flow across the pipeline: the dictionary input populates the prompt, the formatted prompt passes to the chat model, and the model's raw completion streams directly into the parser.

#### STEP 3: Execution, Testing, and Evaluation
Invoke the compiled chain using .invoke() with a test payload containing concrete values for both parameters (e.g., {"topic": "Quantum Computing", "target_audience": "high school students"}).

Verify the returned parsed output for structural validity, coherence, and adherence to the dynamic prompt constraints across relevant scenarios.

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
)
model = ChatOpenAI(
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

<img width="987" height="975" alt="image" src="https://github.com/user-attachments/assets/537c226d-5d9a-4d59-a38f-3029ac153a45" />

<img width="975" height="500" alt="image" src="https://github.com/user-attachments/assets/d57880e8-538c-4498-aed2-ac8a9aa12404" />



### RESULT:

Thus, the LangChain Expression Language (LCEL) chain incorporating at least two prompt parameters and the three core components (prompt, model, and output parser) was successfully designed, implemented, and evaluated for seamless end-to-end execution in real-world application scenarios.
