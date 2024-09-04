# AI-receptionist-for-Doctor
## Overview
The AI Receptionist is designed to assist in managing patient interactions via text-based communication. It can distinguish between emergency situations and routine messages, providing immediate instructions or forwarding messages to the doctor as needed. This solution uses state-of-the-art NLP models and a vector database to handle emergency responses in real-time.

## Project Structure
main.ipynb: This Jupyter Notebook contains the entire implementation of the AI Receptionist, including model initialization, vector database setup, and the main interaction loop.

## Technologies Used
- Transformers by Hugging Face: Used for initializing and running the language model (NousResearch/Meta-Llama-3.1-8B).
- Sentence-Transformers: Utilized for embedding emergency descriptions into vector space.
- FAISS (Facebook AI Similarity Search): Implemented as the vector database for fast similarity searches.
- Python Libraries:
  torch: For handling GPU operations and model computations.
  faiss-cpu: For vector similarity searches.
  aiohttp and asyncio: For asynchronous programming.
  random: To generate random ETA for doctor arrival.

## How It Works
1. Initialization: The AI receptionist initializes the LLM (Language Model) and the Sentence Transformer model for encoding emergency
   descriptions. It also sets up a FAISS index for storing and querying these encoded descriptions.

2. User Interaction:
   The AI receptionist asks the user if they are experiencing an emergency or if they want to leave a message for the doctor.
   If it’s a message, the user is prompted to enter their message, and the AI confirms that the message will be forwarded.
   If it’s an emergency, the AI asks for a description of the emergency, encodes it, and queries the FAISS database for the most relevant
   response.
3. Real-Time Updates: While waiting for the database query, the AI continues the conversation by asking for the user's location and provides a random ETA for the doctor's arrival.

4. Handling User Responses:
   If the user indicates that the doctor’s arrival will be too late, the AI immediately provides the relevant emergency instructions.
   Otherwise, it reassures the user to follow the steps while the doctor is on the way.
