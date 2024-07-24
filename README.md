# Project Overview

I finetuned a llama2 model - (https://huggingface.co/meta-llama/Llama-2-7b-hf). My problem statement was to make a text to sql model that gives me precise enough SQL Queries for any Natural language question we ask it. I used multiple methods and multiple models results of which are the many fine tuned model hosted on my huggingface hub profile - https://huggingface.co/Nishika26

### Getting into tyhe the files in this repo :-

1. Supervised_Fine_Tuning.ipynb :- This file contains fine tuning of model with SFTTrainer(HF Library), The Model that came out of this is the one that was used for the all the inference files.

2. ORPO-finetuning.ipynb :- This code contains finetuning of model using Odds Ratio Preference Optimization (ORPO) where the dataset given to the LLM contains question (or prompt), Chosen answer and Rejected answer. It incoperates Reinforcement learning's concept and "ORPOTrainer" is used for it. Although the fine tuned model that came out of this one was not so good.

3. huggingface_model_inference.ipynb :- In this, We run the inference of our finetuned model with the help of huggingface and langchain. The time the model takes to download and run to produce answers was huge so I converted the model to an ollama model. The steps i took for that were :-

              - First I downloaded my fine tuned hugging face model into my system.
   
              - Then, I quantized that model into a gguf model using llama.cpp - https://github.com/ggerganov/llama.cpp/tree/master
   
              - I made a Modelfile for my model (Modelfile7)
   
              - Then I used that Modelfile to create my ollama model using "ollama create llama2-sql-nishh -f Modelfile7"
   
              - After the model was created, I pushed it into my ollama account using some more commands
   And so now,

       This is my model  -   https://ollama.com/nishika/llama2-sql-nishh

Anybody can download the model into their local system using "ollama pull nishika/llama2-sql-nishh" into their Terminal, and then can be used in your code as well.

4. Ollama_Model_Inference.ipynb - This file contains the inference of my ollama model and it takes second to generate outputs. I have also drawn a comparision between the base model and my fine tuned model for the same query.


