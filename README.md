# Multimodal Conversational AI for E-commerce
This project builds a multimodal conversational AI assistant for e-commerce, combining text and image embeddings with retrieval-augmented generation (RAG). It enables natural product Q&A, evidence-grounded responses, and improved shopping experiences through conversational search.

## Architecture
<img width="1124" height="482" alt="image" src="https://github.com/user-attachments/assets/1e3f8737-2724-4f77-9f5a-8b4fd4974600" />

Flow ：
1. User Interface  
   - Users interact via a chatbot interface, submitting text and/or images  

2. Query Embedding (CLIP)  
   - Text is embedded with CLIP’s text encoder  
   - Images are embedded with CLIP’s image encoder  
   - If both are present, embeddings are concatenated and L2-normalized  

3. Vector Search (Qdrant)  
   - The normalized query embedding is sent to Qdrant  
   - Qdrant searches against stored product embeddings  
   - Returns top-K most similar products with metadata (name, price, description, image URL)  

4. Prompt Construction  
   - Retrieved product data is formatted into a structured prompt  
   - Includes instructions and fallback examples to ground the LLM response strictly in context  

5. Answer Generation (LLaMA 2)  
   - LLaMA 2 generates a natural-language response  
   - Response is grounded only in the retrieved product context  

## Answer Generation
https://github.com/katarinaa19/Multimodal-Conversational-AI-for-E-commerce-/blob/main/Evaluation%20and%20Answer%20Generation.pdf 
