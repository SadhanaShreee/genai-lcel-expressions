## Design and Implementation of LangChain Expression Language (LCEL) Expressions

### AIM:
To design and implement a LangChain Expression Language (LCEL) expression that utilizes at least two prompt parameters and three key components (prompt, model, and output parser), and to evaluate its functionality by analyzing relevant examples of its application in real-world scenarios.

### PROBLEM STATEMENT:
Design a chatbot that recommends products based on the user’s input of product category and budget. The chatbot should prompt the user to enter a desired product type and maximum spending limit. It will then return a list of suitable products within the specified budget. The system should handle various product categories and provide relevant recommendations.

### DESIGN STEPS:

#### STEP 1: Load Environment Variables

#### STEP 2: Set up Prompt and Model

#### STEP 3: Chain the Components Together & User Input

### STEP 4: Invoke the Chain & Output the result

### PROGRAM:
```
import os
import openai
from dotenv import find_dotenv, load_dotenv
from langchain.prompts import ChatPromptTemplate
from langchain.chat_models import ChatOpenAI
from langchain.schema.output_parser import StrOutputParser
_ = load_dotenv(find_dotenv())

openai.api_key=os.environ['OPENAI_API_KEY']

prompt = ChatPromptTemplate.from_template("what is the westher now in {P} .")
model = ChatOpenAI(temperature=1.0)  #adjust the temperature to get creeative response
output_parser = StrOutputParser()

chain = prompt | model | output_parser

product_input = input("ENTER THE PRODUCTS: ")
budget_input = input("ENTER THE BUDGET: ")

result = chain.invoke({"Products": product_input, "budget": budget_input})

print("Recommendation:", result)
```
### OUTPUT:
![Screenshot 2024-11-28 212346](https://github.com/user-attachments/assets/34d1c2af-b65e-45a3-8b35-2ac2df0bd639)

### RESULT:
Thus, implementing LCEL with parameters (topic and budget) successfully generates product recommendations, integrating prompt, model, and parser for dynamic, efficient responses.
