# Intelligent-Hiring-Assistant-Chatbot-for-Recruitment-Agency

# Project Overview:
The TalentScout Hiring Assistant Chatbot is an intelligent recruitment tool designed to interactively gather candidate information, assess technical skills, and generate personalized technical interview questions using an LLM. Built using Gradio, it provides a chat-like interface for candidates to communicate naturally, while the backend handles information gathering, question generation, and response storage. The assistant helps recruiters streamline the initial screening process and ensures a seamless and scalable candidate experience.

# Objectives:
Automate collection of applicant details through natural conversation.

Generate skill-specific, experience-based technical questions using a language model.

Store all interactions and responses in structured formats for HR use.

Create a seamless, user-friendly interface using Gradio.

# Installation Instructions:
To run the chatbot locally, follow the steps below:

1)Clone the Repository:

         git clone <repository-link>
         cd <repository-directory>

2)Install Required Packages Ensure you have Python 3.9+ and install the dependencies:

         pip install gradio transformers torch accelerate bitsandbytes

3)Launch the Application Run the Python script:

         python app.py

This will launch a local server and open the chatbot in your browser.

# Technical Details:

🔧 Libraries & Tools:

     Gradio – for building the chatbot interface

     Transformers – to load and use the LLM for prompt-based question generation

     Torch – model inference

     Accelerate & Bitsandbytes – for optimized model loading and 4-bit quantization

🧠 Model Used:

      Model Name: mistralai/Mistral-7B-Instruct-v0.1

      Architecture: Causal LLM, fine-tuned for instruction following

      Deployment: Inference with load_in_4bit=True for performance optimization

🏗 Architecture Highlights:

      State management using a conversation_state dictionary

      Step-wise information gathering → question generation → response recording

      All outputs saved in structured JSON files for easy review by recruiters

      Progress tracked using Gradio UI elements (sliders, buttons)

# Workflow:

User Interaction:

           Collects full name, email, phone, experience level, preferred position, location, and technical skills.

Dynamic Question Generation:

            Based on selected tech_stack and experience, the model generates:

             1)Conceptual questions

             2)Practical scenarios

             3)Coding challenges

             4)Advanced problems

             5)Best practice discussions

Candidate Response Collection:

           Each question is asked sequentially.Answers are saved and associated with the relevant question.

Data Storage:

           Candidate profile and Q&A are saved in timestamped .json files for HR access.

# Prompt Design:

The prompt for generating technical questions was crafted carefully to instruct the LLM clearly. It follows this format:

              Generate 5 technical questions for each skill in: {tech_stack}.For a candidate with {experience} years experience, create:
                       
                       1. Conceptual question
                       
                       2. Practical application

                       3. Coding challenge

                       4. Advanced problem

                       5. Best practices
                       
This ensures:

1)Questions are skill-specific

2)Depth of question matches experience level

3)A variety of question types for comprehensive evaluation

4)The LLM returns the output in a structured format, which is parsed into (technology, question) pairs.

# Challenges & Solutions:

# Challenge:

     Slow model loading

     Prompt output inconsistency

     State tracking across multiple UI events

     User input errors (e.g., skipping fields)

     Data persistence

# Solution:

      Used load_in_4bit=True with bitsandbytes to reduce memory usage

      Enforced a strict format in the prompt and added a custom parser to extract valid questions

      Implemented a global conversation_state dictionary to manage user flow

      Added checks and controlled transitions between steps to avoid invalid flows

      Structured responses and metadata saved in JSON files with timestamped filenames for easy record-keeping

# Conclusion:

The TalentScout Hiring Assistant Chatbot successfully demonstrates how conversational AI can streamline the recruitment process by intelligently gathering candidate information and dynamically generating tailored technical questions. By integrating powerful LLM capabilities with an intuitive Gradio interface, the system offers both recruiters and candidates a seamless, interactive experience.

With modular architecture, clear prompt design, and efficient state management, the chatbot serves as a robust prototype for AI-powered hiring solutions. Its ability to personalize interviews based on skillset and experience not only saves recruiter time but also enhances candidate engagement. Future enhancements like multilingual support, scoring mechanisms, and backend integration with applicant tracking systems (ATS) could further elevate its utility in real-world recruitment workflows.
