# Automated-dm-reply-instagram

Automated reply system for Instagram messages built with n8n and LLMs.  
This project demonstrates a pipeline that receives inbound messages via a webhook, performs RAG (Retrieval-Augmented Generation) using Pinecone as the vector store, drafts replies with an LLM, ensures the reply is JSON-valid, and returns it via an HTTP Request node.

Video demonstration: https://drive.google.com/file/d/1CMdVrbjaDRdEjNxMRB2VwPZVR7WjiO7_/view?usp=sharing

## Features
- Webhook-triggered flow when a message is received.
- RAG using Pinecone vector store to retrieve context/knowledge.
- LLM drafts replies based on retrieved context and the incoming message.
- Replies are validated to be JSON-compliant and sent back using an HTTP Request node.

## High-level flow
1. Instagram (or intermediary) sends incoming message to n8n webhook.
2. n8n extracts message payload and performs a vector search against Pinecone.
3. Retrieved context + incoming message are passed to the LLM to draft a reply.
4. The drafted reply is validated (JSON-valid) and returned to the sender via HTTP Request node.


## Prerequisites
- n8n instance (cloud or self-hosted).
- Pinecone account + API key and an index populated with embeddings.
- LLM provider account (e.g., OpenAI API key) or accessible LLM node in n8n.
- A method to receive Instagram messages (or a proxy) that can call the n8n webhook.
- Basic JSON validator (built-in in n8n or use an external/utility step).

