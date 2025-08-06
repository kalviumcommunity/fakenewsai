Fake News Detective AI
Fake News Detective AI is an intelligent web application that detects and explains whether a piece of news is real or fake using LLM-based text analysis and retrieval techniques. The goal is to combat misinformation and provide users with a reliable and explainable classification of any news article or statement.

Project Overview
This project uses Gemini AI (or any LLM with function-calling support), integrates MERN stack, and leverages Retrieval-Augmented Generation (RAG) to:

Accept user-submitted news text

Analyze its authenticity using prompting and structured output

Retrieve facts from trusted sources

Respond with an explanation and verdict ("Real" or "Fake")

Key Concepts Implemented
1. Prompting
Well-designed prompts are crafted to guide the LLM in detecting misinformation. Prompts focus on:

Tone analysis (e.g., sensationalism)

Claim extraction

Reformulating queries for RAG

Generating a verdict and explanation

Example Prompt:

Analyze the following news statement for truthfulness. State if it's true or fake. Provide the reasoning in less than 150 words.
Statement: "{user_input}"

2. Structured Output
To ensure consistency and automation, responses follow a strict JSON schema:

json
Copy
Edit
{
  "verdict": "Real" | "Fake" | "Unclear",
  "confidence": "High" | "Medium" | "Low",
  "reason": "Explanation here"
}
This allows easy display and further logic in the frontend.

3. Function Calling
LLMs use function calling to interact with backend tools:

Example:

json
Copy
Edit
{
  "function": "query_fact_database",
  "arguments": {
    "query": "India launches Chandrayaan-4 in 2025"
  }
}
Functions include:

Searching fact databases

Fetching metadata

Logging usage

4. RAG (Retrieval-Augmented Generation)
To ensure factual correctness, the system:

Extracts the claim

Searches a vector DB (e.g., Pinecone) for related facts

Passes this context to the LLM

Generates a final response

Flow:

User inputs statement

Create embedding

Search trusted DB

Attach top-k results

Generate response

Tech Stack
Frontend: React (Vite), Tailwind CSS

Backend: Node.js, Express.js

LLM: Gemini / OpenAI (Function calling enabled)

Vector DB: Pinecone / ChromaDB

Database: MongoDB (for logs and feedback)

Evaluation Criteria
Criteria	Description
Correctness	Uses structured prompts and RAG to improve factual reliability
Efficiency	Fast responses via async calls and cache
Scalability	Modular and optimized backend for scaling across requests and APIs
