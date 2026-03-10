## Copyright and Licensing
© [2026] [Srinath Kuruva]. All rights reserved.

This project is provided for demonstration purposes only and is not intended for commercial use, modification, or redistribution without explicit written consent from the author. All intellectual property rights remain with the author

## Prerequisites
* googlecolab
* Jupyter

# **Chatbot for Food Delivery Business**

## **Motivation:** 
The online food ordering platforms have become very popular in the recent years. The survivability of any such online business greatly depends on the satisfaction levels of customer support service. Customers frequently raise queries about their orders, such as delivery time, order status, payment details, or return/replacement policies. Providing manual customer support to a huge customer base such as answering queries is challenging, cost intensive with a high risk of poor customer experience.

## **Objecttive**
The objective is to design and implement a functional AI-powered chatbot that connects to the order database using an SQL agent to fetch accurate order details and convert them into concise, polite, and customer-friendly responses. Additionally, the chatbot will apply input and output guardrails to ensure safe interactions, prevent misuse, and escalate queries to human agents when necessary, thereby improving efficiency and enhancing customer satisfaction.

## **Approach Employed**
The chatbot is built on the LangChain framework, enabling a modular and extensible architecture. 
Key technical decisions and methodologies include:

- LangChain Framework: Utilized for orchestrating the interactions between the Large Language Model (LLM), various agents, and custom tools.

- SQL Agent for Database Interaction: An SQLAgent is employed to enable the LLM to query and retrieve information from the orders database using natural language. This allows the chatbot to fetch real-time order details without direct SQL coding.

- Input Guardrails (LLM-based Classification): An LLM-powered classifier (input_guard_check function) is implemented to categorize incoming user queries.

Output Guardrails (LLM-based Validation): An LLM-based validator (output_guard_check function) examines the chatbot's generated responses before they are presented to the user. 

Custom Tools for Response Generation:
order_query_tool_func: Extracts specific information from the raw database context based on the user's query, ensuring only requested facts are retrieved.
answer_tool_func: Formats the extracted factual information into concise, polite, and customer-friendly responses, adhering to conversational best practices.
Chat Agent: A structured-chat-zero-shot-react-description agent is initialized with these custom tools to manage the overall conversation flow, decide which tool to use, and generate coherent replies.
LLM: The gpt-4o-mini model is used for all LLM-powered components due to its efficiency and performance.

## **Workflow**
1. The User inputs the order ID
2. The SQL agent is invoked
  a. If the order ID is not valid - respond accordingly
  b. if the order ID is valid - the customer is asked to enter squery
3. The entered query is passed through the input safety gaurdrail
4. If the user query is safe, the chat agent is invoked which responds to the user queries using its two tools and LLM


